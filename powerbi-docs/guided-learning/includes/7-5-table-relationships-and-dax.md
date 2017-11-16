O Power BI permite criar relações entre várias tabelas, incluindo tabelas provenientes de fontes de dados completamente diferentes. Você pode ver esses relacionamentos de qualquer modelo de dados na exibição **Relações** do Power BI Desktop.

![](media/7-5-table-relationships-and-dax/dax-relationships_1.png)

## <a name="dax-relational-functions"></a>Funções relacionais do DAX
O DAX tem **funções relacionais** que permitem interagir com tabelas que têm relações estabelecidas.

Você pode retornar o valor de uma coluna ou retornar todas as linhas em uma relação usando as funções DAX.

Por exemplo, a função **TABLE** segue as relações e retorna o valor de uma coluna, enquanto **RELATEDTABLE** segue as relações e retorna uma tabela inteira que é filtrada para incluir somente as linhas relacionadas.

![](media/7-5-table-relationships-and-dax/dax-relationships_2.png)

A função **RELATED** funciona em relações *muitos para um*, enquanto **RELATEDTABLE** é usada para relações *um para muitos*.

É possível usar funções relacionais para criar expressões que incluem valores em várias tabelas. O DAX retornará um resultado com essas funções, independentemente do tamanho da cadeia da relação.

> Conteúdo do vídeo gentilmente cedido por [Alberto Ferrari, SQLBI](http://www.sqlbi.com/learning-dax/?utm_source=powerbi&utm_medium=marketing&utm_campaign=after-summit)
> 
> 

