---
title: Onde está localizado meu locatário do Power BI?
description: Saiba onde está localizado seu locatário do Power BI e como essa localização é selecionada. É importante entender isso, já que é algo que pode afetar suas interações com o serviço.
services: powerbi
documentationcenter: ''
author: mgblythe
manager: kfile
backup: ''
editor: ''
tags: ''
qualityfocus: no
qualitydate: ''
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 08/10/2017
ms.author: mblythe
LocalizationGroup: Administration
ms.openlocfilehash: 22b5319cf95beb3ea4a4a498c7174a701e56fb95
ms.sourcegitcommit: 8552a34df8e6141eb704314c1a019992901d6e78
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2018
---
# <a name="where-is-my-power-bi-tenant-located"></a>Onde está localizado meu locatário do Power BI?
<iframe width="560" height="315" src="https://www.youtube.com/embed/0fOxaHJPvdM?showinfo=0" frameborder="0" allowfullscreen></iframe>

Saiba onde está localizado seu locatário do Power BI e como essa localização é selecionada. É importante entender isso, já que é algo que pode afetar suas interações com o serviço.

## <a name="how-to-determine-where-your-power-bi-tenant-is-located"></a>Como determinar onde se encontra o seu locatário do Power BI
Para encontrar a região em que seu locatário está, você pode fazer o seguinte.

1. Selecione **?** no serviço do Power BI.
2. Selecione **Sobre o Power BI**.
3. Procure o valor ao lado de **Seus dados são armazenados em**. Essa é a região em que você está localizado.

![](media/service-admin-where-is-my-tenant-located/power-bi-data-region.png)

## <a name="how-the-data-region-is-selected"></a>Como a região de dados é selecionada
A região de dados baseia-se no país selecionado quando o locatário foi inicialmente criado. Isso se aplica ao inscrever-se para o Office 365 além do Power BI, já que essas informações são compartilhadas. Se esse for um novo locatário, ao se inscrever, você verá uma lista suspensa de países.

![](media/service-admin-where-is-my-tenant-located/sign-up-country-selection.png)

Essa seleção é o que determina o local onde os dados serão armazenados. O Power BI selecionará uma região de dados mais próxima desta seleção.

> [!WARNING]
> Não é possível alterar essa seleção!
> 
> 

Mais perguntas? [Experimente a Comunidade do Power BI](http://community.powerbi.com/)

