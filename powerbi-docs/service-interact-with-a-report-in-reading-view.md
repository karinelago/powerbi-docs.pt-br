---
title: "Interagir com um relatório na Exibição de Leitura no Power BI"
description: "Interagir com um relatório na Exibição de Leitura no Power BI"
services: powerbi
documentationcenter: 
author: mihart
manager: kfile
backup: 
editor: 
tags: 
qualityfocus: monitoring
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 08/15/2017
ms.author: mihart
ms.openlocfilehash: 54de712e0743801b3e8c565ca997bbc56e254c69
ms.sourcegitcommit: 99cc3b9cb615c2957dde6ca908a51238f129cebb
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/13/2017
---
# <a name="interact-with-a-report-in-reading-view-in-power-bi"></a>Interagir com um relatório na Exibição de Leitura no Power BI
## <a name="reading-view"></a>Modo de Exibição de Leitura
O Modo de Exibição de Leitura não é tão interativo quanto o [Modo de Exibição de Edição](service-interact-with-a-report-in-editing-view.md), mas ainda oferece muitas opções para explorar os dados. Isso é útil ao exibir relatórios [compartilhados com você](service-share-dashboards.md), que podem ser abertos somente no Modo de Exibição de Leitura.

A exibição de Leitura é um modo divertido e seguro de experimentar e conhecer seus dados. Na exibição de Leitura, você pode filtrar e destacar de maneira cruzada os elementos visuais de uma página.  Basta realçar ou selecionar um valor em um visual para ver imediatamente seu impacto sobre os outros visuais. Use o painel Filtrar para adicionar e modificar filtros em uma página de relatório e alterar a maneira como os valores são classificados em uma visualização. Qualquer filtragem e realce que você fizer não serão salvos com o relatório.

## <a name="cross-highlight-the-related-visualizations-on-a-page"></a>Destacar de maneira cruzada as visualizações relacionadas em uma página.
As visualizações em uma página de relatório único são "conectadas" umas às outras.  Isso significa que, se você selecionar um ou mais valores em uma visualização, outras visualizações que usam o mesmo valor serão alteradas com base nessa seleção.

![](media/service-interact-with-a-report-in-reading-view/pagefilter3b.gif)

> [!NOTE]
> Para selecionar mais de um elemento em uma visualização, mantenha pressionada a tecla CTRL.
> 
> 

## <a name="hover-over-visual-elements-to-see-the-details"></a>Focalizar os elementos visuais para ver detalhes
![](media/service-interact-with-a-report-in-reading-view/amarillachart.png)

## <a name="sort-the-data-in-a-visualization"></a>Classificar os dados em uma visualização
Selecione as reticências (...) para abrir **Classificar por**. Selecione a seta suspensa para escolher qual campo classificar, ou selecione o ícone AZ para alternar entre crescente e decrescente. 

![](media/service-interact-with-a-report-in-reading-view/pbi_changechartsort.gif) 

## <a name="interact-with-filters"></a>Interagir com filtros
Se o autor do relatório adicionar filtros a uma página em um relatório, você pode interagir com eles no modo de exibição de leitura. As alterações feitas não serão salvas com o relatório.

1. Selecione o ícone de filtro no canto superior direito.
   
   ![](media/service-interact-with-a-report-in-reading-view/filters.png)  
2. Você verá todos os filtros que foram aplicados ao visual selecionado (Filtros no nível do visual), em toda a página do relatório (Filtros no nível da página) e no relatório inteiro (Filtros no nível do relatório).
   
   ![](media/service-interact-with-a-report-in-reading-view/power-bi-reading-filters.png)
3. Passe o mouse sobre um filtro e expanda-o, selecionando a seta para baixo.
   
   ![](media/service-interact-with-a-report-in-reading-view/power-bi-expan-filter.png)
4. Altere os filtros e veja como os elementos visuais são afetados.  
   
   * Neste exemplo, temos um filtro no nível da Página para **Rede**. Altere-o para **Fashions Direct** em vez de **Lindseys**, removendo a marca de seleção de um deles e adicionando-a ao outro.
     
     ![](media/service-interact-with-a-report-in-reading-view/power-bi-filter-chain.png)
   * Outra opção é remover a filtragem por completo em **Rede** selecionando o ícone de borracha ![](media/service-interact-with-a-report-in-reading-view/power-bi-eraser-icon.png) ou selecionando as lojas da rede.
   * Selecione o filtro de nível de página **Distrito** e mude para **Filtragem avançada**. Filtre para mostrar apenas distritos que começam com **FD** e não contêm o número 4.
     
     ![](media/service-interact-with-a-report-in-reading-view/power-bi-advanced-filter.png)

Para obter mais informações, veja [Adicionar um filtro a um relatório](power-bi-report-add-filter.md) e [Sobre filtros e realce em relatórios](power-bi-reports-filters-and-highlighting.md).

## <a name="zoom-in-on-individual-visuals"></a>Ampliar elementos visuais individuais
Focalize um visual e selecione o ícone do **modo Foco**![](media/service-interact-with-a-report-in-reading-view/pbi_popouticon.jpg). Quando você exibe uma visualização no modo de Foco, ela se expande para preencher toda a tela do relatório, conforme mostrado abaixo.

![](media/service-interact-with-a-report-in-reading-view/powerbi-focus-mode.png)

Para exibir a mesma visualização sem a distração das barras de menu, do painel de filtro e de outros detalhes, selecione o ícone de **Tela Inteira** no menu de barras superior ![](media/service-interact-with-a-report-in-reading-view/power-bi-focus-icon.png).

![](media/service-interact-with-a-report-in-reading-view/power-bi-full-screen.png)

Para obter mais informações, consulte [Modo de foco para relatórios](service-focus-mode.md) e [Modo de Tela Inteira para relatórios](service-fullscreen-mode.md)

## <a name="adjust-the-display-dimensions"></a>Ajustar as dimensões da exibição
Os relatórios são exibidos em vários dispositivos diferentes, com diferentes tamanhos de tela e taxas de proporção.  O processamento padrão pode não ser o que você deseja ver em seu dispositivo.  Para ajustar, selecione **Exibir** e escolha:

* Ajustar à página: ajustar o conteúdo para melhor se ajustar à página
* Ajustar à Largura: ajuste o conteúdo à largura da página
* Tamanho real: exiba o conteúdo em tamanho real  

![](media/service-interact-with-a-report-in-reading-view/power-bi-view.png)

  No modo de leitura, você seleciona a opção de exibição temporária - que não é salvo quando você fecha o relatório.

  Para saber mais, consulte o [Tutorial: Alterar as configurações de exibição em um relatório](power-bi-change-report-display-settings.md).

## <a name="next-steps"></a>Próximas etapas
[Relatórios no Power BI](service-reports.md)

[Abrir o Modo de exibição de edição](service-reading-view-and-editing-view.md)

Mais perguntas? [Experimente a Comunidade do Power BI](http://community.powerbi.com/)

