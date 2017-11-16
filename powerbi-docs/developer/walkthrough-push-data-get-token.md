---
title: "Obter um token de acesso de autenticação"
description: "Passo a passo para enviar dados por push - Obter um token de acesso de autenticação"
services: powerbi
documentationcenter: 
author: guyinacube
manager: kfile
backup: 
editor: 
tags: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: get-started-article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 08/10/2017
ms.author: asaxton
ms.openlocfilehash: 068baa78315bfc7e4f7078ed47596a480dbe3765
ms.sourcegitcommit: 284b09d579d601e754a05fba2a4025723724f8eb
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/15/2017
---
# <a name="step-2-get-an-authentication-access-token"></a>Etapa 2: Obter um token de acesso de autenticação
Este artigo faz parte do passo a passo para [enviar dados por push a um conjunto de dados](walkthrough-push-data.md).

Na **etapa 1**, [Registrar o aplicativo no Azure AD](walkthrough-push-data-register-app-with-azure-ad.md), de Enviar dados por push a um conjunto de dados, você registrou um aplicativo cliente no Azure AD. Nesta etapa, você obtém um token de acesso de autenticação. Os aplicativos do Power BI são integrados ao **Azure AD** para fornecer conexão e autorização seguras para seu aplicativo. Você usa um token para autenticar para o **Azure AD** e obter acesso a recursos do Power BI.

Veja como obter um token de acesso de autenticação.

## <a name="get-an-authentication-access-token"></a>Obter um token de acesso de autenticação
> **OBSERVAÇÃO**: antes de começar, lembre-se de seguir as etapas anteriores no passo a passo [enviar dados por push a um conjunto de dados](walkthrough-push-data.md).
> 
> 

1. No Visual Studio 2015, crie um projeto do **Aplicativo de Console** .
2. Instale a [Biblioteca de Autenticação do Azure AD para o pacote NuGet do .NET](https://www.nuget.org/packages/Microsoft.IdentityModel.Clients.ActiveDirectory/). Para obter um token de segurança de autenticação em um aplicativo .NET, use este pacote. Veja como instalar o pacote:
   
     a. No Visual Studio 2015, escolha **Ferramentas** > **Gerenciador de Pacotes NuGet** > **Console do Gerenciador de Pacotes**.
   
     b. No **Console do Gerenciador de Pacotes**, digite Install-Package Microsoft.IdentityModel.Clients.ActiveDirectory -Version 2.21.301221612.
3. Adicione o código a seguir à classe Program {…}.
4. Substitua "{ClientID}" pela **ID do Cliente** que você recebeu ao registrar o aplicativo. Veja [Registrar o aplicativo no Azure AD](walkthrough-push-data-register-app-with-azure-ad.md).
5. Depois de instalar o pacote Microsoft.IdentityModel.Clients.ActiveDirectory, adicione **using Microsoft.IdentityModel.Clients.ActiveDirectory;** a Program.cs.
6. Execute o Aplicativo de Console e faça logon na sua conta do Power BI. Você deve ver uma cadeia de caracteres de token na janela do Console.

**Exemplo de código para obter um token de segurança de autenticação**

Adicione este código a Program {...}.

* Uma variável de token para chamar operações:
  
  ```
  private static string token = string.Empty;
  
  static void Main(string[] args)
  {
  }
  ```
* Em static void Main(string[] args):
  
  ```
  static void Main(string[] args)
  {
    //Get an authentication access token
    token = GetToken();
  }
  ```
* Adicione um método GetToken():

```
       #region Get an authentication access token
       private static string GetToken()
       {
           // TODO: Install-Package Microsoft.IdentityModel.Clients.ActiveDirectory -Version 2.21.301221612
           // and add using Microsoft.IdentityModel.Clients.ActiveDirectory

           //The client id that Azure AD created when you registered your client app.
           string clientID = "{Client_ID}";

           //RedirectUri you used when you register your app.
           //For a client app, a redirect uri gives Azure AD more details on the application that it will authenticate.
           // You can use this redirect uri for your client app
           string redirectUri = "https://login.live.com/oauth20_desktop.srf";

           //Resource Uri for Power BI API
           string resourceUri = "https://analysis.windows.net/powerbi/api";

           //OAuth2 authority Uri
           string authorityUri = "https://login.windows.net/common/oauth2/authorize";

           //Get access token:
           // To call a Power BI REST operation, create an instance of AuthenticationContext and call AcquireToken
           // AuthenticationContext is part of the Active Directory Authentication Library NuGet package
           // To install the Active Directory Authentication Library NuGet package in Visual Studio,
           //  run "Install-Package Microsoft.IdentityModel.Clients.ActiveDirectory" from the nuget Package Manager Console.

           // AcquireToken will acquire an Azure access token
           // Call AcquireToken to get an Azure token from Azure Active Directory token issuance endpoint
           AuthenticationContext authContext = new AuthenticationContext(authorityUri);
           string token = authContext.AcquireToken(resourceUri, clientID, new Uri(redirectUri)).AccessToken;

           Console.WriteLine(token);
           Console.ReadLine();

           return token;
       }

       #endregion
```

Depois de obter um token de autenticação, você pode chamar qualquer operação do Power BI. A próxima etapa mostra como chamar a operação [Criar Conjunto de Dados](https://msdn.microsoft.com/library/mt203562.aspx) para criar um conjunto de dados para enviar dados por push para o dashboard.

A próxima etapa mostra como [criar um conjunto de dados no Power BI](walkthrough-push-data-create-dataset.md).

Apresentamos abaixo a [listagem de código completa](#code).

<a name="code"/>

## <a name="complete-code-listing"></a>Listagem de código completo
    using System;
    using Microsoft.IdentityModel.Clients.ActiveDirectory;

    namespace walkthrough_push_data
    {
        class Program
        {
            private static string token = string.Empty;

            static void Main(string[] args)
            {

                //Get an authentication access token
                token = GetToken();

            }

            #region Get an authentication access token
            private static string GetToken()
            {
                // TODO: Install-Package Microsoft.IdentityModel.Clients.ActiveDirectory -Version 2.21.301221612
                // and add using Microsoft.IdentityModel.Clients.ActiveDirectory

                //The client id that Azure AD created when you registered your client app.
                string clientID = "{Client_ID}";

                //RedirectUri you used when you register your app.
                //For a client app, a redirect uri gives Azure AD more details on the application that it will authenticate.
                // You can use this redirect uri for your client app
                string redirectUri = "https://login.live.com/oauth20_desktop.srf";

                //Resource Uri for Power BI API
                string resourceUri = "https://analysis.windows.net/powerbi/api";

                //OAuth2 authority Uri
                string authorityUri = "https://login.windows.net/common/oauth2/authorize";

                //Get access token:
                // To call a Power BI REST operation, create an instance of AuthenticationContext and call AcquireToken
                // AuthenticationContext is part of the Active Directory Authentication Library NuGet package
                // To install the Active Directory Authentication Library NuGet package in Visual Studio,
                //  run "Install-Package Microsoft.IdentityModel.Clients.ActiveDirectory" from the nuget Package Manager Console.

                // AcquireToken will acquire an Azure access token
                // Call AcquireToken to get an Azure token from Azure Active Directory token issuance endpoint
                AuthenticationContext authContext = new AuthenticationContext(authorityUri);
                string token = authContext.AcquireToken(resourceUri, clientID, new Uri(redirectUri)).AccessToken;

                Console.WriteLine(token);
                Console.ReadLine();

                return token;
            }

            #endregion

        }
    }


[Próxima etapa >](walkthrough-push-data-create-dataset.md)

## <a name="next-steps"></a>Próximas etapas
[Criar um conjunto de dados no Power BI](walkthrough-push-data-create-dataset.md)  
[Registrar um aplicativo com o Azure AD](walkthrough-push-data-register-app-with-azure-ad.md)  
[Biblioteca de Autenticação do Azure AD para o pacote NuGet .NET](https://www.nuget.org/packages/Microsoft.IdentityModel.Clients.ActiveDirectory/)  
[Enviar dados por push a um conjunto de dados do Power BI](walkthrough-push-data.md)  
[Visão geral da API REST do Power BI](overview-of-power-bi-rest-api.md)  
[Referência da API REST do Power BI](https://msdn.microsoft.com/library/mt147898.aspx)  
Mais perguntas? [Experimente a Comunidade do Power BI](http://community.powerbi.com/)

