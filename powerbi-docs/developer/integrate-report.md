---
title: Integrar um relatório do Power BI em um aplicativo para sua organização
description: Aprenda a integrar ou inserir um relatório em um aplicativo Web usando APIs do Power BI.
author: markingmyname
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-developer
ms.topic: conceptual
ms.date: 10/05/2017
ms.author: maghan
ms.openlocfilehash: d2fa65587fdbd85aabd429d531b79e9e614d2f49
ms.sourcegitcommit: 638de55f996d177063561b36d95c8c71ea7af3ed
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/17/2018
---
# <a name="integrate-a-report-into-an-app-for-your-organization"></a>Integrar um relatório em um aplicativo para sua organização
Saiba como integrar ou inserir um relatório em um aplicativo Web usando chamadas à API REST, junto com a API JavaScript do Power BI durante a inserção para a organização.

![Amostra de relatório inserido](media/integrate-report/powerbi-embedded-report.png)

Para começar este passo a passo, você precisará de uma conta do **Power BI**. Caso você não tenha uma conta, [inscreva-se em uma conta gratuita do Power BI](../service-self-service-signup-for-power-bi.md) ou crie seu próprio [locatário do Azure Active Directory](create-an-azure-active-directory-tenant.md) para fins de teste.

> [!NOTE]
> Você está buscando inserir um relatório para os clientes, usando um embedtoken, em vez disso? Consulte [Integrar um dashboard, bloco ou relatório no aplicativo para os clientes](embed-sample-for-customers.md).
> 
> 

Para integrar um relatório em um aplicativo Web, use a API REST do **Power BI** ou o SDK do C# do Power BI e um **token de acesso** de autorização do Azure AD (Active Directory) para obter um relatório. Em seguida, carregue o relatório usando o mesmo token de acesso. A API do **Power BI** fornece acesso programático a determinados recursos do **Power BI**. Para obter mais informações, consulte [Visão geral da API REST do Power BI](https://msdn.microsoft.com/library/dn877544.aspx) e a [API JavaScript do Power BI](https://github.com/Microsoft/PowerBI-JavaScript).

## <a name="download-the-sample"></a>Baixe o exemplo
Este artigo mostra o código usado no [integrate-report-web-app](https://github.com/Microsoft/PowerBI-Developer-Samples/tree/master/User%20Owns%20Data/integrate-report-web-app) no GitHub. Para acompanhar esse passo a passo, baixe a amostra.

## <a name="step-1---register-an-app-in-azure-ad"></a>Etapa 1 – registrar um aplicativo no Azure AD
Você precisará registrar seu aplicativo no Azure AD para fazer chamadas à API REST. Para obter mais informações, consulte [Registrar um aplicativo do Azure AD para inserir o conteúdo do Power BI](register-app.md).

Se você baixou o [integrate-report-web-app](https://github.com/Microsoft/PowerBI-Developer-Samples/tree/master/User%20Owns%20Data/integrate-report-web-app), use a **ID do Cliente** e o **Segredo do Cliente** obtidos após o registro para que a amostra possa ser autenticada no Azure AD. Para configurar a amostra, altere a **ID do Cliente** e o **Segredo do Cliente** no arquivo *cloud.config*.

![](media/integrate-report/powerbi-embed-dashboard-register-app4.png)

## <a name="step-2---get-an-access-token-from-azure-ad"></a>Etapa 2 – Obter um token de acesso do Azure AD
No aplicativo, primeiro você precisará obter um **token de acesso** do Azure AD antes de poder fazer chamadas à API REST do Power BI. Para obter mais informações, consulte [Autenticar usuários e obter um token de acesso do Azure AD para o aplicativo do Power BI](get-azuread-access-token.md).

## <a name="step-3---get-a-report"></a>Etapa 3 – Obter um relatório
Para obter um relatório do **Power BI**, você usa a operação [Obter Relatórios](https://msdn.microsoft.com/library/mt634543.aspx) que obtém uma lista de relatórios do **Power BI**. Na lista de relatórios, obtenha uma ID de relatório.

### <a name="get-reports-using-an-access-token"></a>Obter relatórios usando um token de acesso
Com o **token de acesso** recuperado na [etapa 2](#step-2-get-an-access-token-from-azure-ad), chame a operação [Obter Relatórios](https://msdn.microsoft.com/library/mt634543.aspx). A operação [Obter Relatórios](https://msdn.microsoft.com/library/mt634543.aspx) retorna uma lista de relatórios. É possível obter um relatório individual na lista de relatórios. Veja abaixo um método do C# completo para obter um relatório. 

Para fazer a chamada à API REST, você deve incluir um cabeçalho *Autorização* no formato *Portador {token de acesso}*.

#### <a name="get-reports-with-the-rest-api"></a>Obter relatórios com a API REST
**Default.aspx.cs**

```
using Newtonsoft.Json;

//Get a Report. In this sample, you get the first Report.
protected void GetReport(int index)
{
    //Configure Reports request
    System.Net.WebRequest request = System.Net.WebRequest.Create(
        String.Format("{0}/Reports",
        baseUri)) as System.Net.HttpWebRequest;

    request.Method = "GET";
    request.ContentLength = 0;
    request.Headers.Add("Authorization", String.Format("Bearer {0}", accessToken.Value));

    //Get Reports response from request.GetResponse()
    using (var response = request.GetResponse() as System.Net.HttpWebResponse)
    {
        //Get reader from response stream
        using (var reader = new System.IO.StreamReader(response.GetResponseStream()))
        {
            //Deserialize JSON string
            PBIReports Reports = JsonConvert.DeserializeObject<PBIReports>(reader.ReadToEnd());

            //Sample assumes at least one Report.
            //You could write an app that lists all Reports
            if (Reports.value.Length > 0)
            {
                var report = Reports.value[index];

                txtEmbedUrl.Text = report.embedUrl;
                txtReportId.Text = report.id;
                txtReportName.Text = report.name;
            }
        }
    }
}

//Power BI Reports used to deserialize the Get Reports response.
public class PBIReports
{
    public PBIReport[] value { get; set; }
}
public class PBIReport
{
    public string id { get; set; }
    public string name { get; set; }
    public string webUrl { get; set; }
    public string embedUrl { get; set; }
}
```

#### <a name="get-reports-using-the-net-sdk"></a>Obter relatórios usando o SDK do .NET
Use o SDK do .NET para recuperar uma lista de relatórios, em vez de chamar a API REST diretamente.

```
using Microsoft.IdentityModel.Clients.ActiveDirectory;
using Microsoft.PowerBI.Api.V2;
using Microsoft.PowerBI.Api.V2.Models;

var tokenCredentials = new TokenCredentials(<ACCESS TOKEN>, "Bearer");

// Create a Power BI Client object. It will be used to call Power BI APIs.
using (var client = new PowerBIClient(new Uri(ApiUrl), tokenCredentials))
{
    // Get the first report all reports in that workspace
    ODataResponseListReport reports = client.Reports.GetReports();

    Report report = reports.Value.FirstOrDefault();

    var embedUrl = report.EmbedUrl;
}
```

## <a name="step-4---load-a-report-using-javascript"></a>Etapa 4 – Carregar um relatório usando o JavaScript
Use o JavaScript para carregar um relatório em um elemento div na página da Web.

**Default.aspx**

```
<!-- Embed Report-->
<div> 
    <asp:Panel ID="PanelEmbed" runat="server" Visible="true">
        <div>
            <div><b class="step">Step 3</b>: Embed a report</div>

            <div>Enter an embed url for a report from Step 2 (starts with https://):</div>
            <input type="text" id="tb_EmbedURL" style="width: 1024px;" />
            <br />
            <input type="button" id="bEmbedReportAction" value="Embed Report" />
        </div>

        <div id="reportContainer"></div>
    </asp:Panel>
</div>
```

**Site.master**

```
window.onload = function () {
    // client side click to embed a selected report.
    var el = document.getElementById("bEmbedReportAction");
    if (el.addEventListener) {
        el.addEventListener("click", updateEmbedReporte, false);
    } else {
        el.attachEvent('onclick', updateEmbedReport);
    }

    // handle server side post backs, optimize for reload scenarios
    // show embedded report if all fields were filled in.
    var accessTokenElement = document.getElementById('MainContent_accessTokenTextbox');
    if (accessTokenElement !== null) {
        var accessToken = accessTokenElement.value;
        if (accessToken !== "")
            updateEmbedReport();
    }
};

// update embed report
function updateEmbedReport() {

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
        type: 'report',
        accessToken: accessToken,
        embedUrl: embedUrl
    };

    // Grab the reference to the div HTML element that will host the report.
    var reportContainer = document.getElementById('reportContainer');

    // Embed the report and display it within the div container.
    var report = powerbi.embed(reportContainer, config);

    // report.on will add an event handler which prints to Log window.
    report.on("error", function (event) {
        var logView = document.getElementById('logView');
        logView.innerHTML = logView.innerHTML + "Error<br/>";
        logView.innerHTML = logView.innerHTML + JSON.stringify(event.detail, null, "  ") + "<br/>";
        logView.innerHTML = logView.innerHTML + "---------<br/>";
    });
}
```

Se você baixou e executou o [integrate-report-web-app](https://github.com/Microsoft/PowerBI-Developer-Samples/tree/master/User%20Owns%20Data/integrate-report-web-app), a amostra será parecida com a mostrada abaixo.

![Amostra de relatório inserido](media/integrate-report/powerbi-embedded-report.png)

## <a name="working-with-groups-app-workspaces"></a>Trabalhando com grupos (espaços de trabalho de aplicativo)
Para inserir um relatório de um grupo (espaço de trabalho de aplicativo), obtenha a lista de todos os relatórios disponíveis no dashboard do grupo usando a chamada à API REST a seguir. Para obter mais informações sobre essa chamada à API REST, consulte [Obter Relatórios](https://msdn.microsoft.com/library/mt634543.aspx). Você precisará ter permissão no grupo à solicitação para retornar os resultados.

```
https://api.powerbi.com/v1.0/myorg/groups/{group_id}/reports
```

A API acima retorna a lista de relatórios disponíveis. Cada relatório tem uma propriedade EmbedUrl que já é construída para dar suporte à inserção de grupo.

```
https://app.powerbi.com/reportEmbed?reportId={report_id}&groupId={group_id}
```

## <a name="next-steps"></a>Próximas etapas
Um aplicativo de exemplo está disponível no GitHub para você examinar. Para obter mais informações, consulte [integrate-report-web-app](https://github.com/Microsoft/PowerBI-Developer-Samples/tree/master/User%20Owns%20Data/integrate-report-web-app).

Mais informações estão disponíveis sobre a API JavaScript em [API JavaScript do Power BI](https://github.com/Microsoft/PowerBI-JavaScript).

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](http://community.powerbi.com/)

