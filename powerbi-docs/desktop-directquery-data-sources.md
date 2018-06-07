---
title: Fontes de dados com suporte do DirectQuery no Power BI
description: Obtenha uma lista de quais fontes de dados podem usar o DirectQuery.
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 06/02/2018
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 55d6259c3ae044d395bd0b077577856dd88ff43c
ms.sourcegitcommit: 80d6b45eb84243e801b60b9038b9bff77c30d5c8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34720755"
---
# <a name="data-sources-supported-by-directquery-in-power-bi"></a>Fontes de dados com suporte do DirectQuery no Power BI
O **Power BI Desktop** e o **serviço do Power BI** têm várias fontes de dados às quais você pode se conectar para obter acesso aos dados. Este artigo descreve quais fontes de dados do Power BI dão suporte ao método de conexão conhecido como **DirectQuery**. Para obter mais informações sobre o DirectQuery, consulte [**DirectQuery no Power BI**](desktop-directquery-about.md).

As seguintes fontes de dados dão suporte ao DirectQuery no Power BI:

* Amazon Redshift
* Azure HDInsight Spark (Beta)
* Banco de dados SQL do Azure
* SQL Data Warehouse do Azure
* Google BigQuery (Beta)
* IBM Netezza (Beta)
* Impala (versão 2.x)
* Banco de Dados Oracle (versão 12 e posterior)
* Servidor de Aplicativos SAP Business Warehouse
* Servidor de Mensagens SAP Business Warehouse (Beta)
* SAP HANA
* Snowflake
* Spark (Beta) (versão 0.9 e posterior)
* SQL Server
* Banco de dados Teradata
* Vertica (Beta)

Fontes de dados que têm **(Beta)** ou **(Versão prévia)** depois do nome estão sujeitos a alterações e não há suporte para seu uso em produção. É possível que também não haja suporte para eles após publicar um relatório no **serviço do Power BI**, o que significa que abrir um relatório publicado ou explorar o conjunto de dados pode resultar em um erro.

A única diferença entre fontes de dados **(Beta)** e em **(Versão prévia)** é que as fontes em **(Versão prévia)** precisam ser habilitadas como um recurso de versão prévia antes que fiquem disponíveis para uso. Para habilitar um conector de dados em **(Versão prévia)**, no **Power BI Desktop**, acesse **Arquivo > Opções e Configurações > Opções** e, em seguida, **Recursos de versão prévia**.

> [!NOTE]
> Consultas DirectQuery para SQL Server requerem autenticação usando as credenciais de autenticação atuais do Windows ou credenciais de banco de dados para estabelecer o acesso. Credenciais alternativas não são compatíveis.
>

## <a name="on-premises-gateway-requirements"></a>Requisitos de gateway local
A tabela a seguir especifica se um **Gateway de dados local** é necessário para se conectar à fonte de dados especificada após publicar um relatório no **serviço do Power BI**.

| Fonte | Gateway necessário? |
| --- | --- |
| SQL Server |Sim |
| Banco de dados SQL do Azure |Não |
| SQL Data Warehouse do Azure |Não |
| SAP HANA |Sim |
| Banco de dados Oracle |Sim |
| Banco de dados Teradata |Sim |
| Amazon Redshift |Não |
| Impala (versão 2.x) |Sim |
| Snowflake |Sim |
| Spark (beta), versão 0.9 e posterior |Ainda não tem suporte no **serviço do Power BI** |
| Azure HDInsight Spark (Beta) |Não |
| IBM Netezza |Sim |
| Servidor de Aplicativos SAP Business Warehouse |Sim |
| Servidor de Mensagens SAP Business Warehouse |Ainda não tem suporte no **serviço do Power BI** |
| Google BigQuery |Não |


## <a name="next-steps"></a>Próximas etapas
Para obter mais informações sobre o DirectQuery, confira os seguintes recursos:

* [DirectQuery no Power BI](desktop-directquery-about.md)
* [DirectQuery e SAP HANA](desktop-directquery-sap-hana.md)
* [DirectQuery e SAP BW](desktop-directquery-sap-bw.md)
* [Gateway de dados local](service-gateway-onprem.md)

