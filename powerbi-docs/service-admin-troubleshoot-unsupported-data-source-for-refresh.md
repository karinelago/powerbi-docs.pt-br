---
title: "Solucionando problemas de fonte de dados sem suporte para atualização"
description: "Solucionando problemas de fonte de dados sem suporte para atualização"
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
ms.date: 12/06/2017
ms.author: davidi
ms.openlocfilehash: d95b9d7ca8cae1e4311ef679093814c51a9ba3c0
ms.sourcegitcommit: d91436de68a0e833ecff18d976de9d9431bc4121
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/06/2017
---
# <a name="troubleshooting-unsupported-data-source-for-refresh"></a>Solucionando problemas de fonte de dados sem suporte para atualização
Você verá um erro ao tentar configurar um conjunto de dados para atualização agendada.

        You cannot schedule refresh for this dataset because it gets data from sources that currently don’t support refresh.

Isso acontece quando a fonte de dados usada no Power BI Desktop não dá suporte para atualização. Você precisará encontrar a fonte de dados que está usando e compará-la com a lista de fontes de dados com suporte em [Atualizar dados no Power BI](refresh-data.md). 

## <a name="find-the-data-source"></a>Encontrar a fonte de dados
Se você não tiver certeza de qual fonte de dados foi usada, você pode encontrar usando as seguintes etapas no Power BI Desktop.  

1. No Power BI Desktop, tenha certeza de que está no painel **Relatório** .  
   ![](media/service-admin-troubleshoot-unsupported-data-source-for-refresh/tshoot-report-pane.png)
2. Selecione **Editar Consultas** na barra da faixa de opções.  
   ![](media/service-admin-troubleshoot-unsupported-data-source-for-refresh/tshoot-edit-queries.png)
3. Selecione **Editor Avançado**.  
   ![](media/service-admin-troubleshoot-unsupported-data-source-for-refresh/tshoot-advanced-editor.png)
4. Anote o provedor listado para a fonte.  Neste exemplo, o provedor é Active Directory.  
   ![](media/service-admin-troubleshoot-unsupported-data-source-for-refresh/tshoot-provider.png)
5. Compare o provedor com a lista de fontes de dados com suporte encontrada em [Atualizar dados no Power BI](refresh-data.md).  Você verá que o Active Directory não é uma fonte de dados com suporte para a atualização.  

## <a name="next-steps"></a>Próximas etapas
[Atualização de dados](refresh-data.md)  
[Gateway do Power BI – Pessoal](personal-gateway.md)  
[Gateway de dados local](service-gateway-onprem.md)  
[Solução de problemas do gateway de dados local](service-gateway-onprem-tshoot.md)  
[Solução de problemas do Gateway do Power BI – Pessoal](service-admin-troubleshooting-power-bi-personal-gateway.md)  

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](http://community.powerbi.com/)

