---
title: "Noções básicas do DAX no Power BI Desktop"
description: "Noções básicas do DAX no Power BI Desktop"
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
ms.openlocfilehash: 761f25f92151c2bc2bd6557757de97e6ad8dd54d
ms.sourcegitcommit: 284b09d579d601e754a05fba2a4025723724f8eb
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/15/2017
---
# <a name="dax-basics-in-power-bi-desktop"></a>Noções básicas do DAX no Power BI Desktop
Este artigo é destinado aos novos usuários do Power BI Desktop. O objetivo é oferecer uma introdução rápida e fácil sobre como você pode usar expressões DAX (Data Analysis Expressions) para resolver vários problemas de análise de dados e de cálculo básico. Vamos examinar algumas informações conceituais e uma série de tarefas que você pode executar, além de alguns testes para verificar o que você aprendeu. Depois de ler este artigo, você deve ter uma boa compreensão dos conceitos fundamentais mais importantes no DAX.

## <a name="what-is-dax"></a>O que é DAX?
O DAX é uma coleção de funções, operadores e constantes que podem ser usados em uma fórmula, ou expressão, para calcular e retornar um ou mais valores. Resumindo, o DAX ajuda você a criar novas informações de dados já presentes em seu modelo.

## <a name="why-is-dax-so-important"></a>Por que DAX é tão importante?
É muito fácil criar um novo arquivo do Power BI Desktop e importar alguns dados nele. Você pode até mesmo criar relatórios que mostrem informações valiosas sem usar nenhuma fórmula DAX. Mas e se você precisar analisar o percentual de crescimento em diferentes categorias de produto e para intervalos de datas diferentes? Ou então, se você precisar calcular o crescimento ano a ano comparado às tendências do mercado? As fórmulas DAX oferecem essa e outras funcionalidades importantes também. Aprender a criar fórmulas DAX eficientes ajudará você a tirar o máximo proveito de seus dados. Quando obtém as informações de que precisa, você pode começar a resolver problemas comerciais reais, que afetam o seu resultado final. Esse é o potencial do Power BI, e o DAX ajudará você a aproveitá-lo.

## <a name="prerequisites"></a>Pré-requisitos
Você pode já estar familiarizado com a criação de fórmulas no Microsoft Excel. Esse conhecimento será útil na compreensão do DAX, mas mesmo se você não tiver experiência com fórmulas do Excel, os conceitos descritos aqui ajudarão você a começar a criar fórmulas DAX e resolver problemas do BI do mundo real, imediatamente.

Vamos nos concentrar em compreender as fórmulas DAX usadas em cálculos, mais especificamente, em medidas e colunas calculadas. Você já deve estar familiarizado com o Power BI Desktop, a importação de dados, a adição de campos a um relatório, além dos conceitos fundamentais de [Medidas](desktop-measures.md) e [Colunas calculadas](desktop-calculated-columns.md).

**Pasta de trabalho de exemplo**

A melhor maneira de aprender sobre o DAX é criar algumas fórmulas básicas, usá-las com alguns dados reais e ver os resultados. Os exemplos e as tarefas aqui usam o Exemplo de Vendas da Contoso para o arquivo de Visualização do Power BI Desktop. Esse é o mesmo arquivo de exemplo usado no artigo “Tutorial: criar suas próprias medidas no Power BI”. É possível baixá-lo [aqui](http://download.microsoft.com/download/4/6/A/46AB5E74-50F6-4761-8EDB-5AE077FD603C/Contoso%20Sales%20for%20Power%20BI%20Designer.zip).

## <a name="lets-begin"></a>Vamos começar!
Vamos estruturar nossa compreensão do DAX em torno de três conceitos fundamentais: *Sintaxe*, *Funções* e *Contexto*. Claro que há outros conceitos importantes no DAX, mas entender esses três conceitos oferecerá a melhor base para desenvolver suas habilidades com o DAX.

### <a name="syntax"></a>Sintaxe
Antes de criar suas próprias fórmulas, vamos dar uma olhada na sintaxe das fórmulas DAX. A sintaxe inclui os vários elementos que compõem uma fórmula, ou mais resumidamente, o modo como a fórmula é escrita. Por exemplo, vamos examinar uma medida de uma fórmula DAX simples.

![](media/desktop-quickstart-learn-dax-basics/qsdax_1_syntax.png)

Esta fórmula inclui os seguintes elementos de sintaxe:

**A.** O nome da medida **Total Sales**.

**B.** O operador de sinal de igual (**=**) indica o início da fórmula. Quando calculada, ela retornará um resultado.

**C.** A função **SUM** do DAX soma todos os números na coluna **Sales[SalesAmount]**. Você aprenderá mais sobre as funções mais tarde.

**D.** Os parênteses **()** envolvem uma expressão que contém um ou mais argumentos. Todas as funções exigem pelo menos um argumento. Um argumento transmite um valor para uma função.

**E.** A tabela referenciada **Sales**.

**F.** A coluna referenciada **[SalesAmount]** na tabela Sales. Com este argumento, a função SUM sabe em que coluna deve agregar uma SUM.

Ao tentar entender uma fórmula DAX, geralmente é útil decompor os elementos em uma linguagem que você usa e fala todos os dias. Por exemplo, você pode ler esta fórmula como:

> *Para a medida chamada Total Sales, calcule (=) a SUM dos valores na coluna [SalesAmount], na tabela Sales.*
> 
> 

Quando adicionada a um relatório, essa medida calcula e retorna valores somando as quantidades de vendas para cada um dos outros campos que são incluídos, por exemplo, “Cell Phones in the USA”.

Você deve estar pensando: “Por acaso essa medida não faz a mesma coisa que adicionar o campo SalesAmount ao meu relatório?” Bem, sim. Porém, há um bom motivo para criar nossa própria medida que soma os valores do campo SalesAmount: podemos usar isso como um argumento em outras fórmulas. Isso pode parecer um pouco confuso agora, mas à medida que suas habilidades com fórmulas DAX aumentarem, saber disso tornará suas fórmulas e seu modelo mais eficientes. Na verdade, você verá mais tarde a medida Total Sales aparecendo como um argumento em outras fórmulas.

Vamos dar uma olhada em mais alguns pontos sobre essa fórmula. Em especial, vale lembrar que introduzimos uma função, [SUM](https://msdn.microsoft.com/library/ee634387.aspx). Funções são fórmulas gravadas previamente, que tornam mais fácil fazer cálculos complexos e manipulações com números, datas, hora, texto e muito mais. Você aprenderá mais sobre as funções mais tarde.

Você também pode ver que a coluna [SalesAmount] era precedida pela tabela Sales, à qual a coluna pertence. Isso é conhecido como um nome de coluna totalmente qualificado, que inclui o nome da coluna precedido pelo nome da tabela. Colunas referenciadas na mesma tabela não exigem que o nome da tabela seja incluído na fórmula. Isso pode tornar fórmulas longas, que fazem referência a várias colunas, mais curtas e fáceis de ler. No entanto, é uma prática recomendada incluir o nome da tabela em suas fórmulas de medida, mesmo quando se tratar da mesma tabela.

> [!NOTE]
> Se um nome de tabela contiver espaços, palavras-chave reservadas ou caracteres não permitidos, coloque o nome da tabela entre aspas simples. Além disso, você precisará colocar os nomes de tabela entre aspas se o nome contiver quaisquer caracteres fora do conjunto de caracteres alfanuméricos ANSI, independentemente de sua localidade dar ou não suporte ao conjunto de caracteres.
> 
> 

É importante que suas fórmulas tenham a sintaxe correta. Na maioria dos casos, se a sintaxe não estiver correta, um erro de sintaxe será retornado. Em outros casos, a sintaxe pode estar correta, mas os valores retornados podem não ser o que você esperava. O editor do DAX no Power BI Desktop inclui sugestões, um recurso usado para criar fórmulas sintaticamente corretas, ajudando você a selecionar os elementos corretos.

Vamos criar uma fórmula simples. Essa tarefa ajudará você a entender melhor a sintaxe da fórmula e como o recurso de sugestões na barra de fórmulas pode ajudá-lo.

### <a name="task-create-a-measure-formula"></a>Tarefa: criar uma fórmula de medida
Para concluir esta tarefa, você precisará abrir o arquivo Exemplo de Vendas da Contoso para o Power BI Desktop.

**1.**  Na visualização de Relatório, na lista Campos, clique com o botão direito do mouse na tabela **Sales** e clique em **Nova Medida**.

**2.**  Na barra de fórmulas, substitua **Measure** digitando um novo nome de medida, **Previous Quarter Sales**.

**3.**  Após o sinal de igual, digite **SUM**, seguido de um parêntese de abertura.

> Em vez de digitar um nome de coluna para somar imediatamente, vamos inserir outra função para *filtrar* os dados que desejamos somar.
> 
> 

**4.**  Entre os parênteses, digite **CALCULATE**, seguido de um parêntese de abertura.

> Você usará a função CALCULATE para filtrar os valores que desejamos somar por um argumento que transmitimos à função CALCULATE. É isso que chamamos de aninhar funções. A função CALCULATE tem pelo menos dois argumentos. O primeiro é a expressão a ser avaliada e o segundo é um filtro.
> 
> 

**5.**  Entre os parênteses **()** para a função **CALCULATE**, digite **Sales[SalesAmount]**. Esse é o primeiro argumento de expressão para a função CALCULATE.

**6.** Digite uma vírgula (**,**) para especificar o primeiro filtro e, em seguida, digite **PREVIOUSQUARTER** seguido de um parêntese de abertura.

> Você usará a função de time intelligence PREVIOUSQUARTER para filtrar nossos resultados SUM pelo trimestre anterior.
> 
> 

**7.** Entre os parênteses **()**, para a função PREVIOUSQUARTER, digite **Calendar[DateKey]**.

> A função PREVIOUSQUARTER tem um argumento, uma coluna contendo um intervalo contíguo de datas.
> 
> 

**8.** Verifique se ambos os argumentos passados para as funções PREVIOUSQUARTER e CALCULATE estão entre dois parênteses de fechamento **))**.

Sua fórmula agora deve ter essa aparência:

> **Previous Quarter Sales = CALCULATE(SUM(Sales[SalesAmount]), PREVIOUSQUARTER(Calendar[DateKey]))**
> 
> 

**9.** Clique na marca de seleção ![](media/desktop-quickstart-learn-dax-basics/qsdax_syntax_taskcheckmark.png) na barra de fórmulas ou pressione Enter para validar a fórmula e adicioná-la ao modelo.

Você conseguiu! Você acabou de criar uma medida usando DAX, e não estamos falando de uma medida fácil. O que essa fórmula fará é calcular o total de vendas do trimestre anterior, dependendo dos filtros aplicados em um relatório. Por exemplo, se colocamos SalesAmount e nossa nova medida Previous Quarter Sales em um gráfico e adicionamos Year e QuarterOfYear como Segmentações de Dados, obteremos algo semelhante ao exemplo abaixo:

![](media/desktop-quickstart-learn-dax-basics/qsdax_3_chart.png)

Você acabou de conhecer vários aspectos importantes das fórmulas DAX. Em primeiro lugar, esta fórmula incluiu duas funções. É importante observar que [PREVIOUSQUARTER](https://msdn.microsoft.com/library/ee634385.aspx), uma função de inteligência de dados temporais, está aninhada como um argumento transmitido para [CALCULATE](https://msdn.microsoft.com/library/ee634825.aspx), uma função de filtro. Fórmulas DAX podem conter até 64 funções aninhadas. É improvável que uma fórmula chegue a conter tantas funções aninhadas. Na verdade, uma fórmula como essa seria muito difícil de criar e depurar; além disso, ela provavelmente não seria muito rápida.

Nesta fórmula, você também usou filtros. Filtros restringem o que será calculado. Nesse caso, você selecionou um filtro como um argumento, que é, na verdade, o resultado de outra função. Você aprenderá mais sobre filtros posteriormente.

Por fim, você usou a função CALCULATE. Essa é uma das funções mais poderosas em DAX. Conforme você criar modelos e fórmulas mais complexas, provavelmente utilizará essa função muitas vezes. Discutir a função CALCULATE está fora do escopo deste artigo, mas fique atento a ela conforme seu conhecimento sobre o DAX aumentar.

### <a name="syntax-quickquiz"></a>Teste rápido sobre sintaxe
1. Qual é a função desse botão na barra de fórmulas?
   
   > ![](media/desktop-quickstart-learn-dax-basics/qsdax_2_syntaxquiz.png)
   > 
   > 
2. O que sempre está em torno de um nome de coluna em uma fórmula DAX?

As respostas são fornecidas no final deste artigo.

### <a name="functions"></a>Funções
Funções são fórmulas predefinidas que realizam cálculos usando valores específicos, chamados argumentos, em uma determinada ordem ou estrutura. Argumentos podem ser outras funções, outra fórmula, expressão, referências de coluna, números, texto, valores lógicos como TRUE ou FALSE, ou constantes.

O DAX inclui as seguintes categorias de funções: [Data e Hora](https://msdn.microsoft.com/library/ee634786.aspx), [Inteligência de Dados Temporais](https://msdn.microsoft.com/library/ee634763.aspx)[,](https://msdn.microsoft.com/library/ee634552.aspx)[Informações](https://msdn.microsoft.com/library/ee634552.aspx), [Lógica](https://msdn.microsoft.com/library/ee634365.aspx)[,](https://msdn.microsoft.com/library/ee634365.aspx)[Matemática](https://msdn.microsoft.com/library/ee634241.aspx), [Estatística](https://msdn.microsoft.com/library/ee634822.aspx), [Texto](https://msdn.microsoft.com/library/ee634938.aspx), [Pai/Filho](https://msdn.microsoft.com/library/mt150102.aspx) e [Outras](https://msdn.microsoft.com/library/mt150101.aspx). Se já estiver familiarizado com as funções em fórmulas do Excel, muitas das funções no DAX podem parecer semelhantes para você. No entanto, as funções DAX são exclusivas nos seguintes aspectos:

* Uma função DAX sempre referencia uma coluna ou uma tabela completa. Se desejar usar apenas valores específicos de uma tabela ou coluna, é possível adicionar filtros à fórmula.
* Se precisar personalizar cálculos linha por linha, o DAX fornece funções que permitem usar o valor da linha atual ou um valor relacionado como um tipo de argumento, para realizar cálculos que variam de acordo com o contexto. Você aprenderá mais sobre contexto posteriormente.
* O DAX inclui várias funções que retornam uma tabela em vez de um valor. A tabela não é exibida, mas é usada para fornecer informações de entrada a outras funções. Por exemplo, é possível recuperar uma tabela e, em seguida, contar os valores distintos contidos nela, ou calcular somas dinâmicas em diferentes colunas ou tabelas filtradas.
* O DAX inclui uma variedade de funções de inteligência de dados temporais. Estas funções permitem definir ou selecionar intervalos de datas e executar cálculos dinâmicos, baseados nesses intervalos. Por exemplo, é possível comparar somas em períodos paralelos.
* O Excel tem uma função muito popular, VLOOKUP. As funções DAX não usam uma célula ou intervalo de células como referência, como a VLOOKUP faz no Excel. As funções DAX usam uma coluna ou tabela como referência. Lembre-se: no Power BI Desktop, você está trabalhando com um modelo de dados relacionais. Procurar por valores em outra tabela é realmente muito fácil e, na maioria dos casos, você não precisa criar nenhuma fórmula.
  
  Como você pode ver, as funções no DAX podem ajudá-lo a criar fórmulas muito poderosas. Nós abordamos apenas as noções básicas das funções. Na medida em que suas habilidades com DAX aumentarem, você criará fórmulas usando muitas funções diferentes. Um dos melhores lugares para obter detalhes sobre cada uma das funções DAX é a [Referência de funções DAX](https://msdn.microsoft.com/library/ee634396.aspx).

### <a name="functions-quickquiz"></a>Teste rápido sobre funções
1. Uma função sempre faz referência a que?
2. Uma fórmula pode conter mais de uma função?
3. Que categoria de funções você usaria para concatenar duas cadeias de caracteres de texto em uma cadeia de caracteres?

As respostas são fornecidas no final deste artigo.

### <a name="context"></a>Contexto
Contexto é um dos conceitos do DAX mais importantes para se compreender. Há dois tipos de contexto em DAX: o contexto de linha e o contexto de filtro. Primeiro, vamos dar uma olhada no contexto de linha.

**Contexto de linha**

É mais fácil pensar no contexto de linha como a linha atual. Ele se aplica sempre que uma fórmula tem uma função que utiliza filtros para identificar uma única linha em uma tabela. A função aplicará inerentemente um contexto de linha a cada linha da tabela que essa função está filtrando. Esse tipo de contexto de linha geralmente se aplica a medidas.

**Contexto de Filtro**

O contexto do filtro é um pouco mais difícil de entender do que o contexto de linha. É mais fácil pensar no contexto de filtro como um ou mais filtros aplicados em um cálculo que determina um resultado ou valor.

O contexto de filtro não existe no lugar do contexto de linha; em vez disso, eles são aplicados em conjunto. Por exemplo, para restringir ainda mais os valores a serem incluídos em um cálculo, você pode aplicar um contexto de filtro que não só especifica o contexto de linha, mas também especifica apenas um valor específico (filtro) nesse contexto de linha.

O contexto de filtro é visto facilmente em seus relatórios. Por exemplo, ao adicionar TotalCost a uma visualização e, em seguida, Year e Region, você está definindo um contexto de filtro que seleciona um subconjunto de dados com base em um determinado ano e região.

Por que o contexto de filtro é tão importante no DAX? Visto que, embora o contexto de filtro possa ser aplicado mais facilmente pela adição de campos a uma visualização, ele também pode ser aplicado em uma fórmula DAX pela definição de um filtro com funções como ALL, RELATED, FILTER, CALCULATE, por relações e por outras medidas e colunas. Por exemplo, vamos dar uma olhada na seguinte fórmula em uma medida chamada Store Sales:

![](media/desktop-quickstart-learn-dax-basics/qsdax_4_context.png)

Para entender melhor essa fórmula podemos decompô-la, de modo muito similar ao que ocorre em outras fórmulas.

Esta fórmula inclui os seguintes elementos de sintaxe:

**A.** O nome da medida **Store Sales**.

**B.** O operador de sinal de igual (**=**) indica o início da fórmula.

**C.** A função **CALCULATE** avalia uma expressão, como um argumento, em um contexto que é modificado pelos filtros especificados.

**D.** Os parênteses **()** envolvem uma expressão que contém um ou mais argumentos.

**E.** Uma medida **[Total Sales]** na mesma tabela como uma expressão. A medida Total Sales tem a fórmula: =SUM(Sales[SalesAmount]).

**F.** Uma vírgula (**,**) separa o primeiro argumento da expressão do argumento do filtro.

**G.** A coluna referenciada totalmente qualificada, **Channel[ChannelName]**. Esse é o nosso contexto de linha. Cada linha nesta coluna especifica um canal: Store, Online, etc.

**H.** O valor específico, **Store**, como um filtro. Esse é o nosso contexto de filtro.

Esta fórmula garante que somente valores de vendas definidos pela medida Total Sales sejam calculados, apenas para linhas na coluna Channel[ChannelName] e usando o valor "Store" como um filtro.

Como você pode imaginar, a capacidade de definir o contexto de filtro em uma fórmula apresenta funcionalidades incríveis e poderosas. Ser capaz de fazer referência a um determinado valor em uma tabela relacionada é apenas um exemplo. Não se preocupe se você não entender totalmente o contexto, logo de imediato. Ao criar suas próprias fórmulas, você entenderá melhor o contexto e a razão pela qual ele é tão importante no DAX.

### <a name="context-quickquiz"></a>Teste rápido de contexto
1. Quais são os dois tipos de contexto?
2. O que é o contexto de filtro?
3. O que é o contexto de linha?

As respostas são fornecidas no final deste artigo.

## <a name="summary"></a>Resumo
Agora que você tem uma noção básica dos conceitos mais importantes do DAX, você pode começar a criar fórmulas DAX para medidas por conta própria. DAX pode ser realmente um pouco difícil de aprender, mas há muitas fontes de aprendizado disponíveis para você. Depois de ler este artigo e experimentar algumas das suas próprias fórmulas, você pode aprender mais sobre outros conceitos e fórmulas de DAX que podem ajudá-lo a resolver seus próprios problemas empresariais. Há muitos recursos do DAX disponíveis para você: o mais importante é a [Referência ao DAX (Expressões de Análise de Dados)](https://msdn.microsoft.com/library/gg413422.aspx).

DAX já existe há anos em outras ferramentas de BI da Microsoft, como modelos de tabela do Analysis Services e Power Pivot, portanto, há muitas informações disponíveis. Você encontrará mais informações em white papers, livros e blogs tanto da Microsoft quanto de profissionais de BI de vanguarda. O [Wiki do Centro de Recursos do DAX no TechNet](http://social.technet.microsoft.com/wiki/contents/articles/dax-resource-center.aspx) também é um ótimo lugar para começar.

### <a name="quickquiz-answers"></a>Respostas do Teste Rápido
Sintaxe:

1. Valida e insere a medida no modelo.
2. Colchetes [].

Funções:

1. Uma tabela e uma coluna.
2. Sim. Uma fórmula pode conter até 64 funções aninhadas.
3. [Funções de texto](https://msdn.microsoft.com/library/ee634938.aspx).

Contexto:

1. Contexto de linha e contexto de filtro.
2. Um ou mais filtros em um cálculo que determina um único valor.
3. A linha atual.

