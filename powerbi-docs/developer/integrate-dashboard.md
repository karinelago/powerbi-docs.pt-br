---
title: "Integrar um dashboard do Power BI em um aplicativo para sua organização"
description: Aprenda a integrar ou inserir um dashboard em um aplicativo Web usando APIs do Power BI.
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
ms.topic: get-started-article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 02/13/2018
ms.author: maghan
ms.openlocfilehash: e85b745798fd33ffbb5061f4c156054d2218bfb1
ms.sourcegitcommit: 2ceea44d3606c15b57142c37649c9d481ec4becc
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/15/2018
---
# <a name="integrate-a-dashboard-into-an-app-for-your-organization"></a>Integrar um dashboard do Power BI em um aplicativo para sua organização
Saiba como integrar ou inserir um dashboard em um aplicativo Web usando chamadas à API REST, junto com a API JavaScript do Power BI durante a inserção para a organização.

![Dashboard inserido](media/integrate-dashboard/powerbi-embed-dashboard.png)

Para começar este passo a passo, você precisará de uma conta do **Power BI**. Caso você não tenha uma conta, [inscreva-se em uma conta gratuita do Power BI](../service-self-service-signup-for-power-bi.md) ou crie seu próprio [locatário do Azure Active Directory](create-an-azure-active-directory-tenant.md) para fins de teste.

> [!NOTE]
> Você está buscando inserir um dashboard para os clientes, usando um embedtoken, em vez disso? Consulte [Integrar um dashboard, bloco ou relatório no aplicativo para os clientes](embed-sample-for-customers.md).
> 
> 

Para integrar um dashboard em um aplicativo Web, use a API REST do **Power BI** ou o SDK do C# do Power BI e um **token de acesso** de autorização do Azure AD (Active Directory) para obter um dashboard. Em seguida, carregue o dashboard usando o mesmo token de acesso. A API do **Power BI** fornece acesso programático a determinados recursos do **Power BI**. Para obter mais informações, consulte [Visão geral da API REST do Power BI](https://msdn.microsoft.com/library/dn877544.aspx) e a [API JavaScript do Power BI](https://github.com/Microsoft/PowerBI-JavaScript).

## <a name="download-the-sample"></a>Baixe o exemplo
Este artigo mostra o código usado no [integrate-dashboard-web-app](https://github.com/Microsoft/PowerBI-Developer-Samples/tree/master/User%20Owns%20Data/integrate-dashboard-web-app) no GitHub. Para acompanhar esse passo a passo, baixe a amostra.

## <a name="step-1---register-an-app-in-azure-ad"></a>Etapa 1 – registrar um aplicativo no Azure AD
Você precisará registrar seu aplicativo no Azure AD para fazer chamadas à API REST. Para obter mais informações, consulte [Registrar um aplicativo do Azure AD para inserir o conteúdo do Power BI](register-app.md).

Se você baixou a [amostra Integrar um dashboard](https://github.com/Microsoft/PowerBI-Developer-Samples/tree/master/User%20Owns%20Data/integrate-dashboard-web-app), use a **ID do Cliente** e o **Segredo do Cliente** obtidos, após o registro, para que a amostra seja autenticada no Azure AD. Para configurar a amostra, altere a **ID do Cliente** e o **Segredo do Cliente** no arquivo *cloud.config*.

![](media/integrate-dashboard/powerbi-embed-dashboard-register-app4.png)

## <a name="step-2---get-an-access-token-from-azure-ad"></a>Etapa 2 – Obter um token de acesso do Azure AD
No aplicativo, primeiro você precisará obter um **token de acesso** do Azure AD antes de poder fazer chamadas à API REST do Power BI. Para obter mais informações, consulte [Autenticar usuários e obter um token de acesso do Azure AD para o aplicativo do Power BI](get-azuread-access-token.md).

## <a name="step-3---get-a-dashboard"></a>Etapa 3 – Obter um dashboard
Para obter um dashboard do **Power BI**, você usa a operação [Obter Dashboards](https://msdn.microsoft.com/library/mt465739.aspx) que obtém uma lista de dashboards do **Power BI**. Na lista de dashboards, é possível obter uma ID de dashboard.

![](media/integrate-dashboard/powerbi-embed-dashboard-get-dashboards.png)

### <a name="get-dashboards-using-an-access-token"></a>Obter dashboards usando um token de acesso
Com o **token de acesso** recuperado na [etapa 2](#step-2-get-an-access-token-from-azure-ad), chame a operação [Obter Dashboards](https://msdn.microsoft.com/library/mt465739.aspx). A operação [Obter Dashboards](https://msdn.microsoft.com/library/mt465739.aspx) retorna uma lista de dashboards. É possível obter um dashboard individual na lista de dashboards. Veja abaixo um método do C# completo para obter um dashboard. 

Para fazer a chamada à API REST, você deve incluir um cabeçalho *Autorização* no formato *Portador {token de acesso}*.

#### <a name="get-dashboards-with-the-rest-api"></a>Obter dashboards com a API REST
**Default.aspx.cs**

```
protected void getDashboardsButton_Click(object sender, EventArgs e)
{
    string responseContent = string.Empty;

    //Configure dashboards request
    System.Net.WebRequest request = System.Net.WebRequest.Create(String.Format("{0}dashboards", baseUri)) as System.Net.HttpWebRequest;
    request.Method = "GET";
    request.ContentLength = 0;
    request.Headers.Add("Authorization", String.Format("Bearer {0}", authResult.AccessToken));

    //Get dashboards response from request.GetResponse()
    using (var response = request.GetResponse() as System.Net.HttpWebResponse)
    {
        //Get reader from response stream
        using (var reader = new System.IO.StreamReader(response.GetResponseStream()))
        {
            responseContent = reader.ReadToEnd();

            //Deserialize JSON string
            PBIDashboards PBIDashboards = JsonConvert.DeserializeObject<PBIDashboards>(responseContent);

            if (PBIDashboards != null)
            {
                var gridViewDashboards = PBIDashboards.value.Select(dashboard => new {
                    Id = dashboard.id,
                    DisplayName = dashboard.displayName,
                    EmbedUrl = dashboard.embedUrl
                });

                this.GridView1.DataSource = gridViewDashboards;
                this.GridView1.DataBind();
            }
        }
    }
}

//Power BI Dashboards used to deserialize the Get Dashboards response.
public class PBIDashboards
{
    public PBIDashboard[] value { get; set; }
}
public class PBIDashboard
{
    public string id { get; set; }
    public string displayName { get; set; }
    public string embedUrl { get; set; }
    public bool isReadOnly { get; set; }
}
```

#### <a name="get-dashboards-using-the-net-sdk"></a>Obter dashboards usando o SDK do .NET
Use o SDK do .NET para recuperar uma lista de painéis em vez de chamar a API REST diretamente.

```
using Microsoft.IdentityModel.Clients.ActiveDirectory;
using Microsoft.PowerBI.Api.V2;
using Microsoft.PowerBI.Api.V2.Models;

var tokenCredentials = new TokenCredentials(<ACCESS TOKEN>, "Bearer");

// Create a Power BI Client object. It will be used to call Power BI APIs.
using (var client = new PowerBIClient(new Uri(ApiUrl), tokenCredentials))
{
    // Get a list of dashboards your "My Workspace"
    ODataResponseListDashboard dashboards = client.Dashboards.GetDashboards();

    // Get a list of dashboards from a group (app workspace)
    ODataResponseListDashboard dashboards = client.Dashboards.GetDashboardsInGroup(groupId);

    Dashboard dashboard = dashboards.Value.FirstOrDefault();

    var embedUrl = dashboard.EmbedUrl
}
```

## <a name="step-4---load-a-dashboard-using-javascript"></a>Etapa 4 – Carregar um dashboard usando o JavaScript
Você pode usar o JavaScript para carregar um dashboard em um elemento div na sua página da Web.

**Default.aspx**

```
<!-- Embed Dashboard-->
<div> 
    <asp:Panel ID="PanelEmbed" runat="server" Visible="true">
        <div>
            <div><b class="step">Step 3</b>: Embed a dashboard</div>

            <div>Enter an embed url for a dashboard from Step 2 (starts with https://):</div>
            <input type="text" id="tb_EmbedURL" style="width: 1024px;" />
            <br />
            <input type="button" id="bEmbedDashboardAction" value="Embed Dashboard" />
        </div>

        <div id="dashboardContainer"></div>
    </asp:Panel>
</div>
```

**Site.master**

```
window.onload = function () {
    // client side click to embed a selected dashboard.
    var el = document.getElementById("bEmbedDashboardAction");
    if (el.addEventListener) {
        el.addEventListener("click", updateEmbedDashboard, false);
    } else {
        el.attachEvent('onclick', updateEmbedDashboard);
    }

    // handle server side post backs, optimize for reload scenarios
    // show embedded dashboard if all fields were filled in.
    var accessTokenElement = document.getElementById('MainContent_accessTokenTextbox');
    if (accessTokenElement !== null) {
        var accessToken = accessTokenElement.value;
        if (accessToken !== "")
            updateEmbedDashboard();
    }
};

// update embed dashboard
function updateEmbedDashboard() {

    // check if the embed url was selected
    var embedUrl = document.getElementById('tb_EmbedURL').value;
    if (embedUrl === "")
        return;

    // get the access token.
    accessToken = document.getElementById('MainContent_accessTokenTextbox').value;

    // Embed configuration used to describe the what and how to embed.
    // This object is used when calling powerbi.embed.
    // You can find more information at https://github.com/Microsoft/PowerBI-JavaScript/wiki/Embed-Configuration-Details.
    var config = {
        type: 'dashboard',
        accessToken: accessToken,
        embedUrl: embedUrl
    };

    // Grab the reference to the div HTML element that will host the dashboard.
    var dashboardContainer = document.getElementById('dashboardContainer');

    // Embed the dashboard and display it within the div container.
    var dashboard = powerbi.embed(dashboardContainer, config);

    // dashboard.on will add an event handler which prints to Log window.
    dashboard.on("tileClicked", function (event) {
        var logView = document.getElementById('logView');
        logView.innerHTML = logView.innerHTML + "Tile Clicked<br/>";
        logView.innerHTML = logView.innerHTML + JSON.stringify(event.detail, null, "  ") + "<br/>";
        logView.innerHTML = logView.innerHTML + "---------<br/>";
    });

    // dashboard.on will add an event handler which prints to Log window.
    dashboard.on("error", function (event) {
        var logView = document.getElementById('logView');
        logView.innerHTML = logView.innerHTML + "Error<br/>";
        logView.innerHTML = logView.innerHTML + JSON.stringify(event.detail, null, "  ") + "<br/>";
        logView.innerHTML = logView.innerHTML + "---------<br/>";
    });
}
```

Se você baixou e executou a [amostra Integrar um painel](https://github.com/Microsoft/PowerBI-Developer-Samples/tree/master/User%20Owns%20Data/integrate-dashboard-web-app), a amostra será parecida com a mostrada abaixo.

![](media/integrate-dashboard/powerbi-embed-dashboard.png)

## <a name="tile-clicked-events"></a>Eventos clicados em bloco
Talvez você tenha observado no exemplo acima que é possível manipular eventos quando o bloco é clicado no dashboard. Para obter mais informações sobre eventos, consulte [Manipulação de eventos na API de JavaScript](https://github.com/Microsoft/PowerBI-JavaScript/wiki/Handling-Events).

```
// dashboard.on will add an event handler which prints to Log window.
dashboard.on("tileClicked", function (event) {
    var logView = document.getElementById('logView');
    logView.innerHTML = logView.innerHTML + "Tile Clicked<br/>";
    logView.innerHTML = logView.innerHTML + JSON.stringify(event.detail, null, "  ") + "<br/>";
    logView.innerHTML = logView.innerHTML + "---------<br/>";
});

// dashboard.on will add an event handler which prints to Log window.
dashboard.on("error", function (event) {
    var logView = document.getElementById('logView');
    logView.innerHTML = logView.innerHTML + "Error<br/>";
    logView.innerHTML = logView.innerHTML + JSON.stringify(event.detail, null, "  ") + "<br/>";
    logView.innerHTML = logView.innerHTML + "---------<br/>";
});
```

Se você baixou e executou o [Exemplo de integrar um dashboard](https://github.com/Microsoft/PowerBI-Developer-Samples/tree/master/PowerBI.com%20Integrate/integrate-dashboard-web-app), clicar em um bloco produzirá um texto abaixo do dashboard. O texto será semelhante ao seguinte. Isso permitirá registrar que um bloco recebeu um clique e, em seguida, conduzir o usuário para o local apropriado.

```
Tile Clicked
{ "event": "TileClick", "reportEmbedUrl": "", "navigationUrl": "https://app.powerbi.com/dashboards/fcff76f9-15ff-4a8e-8242-275ac9c25b90/qna?q=count%20of%20new%20hires%20from%20July%202014%20to%20December%202014", "tileId": "0e99b45c-9b53-4920-b239-cee7d37d2369" }
---------
Tile Clicked
{ "event": "TileClick", "reportEmbedUrl": "https://app.powerbi.com/reportEmbed?reportId=ab199308-80b1-4626-9823-43a84623bd9c", "navigationUrl": "https://app.powerbi.com/reports/ab199308-80b1-4626-9823-43a84623bd9c/ReportSection1", "tileId": "ffc30447-674a-4511-944f-79e182d719de", "pageName": "ReportSection1" }
---------
```

## <a name="working-with-groups-app-workspaces"></a>Trabalhando com grupos (espaços de trabalho de aplicativo)
Para inserir um dashboard por meio de um grupo (espaço de trabalho de aplicativo), obtenha a lista de todos os dashboards disponíveis em um grupo usando a chamada à API REST a seguir. Para obter mais informações sobre essa chamada à API REST, consulte [Obter painéis](https://msdn.microsoft.com/library/mt465739.aspx). Você precisará ter permissão no grupo à solicitação para retornar os resultados.

```
https://api.powerbi.com/v1.0/myorg/groups/{groupId}/dashboards
```

A API acima retorna a lista de painéis disponíveis. Cada painel tem uma propriedade EmbedUrl que já é construída para oferecer suporte a inserção de grupo.

```
https://app.powerbi.com/dashboardEmbed?dashboardId={dashboardId}&groupId={groupId}
```

## <a name="limitations"></a>Limitações
* Os usuários finais que acessam os dashboards inseridos devem ter uma conta do Power BI e ter acesso ao dashboard. Eles possuem o dashboard ou o dashboard foi compartilhado com o usuário.
* Atualmente não há suporte para P e R nos painéis inseridos.
* Como uma limitação temporária, ao compartilhar um painel com grupos de segurança, o usuário precisa primeiro acessar os painéis no PowerBI.com antes de vê-lo inserido.

## <a name="next-steps"></a>Próximas etapas
Um aplicativo de exemplo está disponível no GitHub para você examinar. Os exemplos acima baseiam-se nessa amostra. Para obter mais informações, consulte [integrate-dashboard-web-app](https://github.com/Microsoft/PowerBI-Developer-Samples/tree/master/User%20Owns%20Data/integrate-dashboard-web-app).

Mais informações estão disponíveis sobre a API JavaScript em [API JavaScript do Power BI](https://github.com/Microsoft/PowerBI-JavaScript).

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](http://community.powerbi.com/)

