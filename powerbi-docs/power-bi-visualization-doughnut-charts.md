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
ms.date: 09/27/2017
ms.author: mihart
ms.openlocfilehash: 2f428095eb57c5358770f1d6d8572316d2b84c37
ms.sourcegitcommit: 99cc3b9cb615c2957dde6ca908a51238f129cebb
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/13/2017
---
# <a name="doughnut-charts-in-power-bi-tutorial"></a>Gráficos de rosca no Power BI (tutorial)
Um gráfico de rosca é semelhante a um gráfico de pizza, pois mostra a relação das partes com o todo. A única diferença é que o centro está em branco e permite o espaço para um rótulo ou ícone.

## <a name="create-a-doughnut-chart"></a>Crie um gráfico de rosca
Para acompanhar, entre no Power BI e selecione **Obter Dados** \> **Amostras** \> **Amostra de Análise de Varejo** \> **Conectar**. 

1. No painel, selecione o bloco **Armazenamentos Totais** para abrir o relatório "Exemplo de Análise de Varejo".
2. Selecione **Editar relatório** para abrir o relatório no modo de Exibição de Edição.
3. [Adicione uma nova página do relatório](power-bi-report-add-page.md).
4. Criar um gráfico de rosca que exibe as vendas deste ano por categoria.
   
   * No painel **Campos**, selecione **Vendas** \> **Vendas do Ano Passado**.
   * Converter em um gráfico de rosca. Se as vendas do ano passado não estiverem na área **Valores** área, arraste-as para lá.
     
       ![](media/power-bi-visualization-doughnut-charts/convertdonut.png)
   * Selecione **Item** \> **Categoria** para adicioná-lo à área **Legenda**. 
     
       ![](media/power-bi-visualization-doughnut-charts/doughnuttutorial.png)

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

