---
title: "Gráfico de combinação no Power BI (tutorial)"
description: "Esta documentação consiste em um tutorial (com vídeo) que mostra por que e como criar um Gráfico de Combinação no Power BI."
services: powerbi
documentationcenter: 
author: mihart
manager: kfile
backup: 
editor: 
tags: 
featuredvideoid: lnv66cTZ5ho
qualityfocus: monitoring
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 10/27/2017
ms.author: mihart
ms.openlocfilehash: c00ba74501a411743036c4514750bccbbae3eb00
ms.sourcegitcommit: 99cc3b9cb615c2957dde6ca908a51238f129cebb
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/13/2017
---
# <a name="combo-chart-in-power--tutorial"></a>Gráfico de combinação no Power (tutorial)
No Power BI, um gráfico de combinação é uma visualização única que combina um gráfico de linhas e um gráfico de colunas. Combinando os 2 gráficos em um permite você faça uma comparação rápida dos dados.

Os gráficos de combinação podem ter um ou dois eixos Y.

## <a name="when-to-use-a-combo-chart"></a>Quando usar um gráfico de combinação?
Os gráficos de combinação são uma ótima opção:

* Quando você tem um gráfico de linhas e um gráfico de colunas com o mesmo eixo X.
* para comparar várias medidas com intervalos de valores diferentes.
* para ilustrar a correlação entre duas medidas em uma visualização.
* para verificar se uma medida atende o destino definido pela outra medida
* para conservar o espaço de tela.

## <a name="create-a-basic-single-axis-combo-chart"></a>Criar um gráfico de combinação básico de eixo único
Veja Will criar um gráfico de combinação usando a amostra de Vendas e Marketing.

<iframe width="560" height="315" src="https://www.youtube.com/embed/lnv66cTZ5ho?list=PL1N57mwBHtN0JFoKSR0n-tBkUJHeMP2cP" frameborder="0" allowfullscreen></iframe>


Para criar seu próprio gráfico de combinação, entre no Power BI e selecione **Obter Dados \> Amostras \> Amostra de Análise de Varejo**. 

1. No painel "Exemplo de análise de varejo", selecione o bloco **Armazenamentos Totais** para abrir o relatório “Exemplo de Análise de Varejo”.
2. Selecione **Editar relatório** para abrir o relatório no modo de Exibição de Edição.
3. [Adicione uma nova página do relatório](power-bi-report-add-page.md).
4. Crie um gráfico de coluna que exibe as vendas deste e margem bruta por mês.
   
    a.  No painel Campos, selecione **Vendas** \> **Vendas do Deste Ano** > **Valor**.
   
    b.  Arraste **Vendas** \> **Margem Bruta Deste Ano** para a seção **Valor**.
   
    c.  Selecione **Hora** \> **FiscalMonth** para adicioná-la à seção **Eixo**. 
   
    ![](media/power-bi-visualization-combo-chart/combotutorial1new.png)
5. Selecione as reticências (...) no canto superior direito da visualização e escolha **Classificar por FiscalMonth**.
6. Converta o gráfico de colunas em um gráfico de combinação. Com o gráfico de coluna selecionado, no painel **Visualizações**, selecione o **Gráfico de colunas agrupadas e linha**.
   
    ![](media/power-bi-visualization-combo-chart/converttocombo_new2.png)
7. No painel **Campos**, arraste **Vendas** \> **Vendas do Ano Passado** para o bucket **Valores de Linha**.
   
   ![](media/power-bi-visualization-combo-chart/linevaluebucket.png)
   
   O gráfico de combinação deve ter esta aparência:
   
   ![](media/power-bi-visualization-combo-chart/combochartdone-new.png)

## <a name="create-a-combo-chart-with-two-axes"></a>Criar um gráfico de combinação com dois eixos
Nesta tarefa, vamos comparar as vendas e a margem bruta.

1. Crie um novo gráfico de linhas que acompanha o percentual de margem bruta do ano passado por mês.  Em janeiro, a % de Margem Bruta foi de 35%, chegando ao seu máximo em 45% em abril, caindo em julho e chegando ao seu máximo novamente em agosto. Será que vamos ver um padrão semelhante nas vendas do ano passado e deste ano?
   
   ![](media/power-bi-visualization-combo-chart/combo1_new.png)
2. Adicione **Vendas deste ano > Valor** e **Vendas do último ano** no gráfico de linhas. A escala de **% de Margem Bruta do Ano Passado** é muito menor do que a escala de **Vendas** , o que dificulta a comparação.      
   
   ![](media/power-bi-visualization-combo-chart/flatline_new.png)
3. Para tornar o visual mais fácil de ler e interpretar, converta o gráfico de linhas em um gráfico de linha e coluna empilhada.
   
   ![](media/power-bi-visualization-combo-chart/converttocombo_new.png)
4. Arraste **% de Margem Bruta no Ano Passado** de **Valores de Coluna** para **Valores de Linha**. O Power BI cria dois eixos, permitindo que os conjuntos de dados sejam escalonados de modo diferente: o eixo à esquerda calcula dólares e o eixo à direita calcula o percentual.
   
   ![](media/power-bi-visualization-combo-chart/power-bi-combochart.png)    

## <a name="add-titles-to-the-axes"></a>Adicionar títulos aos eixos
1. Selecione o ícone de rolo de pintura ![](media/power-bi-visualization-combo-chart/power-bi-paintroller.png) para abrir o painel Formatação.
2. Selecione a seta para baixo para expandir as opções do **eixo Y** .
3. Para o **Eixo Y (Coluna)**, defina a **Posição** para a **Esquerda**, o **Título** como **Ativado**, o **Estilo** como **Mostrar somente o título** e a **Exibição** como **Milhões**.
   
   ![](media/power-bi-visualization-combo-chart/power-bi-y-axis-column.png)
4. No **Eixo Y (coluna)**, verifique também se **Mostrar secundário** está **Ativado**. Isso exibe as opções para formatar a seção de gráfico de linhas do gráfico de combinação.
   
   ![](media/power-bi-visualization-combo-chart/power-bi-show-secondary.png)
5. Para o **Eixo Y (Linha)**, deixe a **Posição** como **Direita**, altere o **Título** para **Ativado** e defina o **Estilo** para **Mostrar apenas título**.
   
   Seu gráfico de combinação agora exibe eixos duplos, ambos com títulos.
   
   ![](media/power-bi-visualization-combo-chart/power-bi-titles-on.png)

Daqui, talvez você queira:

* [Adicione o gráfico de combinação como um bloco do dashboard](service-dashboard-tiles.md).
* [Salve o relatório](service-report-save.md).

## <a name="highlighting-and-cross-filtering"></a>Realce e filtragem cruzada
Para obter informações sobre como usar o painel Filtros, veja [Adicionar um filtro a um relatório](power-bi-report-add-filter.md).

Realçar uma coluna ou uma linha em um gráfico de combinação faz a filtragem cruzada com outras visualizações na página do relatório e vice-versa.

## <a name="next-steps"></a>Próximas etapas
[Adicionar uma visualização a um relatório](power-bi-report-add-visualizations-i.md)

[Visualizações em relatórios do Power BI](power-bi-report-visualizations.md)

[Tipos de visualização no Power BI](power-bi-visualization-types-for-reports-and-q-and-a.md)

[Power BI – conceitos básicos](service-basic-concepts.md)

[Experimente – é gratuito!](https://powerbi.com/)

Mais perguntas? [Experimente a Comunidade do Power BI](http://community.powerbi.com/)
