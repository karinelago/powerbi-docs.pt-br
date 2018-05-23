---
title: Exibição de Relações no Power BI Desktop
description: Exibição de Relações no Power BI Desktop
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 05/02/2018
ms.author: davidi
LocalizationGroup: Model your data
ms.openlocfilehash: 58886dc1ae5490113d4d0ba9af00d16aefecbe71
ms.sourcegitcommit: 638de55f996d177063561b36d95c8c71ea7af3ed
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/17/2018
---
# <a name="relationship-view-in-power-bi-desktop"></a>Exibição de Relações no Power BI Desktop
A **Exibição de Relações** mostra todas as tabelas, colunas e relações em seu modelo. Isso pode ser especialmente útil quando o modelo tem relações complexas entre várias tabelas.

Vamos dar uma olhada.

![](media/desktop-relationship-view/relationshipview_fullscreen.png)

**A.**  Ícone Exibição de Relações – clique para mostrar o modelo na Exibição de Relações

**B.** Relação – você pode passar o cursor sobre uma relação para mostrar as colunas usadas. Clique duas vezes em uma relação para abri-la na caixa de diálogo **Editar Relação**. 

Na figura acima, você pode ver que a tabela *Stores* tem uma coluna *StoreKey* que está relacionada à tabela *Sales*, que também tem uma coluna *StoreKey*. Podemos ver que se trata de uma relação do tipo *Muitos para Um* (\*:1) e que o ícone no meio da linha mostra a direção da filtragem cruzada definida como *Ambas*. A seta no ícone mostra a direção do fluxo do contexto de filtro.

Para saber mais sobre as relações, consulte [Criar e gerenciar relações no Power BI Desktop](desktop-create-and-manage-relationships.md).

