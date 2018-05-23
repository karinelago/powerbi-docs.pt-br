---
title: Usando tabelas calculadas no Power BI Desktop
description: Tabelas calculadas no Power BI Desktop
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 04/24/2018
ms.author: davidi
LocalizationGroup: Model your data
ms.openlocfilehash: 223cd6442f8856a2e7a7cabe234e6539cd119d4a
ms.sourcegitcommit: 638de55f996d177063561b36d95c8c71ea7af3ed
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/17/2018
---
# <a name="using-calculated-tables-in-power-bi-desktop"></a>Usando tabelas calculadas no Power BI Desktop
Com tabelas calculadas, você pode adicionar uma nova tabela ao modelo. Mas em vez de consultar e carregar valores nas colunas de sua nova tabela por meio de uma fonte de dados, você cria uma fórmula DAX (Data Analysis Expressions) que define os valores da tabela. No Power BI Desktop, as tabelas calculadas são criadas usando o recurso Nova Tabela na Exibição de Relatório ou Exibição de Dados.

Na maioria das vezes, você importa dados para o seu modelo de uma fonte de dados externa. No entanto, as tabelas calculadas oferecem certas vantagens. Tabelas calculadas são geralmente melhores para cálculos intermediários e para aqueles dados que você prefere que sejam armazenados como parte do modelo, em vez de calculados dinamicamente ou como parte de uma consulta.

Diferentemente das tabelas criadas como parte de uma consulta, as tabelas calculadas criadas na Exibição de Relatório ou Exibição de Dados são baseadas em dados que você já carregou no modelo. Por exemplo, você pode optar entre união convencional ou cruzada de duas tabelas.

Assim como ocorre para as tabelas normais, as tabelas calculadas podem ter relações com outras tabelas. As colunas na tabela calculada têm tipos de dados, formatação e podem pertencer a uma categoria de dados. Você pode nomear suas colunas como desejar e adicioná-las a uma visualização de relatório, assim como com outros campos. Tabelas calculadas são recalculadas se qualquer uma das tabelas das quais elas recebem dados por pull são renovadas ou atualizadas de qualquer maneira.

Tabelas calculadas calculam os resultados usando [DAX](https://msdn.microsoft.com/library/gg413422.aspx) (Data Analysis Expressions), uma linguagem de fórmula destinada a trabalhar com dados relacionais, como no Power BI Desktop. DAX inclui uma biblioteca de mais de 200 funções, operadores e construtores, fornecendo enorme flexibilidade na criação de fórmulas para calcular os resultados de praticamente qualquer análise de dados exigida.

## <a name="lets-look-at-an-example"></a>Vejamos um exemplo
Jeff, um gerente de projetos da Contoso, tem uma tabela com funcionários no Noroeste em e outra tabela com funcionários no Sudoeste. Jeff deseja mesclar as duas em uma única tabela.

**NorthwestEmployees**

 ![](media/desktop-calculated-tables/calctables_nwempl.png)

**SoutwestEmployees**

 ![](media/desktop-calculated-tables/calctables_swempl.png)

Com uma tabela calculada, é muito fácil unir essas duas tabelas. Embora Jeff possa criar uma tabela calculada na Exibição de Relatório ou Exibição de Dados, é um pouco mais fácil fazê-lo na Exibição de Dados porque assim ele pode ver imediatamente a nova tabela calculada.

Em **Exibição de Dados**, na guia **Modelagem** , Jeff clica em **Nova Tabela**. Uma barra de fórmulas é exibida.

 ![](media/desktop-calculated-tables/calctables_formulabarempty.png)

Jeff então insere a fórmula a seguir:

 ![](media/desktop-calculated-tables/calctables_formulabarformula.png)

É criada uma nova tabela chamada Western Region Employees.

 ![](media/desktop-calculated-tables/calctables_westregionempl.png)

A nova tabela Western Region Employees de Jeff aparece como qualquer outra tabela na lista Campos. Ele pode criar relações com outras tabelas, adicionar medidas e colunas calculadas e adicionar qualquer um de seus campos a relatórios, assim como com qualquer outra tabela.

 ![](media/desktop-calculated-tables/calctables_fieldlist.png)

## <a name="functions-for-calculated-tables"></a>Funções para tabelas calculadas
Tabelas calculadas podem ser definidas por qualquer expressão DAX que retorne uma tabela, incluindo uma simples referência a outra tabela. Por exemplo:

 ![](media/desktop-calculated-tables/calctables_formulabarsimpleformula.png)

Você pode usar tabelas calculadas com o DAX para solucionar muitos problemas analíticos. Fornecemos aqui apenas uma rápida introdução às tabelas calculadas. Conforme você começa a trabalhar com tabelas calculadas, veja aqui algumas das funções DAX de tabela mais comuns e que podem ser úteis:

* DISTINCT
* VALUES
* CROSSJOIN
* UNION
* NATURALINNERJOIN
* NATURALLEFTOUTERJOIN
* INTERSECT
* CALENDAR
* CALENDARAUTO

Consulte a [Referência de Função DAX](https://msdn.microsoft.com/ee634396.aspx) para essas e outras tabelas retornando funções DAX.

