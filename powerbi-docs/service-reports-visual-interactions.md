---
title: "Alterar como os visuais interagem em um relatório"
description: "Documentação para saber como definir as interações visuais em um relatório de serviço do Microsoft Power BI e um relatório do Power BI Desktop."
services: powerbi
documentationcenter: 
author: mihart
manager: kfile
backup: 
editor: 
tags: 
featuredvideoid: N_xYsCbyHPw
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 02/28/2018
ms.author: mihart
LocalizationGroup: Reports
ms.openlocfilehash: 7e2ef4a1ec49335a49e7f934a7606b2fe64f755c
ms.sourcegitcommit: 5e1f7d2673efe25c47b9b9f315011055bfe92c8f
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/09/2018
---
# <a name="visualization-interactions-in-a-power-bi-report"></a>Interações de visualização em um relatório do Power BI
Se você tiver permissões de edição para um relatório, poderá usar as **interações visuais** para alterar como as visualizações em uma página de relatório afetam umas às outras. 

Por padrão, as visualizações em uma página de relatório podem ser usadas para filtro cruzado e realce cruzado de outras visualizações na página.
Por exemplo, selecionar um estado em uma visualização de mapa realça o gráfico de colunas e filtra o gráfico de linhas para exibir apenas os dados que se aplicam a um estado.
Veja [Sobre filtragem e realce](power-bi-reports-filters-and-highlighting.md). E se você tiver uma visualização que é compatível com [drill down](power-bi-visualization-drill-down.md), por padrão, fazer drill down em uma visualização não afeta as outras visualizações na página do relatório. Mas ambos os comportamentos padrão podem ser substituídos e as interações definidas por visualização.

Este artigo mostra como usar as **interações visuais** no [Exibição de edição](service-interact-with-a-report-in-editing-view.md) do serviço do Power BI e no Power BI Desktop. Se um relatório foi compartilhado com você, não será possível alterar as configurações de interações visuais.

> [!NOTE]
> Os termos *filtro cruzado* e *realce cruzado* são usados para distinguir o comportamento descrito aqui do que acontece quando você usa o painel **Filtros** painel para filtrar e realçar visualizações.  
> 
> 

<iframe width="560" height="315" src="https://www.youtube.com/embed/N_xYsCbyHPw?list=PL1N57mwBHtN0JFoKSR0n-tBkUJHeMP2cP" frameborder="0" allowfullscreen></iframe>

1. Selecione a visualização para ativá-la.  
2. Exiba as opções de **Interações Visuais**.
    - No serviço do Power BI, selecione o menu suspenso na barra de menus do relatório.

       ![Lista suspensa de Interações visuais](media/service-reports-visual-interactions/power-bi-visual-interaction.png)

    - Na Área de trabalho, selecione **Formato > Interações**.

        ![selecione Formato e depois Interações](media/service-reports-visual-interactions/pbi-visual-interaction-desktop.png)

3. Para ativar os controles de interação de visualização, selecione **Editar interações**. O Power BI adiciona os ícones de filtro cruzado e realce cruzado a todas as outras visualizações na página do relatório.
   
    ![relatório com interações visuais ligadas](media/service-reports-visual-interactions/power-bi-icons-on.png)
3. Determine o impacto que a visualização selecionada deve ter nas outras visualizações.  E, como opção, repita para todas as outras visualizações na página do relatório.
   
   * Se deve realizar a filtragem cruzada da visualização, selecione o ícone **filtrar** ![ícone filtrar](media/service-reports-visual-interactions/pbi-filter-icon-outlined.png).
   * Se deve realizar o realce cruzado da visualização, selecione o ícone **realçar** ![ícone realçar](media/service-reports-visual-interactions/pbi-highlight-icon-outlined.png).
   * Se deve não ter impacto, selecione o ícone **sem impacto** ![ícone sem impacto](media/service-reports-visual-interactions/pbi-noimpact-icon-outlined.png).

4. Para ativar os controles de drill down, selecione **Filtros detalhados de outros elementos visuais**.  Agora, quando você fizer drill down (e up) em uma visualização, as outras visualizações na página do relatório serão alteradas para refletir sua seleção atual de detalhamento. 

   ![vídeo de ligar o detalhamento de controles](media/service-reports-visual-interactions/drill2.gif)

### <a name="next-steps"></a>Próximas etapas
[Como usar filtros de relatório](power-bi-how-to-report-filter.md)

[Filtros e realce em relatórios](power-bi-reports-filters-and-highlighting.md)

[Power BI – conceitos básicos](service-basic-concepts.md)

Mais perguntas? [Experimente a Comunidade do Power BI](http://community.powerbi.com/)

