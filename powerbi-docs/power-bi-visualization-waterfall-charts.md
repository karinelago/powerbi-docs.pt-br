---
title: "Gráficos de cascata no Power BI (tutorial)"
description: "Tutorial: Gráficos de cascata no Power BI"
services: powerbi
documentationcenter: 
author: mihart
manager: kfile
backup: 
editor: 
tags: 
featuredvideoid: maTzOJSRB3g
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 01/20/2018
ms.author: mihart
ms.openlocfilehash: 24eea40512f8aa6765032399160f0e18dc29c71a
ms.sourcegitcommit: 2ae323fbed440c75847dc55fb3e21e9c744cfba0
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2018
---
# <a name="waterfall-charts-in-power-bi-tutorial"></a>Gráficos de cascata no Power BI (tutorial)
O gráfico de cascata mostram uma duração total conforme os valores são adicionados ou subtraídos. É útil para entender como um valor inicial (por exemplo, a receita líquida) é afetado por uma série de alterações positivas e negativas.

As colunas são codificadas para que você possa rapidamente aumentar e diminuir. Com frequência, as colunas de valor inicial e final [iniciam-se no eixo horizontal](https://support.office.com/article/Create-a-waterfall-chart-in-Office-2016-for-Windows-8de1ece4-ff21-4d37-acd7-546f5527f185#BKMK_Float "iniciam-se no eixo horizontal"), enquanto os valores intermediários são colunas flutuantes. Devido a essa "aparência", os gráficos de cascata também são chamados de gráficos de ponte.

<iframe width="560" height="315" src="https://www.youtube.com/embed/qKRZPBnaUXM" frameborder="0" allow="autoplay; encrypted-media" allowfullscreen></iframe>

## <a name="when-to-use-a-waterfall-chart"></a>Ao usar um gráfico de cascata
Os gráficos de cascata são uma ótima opção:

* quando houver alterações de medida em uma série de tempo ou categorias diferentes
* para auditar as principais alterações que contribuem para o valor total
* para traçar o lucro anual da empresa, mostrando várias fontes de receita e chegar ao lucro total (ou perda).
* para ilustrar o início e final do número de funcionários de sua empresa em um ano
* para visualizar a quantidade de dinheiro, faça e gaste todo mês e o saldo parcial para sua conta. 

## <a name="create-a-waterfall-chart"></a>Criar um gráfico de cascata
Criaremos um gráfico de cascata que exibe a variação de vendas (vendas estimadas versus vendas reais) por mês. Para acompanhar, entre no Power BI e selecione **Obter Dados \> Amostras \> Amostra de Análise de Varejo**. 

1. Selecione a guia **Conjuntos de dados** e role até o novo conjunto de dados "Exemplo de Análise de Varejo".  Selecione o ícone **Criar relatório** para abrir o conjunto de dados no modo de exibição de edição de relatório. 
   
    ![](media/power-bi-visualization-waterfall-charts/power-bi-waterfall-report.png)
2. No painel **Campos**, selecione **Vendas \> Variação do Total de Vendas**. Se a **Variação Total de Vendas** não está na área do **eixo Y** , arraste-o para lá.
3. Converter o gráfico para uma **Cascata**. 
   
    ![](media/power-bi-visualization-waterfall-charts/convertwaterfall.png)
4. Selecione **Hora** \> **FiscalMonth** para adicioná-la à seção **Categoria**. 
   
    ![](media/power-bi-visualization-waterfall-charts/power-bi-waterfall.png)
5. Classifique o gráfico de cascata em ordem cronológica. No canto direito do gráfico, selecione as reticências (...) e **FiscalMonth**.
   
    ![](media/power-bi-visualization-waterfall-charts/power-bi-waterfall-sort.png)
   
    ![](media/power-bi-visualization-waterfall-charts/power-bi-waterfall-sorted.png)
6. Aprofunde-se um pouco mais para ver o que está contribuindo mais para as alterações a cada mês. Arraste **Repositório** > **Região** para o bucket **Divisão**.
   
    ![](media/power-bi-visualization-waterfall-charts/power-bi-waterfall-breakdown.png)
7. Por padrão, o Power BI adiciona os cinco principais colaboradores a aumentos ou diminuições por mês. Mas queremos apenas os dois colaboradores principais.  No painel de formatação, selecione **Divisão** e defina **Máximo** como 2.
   
    ![](media/power-bi-visualization-waterfall-charts/power-bi-waterfall-breakdown-maximum.png)
   
    Uma rápida análise revela que as regiões de Ohio e Pensilvânia são os maiores colaboradores para a movimentação, negativa e positiva, em nosso gráfico de cascata. 
   
    ![](media/power-bi-visualization-waterfall-charts/power-bi-waterfall-axis.png)
8. Essa é uma descoberta interessante. Ohio e Pensilvânia têm um impacto significativo por as vendas nessas duas regiões serem muito maiores do que nas outras?  Podemos verificar isso. Crie um mapa que analise as vendas por região.  
   
    ![](media/power-bi-visualization-waterfall-charts/power-bi-map.png)
   
    Nosso mapa corrobora nossa teoria.  Ele mostra que essas duas regiões tiveram o valor mais alto de vendas no ano passado (tamanho da bolha) e neste ano (sombreamento da bolha).

## <a name="highlighting-and-cross-filtering"></a>Realce e filtragem cruzada
Para obter informações sobre como usar o painel Filtros, veja [Adicionar um filtro a um relatório](power-bi-report-add-filter.md).

Realçar uma coluna em um gráfico de cascata faz a filtragem cruzada dos filtros com outras visualizações na página do relatório e vice-versa. No entanto, a coluna Total não dispara o realce ou responda a filtragem cruzada.

## <a name="next-steps"></a>Próximas etapas
[Relatórios no Power BI](service-reports.md)

[Tipos de visualização no Power BI](power-bi-visualization-types-for-reports-and-q-and-a.md)

[Visualizações em relatórios do Power BI](power-bi-report-visualizations.md)

[Power BI – conceitos básicos](service-basic-concepts.md)

Mais perguntas? [Experimente a Comunidade do Power BI](http://community.powerbi.com/)

