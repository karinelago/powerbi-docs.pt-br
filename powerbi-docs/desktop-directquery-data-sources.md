---
title: Fontes de dados com suporte do DirectQuery no Power BI
description: Obtenha uma lista de quais fontes de dados podem usar o DirectQuery.
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
ms.date: 10/26/2017
ms.author: davidi
ms.openlocfilehash: 5de07cb5f834d7f40ddd5391e83afa85edd7233c
ms.sourcegitcommit: 284b09d579d601e754a05fba2a4025723724f8eb
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/15/2017
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
* SAP Business Warehouse (Beta)
* SAP HANA
* Snowflake
* Spark (Beta) (versão 0.9 e posterior)
* SQL Server
* Banco de dados Teradata
* Vertica (Beta)

Fontes de dados que têm **(Beta)** ou **(Versão prévia)** depois do nome estão sujeitos a alterações e não há suporte para seu uso em produção. É possível que também não haja suporte para eles após publicar um relatório no **serviço do Power BI**, o que significa que abrir um relatório publicado ou explorar o conjunto de dados pode resultar em um erro.

A única diferença entre fontes de dados **(Beta)** e em **(Versão prévia)** é que as fontes em **(Versão prévia)** precisam ser habilitadas como um recurso de versão prévia antes que fiquem disponíveis para uso. Para habilitar um conector de dados em **(Versão prévia)**, no **Power BI Desktop**, acesse **Arquivo > Opções e Configurações** e, em seguida, **Configurações > Opções > Recursos de Versão prévia**.

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
| Snowflake (Versão prévia) |Ainda não tem suporte no **serviço do Power BI** |
| Spark (beta), versão 0.9 e posterior |Ainda não tem suporte no **serviço do Power BI** |
| Azure HDInsight Spark (Beta) |Ainda não tem suporte no **serviço do Power BI** |
| IBM Netezza (Beta) |Ainda não tem suporte no **serviço do Power BI** |
| SAP Business Warehouse (Beta) |Ainda não tem suporte no **serviço do Power BI** |

## <a name="next-steps"></a>Próximas etapas
Para obter mais informações sobre o DirectQuery, confira os seguintes recursos:

* [DirectQuery no Power BI](desktop-directquery-about.md)
* [DirectQuery e SAP HANA](desktop-directquery-sap-hana.md)
* [DirectQuery e SAP BW](desktop-directquery-sap-bw.md)
* [Gateway de dados local](service-gateway-onprem.md)

