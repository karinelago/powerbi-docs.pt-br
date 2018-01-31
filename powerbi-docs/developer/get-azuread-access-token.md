---
title: "Autenticar usuários e obter um token de acesso do Azure AD para o aplicativo"
description: "Saiba como registrar um aplicativo no Azure Active Directory para uso com a inserção de conteúdo do Power BI."
services: powerbi
documentationcenter: 
author: markingmyname
manager: kfile
backup: 
editor: 
tags: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 08/11/2017
ms.author: maghan
ms.openlocfilehash: 3ff0fa3c83654ac577e98e730dc68ce3686e1198
ms.sourcegitcommit: 6e693f9caf98385a2c45890cd0fbf2403f0dbb8a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2018
---
# <a name="authenticate-users-and-get-an-azure-ad-access-token-for-your-power-bi-app"></a>Autenticar usuários e obter um token de acesso do Azure AD para o aplicativo Power BI
Saiba como você pode autenticar usuários no aplicativo do Power BI e recuperar um token de acesso para usar com a API REST.

Antes de chamar a API REST do Power BI, você precisa obter um **token de acesso de autenticação** (token de acesso) do Azure AD (Azure Active Directory). Um **token de acesso** é usado para permitir que seu aplicativo acesse os painéis, blocos e relatórios do **Power BI**. Para saber mais sobre o fluxo do **token de acesso** do Azure Active Directory, veja [Fluxo de concessão de código de autorização do Azure AD](https://msdn.microsoft.com/library/azure/dn645542.aspx).

Dependendo de como você insere o conteúdo, o token de acesso será recuperado de maneira diferente. Duas abordagens diferentes são usadas neste artigo.

## <a name="access-token-for-power-bi-users-user-owns-data"></a>Token de acesso para usuários do Power BI (o usuário possui dados)
Este exemplo refere-se a quando os usuários farão logon manualmente no Azure AD com o logon da organização. Isso é usado ao inserir conteúdo para usuários do Power BI que acessarão o conteúdo ao qual eles têm acesso no serviço do Power BI.

### <a name="get-an-authorization-code-from-azure-ad"></a>Obter um código de autorização do Azure AD
A primeira etapa para obter um **token de acesso** é obter um código de autorização do **Azure AD**. Para fazer isso, você constrói uma cadeia de caracteres de consulta com as propriedades a seguir e a redireciona para o **Azure AD**.

**Cadeia de caracteres de consulta do código de autorização**

```
var @params = new NameValueCollection
{
    //Azure AD will return an authorization code. 
    //See the Redirect class to see how "code" is used to AcquireTokenByAuthorizationCode
    {"response_type", "code"},

    //Client ID is used by the application to identify themselves to the users that they are requesting permissions from. 
    //You get the client id when you register your Azure app.
    {"client_id", Properties.Settings.Default.ClientID},

    //Resource uri to the Power BI resource to be authorized
    // https://analysis.windows.net/powerbi/api
    {"resource", Properties.Settings.Default.PowerBiAPI},

    //After user authenticates, Azure AD will redirect back to the web app
    {"redirect_uri", "http://localhost:13526/Redirect"}
};
```

Depois de construir uma cadeia de caracteres de consulta, você a redireciona para o **Azure AD** para obter um **código de autorização**.  Veja abaixo um método em C# completo para construir uma cadeia de caracteres de consulta do **código de autorização** e redirecioná-la para o **Azure AD**. Depois de conseguir o código de autorização, obtenha um **token de acesso** usando o **código de autorização**.

Em redirect.aspx.cs, [AuthenticationContext.AcquireTokenByAuthorizationCode](https://msdn.microsoft.com/library/azure/dn479531.aspx) será chamado em seguida para gerar o token.

**Obter o código de autorização**

```
protected void signInButton_Click(object sender, EventArgs e)
{
    //Create a query string
    //Create a sign-in NameValueCollection for query string
    var @params = new NameValueCollection
    {
        //Azure AD will return an authorization code. 
        //See the Redirect class to see how "code" is used to AcquireTokenByAuthorizationCode
        {"response_type", "code"},

        //Client ID is used by the application to identify themselves to the users that they are requesting permissions from. 
        //You get the client id when you register your Azure app.
        {"client_id", Properties.Settings.Default.ClientID},

        //Resource uri to the Power BI resource to be authorized
        // https://analysis.windows.net/powerbi/api
        {"resource", Properties.Settings.Default.PowerBiAPI},

        //After user authenticates, Azure AD will redirect back to the web app
        {"redirect_uri", "http://localhost:13526/Redirect"}
    };

    //Create sign-in query string
    var queryString = HttpUtility.ParseQueryString(string.Empty);
    queryString.Add(@params);

    //Redirect authority
    //Authority Uri is an Azure resource that takes a client id to get an Access token
    // AADAuthorityUri = https://login.windows.net/common/oauth2/authorize/
    string authorityUri = Properties.Settings.Default.AADAuthorityUri;
    var authUri = String.Format("{0}?{1}", authorityUri, queryString);
    Response.Redirect(authUri);
}
```

### <a name="get-an-access-token-from-authorization-code"></a>Obter um token de acesso do código de autorização
Agora você deve ter um código de autorização do Azure AD. Depois que o **Azure AD** redirecionar de volta para seu aplicativo Web com um **código de autorização**, você usa o **código de autorização** para obter um token de acesso. Veja abaixo uma amostra do C# que pode ser usada na página de redirecionamento e no evento Page_Load da página default.aspx.

O namespace **Microsoft.IdentityModel.Clients.ActiveDirectory** pode ser recuperado no pacote NuGet da [Biblioteca de Autenticação do Active Directory](https://www.nuget.org/packages/Microsoft.IdentityModel.Clients.ActiveDirectory/).

```
Install-Package Microsoft.IdentityModel.Clients.ActiveDirectory
```

**Redirect.aspx.cs**

```
using Microsoft.IdentityModel.Clients.ActiveDirectory;

protected void Page_Load(object sender, EventArgs e)
{
    //Redirect uri must match the redirect_uri used when requesting Authorization code.
    string redirectUri = String.Format("{0}Redirect", Properties.Settings.Default.RedirectUrl);
    string authorityUri = Properties.Settings.Default.AADAuthorityUri;

    // Get the auth code
    string code = Request.Params.GetValues(0)[0];

    // Get auth token from auth code
    TokenCache TC = new TokenCache();

    AuthenticationContext AC = new AuthenticationContext(authorityUri, TC);
    ClientCredential cc = new ClientCredential
        (Properties.Settings.Default.ClientID,
        Properties.Settings.Default.ClientSecret);

    AuthenticationResult AR = AC.AcquireTokenByAuthorizationCode(code, new Uri(redirectUri), cc);

    //Set Session "authResult" index string to the AuthenticationResult
    Session[_Default.authResultString] = AR;

    //Redirect back to Default.aspx
    Response.Redirect("/Default.aspx");
}
```

**Default.aspx**

```
using Microsoft.IdentityModel.Clients.ActiveDirectory;

protected void Page_Load(object sender, EventArgs e)
{

    //Test for AuthenticationResult
    if (Session[authResultString] != null)
    {
        //Get the authentication result from the session
        authResult = (AuthenticationResult)Session[authResultString];

        //Show Power BI Panel
        signInStatus.Visible = true;
        signInButton.Visible = false;

        //Set user and token from authentication result
        userLabel.Text = authResult.UserInfo.DisplayableId;
        accessTokenTextbox.Text = authResult.AccessToken;
    }
}
```

## <a name="access-token-for-non-power-bi-users-app-owns-data"></a>Token de acesso para usuários que não têm o Power BI (o aplicativo possui dados)
Normalmente, essa abordagem é usada para aplicativos do tipo ISV em que o aplicativo possui acesso aos dados. Os usuários não serão necessariamente usuários do Power BI e o aplicativo controla a autenticação e o acesso para os usuários finais.

Para essa abordagem, você usará uma única conta *mestre* que é um usuário do Power BI Pro. As credenciais dessa conta são armazenadas no aplicativo. O aplicativo fará a autenticação no Azure AD com essas credenciais armazenadas. O código de exemplo mostrado abaixo foi obtido da [amostra O aplicativo possui dados](https://github.com/guyinacube/PowerBI-Developer-Samples/tree/master/App%20Owns%20Data)

**HomeController.cs**

```
using Microsoft.IdentityModel.Clients.ActiveDirectory;

// Create a user password cradentials.
var credential = new UserPasswordCredential(Username, Password);

// Authenticate using created credentials
var authenticationContext = new AuthenticationContext(AuthorityUrl);
var authenticationResult = await authenticationContext.AcquireTokenAsync(ResourceUrl, ClientId, credential);

if (authenticationResult == null)
{
    return View(new EmbedConfig()
    {
        ErrorMessage = "Authentication Failed."
    });
}

var tokenCredentials = new TokenCredentials(authenticationResult.AccessToken, "Bearer");
```

Para obter informações sobre como usar **await**, consulte [await (referência do C#)](https://docs.microsoft.com/dotnet/csharp/language-reference/keywords/await)

## <a name="next-steps"></a>Próximas etapas
Agora que você tem o token de acesso, chame a API REST do Power BI para inserir o conteúdo. Para obter informações sobre como inserir o conteúdo, consulte [Como inserir os dashboards, relatórios e blocos do Power BI](embedding-content.md#step-2-embed-your-content).

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](http://community.powerbi.com/)

