---
title: "Tutorial – gráficos de medidor radial no Power BI"
description: "Tutorial: Gráficos de medidor radial no Power BI"
services: powerbi
documentationcenter: 
author: mihart
manager: kfile
backup: 
editor: 
tags: 
featuredvideoid: xmja6Epqa
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 01/21/2018
ms.author: mihart
ms.openlocfilehash: 354bfc01231f0f11aabd533bf29f987dec7c9771
ms.sourcegitcommit: 2ae323fbed440c75847dc55fb3e21e9c744cfba0
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2018
---
# <a name="radial-gauge-charts-in-power-bi-tutorial"></a>Gráficos de medidor radial no Power BI (tutorial)
Um gráfico de medidor radial tem um arco circular e exibe um único valor que acompanha o progresso em relação a um objetivo/KPI.  A meta, ou o valor de destino, é representada pela linha (agulha). Progresso em relação a esse objetivo é representado pelo sombreamento.  E o valor que representa o progresso é mostrado em negrito dentro do arco. Todos os valores possíveis são distribuídos uniformemente ao longo do arco, do mínimo (valor mais à esquerda) para o máximo (valor mais à direita).

No exemplo a seguir, somos um revendedor de carro, controlando a média de vendas da nossa equipe por mês. Nosso objetivo é 140 e é representado pela agulha preta.  A média mínima possível de vendas é 0 e definimos o máximo como 200.  O sombreamento azul mostra que temos atualmente uma média de aproximadamente 120 vendas neste mês. Felizmente, ainda temos outra semana para atingir a nossa meta.

![](media/power-bi-visualization-radial-gauge-charts/gauge_m.png)

## <a name="when-to-use-a-radial-gauge"></a>Quando usar um medidor radial
Os medidores radiais são uma ótima opção para:

* mostrar o progresso para atingir uma meta.
* representar uma medida percentual, como um KPI.
* mostrar a integridade de uma única medida.
* exibir informações que podem ser examinadas e compreendidas rapidamente.

### <a name="prerequisites"></a>Pré-requisitos
 - Serviço do Power BI ou Power BI Desktop
 - Pasta de trabalho do Excel de exemplo financeiro: [baixe o exemplo diretamente](http://go.microsoft.com/fwlink/?LinkID=521962).

## <a name="create-a-basic-radial-gauge"></a>Criar um medidor radial básico
Estas instruções usam o serviço do Power BI. Para acompanhar, entre no Power BI e abra o arquivo Exemplo Financeiro do Excel.  

Ou veja Will mostrando como criar elementos visuais de métrica únicos: medidores, cartões e KPIs.

<iframe width="560" height="315" src="https://www.youtube.com/embed/xmja6EpqaO0?list=PL1N57mwBHtN0JFoKSR0n-tBkUJHeMP2cP" frameborder="0" allowfullscreen></iframe>

### <a name="step-1-open-the-financial-sample-excel-file"></a>Etapa 1: abrir o arquivo do Excel de Exemplo Financeiro
1. [Baixe o arquivo do Excel de exemplo Financeiro](sample-financial-download.md) se ainda não tiver feito isso. Lembre-se do local em que você o salvou.

2. Abra o arquivo no ***serviço do Power BI*** selecionando **Obter dados \> Arquivos** e navegando até o local em que você salvou o arquivo. Selecione **Importar**. A Amostra Financeira é adicionada a seu espaço de trabalho como um conjunto de dados.

3. Da lista de conteúdo **Conjunto de dados**, selecione **Exemplo Financeiro** para abri-lo no modo de Explorar.

    ![](media/power-bi-visualization-radial-gauge-charts/power-bi-dataset.png)

### <a name="step-2-create-a-gauge-to-track-gross-sales"></a>Etapa 2: criar um medidor para acompanhar as Vendas Brutas
1. No painel **Campos** , selecione **Vendas Brutas**.
   
   ![](media/power-bi-visualization-radial-gauge-charts/grosssalesvalue_new.png)
2. Altere a agregação para **Médio**.
   
   ![](media/power-bi-visualization-radial-gauge-charts/changetoaverage_new.png)
3. Selecione o ícone de medidor ![](media/power-bi-visualization-radial-gauge-charts/gaugeicon_new.png) para converter o Gráfico de colunas em um medidor.
   
   Por padrão, o Power BI cria um gráfico de medidor no qual o valor atual (nesse caso, média de vendas brutas) deve estar no ponto na metade do medidor. Como a Média das Vendas Brutas é de US$ 182.760, o valor inicial (Mínimo) é definido como 0 e o valor final (Máximo) é definido como o dobro do valor atual.
   
   ![](media/power-bi-visualization-radial-gauge-charts/gauge_no_target.png)

### <a name="step-3-set-a-target-value"></a>Etapa 3: definir um valor de destino
1. Arraste **COGS** para o contêiner **Valor de destino** .
2. Altere a agregação para **Médio**.
   O Power BI adiciona uma agulha para representar o valor de destino de **US$ 145.480**. Observe que ultrapassamos o nosso alvo.
   
   ![](media/power-bi-visualization-radial-gauge-charts/gaugeinprogress_new.png)
   
   > [!NOTE]
   > Você pode inserir manualmente um valor de destino.  Veja “Usar as opções de formatação para definir manualmente os valores Mínimo, Máximo e Destino” abaixo.
   > 
   > 

### <a name="step-4-set-a-maximum-value"></a>Etapa 4: definir um valor máximo
Na Etapa 2, o Power BI usou o campo Valor para definir automaticamente o mínimo (início) e o máximo (final).  Mas e se você quiser definir seu próprio valor máximo?  Digamos que, em vez de usar o dobro do valor atual como o valor máximo possível, você deseja defini-lo como o maior número de vendas brutas no conjunto de dados? 

1. Arraste **Vendas Brutas** da lista **Campos** para o **Valor Máximo** também.
2. Altere a agregação para **Máximo**.
   
   ![](media/power-bi-visualization-radial-gauge-charts/setmaximum_new.png)
   
   O medidor é redesenhado com um novo valor de término, 1,21 milhão em vendas brutas.
   
   ![](media/power-bi-visualization-radial-gauge-charts/power-bi-final-gauge.png)

### <a name="step-5-save-your-report"></a>Etapa 5: salvar o relatório
1. [Salve o relatório](service-report-save.md).
2. [Adicione o gráfico de medidor como um bloco do dashboard](service-dashboard-tiles.md). 

## <a name="use-formatting-options-to-manually-set-minimum-maximum-and-target-values"></a>Use as opções de formatação para definir manualmente os valores Mínimo, Máximo e Destino
1. Remova **Vendas Brutas Máx.** do **Valor máximo** também.
2. Abra o painel de formatação selecionando o ícone do rolo de pintura.
   
   ![](media/power-bi-visualization-radial-gauge-charts/power-bi-roller.png)
3. Expanda o **Eixo indicador** e insira valores para **Mín.** e **Máx**.
   
    ![](media/power-bi-visualization-radial-gauge-charts/power-bi-gauge-axis.png)
4. Remova o valor de destino atual removendo a marca de seleção ao lado de **COGS**.
   
    ![](media/power-bi-visualization-radial-gauge-charts/pbi_remove_target.png)
5. Quando o campo **Destino** aparecer no **Eixo do medidor**, insira um valor.
   
    ![](media/power-bi-visualization-radial-gauge-charts/power-bi-gauge-target.png)
6. Como opção, continue com a formatação do gráfico de medidor.

## <a name="next-steps"></a>Próximas etapas
[Tipos de visualização no Power BI](power-bi-visualization-types-for-reports-and-q-and-a.md)

[Adicionar uma visualização a um relatório](power-bi-report-add-visualizations-i.md)

[Fixar uma visualização em um dashboard](service-dashboard-pin-tile-from-report.md)

[ Power BI – conceitos básicos](service-basic-concepts.md)

Mais perguntas? [Experimente a Comunidade do Power BI](http://community.powerbi.com/)

