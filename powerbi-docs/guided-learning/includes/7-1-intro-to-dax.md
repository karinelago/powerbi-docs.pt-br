Bem-vindo à seção **Aprendizado Interativo** do Power BI, desenvolvida para apresentá-lo ao **DAX**.

**DAX** significa **Data Analysis Expressions** e é a linguagem de fórmula usada no Power BI (também usada pelo Power BI nos bastidores). O DAX também pode ser encontrado em outras ofertas da Microsoft, como o Power Pivot e SSAS de Tabela, mas esta coleção de tópicos do Aprendizado Interativo se concentra em como o DAX é usado – e pode ser usado por você – no Power BI.

## <a name="dax-and-this-guided-learning-video-series"></a>DAX e essa série de vídeos de Aprendizado Interativo
O objetivo desta seção **Aprendizado Interativo** é ensinar a você noções básicas e fundamentos do DAX – considerações sobre o DAX, como ele funciona e os recursos mais úteis, explicados (e aprendidos com muita experiência) por um renomado especialista no DAX, [Alberto Ferrari](http://www.sqlbi.com/learning-dax/?utm_source=powerbi&utm_medium=marketing&utm_campaign=after-summit).

![Retrato de Alberto Ferrari](media/7-1-intro-to-dax/intro_dax_6_alberto_ferrari.png)

Os vídeos apresentados nesta seção **Aprendizado Interativo** no **DAX** ensinam os fundamentos do DAX da perspectiva de como funciona a linguagem de fórmula DAX. Isso é útil ao criar fórmulas DAX do zero, mas também é muito útil para entender como o Power BI cria essas fórmulas DAX conforme você cria consultas no **Editor de Consultas**.

## <a name="in-this-video---introduction-to-dax"></a>Neste vídeo – Introdução ao DAX
Os conceitos do DAX são bem simples, mas o DAX é avançado. O DAX usa alguns conceitos e padrões de programação exclusivos, que podem dificultar seu pleno uso e entendimento. As maneiras tradicionais de aprendizado de linguagens podem não ser a melhor abordagem em relação ao DAX; portanto, o objetivo deste vídeo é ensinar conceitos e a teoria que o ajudarão adiante em seu trabalho com o Power BI.

O DAX é uma *linguagem funcional*, o que significa que o código executado completo está contido em uma função.

No DAX, as funções podem conter outras funções aninhadas, instruções condicionais e referências de valor. A execução no DAX começa na função ou parâmetro mais interno e trabalha para fora. No Power BI, as fórmulas DAX são escritas em uma única linha e, portanto, a formatação correta das funções é importante para facilitar a leitura.

O DAX foi projetado para funcionar com tabelas e, dessa forma, tem apenas dois tipos de dados primários: **Numéricos** e **Outros**. **Numéricos** podem incluir *inteiros*, *decimais* e *moeda*. **Outros** podem incluir *cadeias de caracteres* e *objetos binários*. Isso significa que, se você criar a função DAX para funcionar em um tipo de número, você poderá ter certeza de que ela funcionará em todos os outros dados Numéricos.

O DAX usa a sobrecarga de operador, o que significa que é possível combinar tipos de dados em seus cálculos e os resultados serão alterados com base no tipo de dados usado nas entradas. A conversão ocorre automaticamente. Isso indica que você não precisa conhecer os tipos de dados das colunas com as quais está trabalhando no Power BI, mas também significa que, às vezes, a conversão poderá ocorrer de maneiras inesperadas. É uma boa prática entender os dados que estão sendo usados para garantir que os operadores estão se comportando como previsto.

Em particular, há um tipo de dados com o qual você provavelmente trabalhará muito no Power BI: **DateTime**. **DateTime** é armazenado como um valor de ponto flutuante com partes de inteiro e decimal. DateTime pode ser usado com precisão para cálculos de qualquer período após 1º de março de 1900.

> Conteúdo do vídeo gentilmente cedido por [Alberto Ferrari, SQLBI](http://www.sqlbi.com/learning-dax/?utm_source=powerbi&utm_medium=marketing&utm_campaign=after-summit)
> 
> 

