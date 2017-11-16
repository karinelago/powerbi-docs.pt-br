Há dois cálculos principais que podem ser criados usando o DAX:

* **colunas calculadas**
* **medidas calculadas**

Antes de nos aprofundarmos na criação deles, é bom ter uma compreensão profunda sobre a sintaxe do DAX em tabelas e colunas, que você usará ao criar **colunas calculadas** ou **medidas calculadas**.

## <a name="dax-table-and-column-name-syntax"></a>Sintaxe de nome de tabela e coluna do DAX
Se você estiver criando uma nova coluna ou medida, é importante saber o formato geral dos nomes de tabela no DAX:

    'Table Name'[ColumnName]

Se houver espaços no nome da tabela (conforme mostrado acima), as aspas simples em torno do nome da tabela serão obrigatórias. Se o nome da tabela não tiver espaços, as aspas simples poderão ser omitidas para que a sintaxe seja parecida com esta:

    TableName[ColumnName]

A seguinte imagem mostra uma fórmula DAX que está sendo criada no Power BI:

![](media/7-2-dax-calculation-types/dax-calc-types_1.png)

Você também pode omitir por completo o nome da tabela e usar apenas o nome da coluna, mas essa é uma prática inadequada para a escrita de funções bem-definidas (e assim, para limpar o código do DAX). Nomes de coluna devem sempre incluir os colchetes.

É uma prática recomendada *sempre* fazer o seguinte:

* Sem espaços em nomes de tabela
* Sempre inclua o nome da tabela nas fórmulas (não o omita, mesmo que isso seja permitido pelo DAX)

## <a name="creating-calculated-columns"></a>Criando colunas calculadas
**Colunas calculadas** serão úteis quando você desejar segmentar ou filtrar o valor ou se quiser um cálculo para cada linha na tabela.

Você pode criar colunas calculadas no Power BI Desktop selecionando **Nova Coluna** na guia **Modelagem**. É melhor estar na exibição **Dados** (em vez da exibição **Relatório** ou **Relações**), já que você pode ver a nova coluna criada e a **Barra de Fórmulas** é populada e está pronta para a fórmula DAX.

![](media/7-2-dax-calculation-types/dax-calc-types_2a.png)

Depois de selecionar o botão **Nova Coluna**, a **Barra de Fórmulas** será populada com um nome de coluna básico (que você muda de acordo com a fórmula, é claro) e o operador **=** e a nova coluna aparecerá na grade de dados, como mostrado na imagem a seguir.

![](media/7-2-dax-calculation-types/dax-calc-types_3.png)

Os elementos necessários para uma coluna calculada são os seguintes:

* um novo nome de coluna
* pelo menos uma função ou expressão

Se você fizer referência a uma tabela ou coluna na fórmula da coluna calculada, não será necessário especificar uma linha na tabela – para cada cálculo, o Power BI calculará a coluna da linha atual.

## <a name="creating-calculated-measures"></a>Criando medidas calculadas
Use uma **medida calculada** quando estiver calculando percentuais ou taxas ou se precisar de agregações complexas. Para criar uma medida usando uma fórmula DAX, selecione o botão **Nova Medida** na guia **Modelagem**. Mais uma vez, é melhor estar na exibição **Dados** do Power BI Desktop, já que ela mostra a **Barra de Fórmula** e facilita o trabalho de escrever sua fórmula DAX.

![](media/7-2-dax-calculation-types/dax-calc-types_4.png)

Com **medidas**, você verá um novo ícone de medidas aparecer no painel **Campos** com o nome da medida. A **Barra de Fórmulas** é populada novamente com o nome da fórmula DAX (dessa vez, com a medida).

![](media/7-2-dax-calculation-types/dax-calc-types_5.png)

Os elementos necessários para uma medida calculada são os mesmos usados para uma coluna calculada:

* um novo nome de medida
* pelo menos uma função ou expressão

> Conteúdo do vídeo gentilmente cedido por [Alberto Ferrari, SQLBI](http://www.sqlbi.com/learning-dax/?utm_source=powerbi&utm_medium=marketing&utm_campaign=after-summit)
> 
> 

