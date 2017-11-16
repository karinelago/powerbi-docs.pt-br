Com o DAX, há muitas funções disponíveis para formatar, formar ou, de outro modo, analisar seus dados. Essas funções podem ser agrupadas em algumas categorias:

* Funções de **agregação**
* Funções de **contagem**
* Funções **lógicas**
* Funções de **informações**
* Funções de **texto**
* Funções de **data**

De forma semelhante ao Excel, quando você começa a digitar a fórmula na **Barra de Fórmulas** do Power BI Desktop, é exibida uma lista das funções disponíveis para ajudá-lo a determinar qual função disponível você deseja selecionar. Além disso, com o uso das teclas de direção **para cima** e **para baixo** no teclado, você pode realçar qualquer uma das funções disponíveis e uma breve descrição será exibida.

O Power BI exibe as funções que correspondem às letras digitadas até o momento; portanto, se você digitar *S*, apenas as funções que começam com *S* aparecerão na lista. Se você digitar *Su*, apenas as funções que *contêm* a sequência de letras *Su* em seus nomes aparecerão na lista (eles não precisam começar com *Su*, apenas precisam conter essa sequência de letras).

![](media/7-3-dax-functions/dax-functions_1.png)

É fácil testar o DAX dessa forma e encontrar cada uma das várias funções DAX disponíveis no Power BI. Basta começar a digitar e o Power BI o ajuda neste processo.

Agora que sabemos como executar essa fórmula DAX, vamos dar uma olhada em cada uma dessas categorias de função por vez.

## <a name="aggregation-functions"></a>Funções de agregação
O DAX tem diversas funções de **agregação**, incluindo as seguintes funções mais usadas:

* SUM
* AVERAGE
* MIN
* MAX
* SUMX (e outras funções *X*)

Essas funções funcionam somente em colunas numéricas e, geralmente, podem agregar apenas uma coluna por vez.

No entanto, as funções de agregação especiais que terminam em **X**, como **SUMX**, podem funcionar em várias colunas. Essas funções iteram pela tabela e avaliam a expressão para cada linha.

## <a name="counting-functions"></a>Funções de contagem
As funções de **contagem** mais usadas no DAX incluem as seguintes:

* COUNT
* COUNTA
* COUNTBLANK
* COUNTROWS
* DISTINCTCOUNT

Essas funções contam elementos diferentes, como valores distintos, valores não vazios e linhas de tabela.

## <a name="logical-functions"></a>Funções lógicas
A coleção de funções **lógicas** no DAX inclui:

* AND
* OR
* NOT
* IF
* IFERROR

Essas funções especiais também podem ser expressas com *operadores*. Por exemplo, **AND** pode ser digitado como (substituído por) **&&** na fórmula DAX.

Você pode usar operadores (como **&&**) quando precisar de mais de duas condições na fórmula; caso contrário, é uma prática recomendada usar o próprio nome da função (como **AND**) para facilitar a leitura do código DAX.

## <a name="information-functions"></a>Funções de informações
As funções de **informações** no DAX incluem:

* ISBLANK
* ISNUMBER
* ISTEXT
* ISNONTEXT
* ISERROR

Embora essas funções possam ser circunstancialmente úteis, é importante saber o tipo de dados das colunas com antecedência, em vez de depender dessas funções para fornecer o tipo de dados.

O DAX usa as funções **MAX** e **MIN** tanto para *agregar* quanto para *comparar* valores.

## <a name="text-functions"></a>Funções de texto
As funções de **texto** no DAX incluem as seguintes:

* CONCATENATE
* REPLACE
* SEARCH
* UPPER
* FIXED

Essas funções de **texto** funcionam de forma muito semelhante às funções homônimas do Excel; portanto, se você estiver familiarizado com a maneira como o Excel lida com as funções de texto, você já estará um passo à frente. Caso contrário, você sempre poderá testar essas funções no Power BI e saber mais sobre como elas se comportam.

## <a name="date-functions"></a>Funções de data
O DAX inclui as seguintes funções **Date**:

* DATE
* HOUR
* NOW
* EOMONTH
* WEEKDAY

Embora essas funções sejam úteis para calcular e extrair informações de valores de *data*, elas não se aplicam à inteligência de dados temporais, que usa uma tabela de data.

> Conteúdo do vídeo gentilmente cedido por [Alberto Ferrari, SQLBI](http://www.sqlbi.com/learning-dax/?utm_source=powerbi&utm_medium=marketing&utm_campaign=after-summit)
> 
> 

