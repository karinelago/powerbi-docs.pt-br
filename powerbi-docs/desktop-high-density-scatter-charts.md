---
title: Gráficos de dispersão de alta densidade no Power BI
description: Gráficos de dispersão de alta densidade no Power BI
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 04/19/2018
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: 6df40c8229575a7e6167e75b773228cbd18d1243
ms.sourcegitcommit: 80d6b45eb84243e801b60b9038b9bff77c30d5c8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34291110"
---
# <a name="high-density-sampling-in-power-bi-scatter-charts"></a>Amostragem de alta densidade em gráficos de dispersão do Power BI
Começando com a versão de setembro de 2017 do **Power BI Desktop** e as atualizações do **serviço do Power BI**, está disponível um novo algoritmo de amostragem que melhora como os gráficos de dispersão representam dados de alta densidade.

Por exemplo, você pode criar um gráfico de dispersão com base na atividade de vendas de sua organização, com cada loja tendo dezenas de milhares de pontos de dados a cada ano. Um gráfico de dispersão de informações como essas extrairia dados de amostra (selecione uma representação significativa dos dados, para ilustrar como as vendas ocorreram ao longo do tempo) dos dados disponíveis e criaria um gráfico de dispersão representando os dados subjacentes. Essa é uma prática comum em gráficos de dispersão de alta densidade. O Power BI melhorou sua amostragem de dados de alta densidade, cujos detalhes estão descritos neste artigo.

![](media/desktop-high-density-scatter-charts/high-density-scatter-charts_01.png)

> [!NOTE]
> O algoritmo de **Amostragem de Alta Densidade** descrito neste artigo está disponível no gráfico de dispersão do **Power BI Desktop** e do **serviço do Power BI**.
> 
> 

## <a name="how-high-density-scatter-charts-work"></a>Como funcionam os gráficos de dispersão de alta densidade
Anteriormente, o **Power BI** selecionava uma coleção de pontos de dados de exemplo em toda a gama de dados subjacentes de uma maneira determinística para criar um gráfico de dispersão. Especificamente, o Power BI selecionava as primeira e última linhas de dados na série de gráficos de dispersão e, em seguida, dividia as linhas restantes igualmente, de modo que o total de 3.500 pontos de dados fossem plotados no gráfico de dispersão. Por exemplo, se a amostra tivesse 35.000 linhas, a primeira e a última linha seriam selecionadas para plotagem e, a cada dez linhas, as linhas também seriam plotadas (35.000/10 = a cada dez linhas = 3.500 pontos de dados). Além disso, antes, os pontos ou valores nulos que não podiam ser plotados (como valores de texto) na série de dados não eram mostrados e, portanto, não eram considerados durante a geração do visual. Com essa amostragem, a densidade percebida do gráfico de dispersão também era baseada nos pontos de dados representativos e, portanto, a densidade implícita do visual era uma particularidade dos pontos amostrados e não da coleção completa dos dados subjacentes.

Quando você habilita a **Amostragem de Alta Densidade**, o Power BI implementa um algoritmo que elimina os pontos sobrepostos e garante que os pontos no visual possam ser alcançados durante a interação com o visual. O algoritmo também garante que todos os pontos no conjunto de dados sejam representados no visual, fornecendo contexto para o significado dos pontos selecionados, em vez de apenas plotar uma amostra representativa.

Por definição, os dados de alta densidade são amostrados para criar com uma rapidez razoável visualizações que atendam à interatividade. Um número muito grande de pontos de dados em um visual pode atrasá-lo e diminuir a visibilidade de tendências. Portanto, a maneira em que esses dados são amostrados é o que orienta a criação do algoritmo de amostragem para oferecer a melhor experiência de visualização e garantir que todos os dados sejam representados. No Power BI, o algoritmo foi melhorado para fornecer a melhor combinação de capacidade de resposta, representação e preservação clara de pontos importantes no conjunto de dados geral.

> [!NOTE]
> Os gráficos de dispersão que usam o algoritmo de **Amostragem de Alta Densidade** são mais bem plotados em visuais quadrados, assim como ocorre com todos os gráficos de dispersão.
> 
> 

## <a name="how-the-new-scatter-chart-sampling-algorithm-works"></a>Como funciona o novo algoritmo de amostragem de gráfico de dispersão
O novo algoritmo de **Amostragem de Alta Densidade** para gráficos de dispersão usa métodos que capturam e representam os dados subjacentes com mais eficiência e elimina os pontos sobrepostos. Ele faz isso começando com um pequeno raio em cada ponto de dados (o tamanho do círculo visual de determinado ponto na visualização). Em seguida, ele aumenta o raio de todos os pontos de dados; quando dois (ou mais) pontos de dados são sobrepostos, um único círculo (do tamanho do raio maior) representa os pontos de dados sobrepostos. O algoritmo continua aumentando o raio dos pontos de dados até que o valor do raio resulte em um número razoável de pontos de dados – 3.500 – exibidos no gráfico de dispersão.

Os métodos deste algoritmo garantem que as exceções sejam representadas no visual resultante. O algoritmo respeita a escala ao determinar a sobreposição também, de modo que as escalas exponenciais sejam visualizadas com fidelidade aos pontos subjacentes visualizados.

O algoritmo também preserva a forma geral do gráfico de dispersão.

> [!NOTE]
> Ao usar o algoritmo de **Amostragem de Alta Densidade** para gráficos de dispersão, a *distribuição precisa* dos dados é a meta e a densidade implícita do visual *não* é a meta. Por exemplo, talvez você veja um gráfico de dispersão com vários círculos que se sobrepõem (densidade) em determinada área e imagine que muitos pontos de dados devem estar clusterizados nele. Como o algoritmo de **Amostragem de Alta Densidade** pode usar um único círculo para representar muitos pontos de dados, uma densidade implícita do visual como essa (ou “clustering”) não será mostrada. Para obter mais detalhes de determinada área, use as segmentações para ampliar.
> 
> 

Além disso, os pontos de dados que não podem ser plotados (como valores nulos ou valores de texto) são ignorados, para que outro valor que pode ser plotado seja selecionado, garantindo ainda que a forma verdadeira do gráfico de dispersão seja mantida.

### <a name="when-the-standard-algorithm-for-scatter-charts-is-used"></a>Quando o algoritmo padrão para gráficos de dispersão é usado
Há circunstâncias em que a **Amostragem de Alta Densidade** não pode ser aplicada a um gráfico de dispersão e o algoritmo original é usado. Essas circunstâncias são as seguintes:

* Se você clicar com o botão direito do mouse em um valor em **Detalhes** e defini-lo como **Mostrar itens sem dados** no menu, o gráfico de dispersão será revertido para o algoritmo original.
  
  ![](media/desktop-high-density-scatter-charts/high-density-scatter-charts_02.png)
* Os valores do eixo **Reproduzir** resultarão na reversão do gráfico de dispersão para o algoritmo original.
* Se os eixos X e Y estiverem ausentes em um gráfico de dispersão, o gráfico será revertido para o algoritmo original.
* O uso de uma **Linha de proporção** no painel **Análise** resulta na reversão do gráfico para o algoritmo original.
  
  ![](media/desktop-high-density-scatter-charts/high-density-scatter-charts_03.png)

## <a name="how-to-turn-on-high-density-sampling-for-a-scatter-chart"></a>Como ativar a amostragem de alta densidade em um gráfico de dispersão
Para ativar a **Amostragem de Alta Densidade**, selecione um gráfico de dispersão, acesse o painel **Formatação**, expanda o cartão **Geral** e, na parte inferior do cartão, deslize o controle deslizante de alternância **Amostragem de Alta Densidade** para **Ativar**.

![](media/desktop-high-density-scatter-charts/high-density-scatter-charts_04.png)

> [!NOTE]
> Depois que o controle deslizante for ativado, o Power BI tentará usar o algoritmo de **Amostragem de Alta Densidade** sempre que possível. Quando o algoritmo não puder ser usado (por exemplo, você coloca um valor no eixo *Reproduzir*), o controle deslizante permanecerá na posição **Ativado** mesmo que o gráfico tenha sido revertido para o algoritmo padrão. Se, em seguida, você remover um valor do eixo *Reproduzir* (ou se mudarem as condições para habilitar o uso do algoritmo de amostragem de alta densidade), o gráfico usará a amostragem de alta densidade automaticamente neste gráfico porque o recurso estará ativo.
> 
> [!NOTE]
> Os pontos de dados são agrupados ou selecionados pelo índice. Ter uma legenda não afeta a amostragem do algoritmo, somente a ordenação do visual.
> 
> 

## <a name="considerations-and-limitations"></a>Considerações e limitações
O algoritmo de amostragem de alta densidade é uma melhoria importante no Power BI, mas há algumas considerações que você precisa saber ao trabalhar com valores de alta densidade e gráficos de dispersão.

* O algoritmo de **Amostragem de Alta Densidade** funciona apenas com conexões dinâmicas em modelos baseados no serviço do Power BI, modelos importados ou o DirectQuery.

## <a name="next-steps"></a>Próximas etapas
Para obter mais informações sobre amostragem de alta densidade em outros gráficos, confira o artigo a seguir.

* [Amostragem de linha de alta densidade no Power BI](desktop-high-density-sampling.md)

