---
title: Usar medidas no Power BI Desktop
description: Medidas no Power BI Desktop
services: powerbi
documentationcenter: ''
author: davidiseminger
manager: kfile
backup: ''
editor: ''
tags: ''
qualityfocus: no
qualitydate: ''
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 05/02/2018
ms.author: davidi
LocalizationGroup: Model your data
ms.openlocfilehash: 6f9bec7802b2b16874dccd5b264c177fb4f4e2b0
ms.sourcegitcommit: f679c05d029ad0765976d530effde744eac23af5
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="measures-in-power-bi-desktop"></a>Medidas no Power BI Desktop
O **Power BI Desktop** ajuda a criar informações sobre seus dados com apenas alguns cliques. Mas, às vezes, esses dados simplesmente não incluem tudo o que você precisa para responder algumas de suas perguntas mais importantes. As medidas podem ajudá-lo a alcançar essa meta.

As medidas são usadas em algumas das análises de dados mais comuns; por exemplo, somas, médias, valores mínimos ou máximos, contagens ou cálculos mais avançados que você cria por conta própria usando uma fórmula DAX. Os resultados calculados das medidas estão sempre mudando em resposta à sua interação com seus relatórios, permitindo uma exploração de dados ad hoc, rápida e dinâmica. Vamos ver isso mais de perto.

## <a name="understanding-measures"></a>Noções básicas sobre medidas
No **Power BI Desktop**, as medidas são criadas e usadas na **Exibição de Relatório** ou na **Exibição de Dados**. As medidas que você cria são exibidas na lista Campos com um ícone de calculadora. Você pode nomear as medidas como desejar e adicioná-las a uma visualização nova ou existente, assim como com qualquer outro campo.

![](media/desktop-measures/measuresinpbid_measinfieldlist.png)

> [!NOTE]
> Talvez sejam também de seu interesse **medidas rápidas**, que são medidas prontas que podem ser selecionadas nas caixas de diálogo. Elas são uma boa maneira de criar medidas rapidamente e também de aprender a sintaxe DAX, uma vez que suas fórmulas DAX criadas automaticamente estão disponíveis para examinar. Confira o artigo: [medidas rápidas](desktop-quick-measures.md).
> 
> 

## <a name="data-analysis-expressions"></a>Data Analysis Expressions (expressões de análise de dados)
As medidas calculam um resultado por meio de uma fórmula de expressão. Quando criar suas próprias medidas, você usará a linguagem de fórmula DAX [(Data Analysis Expressions)](https://msdn.microsoft.com/library/gg413422.aspx). DAX inclui uma biblioteca de mais de 200 funções, operadores e construtores, fornecendo enorme flexibilidade na criação de medidas para calcular os resultados de praticamente qualquer análise de dados exigida.

As fórmulas DAX são muito semelhantes às fórmulas do Excel. DAX tem até mesmo muitas das mesmas funções, como DATE, SUM e LEFT. As funções do DAX, no entanto, devem funcionar com dados relacionais, como os que temos no Power BI Desktop.

## <a name="lets-look-at-an-example"></a>Vejamos um exemplo
Julia é gerente de vendas da Contoso. Foi requisitado que ela fornecesse projeções de vendas de revendedores para o próximo ano fiscal. Ela decide basear suas estimativas nos valores de vendas do ano anterior, com um aumento anual de 6% resultante de várias promoções agendadas para os próximos seis meses.

Para relatar as estimativas, ela importa os dados de vendas do ano anterior no Power BI Desktop. Ela localiza o campo SalesAmount na tabela Reseller Sales. Como os dados importados por ela contêm somente valores de vendas para o último ano, ela renomeia o campo SalesAmount para Last Years Sales. Em seguida, ela arrasta Last Years Sales para a tela Relatório. Eles aparecem em uma visualização de gráfico como um valor único, que é a soma de todas as vendas dos revendedores do ano anterior.

Ela observa que um cálculo foi fornecido automaticamente, embora ela não tenha especificado nenhum. O Power BI Desktop criou sua própria medida somando todos os valores em Last Years Sales.

No entanto, Julia precisa de uma medida para calcular as projeções de vendas para o próximo ano, que serão baseadas nas vendas do ano anterior multiplicadas por 1,06 - para considerar o aumento de 6% esperado nos negócios. Para esse cálculo, ela criará sua própria medida. Usando o recurso Nova Medida, ela cria uma nova medida e, em seguida, insere a seguinte fórmula DAX:

    Projected Sales = SUM('Sales'[Last Years Sales])*1.06

Em seguida, Jan arrasta sua nova medida Projected Sales até o gráfico.

![](media/desktop-measures/measuresinpbid_lastyearsales.png)

Muito rapidamente e com pouquíssimo trabalho, Jan agora tem uma medida para calcular as vendas projetadas. Ela poderá analisar melhor suas projeções filtrando por revendedores específicos ou adicionando outros campos ao seu relatório.

## <a name="learn-more"></a>Saiba mais
Fornecemos aqui apenas uma rápida introdução às medidas, mas há muito mais conteúdo para lhe ajudar a criá-las por conta própria. Não deixe de conferir [Tutorial: Create calculated columns in Power BI Desktop](desktop-tutorial-create-measures.md) (Tutorial: criar suas próprias medidas no Power BI Desktop), em que você pode baixar um arquivo de exemplo e obter lições passo a passo sobre como criar mais medidas.  

Para se aprofundar mais no DAX, não deixe de conferir [DAX basics in Power BI Desktop](desktop-quickstart-learn-dax-basics.md) (Noções básicas do DAX no Power BI Desktop). A [Referência de Data Analysis Expressions](https://msdn.microsoft.com/library/gg413422.aspx) fornece artigos detalhados sobre cada uma das funções, sintaxe, operadores e convenções de nomenclatura. DAX já existe há muitos anos no Power Pivot em Excel e SQL Server Analysis Services, portanto, há muitos outros recursos excelentes disponíveis. Não deixe de conferir o [Wiki do Centro de Recursos do DAX](http://social.technet.microsoft.com/wiki/contents/articles/1088.dax-resource-center.aspx), no qual membros influentes da comunidade de BI compartilham seus conhecimentos sobre o DAX.



