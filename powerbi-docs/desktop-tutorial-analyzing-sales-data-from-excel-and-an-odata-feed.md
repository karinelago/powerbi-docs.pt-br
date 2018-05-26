---
title: 'Tutorial: combinar dados do Excel e de um feed OData no Power BI Desktop'
description: 'Tutorial: combinar dados do Excel e de um feed OData'
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: tutorial
ms.date: 05/21/2018
ms.author: v-thepet
LocalizationGroup: Learn more
ms.openlocfilehash: c6cd75efd44259c2812f98a37875cf716d4843ad
ms.sourcegitcommit: e6db826c2f43a69e4c63d5f4920baa8f66bc41be
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/23/2018
---
# <a name="tutorial-combine-sales-data-from-excel-and-an-odata-feed"></a>Tutorial: combinar dados de vendas do Excel e de um feed OData

É comum ter dados distribuídos em várias fontes de dados, como informações de produtos em um banco de dados e informações de vendas em outro. Com o **Power BI Desktop**, é possível combinar dados de diferentes origens para criar visualizações e análises de dados interessantes e atrativas. 

Neste tutorial, você aprenderá a combinar dados de duas fontes: uma pasta de trabalho do Excel incluindo informações de produto e um feed OData contendo dados de pedidos. Após importar cada conjunto de dados e executar as etapas de transformação e agregação, você usará dados das duas fontes para produzir um relatório de análise de vendas com visualizações interativas. Essas técnicas também podem ser aplicadas a consultas de SQL Server, arquivos CSV e qualquer outra fonte de dados no Power BI Desktop.

>[!NOTE]
>No Power BI Desktop, normalmente há algumas maneiras de realizar uma mesma tarefa. Por exemplo, várias seleções da faixa de opções também estão disponíveis por meio de um clique com o botão direito do mouse ou de um menu **Mais opções** em uma coluna ou célula. Vários métodos alternativos são descritos nas etapas abaixo. 

## <a name="import-the-product-data-from-excel"></a>Importar os dados de produto do Excel

Primeiro, importe os dados de produto da pasta de trabalho Products.xlsx do Excel para o Power BI Desktop.

1. [Baixe a pasta de trabalho Products.xlsx do Excel](http://download.microsoft.com/download/1/4/E/14EDED28-6C58-4055-A65C-23B4DA81C4DE/Products.xlsx) e salve-a como **Products.xlsx**.
   
2. Selecione a seta suspensa ao lado de **Obter Dados** na guia **Início** da faixa de opções do Power BI Desktop e, em seguida, selecione **Excel** no menu suspenso **Mais Comum**. 
   
   ![Obter dados](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/t_excelodata_1.png)
   
   >[!NOTE]
   >Também é possível selecionar o próprio item **Obter Dados** ou, ainda, selecionar **Obter Dados** na caixa de diálogo **Começar** do Power BI e, em seguida, selecionar **Excel** ou **Arquivo** > **Excel** na caixa de diálogo **Obter Dados** e, então, selecionar **Conectar**.
   
3. Na caixa de diálogo **Abrir**, navegue até o arquivo **Products.xlsx** e selecione-o e, em seguida, selecione **Abrir**.
   
4. No painel **Navegador** , selecione a tabela **Products** e, em seguida, **Editar**.
   
   ![Painel Navegador do Excel](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/t_excelodata_2.png)
   
Uma visualização da tabela é aberta no **Power Query Editor**, no qual é possível aplicar transformações para limpar os dados. 
   
![Editor do Power Query](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/t_excelodata_3.png)
   
>[!NOTE]
>Também é possível abrir o **Power Query Editor** selecionando **Editar Consultas** > **Editar Consultas** na faixa de opções **Início** do Power BI Desktop, clicando com o botão direito do mouse ou escolhendo **Mais opções** ao lado de qualquer consulta em **Exibição de Relatório** e selecionando **Editar Consulta**.

## <a name="clean-up-the-products-columns"></a>Limpar as colunas de produtos

Seu relatório combinado usará apenas as colunas **ProductID**, **ProductName**, **QuantityPerUnit** e **UnitsInStock** da pasta de trabalho do Excel, de modo que você pode remover as outras colunas. 

1. No **Power Query Editor**, selecione as colunas **ProductID**, **ProductName**, **QuantityPerUnit** e **UnitsInStock** (use **Ctrl**+**clique** para selecionar mais de uma coluna ou **Shift**+**clique** para selecionar colunas que estão ao lado umas das outras).
   
2. Clique com o botão direito do mouse em qualquer um dos cabeçalhos selecionados e selecione **Remover Outras Colunas** no menu suspenso para remover todas as colunas da tabela, exceto pelas selecionadas. 
   Também é possível selecionar **Remover Colunas** > **Remover Outras Colunas** do grupo **Gerenciar Colunas** na guia de faixa de opções **Início**. 
   
   ![Remover outras colunas](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/analyzingsalesdata_removeothercolumns.png)

## <a name="import-the-order-data-from-an-odata-feed"></a>Importar os dados de pedido de um feed OData

Em seguida, importe os dados de pedido do feed OData de exemplo do sistema de vendas da Northwind. 

1. No **Power Query Editor**, selecione **Nova Fonte** e, em seguida, selecione **Feed OData** na lista suspensa **Mais Comum**. 
   
   ![Obter OData](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/get_odata.png)
   
2. Na caixa de diálogo **Feed OData**, cole a URL do feed OData da Northwind, `http://services.odata.org/V3/Northwind/Northwind.svc/`, e selecione **OK**.
   
   ![Caixa de diálogo do feed OData](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/get_odata2.png)
   
3. No painel **Navegador**, selecione a tabela **Orders** e, em seguida, selecione **OK** para carregar os dados no **Power Query Editor**.
   
   ![Painel Navegador do OData](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/analyzingsalesdata_odatafeed.png)
   
   >[!NOTE]
   >No **Navegador**, você pode selecionar qualquer nome de tabela sem marcar a caixa de seleção para ver uma visualização.

## <a name="expand-the-order-data"></a>Expandir os dados de pedido

Quando se conecta a fontes de dados com várias tabelas, como bancos de dados relacionais ou o feed OData da Northwind, você pode usar referências entre as tabelas para criar suas consultas. A tabela **Orders** contém referências a várias tabelas relacionadas. Você pode adicionar as colunas **ProductID**, **UnitPrice** e **Quantity** da tabela relacionada **Order_Details** na tabela em questão (**Orders**) usando a operação **Expandir**. 

1. Role para a direita na tabela **Orders** até ver a coluna **Order_Details**. Observe que, em vez de dados, ela contém referências a outra tabela.
   
   ![Coluna Order_Details](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/7.png)
   
2. Selecione o ícone **Expandir** (![ícone Expandir](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/expand.png)) no cabeçalho da coluna **Order_Details**. 
   
3. Na lista suspensa **Expandir** :
   
   1. Selecione **(Selecionar Todas as Colunas)** para limpar todas as colunas.
      
   2. Selecione **ProductID**, **UnitPrice** e **Quantity** e, então, selecione **OK**.
      
      ![Caixa de diálogo Expandir](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/8.png)

Após você expandir a tabela **Order_Details**, a coluna **Order_Details** será substituída pelas três novas colunas da tabela aninhada e você verá novas linhas na tabela para os dados adicionados de cada pedido. 

![Colunas expandidas](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/9.png)

## <a name="create-a-custom-calculated-column"></a>Criar uma coluna calculada personalizada

O Power Query Editor permite criar cálculos e campos personalizados para enriquecer seus dados. Você criará uma coluna personalizada que calcula o preço total de cada item de linha de um pedido multiplicando o preço unitário pela quantidade de itens.

1. Na guia de faixa de opções **Adicionar Coluna** do Power Query Editor, selecione **Coluna Personalizada**.
   
   ![](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/10.png)
   
2. Na caixa de diálogo **Coluna Personalizada**, digite **LineTotal** no campo **Nome da nova coluna**.

3. No campo **Fórmula de coluna personalizada** depois de **=**, insira **[Order_Details.UnitPrice]** \* **[Order_Details.Quantity]**. (Você também pode selecionar os nomes dos campos na caixa de rolagem **Colunas disponíveis** e selecionar **<< Inserir** em vez de digitá-los.) 
3. Selecione **OK**.
   
   ![Caixa de diálogo Coluna Personalizada](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/11.png)

O novo campo **LineTotal** aparece como a última coluna na tabela **Orders**.

## <a name="set-the-data-type-for-the-new-field"></a>Defina o tipo de dados do novo campo

Quando se conecta aos dados, o Power Query Editor determina o melhor tipo de dados para cada campo e exibe os dados de acordo com o que determinar. É possível ver os tipos de dados atribuídos aos campos pelos ícones nos cabeçalhos ou em **Tipo de Dados** no grupo **Transformar** da guia de faixa de opções **Início**. 

Sua nova coluna **LineTotal** tem o tipo de dados **Qualquer**, mas seus valores são de moeda. Para atribuir um tipo de dados, clique com o botão direito do mouse no cabeçalho da coluna **LineTotal**, selecione **Alterar Tipo de Dados** na lista suspensa e selecione **Número decimal fixo**. 

![Alterar tipo de dados](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/12.png)

>[!NOTE]
>Também é possível selecionar a coluna **LineTotal** e, em seguida, selecionar a seta suspensa ao lado de **Tipo de Dados** na área **Transformar** da guia de faixa de opções **Início** e, por fim, selecionar **Número decimal fixo**.

## <a name="clean-up-the-orders-columns"></a>Limpar as colunas de pedidos

Para facilitar o trabalho com seu modelo nos relatórios, você pode excluir, renomear e reordenar algumas das colunas.

Seu relatório usará apenas as colunas **OrderDate**, **ShipCity**, **ShipCountry**, **Order_Details.ProductID**, **Order_Details.UnitPrice** e **Order_Details.Quantity**. Você pode selecionar essas colunas e usar **Remover Outras Colunas**, como fez com os dados do Excel ou pode selecionar todas as colunas, exceto pelas listadas, clicar com o botão direito do mouse em uma delas e selecionar **Remover Colunas** para remover todas elas. 

Você pode facilitar a identificação das colunas **Order_Details.ProductID**, **Order_Details.UnitPrice** e **Order_Details.Quantity** removendo os prefixos *Order_Details.* dos nomes das colunas. Para renomear as colunas como **ProductID**, **UnitPrice** e **Quantity**, respectivamente:

1. Clique duas vezes ou toque e segure o cabeçalho de cada coluna ou, ainda, clique com o botão direito do mouse no cabeçalho da coluna e selecione **Renomear** na lista suspensa. 
2. Exclua o prefixo *Order_Details.* de cada nome e, em seguida, pressione **Enter**.

Por fim, para tornar a coluna **LineTotal** mais fácil de acessar, arraste e solte-a à esquerda, logo à direita da coluna **ShipCountry**.

![Tabela limpa](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/14.png)

## <a name="review-the-query-steps"></a>Examinar as etapas de consulta

Conforme você moldou e transformou os dados no Power Query Editor, cada etapa foi registrada na área **Etapas Aplicadas** do painel **Config. Consulta** no lado direito do Power Query Editor. Você pode percorrer novamente as Etapas Aplicadas para examinar as alterações feitas e editar, excluir ou reorganizá-las se for necessário (embora isso possa ser arriscado, pois alterar etapas anteriores pode invalidar etapas posteriores). 

Selecione cada uma de suas consultas na lista **Consultas** no lado esquerdo do Power Query Editor e examine as **Etapas Aplicadas** em **Config. Consulta**. Após a aplicação das transformações de dados anteriores, as Etapas Aplicadas de suas duas consultas devem ser semelhantes ao seguinte:

![Etapas Aplicadas de consulta de produtos](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/15.png) &nbsp;&nbsp; ![Etapas Aplicadas de consulta de pedidos](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/17.png)

>[!TIP]
>As Etapas Aplicadas são formadas por fórmulas escritas na **Linguagem do Power Query**, também conhecida como linguagem **M**. Para ver e editar as fórmulas, selecione **Editor Avançado** no grupo **Consulta** da guia Página Inicial da faixa de opções. 

## <a name="import-the-transformed-queries"></a>Importar as consultas transformadas

Quando estiver satisfeito com os dados transformados, selecione **Fechar e Aplicar** > **Fechar e Aplicar** no grupo **Fechar** da guia de faixa de opções **Início** para importar os dados para a Exibição de Relatório do Power BI Desktop. 

![Fechar e Aplicar](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/t_excelodata_4.png)

Após os dados serem carregados, as consultas aparecem na lista **Campos** na Exibição de Relatório do Power BI Desktop.

![Consultas na lista Campos](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/18.png)

## <a name="manage-the-relationship-between-the-datasets"></a>Gerenciar a relação entre conjuntos de dados

O Power BI Desktop não requer que você combine consultas para relatar informações sobre elas. No entanto, você pode usar as relações entre conjuntos de dados, com base nos campos que eles têm em comum, para estender e enriquecer seus relatórios. O Power BI Desktop pode detectar relações automaticamente ou você pode criá-las na caixa de diálogo **Gerenciar Relações** do Power BI Desktop. Para obter mais informações sobre relações no Power BI Desktop, confira [Criar e gerenciar relações](desktop-create-and-manage-relationships.md).

Os conjuntos de dados Orders e Products neste tutorial compartilham um campo *ProductID* comum, portanto, há uma relação entre eles com base nessa coluna. 

1. Na Exibição de Relatório do Power BI Desktop, selecione **Gerenciar Relações** na área **Relações** da guia de faixa de opções **Início**.
   
   ![Faixa de opções Gerenciar Relações](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/t_excelodata_5.png)
   
2. Na caixa de diálogo **Gerenciar Relações**, observe que Power BI Desktop já detectou e listou uma relação ativa entre as tabelas Products e Orders. Para exibir a relação, selecione **Editar**. 
   
   ![Caixa de diálogo Gerenciar Relações](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/t_excelodata_6.png)
   
   A caixa de diálogo **Editar Relação** é aberta, mostrando detalhes sobre a relação.  
   
   ![Caixa de diálogo Editar Relação](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/t_excelodata_7.png)
   
3. O Power BI Desktop detectou automaticamente a relação corretamente, de modo que você pode selecionar **Cancelar** e **Fechar** para sair das caixas de diálogo de relação.

Você também pode exibir e gerenciar as relações entre as consultas selecionando a exibição **Relação** no lado esquerdo da janela do Power BI Desktop. Clique duas vezes na seta na linha que conecta as duas consultas para abrir a caixa de diálogo **Editar Relação** e exibir ou alterar a relação. 

![Exibição de Relação](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/t_excelodata_8.png)

Para sair da Exibição de Relações e voltar à Exibição de Relatório, selecione o ícone de **Exibição de Relatório**. 

![Ícone de Exibição de Relatório](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/t_excelodata_9.png)

## <a name="create-visualizations-using-your-data"></a>Criar visualizações usando seus dados

Na Exibição de Relatório do Power BI Desktop, você pode criar diversas visualizações para obter insights de seus dados. Você pode criar relatórios com várias páginas e cada página pode ter vários visuais. Você e outras pessoas podem interagir com suas visualizações para ajudar a analisar e compreender seus dados. Para obter mais informações sobre como exibir e editar relatórios no Serviço do Power BI (seu site), confira [Editar um Relatório](service-interact-with-a-report-in-editing-view.md).

Você pode usar seus dois conjuntos de dados, bem como a relação entre eles, para ajudar a visualizar e analisar seus dados de vendas. 

Primeiro, crie um gráfico de colunas empilhadas que usa campos das duas consultas para mostrar a quantidade de cada produto pedido. 

1. Selecione o campo **Quantity** de **Orders** no painel **Campos** painel à direita ou arraste-o para um espaço em branco na tela. Isso cria um gráfico de colunas empilhadas mostrando a quantidade total de todos os produtos pedidos. 
   
2. Selecione **ProductName** de **Produtos** no painel **Campos** ou arraste-o para o gráfico para mostrar a quantidade de cada produto pedido. 
   
3. Para classificar os produtos dos mais para os menos pedidos, selecione as reticências (**...**) em **Mais opções** no canto superior direito da visualização e, em seguida, selecione **Classificar por Quantidade**.
   
4. Use as alças nos cantos do gráfico para aumentá-lo para que mais nomes de produtos fiquem visíveis. 
   
   ![Gráfico de barras Quantity por ProductName](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/19.png)

Em seguida, crie um gráfico mostrando os valores em dinheiro dos pedidos (**LineTotal**) ao longo do tempo (**OrderDate**). 

1. Sem nada selecionado na tela, selecione **LineTotal** de **Orders** no painel **Campos** ou arraste-o para um espaço em branco na tela. O gráfico de colunas empilhadas mostra o valor em dinheiro total de todos os pedidos. 
   
2. Com o gráfico selecionado, selecione **OrderDate** em **Orders** ou arraste-o para o gráfico. Agora, o gráfico mostra os totais de linha para cada data de pedido. 
   
3. Redimensione a visualização arrastando os cantos para conseguir ver mais dados. 
   
   ![Gráfico de linhas LineTotals por OrderDate](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/20.png)
   
   >[!TIP]
   >Se só estiver vendo Anos no gráfico (somente três pontos de dados), clique na seta suspensa ao lado de **OrderDate** no campo **Eixo** do painel **Visualizações** e selecione **OrderDate** em vez de **Hierarquia de Datas**. 

Por fim, crie uma visualização de mapa mostrando as quantidades de pedidos de cada país. 

1. Sem nada selecionado na tela, selecione **ShipCountry** de **Orders** no painel **Campos** ou arraste-o para um espaço em branco na tela. O Power BI Desktop detecta que os dados são nomes de países e cria automaticamente uma visualização de mapa com um ponto de dados para cada país com pedidos. 
   
2. Para fazer com que os tamanhos dos pontos de dados reflitam o total de pedidos de cada país, arraste o campo **LineTotal** para o mapa (ou arraste-o até **Arraste campos de dados aqui** em **Tamanho**, na metade inferior do painel **Visualizações**). Agora, os tamanhos dos círculos no mapa refletem os valores em dinheiro dos pedidos de cada país. 
   
   ![Visualização de mapa LineTotals por ShipCountry](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/21.png)

## <a name="interact-with-your-report-visuals-to-analyze-further"></a>Interagir com os elementos visuais de seu relatório para analisar com mais profundidade

O Power BI Desktop permite descobrir mais tendências interagindo com visuais que realizam ações cruzadas de realce e de filtragem entre si. Para obter mais detalhes, veja [Filtragem e realce em relatórios](power-bi-reports-filters-and-highlighting.md). 

Devido à relação entre as consultas, interações com uma visualização afetam todas as outras visualizações na página. 

Na visualização de mapa, selecione o círculo centralizado no **Canadá**. Observe que as outras duas visualizações são filtradas de forma a realçar os totais de linha e as quantidades de pedidos apenas para o Canadá.

![Dados de vendas filtrados para o Canadá](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/22.png)

Se você selecionar um dos produtos no gráfico **Quantity by ProductName**, o mapa e o gráfico de data serão filtrados de forma a refletir os dados relativos ao produto e se você selecionar uma das datas no gráfico **LineTotal by OrderDate**, o mapa e o gráfico de produto serão filtrados de forma a mostrar os dados relativos a essa data. 
>[!TIP]
>Para cancelar uma seleção, selecione-a novamente ou selecione uma das outras visualizações. 

## <a name="complete-the-sales-analysis-report"></a>Concluir o relatório de análise de vendas

Seu relatório concluído combina dados do arquivo do Excel Products.xlsx e do feed OData da Northwind em elementos visuais que ajudam a analisar informações de pedidos relacionadas a diferentes países, períodos e produtos. Quando seu relatório estiver pronto, você poderá [fazer upload dele no serviço do Power BI](desktop-upload-desktop-files.md) ou compartilhá-lo com outros usuários do Power BI.

## <a name="next-steps"></a>Próximas etapas
* [Leia outros tutoriais do Power BI Desktop](http://go.microsoft.com/fwlink/?LinkID=521937)
* [Assista a vídeos do Power BI Desktop](http://go.microsoft.com/fwlink/?LinkID=519322)
* [Visite o Fórum do Power BI](http://go.microsoft.com/fwlink/?LinkID=519326)
* [Leia o Blog do Power BI](http://go.microsoft.com/fwlink/?LinkID=519327)