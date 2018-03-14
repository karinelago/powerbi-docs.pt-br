---
title: "Visualizações personalizadas no Power BI certificado"
description: "Requisitos e processos para enviar um visual personalizado para certificação. E uma lista de visuais personalizados já certificados."
services: powerbi
documentationcenter: 
author: mihart
manager: kfile
backup: 
editor: 
tags: 
featuredvideoid: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 02/13/2018
ms.author: mihart
ms.openlocfilehash: cc50e4e8830aca3951da6004b8ada3913aff28ed
ms.sourcegitcommit: 743e44fc8730fea0f7149916080b0c6d7eb6359d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/28/2018
---
# <a name="getting-a-custom-visual-certified"></a>*Certificando* um visual personalizado
## <a name="what-is-meant-by-certified"></a>O que significa *certificado*?
Um *visual personalizado certificado* é aquele que atendeu um conjunto de requisitos de código e foi aprovado em testes de segurança rígidos.  Depois que um visual personalizado tiver sido certificado, ele poderá ser [exportado para o PowerPoint](service-publish-to-powerpoint.md) e será exibido nos emails recebidos quando um usuário [assinar as páginas de relatório](service-report-subscribe.md). Obviamente, também pode ser usado como [elementos visuais personalizados padrão](power-bi-custom-visuals.md), adicionado ao serviço do Power BI e a relatórios do Power BI Desktop e exibido no Power BI móvel e integrado.

Você é um desenvolvedor da Web e está interessado em criar suas próprias visualizações e adicioná-las ao [Microsoft AppSource](https://appsource.microsoft.com)? Para saber como fazer isso, veja [Introdução às Ferramentas para Desenvolvedores](service-custom-visuals-getting-started-with-developer-tools.md).


## <a name="certification-requirements"></a>Requisitos de certificação
* Microsoft AppSource aprovado    
* O visual personalizado é escrito com a API com versão 1.2 ou superior    
* Repositório de código disponível para análise (por exemplo, Código do visual disponível para nós por meio do GitHub)    
* Usa somente componentes OSS públicos analisáveis    
* Não acessa serviços ou recursos externos    

> **DICA**: recomendamos que você use o EsLint com o conjunto de regras de segurança padrão para validar previamente seu código antes do envio.
> 
> 

## <a name="process-for-submitting-a-custom-visual-for-certification"></a>Processo para enviar um visual personalizado para certificação
Para enviar um visual personalizado para certificação:

1. Envie um email para o suporte de visuais personalizados do Power BI (pbicvsupport@microsoft.com). No email, inclua as seguintes informações:    
   
   * Título: solicitação de certificação do visual    
   * Vincular ao repositório GitHub em que o código-fonte do visual está hospedado    
   * Seguir os requisitos (veja acima)    
   * Passar a análise do código e de segurança    

2. A equipe de Visuais personalizados na Microsoft notificará você quando seu visual personalizado for certificado e adicionado à lista Certificado (abaixo) ou rejeitado com um relatório dos problemas que precisam ser corrigidos. É responsabilidade do desenvolvedor manter uma linha aberta de comunicação com a Microsoft e atualizar os Visuais certificados como necessário.

## <a name="removal-of-power-bi-certified-custom-visuals"></a>Remoção dos Visuais personalizados certificados do Power BI
A Microsoft, a seu critério, poderá remover um visual da lista Certificado.  

## <a name="list-of-custom-visuals-that-have-been-certified"></a>Lista de visuais personalizados que foram certificados
| Link para AppSource | Link para o vídeo |
| --- | --- |
| [Association rules](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380815) | |
| [Aster Plot](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380759) | |
| [Beyondsoft Calendar](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381096) | |
| [Bowtie Chart by MAQ Software](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380838) | [Vídeo](https://youtu.be/So5xKMSpVJI) |
| [Box and Whisker chart](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380831) | |
| [Box and Whisker chart by MAQ Software](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381351) | [Vídeo](https://youtu.be/JoHaFLfhXdo) |
| [Brick Chart by MAQ Software](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380836) | [Vídeo](https://youtu.be/hA3DOsvn2xY) |
| [Bubble Chart by Akvelon](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381340) | |
| [Bullet Chart](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380755) | [Vídeo](https://youtu.be/AOlsFYkfkcw) |
| [Bullet Chart by OKViz](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380953) | [Vídeo](https://youtu.be/mtvUNl9bMjA) |
| [Calendar by Tallan](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381146) | |
| [Candlestick by OKViz](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380952) | [Vídeo](https://youtu.be/nT_18gyRxPo) |
| [Card with States by OKViz](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380967) | |
| [Chiclet Slicer](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380756) | |
| [Chord](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380761) | [Vídeo](https://youtu.be/AQvd2FhRyCI) |
| [Circular Gauge by MAQ Software](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380837) | [Vídeo](https://youtu.be/9NHXALkBXuY) |
| [Cluster Map](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380806) | |
| [Clustering](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380861) | |
| [Clustering With Outliers](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380889) | |
| [Correlation plot](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380814) | |
| [Cylindrical Gauge by MAQ Software](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380874) | [Vídeo](https://youtu.be/DgdoWi7Gcxo) |
| [Decision Tree Chart](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380817) | |
| [Dial Gauge](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381184) | |
| [Dot Plot](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380760) | |
| [Dot Plot by OKViz](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380949) | [Vídeo](https://youtu.be/By16pX9KT40) |
| [Drilldown Cartogram](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381045) | |
| [Drilldown Choropleth](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381044) | |
| [Drill-down column chart](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380857) | [Vídeo](https://youtu.be/lBy2gQQ5YsQ) |
| [Drill-down column chart for time based data](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380881) | [Vídeo](https://youtu.be/T_mRou18vx0) |
| [Drill-down donut chart](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380858) | [Vídeo](https://youtu.be/AUVFrSHmPeo) |
| [Dual KPI](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380774) | |
| [Enhanced Scatter](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380762) | [Vídeo](https://youtu.be/xCfM0cjM4do) |
| [Enlighten Aquarium](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381112) | |
| [Enlighten Slicer](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380960) | |
| [Enlighten Stack Shuffle](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380849) | |
| [Enlighten Waffle Chart](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380850) | |
| [Force-Directed Graph](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380764) | [Vídeo](https://youtu.be/YsTa7uyJ4sg) |
| [Forecasting TBATS](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381326) | |
| [Forecasting with ARIMA](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380888) | |
| [Funnel with Source by MAQ Software](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381334) | [Vídeo](https://youtu.be/R_EcimsLI8U) |
| [Gantt](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380765) | [Vídeo](https://youtu.be/qJ7s_KrGiUU) |
| [Gantt Chart by MAQ Software](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381364) | [Vídeo](https://youtu.be/vJLV9JRCpI8) |
| [Globe Data Bars](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381344) | |
| [Hierarchy Chart by Akvelon](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381333) | [Vídeo](https://youtu.be/0ZGzJaq_KT4) |
| [Histogram Chart](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380776) | |
| [Histogram with points by MAQ Software](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381032) | [Vídeo](https://youtu.be/-ILF--wExrw) |
| [Horizontal Funnel by MAQ Software](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380846) | [Vídeo](https://youtu.be/SudZei68PPo) |
| [Image by CloudScope](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381297) | |
| [Image Grid](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381355) | |
| [Infographic Designer](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380898) | |
| [KPI Chart by Akvelon](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381432) | |
| [KPI Indicator](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380832) | |
| [KPI Ticker da MAQ Software](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380946) | [Vídeo](https://youtu.be/cudG4gsZ2V8) |
| [Linear Gauge by MAQ Software](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380821) | [Vídeo](https://youtu.be/7_jFaM30dkc) |
| [LineDot Chart](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380766) | |
| [Mekko Chart](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380785) | [Vídeo](https://youtu.be/90FLCKpgicA) |
| [Play Axis (Dynamic Slicer)](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380981) | |
| [Power KPI](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381083) | [Vídeo](https://youtu.be/IvfIP3E6-1Q) |
| [Power KPI Matrix](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381299) | [Vídeo](https://youtu.be/1enze8pcGzY) |
| [Gráfico de quadrante por MAQ Software](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381011) | [Vídeo](https://youtu.be/ppBnyhqWNC0) |
| [Radar Chart](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380771) | |
| [Ring Chart by MAQ Software](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380824) | [Vídeo](https://youtu.be/pDToHDFHnq8) |
| [Rotating Chart by MAQ Software](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381007) | [Vídeo](https://youtu.be/d5xBCMmb3hU) |
| [Sankey Chart](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380777) | [Vídeo](https://youtu.be/WWP9wVUHGaA) |
| [Scroller](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381018) | |
| [Smart Filter by OKViz](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380859) | [Vídeo](https://youtu.be/gcJsDDRQq28) |
| [Sparkline by OKViz](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380910) | [Vídeo](https://youtu.be/0m3Vnvso9tY) |
| [Spline chart](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380860) | |
| [Stream Graph](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380772) | |
| [Sunburst](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380767) | |
| [Table Heatmap](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380818) | |
| [Tachometer](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380937) | [Vídeo](https://youtu.be/C3OXdETbS9o) |
| [Filtro de texto](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381309) | |
| [Text Wrapper by MAQ Software](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380826) | |
| [Thermometer](https://appsource.microsoft.com/en-us/product/office/WA104379807) | |
| [Time series decomposition chart](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380897) | |
| [Time Series Forecasting Chart](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380816) | |
| [Timeline Slicer](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380786) | [Vídeo](https://youtu.be/ozMtZ4_NZ10) |
| [Tornado chart](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380768) | [Vídeo](https://www.youtube.com/watch?v=AQvd2FhRyCI) |
| [Trading Chart by MAQ Software](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380823) | [Vídeo](https://youtu.be/xhTR6y6J9Ko) |
| [Ultimate Variance](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381140) | [Vídeo](https://youtu.be/pDYF8iZxERs) |
| [Ultimate Waterfall](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380956) | [Vídeo](https://youtu.be/0BZsVCQdEkc) |
| [User List by CloudScope](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381426) | |
| [Waffle Chart](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381049) | [Vídeo](https://youtu.be/1vRqYUsm3Vk) |
| [Word Cloud](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380752) | [Vídeo](https://youtu.be/AblTenl9fqo) |

## <a name="next-steps"></a>Próximas etapas
[Introdução às ferramentas do desenvolvedor de visuais personalizados (Visualização)](service-custom-visuals-getting-started-with-developer-tools.md)      
[Playlist de visuais personalizados da Microsoft no YouTube](https://www.youtube.com/playlist?list=PL1N57mwBHtN1vIjfvuBIzZllrmKo-Vz6x)  
[Visualizações no Power BI](power-bi-report-visualizations.md)  
[Visualizações personalizadas no Power BI](power-bi-custom-visuals.md)  
[Publicar visuais personalizados no Microsoft AppSource](developer/office-store.md)  
Mais perguntas? [Experimente a Comunidade do Power BI](http://community.powerbi.com/)

