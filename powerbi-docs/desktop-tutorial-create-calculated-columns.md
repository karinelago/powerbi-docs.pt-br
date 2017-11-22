---
title: 'Tutorial: criar colunas calculadas no Power BI Desktop'
description: 'Tutorial: criar colunas calculadas no Power BI Desktop'
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
ms.openlocfilehash: 7e959054300dafcab5f38bfce121fe0ac91dca06
ms.sourcegitcommit: f2b38777ca74c28f81b25e2f739e4835a0ffa75d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/17/2017
---
# <a name="tutorial-create-calculated-columns-in-power-bi-desktop"></a>Tutorial: criar colunas calculadas no Power BI Desktop
Às vezes, os dados que você está analisando simplesmente não contêm um campo específico, do qual você precisa para obter os resultados que procura. É aqui que entram as colunas calculadas. As colunas calculadas usam fórmulas DAX (Data Analysis Expressions) para definir os valores de uma coluna. Esses valores podem ser praticamente qualquer coisa, seja reunindo valores de texto de duas colunas diferentes em outro lugar no modelo ou calculando um valor numérico por meio de outros valores. Por exemplo, digamos que seus dados têm colunas Cidade e Estado (como campos na lista Campos), mas você deseja um único campo Localização que englobe ambas como um único valor, como “Miami, FL”. É exatamente para isso que as colunas calculadas servem.

As colunas calculadas são semelhantes a medidas no sentido que ambas se baseiam em uma fórmula DAX, mas diferem no modo como são usadas. Medidas são geralmente usadas na área Valores de uma visualização para calcular resultados com base em outros campos que você tem em uma linha de uma tabela, ou em uma área de Eixo, Legenda ou Grupo de uma visualização. Por outro lado, as colunas calculadas são usadas quando você quer os resultados da coluna contidos em uma determinada linha na tabela, ou na área Eixo, Legenda ou Grupo.

Este tutorial serve como guia para que você compreenda as colunas calculadas e crie-as você mesmo no Power BI Desktop. Ele destina-se aos usuários do Power BI já familiarizados com o uso do Power BI Desktop para criar modelos mais avançados. Você já deve estar familiarizado com o uso da Consulta para importar dados, trabalhar com múltiplas tabelas relacionadas e adicionar campos à tela Relatório. Se ainda não estiver familiarizado com o Power BI Desktop, não deixe de conferir a [Introdução ao Power BI Desktop](desktop-getting-started.md).

Para concluir as etapas neste tutorial, você precisará baixar o arquivo [Exemplo de Vendas da Contoso para o Power BI Desktop](http://download.microsoft.com/download/4/6/A/46AB5E74-50F6-4761-8EDB-5AE077FD603C/Contoso%20Sales%20Sample%20for%20Power%20BI%20Desktop.zip). Trata-se do mesmo arquivo de exemplo usado no tutorial [Criar suas próprias medidas no Power BI Desktop](desktop-tutorial-create-measures.md). Ele já inclui dados de vendas da empresa fictícia, Contoso, Inc. Já que os dados no arquivo foram importados de um banco de dados, você não conseguirá conectar-se à fonte de dados nem exibi-los no Editor de Consulta. Quando você tiver o arquivo em seu próprio computador, vá em frente e abra-o no Power BI Desktop.

## <a name="lets-create-a-calculated-column"></a>Vamos criar uma coluna calculada
Vamos dizer que desejamos exibir categorias de produtos juntamente com subcategorias de produtos em um único valor em linhas, como Telefones celulares – Acessórios, Telefones celulares – Smartphones e PDAs, etc. Na Exibição de Relatório ou Exibição de Dados (estamos usando a Exibição de Relatório aqui), se observarmos nossas tabelas de produtos na lista Campos, veremos que não há nenhum campo que fornece o que queremos. Temos, no entanto, um campo ProductCategory e um campo ProductSubcategory, cada um deles em sua própria tabela.

 ![](media/desktop-tutorial-create-calculated-columns/calccol_fileds_nonewcol.png)

Criaremos uma nova coluna calculada, para combinar os valores dessas duas colunas em novos valores para nossa nova coluna. O interessante disso é que precisamos combinar dados de duas tabelas diferentes em uma única coluna. Como nós vamos usar DAX para criar nossa nova coluna, podemos aproveitar todo o potencial do modelo que já temos, incluindo as relações entre tabelas diferentes já existentes.

### <a name="to-create-a-productfullcategory-column"></a>Para criar uma coluna ProductFullCategory
1.  Clique com o botão direito do mouse na tabela **ProductSubcategory** na lista Campos ou clique na seta para baixo nessa mesma tabela; em seguida, clique em **Nova Coluna**. Isso vai assegurar que a nossa nova coluna seja adicionada à tabela ProductSubcategory.
    
    ![](media/desktop-tutorial-create-calculated-columns/calccol_fileds_newcolumn.png)
    
    A barra de fórmulas aparece na parte superior da tela Relatório ou grade de Dados. É ali que podemos renomear nossa coluna e inserir uma fórmula DAX.
    
    ![](media/desktop-tutorial-create-calculated-columns/calccol_fileds_newcolumnformula.png)
    
    Por padrão, uma nova coluna calculada é nomeada simplesmente como Coluna. Se não a renomearmos, a próxima coluna que criamos será nomeada Coluna 2, Coluna 3 e assim por diante. Queremos que nossas colunas sejam identificadas com mais facilidade, então vamos dar um novo nome a nossa nova coluna.
    
2.  Como o nome da **Coluna** já está realçado na barra de fórmulas, basta digitar **ProductFullCategory**.
    
    Agora, podemos começar a inserir nossa fórmula. Queremos que os valores na coluna nova comecem com o nome ProductCategory, da tabela ProductCategory. Como esta coluna está em uma tabela diferente, mas relacionada, vamos usar a função [RELATED](https://msdn.microsoft.com/library/ee634202.aspx) para nos ajudar a obtê-la.
    
3.  Após o sinal de igual, digite um **R**. Você verá uma lista suspensa de sugestões aparecer com todas as funções DAX começando pela letra R. Quanto mais digitamos, mais a lista de sugestões é dimensionada aproximando-se da função que precisamos. Você verá uma descrição da função ao lado desta. Selecione **RELATED** rolando para baixo e depois pressionando Enter.
    
    ![](media/desktop-tutorial-create-calculated-columns/calccol_fileds_pfc_1.png)
    
    Um parêntese de abertura é exibido junto com outra lista de sugestões de todas as colunas disponíveis que podemos passar para a função RELATED. Também são exibidos uma descrição e detalhes sobre quais parâmetros são esperados.
    
    ![](media/desktop-tutorial-create-calculated-columns/calccol_fileds_pfc_2.png)
    
    Uma expressão sempre aparece entre parênteses de abertura e de fechamento. Nesse caso, nossa expressão vai conter um único argumento passado para a função RELATED: uma coluna relacionada, da qual retornar valores. A lista de colunas é reduzida automaticamente para exibir somente as colunas relacionadas. Nesse caso, queremos a coluna ProductCategory na tabela ProductCategory.
    
    Selecione **ProductCategory[ProductCategory]**, e, em seguida, digite um parêntese de fechamento.
    
    > [!TIP]
    > Erros de sintaxe são causados frequentemente por um parêntese de fechamento ausente ou mal posicionado. Mas, muitas vezes, o Power BI Desktop o adicionará se você esquecer.
    > 
    > 
    
    ![](media/desktop-tutorial-create-calculated-columns/calccol_fileds_pfc_3.png)
    
4. Queremos adicionar um símbolo de hífen para separar cada valor, portanto, após o parêntese de fechamento da primeira expressão, digite um espaço, E comercial (&), aspas, espaço, hífen (-), outro espaço, aspas de fechamento e, em seguida, outro E comercial. Sua fórmula agora deve ter essa aparência:
    
    **ProductFullCategory = RELATED(ProductCategory[ProductCategory]) & " - " &**
    
    > [!TIP]
    > Clique na divisa inferior no lado direito da barra de fórmulas para expandir o editor de fórmulas. Clique em Alt + Enter para mover uma linha para baixo e pressione Tab para mudar a posição das coisas.
    > 
    > 
    
5.  Por fim, insira outro colchete de abertura e selecione a coluna **[ProductSubcategory]** para concluir a fórmula. Sua fórmula deve ter essa aparência:
    
    ![](media/desktop-tutorial-create-calculated-columns/calccol_fileds_pfc_5.png)
    
    Você observará que não usamos outra função RELATED na segunda expressão, chamando a coluna ProductSubcategory. Isso ocorre porque essa coluna já está na mesma tabela em que estamos criando nossa nova coluna. Podemos inserir [ProductCategory] com o nome da tabela (totalmente qualificado) ou sem (não qualificado).
    
6.  Complete a fórmula, pressionando Enter ou clicando na marca de confirmação na barra de fórmulas. A fórmula é validada e adicionada à lista de campos na tabela **ProductSubcategory** .
    
    ![](media/desktop-tutorial-create-calculated-columns/calccol_fileds_pfc_6.png)
    
    Você observará que colunas calculadas recebem um ícone especial na lista de campos. Isso mostra que elas contêm uma fórmula. Elas aparecerão assim somente no Power BI Desktop. No serviço PowerBI.com (seu site do Power BI), não é possível alterar uma fórmula; portanto, um campo de coluna calculada não tem um ícone.
    
## <a name="lets-add-our-new-column-to-a-report"></a>Vamos adicionar nossa nova coluna a um relatório
Agora podemos adicionar nossa nova coluna ProductFullCategory à tela de relatório. Vamos examinar SalesAmount por ProductFullCategory.

Arraste a coluna **ProductFullCategory** da tabela **ProductSubcategory** até a tela Relatório e, em seguida, arraste o campo **SalesAmount** da tabela **Sales** até o gráfico.

![](media/desktop-tutorial-create-calculated-columns/calccol_fileds_report_1.png)

## <a name="lets-create-another"></a>Vamos criar mais uma
Agora que você sabe como criar uma coluna calculada, vamos criar outra.

O modelo “Exemplo de Vendas da Contoso para o Power BI Designer” contém dados de vendas tanto para repositórios ativos quanto inativos. Queremos garantir que dados exibidos para repositórios inativos sejam identificados como tal. Por isso, desejamos um campo chamado Active StoreName. Para fazer isso, criaremos outra coluna. Nesse caso, quando um repositório estiver inativo, queremos que nossa nova coluna Active StoreName (como um campo) mostre o nome do repositório como "Inactive", mas mostre o verdadeiro nome do repositório quando este for um repositório ativo.

Felizmente, nossa tabela Stores tem uma coluna denominada Status, com um valor “On” para repositórios ativos e “Off” para repositórios inativos. Podemos testar valores para cada linha na coluna Status, para criar novos valores em nossa nova coluna.

### <a name="to-create-an-active-storename-column"></a>Para criar uma coluna Active StoreName
1.  Crie uma nova coluna calculada chamada **Active StoreName** na tabela **Stores**.
    
    Para esta coluna, nossa fórmula DAX verificará o status de cada repositório. Se um status de um repositório for “On”, a nossa fórmula retornará o nome do repositório. Se o status for “Off”, o repositório terá o nome "Inactive". Para fazer isso, vamos usar a função lógica [IF](https://msdn.microsoft.com/library/ee634824.aspx) para testar o status das lojas e retornar um valor específico se o resultado for “true” ou “false”.
    
2.  Comece digitando **IF**. A lista de sugestões mostrará o que podemos adicionar. Selecione **IF**.
    
    ![](media/desktop-tutorial-create-calculated-columns/calccol_activestore_1.png)
    
    O primeiro argumento para IF é um teste lógico. Queremos testar se um repositório tem ou não um status "On".
    
3.  Digite um colchete de abertura **[**, que nos permite selecionar colunas na tabela Stores. Selecione **[Status]**.
    
    ![](media/desktop-tutorial-create-calculated-columns/calccol_activestore_2.png)
    
4.  Logo após **[Status]**, digite **="On"** e, em seguida, digite uma vírgula (**,**) para inserir o segundo argumento. A dica de contexto sugere que precisamos adicionar o valor quando o resultado é “true”.
    
    ![](media/desktop-tutorial-create-calculated-columns/calccol_activestore_3.png)
    
5.  Se o status do repositório for “On”, queremos que o nome desse repositório seja exibido. Digite um colchete de abertura **[** e selecione a coluna **[StoreName]** , então digite outra vírgula para que possamos inserir nosso terceiro argumento.
    
    ![](media/desktop-tutorial-create-calculated-columns/calccol_activestore_step5.png)
    
6.  Precisamos adicionar um valor quando o resultado for “false”; neste caso, desejamos que o valor seja **“Inactive”**.
    
    ![](media/desktop-tutorial-create-calculated-columns/calccol_activestore_step6.png)
    
7.  Complete a fórmula, pressionando Enter ou clicando na marca de confirmação na barra de fórmulas. A fórmula é validada e adicionada à lista de campos na tabela Stores.
    
    Assim como ocorre com qualquer outro campo, podemos usar nossa nova coluna Active StoreName em visualizações. Neste gráfico, repositórios com um status “On” são exibidos individualmente por nome, mas repositórios com um status “Off” são agrupados juntos e mostrados como “Inactive”. 
    
    ![](media/desktop-tutorial-create-calculated-columns/calccol_activestore_viz.png)
    
## <a name="what-weve-learned"></a>O que aprendemos
Colunas calculadas podem enriquecer nossos dados, facilitando a compreensão das informações. Aprendemos como criar colunas calculadas usando a barra de fórmulas, como usar a lista de sugestões e o melhor modo de nomear nossas novas colunas.

## <a name="next-steps"></a>Próximas etapas
Se desejar se aprofundar nas fórmulas DAX e criar colunas calculadas com fórmulas DAX mais avançadas, veja [Noções básicas do DAX no Power BI Desktop](desktop-quickstart-learn-dax-basics.md). Este artigo enfoca os conceitos fundamentais no DAX, como sintaxe, funções e uma compreensão mais abrangente sobre o contexto.

Certifique-se de adicionar a [Referência ao DAX (Expressões de Análise de Dados)](https://msdn.microsoft.com/library/gg413422.aspx) aos favoritos. É nela que você encontrará informações detalhadas sobre a sintaxe do DAX, operadores, além de mais de 200 funções DAX.

