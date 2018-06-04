---
title: Onde está localizado meu locatário do Power BI?
description: Saiba onde está localizado seu locatário do Power BI e como essa localização é selecionada. É importante entender isso, já que é algo que pode afetar suas interações com o serviço.
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-admin
ms.topic: conceptual
ms.date: 08/10/2017
ms.author: mblythe
LocalizationGroup: Administration
ms.openlocfilehash: c0c6de63292d3087aaa78dd97b73f868ef9d804e
ms.sourcegitcommit: 80d6b45eb84243e801b60b9038b9bff77c30d5c8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34293641"
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

