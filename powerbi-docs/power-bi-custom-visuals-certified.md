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
ms.date: 11/20/2017
ms.author: mihart
ms.openlocfilehash: 3d51475b300fadc55f33960b03c3adc0031a39b8
ms.sourcegitcommit: 12236d08c27c7ee3fabb7ef9d767e9dee693f8aa
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="getting-a-custom-visual-certified"></a>*Certificando* um visual personalizado
## <a name="what-is-meant-by-certified"></a>O que significa *certificado*?
Um *visual personalizado certificado* é aquele que atendeu um conjunto de requisitos de código e foi aprovado em testes de segurança rígidos.  Depois que um visual personalizado tiver sido certificado, ele poderá ser [exportado para o PowerPoint](service-publish-to-powerpoint.md) e será exibido nos emails recebidos quando um usuário [assinar as páginas de relatório](service-report-subscribe.md).

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
| [Gráfico de Aster](https://appsource.microsoft.com/product/power-bi-visuals/WA104380759?src=office&tab=Overview) | |
| [Gráfico de bowtie por MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380838?src=office&tab=Overview) |[Vídeo](https://youtu.be/So5xKMSpVJI) |
| [BciCalendar (Calendário da Beyondsoft)](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381096?src=office&tab=Overview)  | |
| [Caixa Estreita](https://appsource.microsoft.com/product/power-bi-visuals/WA104380831?src=office&tab=Overview) | |
| [Gráfico de marcador](https://store.office.com/app.aspx?assetid=WA104380755) |[Vídeo1](https://youtu.be/AOlsFYkfkcw)   [Vídeo2](https://youtu.be/AQvd2FhRyCI) |
| [Gráfico de marcador por OKViz](https://store.office.com/bullet-chart-by-okviz-WA104380953.aspx) |[Vídeo](https://youtu.be/mtvUNl9bMjA) |
| [Calendário por Tallan](https://appsource.microsoft.com/product/power-bi-visuals/WA104381146?src=office&tab=Overview) | |
| [Segmentação chiclet](https://store.office.com/chiclet-slicer-WA104380756.aspx) |[Vídeo](https://youtu.be/iYOkJ1APueY) |
| [Gráfico de Corda](https://appsource.microsoft.com/product/power-bi-visuals/WA104380761?src=office&tab=Overview) |[Vídeo](https://youtu.be/AQvd2FhRyCI) |
| [Medidor circular da MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380837?tab=Overview) | |
| [Medidor cilíndrico](https://appsource.microsoft.com/product/power-bi-visuals/WA104380874) | |
| [Medidor com mostrador](https://appsource.microsoft.com/product/power-bi-visuals/WA104381184) |[Vídeo](https://youtu.be/AOlsFYkfkcw) |
| [Gráfico de rosca da MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380824?tab=Overview) |[Vídeo](https://youtu.be/pDToHDFHnq8) |
| [Gráfico de Pontos por OKViz](https://appsource.microsoft.com/product/power-bi-visuals/WA104381101?src=office&tab=Overview) |[Vídeo](https://youtu.be/4lskRgcpFJY) |
| [Fazer drill down do gráfico de rosca por ZoomCharts](https://appsource.microsoft.com/product/power-bi-visuals/WA104380858) | |
| [KPI duplo](https://store.office.com/dual-kpi-WA104380774.aspx) |[Vídeo](https://youtu.be/821o0-eVBXo?list=PL1N57mwBHtN1vIjfvuBIzZllrmKo-Vz6x) |
| [Enlighten Aquarium](https://appsource.microsoft.com/product/power-bi-visuals/WA104381112?src=office&tab=Overview) | |
| Enlighten World Flags – Em breve | |
| Enlighten Stack Shuffle – Em breve | |
| [Gantt](https://store.office.com/gantt-WA104380765.aspx) |[Vídeo](https://youtu.be/qJ7s_KrGiUU) |
| [Histograma](https://store.office.com/histogram-chart-WA104380776.aspx) | |
| [Funil horizontal](https://appsource.microsoft.com/product/power-bi-visuals/WA104380846) |[Vídeo](https://youtu.be/SudZei68PPo) |
| [Indicador KPI](https://store.office.com/kpi-indicator-WA104380832.aspx) | |
| [Medidor linear da MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380821?src=office&tab=Overview) |[Vídeo](https://youtu.be/AOlsFYkfkcw) |
| [Gráfico do Mekko](https://appsource.microsoft.com/product/power-bi-visuals/WA104380785?src=office&tab=Overview)  | [Vídeo](https://youtu.be/90FLCKpgicA)|
| [Eixo de reprodução (Segmentação Dinâmica)](https://store.office.com/play-axis-dynamic-slicer-WA104380981.aspx) | |
| [Power KPI](https://appsource.microsoft.com/product/power-bi-visuals/WA104381083) |[Vídeo](https://youtu.be/IvfIP3E6-1Q) |
| [Gráfico de radar](https://store.office.com/radar-chart-WA104380771.aspx) | |
| [Gráfico de rosca da MAQ Software](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380824?src=office&tab=Overview) | [Vídeo](https://youtu.be/pDToHDFHnq8)|
| [Gráfico de Sankey](https://store.office.com/app.aspx?assetid=WA104380777.aspx) |[Vídeo](https://youtu.be/WWP9wVUHGaA) |
| [Controle de rolagem](https://store.office.com/scroller-WA104381018.aspx) |[Vídeo](https://youtu.be/uhRFQF2cGSY) |
| [Filtro Inteligente por SQLBI](https://store.office.com/smart-filter-by-okviz-WA104380859.aspx) |[Vídeo](https://youtu.be/gcJsDDRQq28) |
| [Minigráfico por OKViz](https://appsource.microsoft.com/product/power-bi-visuals/WA104380910?src=office&tab=Overview) |[Vídeo](https://youtu.be/0m3Vnvso9tY) |
| [Sunburst](https://appsource.microsoft.com/product/power-bi-visuals/WA104380767?src=office&tab=Overview) | |
| [Tacômetro](https://store.office.com/tachometer-WA104380937.aspx?) |[Vídeo](https://www.youtube.com/watch?v=C3OXdETbS9o) |
| [Termômetro](https://appsource.microsoft.com/product/power-bi-visuals/WA104380847?src=office&tab=Overview) | [Vídeo](https://youtu.be/SPX9mgrAdBc)|
| [Decomposição da série temporal](https://appsource.microsoft.com/product/power-bi-visuals/WA104380897) | |
| [Mapa de calor de tabela](https://store.office.com/table-heatmap-WA104380818.aspx) | |
| [Wrapper de texto](https://appsource.microsoft.com/product/power-bi-visuals/WA104380826) | |
| [Segmentação da linha do tempo](https://store.office.com/timeline-slicer-WA104380786.aspx) |[Vídeo](https://youtu.be/ozMtZ4_NZ10) |
| [Gráfico de tornado](https://store.office.com/tornado-chart-WA104380768.aspx) |[Vídeo](https://youtu.be/AQvd2FhRyCI) |
| [Gráfico de Waffle](https://appsource.microsoft.com/product/power-bi-visuals/WA104381049?src=office&tab=Overview) |[Vídeo](https://youtu.be/1vRqYUsm3Vk) |
| [Nuvem do Word](https://store.office.com/word-cloud-WA104380752.aspx?) |[Vídeo](https://www.youtube.com/watch?v=AblTenl9fqo) |

## <a name="next-steps"></a>Próximas etapas
[Introdução às ferramentas do desenvolvedor de visuais personalizados (Visualização)](service-custom-visuals-getting-started-with-developer-tools.md)      
[Playlist de visuais personalizados da Microsoft no YouTube](https://www.youtube.com/playlist?list=PL1N57mwBHtN1vIjfvuBIzZllrmKo-Vz6x)  
[Visualizações no Power BI](power-bi-report-visualizations.md)  
[Visualizações personalizadas no Power BI](power-bi-custom-visuals.md)  
[Publicar visuais personalizados no Microsoft AppSource](developer/office-store.md)  
Mais perguntas? [Experimente a Comunidade do Power BI](http://community.powerbi.com/)

