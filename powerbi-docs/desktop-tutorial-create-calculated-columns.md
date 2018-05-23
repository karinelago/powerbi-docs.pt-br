---
title: 'Tutorial: criar colunas calculadas no Power BI Desktop'
description: 'Tutorial: criar colunas calculadas no Power BI Desktop'
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: tutorial
ms.date: 05/21/2018
ms.author: davidi
LocalizationGroup: Learn more
ms.openlocfilehash: d8d11d3f8cf61d01fb3c81519a2b11e729b8671c
ms.sourcegitcommit: e6db826c2f43a69e4c63d5f4920baa8f66bc41be
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/23/2018
---
# <a name="tutorial-create-calculated-columns-in-power-bi-desktop"></a>Tutorial: criar colunas calculadas no Power BI Desktop

Às vezes, os dados que você está analisando não contêm um campo específico, do qual você precisa para obter os resultados que procura. É aqui que entram as *colunas calculadas*. As colunas calculadas usam fórmulas DAX (Data Analysis Expressions) para definir os valores de uma coluna, qualquer coisa desde reunir valores de texto de duas colunas diferentes até calcular um valor numérico de outros valores. Por exemplo, digamos que seus dados tenham os campos **Cidade** e **Estado**, mas você queira um único campo **Local** que tenha ambos, como "Miami, FL". É exatamente para isso que as colunas calculadas servem.

As colunas calculadas são semelhantes a [medidas](desktop-tutorial-create-measures.md), no sentido que ambas se baseiam em fórmulas DAX, mas diferem no modo como são usadas. Muitas vezes você usa medidas na área **Valores** de uma visualização para calcular resultados baseados em outros campos. Use colunas calculadas como novos **Campos** em linhas, eixos, legendas e áreas de grupo de visualizações.

Este tutorial serve como guia para que você compreenda as colunas calculadas e crie-as usando as visualizações de relatório no Power BI Desktop. 

### <a name="prerequisites"></a>Pré-requisitos
- Este tutorial destina-se aos usuários do Power BI já familiarizados com o uso do Power BI Desktop para criar modelos mais avançados. Você já deve saber usar **Obter Dados** e o **Editor do Power Query** para importar dados, trabalhar com várias tabelas relacionadas e adicionar campos à tela de Relatório. Se ainda não estiver familiarizado com o Power BI Desktop, não deixe de conferir a [Introdução ao Power BI Desktop](desktop-getting-started.md).
  
- O tutorial usa o [Exemplo de vendas da Contoso para o Power BI Desktop](http://download.microsoft.com/download/4/6/A/46AB5E74-50F6-4761-8EDB-5AE077FD603C/Contoso%20Sales%20Sample%20for%20Power%20BI%20Desktop.zip), o mesmo exemplo usado para o tutorial [Criar suas próprias medidas no Power BI Desktop](desktop-tutorial-create-measures.md). Esses dados de vendas da empresa fictícia Contoso, Inc foram importados de um banco de dados, então você não conseguirá conectar-se à fonte de dados nem exibi-los no Editor do Power Query. Baixe e extraia o arquivo em seu próprio computador, e abra-o no Power BI Desktop.

## <a name="create-a-calculated-column-with-values-from-related-tables"></a>Criar uma coluna calculada com valores de tabelas relacionadas

No Relatório de vendas, você quer exibir categorias e subcategorias de produtos como valores únicos, como "Telefones celulares – Acessórios", "Telefones celulares – Smartphones e PDAs" etc. Não há nenhum campo na lista **Campos** que forneça esses dados, mas há um campo **ProductCategory** e um campo **ProductSubcategory**, cada um em sua própria tabela. Você pode criar uma coluna calculada que combina os valores dessas duas colunas. As fórmulas DAX podem aproveitar todo o potencial do modelo que você já tem, incluindo as relações entre tabelas diferentes já existentes. 

 ![Colunas na lista de campos](media/desktop-tutorial-create-calculated-columns/create1.png)

1.  Selecione as reticências (...) **Mais opções** (...) ou clique com o botão direito na tabela **ProductSubcategory** na lista Campos e selecione **Nova Coluna**. Isso cria sua nova coluna na tabela ProductSubcategory.
    
    ![Nova Coluna](media/desktop-tutorial-create-calculated-columns/create2.png)
    
    A barra de fórmulas aparece na parte superior da tela do Relatório, pronta para você renomear a coluna e inserir uma fórmula DAX.
    
    ![Barra de fórmulas](media/desktop-tutorial-create-calculated-columns/create3.png)
    
2.  Por padrão, uma nova coluna calculada é nomeada simplesmente como Coluna. Se você não a renomear, as novas colunas serão nomeadas Coluna 2, Coluna 3 e assim por diante. Como você quer que sua coluna seja mais identificável, como o nome **Coluna** já está destacado na barra de fórmula, renomeie-o digitando **ProductFullCategory** e digite um sinal de igual (**=**).
    
3.  Você quer que os valores na coluna nova comecem com o nome ProductCategory. Como esta coluna está em uma tabela diferente, mas relacionada, você pode usar a função [RELATED](https://msdn.microsoft.com/library/ee634202.aspx) para conseguir obtê-la.
    
    Após o sinal de igual, digite um **r**. Uma lista suspensa de sugestões mostra todas as funções DAX começando com a letra R. Selecione cada função para mostrar uma descrição do seu efeito. Conforme você digita, a lista de sugestões é dimensionada mais próxima da função desejada. Selecione **RELATED** e, em seguida, pressione **Enter**.
    
    ![Escolha RELATED](media/desktop-tutorial-create-calculated-columns/create4.png)
    
    Um parêntese de abertura é exibido, junto com outra lista de sugestões das colunas relacionadas que você pode passar para a função RELATED, com descrições e detalhes sobre os parâmetros esperados. 
    
    ![Escolha ProductCategory](media/desktop-tutorial-create-calculated-columns/create5.png)
    
4.  Você quer a coluna **ProductCategory** da tabela **ProductCategory**. Selecione **ProductCategory[ProductCategory]**, pressione **Enter** e, em seguida, digite um parêntese de fechamento.
    
    > [!TIP]
    > Os erros de sintaxe são causados com mais frequência por um parêntese de fechamento ausente ou mal-posicionado, embora às vezes o Power BI Desktop os adicione para você.
    
4. É preciso usar traços e espaços para separar as ProductCategories e ProductSubcategories nos novos valores; portanto, após o parêntese de fechamento da primeira expressão, digite um espaço, e comercial (**&**), aspas duplas (**"**), espaço, tracejado (**-**), outro espaço, aspas duplas outra e outro e comercial. Sua fórmula agora deve ter essa aparência:
    
    `ProductFullCategory = RELATED(ProductCategory[ProductCategory]) & " - " &`
    
    > [!TIP]
    > Se precisar de mais espaço, selecione a divisa inferior no lado direito da barra de fórmulas para expandir o editor de fórmulas. No editor, pressione **Alt + Enter** para mover uma linha para baixo e pressione **Tab** para mudar a posição das coisas.
    
5.  Insira outro colchete de abertura (**[**) e selecione a coluna **[ProductSubcategory]** para concluir a fórmula. 
    
    ![Escolha ProductSubcategory](media/desktop-tutorial-create-calculated-columns/create6.png)
    
    Você não precisa usar outra função RELATED para chamar a tabela ProductSubcategory na segunda expressão, porque está criando a coluna calculada nesta tabela. Você pode inserir [ProductSubCategory] com o prefixo do nome da tabela (totalmente qualificado) ou sem (não qualificado).
    
6.  Complete a fórmula, pressionando **Enter** ou selecionando a marca de confirmação na barra de fórmulas. A fórmula é validada e o nome da coluna **ProductFullCategory** aparece na tabela **ProductSubcategory** na lista Campos. 
    
    ![Coluna ProductFullCategory concluída](media/desktop-tutorial-create-calculated-columns/create7.png)
    
    >[!NOTE]
    >No Power BI Desktop, as colunas calculadas recebem um ícone especial na lista de campos mostrando que contêm fórmulas. No serviço do Power BI (seu site do Power BI), não é possível alterar fórmulas; portanto, as colunas calculadas não têm ícones.
    
## <a name="use-your-new-column-in-a-report"></a>Use sua nova coluna em um relatório

Agora você pode usar sua nova coluna ProductFullCategory para examinar SalesAmount por ProductFullCategory.

1. Selecione ou arraste a coluna **ProductFullCategory** a partir da tabela **ProductSubcategory** para a tela Relatório para criar uma tabela que mostra todos os nomes de ProductFullCategory.
   
   ![Tabela ProductFullCategory](media/desktop-tutorial-create-calculated-columns/vis1.png)
    
2. Selecione ou arraste o campo **SalesAmount** da tabela **Sales** para a tabela para mostrar a quantidade de vendas para cada categoria de produto completa.
   
   ![Tabela SalesAmount por ProductFullCategory](media/desktop-tutorial-create-calculated-columns/vis2.png)
    
## <a name="create-a-calculated-column-that-uses-an-if-function"></a>Criar uma coluna calculada que usa uma função IF

O Exemplo de Vendas da Contoso contém dados de vendas tanto para repositórios ativos quanto inativos. É interessante que as vendas de repositório ativo estejam claramente separadas de vendas de repositório inativo em seu relatório criando um campo Active StoreName. Na nova coluna calculada Active StoreName, cada repositório ativo aparecerá com o nome completo do repositório, enquanto os repositórios inativos estarão agrupados em "Inativo". 

Felizmente, a tabela Stores tem uma coluna denominada **Status**, com valores de "On" para repositórios ativos e "Off" para repositórios inativos, que podemos usar para criar valores para nossa nova coluna Active StoreName. Sua fórmula DAX usará a função lógica [IF](https://msdn.microsoft.com/library/ee634824.aspx) para testar o status de cada repositório e retornar um valor específico dependendo do resultado. Se o status de um repositório for "On", a fórmula retornará o nome do repositório. Se estiver "Off", a fórmula atribuirá um Active StoreName de "Inativo". 


1.  Crie uma nova coluna calculada chamada **Stores** na tabela **Active StoreName** na barra de fórmulas.
    
2.  Após o sinal **=**, comece digitando **IF**. A lista de sugestões mostrará o que você pode adicionar. Selecione **IF**.
    
    ![Selecione IF](media/desktop-tutorial-create-calculated-columns/if1.png)
    
3.  O primeiro argumento para IF é um teste lógico de se o status de um repositório estiver "Ativado". Digite um colchete de abertura **[**, que lista as colunas da tabela Stores e selecione **[Status]**.
    
    ![Selecione Status](media/desktop-tutorial-create-calculated-columns/if2.png)
    
4.  Logo após **[Status]**, digite **= "On"** e, em seguida, digite uma vírgula (**,**) para terminar o argumento. A dica de ferramenta sugere que agora você precisa adicionar um valor a ser retornado quando o resultado for TRUE.
    
    ![Adicionar o valor TRUE](media/desktop-tutorial-create-calculated-columns/if3.png)
    
5.  Se o status do repositório for "On", isso significará que você quer que o nome desse repositório seja exibido. Digite um colchete de abertura (**[**) e selecione a coluna **[StoreName]**, então digite outra vírgula. A dica de ferramenta agora indica que você precisa adicionar um valor a ser retornado quando o resultado for FALSE. 
    
    ![Adicionar um valor FALSE](media/desktop-tutorial-create-calculated-columns/if4.png)
    
6.  Você deseja que o valor seja *Inativo*; portanto, digite **"Inativo"** e, em seguida, complete a fórmula pressionando **Enter** ou selecionando a marca de seleção na barra de fórmulas. A fórmula valida e o nome da nova coluna aparece na tabela **Stores** na lista de campos.
    
    ![Coluna Active StoreName](media/desktop-tutorial-create-calculated-columns/if5.png)
    
8.  Podemos usar nossa nova coluna Active StoreName em visualizações, assim como ocorre com qualquer outro campo. Para mostrar SalesAmounts por Active StoreName, selecione o campo **Active StoreName** ou arraste-o para a tela e, em seguida, selecione o campo **SalesAmount** ou arraste-o para a tabela. Nessa tabela, os repositórios ativos aparecem individualmente por nome, mas os repositórios inativos estão agrupados no final como *Inativos*. 
    
    ![Tabela SalesAmount por Active StoreName](media/desktop-tutorial-create-calculated-columns/if6.png)
    
## <a name="what-youve-learned"></a>O que você aprendeu
Colunas calculadas podem enriquecer seus dados e facilitar a compreensão das informações. Você aprendeu a criar colunas calculadas na lista de campos e na barra de fórmulas, usar listas de sugestão e dicas de ferramenta para ajudar a construir as fórmulas, chamar funções DAX como RELATED e IF com os argumentos apropriados e usar colunas calculadas nas visualizações de relatório.

## <a name="next-steps"></a>Próximas etapas
Se desejar se aprofundar nas fórmulas DAX e criar colunas calculadas com fórmulas mais avançadas, veja [Noções básicas do DAX no Power BI Desktop](desktop-quickstart-learn-dax-basics.md). Este artigo enfoca os conceitos fundamentais no DAX, como sintaxe, funções e uma compreensão mais abrangente sobre o contexto.

Certifique-se de adicionar a [Referência ao DAX (Expressões de Análise de Dados)](https://msdn.microsoft.com/library/gg413422.aspx) aos favoritos. É nela que você encontrará informações detalhadas sobre a sintaxe do DAX, operadores, além de mais de 200 funções DAX.

