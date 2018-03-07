---
title: "Gráficos de rosca no Power BI (tutorial)"
description: "Tutorial: gráficos de rosca no Power BI"
services: powerbi
documentationcenter: 
author: mihart
manager: kfile
backup: 
editor: 
tags: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 12/23/2017
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: dca772fd2a1b8f40fa61f1abc41145e8ff6e5a8a
ms.sourcegitcommit: 88c8ba8dee4384ea7bff5cedcad67fce784d92b0
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/24/2018
---
# <a name="doughnut-charts-in-power-bi-tutorial"></a>Gráficos de rosca no Power BI (tutorial)
Um gráfico de rosca é semelhante a um gráfico de pizza, pois mostra a relação das partes com o todo. A única diferença é que o centro está em branco e permite o espaço para um rótulo ou ícone.

## <a name="create-a-doughnut-chart"></a>Crie um gráfico de rosca
Essas instruções usam o Exemplo de Análise de Varejo para criar um gráfico de rosca que exibe as vendas deste ano por categoria. Para acompanhar, [baixe o exemplo](sample-datasets.md) do serviço do Power BI (app.powerbi.com) ou do Power BI Desktop.

1. Comece em uma [página de relatório em branco ](power-bi-report-add-page.md) e selecione o campo **SalesStage** \> **Sales Stage**. Caso esteja usando o serviço do Power BI, certifique-se de abrir o relatório no [Modo de Exibição de Edição](service-interact-with-a-report-in-editing-view.md).

2. No painel Campos, selecione **Vendas** \> **Vendas do Ano Passado**.  
   
3. No painel Visualizações, selecione o ícone de gráfico de rosca ![ícone de gráfico de rosca]() para converter seu gráfico de barras em um gráfico de rosca. Se as **Vendas do Ano Passado** não estiverem na área **Valores**, arraste-as para lá.
     
   ![](media/power-bi-visualization-doughnut-charts/power-bi-doughnut-chart.png)

4. Selecione **Item** \> **Categoria** para adicioná-lo à área **Legenda**. 
     
    ![](media/power-bi-visualization-doughnut-charts/power-bi-doughnut-done.png)

5. Opcionalmente, [ajuste o tamanho e a cor do texto do gráfico](power-bi-visualization-customize-title-background-and-legend.md). 

## <a name="considerations-and-troubleshooting"></a>Considerações e solução de problemas
* A soma dos valores do gráfico de rosca deve somar até 100%.
* Muitas categorias são difíceis de ler e interpretar.
* Os gráficos de rosca são melhor usados para comparar uma determinada seção ao toda, em vez de comparar as seções individuais entre si. 

## <a name="next-steps"></a>Próximas etapas
[Relatórios no Power BI](service-reports.md)

[Tipos de visualização no Power BI](power-bi-visualization-types-for-reports-and-q-and-a.md)

[Visualizações em relatórios do Power BI](power-bi-report-visualizations.md)

[Power BI – conceitos básicos](service-basic-concepts.md)

Mais perguntas? [Experimente a Comunidade do Power BI](http://community.powerbi.com/)

