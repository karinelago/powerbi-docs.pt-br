---
title: "Dicas e truques para criar relatórios no Power BI Desktop"
description: "Dicas e truques para criar relatórios no Power BI Desktop"
services: powerbi
documentationcenter: 
author: davidiseminger
manager: kfile
backup: 
editor: 
tags: 
qualityfocus: identified
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 12/05/2017
ms.author: davidi
ms.openlocfilehash: 69e4d89f4118e6ea34ddbd4308965a90a662a970
ms.sourcegitcommit: 5e1f7d2673efe25c47b9b9f315011055bfe92c8f
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/09/2018
---
# <a name="tips-and-tricks-for-creating-reports-in-power-bi-desktop"></a>Dicas e truques para criar relatórios no Power BI Desktop
Para aproveitar ao máximo seus dados, às vezes você precisa de uma ajuda extra. Reunimos algumas dicas e truques que você pode usar ao criar relatórios no Microsoft Power BI Desktop *e* nas edições Pro-Plus do Microsoft Excel 2013 ou 2016 com o suplemento do Power Pivot habilitado e o Power Query instalado e habilitado. 

## <a name="learning-to-use-the-query-editor"></a>Aprendendo a usar o Editor de Consultas
Editor de Consultas no Power BI Desktop é semelhante à funcionalidade de suplemento do Power Query no Excel 2013. Embora haja vários artigos úteis no Suporte do Power BI, talvez você também queira ler a documentação do Power Query em support.office.com para começar.

Você pode obter mais informações no [Centro de Recursos do Power Query](https://support.office.com/article/Microsoft-Power-Query-for-Excel-Help-2b433a85-ddfb-420b-9cda-fe0e60b82a94).

É possível também exibir a [Referência de Fórmula](https://support.office.com/Article/Learn-about-Power-Query-formulas-6bc50988-022b-4799-a709-f8aafdee2b2f).

## <a name="data-types-in-query-editor"></a>Tipos de dados no Editor de Consultas
Ao usar o Editor de Consultas no Power BI Desktop para carregar dados, fazemos a melhor estimativa sobre a detecção do tipo de dados.  Ao usar fórmulas, às vezes, as configurações de tipo de dados nas colunas não são preservadas. Você deve verificar se o tipo de dados das colunas está correto depois de fazer as seguintes operações: carregar dados inicialmente na guia de consulta, Primeira Linha como Título, Adicionar coluna, Agrupar por, Mesclar, Acrescentar e antes de pressionar para carregar os dados pela primeira vez.

Um item importante a ser lembrado: itálico na grade de dados não significa que o tipo de dados está configurado corretamente, apenas que os dados não são considerados um Texto.

## <a name="reference-queries-in-the-query-editor"></a>Consultas de referência no Editor de Consultas
No navegador do Editor de Consultas, quando você clica no botão direito do mouse em uma das consultas, uma opção para “Referência” está disponível.  Isso é útil pelo seguinte motivo:

* Quando você usa arquivos como fonte de dados para uma consulta, o caminho absoluto para o arquivo é armazenado na consulta. Ao compartilhar ou mover o arquivo do Power BI Desktop ou a pasta de trabalho do Excel, você economizará tempo quando atualizar os caminhos atualizando-o apenas uma vez, em vez de atualizar os caminhos.

Por padrão, todas as consultas são carregadas em uma planilha do Excel ou no modelo de dados (ou em ambos). Algumas consultas são etapas intermediárias e não se destinam aos usuários finais.  Ao fazer referência a consultas como mencionado acima, isso costuma acontecer.  Você pode controlar o comportamento do carregamento da consulta clicando com o botão direito do mouse no navegador e alternando a opção “Habilitar Carregar”.  Quando “Habilitar Carregar” não tiver uma marca de seleção ao seu lado, a consulta ainda estará disponível na guia de consulta e você poderá usá-la com outras consultas.  É especialmente útil na combinação com transformações de Mesclagem, Acréscimo e Referência.  No entanto, já que os resultados da consulta não são carregados no modelo de dados, a consulta não agrupará a lista de campo dos relatórios ou o modelo de dados. 

## <a name="scatter-charts-need-a-point-identifier"></a>Gráficos de dispersão precisam de um identificador de ponto
Com um exemplo de uma tabela simples de Temperaturas e da Hora em que a leitura foi realizada. Se você plotar isso diretamente em um gráfico de dispersão, o Power BI Desktop agregará todos os valores em um único ponto. Para mostrar os pontos de dados individuais, você deverá adicionar um campo ao bucket Detalhes no contêiner do campo.   Uma maneira simples de fazer isso é na guia de consulta usando a opção “Adicionar coluna de índice” na faixa de opções “Adicionar Coluna”. 

## <a name="reference-lines-in-your-report"></a>Linhas de referência em seu relatório
Você pode usar uma coluna calculada para definir uma linha de referência.  Identifique a tabela e coluna nas quais você deseja criar uma linha de referência.  Selecione “Nova coluna” na faixa de opções e, na barra de fórmulas, digite a seguinte fórmula:

    Target Value = 100

Esta coluna calculada retornará o valor 100, independentemente de onde ele for usado.  A nova coluna aparecerá na Lista Campos.  Adicione a coluna calculada do Valor de Destino a um gráfico de linhas para mostrar como qualquer série se relaciona a essa linha de referência específica.  

## <a name="sort-by-another-column"></a>Classificar por outra coluna
Quando você usa um valor categórico (cadeia de caracteres) no Power BI Desktop para os eixos de gráfico ou em uma segmentação de dados ou filtro, a ordem padrão é alfabética. Se precisar substituir essa ordem, por exemplo, para elementos como dias da semana ou meses, você poderá especificar que o Power BI Desktop classifique por uma coluna diferente. Para saber mais, veja [Classificar por coluna no Power BI Desktop](desktop-sort-by-column.md).

## <a name="building-maps-more-easily-with-hints-to-bing"></a>Criando mapas mais facilmente com dicas para o Bing
O Power BI é integrado ao Bing para fornecer as coordenadas de mapa padrão (um processo chamado codificação geográfica) para facilitar a criação de mapas.  O Bing usa alguns algoritmos e dicas para tentar obter o local certo, mas é sua melhor estimativa.   Para aumentar a probabilidade de uma codificação geográfica correta, você pode usar as seguintes dicas:

Quando você cria um Mapa, geralmente você pretende plotar Países, Estados e Cidades.  Se você usar colunas de nome após a designação geográfica, isso ajudará o Bing a adivinhar o que você deseja exibir. Por exemplo, se você tiver um campo de nomes de Estados dos EUA, como “Califórnia” e “Washington”, o Bing poderá retornar o local de Washington, DC, em vez do Estado de Washington para a palavra “Washington”.  Nomear a coluna “Estado” melhorará a codificação geográfica.  O mesmo acontece com colunas nomeadas “País”, “Estado” e “Cidade”.   

Algumas designações são ambíguas quando consideradas no contexto de vários países/regiões.  Em alguns casos, o que um país/região considera um “estado” é tratado como uma “província” ou “condado” ou alguma outra designação.  Você pode aumentar a precisão da codificação geográfica criando colunas que acrescentam vários campos em conjunto e usá-las para plotar locais de dados.  Um exemplo seria transmitir “Wiltshire, Inglaterra” em vez de apenas “Wiltshire” para obter um resultado mais preciso de codificação geográfica. 

Sempre é possível fornecer locais específicos de latitude e longitude.  Quando você faz isso, também é necessário transmitir um campo Local; caso contrário, os dados serão agregados por padrão e o local da latitude e longitude talvez não corresponda ao esperado.

## <a name="categorizing-geographic-fields-to-hint-bings-geocoding"></a>Categorizando campos geográficos para fornecer dicas de codificação geográfica do Bing
No Power BI Desktop, é possível assegurar que os campos sejam codificados geograficamente de maneira correta definindo a Categoria de Dados nos campos de dados.   No Power BI Desktop, selecione a tabela desejada, vá para a faixa de opções Avançado e defina a Categoria de Dados como Endereço, Cidade, Continente, País/Região, País, Código Postal, Estado ou Província.  Essas categorias de dados ajudam o Bing a codificar a data corretamente. Para saber mais, veja [Categorização de dados no Power BI Desktop](desktop-data-categorization.md).

## <a name="better-geocoding-with-more-specific-locations"></a>Melhor codificação geográfica com locais mais específicos
Às vezes, até mesmo a definição das categorias de dados para o mapeamento é insuficiente.  Dentro da consulta, você pode criar um local mais específico como um endereço usando o Editor de Consultas no Power BI Desktop.  Use o recurso Adicionar Coluna para criar uma coluna personalizada.  Em seguida, crie o local desejado da seguinte maneira: 

    = [Field1] & " " & [Field2]

Em seguida, use este campo resultante nas visualizações de mapa. Isso é bastante útil para a criação de Endereços por meio dos campos Endereço de Entrega que são comuns em conjuntos de dados.  Vale lembrar que a concatenação funciona apenas com campos de texto.  Se necessário, converta o número da rua em um tipo de dados de texto antes de usá-lo para criar um endereço.

## <a name="histograms-in-the-query-stage"></a>Histogramas no estágio de consulta
Há várias maneiras de criar histogramas. Vamos começar com a mais simples e expandir para outras por meio dessa:

Histogramas Mais Simples - Determine qual consulta contém o campo no qual você deseja criar um histograma.  Use a opção “Referência” da consulta para criar uma nova consulta e nomeie-a como “FieldName Histogram”. Use a opção “Agrupar por” na faixa de opções “Transformar” e selecione a agregação “contagem de linhas”.  Verifique se o tipo de dados é um número para a coluna agregada resultante. Em seguida, visualize esses dados na página de relatórios.  Isso é rápido e fácil de criar, mas não funciona bem se você tiver muitos pontos de dados e não permitir a varredura em elementos visuais.

Definindo buckets para criar um histograma - Determine qual consulta contém o campo no qual você deseja criar um histograma.  Use a opção “Referência” da consulta para criar uma nova consulta e nomeie-a como “FieldName”.  Agora, defina os buckets com uma regra.  Use a opção Adicionar Coluna Personalizada na faixa de opções Adicionar Coluna e crie uma regra personalizada.  Uma regra da segmentação simples pode ter esta aparência:

    if([FieldName] \< 2) then "\<2 min" else
    if([FieldName] \< 5) then "\<5 min" else
    if([FieldName] \< 10) then "\<10 min" else
    if([FieldName] \< 30) then "\<30 min" else
    "longer")

Verifique se o tipo de dados é um número para a coluna agregada resultante. Agora você pode usar o grupo pela técnica descrita no Histograma Mais Simples para obter o histograma.  Essa opção trata de mais pontos de dados, mas ainda não ajuda com a varredura.

Definindo um histograma que dá suporte à varredura - Varredura é quando os elementos visuais são vinculados para que, quando um usuário selecionar um ponto de dados em um elemento visual, os outros elementos visuais na página do relatório realcem ou filtrem pontos de dados relacionados ao ponto de dados selecionado.  Como estamos manipulando dados no momento da consulta, precisaremos criar uma relação entre tabelas e garantir que saibamos qual item detalhado se relaciona ao bucket no histograma e vice-versa.

Inicie o processo usando a opção “Referência” na consulta que contém o campo no qual você deseja criar um histograma.  Nomeie a nova consulta “Buckets”.  Para este exemplo, vamos chamar a consulta original “Detalhes”.  Em seguida, remova todas as colunas, exceto a coluna que você usará como o bucket do histograma.  Agora, use o recurso “Remover Duplicatas” na consulta, no menu de atalho ao selecionar a coluna, para que os valores restantes sejam os valores exclusivos na coluna.   Se você tiver números decimais, primeiro você poderá usar a dica para definir buckets para criar um histograma para obter um conjunto gerenciável de buckets.  Agora, verifique os dados mostrados na visualização da consulta.  Se você vir valores nulos ou em branco, você precisará corrigi-los antes de criar uma relação.  Veja “Criando relações quando os dados contêm valores nulos ou em branco”.   Usar essa abordagem pode ser problemático devido à necessidade de classificação.  Para que os buckets sejam classificados corretamente, veja “Ordem de classificação: fazem com que as categorias apareçam na ordem desejada”.  

>[!NOTE]
>É útil pensar sobre a ordem de classificação antes de compilar visuais.   

A próxima etapa do processo é definir uma relação entre as consultas de “Buckets” e “Detalhes” na coluna de buckets.  No Power BI Desktop, clique em **Gerenciar Relações** na faixa de opções.  Crie uma relação em que Buckets está na tabela esquerda e Detalhes na tabela direita e selecione o campo que você está usando para o histograma. 

A última etapa é criar o histograma.  Arraste o campo Bucket da tabela “Buckets”.  Remova o campo padrão do gráfico de colunas resultante.  Agora, na tabela “Detalhes”, arraste o campo de histograma até o mesmo elemento visual.  No contêiner do campo, altere a agregação padrão para Contar.  O resultado é o histograma. Se você criar outro elemento visual como um treemap da tabela de Detalhes, selecione um ponto de dados no treemap para ver o histograma realçado e mostrá-lo para o ponto de dados selecionado em relação à tendência de todo o conjunto de dados.

## <a name="histograms"></a>Histogramas
É possível usar um campo calculado para definir um Histograma.  Identifique a tabela e coluna nas quais você deseja criar um histograma.  Na área de cálculo, digite a seguinte fórmula:

> Frequência:=COUNTROWS(\<Nome da Coluna\>)
> 
> 

Salve as alterações e retorne ao relatório.  Adicione o \<Nome da Coluna\> e a Frequência a uma tabela e converta-os em um gráfico de barras.  Certifique-se de que o \<Nome da Coluna\> está no eixo x e que o campo Frequência calculado está no eixo y.

## <a name="tips-and-tricks-for-creating-relationships"></a>Dicas e truques para criar relações
Geralmente, ao carregar conjuntos de dados detalhados de várias fontes, problemas como valores nulos, valores em branco ou valores duplicados impedem que você crie relações. 

Vejamos um exemplo: 

Se carregarmos conjuntos de dados de solicitações ativas de suporte ao cliente e outro conjunto de dados de itens de trabalho que têm os seguintes esquemas:

> CustomerInicdents: {IncidentID, CustomerName, IssueName, OpenedDate, Status} WorkItems: {WorkItemID, IncidentID, WorkItemName, OpenedDate, Status, CustomerName } 
> 
> 

Quando desejamos acompanhar todos os incidentes e itens de trabalho relacionados a um CustomerName específico, não podemos simplesmente criar uma relação entre esses dois conjuntos de dados.  Alguns WorkItems não podem estar relacionados a um CustomerName, portanto, esse campo estaria em branco ou seria NULL.  Pode haver vários registros em WorkItems e CustomerIncidents para um determinado CustomerName.  

### <a name="creating-relationships-when-the-data-has-null-or-blank-values"></a>Criando relações quando os dados contêm valores nulos ou em branco
Os conjuntos de dados geralmente contêm colunas com valores nulos ou em branco.  Isso pode causar problemas ao tentar usar relações.  Basicamente, você tem duas opções para solucionar os problemas.  É possível remover as linhas com valores nulos ou em branco.  Você pode fazer isso usando o recurso de filtro na guia de consulta ou, se estiver mesclando consultas, selecionar a opção “Mantenha somente as linhas correspondentes”. Como alternativa, você pode substituir os valores nulos ou em branco por valores que funcionam em relações, normalmente cadeias de caracteres como “NULL” e “(Blank)”.   Não há nenhuma abordagem certa aqui - filtrar linhas no estágio de consulta remove as linhas e pode afetar os cálculos e as estatísticas de resumo.  A última abordagem preserva essas linhas de dados, mas pode fazer com que linhas não relacionadas apareçam relacionadas no modelo, gerando erros de cálculo.  Se você adotar a última solução, lembre-se de usar filtros na Exibição/Gráfico quando apropriado para garantir que você esteja obtendo resultados precisos.  O mais importante é avaliar quais linhas são mantidas e removidas e entender o impacto geral na análise.  

### <a name="creating-relationships-when-the-data-has-duplicate-values"></a>Criando relações quando os dados têm valores duplicados
Geralmente, ao carregar conjuntos de dados detalhados de várias fontes, valores de dados duplicados impedem que você crie relações.  Você pode resolver isso criando uma tabela de dimensões com os valores exclusivos de ambos os conjuntos de dados. 

Vejamos um exemplo: 

Se carregarmos conjuntos de dados de solicitações ativas de suporte ao cliente e outro conjunto de dados de itens de trabalho que têm os seguintes esquemas:

> CustomerInicdents: {IncidentID, CustomerName, IssueName, OpenedDate, Status} WorkItems: {WorkItemID, IncidentID, WorkItemName, OpenedDate, Status, CustomerName } 
> 
> 

Quando desejamos acompanhar todos os incidentes e itens de trabalho relacionados a um CustomerName específico, não podemos simplesmente criar uma relação entre esses dois conjuntos de dados.  Alguns WorkItems não podem estar relacionados a um CustomerName, portanto, esse campo estaria em branco ou seria NULL.  Se você tiver todos os valores nulos ou em branco na tabela CustomerNames, talvez você ainda não consiga criar uma relação - veja Criando relações se meus dados contiverem valores nulos ou em branco.  Pode haver vários WorkItems e CustomerIncidents para um único CustomerName.  

Para criar uma relação, nesse caso, precisamos criar um conjunto de dados lógico de todos os CustomerNames entre os dois conjuntos de dados.  Na guia Consulta, você pode usar a seguinte sequência para criar o conjunto de dados lógico:

1. Duplique duas consultas, nomeando a primeira **Temp** e a segunda **CustomerNames**.
2. Em cada consulta, remova todas as colunas, *exceto* a coluna CustomerName
3. Em cada consulta, use  **Remover Duplicar**.
4. Na consulta **CustomerNames** , selecione a opção **Acrescentar** na faixa de opções e, em seguida, selecione a consulta **Temp**.
5. Na consulta **CustomerNames** , selecione **Remover Duplicatas**.

Agora você tem uma tabela de dimensões que pode ser usada para relacionar CustomerIndicents e WorkItems que contém todos os valores de cada um.  

## <a name="patterns-to-jump-start-your-use-of-the-query-editor"></a>Padrões para acelerar seu uso do Editor de Consultas
O Editor de Consultas é bastante eficiente em como ele pode manipular dados para formatar e limpá-los para que estejam prontos para serem visualizados ou modelados. Existem alguns padrões que você deve conhecer.

### <a name="temporary-columns-can-be-deleted-after-computing-a-result"></a>As colunas temporárias podem ser excluídas após o cálculo de um resultado
Geralmente, você precisa criar um cálculo que transforma dados de várias colunas em única nova coluna.  Isso pode ser complexo.  Uma forma fácil de resolver esse problema é decompor a operação em etapas.  Comece duplicando as colunas iniciais. Em seguida, crie nas etapas colunas temporárias. Em seguida, crie uma coluna para o resultado final.  Depois, você pode excluir as colunas temporárias para que o conjunto de dados final não seja agrupado. Isso é possível porque a guia de consulta executa as etapas na ordem. 

### <a name="duplicate-or-reference-queries-followed-by-merge-to-original-query"></a>Duplicar ou referenciar consultas seguidas de mesclagem na consulta original
Às vezes é bastante útil computar estatísticas de resumo para um conjunto de dados.  A forma mais fácil de fazer isso é duplicar ou fazer referência à consulta na guia de consulta. Em seguida, use **Agrupar por** para calcular as estatísticas de resumo.  As estatísticas de resumo ajudam você a normalizar os dados nos dados originais para que eles sejam mais comparáveis do que em .  Isso é especialmente útil para comparar valores individuais com o todo.  Para fazer isso, vá para a consulta original e selecione a opção de mesclagem.  Em seguida, mescle os dados da consulta de estatísticas de resumo que corresponde aos identificadores apropriados.  Agora você está pronto para normalizar os dados conforme necessário para a sua análise.

## <a name="using-dax-for-the-first-time"></a>Usando o DAX pela primeira vez
DAX é a linguagem de fórmula de cálculo no Power BI Desktop.  Ele é otimizado para a análise de BI.  É um pouco diferente do que você talvez esteja familiarizado se você usou apenas uma linguagem de consulta como SQL. Há muito bons recursos online e na literatura para aprender sobre o DAX. 

[Início rápido: aprenda noções básicas do DAX no Power BI Desktop](desktop-quickstart-learn-dax-basics.md)

[Referência do DAX (Data Analysis Expressions)](https://msdn.microsoft.com/library/gg413422.aspx)

[Central de recursos do DAX](http://social.technet.microsoft.com/wiki/contents/articles/1088.dax-resource-center.aspx)

