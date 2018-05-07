---
title: Registrar um aplicativo para inserir o conteúdo do Power BI
description: Saiba como registrar um aplicativo no Azure Active Directory para uso com a inserção de conteúdo do Power BI.
services: powerbi
documentationcenter: ''
author: markingmyname
manager: kfile
backup: ''
editor: ''
tags: ''
qualityfocus: no
qualitydate: ''
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 04/23/2018
ms.author: maghan
ms.openlocfilehash: e3d0e8b98135e232809cd2b5e3fc06827b1f480e
ms.sourcegitcommit: 3f2f254f6e8d18137bae879ddea0784e56b66895
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="register-an-azure-ad-app-to-embed-power-bi-content"></a>Registrar um aplicativo do Azure AD para inserir o conteúdo do Power BI
Saiba como registrar um aplicativo no Azure AD (Azure Active Directory) para uso com a inserção de conteúdo do Power BI.

Registre seu aplicativo com o Azure AD para permitir que seu aplicativo acesse as APIs REST do Power BI. Isso permitirá que você estabeleça uma identidade para seu aplicativo e especifique permissões para recursos REST do Power BI.

> [!IMPORTANT]
> Antes de registrar um aplicativo do Power BI, é necessário um [locatário do Azure Active Directory e um usuário da organização](create-an-azure-active-directory-tenant.md). Se você ainda não se inscreveu no Power BI com um usuário em seu locatário, o registro do aplicativo não será concluído com êxito.
> 
> 

Há duas maneiras de registrar seu aplicativo. A primeira é com a [Ferramenta de Registro de Aplicativo do Power BI](https://dev.powerbi.com/apps/), sendo que também é possível fazê-lo diretamente no Portal do Azure. A Ferramenta de Registro de Aplicativo do Power BI é a opção mais fácil, pois há apenas alguns campos para preencher. Se você desejar fazer alterações ao seu aplicativo, use o Portal do Azure.

## <a name="register-with-the-power-bi-app-registration-tool"></a>Registrar um aplicativo com a Ferramenta de Registro de Aplicativo do Power BI
É necessário registrar seu aplicativo no **Azure Active Directory** para estabelecer uma identidade para o seu aplicativo e especificar permissões para os recursos REST do Power BI. Quando você registra um aplicativo, como um aplicativo de console ou um site da Web, você recebe um identificador usado pelo aplicativo para se identificar aos usuários dos quais eles estão solicitando permissões.

Veja aqui como registrar seu aplicativo com a Ferramenta de Registro de Aplicativo do Power BI:

1. Acesse [dev.powerbi.com/apps](https://dev.powerbi.com/apps).
2. Selecione **Entre com sua conta existente**.
3. Forneça um **Nome do Aplicativo**.
4. A seleção do tipo de aplicativo dependerá do tipo de aplicativo que você estiver usando.
   
   * Use **Aplicativo Web do servidor** para aplicativos Web ou APIs da Web.
   * Use **Aplicativo nativo** para aplicativos executados em dispositivos cliente. ***Você também deverá escolher **Aplicativo nativo** se estiver inserindo o conteúdo para clientes, independentemente de qual é o aplicativo propriamente dito. Isso é válido até mesmo para aplicativos Web.***
5. Insira um valor para **URL de redirecionamento** e **URL da Home Page**. Qualquer URL válida funcionará.
   
    A **URL da Home Page** só estará disponível se você escolher **Aplicativo Web do servidor** para o tipo de aplicativo.
   
    Para as amostras *Inserção para os clientes* e *integrate-dashboard-web-app*, a URL de redirecionamento será `http://localhost:13526/redirect`. Para a amostra de relatório e bloco, a URL de redirecionamento será `http://localhost:13526/`.
6. Escolha as APIs às quais esse aplicativo terá acesso. Para obter mais informações sobre as permissões de acesso do Power BI, veja [Permissões do Power BI](power-bi-permissions.md).
   
    ![](media/register-app/app-registration-apis.png)
7. Selecione **Registrar aplicativo**.
   
    Em seguida, você receberá uma **ID do cliente**. Se você selecionou **Aplicativo Web do servidor**, você também receberá um **Segredo do cliente**. A **ID do Cliente** pode ser recuperada no portal do Azure, mais tarde, se necessário. Se você perder o **Segredo do Cliente**, precisará criar um novo no portal do Azure.

8. Você precisará navegar até o Azure para selecionar **Conceder permissões**.
> [!Note]
    > É necessário ser administrador global no locatário do Azure para concluir isso
>

* Acesse o Azure.
* Pesquise e selecione **Registros do aplicativo**.
* Escolha seu aplicativo.
* Selecione **Configurações**.
* Selecione **Permissões necessárias**:
* Selecione **Serviço do Power BI** para verificar as permissões que você selecionou no site de Registro do aplicativo.
* Selecione **Conceder Permissões**.




Agora é possível usar o aplicativo registrado como parte do aplicativo personalizado para interagir com o serviço do Power BI.

> [!IMPORTANT]
> Se você estiver inserindo o conteúdo para os clientes, precisará configurar permissões adicionais no Portal do Azure. Para obter mais informações, consulte [Aplicar permissões ao aplicativo](#apply-permissions-to-your-application).
> 
> 

## <a name="register-with-the-azure-portal"></a>Registrar com o portal do Azure
Sua outra opção para registrar seu aplicativo é fazer isso diretamente no portal do Azure. Para registrar seu aplicativo, siga estas etapas.

1. Aceite os [Termos da API do Microsoft Power BI](https://powerbi.microsoft.com/api-terms).
2. Entre no [Portal do Azure](https://portal.azure.com).
3. Escolha seu locatário do Azure AD selecionando a sua conta no canto superior direito da página.
4. No painel de navegação à esquerda, escolha **Mais Serviços**, selecione **Registros de Aplicativo** em **Segurança + Identidade** e selecione **Novo registro de aplicativo**.
   
    ![](media/register-app/azuread-new-app-registration.png)
5. Siga os prompts e crie um novo aplicativo.
   
   * Para Aplicativos Web, forneça a URL de Logon, que é a URL base do aplicativo, à qual os usuários podem se conectar, por exemplo, http://localhost:13526.
   * Para aplicativos nativos, forneça um URI de redirecionamento, que usa o Azure AD para retornar respostas de token. Insira um valor específico para seu aplicativo, por exemplo, http://myapplication/redirect

Para obter mais informações sobre como registrar aplicativos no Azure Active Directory, consulte [Integrando aplicativos ao Azure Active Directory](https://docs.microsoft.com/azure/active-directory/develop/active-directory-integrating-applications)

## <a name="how-to-get-the-client-id"></a>Como obter a ID do cliente
Ao registrar um aplicativo, você recebe uma **ID do Cliente**.  A **ID do Cliente** é usada pelo aplicativo para se identificar aos usuários dos quais ele está solicitando permissões.

Eis como obter uma ID do cliente:

1. Entre no [Portal do Azure](https://portal.azure.com).
2. Escolha seu locatário do Azure AD selecionando a sua conta no canto superior direito da página.
3. No painel de navegação esquerdo, escolha **Mais serviços** e selecione **Registros de aplicativo**.
4. Selecione o aplicativo para o qual você deseja recuperar a ID do cliente.
5. Você verá a **ID do Aplicativo** listada como um GUID. Esta é a ID do cliente para o aplicativo.
   
    ![ID do Cliente listada como ID do Aplicativo no registro de aplicativo](media/register-app/powerbi-embedded-app-registration-client-id.png)

## <a name="apply-permissions-to-your-application-within-azure-ad"></a>Aplicar permissões ao aplicativo no Azure AD
> [!IMPORTANT]
> Esta seção se aplica apenas aos aplicativos que estão **inserindo conteúdo para a organização**.
> 
> 

Você precisará habilitar permissões adicionais para o seu aplicativo além do que foi fornecido na página de registro do aplicativo. Você pode fazer isso por meio do portal do Azure AD ou programaticamente.

Você deve estar conectado com a conta *mestre*, usada para a inserção, ou então com uma conta do Administrador Global.

### <a name="using-the-azure-ad-portal"></a>Usando o Portal do Azure AD
1. Navegue até [Registros de aplicativo](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ApplicationsListBlade) no Portal do Azure e selecione o aplicativo que você está usando para inserção.
   
    ![](media/register-app/powerbi-embedded-azuread-registered-apps.png)
2. Selecione **Permissões necessárias** em **Acesso à API**.
   
    ![](media/register-app/powerbi-embedded-azuread-app-required-permissions.png)
3. Selecione **Microsoft Azure Active Directory** e, em seguida, certifique-se de **Acessar o diretório como o usuário conectado** esteja selecionado. Selecione **Salvar**.
   
    ![](media/register-app/powerbi-embedded-azuread-app-permissions01.png)
4. Em **Permissões necessárias**, selecione **Serviço do Power BI (Power BI)**.
   
    ![](media/register-app/powerbi-embedded-azuread-app-permissions03.png)
   
   > [!NOTE]
   > Se você tiver criado o aplicativo diretamente no portal do Azure AD, o **Serviço do Power BI (Power BI)** poderá não estar presente. Se ele não estiver, selecione **+ Adicionar** e **1 Selecionar e API**. Selecione **Serviço do Power BI** na lista de APIs e **Selecionar**.  Se o **serviço do Power BI (Power BI)** não está disponível em **+ Adicionar**, inscreva-se no Power BI com pelo menos um usuário.
   > 
   > 
5. Selecione todas as permissões em **Permissões Delegadas**. Você precisará selecioná-las uma a uma para salvar as seleções. Selecione **Salvar** quando terminar.
   
    ![](media/register-app/powerbi-embedded-azuread-app-permissions04.png)
6. Em **Permissões necessárias**, selecione **Conceder Permissões**.
   
    A ação **Conceder Permissões** é necessária para a *conta mestre*, a fim de evitar prompts de consentimento pelo Azure AD. Se a conta que executar essa ação for um Administrador Global, você concederá permissões para todos os usuários de sua organização a esse aplicativo. Se a conta que executar essa ação for a *conta mestre* e não for um Administrador Global, você concederá permissões apenas para a *conta mestre* a esse aplicativo.
   
    ![Conceder permissões na caixa de diálogo Permissões necessárias](media/register-app/powerbi-embedded-azuread-app-grant-permissions.png)

### <a name="applying-permissions-programmatically"></a>Aplicando permissões de forma programática
1. Você precisará obter as entidades de serviço existentes (usuários) no seu locatário. Para obter informações de como fazer isso, consulte [Obter servicePrincipal](https://developer.microsoft.com/en-us/graph/docs/api-reference/beta/api/serviceprincipal_get).
   
    Você pode chamar a API *Get servicePrincipal* sem {id} e ela obterá todas as entidades de serviço dentro do locatário.
2. Procure por uma entidade de serviço com sua ID de aplicativo cliente como a propriedade **appId**.
3. Crie um novo plano de serviço, se não houver um para o seu aplicativo.
   
    ```
    Post https://graph.microsoft.com/beta/servicePrincipals
    Authorization: Bearer ey..qw
    Content-Type: application/json
    {
    "accountEnabled" : true,
    "appId" : "{App_Client_ID}",
    "displayName" : "{App_DisplayName}"
    }
    ```
4. Conceder Permissão do Aplicativo para a API do PowerBI
   
    ```
    Post https://graph.microsoft.com/beta/OAuth2PermissionGrants
    Authorization: Bearer ey..qw
    Content-Type: application/json
    { 
    "clientId":"{Service_Plan_ID}",
    "consentType":"AllPrincipals",
    "resourceId":"c78b2585-1df6-41de-95f7-dc5aeb7dc98e",
    "scope":"Dataset.ReadWrite.All Dashboard.Read.All Report.Read.All Group.Read Group.Read.All Content.Create Metadata.View_Any Dataset.Read.All Data.Alter_Any",
    "expiryTime":"2018-03-29T14:35:32.4943409+03:00",
    "startTime":"2017-03-29T14:35:32.4933413+03:00"
    }
    ```
5. Conceder Permissão do Aplicativo ao AAD
   
    O valor de **consentType** dependerá do usuário que executar a solicitação. Forneça **AllPrincipals** ou **Principal**. **AllPrincipals** só pode ser usado por um administrador para conceder permissão para todos os usuários. **Principal** é usado para conceder permissão para um usuário específico. 
   
    A concessão de permissão é necessária para a *conta mestre* para evitar prompts de consentimento pelo Azure AD. 
   
    Se você estiver usando um locatário existente e não estiver interessado em conceder permissões em nome de todos os usuários de locatário, poderá conceder permissões substituindo o valor de **contentType** para **Principal**.
   
    ```
    Post https://graph.microsoft.com/beta/OAuth2PermissionGrants
    Authorization: Bearer ey..qw
    Content-Type: application/json
    { 
    "clientId":"{Service_Plan_ID}",
    "consentType":"AllPrincipals",
    "resourceId":"61e57743-d5cf-41ba-bd1a-2b381390a3f1",
    "scope":"User.Read Directory.AccessAsUser.All",
    "expiryTime":"2018-03-29T14:35:32.4943409+03:00",
    "startTime":"2017-03-29T14:35:32.4933413+03:00"
    }
    ```

## <a name="next-steps"></a>Próximas etapas
Agora que você registrou o aplicativo no Azure AD, precisará autenticar usuários no aplicativo. Confira [Autenticar usuários e obter um token de acesso do Azure AD para o aplicativo do Power BI](get-azuread-access-token.md) para saber mais.

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](http://community.powerbi.com/)


