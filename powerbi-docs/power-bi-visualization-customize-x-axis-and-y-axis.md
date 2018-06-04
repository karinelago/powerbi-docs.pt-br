---
title: Personalizar as propriedades dos eixos x e y
description: Personalizar as propriedades dos eixos x e y
author: mihart
manager: kfile
ms.reviewer: ''
featuredvideoid: 9DeAKM4SNJM
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 01/20/2018
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: 372f00e7bd62068688bdcc22c1e983c3fe629f8a
ms.sourcegitcommit: 80d6b45eb84243e801b60b9038b9bff77c30d5c8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34295667"
---
# <a name="customize-x-axis-and-y-axis-properties"></a>Personalizar as propriedades dos eixos x e y
Neste tutorial, você aprenderá várias maneiras diferentes de personalizar os eixos X e Y das suas visualizações. Nem todas as visualizações têm eixos ou podem ser personalizadas; gráficos de pizza, por exemplo, não têm eixos. E opções de personalização variam de visualização para visualização, são muitas opções serem abordadas em um único artigo. Então vamos dar uma olhada em algumas das personalizações de eixos mais usadas e torná-lo familiarizado com a guia de formatação de visualização na tela de relatório do Power BI.  

> [!NOTE]
> Esta página aplica-se ao serviço do Power BI e ao Power BI Desktop. Essas personalizações, que ficam disponíveis quando o **Formato** (ícone de rolo de tinta ![](media/power-bi-visualization-customize-x-axis-and-y-axis/power-bi-paintroller.png)) é selecionado, também estão disponíveis no Power BI Desktop.  
>
>

Assista à Amanda personalizar seus eixos X e Y e demonstrar as várias maneiras de controlar a concatenação ao usar drill up e drill down. Em seguida, siga as instruções passo a passo abaixo do vídeo para experimentar sozinho usando o exemplo de Análise de Varejo.

<iframe width="560" height="315" src="https://www.youtube.com/embed/9DeAKM4SNJM" frameborder="0" allowfullscreen></iframe>


## <a name="customizing-visualization-x-axes-in-reports"></a>Personalizando a visualização dos eixos X em relatórios
## <a name="create-a-stacked-chart-visualization"></a>Criar uma visualização de gráfico empilhado
Entre no serviço do Power BI e abra o relatório **Exemplo de Análise de Varejo** no [Modo de Exibição de Edição](service-interact-with-a-report-in-editing-view.md). Para acompanhar, [conecte-se ao exemplo de Análise de Varejo](sample-datasets.md).

1. Crie um novo gráfico de coluna que mostra as vendas deste ano e o valor das vendas do ano passado por mês fiscal.
2. Converta-o em um gráfico de Colunas empilhadas.

    ![](media/power-bi-visualization-customize-x-axis-and-y-axis/power-bi-create-chart.png)

## <a name="customize-the-x-axis"></a>Personalizar o eixo X
1. No painel Visualizações e Filtros, selecione **Formato** (ícone de rolo de tinta ![](media/power-bi-visualization-customize-x-axis-and-y-axis/power-bi-paintroller.png)) para revelar as opções de personalização.
2. Expanda as opções de eixo X.

   ![](media/power-bi-visualization-customize-x-axis-and-y-axis/power-bi-x-axis.png)
3. Ative o eixo X e desative selecionando o controle deslizante Ativar (ou Desativar). Por enquanto, deixe em **Ativar**.  Um motivo pelo qual você talvez queira desligar o eixo x é para economizar espaço para mais dados.

    ![](media/power-bi-visualization-customize-x-axis-and-y-axis/onoffslider.png)
4. Formate a fonte, o tamanho e a cor do texto. Neste exemplo, definimos a **Cor** do texto para preto, o **Tamanho do Texto** para 14 e a **Fonte** para Arial Black.  
5. **Ative** o título do eixo X e exiba o nome desse eixo – nesse caso, **FiscalMonth**.  
6. Formate a fonte, o tamanho e a cor do texto do título.  Neste exemplo, definimos **Cor do título** para laranja, alteramos o **Título do eixo** para **Mês Fiscal**e definimos o **Tamanho do texto de título** para 21.
7. Para classificar por FiscalMonth, selecione as reticências (...) no canto superior direito do gráfico e selecione **Classificar por FiscalMonth**.

    Depois de todas essas personalizações, o gráfico de colunas deve ser parecido com isto:

     ![](media/power-bi-visualization-customize-x-axis-and-y-axis/power-bi-customize-axis.png)

Para reverter toda a personalização do eixo X feita até agora, selecione **Reverter ao Padrão** na parte inferior do painel de personalização do **eixo X**.

## <a name="customize-the-y-axis"></a>Personalizar o eixo Y
1. Expanda as opções de eixo Y.

   ![](media/power-bi-visualization-customize-x-axis-and-y-axis/power-bi-y-axis.png)

2. Ative e desative o eixo Y selecionando o controle deslizante Ativar (ou Desativar). Por enquanto, deixe em **Ativar**.  Um motivo pelo qual você talvez queira desligar o eixo y é para economizar espaço para mais dados.
   
    ![](media/power-bi-visualization-customize-x-axis-and-y-axis/onoffslider.png)
3. Mova a **Posição** do eixo Y para a direita.
4. Formate a fonte, o tamanho e a cor do texto. Neste exemplo, definimos a **Cor** do texto para preto, o **Tamanho do Texto** para 14 e a **Fonte** para Arial Black.  
5. Mantenha as **Unidades de exibição** definidas como milhões e as **Casas decimais do valor** definidas como zero.
6. Para esta visualização, ter um título de eixo Y não melhora o visual, portanto, deixe o **Título** desativado.  
7. Destacaremos as linhas de grade, alterando a **Cor** para um cinza escuro e aumentando o **Traço** para 2.

    Depois de todas essas personalizações, o gráfico de colunas deve ser parecido com isto:

     ![](media/power-bi-visualization-customize-x-axis-and-y-axis/power-bi-y-axis-complete.png)

## <a name="customizing-visualizations-with-dual-y-axes"></a>Personalizando visualizações de eixo Y duplo
Primeiro, você criará um gráfico de combinação que examina o impacto da contagem da loja nas vendas.  Este é o mesmo gráfico criado no [Tutorial do gráfico de combinação](power-bi-visualization-combo-chart.md). Em seguida, você formatará o eixo Y duplo.

### <a name="create-a-chart-with-two-y-axes"></a>Crie um gráfico com dois eixos Y
1. Crie um novo gráfico de linhas que acompanha a **% de Vendas > Margem Bruta do ano passado** por **Hora > FiscalMonth**.
2. Classificar o elemento visual por mês, selecionando as reticências (...) e escolhendo **Classificar por Mês**

    ![](media/power-bi-visualization-customize-x-axis-and-y-axis/power-bi-line-chart.png)

>[NOTE]: For help sorting by month, see [sorting by other criteria](power-bi-report-change-sort.md#other)
1. Em janeiro, a % de Margem Bruta foi de 35%, chegando ao seu máximo em 45% em abril, caindo em julho e chegando ao seu máximo novamente em agosto. Será que vamos ver um padrão semelhante nas vendas do ano passado e deste ano?
2. Adicione **Vendas deste ano > Valor** e **Vendas do último ano** no gráfico de linhas. A escala de **% de Margem Bruta do Ano Passado** (a linha azul acompanhando a linha de grade 0M%) é muito menor do que a escala de **Vendas**, o que dificulta a comparação. Além disso, os percentuais de rótulo do eixo Y são absurdas.      

   ![](media/power-bi-visualization-customize-x-axis-and-y-axis/flatline_new.png)
5. Para tornar o visual mais fácil de ler e interpretar, converta o gráfico de linhas em um gráfico de linha e coluna empilhada.

   ![](media/power-bi-visualization-customize-x-axis-and-y-axis/converttocombo_new.png)

6. Arraste **% de Margem Bruta no Ano Passado** de **Valores de Coluna** para **Valores de Linha**. O que temos agora é o gráfico de colunas empilhadas que criamos acima ***mais*** um gráfico de linhas.  (Opcionalmente, use o que você aprendeu acima para formatar a cor e o tamanho da fonte dos eixos.)
   

   O Power BI cria dois eixos, permitindo que os conjuntos de dados sejam escalonados de modo diferente: o eixo à esquerda calcula dólares e o eixo à direita calcula o percentual.

   ![](media/power-bi-visualization-customize-x-axis-and-y-axis/power-bi-dual-axes-new.png)

### <a name="format-the-secondary-y-axis"></a>Formate o eixo Y secundário
1. No painel **Visualizações**, selecione o ícone de rolo de tinta para exibir as opções de formatação.
2. Expanda as opções de eixo Y selecionando a seta para baixo.
3. Percorra a lista até encontrar as opções para **Mostrar Secundário**. Alterne **Mostrar Secundário** de **Desativado** para **Ativado**.

   ![](media/power-bi-visualization-customize-x-axis-and-y-axis/combo3.png)

   ![](media/power-bi-visualization-customize-x-axis-and-y-axis/power-bi-dual-axes.png)
4. (Opcional) Personalize os dois eixos. Se você mudar a **Posição** para o eixo da coluna ou o eixo de linha, os dois eixos trocarão de lado.

   ![](media/power-bi-visualization-customize-x-axis-and-y-axis/power-bi-y-axes-options.png)

### <a name="add-titles-to-both-axes"></a>Adicionar títulos a ambos os eixos
Com uma visualização complicada, convém adicionar títulos de eixos.  Os títulos ajudam seus colegas a compreender a história que a sua visualização está mostrando.

1. Alterne **Título** para **Ativado** para o **Eixo Y (Coluna)** e o **Eixo Y (Linha)**.
2. Defina o **Estilo** para **Mostrar somente o título**.

   ![](media/power-bi-visualization-customize-x-axis-and-y-axis/yaxissettings.png)
3. Seu gráfico de combinação agora exibe eixos duplos, ambos com títulos.

   ![](media/power-bi-visualization-customize-x-axis-and-y-axis/power-bi-combo-chart.png)

Para obter mais informações, veja [Dicas e truques para formatação com cores, rotulamento e propriedades de eixo](service-tips-and-tricks-for-color-formatting.md).

## <a name="considerations-and-troubleshooting"></a>Considerações e solução de problemas
Se o eixo X for categorizado pelo proprietário do relatório como um tipo de data, a opção **Tipo** será exibida e você poderá selecionar entre contínua ou categórica.

## <a name="next-steps"></a>Próximas etapas
Mais sobre [Visualizações nos relatórios do Power BI](power-bi-report-visualizations.md)

[Personalizar t](power-bi-visualization-customize-title-background-and-legend.md)[ítulos, telas de fundo e legendas](power-bi-visualization-customize-title-background-and-legend.md)

[Personalizar cores e propriedades de eixo](service-getting-started-with-color-formatting-and-axis-properties.md)

[Power BI – conceitos básicos](service-basic-concepts.md)

Mais perguntas? [Experimente a Comunidade do Power BI](http://community.powerbi.com/)
