---
title: "Gráfico de áreas básico (tutorial)"
description: "Tutorial: gráfico de Área Básica."
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
ms.openlocfilehash: 42e068b11c22c32f1a6736a6ca8f9020594fb40a
ms.sourcegitcommit: 284b09d579d601e754a05fba2a4025723724f8eb
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/15/2017
---
# <a name="basic-area-chart-tutorial"></a>Gráfico de áreas básico (tutorial)
O gráfico de áreas básico (também conhecido como gráfico de áreas em camadas) baseia-se no gráfico de linhas. A área entre o eixo e a linha é preenchida com cores para indicar o volume. 

Os gráficos de área enfatizam a magnitude da alteração ao longo do tempo e pode ser usado para chamar a atenção para o valor total entre uma tendência. Por exemplo, os dados que representam o lucro ao longo do tempo podem ser plotados em um gráfico de área para enfatizar o lucro total.

![](media/power-bi-visualization-basic-area-chart/powerbi-area-chartnew.png)

## <a name="when-to-use-a-basic-area-chart"></a>Quando usar um gráfico de áreas básico
Os gráficos de áreas básicos são uma ótima opção:

* para ver e comparar as tendências de volume em série de tempo 
* para as séries individuais representando conjunto contável fisicamente

## <a name="create-a-basic-area-chart"></a>Criar um gráfico de áreas básico
Para acompanhar, entre no Power BI e selecione **Obter Dados \> Amostras \> Amostra de Análise de Varejo**. 

1. No painel "Exemplo de análise de varejo", selecione o bloco **Armazenamentos Totais** para abrir o relatório “Exemplo de Análise de Varejo”.
2. Selecione **Editar relatório** para abrir o relatório no modo de Exibição de Edição.
3. Adicione uma nova página de relatório.
4. Crie um novo gráfico de área que mostra este ano de vendas e as vendas do ano passado por mês.
   
   a.  No **painel Campos**, selecione **Vendas \> Vendas do Último Ano** e **Vendas Deste Ano > Valor**.
   
   b.  Converta o gráfico em um gráfico de áreas básico.    
   ![](media/power-bi-visualization-basic-area-chart/convertchart.png)
   
   c.  Selecione **Hora \> Mês** para adicionar ao **Eixo**.   
   ![](media/power-bi-visualization-basic-area-chart/powerbi-area-chartnew.png)
   
   d.  Para exibir o gráfico por mês, selecione as reticências (canto superior direito do visual) e escolha **Classificar por mês**.

## <a name="highlighting-and-cross-filtering"></a>Realce e filtragem cruzada
Para obter informações sobre como usar o painel Filtros, veja [Adicionar um filtro a um relatório](power-bi-report-add-filter.md).

Para selecionar uma área, clique dentro dessa área ou ao longo da linha superior.  Os gráficos de áreas básicos não cruzam o filtro das outras visualizações na página do relatório. No entanto, os gráficos de áreas são um alvo de filtragem cruzada acionado por outras visualizações na página do relatório.

## <a name="considerations-and-troubleshooting"></a>Considerações e solução de problemas
* Gráficos de áreas básicos não são eficazes para comparar os valores devido à oclusão nas áreas em camadas. O Power BI usa transparência para indicar a sobreposição das áreas. No entanto, ele só funciona bem com duas ou três áreas diferentes. Quando você precisa comparar tendência com mais de três medidas, tente usar os gráficos de linhas. Quando você precisa comparar volume com mais de três medidas, tente usar o mapa de árvore.

## <a name="next-steps"></a>Próximas etapas
[Relatórios no Power BI](service-reports.md)  
[Visualizações em relatórios do Power BI](power-bi-report-visualizations.md)  
[Power BI – conceitos básicos](service-basic-concepts.md)  
Mais perguntas? [Experimente a Comunidade do Power BI](http://community.powerbi.com/)

