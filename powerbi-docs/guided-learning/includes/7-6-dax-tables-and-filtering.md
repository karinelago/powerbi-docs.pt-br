Uma diferença significativa entre a linguagem de fórmula do **DAX** e do Excel é que o DAX permite passar *tabelas inteiras* entre expressões, em vez de serem restritas a um único valor. Um efeito poderoso é que o DAX permite filtrar tabelas em suas expressões e, em seguida, trabalhar com o conjunto filtrado de valores.

![](media/7-6-dax-tables-and-filtering/dax-tables-filtering_1.png)

Com o DAX, você pode criar tabelas calculadas totalmente novas e, em seguida, tratá-las como qualquer outra tabela – incluindo a criação de relações entre elas e outras tabelas em seu modelo de dados.

## <a name="dax-table-functions"></a>Funções de tabela do DAX
O DAX tem um conjunto avançado de funções de **tabela**, incluindo as seguintes:

* FILTER
* ALL
* VALUES
* DISTINCT
* RELATEDTABLE

Essas funções retornam uma tabela completa, em vez de um valor. Normalmente, você usará os resultados de uma função de **tabela** em uma análise detalhada como parte de uma expressão maior, em vez de usar a tabela retornada como um valor final. É importante observar que, quando você usa uma função de tabela, os resultados herdam as relações de suas colunas.

É possível combinar funções de tabela na expressão, desde que cada função use e retorne uma tabela. Por exemplo, considere a seguinte expressão DAX:

    FILTER (ALL (Table), Condition)

Essa expressão colocaria um filtro sobre a totalidade da *Tabela*, ignorando todo o conteúdo atual do filtro.

A função DISTINCT retorna os valores distintos de uma coluna que também são visíveis no contexto atual. Portanto, para usar o exemplo de expressão DAX acima, o uso **ALL** nessa expressão ignorará os filtros, enquanto a substituição de **ALL** por **DISTINCT** respeitará esses filtros.

## <a name="counting-values-with-dax"></a>Valores de contagem com o DAX
Uma pergunta comum que os construtores de relatórios do Power BI querem responder é a seguinte:

* Quantos valores existem para esta coluna?

Essa pode ser uma pergunta simples de responder com uma tabela exibida na frente, mas o DAX aborda isso de maneira diferente, principalmente quando há uma relação entre as tabelas.

Por exemplo, o Power BI e o DAX incluem valores que não estão indexados de forma cruzada corretamente. Se a relação de entrada for desfeita, o DAX adicionará uma nova linha à tabela relacionada que contém espaços em branco em todos os campos e vinculará essa nova linha à linha não indexada para garantir a integridade referencial. Se sua função incluir linhas em branco, como geralmente é o caso quando se usa **ALL**, essas linhas em branco serão incluídas no número de valores retornados para essa coluna.

Também é possível criar tabelas calculadas inteiras usando funções DAX. As tabelas calculadas criadas com o DAX necessitam de uma função **NAME** e **TABLE**. Tabelas calculadas podem ser usadas como quaisquer outras tabelas, incluindo a definição de relações.

> Conteúdo do vídeo gentilmente cedido por [Alberto Ferrari, SQLBI](http://www.sqlbi.com/learning-dax/?utm_source=powerbi&utm_medium=marketing&utm_campaign=after-summit)
> 
> 

