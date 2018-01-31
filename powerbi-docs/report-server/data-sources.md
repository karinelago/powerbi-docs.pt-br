---
title: "Fontes de dados de relatórios do Power BI no Servidor de Relatórios do Power BI"
description: "Os relatórios do Power BI podem conectar-se a fontes de dados diferentes. Dependendo de como os dados são usados, fontes de dados diferentes estão disponíveis."
services: powerbi
documentationcenter: 
author: markingmyname
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
ms.date: 11/01/2017
ms.author: maghan
ms.openlocfilehash: caa45aab2c31974abb041a82eb2216ebee2eb148
ms.sourcegitcommit: 6e693f9caf98385a2c45890cd0fbf2403f0dbb8a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2018
---
# <a name="power-bi-report-data-sources-in-power-bi-report-server"></a>Fontes de dados de relatórios do Power BI no Servidor de Relatórios do Power BI
Os relatórios do Power BI podem conectar-se a fontes de dados diferentes. Dependendo de como os dados são usados, fontes de dados diferentes estão disponíveis. Os dados podem ser importados ou consultados diretamente usando o DirectQuery ou uma conexão dinâmica ao SQL Server Analysis Services.

Essas fontes de dados são específicas aos relatórios do Power BI usados no Servidor de Relatórios do Power BI. Para obter informações sobre fontes de dados compatíveis com relatórios paginados, consulte [Fontes de dados com suporte no Reporting Services](https://docs.microsoft.com/sql/reporting-services/report-data/data-sources-supported-by-reporting-services-ssrs).

> [!IMPORTANT]
> Todas as fontes de dados em um relatório do Power BI Desktop devem ser compatíveis para configuração da atualização agendada.
> 
> 

## <a name="list-of-supported-data-sources"></a>Lista de fontes de dados compatíveis
Outras fontes de dados podem funcionar mesmo que não estejam na lista de compatibilidade.

| **Fonte de dados** | **Dados armazenados em cache** | **Atualização agendada** | **Live/DirectQuery** |
| --- | --- | --- | --- |
| Banco de dados do SQL Server |Sim |Sim |Sim |
| SQL Server Analysis Services |Sim |Sim |Sim |
| Banco de dados SQL do Azure |Sim |Sim |Sim |
| SQL Data Warehouse do Azure |Sim |Sim |Sim |
| Excel |Sim |Sim |Não |
| Banco de dados do Access |Sim |Sim |Não |
| Active Directory |Sim |Sim |Não |
| Amazon Redshift |Sim |Não |Não |
| Armazenamento de Blobs do Azure |Sim |Sim |Não |
| Azure Data Lake Store |Sim |Não |Não |
| Azure HDInsight (HDFS) |Sim |Sim |Não |
| Azure HDInsight (Spark) |Sim |Sim |Não |
| Armazenamento de Tabelas do Azure |Sim |Sim |Não |
| Dynamics 365 (online) |Sim |Não |Não |
| Facebook |Sim |Não |Não |
| Pasta |Sim |Sim |Não |
| Google Analytics |Sim |Não |Não |
| HDFS (Arquivo do Hadoop) |Sim |Não |Não |
| Banco de dados IBM DB2 |Sim |Sim |Não |
| Impala |Sim |Não |Não |
| JSON |Sim |Sim |Não |
| Microsoft Exchange |Sim |Não |Não |
| Microsoft Exchange Online |Sim |Não |Não |
| Banco de dados MySQL |Sim |Sim |Não |
| Feed OData |Sim |Sim |Não |
| ODBC |Sim |Sim |Não |
| OLE DB |Sim |Sim |Não |
| Banco de dados Oracle |Sim |Sim |Sim |
| Banco de dados PostgreSQL |Sim |Sim |Não |
| Serviço do Power BI |Não |Não |Não |
| Script do R |Sim |Não |Não |
| Objetos do Salesforce |Sim |Não |Não |
| Relatórios do Salesforce |Sim |Não |Não |
| Servidor do SAP Business Warehouse |Sim |Sim |Sim |
| Banco de dados do SAP HANA |Sim |Sim |Sim |
| Pasta do SharePoint (local) |Sim |Sim |Não |
| Lista do SharePoint (local) |Sim |Sim |Não |
| Lista do SharePoint Online |Sim |Não |Não |
| Snowflake |Sim |Não |Não |
| Banco de dados Sybase |Sim |Sim |Não |
| Banco de dados Teradata |Sim |Sim |Sim |
| Texto/CSV |Sim |Sim |Não |
| Web |Sim |Sim |Não |
| XML |Sim |Sim |Não |
| appFigures (Beta) |Sim |Não |Não |
| Banco de dados do Analysis Services do Azure (Beta) |Sim |Não |Não |
| Azure Cosmos DB (Beta) |Sim |Não |Não |
| Azure HDInsight Spark (Beta) |Sim |Não |Não |
| Common Data Service (Beta) |Sim |Não |Não |
| comScore Digital Analytix (Beta) |Sim |Não |Não |
| Dynamics 365 para Customer Insights (Beta) |Sim |Não |Não |
| Dynamics 365 for Financials (Beta) |Sim |Não |Não |
| GitHub (Beta) |Sim |Não |Não |
| Google BigQuery (Beta) |Sim |Não |Não |
| Banco de dados IBM Informix (Beta) |Sim |Não |Não |
| IBM Netezza (Beta) |Sim |Não |Não |
| Kusto (Beta) |Sim |Não |Não |
| MailChimp (Beta) |Sim |Não |Não |
| Microsoft Azure Consumption Insights (Beta) |Sim |Não |Não |
| Mixpanel (Beta) |Sim |Não |Não |
| Planview Enterprise (Beta) |Sim |Não |Não |
| Projectplace (Beta) |Sim |Não |Não |
| QuickBooks Online (Beta) |Sim |Não |Não |
| Smartsheet |Sim |Não |Não |
| Spark (Beta) |Sim |Não |Não |
| SparkPost (Beta) |Sim |Não |Não |
| SQL Sentry (Beta) |Sim |Não |Não |
| Stripe (Beta) |Sim |Não |Não |
| SweetIQ (Beta) |Sim |Não |Não |
| Troux (Beta) |Sim |Não |Não |
| Twilio (Beta) |Sim |Não |Não |
| tyGraph (Beta) |Sim |Não |Não |
| Vertica (Beta) |Sim |Não |Não |
| Visual Studio Team Services (Beta) |Sim |Não |Não |
| Webtrends (Beta) |Sim |Não |Não |
| ZenDesk (Beta) |Sim |Não |Não |

> [!IMPORTANT]
> A segurança de nível de linha configurada na fonte de dados deve funcionar para determinadas conexões dinâmicas e do DirectQuery (SQL Server, Banco de Dados SQL do Azure, Oracle e Teradata) considerando que o Kerberos esteja configurado adequadamente no ambiente.
> 
> 

## <a name="next-steps"></a>Próximas etapas
Agora que você escolheu a fonte de dados, [crie um relatório](quickstart-create-powerbi-report.md) usando os dados dela.

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)

