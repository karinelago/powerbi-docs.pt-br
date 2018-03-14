---
title: "Gerar automaticamente as informações sobre os dados com o Power BI"
description: "Saiba como obter informações sobre seus conjuntos de dados e blocos de painéis."
services: powerbi
documentationcenter: 
author: mihart
manager: kfile
backup: 
editor: 
tags: 
featuredvideoid: et_MLSL2sA8
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 02/28/2018
ms.author: mihart
LocalizationGroup: Dashboards
ms.openlocfilehash: 5623667cd1a39b05795d162055ad0d3351d127bc
ms.sourcegitcommit: 5e1f7d2673efe25c47b9b9f315011055bfe92c8f
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/09/2018
---
# <a name="automatically-generate-data-insights-with-power-bi"></a>Gerar automaticamente as informações sobre os dados com o Power BI
Tem um novo conjunto de dados e não sabe exatamente por onde começar?  Você precisa criar um painel rapidamente?  Deseja procurar informações que você pode ter perdido?

Execute insights rápidos para gerar visualizações interativas e interessantes com base em seus dados. Os Insights Rápidos podem ser executados em um conjunto de dados inteiro (insights rápidos) ou em um bloco de painéis específico (insights com escopo). Você pode até mesmo executar insights em um insight!

> **Observação**: insights não funcionam com DirectQuery; eles funcionam somente com os dados carregados no Power BI.
> 
> 

O recurso de insights tem como base um crescente [conjunto de algoritmos analíticos avançados](service-insight-types.md) desenvolvido em conjunto com a Microsoft Research, os quais continuaremos a utilizar para permitir que mais pessoas encontrem informações em seus dados de maneiras novas e intuitivas.

## <a name="run-quick-insights-on-a-dataset"></a>Executar insights rápidos em um conjunto de dados
Veja a Amanda executar insights rápidos em um conjunto de dados, abrir um insight no modo de foco, fixar um desses insights como um bloco no painel dela e, em seguida, obter insights para um bloco do painel.

<iframe width="560" height="315" src="https://www.youtube.com/embed/et_MLSL2sA8" frameborder="0" allowfullscreen></iframe>


Agora é sua vez. Explore insights usando o [exemplo de análise de qualidade de fornecedor](sample-supplier-quality.md).

1. Na guia **Conjuntos de dados**, selecione as reticências (...) e escolha **Obter insights**.
   
    ![Guia Conjuntos de dados](media/service-insights/power-bi-ellipses.png)
   
    ![menu de reticências](media/service-insights/power-bi-tab.png)
2. O Power BI usa [vários algoritmos](service-insight-types.md) para pesquisar tendências no conjunto de dados.
   
    ![Caixa de diálogo Procurando por insights](media/service-insights/pbi_autoinsightssearching.png)
3. Em poucos segundos, suas informações estão prontas.  Selecione **Exibir insights** para exibir as visualizações.
   
    ![mensagem de êxito](media/service-insights/pbi_autoinsightsuccess.png)
   
   > **OBSERVAÇÃO**: alguns conjuntos de dados não podem gerar insights porque os dados não são estatisticamente significativos.  Para saber mais, veja [Otimizar seus dados para insights](service-insights-optimize.md).
   > 
   > 
1. As visualizações são exibidas em uma tela especial dos **Insights Rápidos** com até 32 cartões de insights separados. Cada cartão contém um gráfico e uma breve descrição.
   
    ![Tela Insights Rápidos](media/service-insights/power-bi-insights.png)

## <a name="interact-with-the-insight-cards"></a>Interagir com os cartões de insights
  ![ícone fixar](media/service-insights/pbi_hover.png)

1. Passe o mouse sobre um cartão e selecione o ícone de alfinete para adicionar a visualização a um dashboard.
2. Passe o mouse sobre um cartão, selecione as reticências (...) e escolha **Exibir insights**. Isso abre a tela de insights.
   
    ![Tela inteira do Insight](media/service-insights/power-bi-insight-focus.png)
3. No modo de Foco você pode:
   
   * Filtrar as visualizações.  Para exibir os filtros, no canto superior direito, selecione a seta para expandir o painel Filtros.
        ![analisar um menu de filtros expandido](media/service-insights/power-bi-insights-filter-new.png)
   * Fixe o cartão de insight em um dashboard selecionando o ícone fixar ![ícone fixar](media/service-insights/power-bi-pin-icon.png) ou **Fixar visual**.
   * Execute os insights no próprio cartão. Geralmente, isso é chamado de **insights com escopo**. No canto superior direito, selecione o ícone de lâmpada ![ícone Obter insights](media/service-insights/power-bi-bulb-icon.png) ou **Obter insights**.
     
       ![barra de menus mostrando o ícone Obter Insights](media/service-insights/pbi-autoinsights-tile.png)
     
     O insight é exibido à esquerda e novos cartões, com base apenas nos dados daquele único insight, são exibidos à direita.
     
       ![insights sobre insights](media/service-insights/power-bi-insights-on-insights-new.png)
4. Para voltar à tela original de insights, no canto superior esquerdo, selecione **Sair do modo de foco**.

## <a name="run-insights-on-a-dashboard-tile"></a>Executar insights em um bloco do painel
Em vez de buscar insights em um conjunto de dados inteiro, restrinja sua pesquisa aos dados usados para criar um único bloco de painel. Geralmente, isso também é chamado de **insights com escopo**.

1. Abra um dashboard.
2. Passe o mouse sobre um bloco. selecione as reticências (...) e escolha **Exibir insights**. O bloco é aberto no [modo de foco](service-focus-mode.md) com os cartões de insights exibidos à direita.    
   
    ![Modo de foco](media/service-insights/pbi-insights-tile.png)    
4. Algum insight desperta seu interesse? Selecione esse cartão de insights para se aprofundar ainda mais. O insight selecionado aparece à esquerda e novos insights, com base apenas nos dados daquele único insight, são exibidos à direita.    
6. Continue examinando seus dados e, quando encontrar um insight interessante, fixe-o ao seu painel selecionando **Fixar visual** no canto superior direito.

## <a name="next-steps"></a>Próximas etapas
Se você é proprietário de um conjunto de dados, [otimize-o para os Insights Rápidos](service-insights-optimize.md)

Saiba mais sobre os [tipos de Insights Rápidos disponíveis](service-insight-types.md)

Mais perguntas? [Experimente a Comunidade do Power BI](http://community.powerbi.com/)

