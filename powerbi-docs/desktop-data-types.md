---
title: Tipos de dados no Power BI Desktop
description: Tipos de dados no Power BI Desktop
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
ms.openlocfilehash: da685cf95adb9d9f5bd4891f9447cbfe76759182
ms.sourcegitcommit: f2b38777ca74c28f81b25e2f739e4835a0ffa75d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/17/2017
---
# <a name="data-types-in-power-bi-desktop"></a>Tipos de dados no Power BI Desktop
Este artigo descreve os tipos de dados com suporte no Power BI Desktop e DAX (Data Analysis Expressions). 

Quando você carrega dados no Power BI Desktop, ele tenta converter o tipo de dados da coluna de origem em um tipo de dados que dá melhor suporte a armazenamento, cálculos e visualização de dados mais eficientes. Por exemplo, se uma coluna de valores que você importa do Excel não tem nenhum valor fracionário, o Power BI Desktop converterá toda a coluna de dados para um tipo de dados de Número Inteiro, que é mais adequado para armazenar inteiros.

Isso é importante porque algumas funções DAX têm requisitos especiais de tipo de dados. Embora em muitos casos o DAX converta implicitamente um determinado tipo de dados para você, há alguns casos em que isso não ocorrerá.  Por exemplo, se uma função DAX requer um tipo de dados de Data e o tipo de dados para a coluna é Texto, a função DAX não funcionará corretamente.  Portanto, é importante e útil obter o tipo de dados correto para uma coluna. Conversões implícitas são descritas posteriormente neste artigo.

## <a name="determine-and-specify-a-columns-data-type"></a>Determinar e especificar o tipo de dados da coluna
Na área de trabalho do Power BI, você pode determinar e especificar o tipo de dados de uma coluna no Editor de Consultas, ou na Exibição de Dados ou de Relatório:

**Tipos de dados no Editor de consultas**

![](media/desktop-data-types/pbiddatatypesinqueryeditort.png)

**Tipos de dados na Exibição de dados ou de relatório**

![](media/desktop-data-types/pbiddatatypesindatareportview.png)

O drop-down Tipo de Dados no Editor de Consultas tem dois tipos de dados que não estão presentes atualmente na Exibição de Dados ou de Relatório: **Data/Hora/Fuso horário** e **Duração**. Quando uma coluna com esses tipos de dados é carregada no modelo e exibida na exibição de Dados ou de Relatório, uma coluna com um tipo de dado de Data/Hora/Fuso horário é convertida em um valor de Data/Hora, enquanto uma coluna com um tipo de dados de Duração é convertida em um Número Decimal.

### <a name="number-types"></a>Tipos de número
O Power BI Desktop dá suporte a três tipos de número:

**Número Decimal** – representa um número de ponto flutuante (oito bytes) de 64 bits. É o tipo de número mais comum e corresponde aos números como você normalmente os imagina.  Embora seja projetado para lidar com números com valores fracionários, ele também lida com números inteiros.  O tipo de Número Decimal pode lidar com valores negativos de -1,79E +308 a -2,23E -308, 0, e valores positivos de 2,23E -308 a 1,79E + 308. Por exemplo, números como 34, 34,01 e 34,000367063 são números decimais válidos. O maior valor que pode ser representado em um tipo de Número Decimal tem 15 dígitos.  O separador decimal pode ocorrer em qualquer lugar no número. O tipo de Número Decimal corresponde a como o Excel armazena seus números.

**Número Decimal Fixo** – tem um local para o separador decimal fixo. O separador decimal tem sempre quatro dígitos à direita e permite 19 dígitos de significância.  O maior valor que ele pode representar é 922.337.203.685.477,5807 (positivo ou negativo).  O tipo de Número Decimal Fixo é útil em casos em que o arredondamento pode introduzir erros.  Quando você trabalha com muitos números que têm valores fracionários pequenos eles podem, às vezes, se acumular e forçar um número a ficar ligeiramente fora do valor correto.  Como os valores após os quatro dígitos à direita do separador decimal são truncados, o tipo Decimal Fixo pode ajudá-lo a evitar esses tipos de erros.   Se você está familiarizado com o SQL Server, esse tipo de dados correspondente ao Decimal (19,4) do SQL Server, ou ao tipo de Dados de Moeda no Power Pivot. 

**Número Inteiro** – representa um valor inteiro (oito bytes) de 64 bits. Como é um número inteiro, ele não tem nenhum dígito à direita da casa decimal. Ele permite 19 dígitos; números inteiros positivos ou negativos entre -9.223.372.036.854.775.808 (-2^63) e 9.223.372.036.854.775.807 (2^63-1).  Ele pode representar o maior número possível dos diversos tipos de dados numéricos.  Assim como com o tipo Decimal Fixo, o tipo de Número Inteiro pode ser útil em casos nos quais você precisa controlar o arredondamento. 

### <a name="datetime-types"></a>Tipos de data/hora
O Power BI Desktop dá suporte a cinco tipos de dados de Data/Hora na Visualização da Consulta e três no modelo e Exibição de Relatório.   Tanto Data/Hora/Fuso horário quanto a Duração são convertidos durante o carregamento para o modelo.

**Data/Hora** – representa um valor de data e um valor temporal.  Nos bastidores, o valor de Data/Hora é armazenado como um Tipo de Número Decimal.  Então, na verdade, é possível converter entre os dois.   A parte de uma data referente à hora é armazenada como uma fração a múltiplos inteiros de 1/300 segundos (3,33 ms).  Há suporte para datas entre os anos de 1900 e 9999.

**Data** – representa apenas uma Data (sem parte referente à hora).  Quando convertido para o modelo, uma Data é o mesmo que um valor de Data/Hora com zero como o valor fracionário.

**Hora** – representa apenas a Hora (nenhuma parte referente à Data).  Quando convertido para o modelo, um valor de Hora é igual a um valor de Data/Hora sem dígitos à esquerda da casa decimal.

**Data/Hora/Fuso horário** – representa uma Data/Hora no formato UTC.  Atualmente, ele é convertido em Data/Hora quando é carregado no modelo.

**Duração** – representa um intervalo de tempo. Ele é convertido em um Tipo de Número Decimal quando é carregado no modelo.  Como um tipo de Número Decimal, ele pode ser adicionado ou subtraído de um campo de Data/Hora com resultados corretos.  Como um tipo de Número Decimal, você pode usá-lo facilmente em visualizações que mostram a magnitude.

### <a name="text-type"></a>Tipo de texto
**Texto** - uma cadeia de caracteres de dados de caractere Unicode. Pode ser composto de cadeias de caracteres, números ou datas representados em um formato de texto. O comprimento máximo da cadeia de caracteres é 268.435.456 caracteres Unicode (caracteres de 256 megabytes) ou 536.870.912 bytes.

### <a name="truefalse-type"></a>Tipo verdadeiro/falso
**Verdadeiro/Falso** – um valor Booliano de Verdadeiro ou Falso.

### <a name="blanksnulls-type"></a>Tipo em branco/nulos
**Em branco** - é um tipo de dados em DAX que representa e substitui nulos SQL. Você também pode gerar um elemento em branco usando a função [BLANK](http://msdn.microsoft.com/library/ee634820.aspx) e testar elementos em branco usando a função lógica [ISBLANK](https://msdn.microsoft.com/library/ee634204.aspx).

### <a name="table-data-type"></a>Tipo de dados de tabela
O DAX usa um tipo de dados de tabela em muitas funções, como agregações e cálculos de inteligência de dados temporais. Algumas funções exigem uma referência a uma tabela; outras funções retornam uma tabela que pode ser usada como entrada para outras funções. Em algumas funções que exigem uma tabela como entrada, você pode especificar uma expressão que é avaliada como uma tabela; para algumas funções, é necessária uma referência a uma tabela base. Para obter informações sobre os requisitos de funções específicas, consulte [Referência de função DAX](https://msdn.microsoft.com/library/ee634396.aspx).

## <a name="implicit-and-explicit-data-type-conversion-in-dax-formulas"></a>Conversão implícita e explícita de tipo de dados em fórmulas DAX
Cada função DAX tem requisitos específicos quanto aos tipos de dados que são usados como entradas e saídas. Por exemplo, algumas funções exigem inteiros para alguns argumentos e datas para outros; outras funções exigem texto ou tabelas.

Se os dados na coluna que você especifica como um argumento são incompatíveis com o tipo de dados exigido pela função, em muitos casos o DAX retornará um erro. No entanto, sempre que possível, o DAX tentará converter implicitamente os dados para o tipo de dados necessário. Por exemplo:

* Você pode digitar uma data como uma cadeia de caracteres e o DAX analisará a cadeia de caracteres e tentará transmiti-la como um dos formatos de data e hora do Windows.
* Você pode adicionar TRUE + 1 e obter o resultado 2, pois TRUE é implicitamente convertido para o número 1 e a operação 1+1 é executada.
* Se você adicionar valores em duas colunas e um valor for representado como texto ("12") e o outro como um número (12), o DAX converte implicitamente a cadeia de caracteres em um número e, em seguida, faz a adição para chegar a um resultado numérico. A expressão a seguir retorna 44: = "22" + 22.
* Se você tentar concatenar dois números, o Excel vai apresentá-los como cadeias de caracteres e, em seguida, concatenar. A expressão a seguir retorna "1234": = 12 & 34.

### <a name="table-of-implicit-data-conversions"></a>Tabela de conversões implícitas de dados
O tipo de conversão executada é determinado pelo operador, que transmite os valores que ele requer antes de executar a operação solicitada. Essas tabelas listam os operadores e indicam a conversão que é realizada em cada tipo de dados na coluna quando ele é emparelhado com o tipo de dados na linha que intersecciona essa coluna.

> [!NOTE]
>  Tipos de dados de texto não são incluídos nessas tabelas. Quando um número é representado em um formato de texto, em alguns casos o Power BI tentará determinar o tipo de número e representá-lo como um número.
> 
> 

**Adição (+)**

| Operador(+) | INTEGER | CURRENCY | REAL | Date/time |
| --- | --- | --- | --- | --- |
| INTEGER |INTEGER |CURRENCY |REAL |Date/time |
| CURRENCY |CURRENCY |CURRENCY |REAL |Date/time |
| REAL |REAL |REAL |REAL |Date/time |
| Date/time |Date/time |Date/time |Date/time |Date/time |

Por exemplo, se um número real é usado em uma operação de adição em combinação com dados de moedas, os dois valores são convertidos em REAL e o resultado é retornado como REAL.

**Subtração (-)**

Na tabela a seguir, o cabeçalho de linha é o minuendo (lado esquerdo) e o cabeçalho da coluna é o subtraendo (lado direito).

| Operador(-) | INTEGER | CURRENCY | REAL | Date/time |
| --- | --- | --- | --- | --- |
| INTEGER |INTEGER |CURRENCY |REAL |REAL |
| CURRENCY |CURRENCY |CURRENCY |REAL |REAL |
| REAL |REAL |REAL |REAL |REAL |
| Date/time |Date/time |Date/time |Date/time |Date/time |

Por exemplo, se uma data é usada em uma operação de subtração com qualquer outro tipo de dados, ambos os valores são convertidos em datas e o valor retornado também é uma data.

> [!NOTE]
>    Modelos de dados também são compatíveis com o operador unário, - (negativo), mas esse operador não altera o tipo de dados do operando.
> 
> 

**Multiplicação(*)**

| Operador(*) | INTEGER | CURRENCY | REAL | Date/time |
| --- | --- | --- | --- | --- |
| INTEGER |INTEGER |CURRENCY |REAL |INTEGER |
| CURRENCY |CURRENCY |REAL |CURRENCY |CURRENCY |
| REAL |REAL |CURRENCY |REAL |REAL |

Por exemplo, se um inteiro for combinado com um número real em uma operação de multiplicação, os dois números são convertidos em números reais, e o valor retornado também é REAL.

**Divisão (/)**

Na tabela a seguir, o cabeçalho da linha é o numerador e o cabeçalho da coluna é o denominador.

| Operador(/) (Linha/Coluna) | INTEGER | CURRENCY | REAL | Date/time |
| --- | --- | --- | --- | --- |
| INTEGER |REAL |CURRENCY |REAL |REAL |
| CURRENCY |CURRENCY |REAL |CURRENCY |REAL |
| REAL |REAL |REAL |REAL |REAL |
| Date/time |REAL |REAL |REAL |REAL |

Por exemplo, se um inteiro for combinado com um valor de moeda em uma operação de divisão, os dois valores são convertidos em números reais e o resultado também é um número real.

### <a name="comparison-operators"></a>Operadores de comparação
Em expressões de comparação, valores Boolianos são considerados maiores que valores de cadeia de caracteres, enquanto valores de cadeia de caracteres são considerados maiores que valores numéricos ou de data/hora; números e valores de data/hora são considerados como tendo a mesma classificação. Nenhuma conversão implícita é executada para valores de cadeia de caracteres ou Boolianos; BLANK ou um valor em branco é convertido em 0/""/false, dependendo do tipo de dados do outro valor comparado.

As seguintes expressões DAX ilustram esse comportamento:

=IF(FALSE()\>"true","Expression is true", "Expression is false"), retorna "Expression is true"

=IF("12"\>12,"Expression is true", "Expression is false"), retorna "Expression is true".

=IF("12"=12,"Expression is true", "Expression is false"), retorna "Expression is false"

As conversões são executadas implicitamente para tipos numéricos ou de data/hora, conforme descrito na tabela a seguir:

| Operador de Comparação | INTEGER | CURRENCY | REAL | Date/time |
| --- | --- | --- | --- | --- |
| INTEGER |INTEGER |CURRENCY |REAL |REAL |
| CURRENCY |CURRENCY |CURRENCY |REAL |REAL |
| REAL |REAL |REAL |REAL |REAL |
| Date/time |REAL |REAL |REAL |Date/time |

### <a name="handling-blanks-empty-strings-and-zero-values"></a>Tratamento de elementos em branco, cadeias de caracteres vazias e valores zero
No DAX, um valor nulo, valor em branco, célula vazia ou um valor ausente são todos representados pelo mesmo novo tipo de valor, um BLANK. Você também pode gerar elementos em branco usando a função BLANK, ou testar elementos em branco usando a função ISBLANK.

O modo como os elementos em branco são tratados em operações como adição ou concatenação depende da função individual. A tabela a seguir resume as diferenças entre as fórmulas DAX e do Microsoft Excel, da maneira que os elementos em branco são tratados.

| Expression | DAX | Excel |
| --- | --- | --- |
| BLANK + BLANK |BLANK |0(zero) |
| BLANK + 5 |5 |5 |
| BLANK * 5 |BLANK |0(zero) |
| 5/BLANK |Infinity |Error |
| 0/BLANK |NaN |Error |
| BLANK/BLANK |BLANK |Error |
| FALSE OR BLANK |FALSE |FALSE |
| FALSE AND BLANK |FALSE |FALSE |
| TRUE OR BLANK |TRUE |TRUE |
| TRUE AND BLANK |FALSE |TRUE |
| BLANK OR BLANK |BLANK |Error |
| BLANK AND BLANK |BLANK |Error |

