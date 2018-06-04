---
title: 'Tutorial: criar suas próprias medidas no Power BI Desktop'
description: 'Tutorial: criar suas próprias medidas no Power BI Desktop'
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: tutorial
ms.date: 05/21/2018
ms.author: davidi
LocalizationGroup: Learn more
ms.openlocfilehash: 8cfa3190acd4ef2ae2e1123f22d8f6221147afb1
ms.sourcegitcommit: 80d6b45eb84243e801b60b9038b9bff77c30d5c8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34456078"
---
# <a name="tutorial-create-your-own-measures-in-power-bi-desktop"></a>Tutorial: criar suas próprias medidas no Power BI Desktop
Você pode criar algumas das soluções de análise de dados mais poderosas no Power BI Desktop usando medidas. As medidas ajudam você a executar cálculos em seus dados conforme você interage com os relatórios. Este tutorial serve como guia para que você compreenda as medidas e crie suas próprias medidas básicas no Power BI Desktop.

### <a name="prerequisites"></a>Pré-requisitos
- Este tutorial destina-se aos usuários do Power BI já familiarizados com o uso do Power BI Desktop para criar modelos mais avançados. Você já deve estar familiarizado com o uso dos recursos Obter Dados e Editor de Consultas para importar dados, trabalho com várias tabelas relacionadas e adição de campos à Tela Relatório. Se ainda não estiver familiarizado com o Power BI Desktop, não deixe de conferir a [Introdução ao Power BI Desktop](desktop-getting-started.md).
  
- Baixe o arquivo [Exemplo de vendas da Contoso para o Power BI Desktop](http://download.microsoft.com/download/4/6/A/46AB5E74-50F6-4761-8EDB-5AE077FD603C/Contoso%20Sales%20Sample%20for%20Power%20BI%20Desktop.zip), que já inclui dados de vendas online da empresa fictícia Contoso, Inc. Esses dados foram importados de um banco de dados, portanto você não conseguirá se conectar à fonte de dados ou exibi-los no Editor de Consultas. Extraia o arquivo em seu próprio computador, e abra-o no Power BI Desktop.

## <a name="understand-measures"></a>Compreender medidas

Normalmente, as medidas são criadas automaticamente para você. No arquivo de Exemplo de Vendas da Contoso, marque a caixa de seleção ao lado do campo **SalesAmount**, na tabela **Sales** na lista Fields, ou arraste **SalesAmount** para a tela do relatório. Uma nova visualização de gráfico de coluna é exibida, mostrando a soma total de todos os valores na coluna SalesAmount da tabela Sales.

![Gráfico SalesAmount](media/desktop-tutorial-create-measures/meastut_salesamountchart.png)

Qualquer campo que apareça na lista Fields com um ícone sigma ![O ícone sigma](media/desktop-tutorial-create-measures/meastut_sigma.png) é numérico, e seus valores podem ser agregados. Em vez de mostrar uma tabela com todas as duas milhões de linhas de valores SalesAmount, o Power BI Desktop detectou um tipo de dados numérico, criou e calculou automaticamente uma medida para agregar os dados. Soma é a agregação padrão de um tipo de dados numérico, mas você pode aplicar facilmente agregações diferentes, como média ou contagem. Entender o funcionamento das agregações é fundamental para compreender as medidas, pois cada medida executa algum tipo de agregação. 

Para alterar a agregação de gráfico para média, na área **Valor** do painel Visualizações, clique na seta para baixo ao lado de **SalesAmount** e selecione **Média**. A visualização muda para uma média de todos os valores de vendas no campo SalesAmount.

![Gráfico de média de SalesAmount](media/desktop-tutorial-create-measures/meastut_salesamountaveragechart.png)

É possível alterar o tipo de agregação dependendo do resultado desejado, mas nem todos os tipos de agregação se aplicam a todo tipo de dados numérico. Por exemplo, para o campo SalesAmount, Sum e Average fazem sentido. Minimum e Maximum também são importantes. No entanto, Contagem não faz muito sentido para o campo SalesAmount, porque embora seus valores sejam numéricos, eles são na verdade monetários.

Os valores calculados por meio de medidas mudam de acordo com as interações em seu relatório. Por exemplo, arrastar o campo **RegionCountryName** da tabela **Geography** para o seu gráfico mostra as quantias médias de vendas para cada país.

![SaleAmount por País](media/desktop-tutorial-create-measures/meastut_salesamountavchartbyrcn.png)

Quando o resultado de uma medida é alterado devido a uma interação com seu relatório, você afetou o *contexto* da sua medida. Sempre que interage com as visualizações de seu relatório, você altera o contexto no qual uma medida calcula e exibe seus resultados.

## <a name="create-and-use-your-own-measures"></a>Criar e usar suas próprias medidas

Na maioria dos casos, o Power BI calcula automaticamente e retorna valores de acordo com os tipos de campos e agregações que você escolher, mas em alguns casos, convém criar suas próprias medidas para executar cálculos mais complexos e exclusivos. Com o Power BI Desktop, você pode criar suas próprias medidas com a linguagem de fórmula DAX (Data Analysis Expressions). 

Fórmulas DAX usam muitos operadores, funções e sintaxe também utilizados pelas fórmulas do Excel. No entanto, as funções DAX foram projetadas para trabalhar com dados relacionais e realizar cálculos mais dinâmicos durante sua interação com os relatórios. Há mais de 200 funções DAX que fazem tudo, desde agregações simples, como Soma e Média, até funções de estatística e de filtragem mais complexas. Há muitos recursos para ajudar você a saber mais sobre o DAX. Depois de concluir este tutorial, não deixe de conferir [Noções básicas do DAX no Power BI Desktop](desktop-quickstart-learn-dax-basics.md).

Quando você cria suas próprias medidas, elas são adicionadas à lista Campos da tabela selecionada, e é chamada de medida *modelo*. Entre as vantagens das medidas de modelo estão a possibilidade de nomeá-las como você quiser, tornando-as mais identificáveis; você pode usá-las como argumentos em outras expressões DAX; e pode fazer com que executem rapidamente cálculos complexos.

>[!TIP]
>A partir da versão de fevereiro de 2018 do Power BI Desktop, muitos cálculos comuns foram disponibilizados como **medidas rápidas**, que escrevem as fórmulas DAX para você com base em suas entradas em uma caixa de diálogo. Esses cálculos rápidos e eficientes também são ótimos para aprender DAX ou propagar suas próprias medidas personalizadas. Para criar ou explorar medidas rápidas, selecione **Nova medida rápida** na lista **Mais opções** de uma tabela ou em **Cálculos** na guia Início da faixa de opções. Veja [Usar medidas rápidas](desktop-quick-measures.md) para saber mais sobre como criar e usar medidas rápidas.

### <a name="create-a-measure"></a>Criar uma medida

Você deseja analisar as vendas líquidas subtraindo descontos e devoluções dos valores de vendas totais. Para qualquer contexto que exista em sua visualização, você precisa de uma medida que subtraia a soma de DiscountAmount e ReturnAmount da soma de SalesAmount. Não há um campo para Net Sales na lista Fields, mas você tem os blocos de construção para criar sua própria medida para calcular as vendas líquidas. 

1.  Clique com o botão direito do mouse na tabela **Sales** na lista Fields, ou passe o mouse sobre a tabela e selecione as reticências de **Mais opções** (...), depois selecione **Nova Medida**. Isso salvará sua nova medida na tabela Sales, onde será mais fácil de ser encontrada.
    
    ![Nova medida](media/desktop-tutorial-create-measures/meastut_netsales_newmeasure.png)
    
    Você também pode criar uma nova medida selecionando **Nova medida** no grupo Cálculos da guia Página Inicial da faixa de opções do Power BI Desktop.
    
    ![Nova medida na faixa de opções](media/desktop-tutorial-create-measures/meastut_netsales_newmeasureribbon.png)
    
    >[!TIP]
    >Ao criar uma medida na faixa de opções, você pode criá-la em qualquer uma das tabelas, no entanto, será mais fácil localizá-la se você criá-la onde pretende usá-la. Nesse caso, selecione a tabela Sales primeiro para torná-la ativa e depois selecione **Nova Medida**. 
    
    A barra de fórmulas aparece na parte superior da tela do Relatório, onde você pode renomear a medida e inserir uma fórmula DAX.
    
    ![Barra de fórmulas](media/desktop-tutorial-create-measures/meastut_netsales_newmeasure_formulabar.png)
    
2.  Por padrão, uma nova medida é simplesmente chamada de Medida. Se você não renomeá-la, outras medidas novas receberão o nome de Measure 2, Measure 3 e assim por diante. Convém tornar suas medidas mais identificáveis, então realce **Medida** na barra de fórmulas e digite **Net Sales**.
    
3.  Agora, você pode começar a inserir sua fórmula. Após o sinal de igual, comece a digitar **Sum**. Conforme você digita, surge uma lista suspensa com sugestões, mostrando todas as funções DAX que começam com as letras que você digitou. Role a tela para baixo se for necessário para selecionar **SUM** na lista, e pressione Enter.
    
    ![Escolher SUM](media/desktop-tutorial-create-measures/meastut_netsales_newmeasure_formula_s.png)
    
    Um parêntese de abertura é exibido junto com outra lista suspensa de sugestões de todas as colunas disponíveis que você pode passar para a função SUM.
    
    ![Escolher a coluna](media/desktop-tutorial-create-measures/meastut_netsales_newmeasure_formula_sum.png)
    
    As expressões sempre aparecem entre parênteses de abertura e de fechamento. Sua expressão conterá um único argumento para passar para a função SUM: a coluna SalesAmount. Comece a digitar "SalesAmount" até que reste apenas um valor na lista: Sales(SalesAmount). O nome da coluna precedido pelo nome da tabela é chamado de *nome totalmente qualificado* da coluna. Nomes de coluna totalmente qualificados facilitam a leitura de suas fórmulas. 
    
    ![Selecione SalesAmount](media/desktop-tutorial-create-measures/meastut_netsales_newmeasure_formula_salesam.png)
    
4. Selecione **Sales[SalesAmount]** e digite um parêntese de fechamento.
    
    > [!TIP]
    > Erros de sintaxe são causados frequentemente por um parêntese de fechamento ausente ou mal posicionado.
    
    
    
5.  Para subtrair as outras duas colunas:
    1. Após o parêntese de fechamento para a primeira expressão, digite um espaço, um operador de subtração (**-**) e outro espaço. 
    2. Insira outra função SUM e comece a digitar "DiscountAmount" até que você possa escolher a coluna **Sales[DiscountAmount]** como argumento. Adicione um parêntese de fechamento. 
    3. Digite um espaço, outro operador de subtração, espaço, outra função SUM com **Sales[ReturnAmount]** como o argumento e um parêntese de fechamento.
    
    ![Fórmula completa](media/desktop-tutorial-create-measures/meastut_netsales_newmeasure_formula_discamount.png)
    
6.  Pressione Enter ou clique na marca de confirmação na barra de fórmulas para concluir e validar a fórmula. Agora, a medida validada está pronta para uso na lista Fields da tabela Sales. 
    
    ![Medida na lista de campos](media/desktop-tutorial-create-measures/meastut_netsales_newmeasure_complete.png)
    
Se você ficar sem espaço para inserir uma fórmula, ou se quiser colocá-la em linhas separadas, selecione a divisa para baixo no lado direito da barra de fórmulas para abrir mais espaço.

![Divisa de fórmula](media/desktop-tutorial-create-measures/meastut_netsales_newmeasure_formula_chevron.png)

Você pode separar partes de sua fórmula em linhas diferentes pressionando **Alt-Enter**, ou mover itens usando a tecla **Tab**.

![Fórmula expandida](media/desktop-tutorial-create-measures/meastut_netsales_newmeasure_formula_expanded.png)

### <a name="use-your-measure-in-the-report"></a>Usar sua medida no relatório
Agora, você pode adicionar sua medida Net Sales à tela do relatório e calcular as vendas líquidas de quaisquer outros campos que você adicionar ao relatório. Para examinar as vendas líquidas por país:

1. Selecione a medida **Net Sales** na tabela **Sales**, ou arraste-a até a tela do relatório.
    
2. Selecione o campo **RegionCountryName** da tabela **Geography**, ou arraste-o até o gráfico.
    
    ![Vendas líquidas por país](media/desktop-tutorial-create-measures/meastut_netsales_byrcn.png)
    
Para ver a diferença entre o valor total de vendas e o de vendas líquidas, selecione o campo **SalesAmount**, ou arraste-o até o gráfico. 

![Valor de vendas e Vendas líquidas por país](media/desktop-tutorial-create-measures/meastut_netsales_byrcnandsalesamount.png)

Agora, o gráfico usa duas medidas: SalesAmount, que foi somada automaticamente, e medida Net Sales que você criou. Cada medida foi calculada no contexto de outro campo, RegionCountryName.
    
### <a name="use-your-measure-with-a-slicer"></a>Usar sua medida com uma segmentação de dados

É possível adicionar uma segmentação de dados para filtrar ainda mais as vendas líquidas e valores de vendas por ano civil.
    
1.  Clique em uma área em branco ao lado do gráfico e, em **Visualizações**, selecione a visualização **Tabela**. Isso cria uma nova visualização de tabela em branco na tela do relatório.
    
    ![](media/desktop-tutorial-create-measures/meastut_netsales_blanktable.png)
    
2.  Arraste o campo **Year** da tabela **Calendar** até a nova visualização de tabela em branco. Como Year é um campo numérico, o Power BI Desktop soma seus valores, mas isso não faz muito sentido como uma agregação. 
    
    ![Agregação de anos](media/desktop-tutorial-create-measures/meastut_netsales_yearaggtable.png)
    
3.  Em **Valores** no painel de visualizações, selecione a seta para baixo ao lado de **Year** e, em seguida, selecione **Não resumir**. Agora, a tabela lista os anos individuais.
    
    ![Não resumir](media/desktop-tutorial-create-measures/meastut_netsales_year_donotsummarize.png)
    
4.  Selecione o ícone **Segmentação de Dados** no painel Visualizações para converter a nova visualização em uma segmentação de dados.

    ![Alterar para segmentação de dados](media/desktop-tutorial-create-measures/meastut_netsales_year_changetoslicer.png)
    
5.  Selecione qualquer valor na segmentação **Year** para filtrar o gráfico **Vendas líquidas e Valor das vendas por país** adequadamente. As medidas Net Sales e SalesAmount são recalculadas e exibem os resultados no contexto do campo Year selecionado. 
    
    ![Gráfico segmentado por ano](media/desktop-tutorial-create-measures/meastut_netsales_chartslicedbyyear.png)

### <a name="use-your-measure-in-another-measure"></a>Usar sua medida em outra medida

Você quer descobrir quais produtos têm o maior valor de vendas líquidas por unidade vendida. Portanto, você precisa de uma medida que divida as vendas líquidas pela quantidade de unidades vendidas. Você pode criar uma nova medida que divide o resultado de sua medida Net Sales pela soma de Sales[SalesQuantity].

1.  Crie uma nova medida chamada **Net Sales per Unit** na tabela Sales.
    
2.  Na barra de fórmulas, comece digitando **Net Sales**. A lista de sugestões mostrará o que você pode adicionar. Selecione **[Net Sales]**.
    
    ![Fórmula usando Net Sales](media/desktop-tutorial-create-measures/meastut_nspu_formulastep2a.png)
    
    Você também pode fazer referência a medidas digitando apenas um colchete de abertura (**[**). A lista de sugestões mostrará apenas as medidas para adicionar à sua fórmula.
    
    ![Colchete mostra apenas as medidas](media/desktop-tutorial-create-measures/meastut_nspu_formulastep2b.png)
    
3.  Insira um espaço, um operador de divisão (**/**), outro espaço, uma função SUM e, em seguida, digite **Quantity**. A lista de sugestões mostra todas as colunas com "Quantity" no nome. Selecione **Sales[SalesQuantity]**, digite o parêntese de fechamento e pressione ENTER, ou selecione a marca de seleção para validar a fórmula. A fórmula deve ter essa aparência:
    
    `Net Sales per Unit = [Net Sales] / SUM(Sales[SalesQuantity])`
    
4. Selecione a medida **Net Sales per Unit** na tabela Sales, ou arraste-a até uma área em branco na tela do relatório. O gráfico mostra a quantidade de vendas líquida por unidade de todos os produtos vendidos, o que não é muito informativo. 
    
    ![Vendas líquidas gerais por unidade](media/desktop-tutorial-create-measures/meastut_nspu_chart.png)
    
5. Para ver de outro jeito, altere o tipo de visualização de gráfico para **Mapa de árvore**.
    
    ![Alterar para mapa de árvore](media/desktop-tutorial-create-measures/meastut_nspu_changetotreemap.png)
    
6. Selecione o campo **Product Category** ou arraste-o para o mapa de árvore ou para o campo Grupo do painel Visualizações. Agora você tem informações úteis!
    
    ![Mapa de árvore por categoria de produto](media/desktop-tutorial-create-measures/meastut_nspu_byproductcat.png)
    
7. Tente remover o campo **ProductCategory** e arrastar o campo **ProductName** campo para o gráfico em vez disso. 
    
    ![Treemap por nome de produto](media/desktop-tutorial-create-measures/meastut_nspu_byproductname.png)
    
OK, agora estamos apenas experimentando, mas você tem que admitir, isso é muito legal! Experimente outras maneiras de filtrar e formatar a visualização.

## <a name="what-youve-learned"></a>O que você aprendeu
As medidas proporcionam muitas possibilidades para obter as informações que você quer de seus dados. Você aprendeu a criar medidas usando a barra de fórmulas, a nomeá-las de um jeito que faça mais sentido e a localizar e selecionar os elementos certos para as fórmulas usando as listas de sugestão de DAX. Você também foi apresentado ao contexto, no qual o resultado dos cálculos em medidas muda de acordo com outros campos ou outras expressões em sua fórmula.

## <a name="next-steps"></a>Próximas etapas
- Para saber mais sobre medidas rápidas do Power BI Desktop, que fornecem muitos cálculos de medida comum para você, consulte [Usar medidas rápidas para realizar facilmente cálculos avançados e comuns](desktop-quick-measures.md).
  
- Se desejar se aprofundar nas fórmulas DAX e criar algumas medidas mais avançadas, veja [Noções básicas do DAX no Power BI Desktop](desktop-quickstart-learn-dax-basics.md). Este artigo enfoca os conceitos fundamentais no DAX, como sintaxe, funções e uma compreensão mais abrangente sobre o contexto.
  
- Certifique-se de adicionar a [Referência ao DAX (Expressões de Análise de Dados)](https://msdn.microsoft.com/library/gg413422.aspx) aos favoritos. É nela que você encontrará informações detalhadas sobre a sintaxe do DAX, operadores, além de mais de 200 funções DAX.

