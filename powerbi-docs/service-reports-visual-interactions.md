---
title: "Alterar como os visuais interagem em um relatório"
description: "Documentação para saber como definir as interações de visuais em um relatório do Microsoft Power BI."
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
ms.date: 09/25/2017
ms.author: mihart
ms.openlocfilehash: 126bd40e98a88138a2732155f9792d65666e52c7
ms.sourcegitcommit: 99cc3b9cb615c2957dde6ca908a51238f129cebb
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/13/2017
---
# <a name="visualization-interactions-in-a-power-bi-report"></a>Interações de visualização em um relatório do Power BI
Por padrão, as visualizações em uma página de relatório podem ser usadas para filtro cruzado e realce cruzado de outras visualizações na página.
Por exemplo, selecionar um estado em uma visualização de mapa realça o gráfico de colunas e filtra o gráfico de linhas para exibir apenas os dados que se aplicam a um estado.
Veja [Sobre filtragem e realce](power-bi-reports-filters-and-highlighting.md).

Para alterar esse comportamento padrão, use o controle **Interação visual**. As interações visuais só estão disponível no [modo de exibição de edição](service-interact-with-a-report-in-editing-view.md). Se um relatório foi compartilhado com você, não haverá acesso às interações visuais.

> [!NOTE]
> Os termos *filtro cruzado* e *realce cruzado* são usados para distinguir o comportamento descrito aqui do que acontece quando você usa o painel **Filtros** painel para filtrar e realçar visualizações.  
> 
> 

<iframe width="560" height="315" src="https://www.youtube.com/embed/N_xYsCbyHPw?list=PL1N57mwBHtN0JFoKSR0n-tBkUJHeMP2cP" frameborder="0" allowfullscreen></iframe>

1. Selecione a visualização para ativá-la.  
2. Ative **Interações Visuais** selecionando-a na barra de menus superior. Observe os ícones de filtrar e realçar que aparecem quando você focaliza outras visualizações na página do relatório.
   
    ![](media/service-reports-visual-interactions/pbi-visual-interaction-icon.png)
3. Determine o impacto que a visualização selecionada deve ter nas outras visualizações.  
   
   * Se ela precisar executar filtro cruzado da outra visualização, selecione o ícone de **filtro** ![](media/service-reports-visual-interactions/pbi-filter-icon-outlined.png).
   * Se ela precisar executar realce cruzado da visualização, selecione o ícone de **realce** ![](media/service-reports-visual-interactions/pbi-highlight-icon-outlined.png).
   * Se ela não precisar ter impacto, selecione o ícone de **nenhum impacto** ![](media/service-reports-visual-interactions/pbi-noimpact-icon-outlined.png).
4. Como opção, repita para todas as outras visualizações na página do relatório.

### <a name="next-steps"></a>Próximas etapas
[Como usar filtros de relatório](power-bi-how-to-report-filter.md)

[Filtros e realce em relatórios](power-bi-reports-filters-and-highlighting.md)

[Power BI – conceitos básicos](service-basic-concepts.md)

Mais perguntas? [Experimente a Comunidade do Power BI](http://community.powerbi.com/)

