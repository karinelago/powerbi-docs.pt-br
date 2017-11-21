---
title: "Tutorial: criar suas próprias medidas no Power BI Desktop"
description: "Tutorial: criar suas próprias medidas no Power BI Desktop"
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
ms.date: 09/06/2017
ms.author: davidi
ms.openlocfilehash: a50264ac4b200a58ac1ffd126084a3ca6bb5b03d
ms.sourcegitcommit: 284b09d579d601e754a05fba2a4025723724f8eb
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/15/2017
---
# <a name="tutorial-create-your-own-measures-in-power-bi-desktop"></a>Tutorial: criar suas próprias medidas no Power BI Desktop
Algumas das mais poderosas soluções de análise de dados no Power BI Desktop podem ser criadas com o uso de medidas. Medidas nos ajudam a executar cálculos sobre nossos dados conforme interagimos com nossos relatórios. Este tutorial serve como guia para que você compreenda as medidas básicas e crie algumas delas no Power BI Desktop.

Este artigo destina-se aos usuários do Power BI já familiarizados com o uso do Power BI Desktop para criar modelos mais avançados. Você já deve estar familiarizado com o uso dos recursos Obter Dados e Editor de Consultas para importar dados, trabalho com várias tabelas relacionadas e adição de campos à Tela Relatório. Se ainda não estiver familiarizado com o Power BI Desktop, não deixe de conferir a [Introdução ao Power BI Desktop](desktop-getting-started.md).

Para concluir as etapas neste tutorial, você precisará baixar o arquivo [Exemplo de Vendas da Contoso para o Power BI Desktop](http://download.microsoft.com/download/4/6/A/46AB5E74-50F6-4761-8EDB-5AE077FD603C/Contoso%20Sales%20Sample%20for%20Power%20BI%20Desktop.zip). Ele já inclui dados de vendas online da empresa fictícia, Contoso, Inc. Como os dados no arquivo foram importados de um banco de dados, você não conseguirá se conectar à fonte de dados nem exibi-los no Editor de Consultas. Quando você tiver o arquivo em seu próprio computador, vá em frente e abra-o no Power BI Desktop.

## <a name="what-are-these-measures-all-about"></a>De que tratam essas medidas?
Na maioria das vezes, as medidas são criadas automaticamente, como quando selecionamos a caixa de seleção ao lado do campo **SalesAmount** da tabela **Sales** na lista de campos, ou arrastamos **SalesAmount** para a tela Relatório.

![](media/desktop-tutorial-create-measures/measurestut_salesamountinfieldlist.png)

Uma nova visualização do gráfico é exibida, como essa:

![](media/desktop-tutorial-create-measures/meastut_salesamountchart.png)

O que obtemos é um Gráfico de colunas mostrando uma soma total dos valores de vendas obtidos do campo SalesAmount.  Nosso campo SalesAmount na verdade é apenas uma coluna chamada SalesAmount na tabela Sales, que já importamos.

A coluna SalesAmount contém mais de dois milhões de linhas de valores de vendas. Você deve estar se perguntando por que você não vê uma tabela com linhas contendo todos esses valores. Bem, o Power BI Desktop sabe que todos os valores em SalesAmount são de um tipo de dados numérico, e você provavelmente desejará agregá-los de algum modo - seja somando-os, obtendo sua média, realizando sua contagem, etc.

Sempre que você vir um campo na lista Campos com um ícone de sigma ![](media/desktop-tutorial-create-measures/meastut_sigma.png), isso significa que esse campo é numérico e que seus valores podem ser agregados. Nesse caso, quando selecionamos SalesAmount, o Power BI Desktop cria suas próprias medidas e a soma de todos os valores de vendas é calculada e exibida em nosso gráfico.

Sum (soma) é a agregação padrão quando selecionamos um campo com um tipo de dados numérico, mas podemos mudar facilmente para outro tipo de agregação.

Na área **Value** , se clicarmos na seta para baixo ao lado de **SalesAmount**, poderemos selecionar **Average**.

![](media/desktop-tutorial-create-measures/meastut_salesamountaverage.png)

Nossa visualização muda para uma média de todos os valores de vendas no campo SalesAmount.

![](media/desktop-tutorial-create-measures/meastut_salesamountaveragechart.png)

É possível alterar o tipo de agregação dependendo do resultado desejado, mas nem todos os tipos de agregação se aplicam a qualquer tipo de dados numérico. Por exemplo, para nosso campo SalesAmount, Sum e Average fazem sentido. Minimum e Maximum também são importantes. No entanto, Count não faz muito sentido para nosso campo SalesAmount, porque embora seus valores sejam numéricos, eles são na verdade referentes à moeda.

Entender o funcionamento das agregações é fundamental para compreender as medidas, pois cada medida executará algum tipo de agregação. Veremos mais exemplos de como usar uma agregação de Soma um pouco mais tarde, quando você criará algumas de suas próprias medidas.

Os valores calculados por meio de medidas estão sempre mudando de acordo com as interações que temos com nosso relatório. Por exemplo, se arrastarmos o campo **RegionCountryName** da tabela **Geography** para nosso gráfico, as médias dos valores de vendas para cada país serão calculadas e exibidas.

![](media/desktop-tutorial-create-measures/meastut_salesamountavchartbyrcn.png)

Quando o resultado de uma medida é alterado devido a uma interação com nosso relatório, estamos afetando o *contexto* de nossa medida. Na verdade, sempre que interage com seu relatório, você altera o contexto no qual uma medida calcula e exibe seus resultados.

Na maioria dos casos, o Power BI faz seu trabalho e calcula e retorna valores de acordo com os campos que adicionamos e os tipos de agregação que escolhemos. Mas em outros casos, talvez você precise criar suas próprias medidas para executar cálculos mais complexos e exclusivos.

Com o Power BI Desktop, você cria suas próprias medidas com a linguagem de fórmula DAX (Data Analysis Expressions). As fórmulas DAX são muito semelhantes às fórmulas do Excel. Na verdade, o DAX usa muitos operadores, funções e sintaxe também utilizados pelas fórmulas do Excel. No entanto, as funções DAX foram projetadas para trabalhar com dados relacionais e realizar cálculos mais dinâmicos durante nossa interação com os relatórios.

Há mais de 200 funções DAX que fazem tudo, desde agregações simples, como Soma e Média, até funções de estatística e de filtragem mais complexas. Não vamos entrar em muitos detalhes sobre a linguagem DAX aqui, mas há muitas fontes para ajudá-lo a saber mais. Depois de acompanhar este tutorial, não deixe de conferir [Noções básicas do DAX no Power BI Desktop](desktop-quickstart-learn-dax-basics.md).

Quando criamos nossas próprias medidas, elas são adicionadas à lista Campos da tabela desejada. Isso é conhecido como uma medida de *modelo*, que permanecerá em nossa tabela como sendo um campo. Algumas das grandes vantagens das medidas de modelo são a possibilidade de nomeá-las como quisermos, tornando-as mais identificáveis. Também podemos usá-las como um argumento em outras expressões DAX, além de criar medidas que executam cálculos complexos muito rapidamente.

## <a name="lets-create-our-own-measure"></a>Vamos criar nossa própria medida
Vamos supor que desejamos analisar nossas vendas líquidas. Se observarmos nossa tabela Sales na lista de campos, veremos que não há nenhum campo denominado NetSales. No entanto, temos os blocos de construção para criar nossa própria medida para calcular as vendas líquidas.

Precisamos de uma medida para subtrair descontos e devoluções dos valores de vendas. Por desejarmos que nossa medida calcule um resultado para qualquer contexto que tenhamos em nossa visualização, precisamos subtrair a soma de DiscountAmount e ReturnAmount da soma de SalesAmount. Isso pode parecer um pouco confuso no momento; não se preocupe, ficará mais claro em breve.

### <a name="net-sales"></a>Vendas Líquidas
**1.**  Clique com o botão direito do mouse na tabela **Sales** na lista de campos ou clique na seta para baixo nessa mesma tabela; em seguida, clique em **Nova Medida**. Isso garantirá que nossa nova medida seja salva na tabela Sales, na qual ela será mais fácil de ser encontrada.

![](media/desktop-tutorial-create-measures/meastut_netsales_newmeasure.png)

> [!TIP]
> Crie também uma nova medida clicando no botão Nova Medida na faixa de opções da guia Página Inicial do Power BI Desktop.
> 
> ![](media/desktop-tutorial-create-measures/meastut_netsales_newmeasureribbon.png)
> 
> Quando você cria uma medida na faixa de opções, a medida pode ser criada em qualquer uma das tabelas. Embora uma medida não precise pertencer a uma tabela específica, ela será mais fácil de localizar se você criá-la na tabela que, por lógica, faz mais sentido para você. Se você quiser que ela fique em uma tabela específica, clique na tabela primeiro, para torná-la ativa. Em seguida, clique em Nova Medida. Em nosso caso, vamos criar nossa primeira medida na tabela Sales.
> 
> 

A barra de fórmulas aparece na parte superior da Tela Relatório. É ali que podemos renomear nossa medida e inserir uma fórmula DAX.

![](media/desktop-tutorial-create-measures/meastut_netsales_newmeasure_formulabar.png)

Vamos dar um nome a nossa nova medida. Por padrão, uma nova medida é simplesmente chamada de Measure. Se não a renomearmos, a próxima medida que criamos será nomeada Measure 2, Measure 3 e assim por diante. Gostaríamos que nossas medidas fossem mais facilmente identificáveis, por isso vamos nomear nossa nova medida Net Sales.

**2.** Realce **Measure** na barra de fórmulas e digite **Net Sales**.

Agora, podemos começar a inserir nossa fórmula.

**3.**  Após o sinal de igual, digite um **S**. Você verá uma lista suspensa de sugestões aparecer com todas as funções DAX começando pela letra S. Quanto mais digitamos, mais a lista de sugestões é dimensionada aproximando-se da função que precisamos. Selecione **SUM** rolando para baixo e pressione Enter.

![](media/desktop-tutorial-create-measures/meastut_netsales_newmeasure_formula_s.png)

Após pressionarmos Enter, um parêntese de abertura é exibido junto com outra lista de sugestões de todas as colunas disponíveis que podemos passar para a função SUM.

![](media/desktop-tutorial-create-measures/meastut_netsales_newmeasure_formula_sum.png)

Uma expressão sempre aparece entre parênteses de abertura e de fechamento. Nesse caso, nossa expressão vai conter um único argumento para passar para a função SUM; uma coluna a somar. Podemos restringir a lista de colunas, digitando as primeiras letras do que queremos. Nesse caso, queremos a coluna SalesAmount, assim, quando começarmos a digitar “salesam”, nossa lista fica menor e observamos dois itens que podem ser selecionados. Na verdade, eles estão na mesma coluna. Um apenas mostra [SalesAmount], pois criamos nossas medidas na mesma tabela em que está a coluna SalesAmount. No outro, podemos ver o nome da tabela antes do nome da coluna.

![](media/desktop-tutorial-create-measures/meastut_netsales_newmeasure_formula_salesam.png)

Em geral, é uma boa prática inserir o nome totalmente qualificado de uma coluna. Ele tornará suas fórmulas mais fáceis de ler.

**4.** Selecione **Sales[SalesAmount]** e digite um parêntese de fechamento.

> [!TIP]
> Erros de sintaxe são causados frequentemente por um parêntese de fechamento ausente ou mal posicionado.
> 
> 

Agora, desejamos subtrair nossas outras duas colunas.

**5.**  Após o parêntese de fechamento para nossa primeira expressão, digite um espaço e um operador de subtração (**-**), seguido de outro espaço. Em seguida, insira outra função SUM tendo como argumento a coluna **Sales[DiscountAmount]** .

![](media/desktop-tutorial-create-measures/meastut_netsales_newmeasure_formula_discamount.png)

Estamos começando a ficar sem espaço para nossa fórmula. Sem problemas.

**6.**  Clique na divisa inferior no lado direito da barra de fórmulas.

![](media/desktop-tutorial-create-measures/meastut_netsales_newmeasure_formula_chevron.png)

Agora temos mais espaço. Podemos inserir novas partes de nossa fórmula em uma nova linha pressionando Alt-Enter. Também podemos mover itens usando a tecla Tab.

![](media/desktop-tutorial-create-measures/meastut_netsales_newmeasure_formula_expanded.png)

Agora podemos adicionar a parte final de nossa fórmula.

**7.**  Adicione outro operador de subtração, seguido de outra função SUM que tenha a coluna **Sales[ReturnAmount]** como argumento.

![](media/desktop-tutorial-create-measures/meastut_netsales_newmeasure_complete.png)

Nossa fórmula agora parece pronta.

**8.**  Pressione Enter ou clique na marca de confirmação na barra de fórmulas para concluir. A fórmula é validada e adicionada à lista de campos na tabela Sales.

### <a name="lets-add-our-new-measure-to-a-report"></a>Vamos adicionar nossa nova medida a um relatório
Agora podemos adicionar nossa medida Net Sales à tela Relatório; as vendas líquidas serão calculadas para quaisquer outros campos que adicionarmos ao relatório. Vamos examinar as vendas líquidas por país.

**1.**  Arraste a medida **Net Sales** da tabela **Sales** até a tela Relatório.

**2.** Agora, arraste o campo **RegionCountryName** da tabela **Geography** para o gráfico.

![](media/desktop-tutorial-create-measures/meastut_netsales_byrcn.png)

Vamos adicionar mais alguns dados.

**3.**  Arraste o campo **SalesAmount** até o gráfico, para ver a diferença entre o valor de vendas e o de vendas líquidas.

Agora temos realmente duas medidas em nosso gráfico. SalesAmount, que foi somada automaticamente, e a medida Net Sales que criamos. Em cada um dos casos, os resultados foram calculados no contexto de outro campo que temos no gráfico, os países em RegionCountryName.

![](media/desktop-tutorial-create-measures/meastut_netsales_byrcnandsalesamount.png)

Vamos adicionar uma Segmentação de dados, para podermos dividir nossas vendas líquidas e valores de vendas por ano civil.

**4.**  Clique em uma área em branco ao lado do gráfico e, em **Visualizações**, clique na visualização de Tabela.

![](media/desktop-tutorial-create-measures/meastut_netsales_blanktablevisbutton.png)

Isso cria uma nova visualização de tabela em branco na tela Relatório.

![](media/desktop-tutorial-create-measures/meastut_netsales_blanktable.png)

**5.**  Arraste o campo **Year** da tabela **Calendar** até a nova tabela em branco.

![](media/desktop-tutorial-create-measures/meastut_netsales_yearaggtable.png)

Como Year é um campo numérico, o Power BI Desktop somou seus valores e nos forneceu um gráfico. Mas isso não nos ajuda muito como uma Segmentação de Dados.

**6.** Em **Valores**, clique na seta para baixo ao lado de **Year** e em **Não Resumir**.

![](media/desktop-tutorial-create-measures/meastut_netsales_year_donotsummarize.png)

Agora podemos alterar o campo Year na visualização de tabela em uma Segmentação de Dados.

**7.**  Em **Visualizações**, clique na visualização **Segmentação**.

![](media/desktop-tutorial-create-measures/meastut_netsales_year_changetoslicer.png)

Agora temos Year como Segmentação de Dados. Podemos selecionar qualquer indivíduo ou grupo de anos e as visualizações de nosso relatório serão todas segmentadas de acordo.

**8.** Vá em frente e clique em **2013**. Você verá o gráfico mudar. Nossas medidas Net Sales e SalesAmount são recalculadas, mostrando os novos resultados apenas para 2013. Aqui, mais uma vez, alteramos o contexto no qual nossas medidas calculam e exibem os resultados.

![](media/desktop-tutorial-create-measures/meastut_netsales_chartslicedbyyear.png)

## <a name="lets-create-another-measure"></a>Vamos criar uma outra medida
Agora que você sabe como criar suas próprias medidas, vamos criar outra.

### <a name="net-sales-per-unit"></a>Net Sales per Unit
E se quisermos descobrir quais são os produtos com o maior valor líquido de vendas por unidade vendida?

Bem, vamos criar outra medida. Nesse caso, desejamos dividir as vendas líquidas pela quantidade de unidades vendidas. Assim, desejamos dividir o resultado de nossa medida Net Sales pela soma de Sales[SalesQuantity].

**1.**  Crie uma nova medida chamada **Net Sales per Unit** na tabela Sales ou Products.

Nessa medida, vamos usar a medida Net Sales que criamos anteriormente. Com o DAX, podemos fazer referência a outras medidas em nossa fórmula.

**2.**  Comece digitando **Net Sales**. A lista de sugestões mostrará o que podemos adicionar. Selecione **[Net Sales]**.

![](media/desktop-tutorial-create-measures/meastut_nspu_formulastep2a.png)

Você também pode fazer referência a outra medida digitando apenas um colchete de abertura (**[**). A lista de sugestões nos mostrará apenas as medidas que podemos adicionar à nossa fórmula.

![](media/desktop-tutorial-create-measures/meastut_nspu_formulastep2b.png)

**3.**  Logo após **[Net Sales]**, insira um espaço e, em seguida, um operador de divisão (**/**); depois, insira uma função SUM e digite **Quantity**. A lista de sugestões mostra todas as colunas cujo nome contém “Quantity”. Selecione **Sales[SalesQuantity]**. A fórmula agora deve ter essa aparência:

> **Net Sales per Unit = [Net Sales] / SUM(Sales[SalesQuantity])**
> 
> 

Muito legal, não? Inserir fórmulas DAX é realmente muito fácil quando usamos a funcionalidade de sugestão e pesquisa do Editor DAX. Agora, vamos ver o que obtemos com nossa nova medida Net Sales per Unit.

**4.** Arraste a medida **Net Sales per Unit** até uma área em branco na tela do relatório.

![](media/desktop-tutorial-create-measures/meastut_nspu_chart.png)

Não muito interessante, certo? Não se preocupe.

**5.**  Altere o tipo de visualização de gráfico para **Tree Map**.

![](media/desktop-tutorial-create-measures/meastut_nspu_changetotreemap.png)

**6.** Agora, arraste o campo **ProductCategory** da tabela **ProductCategory** para baixo até a área **Group**.

![](media/desktop-tutorial-create-measures/meastut_nspu_byproductcat.png)

Essas são boas informações, mas e se desejarmos examinar as vendas líquidas por produto?

**7.** Remova o campo **ProductCategory** e arraste o campo **ProductName** da tabela **Product** para baixo até a área **Group**. 

![](media/desktop-tutorial-create-measures/meastut_nspu_byproductname.png)

OK, agora estamos apenas experimentando, e temos que admitir que isso é bastante interessante! Obviamente, é possível filtrar este tree map de várias maneiras, mas isso está fora do escopo deste tutorial.

## <a name="what-weve-learned"></a>O que aprendemos
As medidas nos oferecem uma enorme capacidade de obter as informações que desejamos por meio de nossos dados. Aprendemos a criar medidas usando a barra de fórmulas. Podemos nomear medidas de uma maneira lógica, enquanto as listas de sugestão facilitam a localização e seleção do elemento certo a ser adicionado às nossas fórmulas. Também aprendemos sobre o contexto, no qual o resultado de cálculos em medidas muda de acordo com outros campos, ou por outras expressões na fórmula da medida.

## <a name="additional-resources"></a>Recursos adicionais
Se desejar se aprofundar nas fórmulas DAX e criar algumas medidas mais avançadas, veja [Noções básicas do DAX no Power BI Desktop](desktop-quickstart-learn-dax-basics.md). Este artigo enfoca os conceitos fundamentais no DAX, como sintaxe, funções e uma compreensão mais abrangente sobre o contexto.

Certifique-se de adicionar a [Referência ao DAX (Expressões de Análise de Dados)](https://msdn.microsoft.com/library/gg413422.aspx) aos favoritos. É nela que você encontrará informações detalhadas sobre a sintaxe do DAX, operadores, além de mais de 200 funções DAX.

