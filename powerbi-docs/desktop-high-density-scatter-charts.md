---
title: "Gráficos de dispersão de alta densidade no Power BI"
description: "Gráficos de dispersão de alta densidade no Power BI"
services: powerbi
documentationcenter: 
author: davidiseminger
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
ms.date: 12/06/2017
ms.author: davidi
ms.openlocfilehash: 21a02c4d8dabd445afaadb43529489b3253d3599
ms.sourcegitcommit: d91436de68a0e833ecff18d976de9d9431bc4121
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/06/2017
---
# <a name="high-density-sampling-in-power-bi-scatter-charts"></a>Amostragem de alta densidade em gráficos de dispersão do Power BI
A partir da versão de setembro de 2017 do **Power BI Desktop** e das atualizações no **serviço do Power BI**, um novo algoritmo de amostragem está disponível, que melhora a maneira como os gráficos de dispersão representam dados de alta densidade.

Por exemplo, você pode criar um gráfico de dispersão com base na atividade de vendas de sua organização, com cada loja tendo dezenas de milhares de pontos de dados a cada ano. Um gráfico de dispersão de informações como essas extrairá uma amostra de dados (selecione uma representação significativa dos dados, para ilustrar como as vendas ocorreram ao longo do tempo) dos dados disponíveis e crie um gráfico de dispersão que representa os dados subjacentes. Essa é uma prática comum nos gráficos de dispersão de alta densidade e o Power BI melhorou sua amostragem de dados de alta densidade, cujos detalhes são descritos neste artigo.

![](media/desktop-high-density-scatter-charts/high-density-scatter-charts_01.png)

> [!NOTE]
> O algoritmo de **amostragem de alta densidade** descrito neste artigo aplica-se a e está disponível no gráfico de dispersão no **Power BI Desktop** e no **serviço do Power BI**.
> 
> 

## <a name="how-high-density-scatter-charts-work"></a>Como funcionam os gráficos de dispersão de alta densidade
Anteriormente, o **Power BI** selecionava uma coleção de pontos de dados de exemplo em toda a gama de dados subjacentes de uma maneira determinística para criar um gráfico de dispersão. Especificamente, o Power BI selecionava as primeira e última linhas de dados na série de gráficos de dispersão e, em seguida, dividia as linhas restantes igualmente, de modo que o total de 3.500 pontos de dados fossem plotados no gráfico de dispersão. Por exemplo, se a amostra tivesse 35.000 linhas, as primeira e última linhas seriam selecionadas para plotagem e, a cada dez linhas, as linhas também seriam plotadas (35.000/10 = a cada dez linhas = 3.500 pontos de dados). Também anteriormente, pontos ou valores nulos que não podiam ser plotados (como valores de texto) na série de dados não eram mostrados e, portanto, não eram considerados durante a geração do visual. Com tal amostragem, a densidade percebida do gráfico de dispersão também era baseada nos pontos de dados representativos e, portanto, a densidade implícita do visual era uma particularidade dos pontos amostrados e não da coleção completa dos dados subjacentes.

Quando você habilita a **Amostragem de Alta Densidade**, o Power BI implementa um algoritmo que elimina os pontos sobrepostos e garante que os pontos no visual possam ser alcançados durante a interação com o visual. Ele também garante que todos os pontos no conjunto de dados sejam representados no visual, fornecendo contexto para o significado dos pontos selecionados, em vez de apenas plotar uma amostra representativa.

Por definição, os dados de alta densidade são amostrados para proporcionar visualizações que podem ser criadas com razoável rapidez e que são dinâmicas à interatividade (o excesso de pontos de dados em um visual pode sobrecarregá-lo e desviar a atenção da visibilidade das tendências). A maneira como esses dados são amostrados, para oferecer a melhor experiência de visualização e garantir que todos os dados sejam representados, é o que orienta a criação do algoritmo de amostragem. No Power BI, o algoritmo foi aprimorado para fornecer a melhor combinação de capacidade de resposta, representação e preservação clara de pontos importantes no conjunto de dados geral.

> [!NOTE]
> Os gráficos de dispersão que usam o algoritmo de **amostragem de alta densidade** são mais bem plotados em visuais quadrados, assim como ocorre com todos os gráficos de dispersão.
> 
> 

## <a name="how-the-new-scatter-chart-sampling-algorithm-works"></a>Como funciona o novo algoritmo de amostragem de gráfico de dispersão
O novo algoritmo de **Amostragem de Alta Densidade** para gráficos de dispersão utiliza métodos que capturam e representam os dados subjacentes com mais eficiência e eliminam pontos sobrepostos. Ele faz isso começando com um pequeno raio em cada ponto de dados (o tamanho do círculo visual de determinado ponto na visualização). Em seguida, ele aumenta o raio de todos os pontos de dados; quando dois (ou mais) pontos de dados são sobrepostos, um único círculo (do tamanho do raio maior) representa os pontos de dados sobrepostos. O algoritmo continua aumentando o raio dos pontos de dados até que o valor do raio resulte em um número razoável de pontos de dados – 3.500 – exibidos no gráfico de dispersão.

Os métodos deste algoritmo garantem que as exceções sejam representadas no visual resultante. O algoritmo respeita a escala ao determinar a sobreposição também, de modo que as escalas exponenciais sejam visualizadas com fidelidade aos pontos subjacentes visualizados.

O algoritmo também preserva a forma geral do gráfico de dispersão.

> [!NOTE]
> Ao usar o algoritmo de **Amostragem de Alta Densidade** para gráficos de dispersão, a *distribuição precisa* dos dados é a meta e a densidade implícita do visual *não* é a meta. Por exemplo, talvez você veja um gráfico de dispersão com vários círculos que se sobrepõem (densidade) em determinada área e imagine que muitos pontos de dados devem estar clusterizados nele. Como o algoritmo de **Amostragem de Alta Densidade** pode usar um único círculo para representar muitos pontos de dados, uma densidade implícita do visual como essa (ou “clustering”) não será mostrada. Para obter mais detalhes de determinada área, use as segmentações para ampliar.
> 
> 

Além disso, os pontos de dados que não podem ser plotados (como valores nulos ou valores de texto) são ignorados, para que outro valor que pode ser plotado seja selecionado, garantindo ainda que a forma verdadeira do gráfico de dispersão seja mantida.

### <a name="when-the-standard-algorithm-for-scatter-charts-is-used"></a>Quando o algoritmo padrão para gráficos de dispersão é usado
Há circunstâncias em que a **Amostragem de Alta Densidade** não pode ser aplicada a um gráfico de dispersão e o algoritmo original é usado. Essas circunstâncias são as seguintes:

* Se você clicar com o botão direito do mouse em **Detalhes** e, em seguida, selecionar **Mostrar itens sem dados** no menu exibido, o gráfico de dispersão será revertido para o algoritmo original.
  
  ![](media/desktop-high-density-scatter-charts/high-density-scatter-charts_02.png)
* Os valores do eixo **Reproduzir** resultarão na reversão do gráfico de dispersão para o algoritmo original.
* Se os eixos X e Y estiverem ausentes em um gráfico de dispersão, o gráfico será revertido para o algoritmo original.
* O uso de uma **Linha de proporção** no painel **Análise** resulta na reversão do gráfico para o algoritmo original.
  
  ![](media/desktop-high-density-scatter-charts/high-density-scatter-charts_03.png)

## <a name="how-to-turn-on-high-density-sampling-for-a-scatter-chart"></a>Como ativar a amostragem de alta densidade em um gráfico de dispersão
Para ativar a **Amostragem de Alta Densidade**, selecione um gráfico de dispersão e, em seguida, acesse o painel **Formatação** e expanda o cartão **Geral**. Na parte inferior do cartão, um controle deslizante de alternância chamado **Amostragem de Alta Densidade** está disponível. Para ativá-lo, deslize-o para **Ativado**.

![](media/desktop-high-density-scatter-charts/high-density-scatter-charts_04.png)

> [!NOTE]
> Depois que o controle deslizante for ativado, o Power BI tentará usar o algoritmo de **Amostragem de Alta Densidade** sempre que possível. Quando o algoritmo não puder ser usado (por exemplo, você coloca um valor no eixo *Reproduzir*), o controle deslizante permanecerá na posição **Ativado** mesmo que o gráfico tenha sido revertido para o algoritmo padrão. Se, em seguida, você remover um valor do eixo *Reproduzir* (ou as condições forem mudadas para habilitar o uso do algoritmo de amostragem de alta densidade), como o controle deslizante está ativado, o gráfico usará a amostragem de alta densidade automaticamente neste gráfico.
> 
> [!NOTE]
> Os pontos de dados são agrupados e/ou selecionados pelo índice. Ter uma legenda não afeta a amostragem do algoritmo, somente a ordenação do visual.
> 
> 

## <a name="considerations-and-limitations"></a>Considerações e limitações
O algoritmo de amostragem de alta densidade é uma melhoria importante no Power BI, mas há algumas considerações que você precisa saber ao trabalhar com valores de alta densidade e gráficos de dispersão.

* O algoritmo de **Amostragem de Alta Densidade** funciona apenas com conexões dinâmicas em modelos baseados no serviço do Power BI, modelos importados ou o DirectQuery.

## <a name="next-steps"></a>Próximas etapas
Para obter mais informações sobre a amostragem de alta densidade em outros gráficos, consulte o artigo a seguir.

* [Amostragem de linha de alta densidade no Power BI](desktop-high-density-sampling.md)

