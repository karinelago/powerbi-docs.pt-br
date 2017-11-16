---
title: "Integrar um bloco do Power BI em um aplicativo para sua organização"
description: "Passo a passo para integrar um bloco em um aplicativo, código de exemplo"
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
ms.date: 10/05/2017
ms.author: asaxton
ms.openlocfilehash: 8527ffb7d9e16bcf55216bc6e0bcd60feec12e16
ms.sourcegitcommit: 99cc3b9cb615c2957dde6ca908a51238f129cebb
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/13/2017
---
# <a name="integrate-a-tile-into-an-app-user-owns-data"></a>Integrar um bloco em um aplicativo (o usuário possui dados)
Saiba como integrar ou inserir um bloco em um aplicativo Web usando chamadas à API REST, junto com a API JavaScript do Power BI durante a inserção para a organização.

![Bloco inserido no aplicativo Web](media/integrate-tile/powerbi-embedded-tile.png)

Para começar este passo a passo, você precisará de uma conta do **Power BI**. Caso você não tenha uma conta, [inscreva-se em uma conta gratuita do Power BI](../service-self-service-signup-for-power-bi.md) ou crie seu próprio [locatário do Azure Active Directory](create-an-azure-active-directory-tenant.md) para fins de teste.

> [!NOTE]
> Você está buscando inserir um bloco para os clientes, usando um embedtoken, em vez disso? Consulte [Integrar um dashboard, bloco ou relatório no aplicativo para os clientes](embed-sample-for-customers.md).
> 
> 

Para integrar um bloco em um aplicativo Web, use a API REST do **Power BI**, ou o SDK do C# do Power BI, e um **token de acesso** de autorização do Azure AD (Active Directory) para obter um bloco. Em seguida, carregue o bloco usando o mesmo token de acesso. A API do **Power BI** fornece acesso programático a determinados recursos do **Power BI**. Para obter mais informações, consulte [Visão geral da API REST do Power BI](https://msdn.microsoft.com/library/dn877544.aspx) e a [API JavaScript do Power BI](https://github.com/Microsoft/PowerBI-JavaScript).

## <a name="download-the-sample"></a>Baixe o exemplo
Este artigo mostra o código usado no [integrate-tile-web-app](https://github.com/Microsoft/PowerBI-Developer-Samples/tree/master/User%20Owns%20Data/integrate-tile-web-app) no GitHub. Para acompanhar esse passo a passo, baixe a amostra.

## <a name="step-1---register-an-app-in-azure-ad"></a>Etapa 1 – registrar um aplicativo no Azure AD
Você precisará registrar seu aplicativo no Azure AD para fazer chamadas à API REST. Para obter mais informações, consulte [Registrar um aplicativo do Azure AD para inserir o conteúdo do Power BI](register-app.md).

Se você baixou o [integrate-tile-web-app](https://github.com/Microsoft/PowerBI-Developer-Samples/tree/master/User%20Owns%20Data/integrate-tile-web-app), use a **ID do Cliente** e o **Segredo do Cliente** obtidos após o registro para que a amostra possa ser autenticada no Azure AD. Para configurar a amostra, altere a **ID do Cliente** e o **Segredo do Cliente** no arquivo *cloud.config*.

![](media/integrate-tile/powerbi-embed-dashboard-register-app4.png)

## <a name="step-2---get-an-access-token-from-azure-ad"></a>Etapa 2 – Obter um token de acesso do Azure AD
No aplicativo, primeiro você precisará obter um **token de acesso** do Azure AD antes de poder fazer chamadas à API REST do Power BI. Para obter mais informações, consulte [Autenticar usuários e obter um token de acesso do Azure AD para o aplicativo do Power BI](get-azuread-access-token.md).

## <a name="step-3---get-a-tile"></a>Etapa 3 – Obter um bloco
Para obter um bloco do **Power BI**, use a operação [Obter Blocos](https://msdn.microsoft.com/library/mt465741.aspx), que obtém uma lista de blocos do **Power BI** de determinado dashboard. Na lista de blocos, obtenha uma ID de bloco e a URL de inserção.

Uma ID de dashboard precisará ser recuperada primeiro antes que você possa obter o bloco. Para obter informações sobre como recuperar um dashboard, consulte [Integrar um dashboard em um aplicativo (o usuário possui dados)](integrate-dashboard.md).

### <a name="get-tiles-using-an-access-token"></a>Obter blocos usando um token de acesso
Com o **token de acesso** recuperado na [etapa 2](#step-2-get-an-access-token-from-azure-ad), chame a operação [Obter Blocos](https://msdn.microsoft.com/library/mt465741.aspx). A operação [Obter Blocos](https://msdn.microsoft.com/library/mt465741.aspx) retorna uma lista de blocos. É possível obter um bloco individual na lista de blocos. Veja abaixo um método completo do C# para obter um bloco. Para obter exemplos de como usar a API REST do Power BI, consulte [API REST do Power BI no APIARY](http://docs.powerbi.apiary.io/).

Para fazer a chamada à API REST, você deve incluir um cabeçalho *Autorização* no formato *Portador {token de acesso}*.

#### <a name="get-tiles-with-the-rest-api"></a>Obter blocos com a API REST
**Default.aspx.cs**

```
using Newtonsoft.Json;

//Get a tile from a dashboard. In this sample, you get the first tile.
protected void GetTile(string dashboardId, int index)
{
    //Configure tiles request
    System.Net.WebRequest request = System.Net.WebRequest.Create(
        String.Format("{0}Dashboards/{1}/Tiles",
        baseUri,
        dashboardId)) as System.Net.HttpWebRequest;

    request.Method = "GET";
    request.ContentLength = 0;
    request.Headers.Add("Authorization", String.Format("Bearer {0}", accessToken.Value));

    //Get tiles response from request.GetResponse()
    using (var response = request.GetResponse() as System.Net.HttpWebResponse)
    {
        //Get reader from response stream
        using (var reader = new System.IO.StreamReader(response.GetResponseStream()))
        {
            //Deserialize JSON string
            PBITiles tiles = JsonConvert.DeserializeObject<PBITiles>(reader.ReadToEnd());

            //Sample assumes at least one Dashboard with one Tile.
            //You could write an app that lists all tiles in a dashboard
            if (tiles.value.Length > 0)
                tileEmbedUrl.Text = tiles.value[index].embedUrl;
        }
    }
}

//Power BI Tiles used to deserialize the Get Tiles response.
public class PBITiles
{
    public PBITile[] value { get; set; }
}
public class PBITile
{
    public string id { get; set; }
    public string title { get; set; }
    public string embedUrl { get; set; }
}
```

#### <a name="get-tiles-using-the-net-sdk"></a>Obter blocos usando o SDK do .NET
Use o SDK do .NET para recuperar uma lista de dashboards, em vez de chamar a API REST diretamente.

```
using Microsoft.IdentityModel.Clients.ActiveDirectory;
using Microsoft.PowerBI.Api.V2;
using Microsoft.PowerBI.Api.V2.Models;

var tokenCredentials = new TokenCredentials(<ACCESS TOKEN>, "Bearer");

// Create a Power BI Client object. It will be used to call Power BI APIs.
using (var client = new PowerBIClient(new Uri(ApiUrl), tokenCredentials))
{
    // Get a list of dashboards your "My Workspace"
    ODataResponseListDashboard tiles = client.Dashboards.GetDashboards();

    // Get a list of dashboards from a group (app workspace)
    ODataResponseListDashboard dashboards = client.Dashboards.GetDashboardsInGroup(groupId);

    Dashboard dashboard = dashboards.Value.FirstOrDefault();

    // Get the first tile from the above dashbaord
    ODataResponseListTile tiles = client.Dashboards.GetTiles(dashboard.Id);

    Tile tile = tiles.Value.FirstOrDefault();
}
```

## <a name="step-4---load-a-tile-using-javascript"></a>Etapa 4 – Carregar um bloco usando o JavaScript
Use o JavaScript para carregar um bloco em um elemento div na página da Web.

**Default.aspx**

```
<!-- Embed Tile-->
<div> 
    <asp:Panel ID="PanelEmbed" runat="server" Visible="true">
        <div>
            <div><b class="step">Step 3</b>: Embed a tile</div>

            <div>Enter an embed url for a tile from Step 2 (starts with https://):</div>
            <input type="text" id="tb_EmbedURL" style="width: 1024px;" />
            <br />
            <input type="button" id="bEmbedTileAction" value="Embed Tile" />
        </div>

        <div id="tileContainer"></div>
    </asp:Panel>
</div>
```

**Site.master**

```
window.onload = function () {
    // client side click to embed a selected tile.
    var el = document.getElementById("bEmbedTileAction");
    if (el.addEventListener) {
        el.addEventListener("click", updateEmbedTile, false);
    } else {
        el.attachEvent('onclick', updateEmbedTile);
    }

    // handle server side post backs, optimize for reload scenarios
    // show embedded tile if all fields were filled in.
    var accessTokenElement = document.getElementById('MainContent_accessTokenTextbox');
    if (accessTokenElement !== null) {
        var accessToken = accessTokenElement.value;
        if (accessToken !== "")
            updateEmbedTile();
    }
};

// update embed tile
function updateEmbedTile() {

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
        type: 'tile',
        accessToken: accessToken,
        embedUrl: embedUrl
    };

    // Grab the reference to the div HTML element that will host the tile.
    var tileContainer = document.getElementById('tileContainer');

    // Embed the tile and display it within the div container.
    var tile = powerbi.embed(tileContainer, config);

    // tile.on will add an event handler which prints to Log window.
    tile.on("error", function (event) {
        var logView = document.getElementById('logView');
        logView.innerHTML = logView.innerHTML + "Error<br/>";
        logView.innerHTML = logView.innerHTML + JSON.stringify(event.detail, null, "  ") + "<br/>";
        logView.innerHTML = logView.innerHTML + "---------<br/>";
    });
}
```

Se você baixou e executou o [integrate-tile-web-app](https://github.com/Microsoft/PowerBI-Developer-Samples/tree/master/User%20Owns%20Data/integrate-tile-web-app), a amostra será parecida com a mostrada abaixo.

![Bloco inserido no aplicativo Web](media/integrate-tile/powerbi-embedded-tile.png)

## <a name="working-with-groups-app-workspaces"></a>Trabalhando com grupos (espaços de trabalho de aplicativo)
Para inserir um bloco de um grupo (espaço de trabalho de aplicativo), obtenha a lista de todos os blocos disponíveis no dashboard do grupo usando a chamada à API REST a seguir. Para obter mais informações sobre essa chamada à API REST, consulte [Obter Blocos](https://msdn.microsoft.com/library/mt465741.aspx). Você precisará ter permissão no grupo à solicitação para retornar os resultados.

```
https://api.powerbi.com/v1.0/myorg/groups/{groupId}/dashboards/{dashboard_id}/tiles
```

A API acima retorna a lista de blocos disponíveis. Cada bloco tem uma propriedade EmbedUrl que já é construída para dar suporte à inserção de grupo.

```
https://app.powerbi.com/embed?dashboardId={dashboard_id}&tileId={tile_id}&groupId={group_id}
```

## <a name="next-steps"></a>Próximas etapas
Um aplicativo de exemplo está disponível no GitHub para você examinar. Para obter mais informações, consulte [integrate-tile-web-app](https://github.com/Microsoft/PowerBI-Developer-Samples/tree/master/User%20Owns%20Data/integrate-tile-web-app).

Mais informações estão disponíveis sobre a API JavaScript em [API JavaScript do Power BI](https://github.com/Microsoft/PowerBI-JavaScript).

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](http://community.powerbi.com/)

