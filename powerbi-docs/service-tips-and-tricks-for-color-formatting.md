---
title: Dicas e truques para formatação com cores no Power BI
description: Dicas e truques para formatação com cores no Power BI
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 05/02/2018
ms.author: davidi
LocalizationGroup: Visualizations
ms.openlocfilehash: 3c91a6a70899a4a59c3d98cd9ab948284df5b662
ms.sourcegitcommit: 80d6b45eb84243e801b60b9038b9bff77c30d5c8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34298379"
---
# <a name="tips-and-tricks-for-color-formatting-in-power-bi"></a>Dicas e truques para formatação com cores no Power BI
O Power BI fornece diversas maneiras de personalizar os painéis e relatórios. Este artigo detalha uma coleção de dicas que podem tornar suas visualizações do Power BI mais convincentes, interessantes e personalizadas para suas necessidades.

As dicas a seguir são fornecidas. Há outra dica excelente? Ótimo! Envie para nós e vermos sobre adicioná-la à lista.

* Alterar a cor de um único ponto de dados
* Basear as cores de um gráfico em um valor numérico
* Base da cor de pontos de dados no valor de campo
* Personalizar as cores usadas na escala de cores
* Usar escalas de cores divergentes
* Como desfazer no Power BI

Para fazer alterações, você deve editar um relatório: selecione o **Relatório** no painel **Meu espaço de trabalho** , selecione **Editar relatório** na área do menu superior, conforme mostrado na imagem a seguir.

![](media/service-tips-and-tricks-for-color-formatting/tipstrickscolor_1.png)

Quando o painel **Visualizações** é exibido no lado direito da tela **Relatório** , você estará pronto para começar a personalizar.

![](media/service-tips-and-tricks-for-color-formatting/tipstrickscolor_2.png)

## <a name="change-the-color-of-a-single-data-point"></a>Alterar a cor de um único ponto de dados
Às vezes você deseja realçar um determinado ponto de dados. Talvez seja os números de vendas para o lançamento de um novo produto, ou pontuações de qualidade aumentadas depois de lançar um novo programa. Com o Power BI, você pode realçar um determinado ponto de dados alterando sua cor.

A seguinte visualização classifica estados em termos de custo de vida. 

![](media/service-tips-and-tricks-for-color-formatting/tipstrickscolor_3.png)

Agora imagine que você deseja mostrar rapidamente onde Washington está nessa lista classificada, usando cores. Aqui estão as etapas para fazer isso:

Aumenta a seção **Cores de Dados** . ApareceA seguir é exibido.

![](media/service-tips-and-tricks-for-color-formatting/tipstrickscolor_4.png)

Definir **Mostrar tudo** para **Ativado**. Isso exibe as cores para cada elemento de dados na visualização. Ao focalizar os pontos de dados, a rolagem é habilidade para que você possa modificar qualquer ponto de dados.

![](media/service-tips-and-tricks-for-color-formatting/tipstrickscolor_5.png)

Nesse caso, vamos alterar **Washington** para verde. Podemos rolar para baixo até **Washington** e selecionar a seta para baixo dentro de sua caixa de cor e a janela de seleção de cor é exibida.

![](media/service-tips-and-tricks-for-color-formatting/tipstrickscolor_6.png)

Uma vez selecionada, o ponto de dados **Washington** estará com uma boa tonalidade de verde e certamente se destaca.

![](media/service-tips-and-tricks-for-color-formatting/tipstrickscolor_7.png)

Mesmo se você alterar os tipos de visualização, e, em seguida, retornar, o Power BI lembra sua seleção e mantém **Washington** verde.

Você também pode alterar a cor de um ponto de dados para mais de um elemento de dados. A imagem a seguir, **Arizona** está vermelha, e **Washington** ainda verde.

![](media/service-tips-and-tricks-for-color-formatting/tipstrickscolor_8.png)

Há inúmeras coisas que você pode fazer com o Power BI Desktop. Na próxima seção, vamos dar uma olhada em gradientes.

## <a name="base-the-colors-of-a-chart-on-a-numeric-value"></a>Basear as cores de um gráfico em um valor numérico
Os gráficos muitas vezes se beneficiam de configurar a cor com base no valor numérico de um campo. Ao fazer isso, você pode mostrar um valor diferente para que é usado o tamanho de uma barra e mostrar dois valores em um único gráfico. Ou você pode usar isso para realçar pontos de dados acima (ou abaixo) de um determinado valor – talvez destacando lucratividade baixa.

As seções a seguir demonstram maneiras diferentes de cor de base em um valor numérico.

## <a name="base-the-color-of-data-points-on-a-value"></a>Base da cor de pontos de dados em um valor
Para alterar a cor com base em um valor, arraste o campo que você deseja basear a cor para a área **Saturação de Cor** no painel **Campo** . A imagem a seguir, **Lucro antes do imposto** foi arrastada para **Saturação de Cor**. Como podemos ver que, embora **Velo** tenha mais **Vendas Brutas** (uma coluna for maior), **Amarilla** tem uma maior **Lucro antes do imposto** (sua coluna tem mais de saturação de cor).

![](media/service-tips-and-tricks-for-color-formatting/tipstrickscolor_9.png)

## <a name="customize-the-colors-used-in-the-color-scale"></a>Personalizar as cores usadas na escala de cores
Você pode personalizar as cores usadas na escala de cores. Expanda as **Cores de dados** e verá um gradiente de cores usado para visualizar seus dados. Por padrão, o valor mais baixo em seus dados é mapeado para a cor menos saturada e o valor mais alto para a cor mais saturada.

O intervalo de cores é mostrado na barra de gradiente que exibe o espectro entre os valores de cor **mínimo** e **máximo** , com a cor de valoro **mínimo** à esquerda, e **máximo** valor de cor para a direita.

![](media/service-tips-and-tricks-for-color-formatting/tipstrickscolor_10.png)

Para alterar a escala para usar um intervalo diferente de cores, selecione a lista suspensa ao lado da cor **mínimo** ou **máximo**, e selecione uma cor. A imagem a seguir mostra a cor **máximo** alterada para preto e a barra de gradiente mostra o novo espectro de cores entre **mínimo** e **máximo**.

![](media/service-tips-and-tricks-for-color-formatting/tipstrickscolor_11.png)

Você também pode alterar a maneira como os valores mapeiam essas cores. Na imagem a seguir, as cores **mínimo** e **máximo** são definidas como laranja e verde, respectivamente.

Nesta primeira imagem, observe como as barras no gráfico refletem o gradiente mostrado na barra; o valor mais alto é verde, o mais baixo é laranja e cada barra é colorida com um tom do espectro entre verde e laranja.

![](media/service-tips-and-tricks-for-color-formatting/tipstrickscolor_12.png)

Agora, vejamos o que acontece se podemos fornecer valores numéricos nas caixas **mínimo** e **máximo** , que estão abaixo do valor dos seletores de cor **mínimo** e **máximo** (mostrados na imagem a seguir). Vamos definir **mínimo** para 20.000.000 e **máximo** para 20.000.000.

Ao definir esses valores, gradiente não é mais aplicado a valores no gráfico que estão abaixo do **mínimo** ou acima do **máximo**; qualquer barra com um valor acima do valor **máximo** é verde e qualquer barra com um valor baixo do **mínimo** fica em vermelho.

![](media/service-tips-and-tricks-for-color-formatting/tipstrickscolor_13.png)

## <a name="use-diverging-color-scales"></a>Usar escalas de cores divergentes
Às vezes, seus dados podem ter uma escala divergente naturalmente. Por exemplo, um intervalo de temperatura tem um centro natural em congelamento de ponto e uma pontuação de lucratividade tem um ponto intermediário natural (zero).

Para usar escalas de cores divergentes, deslize o controle deslizante **Divergente** para **Ativado**. Quando **Divergente** estiver ativado, um seletor de cores adicionais e caixa de valor, ambos com o nome **Centro**, exibido, conforme mostrado na imagem a seguir.

![](media/service-tips-and-tricks-for-color-formatting/tipstrickscolor_14.png)

Quando o controle deslizante **Divergente** estiver ativo, você pode definir as cores **mínimo**, **máximo** e **centro** separadamente. Na imagem a seguir, **Centro** está definido como um, então barras com valores acima de uma são uma gradiente tonalidade de verde e barras abaixo são tons de vermelho.

## <a name="how-to-undo-in-power-bi"></a>Como desfazer no Power BI
Como muitos outros serviços da Microsoft e o software, o Power BI fornece uma maneira fácil para desfazer o último comando. Por exemplo, vamos dizer que você altera a cor de um ponto de dados ou uma série de pontos de dados, e você não gosta de cor quando ele for exibido na visualização. Você não lembra exatamente qual cor era antes, mas você sabe que deseja voltar àquela cor!

Para **Desfazer** a última ação ou as últimas ações, o que você precisa fazer é:

- Digitar CTRL + Z

## <a name="feedback"></a>Comentários
Você tem uma dica que gostaria de compartilhar? Envie para nós e veremos sobre adicioná-la à lista.

>[!NOTE]
>Essas personalizações de cor, eixo e outras relacionadas, disponíveis quando o ícone **Formatar** é selecionado, também estão disponíveis no Power BI Desktop.

## <a name="next-steps"></a>Próximas etapas
[Introdução com propriedades de eixo e formatação de cor](service-getting-started-with-color-formatting-and-axis-properties.md)

