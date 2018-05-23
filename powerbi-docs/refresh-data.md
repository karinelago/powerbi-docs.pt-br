---
title: Atualizar dados no Power BI
description: Atualizar dados no Power BI
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 05/02/2018
ms.author: davidi
LocalizationGroup: Data refresh
ms.openlocfilehash: 779bfb3e69a76d0fe9e9a34d6576b2054de89cc1
ms.sourcegitcommit: 998b79c0dd46d0e5439888b83999945ed1809c94
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/17/2018
---
# <a name="data-refresh-in-power-bi"></a>Atualizar dados no Power BI
Certificando-se de que sempre obterá os dados mais recentes que costumam ser fundamentais para tomar as decisões corretas. Você provavelmente já usou Obter Dados no Power BI para conectar e carregar alguns dados, criou alguns relatórios e um painel de controle. Agora, você deseja certificar-se de que seus dados são realmente mais recentes e maiores.

Em muitos casos, você não precisa fazer absolutamente nada. Alguns dados, como provenientes do pacote de conteúdo Salesforce ou Marketo são atualizados automaticamente para você. Caso sua conexão utilize uma conexão dinâmica ou o DirectQuery, os dados estarão atualizados até o momento. Mas, em outros casos, como ocorre com uma pasta de trabalho do Excel ou um arquivo do Power BI Desktop que se conecta a uma fonte de dados externa online ou local, você precisará atualizar manualmente ou configurar um agendamento de atualização para o que o Power BI possa atualizar os dados em seus relatórios e dashboards para você.

Neste artigo, juntamente com alguns outros, destinam-se a ajudá-lo a entender como a atualização de dados no Power BI realmente funciona, ou o que não é necessário para configurar uma agenda de atualização e o que precisa ser in-loco para atualizar os dados com êxito.

## <a name="understanding-data-refresh"></a>Entendendo a atualização de dados
Antes de configurar a atualização, é importante entender o que você está atualizando e onde você está obtendo os dados.

Uma *fonte de dados* é onde os dados que você explora em seus relatórios e painéis realmente são provenientes; por exemplo, um serviço online, como Google Analytics ou QuickBooks, um banco de dados na nuvem como banco de dados do SQL Azure, ou um banco de dados ou arquivo em um computador local ou servidor em sua própria organização. Essas são todas as fontes de dados. O tipo de fonte de dados determina como os dados são atualizados. Passaremos a atualização para cada tipo de fonte de dados em [O que pode ser atualizado?](#what-can-be-refreshed) seção.

Um *conjunto de dados* é criado automaticamente no Power BI, quando você usa Obter Dados para se conectar ao e carregar dados de um pacote de conteúdo, arquivo ou se conectar a uma fonte de dados ao vivo. No Power BI Desktop e Excel 2016, também é possível publicar seu arquivo direitamente no serviço do Power BI, que é semelhante ao uso do recurso Obter Dados.

Em cada caso, um conjunto de dados é criado e exibido nos contêineres Meu Espaço de Trabalho ou Grupo do serviço do Power BI. Ao selecionar as **reticências (...)**, é possível explorar os dados em um relatório, editar as configurações e configurar a atualização.

![](media/refresh-data/dataset-menu.png)

Um conjunto de dados pode obter dados de uma ou mais fontes de dados. Por exemplo, você pode usar a área de trabalho do Power BI para obter dados de um banco de dados SQL em sua organização e obter outros dados de online do feed OData. Em seguida, ao publicar o arquivo para o Power BI, um único conjunto de dados é criado, mas ele terá fontes de dados para o banco de dados SQL e o feed OData.

Um conjunto de dados contém informações sobre as fontes de dados, credenciais de fonte de dados, e na maioria dos casos, um sub conjunto de dados copiados da fonte de dados. Ao criar visualizações em relatórios e dashboards, você observa os dados no conjunto de dados ou, no caso de uma conexão dinâmica com o Banco de Dados SQL do Azure, o conjunto de dados define os dados que você verá diretamente por meio da fonte de dados. Para uma conexão dinâmica com o Analysis Services, a definição do conjunto de dados é recebida diretamente do Analysis Services.

> *Ao atualizar os dados, você está atualizando os dados no conjunto de dados que é armazenado no Power BI por meio da fonte de dados. Essa atualização é uma atualização completa e não incremental.*
> 
> 

Sempre que você atualizar os dados em um conjunto de dados, ao usar Atualizar Agora ou configurar uma agenda de atualização, o Power BI usa informações do conjunto de dados para se conectar às fontes de dados definidas para ela, consultar para dados atualizados, e em seguida, carrega os dados atualizados no conjunto de dados. Qualquer visualizações em seus relatórios ou painéis baseados nos dados são atualizadas automaticamente.

Antes de continuarmos, precisamos abordar algo que é muito importante compreender:

> *Independentemente da frequência com que você atualiza o conjunto de dados ou examina dados dinâmicos, são os dados na fonte de dados que devem estar atualizados primeiro.*
> 
> 

A maioria das organizações processa os dados uma vez por dia, geralmente durante a noite. Se você agendara atualização de um conjunto de dados criado a partir de um arquivo do Power BI Desktop que conecta a um banco de dados local e seu departamento de TI executa o processamento naquele banco de dados SQL, uma vez durante a noite, você só precisa configurara  atualização agendada para ser executada uma vez por dia. Por exemplo, após o processamento do banco de dados ocorrer, mas antes de você entrar no trabalho. É claro que isso nem sempre é o caso. O Power BI fornece várias maneiras de se conectar a fontes de dados que são atualizadas com frequência ou até mesmo em tempo real.

## <a name="types-of-refresh"></a>Tipos de atualização
Há quatro tipos principais de atualização que ocorrem no Power BI. Atualização de pacotes, atualização de modelo/dados, atualização de blocos e atualização de contêineres de visuais.

### <a name="package-refresh"></a>Atualização de pacotes
Isso sincroniza o arquivo do Power BI Desktop ou do Excel entre o serviço do Power BI e o OneDrive ou SharePoint Online. Isso não efetua pull de dados da fonte de dados original. O conjunto de dados no Power BI só será atualizado com o conteúdo dfo arquivo no OneDrive ou SharePoint Online.

![](media/refresh-data/package-refresh.png)

### <a name="modeldata-refresh"></a>Atualização de dados/modelo
Isso se refere à atualização do conjunto de dados, no serviço do Power BI, com dados da fonte de dados original. Isso é feito por meio da atualização agendada ou do recurso Atualizar Agora. Isso exige um gateway para fontes de dados locais.

### <a name="tile-refresh"></a>Atualização de bloco
A atualização de blocos atualiza o cache dos visuais do bloco, no dashboard, após as alterações de dados. Isso ocorre, aproximadamente, a cada quinze minutos. Também é possível forçar uma atualização do bloco selecionando as **reticências (...)** no canto superior direito de um dashboard e selecionando **Atualizar os blocos de dashboard**.

![](media/refresh-data/dashboard-tile-refresh.png)

Para obter detalhes sobre os erros comuns de atualização de bloco, veja [Solucionar problemas de erros de bloco](refresh-troubleshooting-tile-errors.md).

### <a name="visual-container-refresh"></a>Atualização de contêineres de visuais
A atualização do contêiner de visuais atualiza também os visuais do relatório armazenados em cache, em um relatório, após as alterações de dados.

## <a name="what-can-be-refreshed"></a>O que pode ser atualizado?
No Power BI, normalmente, você usará Obter Dados para importar dados de um arquivo em uma unidade local, no OneDrive ou SharePoint Online, publicar um relatório por meio do Power BI Desktop ou conectar-se diretamente a um banco de dados na nuvem em sua própria organização. Praticamente, quaisquer dados no Power BI podem ser atualizados, mas saber se isso será necessário dependerá de se o conjunto de dados foi criado por meio de fontes de dados e das fontes de dados às quais ele se conecta. Vamos ver como cada um atualiza os dados.

Antes de ir adiante, aqui estão algumas definições importantes para entender:

**Atualização automática**  -  significa que nenhuma configuração de usuário é necessária para o conjunto de dados a ser atualizado regularmente. As configurações de atualização de dados são configuradas para você pelo Power BI. Para provedores de serviços online, a atualização normalmente ocorre uma vez por dia. Para arquivos carregados a partir do OneDrive, a atualização automática ocorre sobre a cada hora por dados que não seja proveniente de uma fonte de dados externa. Enquanto você pode definir as configurações de atualização de agenda diferentes e atualizar manualmente, você provavelmente não precisará.

**Atualização manual ou agendada configurada pelo usuário** – isso significa que você pode atualizar um conjunto de dados usando Atualizar agora manualmente ou configurar uma atualização agendada usando Atualizar programação em configurações do conjunto de dados. Esse tipo de atualização é necessário para arquivos de área de trabalho do Power BI e pastas de trabalho do Excel que se conectam a fontes de dados locais e online externas.

> [!NOTE]
> Quando você configura um horário para a atualização agendada, pode haver um atraso de até uma hora antes do início da atualização.
> 
> 

**Live/DirectQuery** – Isso significa que há uma conexão dinâmica entre Power BI e a fonte de dados. Para fontes de dados locais, os Administradores precisarão ter uma fonte de dados configurada em um gateway corporativo, porém, a interação do usuário pode não ser necessária.

> [!NOTE]
> Para melhorar o desempenho, os dashboards com os dados conectados usando o DirectQuery são atualizados automaticamente. Você também pode atualizar manualmente um bloco a qualquer momento, usando o menu **Mais** no bloco.
> 
> 

## <a name="local-files-and-files-on-onedrive-or-sharepoint-online"></a>Arquivos locais e arquivos no OneDrive ou SharePoint Online
A atualização de dados é suportada para arquivos do Power Bi Desktop e pastas de trabalho do Excel que se conectam a fontes de dados locais ou online externas. Isso atualizará apenas os dados do conjunto de dados no serviço do Power BI. Não atualizará o arquivo local.

Manter seus arquivos no OneDrive ou SharePoint Online e se conectar a eles por meio do Power BI é um meio de fornecer uma grande quantidade de flexibilidade. Mas com toda essa flexibilidade, também se torna uma das mais desafiadores de entender. A atualização agendada para os arquivos armazenados no OneDrive ou SharePoint Online é diferente da atualização de pacotes. É possível saber mais na seção [Tipos de atualização](#types-of-refresh).

### <a name="power-bi-desktop-file"></a>Arquivo do Power BI Desktop
| **Fonte de dados** | **Atualização automática** | **Atualização manual ou agendada configurada pelo usuário** | **Gateway necessário** |
| --- | --- | --- | --- |
| Obter Dados (na faixa de opções) é usado para conectar e consultar dados de qualquer fonte de dados online listados. |Não |Sim |Não (veja abaixo) |
| O recurso Obter Dados é usado para se conectar a um banco de dados dinâmico do Analysis Services e explorá-lo. |Sim |Não |Sim |
| O recurso Obter Dados é usado para se conectar a uma fonte de dados local do DirectQuery com suporte e explorá-la. |Sim |Não |Sim |
| Obter Dados é usado para conectar e consultar dados a partir de um Spark do Azure SQL Database, Azure SQL Data Warehouse, Azure HDInsight. |Sim |Sim |Não |
| O recurso Obter Dados é usado para se conectar a dados de qualquer fonte de dados local listada e explorá-los, exceto o arquivo do Hadoop (HDFS) e o Microsoft Exchange. |Não |Sim |Sim |

> [!NOTE]
> Se estiver usando a função [**Web.Page**](https://msdn.microsoft.com/library/mt260924.aspx), você precisará de um gateway se tiver republicado o conjunto de dados ou o relatório após 18 de novembro de 2016.
> 
> 

Para obter detalhes, veja [Atualizar um conjunto de dados criado com base em um arquivo do Power BI Desktop no OneDrive](refresh-desktop-file-onedrive.md).

### <a name="excel-workbook"></a>Pasta de trabalho do Excel
| **Fonte de dados** | **Atualização automática** | **Atualização manual ou agendada configurada pelo usuário** | **Gateway necessário** |
| --- | --- | --- | --- |
| Tabelas de dados em uma planilha não carregadas no modelo de dados Excel |Sim, por hora *(somente OneDrive/SharePointOnline)* |Somente manual *(somente OneDrive/SharePoint Online)* |Não |
| Tabelas de dados em uma planilha vinculada a uma tabela no modelo de dados do Excel (tabelas vinculadas). |Sim, por hora *(somente OneDrive/SharePoint Online)* |Somente manual *(somente OneDrive/SharePoint Online)* |Não |
| Power Query* é usada para se conectar e consultar dados de qualquer fonte de dados online listada e carregar dados para o modelo de dados do Excel. |Não |Sim |Não |
| O Power Query* é usado para carregar dados no modelo de dados do Excel e para conectar-se a e consultar dados de qualquer fonte de dados listada local, exceto o arquivo do Hadoop (HDFS) e o Microsoft Exchange. |Não |Sim |Sim |
| Power Pivot é usada para se conectar e consultar dados de qualquer fonte de dados online listada e carregar dados para o modelo de dados do Excel. |Não |Sim |Não |
| Power Pivot* é usada para se conectar e consultar dados de qualquer fonte de dados no local listada e carregar dados para o modelo de dados do Excel. |Não |Sim |Sim |

*\* Power Query é conhecida como Obter & transformar dados no Excel 2016.*

Para obter informações mais detalhadas, veja [Atualizar um conjunto de dados criado com base em uma pasta do Excel no OneDrive](refresh-excel-file-onedrive.md).

### <a name="comma-separated-value-csv-file-on-onedrive-or-sharepoint-online"></a>Arquivo .csv (valores separados por vírgula) no OneDrive ou SharePoint Online
| **Fonte de dados** | **Atualização automática** | **Atualização manual ou agendada configurada pelo usuário** | **Gateway necessário** |
| --- | --- | --- | --- |
| Valor separado por vírgulas simples |Sim, por hora |Apenas manual |Não |

Para obter informações mais detalhadas, veja [Atualizar um conjunto de dados criado com base em um arquivo .csv (valores separados por vírgula) no OneDrive](refresh-csv-file-onedrive.md).

## <a name="content-packs"></a>Pacotes de Conteúdo
Há dois tipos de pacotes de conteúdo no Power BI:

**Pacotes de conteúdo dos serviços online**: como Adobe Analytics, SalesForce e Dynamics CRM Online. Conjuntos de dados criados a partir de serviços online são atualizados automaticamente uma vez por dia. Embora provavelmente não seja necessário, você pode atualizar manualmente ou configurar uma agenda de atualização. Como os serviços online estão na nuvem, um gateway não é necessário.

**Pacotes de conteúdo organizacionais**: criados e compartilhados por usuários em sua organização. Os consumidores de conteúdo do pacote não podem configurar para atualizar uma programação ou atualizar manualmente. Apenas o criador do conteúdo do pacote pode configurar a atualização para os conjuntos de dados no pacote de conteúdo. Atualizar as configurações são herdadas com o conjunto de dados.

### <a name="content-packs-from-online-services"></a>Pacotes de conteúdo de serviços online
| **Fonte de dados** | **Atualização automática** | **Atualização manual ou agendada configurada pelo usuário** | **Gateway necessário** |
| --- | --- | --- | --- |
| Serviços online em Obter Dados &gt; Serviços |Sim |Sim |Não |

### <a name="organizational-content-packs"></a>Pacotes de conteúdo organizacional
As funcionalidades de atualização de um conjunto de dados incluídas em um pacote de conteúdo organizacional dependem do conjunto de dados. Veja as informações acima em relação aos arquivos locais, OneDrive ou SharePoint Online.

Para saber mais, veja [Introdução aos pacotes de conteúdo organizacional](service-organizational-content-pack-introduction.md).

## <a name="live-connections-and-directquery-to-on-premises-data-sources"></a>Conexões dinâmicas e DirectQuery para fontes de dados locais
Com o gateway de dados local, é possível emitir consultas do Power BI para fontes de dados locais. Quando você interage com uma visualização, as consultas são enviadas do Power BI diretamente para o banco de dados. Os dados atualizados são retornados e as visualizações são atualizadas. Como há uma conexão direta entre o Power BI e o banco de dados, não é necessário atualizar programar a atualização.

Ao conectar-se a uma fonte de dados do SSAS (SQL Server Analysis Services) usando uma conexão dinâmica, diferentemente do DirectQuery, a conexão dinâmica com uma fonte do SSAS pode ser executada no cache, mesmo após um relatório ser carregado. Esse comportamento melhora o desempenho da carga para o relatório. É possível solicitar os dados mais recentes da fonte de dados do SSAS usando o botão **atualizar**. Os proprietários das fontes de dados do SSAS podem configurar a frequência de atualização agendada do cache para o conjunto de dados para garantir que os relatórios estejam tão atualizados quanto seja necessário. 

Ao configurar uma fonte de dados com o gateway de dados local, é possível usar essa fonte de dados como a opção de atualização agendada. Isso seria usado em vez do gateway pessoal.

> [!NOTE]
> Se o conjunto de dados estiver configurado para uma conexão dinâmica ou DirectQuery, os conjuntos de dados serão atualizados aproximadamente a cada hora ou quando ocorrer a interação com os dados. Você pode ajustar manualmente a *frequência de atualização* na opção *Atualização do cache agendada*, no serviço do Power BI.
> 
> 

| **Fonte de dados** | **Live/DirectQuery** | **Atualização manual ou agendada configurada pelo usuário** | **Gateway necessário** |
| --- | --- | --- | --- |
| Tabela do Analysis Services |Sim |Sim |Sim |
| Multidimensional do Analysis Services |Sim |Sim |Sim |
| SQL Server |Sim |Sim |Sim |
| SAP HANA |Sim |Sim |Sim |
| Oracle |Sim |Sim |Sim |
| Teradata |Sim |Sim |Sim |

Para obter mais informações, veja [Gateway de dados local](service-gateway-onprem.md)

## <a name="databases-in-the-cloud"></a>Bancos de dados na nuvem
Com o DirectQuery, há uma conexão dinâmica entre o Power BI e o banco de dados na nuvem. Quando você interage com uma visualização, as consultas são enviadas do Power BI diretamente para o banco de dados. Os dados atualizados são retornados e as visualizações são atualizadas. E, como o serviço do Power BI e a fonte de dados estão na nuvem, não é necessário  um Gateway de Pessoal.

Se não houver nenhuma interação do usuário em uma visualização, os dados serão atualizados automaticamente, aproximadamente a cada hora. Você pode alterar essa frequência de atualização usando a opção *Atualização do cache agendada* e definir a frequência de atualização.

Para definir a frequência, selecione o ícone **engrenagem** no canto superior direito do serviço do Power BI e escolha **Configurações**.

![](media/refresh-data/refresh-data_2.png)

A página **Configurações** será exibida, permitindo selecionar o conjunto de dados para o qual deseja ajustar a frequência. Nessa página, selecione a guia **Conjuntos de dados** na parte superior.

![](media/refresh-data/refresh-data_3.png)

Selecione o conjunto de dados e, no painel direito, aparecerá uma coleção de opções para esse conjunto de dados. Para a conexão Dinâmica/DirectQuery, você pode definir a frequência de atualização desde 15 minutos até semanal, usando o menu suspenso associado, conforme é mostrado na imagem a seguir.

![](media/refresh-data/refresh-data_1.png)

| **Fonte de dados** | **Live/DirectQuery** | **Atualização manual ou agendada configurada pelo usuário** | **Gateway necessário** |
| --- | --- | --- | --- |
| SQL Azure Data Warehouse |Sim |Sim |Não |
| Sparks no HDInsight |Sim |Sim |Não |

Para saber mais, veja [Azure e Power BI](service-azure-and-power-bi.md).

## <a name="real-time-dashboards"></a>Painéis em tempo real
Os dashboards em tempo real usam a API REST do Microsoft Power BI ou o Microsoft Stream Analytics para garantir que os dados estão atualizados. Uma vez que os painéis em tempo real não exigem que os usuários configurarem a atualização, eles estão fora do escopo deste artigo.

| **Fonte de dados** | **Automático** | **Atualização manual ou agendada configurada pelo usuário** | **Gateway necessário** |
| --- | --- | --- | --- |
| Aplicativos personalizados desenvolvidos com o API Rest do Power BI ou  Microsoft Stream Analytics |Sim, transmissão ao vivo |Não |Não |

Para obter mais informações, veja [Criar um dashboard em tempo real no Power BI](https://msdn.microsoft.com/library/mt267603.aspx).

## <a name="configure-scheduled-refresh"></a>Configurar a atualização agendada
Para saber como configurar a atualização agendada, veja [Configurar a atualização agendada](refresh-scheduled-refresh.md)

## <a name="common-data-refresh-scenarios"></a>Cenários de atualização de dados comuns
Às vezes, a melhor maneira de aprender sobre a atualização de dados no Power BI é ver exemplos. Aqui estão alguns dos cenários de atualização de dados mais comuns:

### <a name="excel-workbook-with-tables-of-data"></a>Pasta de trabalho do Excel com tabelas de dados
Você tem uma pasta de trabalho do Excel com várias tabelas de dados, mas nenhuma delas são carregadas no modelo de dados do Excel. Use Obter Dados para carregar o arquivo de pasta de trabalho de sua unidade local no Power BI e criar um painel de controle. Mas, agora você fez algumas alterações em algumas tabelas da pasta de trabalho em sua unidade local, e você deseja atualizar o painel no Power BI com os novos dados.

Infelizmente, a atualização não é suportada neste cenário. Para atualizar o conjunto de dados para o seu painel, você precisará carregar novamente a pasta de trabalho. No entanto, há uma excelente solução: colocar o arquivo de pasta de trabalho no OneDrive ou SharePoint Online!

Quando você se conectar a um arquivo no OneDrive ou SharePoint Online, os relatórios e dashboards mostrarão os dados como estão no arquivo. Neste caso, sua pasta do Excel. O Power BI verifica automaticamente se há atualizações ao arquivo em intervalos aproximados de sessenta minutos. Se você fizer alterações à pasta de trabalho (armazenada no OneDrive ou SharePoint Online), essas alterações serão refletidas no dashboard e os relatórios em menos uma hora. Você não precisa de instalação de atualização. No entanto, se você precisar ver suas atualizações no Power BI imediatamente, você pode atualizar manualmente o conjunto de dados usando Atualizar Agora.

Para saber mais, consulte [Dados de Excel no Power BI](service-excel-workbook-files.md) ou [Atualizar um conjunto de dados criado com base em uma pasta de trabalho do Excel no OneDrive](refresh-excel-file-onedrive.md).

### <a name="excel-workbook-connects-to-a-sql-database-in-your-company"></a>A pasta de trabalho do Excel se conecta a um banco de dados SQL em sua empresa
Digamos que você tenha uma planilha do Excel denominada SalesReport.xlsx no computador local. Power Query no Excel foi usada para se conectar a um banco de dados SQL em um servidor em sua empresa e consultar dados de vendas que são carregados no modelo de dados. Todas as manhãs, abra a pasta de trabalho e clique em atualizar para atualizar suas PivotTables.

Agora que você quer explorar seus dados de vendas no Power BI para usar Obter Dados para conectar e carregar a pasta de trabalho SalesReport.xlsx de sua unidade local.

Nesse caso, manualmente pode atualizar os dados no conjunto de dados SalesReport.xlsx ou configurar uma agenda de atualização. Visto que os dados são, de fato, recebidos do banco de dados SQL em sua empresa, você precisará baixar e instalar um gateway. Depois de instalado e configurado o gateway, você precisará entrar nas configurações do conjunto de dados SalesReport e inscrever-se à fonte de dados; mas você só precisa fazer isso uma vez. Você pode então configurar uma atualização de programação para que o Power BI se conecte automaticamente ao banco de dados do SQL e obtenha dados atualizados. Os relatórios e painéis também serão atualizados automaticamente.

> [!NOTE]
> Isso atualizará apenas os dados no conjunto de dados no serviço do Power BI. O arquivo local não será atualizado como parte da atualização.
> 
> 

Para obter mais informações, veja [Dados do Excel no Power BI](service-excel-workbook-files.md), [Power BI Gateway – Personal](personal-gateway.md), [Gateway de dados local](service-gateway-onprem.md) e [Atualizar um conjunto de dados criado com base em uma pasta de trabalho do Excel em uma unidade local](refresh-excel-file-local-drive.md).

### <a name="power-bi-desktop-file-with-data-from-an-odata-feed"></a>Arquivo do Power BI Desktop com dados a partir de um feed OData
Nesse caso, você usa Obter Dados na área de trabalho do Power BI para conectar e importar dados de censo de um feed OData.  Criar vários relatórios na área de trabalho do Power BI, em seguida, nomeie o arquivo WACensus e salvá-lo em um compartilhamento em sua empresa. Em seguida, você publica o arquivo no serviço do Power BI.

Nesse caso, manualmente pode atualizar os dados no conjunto de dados WACensus ou configurar uma agenda de atualização. Como os dados na fonte de dados são recebidos de um feed online OData, não é necessário instalar um gateway; no entanto, você precisará ir para as configurações do conjunto de dados do WACensus e entrar na fonte de dados do OData. Você pode então configurar uma atualização de programação para que o Power BI se conecte automaticamente ao feed do OData e obter os dados atualizados. Os relatórios e painéis também serão atualizados automaticamente.

Para saber mais, veja [Publicar por meio do Power BI Desktop](desktop-upload-desktop-files.md), [Atualizar um conjunto de dados criado com base em um arquivo do Power BI Desktop em uma unidade local](refresh-desktop-file-local-drive.md) e [Atualizar um conjunto de dados criado com base em um arquivo do Power BI Desktop no OneDrive](refresh-desktop-file-onedrive.md).

### <a name="shared-content-pack-from-another-user-in-your-organization"></a>Pacote de conteúdo compartilhado a partir de outro usuário em nossa organização.
Você se conectou a um pacote de conteúdo organizacional. Isso inclui um painel, vários relatórios e um conjunto de dados.

Nesse cenário, você não pode configurar a atualização ao conjunto de dados. Analistas de dados que criou o pacote de conteúdo é responsável por verificar se o conjunto de dados é atualizado, dependendo das fontes de dados usadas.

Se os seus painéis e relatórios do pacote de conteúdo não estiver atualizados, você deverá conversar com o analista de dados que criou o pacote de conteúdo.

Para saber mais, veja [Introdução aos pacotes de conteúdo organizacional](service-organizational-content-pack-introduction.md) e [Trabalhar com pacotes de conteúdo organizacional](service-organizational-content-pack-copy-refresh-access.md).

### <a name="content-pack-from-an-online-service-provider-like-salesforce"></a>Pacote de conteúdo de um provedor de serviços online como o Salesforce
No Power BI, você usou Obter Dados para se conectar a seus dados e importá-los de um provedor de serviços online como o Salesforce. Bem, não há muito o que fazer aqui. O seu conjunto de dados do Salesforce é atualizado automaticamente para atualizar uma vez por dia. 

Como a maioria dos provedores de serviços, o Salesforce atualiza os dados uma vez por dia, geralmente à noite. Você pode atualizar manualmente seu conjunto de dados do Salesforce ou configurar uma agenda de atualização, mas não é necessário porque o Power BI atualizará automaticamente o conjunto de dados e os relatórios e painéis também são atualizados.

Para saber mais, veja [Pacote de conteúdo do Salesforce para o Power BI](service-connect-to-salesforce.md).

## <a name="troubleshooting"></a>Solução de problemas
Quando as coisas dão errado, normalmente, isso se deve ao fato de o Power BI não conseguir entrar em fontes de dados. Outra razão é que se o conjunto de dados se conecta a uma fonte de dados local, o gateway fica offline. Verifique se o Power BI pode entrar em fontes de dados. Se uma senha que você usa para entrar em uma fonte de dados for alterada ou o Power BI for desconectado de uma fonte de dados, certifique-se de tentar entrar novamente em suas fontes de dados novamente nas Credenciais da Fonte de Dados.

Para obter mais informações sobre como solucionar problemas, veja [Ferramentas para solucionar problemas de atualização](service-gateway-onprem-tshoot.md) e [Cenários de solução de problemas de atualização](refresh-troubleshooting-refresh-scenarios.md).

## <a name="next-steps"></a>Próximas etapas
[Ferramentas para solucionar problemas de atualização](service-gateway-onprem-tshoot.md)  
[Solucionar problemas de atualização](refresh-troubleshooting-refresh-scenarios.md)  
[Gateway do Power BI – Pessoal](personal-gateway.md)  
[Gateway de dados local](service-gateway-onprem.md)  

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](http://community.powerbi.com/)

