---
title: "Tutorial: segurança em nível de linha dinâmica com modelo da tabela do Analysis Services no Power BI"
description: "Tutorial: segurança em nível de linha dinâmica com modelo da tabela do Analysis Services"
services: powerbi
documentationcenter: 
author: selvarms
manager: amitaro
backup: davidi
editor: davidi
tags: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 10/12/2017
ms.author: selvar
LocalizationGroup: Connect to data
ms.openlocfilehash: 67b347be9974605156d02cbbf179126c68ae91e8
ms.sourcegitcommit: 4217430c3419046c3a90819c34f133ec7905b6e7
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2018
---
# <a name="tutorial-dynamic-row-level-security-with-analysis-services-tabular-model"></a>Tutorial: segurança em nível de linha dinâmica com modelo da tabela do Analysis Services
Este tutorial apresenta as etapas necessárias para implementar a **segurança em nível de linha** no **Modelo de Tabela do Analysis Services** e mostra como usá-la em um relatório do Power BI. As etapas deste tutorial foram projetadas para permitir que você acompanhe e conheça as etapas necessárias preenchendo um conjunto de dados de exemplo.

Durante este tutorial, as seguintes etapas são descritas detalhadamente, ajudando a entender o que você precisa fazer para implementar a segurança dinâmica em nível de linha com o modelo de tabela do Analysis Services:

* Criar uma nova tabela de segurança no banco de dados **AdventureworksDW2012**
* Criar o modelo de tabela com as tabelas de fatos e dimensões necessárias
* Definir as funções e permissões para os usuários
* Implantar o modelo em uma instância da **tabela do Analysis Services**
* Usar o Power BI Desktop para criar um relatório que exibe os dados correspondentes ao usuário que está acessando o relatório
* Implantar o relatório no **serviço do Power BI**
* Criar um novo dashboard baseado no relatório e, por último,
* Compartilhar o dashboard com seus colegas

Para seguir as etapas deste tutorial, você precisa do banco de dados **AdventureworksDW2012**, que pode ser baixado **[aqui.](http://msftdbprodsamples.codeplex.com/releases/view/55330)**

## <a name="task-1-create-the-user-security-table-and-define-data-relationship"></a>Tarefa 1: Criar a tabela de segurança de usuário e definir a relação de dados
Há vários artigos publicados que descrevem como definir a segurança dinâmica em nível de linha com o modelo de **tabela do SSAS (SQL Server Analysis Services)**. [Para nossa amostra, seguimos este artigo.](https://msdn.microsoft.com/library/hh479759.aspx) As etapas a seguir mostrarão a primeira tarefa deste tutorial.

1. No nosso exemplo, usaremos o banco de dados relacional **AdventureworksDW2012**. Nesse banco de dados, crie a tabela **DimUserSecurity**, conforme mostrado na imagem a seguir. Para esta amostra, estamos usando o SSMS (SQL Server Management Studio) para criar a tabela.
   
   ![](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/createusersecuritytable.png)
2. Depois que a tabela for criada e salva, será necessário criar a relação entre a coluna **SalesTerritoryID** da tabela **DimUserSecurity** e a coluna **SalesTerritoryKey** da tabela **DimSalesTerritory**, como mostrado na imagem a seguir. Faça isto no **SSMS**, clicando com o botão direito do mouse na tabela **DimUserSecurity** e selecionando **Editar**.
   
   ![](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/createusersecuritytable_keys.png)
3. Salve a tabela e adicione algumas linhas de informações do usuário à tabela novamente clicando com o botão direito do mouse na tabela **DimUserSecurity** e selecionando **Editar as 200 primeiras linhas**. Depois de adicionar os usuários, as linhas da tabela **DimUserSecurity** serão parecidas com a seguinte imagem:
   
   ![](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/createusersecuritytable_users.png)
   
   Voltaremos a esses usuários em tarefas futuras.
4. Em seguida, fazemos uma *junção interna* com a tabela **DimSalesTerritory**, que mostra os detalhes da região associados ao usuário. O código a seguir executa a *junção interna*, e a imagem a seguir mostra como a tabela aparece depois que a *junção interna* é bem-sucedida.
   
       **select b.SalesTerritoryCountry, b.SalesTerritoryRegion, a.EmployeeKey, a.FirstName, a.LastName, a.UserName from [dbo].[DimUserSecurity] as a join  [dbo].[DimSalesTerritory] as b on a.[SalesTerritoryKey] = b.[SalesTerritoryKey]**
   
   ![](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/createusersecuritytable_join_users.png)
5. Observe que a imagem acima mostra informações, como qual usuário é responsável por qual região de vendas. Esses dados são exibidos devido à relação que criamos na **Etapa 2**. Além disso, observe que o usuário **Carlos Silva faz parte da região de vendas Austrália**. Voltaremos a Carlos Silva em tarefas e etapas futuras.

## <a name="task-2-create-the-tabular-model-with-facts-and-dimension-tables"></a>Tarefa 2: Criar o modelo de tabela com tabelas de fatos e dimensão
1. Depois de implementar o data warehouse relacional, é hora de definir o modelo de tabela. O modelo pode ser criado usando o **SSDT (SQL Server Data Tools)**. Para obter mais informações sobre como definir um modelo de tabela, [confira este artigo](https://msdn.microsoft.com/library/hh231689.aspx).
2. Importe todas as tabelas necessárias no modelo, conforme mostrado abaixo.
   
    ![](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/ssdt_model.png)
3. Depois de importar as tabelas necessárias, você precisa definir uma função chamada **SalesTerritoryUsers** com a permissão **Leitura**. Faça isto clicando no menu **Modelo** no SQL Server Data Tools e clicando em **Funções**. Na caixa de diálogo **Gerenciador de Funções**, clique em **Novo**.
4. Na guia **Membros** do **Gerenciador de Funções**, adicione os usuários que definimos na tabela **DimUserSecurity**, na **Tarefa 1 – etapa 3**.
   
    ![](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/rolemanager.png)
5. Em seguida, adicione as funções apropriadas para as tabelas **DimSalesTerritory** e **DimUserSecurity**, conforme mostrado abaixo na guia **Filtros de Linha**.
   
    ![](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/rolemanager_complete.png)
6. Nesta etapa, usamos a função **LOOKUPVALUE** para retornar valores de uma coluna na qual o nome de usuário do Windows é o mesmo que o nome de usuário retornado pela função **USERNAME**. As consultas poderão ser restringidas nos casos em que os valores retornados por **LOOKUPVALUE** corresponderem aos valores na mesma tabela ou em uma tabela relacionada. Na coluna **Filtro DAX**, digite a seguinte fórmula:
   
       =DimSalesTerritory[SalesTerritoryKey]=LOOKUPVALUE(DimUserSecurity[SalesTerritoryID], DimUserSecurity[UserName], USERNAME(), DimUserSecurity[SalesTerritoryID], DimSalesTerritory[SalesTerritoryKey])
7. Nesta fórmula, a função **LOOKUPVALUE** retorna todos os valores da coluna **DimUserSecurity[SalesTerritoryID]**, em que o **DimUserSecurity[UserName]** é o mesmo nome de usuário atual do Windows conectado, e a **DimUserSecurity[SalesTerritoryID]** é igual a **DimSalesTerritory[SalesTerritoryKey]**.
   
   O conjunto de SalesTerritoryKeys de Vendas retornado por **LOOKUPVALUE** é usado para restringir as linhas mostradas em **DimSalesTerritory**. Somente as linhas em que **SalesTerritoryKey** da linha estiver no conjunto de IDs retornadas pela função **LOOKUPVALUE** são exibidas.
8. Para a tabela **DimUserSecurity**, na coluna **Filtro DAX**, digite a fórmula a seguir.
   
       =FALSE()
9. Esta fórmula especifica que todas as colunas são resolvidas para a condição booliana false; portanto, nenhuma coluna da tabela **DimUserSecurity** pode ser consultada.
10. Agora, precisamos processar e implantar o modelo. Confira [este artigo](https://msdn.microsoft.com/library/hh231693.aspx) para obter assistência na implantação do modelo.

## <a name="task-3-adding-data-sources-within-your-on-premises-data-gateway"></a>Tarefa 3: adicionando fontes de dados ao Gateway de dados local
1. Depois que o modelo de tabela for implantado e estiver pronto para consumo, você precisará adicionar uma conexão de fonte de dados ao servidor de tabela do Analysis Services local no portal do Power BI.
2. Para permitir que o **serviço do Power BI** acesse o serviço de análise local, é necessário ter um **[Gateway de dados local](service-gateway-onprem.md)** instalado e configurado no seu ambiente.
3. Depois de configurar o gateway corretamente, é necessário criar uma conexão de fonte de dados à instância de tabela do **Analysis Services**. Este artigo o ajudará a [adicionar uma fonte de dados no portal do Power BI](service-gateway-enterprise-manage-ssas.md).
   
   ![](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/pbi_gateway.png)
4. Após a conclusão da etapa anterior, o gateway está configurado e pronto para interagir com sua fonte de dados do **Analysis Services** local.

## <a name="task-4-creating-report-based-on-analysis-services-tabular-model-using-power-bi-desktop"></a>Tarefa 4: Criando relatórios baseados no modelo de tabela do Analysis Services usando o Power BI Desktop
1. Inicie o **Power BI Desktop** e selecione **Obter Dados > Banco de Dados**.
2. Na lista de fontes de dados, selecione o **Banco de Dados do SQL Server Analysis Services** e selecione **Conectar**.
   
   ![](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/getdata.png)
3. Preencha os detalhes da instância de tabela do **Analysis Services** e selecione **Conexão Dinâmica**. Selecione OK. Com o **Power BI**, a segurança dinâmica funciona apenas com a **Conexão dinâmica**.
   
   ![](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/getdata_connectlive.png)
4. Você verá que o modelo foi implantado na instância do **Analysis Services**. Selecione o respectivo modelo e selecione **OK**.
   
   ![](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/getdata_connectlive.png)
5. Agora, o **Power BI Desktop** exibe todos os campos disponíveis à direita da tela no painel **Campos**.
6. No painel **Campos** à direita, selecione a medida **SalesAmount** na tabela **FactInternetSales** e a dimensão **SalesTerritoryRegion** na tabela **SalesTerritory**.
7. Vamos manter esse relatório simples e, por isso, não adicionamos mais nenhuma coluna. Para ter uma representação mais significativa dos dados, vamos alterar a visualização para **Gráfico de rosca**.
   
   ![](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/donut_chart.png)
8. Quando o relatório estiver pronto, você poderá publicá-lo diretamente no portal do Power BI. Na faixa de opções **Página Inicial** do **Power BI Desktop**, selecione **Publicar**.

## <a name="task-5-creating-and-sharing-a-dashboard"></a>Tarefa 5: Criando e compartilhando um dashboard
1. Você criou o relatório e clicou em **Publicar** no **Power BI Desktop**; portanto, o relatório foi publicado no serviço do **Power BI**. Agora que ele está no serviço, nosso cenário de segurança do modelo pode ser demonstrado com o exemplo criado nas etapas anteriores.
   
   Em sua função, o **Gerente de vendas – Pedro** pode ver os dados de todas as diferentes regiões de vendas. Portanto, ele cria esse relatório (o relatório criado nas etapas da tarefa anterior) e o publica no serviço do Power BI.
   
   Depois de publicar o relatório, ele cria um dashboard no serviço do Power BI chamado **TabularDynamicSec** com base no relatório. Na imagem a seguir, observe que o Gerente de vendas (Pedro) consegue ver os dados correspondentes a todas as regiões de vendas.
   
   ![](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/donut_chart_1.png)
2. Agora, Pedro compartilha o dashboard com seu colega, Carlos Silva, responsável pelas vendas na região da Austrália.
   
   ![](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/user_jon_doe.png)
   
   ![](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/pbi_dashboard.png)
3. Quando Carlos Silva fizer logon no serviço do **Power BI** e exibir o dashboard compartilhado criado por Pedro, Carlos Silva deverá ver **somente** as vendas da região pela qual é responsável. Portanto, Carlos Silva faz logon, acessa o dashboard que Pedro compartilhou com ele e Carlos Silva vê **somente** as vendas da região da Austrália.
   
   ![](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/dashboard_jon_doe.png)
4. Parabéns! A segurança dinâmica em nível de linha definida no modelo de tabela do **Analysis Services** local foi refletida com êxito e observada no serviço do **Power BI**. O Power BI usa a propriedade **effectiveusername** para enviar as atuais credenciais de usuário do Power BI à fonte de dados local para executar as consultas.

## <a name="task-6-understanding-what-happens-behind-the-scenes"></a>Tarefa 6: Entendendo o que acontece nos bastidores
1. Esta tarefa pressupõe que você esteja familiarizado com o SQL Profiler, já que você precisa capturar um rastreamento do criador de perfil do SQL Server na instância de tabela do SSAS local.
2. A sessão é inicializada assim que o usuário (Carlos Silva, neste caso) acessa o dashboard no serviço do Power BI. Você pode ver que a função **salesterritoryusers** funciona imediatamente com o nome de usuário efetivo **<EffectiveUserName>jondoe@moonneo.com</EffectiveUserName>**
   
       <PropertyList><Catalog>DefinedSalesTabular</Catalog><Timeout>600</Timeout><Content>SchemaData</Content><Format>Tabular</Format><AxisFormat>TupleFormat</AxisFormat><BeginRange>-1</BeginRange><EndRange>-1</EndRange><ShowHiddenCubes>false</ShowHiddenCubes><VisualMode>0</VisualMode><DbpropMsmdFlattened2>true</DbpropMsmdFlattened2><SspropInitAppName>PowerBI</SspropInitAppName><SecuredCellValue>0</SecuredCellValue><ImpactAnalysis>false</ImpactAnalysis><SQLQueryMode>Calculated</SQLQueryMode><ClientProcessID>6408</ClientProcessID><Cube>Model</Cube><ReturnCellProperties>true</ReturnCellProperties><CommitTimeout>0</CommitTimeout><ForceCommitTimeout>0</ForceCommitTimeout><ExecutionMode>Execute</ExecutionMode><RealTimeOlap>false</RealTimeOlap><MdxMissingMemberMode>Default</MdxMissingMemberMode><DisablePrefetchFacts>false</DisablePrefetchFacts><UpdateIsolationLevel>2</UpdateIsolationLevel><DbpropMsmdOptimizeResponse>0</DbpropMsmdOptimizeResponse><ResponseEncoding>Default</ResponseEncoding><DirectQueryMode>Default</DirectQueryMode><DbpropMsmdActivityID>4ea2a372-dd2f-4edd-a8ca-1b909b4165b5</DbpropMsmdActivityID><DbpropMsmdRequestID>2313cf77-b881-015d-e6da-eda9846d42db</DbpropMsmdRequestID><LocaleIdentifier>1033</LocaleIdentifier><EffectiveUserName>jondoe@moonneo.com</EffectiveUserName></PropertyList>
3. Com base na solicitação de nome de usuário efetivo, o Analysis Services converte a solicitação para a credencial real moonneo\carlossilva depois de consultar o Active Directory local. Depois que o **Analysis Services** obtém a credencial real do Active Directory, em seguida, com base no acesso para o qual o usuário tem permissões nos dados, o **Analysis Services** retorna somente os dados para os quais ele tem permissão.
4. Se outras atividades forem realizadas no dashboard, por exemplo, se Carlos Silva acessar o dashboard e depois o relatório subjacente, com o SQL Profiler, você verá uma consulta específica retornando para o modelo de tabela do Analysis Services como uma consulta DAX.
   
   ![](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/profiler1.png)
5. Você também pode ver abaixo a consulta DAX sendo executada para popular os dados do relatório.
   
   ```
   EVALUATE
     ROW(
       "SumEmployeeKey", CALCULATE(SUM(Employee[EmployeeKey]))
     )
   
   <PropertyList xmlns="urn:schemas-microsoft-com:xml-analysis">``
             <Catalog>DefinedSalesTabular</Catalog>
             <Cube>Model</Cube>
             <SspropInitAppName>PowerBI</SspropInitAppName>
             <EffectiveUserName>jondoe@moonneo.com</EffectiveUserName>
             <LocaleIdentifier>1033</LocaleIdentifier>
             <ClientProcessID>6408</ClientProcessID>
             <Format>Tabular</Format>
             <Content>SchemaData</Content>
             <Timeout>600</Timeout>
             <DbpropMsmdRequestID>8510d758-f07b-a025-8fb3-a0540189ff79</DbpropMsmdRequestID>
             <DbPropMsmdActivityID>f2dbe8a3-ef51-4d70-a879-5f02a502b2c3</DbPropMsmdActivityID>
             <ReturnCellProperties>true</ReturnCellProperties>
             <DbpropMsmdFlattened2>true</DbpropMsmdFlattened2>
             <DbpropMsmdActivityID>f2dbe8a3-ef51-4d70-a879-5f02a502b2c3</DbpropMsmdActivityID>
           </PropertyList>
   ```

## <a name="considerations"></a>Considerações
Há algumas considerações para ter em mente ao trabalhar com a segurança em nível de linha, o SSAS e o Power BI.

1. A segurança em nível de linha local com o Power BI só está disponível com a Conexão Dinâmica.
2. Quaisquer alterações nos dados após o processamento do modelo seriam imediatamente disponibilizadas para os usuários que estão acessando o relatório baseadas na **conexão dinâmica** por meio do serviço do Power BI.

