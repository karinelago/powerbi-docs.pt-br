---
title: "Crie um bloco de número grande por meio de um relatório do Power BI"
description: "Crie um bloco de número grande por meio de um relatório do Power BI"
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
ms.date: 09/26/2017
ms.author: mihart
ms.openlocfilehash: 9f748ed1d3a34c6c6aceb14337bbb780598a15f9
ms.sourcegitcommit: 99cc3b9cb615c2957dde6ca908a51238f129cebb
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/13/2017
---
# <a name="create-a-big-number-tile-from-a-power-bi-report"></a>Crie um bloco de número grande por meio de um relatório do Power BI
Às vezes, um único número é a coisa mais importante que você deseja controlar no seu painel do Power BI, como vendas totais, ano de compartilhamento de mercado ao longo do ano, ou oportunidades totais. Você pode criar um bloco de número grande [fazendo uma pergunta na caixa de P e R](power-bi-visualization-big-number.md) ou em um relatório do Power BI. Este artigo explica como criar um em um relatório.

1. Crie um [dashboard](service-dashboards.md) e [obtenha dados](service-get-data.md).
   
   Se você quiser praticar usando dados, [baixe o exemplo de Análise de Varejo](sample-retail-analysis.md). 
2. Abra o relatório no [Modo de Exibição de Edição](service-reading-view-and-editing-view.md).
3. No relatório, encontre uma página com um espaço em branco, ou [adicione uma nova página ao relatório](power-bi-report-add-page.md).
4. Na lista de campos, selecione o campo de número que você deseja exibir.
   
   Neste exemplo, **Abrir contagem de loja** na tabela **Loja** . O Power BI cria um gráfico de colunas com um número.
   
   ![](media/power-bi-visualization-big-number-report/pbi_rptnumbertilechart.png)
5. No painel de Visualizações, selecione o ícone de cartão.
   
   ![](media/power-bi-visualization-big-number-report/pbi_changechartcard.png)
6. Passe o mouse sobre um cartão e selecione o ícone de fixar ![](media/power-bi-visualization-big-number-report/pbi_pintile.png) para adicionar o bloco a um dashboard. 
   
   ![](media/power-bi-visualization-big-number-report/power-bi-pin-icon.png)
7. Fixe o bloco em um painel existente ou em um novo painel. 
   
   * Painel existente: selecione o nome do painel no menu suspenso.
   * Novo painel: digite o nome do novo painel.
8. Selecione **Fixar**.
   
   Uma mensagem de Êxito (perto do canto superior direito) informa que a visualização foi adicionada, como um bloco, ao painel.
   
   ![](media/power-bi-visualization-big-number-report/power-bi-pin-success-message.png)
9. Selecione **Ir para o dashboard**. Nele, você pode [editar e mover](service-dashboard-edit-tile.md) a visualização fixada.

## <a name="next-steps"></a>Próximas etapas
[Blocos de Dashboard no Power BI](service-dashboard-tiles.md)

[Dashboards no Power BI](service-dashboards.md)

[Power BI – conceitos básicos](service-basic-concepts.md)

Mais perguntas? [Experimente a Comunidade do Power BI](http://community.powerbi.com/)

