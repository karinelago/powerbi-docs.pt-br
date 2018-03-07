---
title: "Entender a RLS (segurança em nível de linha) com o Power BI Desktop"
description: "Como configurar a segurança em nível de linha de conjuntos de dados importados e o DirectQuery no Power BI Desktop."
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
ms.tgt_pltfrm: na
ms.workload: powerbi
ms.date: 10/12/2017
ms.author: maghan
LocalizationGroup: Create reports
ms.openlocfilehash: febe8cafb7be578be0dcf23a151f28deb544a4c8
ms.sourcegitcommit: 88c8ba8dee4384ea7bff5cedcad67fce784d92b0
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/24/2018
---
# <a name="row-level-security-rls-with-power-bi-desktop"></a>RLS (segurança em nível de linha) com o Power BI Desktop
A RLS (segurança em nível de linha) com o Power BI Desktop pode ser usada para restringir o acesso a dados para determinados usuários. Os filtros restringem os dados no nível da linha. É possível definir filtros nas funções.

Agora é possível configurar a RLS de modelos de dados importados para o Power BI com o Power BI Desktop. Você também pode configurar RLS em conjuntos de dados que estão usando DirectQuery, como o SQL Server. Anteriormente, você conseguia apenas implementar a RLS nos modelos do Analysis Services local fora do Power BI. Para as conexões dinâmicas do Analysis Services, configure a Segurança em nível de linha no modelo local. A opção de segurança não será exibida para conjuntos de dados com conexão dinâmica.

> [!IMPORTANT]
> Se você tiver definido funções/regras no serviço do Power BI, será necessário recriar essas funções no Power BI Desktop e publicar o relatório no serviço.
> 
> 

Saiba mais sobre as opções para a [RLS no serviço do Power BI](service-admin-rls.md).

[!INCLUDE [include-short-name](./includes/rls-desktop-define-roles.md)]

[!INCLUDE [include-short-name](./includes/rls-desktop-view-as-roles.md)]

[!INCLUDE [include-short-name](./includes/rls-limitations.md)]

[!INCLUDE [include-short-name](./includes/rls-faq.md)]

## <a name="next-steps"></a>Próximas etapas
[RLS (segurança em nível de linha) com o serviço do Power BI](service-admin-rls.md)  

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](http://community.powerbi.com/)

