---
title: "Agregações (soma, média, máximo, etc.) no Power BI"
description: "Alterar a agregação em um gráfico (soma, média, máximo, etc.) no Power BI"
services: powerbi
documentationcenter: 
author: mihart
manager: kfile
backup: 
editor: 
tags: 
qualityfocus: modifying
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 09/23/2017
ms.author: mihart
ms.openlocfilehash: 42f9ec1dd56c2317bec07abde9822fc2b5340c07
ms.sourcegitcommit: 99cc3b9cb615c2957dde6ca908a51238f129cebb
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/13/2017
---
# <a name="aggregates-in-power-bi"></a>Agregações no Power BI
## <a name="what-is-an-aggregate"></a>O que é uma agregação?
Às vezes, você deseja combinar matematicamente os valores de linhas em uma coluna. A operação matemática pode ser soma, média, máximo, contagem etc. O ato de combinar o valor dos dados em linhas de uma coluna é chamado de agregação. O resultado dessa operação matemática é um *agregado*. 

Um campo numérico é um valor que será agregado (somado ou cuja média será obtida, por exemplo) em um campo categórico.  Por exemplo, “valor de vendas por produto” e “número de defeitos por região”. Campos numéricos costumam ser chamados de **medidas**. Na lista Campos, a medidas são mostradas com o símbolo ∑. Para obter mais informações, veja [O editor de relatório... Faça um tour](service-the-report-editor-take-a-tour.md).

Às vezes, uma *medida* é, de fato, uma *medida calculada*. As medidas calculadas no Power BI são importadas com os dados (definidos no modelo de dados no qual o relatório se baseia). Cada medida calculada tem sua própria fórmula embutida em código. Você não pode alterar a agregação usada, por exemplo, se ela for uma soma, ela só poderá ser uma soma. Na lista Campos, as *medidas calculadas* são mostradas com o símbolo de calculadora. Para obter mais informações sobre como as medidas calculadas são criadas, consulte [Medidas no Power BI Desktop](desktop-measures.md).

Os campos categóricos não são numéricos, mas mesmo assim podem ser agregados.  Quando os campos categóricos são colocados em um bucket *somente numérico* como **Valores** ou **Dicas de ferramenta**, o Power BI pode contar as ocorrências ou as ocorrências distintas de cada categoria.  Para cadeias de caracteres e datas, o Power BI conta com algumas outras opções de agregação: o mais recente, o menos recente, primeiro e último.  

## <a name="why-dont-aggregates-work-the-way-i-want-them-to"></a>Por que as agregações não funcionam do jeito que eu quero?
Trabalhar com agregações no serviço do Power BI pode ser confuso; talvez você tenha um campo numérico e o Power BI não permitirá que você altere a agregação. Ou talvez você tenha um campo, como um ano, e você não deseja agregá-lo, apenas contar o número de ocorrências.

Geralmente, a origem do problema é como o campo foi categorizado no conjunto de dados do Power BI. Talvez o campo esteja categorizado como texto e isso explica por que ele não pode ser somado ou por que não é possível obter sua média. Infelizmente, [somente o proprietário do conjunto de dados pode alterar a maneira como um campo é categorizado](desktop-measures.md).  

Para ajudá-lo a evitar essa confusão, temos uma seção especial ao final deste artigo chamada **Dicas e solução de problemas**.  Caso você não encontre a resposta nessa seção, poste sua pergunta no [fórum da Comunidade do Power BI](http://community.powerbi.com) para obter uma resposta rápida diretamente da equipe do Power BI.

## <a name="change-how-a-numeric-field-is-aggregated"></a>Mudar a forma como um campo numérico é agregado
Digamos que você tenha um gráfico que resume is dados de vendas de regiões diferentes, mas você prefere a média. 

1. No Modo de Exibição de Edição do relatório, adicione a medida a uma visualização.
2. Encontre o campo no painel de visualizações, clique com o botão direito do mouse e selecione o tipo de agregação que você precisa. Se você não vir a agregação que precisa, contate o proprietário do conjunto de dados. Pode ser um problema com a maneira como o campo foi categorizado pelo proprietário.  
   
   ![](media/service-aggregates/aggregate_new.png)
   
   > [!NOTE]
   > As opções disponíveis na lista suspensa variarão dependendo 1) do campo selecionado e 2) da maneira que o campo foi categorizado pelo proprietário do conjunto de dados.
   > 
   > 

Algumas das opções que podem estar disponíveis para um campo de agregação:

* **Não resumir**. Com essa opção escolhida, cada valor nesse campo é tratada separadamente e não resumida. Isso geralmente é usado se você tiver uma coluna de ID numérica que não deve ser somada.
* **Soma**. Isso adiciona todos os valores nesse campo para cima.
* **Média**. Usa uma média aritmética dos valores.
* **Mínimo**. Mostra o menor valor.
* **Máximo**. Mostra o maior valor.
* **Contagem (Não em branco).** Isso conta o número de valores no campo que não está em branco.
* **Contagem (Distinto).** Isso conta o número de valores diferentes no campo.
* **Desvio padrão.**
* **Variação**.
* **Mediana**.  Mostra o valor mediano (meio). Esse é o valor que tem o mesmo número de itens acima e abaixo.  Se houver duas medianas, o Power BI obterá suas médias.

Por exemplo, esses dados:

| País | Quantidade |
|:--- |:--- |
| EUA |100 |
| REINO UNIDO |150 |
| Canadá |100 |
| Alemanha |125 |
| França | |
| Japão |125 |
| Austrália |150 |

Daria os seguintes resultados:

* **Não resumir**: cada valor é exibido separadamente
* **Soma**: 750
* **Média**: 125
* **Máximo**: 150
* **Mínimo**: 100
* **Contagem (não em branco):** 6
* **Contagem (distinta):** 4
* **Desvio padrão:** 20.4124145...
* **Variação:** 416.666...
* **Mediana:** 125

## <a name="use-a-non-aggregated-field-as-a-numeric-field"></a>Usar um campo não agregado como um campo numérico
Você também pode usar um campo não agregado como um campo numérico. Por exemplo, se tiver um campo Nome do Produto, você poderá adicioná-lo como um valor e defini-lo como **Contagem** ou **Contagem distinta**. 

1. Por exemplo, se você selecionar **Loja > Rede**.
   
   ![](media/service-aggregates/count-of-chain-do_not_summarize.png)
2. E se você alterar a agregação do padrão **Não resumir** para **Contagem (Distinta)**, o Power BI contará o número de diferentes cadeias. Nesse caso, existem 2: Fashions Direct e Lindseys.
   
   ![](media/service-aggregates/aggregates_count.png)
3. Se você alterar a agregação para **Contagem**, o Power BI contará o número total. Nesse caso, há 104 entradas para **Cadeia**. Adicionando **Cadeia** como filtro, você pode ver que há 37 linhas para Fashions Direct e 67 para Lindseys.  
   
   ![](media/service-aggregates/count_of_chain_104.png)

## <a name="tips-and-troubleshooting"></a>Dicas e Solução de problemas
P: Por que não vejo uma opção **Não resumir**?

R: O campo que você selecionou provavelmente é uma medida calculada. Lembre-se de que cada medida calculada tem sua própria fórmula embutida em código. Não é possível alterar o cálculo.

P: Meu campo **é** numérico. Por que as únicas opções exibidas são **Contagem** e **Contagem distinta**?

R: A explicação provável é que o proprietário do conjunto de dados, acidental ou intencionalmente, *não* classificou o campo como um número. Por exemplo, se um conjunto de dados tiver um campo **ano**, o proprietário do conjunto de dados poderá categorizar como texto porque é mais provável que o campo **ano** será contado (ou seja, o número de pessoas nascidos em 1974) e não que ele será somado ou terá a média calculada. Se você for o proprietário, poderá abrir o conjunto de dados no Power BI Desktop e usar a guia **Modelagem** para alterar o tipo de dados.  

R: Outra possibilidade é que você soltou o campo em um *bucket* que permite somente valores categóricos.  Nesse caso, as únicas opções serão contagem e contagem distinta.

R: E uma terceira possibilidade é que você está usando o campo para um eixo. Em um eixo de gráfico de barras, por exemplo, o Power BI mostra uma barra para cada valor distinto – ele não agrega os valores de campo. OBSERVAÇÃO: a exceção para essa regra são os gráficos de dispersão, que *exigem* valores de agregação para os eixos X e Y.

P: Tenho um diagrama de dispersão e *não* quero que meu campo seja agregado.  Como faço isso?

R: Adicione o campo ao bucket **Detalhes** e não aos buckets dos eixos X ou Y.

P: Quando adiciono um campo numérico a uma visualização, a maioria deles usa soma como padrão, mas outros usam média ou contagem ou alguma outra agregação como padrão.  Por que a agregação padrão nem sempre é a mesma?

R: Os proprietários de conjuntos de dados têm a opção de definir o resumo padrão para cada campo. Se você for um proprietário de conjunto de dados, altere o resumo padrão na guia **Modelagem** do Power BI Desktop.

P: Meu campo **é** numérico. Por que não existem opções de agregação na lista suspensa?

R: Se o campo tem um ícone de calculadora, isso significa que ele é uma *medida calculada* e cada medida calculada tem sua própria fórmula embutida em código que não pode ser alterada no serviço do Power BI. O cálculo que está sendo usado pode ser uma agregação simples como uma média ou soma, mas também algo mais complicado, como um “percentual de contribuição para a categoria pai” ou “total acumulado desde o início do ano”. O Power BI não vai somar nem obter a média dos resultados, mas em vez disso, apenas calculará novamente (usando a fórmula embutida em código) para cada ponto de dados.

P: Sou o proprietário de um conjunto de dados e quero garantir que um campo nunca é agregado.

R: No Power BI Desktop, na guia **Modelagem**, defina **Tipo de dados** como **Texto**.

P: Não consigo ver **Não resumir** como uma opção na lista suspensa.

R: Tente remover o campo e adicioná-lo novamente.

Mais perguntas? [Experimente a Comunidade do Power BI](http://community.powerbi.com/)

