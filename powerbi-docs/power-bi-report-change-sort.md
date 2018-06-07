---
title: Altere como um gráfico é classificado em um relatório do Power BI
description: Altere como um gráfico é classificado em um relatório do Power BI
author: mihart
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 05/20/2018
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: 3c32fc3cc9dc2b16384016ca624d4dd3a773aacb
ms.sourcegitcommit: 80d6b45eb84243e801b60b9038b9bff77c30d5c8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34561783"
---
# <a name="change-how-a-chart-is-sorted-in-a-power-bi-report"></a>Altere como um gráfico é classificado em um relatório do Power BI
Em um relatório do Power BI, você pode classificar a maioria das visualizações em ordem alfabética pelos nomes das categorias no gráfico, ou pelos valores numéricos de cada categoria. Por exemplo, este gráfico é classificado por nome de loja.

![](media/power-bi-report-change-sort/pbi_chartsortcategory.png)

É fácil alterar a classificação de uma categoria (nome do repositório) para um valor (vendas por pés quadrados).

1. Selecione as reticências (...) e escolha **Classificar por Vendas por metros quadrados**.
2. Se necessário, selecione o ícone de classificação ![](media/power-bi-report-change-sort/sorticon.png) para alterar para **Decrescente**.

   ![](media/power-bi-report-change-sort/sortby.gif)

   **OBSERVAÇÃO**: nem todos os visuais podem ser classificados.  Por exemplo, os seguintes visuais não podem ser classificados: Mapa de Árvore, Mapa, Mapa Coroplético, Dispersão, Medidor, Cartão, Cartão de Múltiplas Linhas e Cascata.

## <a name="saving-changes-you-make-to-sort-order"></a>Salvar as alterações feitas na ordem de classificação
Os relatórios do Power BI retêm os filtros, divisões, classificações e outras alterações de exibição de dados que você fizer. Portanto, se você sair de um relatório e retornar mais tarde, suas alterações serão salvas.  Se você quiser reverter as alterações para as configurações do autor do relatório, selecione **Redefinir para padrão** na barra de menus superior. 

![classificação persistente](media/power-bi-report-change-sort/power-bi-reset-to-default.png)

Se, no entanto, o botão **Redefinir para padrão** estiver esmaecido, significará que o autor do relatório desabilitou a funcionalidade de salvar (persistir) as alterações.

<a name="other"></a>
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
