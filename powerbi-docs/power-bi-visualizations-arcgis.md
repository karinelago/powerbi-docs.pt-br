---
title: Interagindo com um mapa do ArcGIS que foi compartilhado com você
description: 'Usando o mapa do ArcGis no modo de exibição de leitura '
author: mihart
manager: kfile
ms.reviewer: ''
tags: power bi, service, desktop, mobile
featuredvideoid: ''
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 02/28/2018
ms.author: mihart
ms.openlocfilehash: 2a5e654062c056308431b2a94f7e2da4e3d46d17
ms.sourcegitcommit: 80d6b45eb84243e801b60b9038b9bff77c30d5c8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34240873"
---
# <a name="interacting-with-arcgis-maps-in-power-bi"></a>Interagindo com mapas do ArcGIS no Power BI
Este tópico foi escrito do ponto de vista de uma pessoa que está *consumindo* um mapa do ArcGIS no serviço do Power BI, no Desktop ou em um dispositivo móvel. Depois que um criador compartilha um mapa do ArcGIS com você, há muitas formas de interagir com o mapa.  Para saber mais sobre como criar um mapa do ArcGIS, consulte [Tutorial de mapas do ArcGIS pelo ESRI](power-bi-visualization-arcgis.md).

A combinação de mapas do ArcGIS e do Power BI leva o mapeamento para além da apresentação de pontos em um mapa, para um nível totalmente novo. As opções disponíveis para mapas base, tipos de localização, temas, estilos de símbolo e camadas de referência criam visualizações de mapa informativas e impressionantes. A combinação de camadas de dados autoritativas (como dados de censo) em um mapa com análise espacial transmite uma compreensão mais profunda dos dados na visualização.

> [!TIP]
> GIS significa Geographic Information Science (Ciência de Informações Geográficas).
> 

O exemplo que estamos usando é o mesmo mapa do ArcGIS criado no [tutorial de mapas do ArcGIS pelo ESRI](power-bi-visualization-arcgis.md). Ele analisa as vendas do ano passado por cidade e usa um mapa base de ruas, símbolos de bolha para representar o tamanho e uma camada de referência para a renda familiar média. O mapa contém 3 marcadores e um raio do tempo de viagem (em roxo).

![](media/power-bi-visualizations-arcgis/power-bi-arcgis-esri-new.png)

> [!TIP]
> Visite a [página do ESRI no Power BI](https://www.esri.com/powerbi) para ver vários exemplos e ler depoimentos. E, em seguida, consulte a [Página de Introdução do ArcGIS Maps para o Power BI](https://doc.arcgis.com/en/maps-for-powerbi/get-started/about-maps-for-power-bi.htm) no ESRI.
> 
> 

<br/>

## <a name="user-consent"></a>Consentimento do usuário
Na primeira vez que um colega compartilhar um mapa do ArcGIS com você, o Power BI exibirá um prompt. O ArcGIS Maps for Power BI é fornecido pela ESRI (www.esri.com) e o uso do ArcGIS Maps for Power BI está sujeito aos termos e à política de privacidade da Esri. Os usuários do Power BI que desejam usar os visuais dos Mapas do ArcGIS para o Power BI precisarão aceitar a caixa de diálogo de consentimento.

## <a name="selection-tools"></a>Ferramentas de seleção
O ArcGIS Maps para Power BI permite três modos de seleção. No máximo, 250 pontos de dados podem ser selecionados por vez.

![](media/power-bi-visualizations-arcgis/power-bi-esri-selection-tools2.png)

![](media/power-bi-visualizations-arcgis/power-bi-esri-selection-single2.png) Selecionar pontos de dados individuais.

![](media/power-bi-visualizations-arcgis/power-bi-esri-selection-marquee2.png) Desenha um retângulo no mapa e seleciona os pontos de dados contidos. Use CTRL para selecionar mais de uma área retangular.

![](media/power-bi-visualizations-arcgis/power-bi-esri-selection-reference-layer2.png) Permite que os limites ou polígonos nas camadas de referência sejam usados para selecionar os pontos de dados contidos.

<br/>

## <a name="interacting-with-an-arcgis-map"></a>Interagindo com um mapa do ArcGIS
Os recursos disponíveis dependem se você é o *criador* (a pessoa que fez o mapa) ou o *consumidor* (alguém compartilhou um mapa do ArcGIS com você). Se você estiver interagindo com um mapa do ArcGIS como consumidor (também conhecido como [modo de exibição de Leitura](service-reading-view-and-editing-view.md)), estas serão as ações disponíveis para você.

* Assim como ocorre com outros tipos de visualização, você pode [fixar nos dashboards](service-dashboard-pin-tile-from-report.md), [exibir](service-reports-show-data.md) e/ou [exportar os dados subjacentes](power-bi-visualization-export-data.md) e ver o mapa no [Modo de foco](service-focus-mode.md) e em [Tela inteira](service-fullscreen-mode.md).    
* Expanda o painel **Filtros** para explorar o mapa usando filtros. Quando você fecha o relatório, os filtros aplicados não são salvos.    
    ![](media/power-bi-visualizations-arcgis/power-bi-filter-newer.png)  
* Se o mapa tiver uma camada de referência, selecione as localizações para exibir os detalhes em uma dica de ferramenta. Aqui, selecionamos o Condado Adams e vemos os dados da camada de referência de renda familiar média que o criador adicionou ao mapa.
  
    ![](media/power-bi-visualizations-arcgis/power-bi-reference-layer.png)  
  
    Nesse caso, também obtemos um gráfico. Selecione uma barra no gráfico para examinar os dados. Aqui, vemos que 79 residências no condado Adams ganham US$ 200.000 ou mais.
  
    ![](media/power-bi-visualizations-arcgis/power-bi-tooltip-chart.png)
  
    Selecione a seta para exibir os outros gráficos.
* Focalize os símbolos de localização do mapa base para exibir os detalhes em uma dica de ferramenta.     
  ![](media/power-bi-visualizations-arcgis/power-bi-arcgis-hover.png)
  
  > [!TIP]
  > Talvez você precise ampliar para selecionar uma localização específica.  Caso contrário, se houver localizações sobrepostas, o Power BI poderá apresentar mais de uma dica de ferramenta por vez. Selecionar as setas para mover entre as dicas de ferramentas
  > 
  > ![](media/power-bi-visualizations-arcgis/power-bi-3-screens.png)
  > 
  > 
* Se o criador tiver adicionado uma camada Infográficos ao mapa do ArcGIS, você verá dados adicionais exibidos no canto superior direito do mapa.  Por exemplo, aqui, o criador do mapa adicionou “Filhos menores de 14”.
  
    ![](media/power-bi-visualizations-arcgis/power-bi-demographics.png)

## <a name="considerations-and-limitations"></a>Considerações e limitações
Os Mapas do ArcGIS para o Power BI estão disponíveis nos seguintes serviços e aplicativos:

<table>
<tr><th>Serviço/Aplicativo</th><th>Disponibilidade</th></tr>
<tr>
<td>Power BI Desktop</td>
<td>Sim</td>
</tr>
<tr>
<td>Serviço do Power BI (app.powerbi.com)</td>
<td>Sim</td>
</tr>
<tr>
<td>Aplicativos móveis do Power BI</td>
<td>Sim</td>
</tr>
<tr>
<td>Publicar na Web do Power BI</td>
<td>Não</td>
</tr>
<tr>
<td>Power BI Embedded</td>
<td>Não</td>
</tr>
<tr>
<td>Incorporação do serviço do Power BI (PowerBI.com)</td>
<td>Não</td>
</tr>
</table>

**Como os ArcGIS Maps for Power BI funcionam juntos?**
O ArcGIS Maps for Power BI é fornecido pela Esri (www.esri.com). O uso do ArcGIS Maps for Power BI está sujeito aos [termos](https://go.microsoft.com/fwlink/?LinkID=8263222) e à [política de privacidade](https://go.microsoft.com/fwlink/?LinkID=826323) da Esri. Os usuários do Power BI que queiram usar os visuais do ArcGIS Maps for Power BI precisam aceitar a caixa de diálogo de consentimento (consulte Consentimento do usuário para obter detalhes).  Usar o ArcGIS Maps for Power BI da Esri está sujeito aos Termos e à Política de Privacidade da Esri que também estão vinculados à caixa de diálogo de consentimento. Cada usuário deve consentir antes de usar o ArcGIS Maps for Power BI pela primeira vez. Depois que o usuário aceitar o consentimento, os dados vinculados ao visual são enviados aos serviços da Esri pelo menos para geocodificação, que significa transformar informações de localização em informações de latitude e longitude que podem ser representadas em um mapa. Você deve considerar que os dados associados à visualização de dados podem ser enviados aos serviços da Esri. A Esri fornece serviços como mapas de base, análise espacial, geocodificação, etc. O visual do ArcGIS Maps for Power BI interage com esses serviços usando uma conexão SSL protegida por um certificado fornecido e mantido pela Esri. Informações adicionais sobre o ArcGIS Maps for Power BI podem ser obtidas da [página do produto ArcGIS Maps for Power BI](https://www.esri.com/powerbi).

Quando um usuário se inscreve para uma assinatura Plus oferecida pela Esfri por meio do ArcGIS Maps for Power BI, ele está entrando em uma relação direta com a Esri. O Power BI não envia informações pessoais sobre o usuário à Esri. O usuário entra e confia em um aplicativo AAD fornecido pela Esri usando sua própria identidade do AAD. Ao fazer isso, o usuário compartilhará suas informações pessoais diretamente com a Esri. Depois que o usuário adicionar o conteúdo Plus a um visual do ArcGIS Maps for Power BI, outros usuários do Power BI também precisarão de uma assinatura Plus da Esri para exibir ou editar esse conteúdo. 

Para obter perguntas técnicas detalhadas sobre como o ArcGIS Maps for Power BI da Esri funciona, contate a Esri por meio do site de suporte.

**O mapa do ArcGIS não está sendo exibido**    
Em serviços ou aplicativos em que os Mapas do ArcGIS para o Power BI não estiverem disponíveis, a visualização será mostrada como um visual vazio com o logotipo do Power BI.

**Não consigo ver todos os meus endereços no mapa**    
Ao codificar endereços geograficamente, somente os primeiros 1500 endereços serão codificados. Codificações geográficas de nomes de locais ou países não estarão sujeitas ao limite de 1500 endereços.

**O uso do ArcGIS Maps para Power BI é cobrado?**

O Mapa do ArcGIS para o Power BI está disponível para todos os usuários do Power BI sem custo adicional. Ele é um componente fornecido pela **Esri** e seu uso está sujeito aos termos e à política de privacidade fornecidos pela **Esri**, conforme mencionado anteriormente neste artigo.

**Estou recebendo uma mensagem de erro que informa que meu cache está cheio**

Esse é um bug que está sendo resolvido.  Enquanto isso, selecione o link exibido na mensagem de erro para obter instruções sobre como limpar o cache do Power BI.

**Posso exibir meus mapas do ArcGIS offline?**

Não, o Power BI precisa de conectividade de rede para exibir os mapas.

## <a name="next-steps"></a>Próximas etapas
Obtendo ajuda: o **ESRI** fornece uma [documentação abrangente](https://go.microsoft.com/fwlink/?LinkID=828772) sobre o conjunto de recursos dos **Mapas do ArcGIS para o Power BI**.

Você pode fazer perguntas, encontrar as informações mais recentes, reportar problemas e encontrar respostas no [thread da comunidade do Power BI relacionado ao **ArcGIS Maps para o Power BI**](https://go.microsoft.com/fwlink/?LinkID=828771).

Se você tiver alguma sugestão de melhoria, envie-a para a [Lista de ideias do Power BI](https://ideas.powerbi.com).

[Página do produto ArcGIS Maps para Power BI](https://www.esri.com/powerbi)

