---
title: "Altere como um gráfico é classificado em um relatório do Power BI"
description: "Altere como um gráfico é classificado em um relatório do Power BI"
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
ms.date: 09/08/2017
ms.author: mihart
ms.openlocfilehash: 37161fab1e19e6ce00eb0f02c96b6e5cbdd60f18
ms.sourcegitcommit: 284b09d579d601e754a05fba2a4025723724f8eb
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/15/2017
---
# <a name="change-how-a-chart-is-sorted-in-a-power-bi-report"></a>Altere como um gráfico é classificado em um relatório do Power BI
No Power BI, você pode classificar os gráficos em ordem alfabética pelos nomes das categorias no gráfico, ou pelos valores numéricos de cada categoria. Por exemplo, este gráfico é classificado por nome de loja.

![](media/power-bi-report-change-sort/pbi_chartsortcategory.png)

Em vez disso, é fácil classificá-los do valor mais alto ao mais baixo de vendas por pés quadrados.

1. Selecione as reticências (...) e escolha **Classificar por Vendas por metros quadrados**.
2. Se necessário, selecione o ícone de classificação ![](media/power-bi-report-change-sort/sorticon.png) para alterar para **Decrescente**.
   
   ![](media/power-bi-report-change-sort/sortby.gif)
   
   **OBSERVAÇÃO**: nem todos os visuais podem ser classificados.  Por exemplo, os seguintes visuais não podem ser classificados: Mapa de Árvore, Mapa, Mapa Coroplético, Dispersão, Medidor, Cartão, Cartão de Múltiplas Linhas e Cascata.

## <a name="sorting-using-other-criteria"></a>Classificando o uso de outros critérios
Às vezes, você deseja classificar seu visual usando um campo diferente ou outros critérios.  Por exemplo, talvez você queira classificar por mês (e não em ordem alfabética) ou talvez queira classificar por números inteiros em vez de por dígitos (exemplo, 0, 1, 9, 20 e não 0, 1, 20, 9).  

Em alguns casos, é permitido classificar o visual da maneira desejada, por exemplo, por mês.  Caso não seja possível, o motivo poderá ser que o conjunto de dados subjacente ao relatório precisa de alguns ajustes. Aqui estão várias soluções:

* No Power BI Desktop, [use a guia Modelagem da Ferramentas de Dados para classificar por uma coluna diferente](desktop-sort-by-column.md).
* No Excel, se você possui o conjunto de dados, adicione uma nova coluna que concatena o nome do mês e o número. Em seguida, atualize ou importe novamente o conjunto de dados para ver a nova coluna na área Campos.
* No Excel, certifique-se de que as colunas numéricas estejam marcadas como "número inteiro" ou "decimal" e não como "texto".

## <a name="next-steps"></a>Próximas etapas
Mais sobre [Visualizações nos relatórios do Power BI](power-bi-report-visualizations.md).

[Power BI – conceitos básicos](service-basic-concepts.md)

Mais perguntas? [Experimente a Comunidade do Power BI](http://community.powerbi.com/)

