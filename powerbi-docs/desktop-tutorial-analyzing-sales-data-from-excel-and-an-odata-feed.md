---
title: 'Tutorial: Analisando dados de vendas do Excel e de um feed OData no Power BI Desktop'
description: 'Tutorial: Analisando dados de vendas do Excel e de um feed OData'
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
ms.date: 01/24/2018
ms.author: davidi
ms.openlocfilehash: 0723b3a7155626f875044fa813a522ef6d4923df
ms.sourcegitcommit: 6e693f9caf98385a2c45890cd0fbf2403f0dbb8a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2018
---
# <a name="tutorial-analyzing-sales-data-from-excel-and-an-odata-feed"></a>Tutorial: Analisando dados de vendas do Excel e de um feed OData
Com o **Power BI Desktop**, você pode se conectar todo tipo de fontes de dados diferentes, combinar e formatá-las de maneiras que facilitam a realização de análises de dados e visualizações interessantes e atraentes. Neste tutorial, você aprenderá a combinar dados de duas fontes de dados. 

É comum ter dados distribuídos em várias fontes de dados, como informações de produtos em um banco de dados e informações de vendas em outro. As técnicas que você aprenderá neste documento incluem uma pasta de trabalho do Excel e um feed OData, mas essas técnicas podem ser aplicadas a outras fontes de dados também, como consultas do SQL Server, arquivos CSV ou qualquer fonte de dados no Power BI Desktop.

Neste tutorial, você importará dados do Excel (ele inclui informações de produto) e do feed OData (que contém dados de pedidos). Você executará etapas de transformação e agregação, além de combinar dados de ambas as fontes, para produzir um relatório de **Total de vendas por produto e ano** que inclui visualizações interativas. 

Eis a aparência que esse relatório final terá:

![](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/18.png)

Para seguir as etapas neste tutorial, você precisa da pasta de trabalho Products, que pode ser baixada**:**[ clique](http://download.microsoft.com/download/1/4/E/14EDED28-6C58-4055-A65C-23B4DA81C4DE/Products.xlsx)[aqui](http://download.microsoft.com/download/1/4/E/14EDED28-6C58-4055-A65C-23B4DA81C4DE/Products.xlsx)[ para baixar](http://download.microsoft.com/download/1/4/E/14EDED28-6C58-4055-A65C-23B4DA81C4DE/Products.xlsx)**[Products.xlsx](http://download.microsoft.com/download/1/4/E/14EDED28-6C58-4055-A65C-23B4DA81C4DE/Products.xlsx)**[.](http://download.microsoft.com/download/1/4/E/14EDED28-6C58-4055-A65C-23B4DA81C4DE/Products.xlsx)

Na caixa de diálogo **Salvar Como** , nomeie o arquivo **Products.xlsx**.

## <a name="task-1-get-product-data-from-an-excel-workbook"></a>Tarefa 1: obter dados de produto de uma pasta de trabalho do Excel
Nesta tarefa, você importará produtos do arquivo Products.xlsx no Power BI Desktop.

### <a name="step-1-connect-to-an-excel-workbook"></a>Etapa 1: conectar-se a uma pasta de trabalho do Excel
1. Inicie o Power BI Desktop.
2. Na faixa de opções Página Inicial, selecione **Obter Dados**. Excel é uma das conexões de dados **Mais Comuns** , portanto você pode selecioná-la diretamente no menu **Obter Dados** .
   
   ![](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/t_excelodata_1.png)
3. Se você selecionar o botão Obter Dados diretamente, também é possível selecionar **Arquivo \> Excel** e **Conectar.**
4. Na caixa de diálogo **Abrir Arquivo** , selecione o arquivo **Products.xlsx** .
5. No painel **Navegador** , selecione a tabela **Products** e, em seguida, **Editar**.
   
   ![](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/t_excelodata_2.png)

### <a name="step-2-remove-other-columns-to-only-display-columns-of-interest"></a>Etapa 2: remover outras colunas para exibir apenas as colunas de interesse
Nesta etapa, você removerá todas as colunas exceto **ProductID**, **ProductName**, **UnitsInStock**e **QuantityPerUnit**. No Power BI Desktop, geralmente há algumas maneiras de realizar a mesma tarefa. Por exemplo, vários botões na faixa de opções também podem ser obtidos por meio do menu de atalho em uma coluna ou célula.

O Power BI Desktop inclui um Editor de Consultas, que é onde você formata e transforma suas conexões de dados. O Editor de Consultas é aberto automaticamente quando você seleciona **Editar** do **Navegador**. Você também pode abri-lo selecionando **Editar Consultas** na faixa de opções **Página Inicial** do Power BI Desktop. As etapas a seguir são executadas no Editor de Consultas.

1. No Editor de Consultas, selecione as colunas **ProductID**, **ProductName**, **QuantityPerUnit**e **UnitsInStock** (use **Ctrl + clique** para selecionar mais de uma coluna ou **Shift + clique** para selecionar as colunas que estão ao lado umas das outras).
2. Selecione **Remover Colunas**\>**Remover Outras Colunas** na faixa de opções, ou clique com o botão direito do mouse em um título de coluna e clique em **Remover Outras Colunas**.

![](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/anlayzingsalesdata_removeothercolumns.png)

### <a name="step-3-change-the-data-type-of-the-unitsinstock-column"></a>Etapa 3: alterar o tipo de dados da coluna UnitsInStock
Quando o Editor de Consultas se conecta aos dados, ele examina cada campo e determine o melhor tipo de dados. Para a pasta de trabalho do Excel, os produtos em estoque sempre serão um número inteiro, portanto nesta etapa confirme se o tipo de dados da coluna **UnitsInStock** é um Número Inteiro.

1. Selecione a coluna **UnitsInStock** .
2. Selecione o botão suspenso **Tipo de Dados** na faixa de opções **Página Inicial** .
3. Se não for um Número Inteiro, selecione **Número Inteiro** para o tipo de dados na lista suspensa (o botão **Tipo de Dados:** também exibe o tipo de dados para a seleção atual).
   
   ![](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/anlayzingsalesdata_wholenumber.png)      

### <a name="power-bi-desktop-steps-created"></a>Etapas criadas do Power BI Desktop
Conforme você realiza atividades de consulta no Editor de Consultas, as etapas de consulta são criadas e listadas no painel **Configurações de Consulta** , na lista **Etapas Aplicadas** . Cada etapa de consulta tem uma fórmula correspondente, também conhecida como a linguagem "M". Para obter mais informações sobre a linguagem de fórmula “M”, veja [Saiba mais sobre as fórmulas do Power BI](https://support.office.com/Article/Learn-about-Power-Query-formulas-6bc50988-022b-4799-a709-f8aafdee2b2f).

| Tarefa | Etapa de consulta | Fórmula |
| --- | --- | --- |
| Conectar-se a uma pasta de trabalho do Excel |Fonte |Source{[Name="Products"]}[Data] |
| Promover a primeira linha para títulos de colunas da tabela |FirstRowAsHeader |[Table.PromoteHeaders](https://support.office.com/Article/TablePromoteHeaders-b8eaeb95-042a-42e1-9164-6d3c646acadc "Table.PromoteHeaders") <br /> (Produtos) |
| Remover outras colunas para exibir apenas as colunas de interesse |RemovedOtherColumns |[Table.SelectColumns](https://support.office.com/Article/TableSelectColumns-20bb9e28-9fd3-4cd2-a21b-97972c82ec22 "Table.SelectColumns")  <br />(FirstRowAsHeader,{"ProductID", "ProductName", "QuantityPerUnit", "UnitsInStock"}) |
| Alterar tipo de dados |Tipo Alterado |Table.TransformColumnTypes(\#"Removed Other Columns",{{"UnitsInStock", Int64.Type}}) |

## <a name="task-2-import-order-data-from-an-odata-feed"></a>Tarefa 2: importar dados de pedidos de um feed OData
Nesta tarefa, você poderá inserir dados de pedidos. Esta etapa representa a conexão a um sistema de vendas. Importe dados no Power BI Desktop do exemplo de feed OData Northwind na seguinte URL, que você pode copiar (e colar) nas etapas abaixo: <http://services.odata.org/V3/Northwind/Northwind.svc/> 

### <a name="step-1-connect-to-an-odata-feed"></a>Etapa 1: conectar-se a um feed OData
1. Na guia de faixa de opções **Home** do Editor de Consultas, selecione **Obter Dados.**
2. Navegue até a fonte de dados do **Feed OData** .
3. Na caixa de diálogo **Feed OData** , cole a **URL** do feed OData Northwind.
4. Selecione **OK**.
5. No painel **Navegador** , selecione a tabela **Orders** e, em seguida, **Editar**.
   
   ![](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/anlayzingsalesdata_odatafeed.png)

>[!NOTE]
>Clique em um nome de tabela sem selecionar a caixa de seleção para ver uma versão prévia.

### <a name="step-2-expand-the-orderdetails-table"></a>Etapa 2: Expandir a tabela Order\_Details
A tabela **Orders** contém uma referência a uma tabela **Details**. Esta tabela contém os produtos individuais que foram incluídos em cada Pedido. Quando se conectar a fontes de dados com várias tabelas (como um banco de dados relacional), é possível usar essas referências para criar sua consulta. 

Nesta etapa, você expandirá a tabela **Order\_Details** relacionada à tabela **Orders**, para combinar as colunas **ProductID**, **UnitPrice** e **Quantity** de **Order\_Details** na tabela **Orders**. Essa é uma representação dos dados nessas tabelas:

![](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/orderdetails.png)

A operação **Expandir** combina colunas de uma tabela relacionada em uma tabela de entidade. Quando a consulta é executada, linhas da tabela relacionada (**Order\_Details**) são combinadas em linhas da tabela de entidade (**Orders**).

Depois de expandir a tabela **Order\_Details**, três novas colunas e linhas são adicionadas à tabela **Orders**, uma para cada linha na tabela aninhada ou relacionada.

1. Na **Visualização da Consulta**, role até a coluna **Order\_Details**.
2. Na coluna **Order\_Details**, selecione o ícone de expansão (![](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/expand.png)).
3. Na lista suspensa **Expandir** :
   1. Selecione **(Selecionar Todas as Colunas)** para limpar todas as colunas.
   2. Selecione **ProductID**, **UnitPrice**e **Quantity**.
   3. Clique em **OK**.
      ![](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/7.png)

### <a name="step-3-remove-other-columns-to-only-display-columns-of-interest"></a>Etapa 3: remover outras colunas para exibir apenas as colunas de interesse
Nesta etapa, você removerá todas as colunas, exceto as colunas **OrderDate, ShipCity**, **ShipCountry**, **Order\_Details.ProductID**, **Order\_Details.UnitPrice** e **Order\_Details.Quantity**. Na tarefa anterior, você usou **Remover Outras Colunas**. Para esta tarefa, remova as colunas selecionadas.

1. Na **Visualização da Consulta**, selecione todas as colunas concluindo a. e b.:
   1. Clique na primeira coluna (**OrderID**).
   2. Shift + clique na última coluna (**Shipper**).
   3. Agora que todas as colunas foram selecionadas, use Ctrl + clique para desmarcar as seguintes colunas: **OrderDate**, **ShipCity**, **ShipCountry**, **Order\_Details.ProductID**, **Order\_Details.UnitPrice** e **Order\_Details.Quantity**.
2. Agora que apenas as colunas que desejamos remover foram selecionadas, clique com o botão direito do mouse em qualquer título de coluna selecionado e em **Remover Colunas**.

### <a name="step-4-calculate-the-line-total-for-each-orderdetails-row"></a>Etapa 4: Calcular o total de cada linha Order\_Details
O Power BI Desktop permite criar cálculos com base nas colunas que você está importando, para enriquecer os dados aos quais você se conecta. Nesta etapa, você criará uma **Coluna Personalizada** para calcular o total de cada linha **Order\_Details**.

Calcular o total de cada linha **Order\_Details**:

1. Na guia de faixa de opções **Adicionar Coluna** , clique em **Adicionar** **Coluna Personalizada**.
   
   ![](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/t_excelodata_4.png)
2. Na caixa de diálogo **Adicionar Coluna Personalizada**, na caixa de texto **Fórmula de Coluna Personalizada**, insira **[Order\_Details.UnitPrice] \* [Order\_Details.Quantity]**.
3. Na caixa de texto **Nome da nova coluna** , digite **LineTotal**.
   
   ![](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/8.png)
4. Clique em **OK**.

### <a name="step-5-set-the-datatype-of-the-linetotal-field"></a>Etapa 5: Definir o tipo de dados do campo LineTotal
1. Clique com o botão direito do mouse na coluna **LineTotal** .
2. Selecione **Alterar Tipo** e escolha **Número Decimal**.
   
   ![](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/9.png)

### <a name="step-6-rename-and-reorder-columns-in-the-query"></a>Etapa 6: Renomear e reordenar colunas na consulta
Nesta etapa, renomeando as colunas finais e alterando sua ordem, você concluirá o processo de facilitar o trabalho com o modelo na criação de relatórios.

1. Em **Exibição de Consulta**, arraste a coluna **LineTotal** para a esquerda, após **ShipCountry**.
   
   ![](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/10.png)
2. Remova o prefixo *Order\_Details.* das colunas **Order\_Details.ProductID**, **Order\_Details.UnitPrice** e **Order\_Details.Quantity** clicando duas vezes em cada título de coluna e excluindo o texto do nome da coluna.

### <a name="power-bi-desktop-steps-created"></a>Etapas criadas do Power BI Desktop
Conforme você realiza atividades de consulta no Editor de Consultas, as etapas de consulta são criadas e listadas no painel **Configurações de Consulta** , na lista **Etapas Aplicadas** . Cada etapa de consulta tem uma fórmula Power Query correspondente, também conhecida como a linguagem "M". Para obter mais informações sobre essa linguagem de fórmula, consulte [Saiba mais sobre fórmulas do Power Query](https://support.office.com/Article/Learn-about-Power-Query-formulas-6bc50988-022b-4799-a709-f8aafdee2b2f "Saiba mais sobre fórmulas do Power BI").

| Tarefa | Etapa de consulta | Fórmula |
| --- | --- | --- |
| Conectar-se a um feed OData |Fonte |Source{[Name="Orders"]}[Data] |
| Expandir a tabela Order\_Details |Expandir Order\_Details |[Table.ExpandTableColumn](https://support.office.com/Article/TableExpandTableColumn-54903f25-75a2-4a44-a9a3-52a9d895ee98 "Table.ExpandTableColumn") <br /> (Orders, "Order\_Details", {"ProductID", "UnitPrice", "Quantity"}, {"Order\_Details.ProductID", "Order\_Details.UnitPrice", "Order\_Details.Quantity"}) |
| Remover outras colunas para exibir apenas as colunas de interesse |RemovedColumns |[Table.RemoveColumns](https://support.office.com/Article/TableRemoveColumns-6265190e-2f58-4300-85b8-df88fc1a67d3 "Table.RemoveColumns") <br />(\#"Expand Order\_Details",{"OrderID", "CustomerID", "EmployeeID", "RequiredDate", "ShippedDate", "ShipVia", "Freight", "ShipName", "ShipAddress", "ShipCity", "ShipRegion", "ShipPostalCode", "ShipCountry", "Customer", "Employee", "Shipper"}) |
| Calcular o total de cada linha Order\_Details |InsertedColumn |[Table.AddColumn](https://support.office.com/Article/TableAddColumn-6c64d0a5-9654-4d15-bfb6-9cc380aaf3c0 "Table.AddColumn") <br /> (RemovedColumns, "Custom", each [Order\_Details.UnitPrice] \* [Order\_Details.Quantity]) |

## <a name="task-3-combine-the-products-and-total-sales-queries"></a>Tarefa 3: combinar as consultas de Produtos e Total de Vendas
O Power BI Desktop não requer que você combine consultas para relatar informações sobre elas. Em vez disso, você pode criar **Relações** entre conjuntos de dados. Essas relações podem ser criadas em qualquer coluna que é comum aos seus conjuntos de dados. Para obter mais informações, veja [Criar e gerenciar relações](desktop-create-and-manage-relationships.md).

Neste tutorial, temos os dados de Orders e Products que compartilham um campo “ProductID” comum; portanto, precisamos garantir que há uma relação entre elas no modelo que estamos usando com o Power BI Desktop. Basta especificar no Power BI Desktop que as colunas de cada tabela são relacionadas (ou seja, colunas que contêm os mesmos valores). O Power BI Desktop estabelece a direção e a cardinalidade da relação para você. Em alguns casos, ele até mesmo detectará as relações automaticamente.

Nesta tarefa, você confirmará que uma relação foi estabelecida no Power BI Desktop entre as consultas **Produtos** e **Total de Vendas** .

### <a name="step-1-confirm-the-relationship-between-products-and-total-sales"></a>Etapa 1: confirmar a relação entre Produtos e Total de Vendas
1. Primeiro, precisamos carregar o modelo que criamos no Editor de Consultas no Power BI Desktop. No faixa de opções **Home** do Editor de Consultas, selecione **Fechar e Carregar**.
   
   ![](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/t_excelodata_4.png)
2. O Power BI Desktop carrega os dados de duas consultas.
   
   ![](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/11.png)      
3. Depois de carregar os dados, selecione o botão **Gerenciar Relações** na faixa de opções **Página Inicial** .
   
   ![](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/t_excelodata_5.png)
4. Selecione o botão **Novo...** .
   
   ![](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/t_excelodata_6.png)
5. Ao tentar criar a relação, vemos que ela já existe! Como mostrado no diálogo **Criar Relacionamento** (pelas colunas sombreadas), os campos **ProductsID** em cada consulta já têm uma relação estabelecida.
   
    ![](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/12.png)
6. Selecione **Cancelar**e, em seguida, exibição de **Relação** no Power BI Desktop.
   
   ![](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/t_excelodata_7.png)
7. Vemos o seguinte, que visualiza a relação entre as consultas:
   
   ![](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/t_excelodata_8.png)
8. Quando você clica duas vezes na seta da linha que conecta o às consultas, um diálogo **Editar Relação** é exibido.
   
   ![](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/t_excelodata_9.png)
9. Como não é necessário fazer nenhuma alteração, vamos apenas selecionar **Cancelar** para fechar o diálogo **Editar Relação** .

## <a name="task-4-build-visuals-using-your-data"></a>Tarefa 4: criar elementos visuais com seus dados
O Power BI Desktop permite criar diversas visualizações para obter informações dos seus dados. Você pode criar relatórios com várias páginas e cada página pode ter vários elementos visuais. Você pode interagir com suas visualizações para ajudar a analisar e compreender seus dados. Para obter mais informações sobre como editar relatórios, veja [Editar um relatório](service-interact-with-a-report-in-editing-view.md).

Nesta tarefa, você criará um relatório com base nos dados carregados anteriormente. Use o painel Campos para selecionar as colunas por meio das quais você criará as visualizações.

### <a name="step-1-create-charts-showing-units-in-stock-by-product-and-total-sales-by-year"></a>Etapa 1: Criar gráficos mostrando Unidades em Estoque por Produto e o Total de Vendas por Ano
Arraste **UnitsInStock** do painel Campo (o painel Campos está à direita da tela) para um espaço em branco na tela. Uma visualização de Tabela é criada. Em seguida, arraste ProductName até à caixa Eixo, localizada na metade inferior do painel Visualizações. Depois, selecionamos **Classificar Por \> UnitsInStock** usando o marcador no canto superior direito da visualização.

![](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/14.png)

Arraste **OrderDate** para a tela abaixo do primeiro gráfico e, em seguida, arraste LineTotal (novamente, do painel Campos) para o elemento visual e selecione o Gráfico de Linhas. A visualização a seguir é criada.

![](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/15.png)

 Depois, arraste **ShipCountry** para um espaço no canto superior direito da tela. Como você selecionou um campo geográfico, um mapa foi criado automaticamente. Agora, arraste **LineTotal** para o campo **Values** ; os círculos no mapa para cada país agora são relativos em tamanho em relação a **LineTotal** dos pedidos enviados para esse país.

![](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/17.png)

### <a name="step-2-interact-with-your-report-visuals-to-analyze-further"></a>Etapa 2: Interagir com os elementos visuais de seu relatório para analisar com mais profundidade
O Power BI Desktop permite interagir com elementos visuais que realizam ações cruzadas de realce e filtragem entre si para revelar outras tendências. Para obter mais detalhes, veja [Filtragem e realce em relatórios](power-bi-reports-filters-and-highlighting.md)

1. Clique no círculo azul claro centralizado em **Canad****á.** Observe como os outros visuais são filtrados para mostrar o Estoque (**ShipCountry**) e o Total de Pedidos (**LineTotal**) somente para o Canadá.
   
   ![](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/18.png)

## <a name="complete-sales-analysis-report"></a>Relatório de Análise de Vendas completo
Depois de realizar todas essas etapas, você terá um Relatório de Vendas que combina dados do arquivo Products.xlsx e do feed OData Northwind. O relatório mostra os elementos visuais que ajudam a analisar informações de vendas de diferentes países. Você pode baixar [aqui](http://download.microsoft.com/download/1/4/E/14EDED28-6C58-4055-A65C-23B4DA81C4DE/Analyzing_Sales_Data.pbix) um arquivo completo do Power BI Desktop para este tutorial.

## <a name="next-steps"></a>Próximas etapas
* [Leia outros tutoriais do Power BI Desktop](http://go.microsoft.com/fwlink/?LinkID=521937)
* [Assista a vídeos do Power BI Desktop](http://go.microsoft.com/fwlink/?LinkID=519322)
* [Visite o Fórum do Power BI](http://go.microsoft.com/fwlink/?LinkID=519326)
* [Leia o Blog do Power BI](http://go.microsoft.com/fwlink/?LinkID=519327)


