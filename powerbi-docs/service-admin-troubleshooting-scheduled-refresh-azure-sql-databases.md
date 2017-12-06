---
title: "Solucionando problemas da atualização agendada para Bancos de Dados SQL do Azure"
description: "Solucionando problemas em atualização agendada para bancos de dados SQL Azure no Power BI"
services: powerbi
documentationcenter: 
author: guyinacube
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
ms.date: 12/06/2017
ms.author: davidi
ms.openlocfilehash: 0b2f5da3fccd1741cb5a9ea02a1aebbd8fbac96f
ms.sourcegitcommit: d91436de68a0e833ecff18d976de9d9431bc4121
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/06/2017
---
# <a name="troubleshooting-scheduled-refresh-for-azure-sql-databases-in-power-bi"></a>Solucionando problemas em atualização agendada para bancos de dados SQL Azure no Power BI
Para obter etapas detalhadas sobre como configurar a atualização agendada, certifique-se de ver [Atualizar dados no Power BI](refresh-data.md).

Ao configurar a atualização agendada para o banco de dados SQL Azure, se você receber um erro com o código de erro 400 durante a edição de credenciais, tente o seguinte para configurar a regra de firewall apropriada:

1. Entre no Portal de Gerenciamento do Azure
2. Vá ara o servidor SQL Azure no qual você está configurando a atualização
3. Ative “Serviços do Windows Azure” na seção de serviços permitidos

![](media/service-admin-troubleshooting-scheduled-refresh-azure-sql-databases/azurerefresh.png)  

Mais perguntas? [Experimente a Comunidade do Power BI](http://community.powerbi.com/)

