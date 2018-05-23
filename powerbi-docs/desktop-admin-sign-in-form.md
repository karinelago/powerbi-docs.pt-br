---
title: Como os administradores podem gerenciar o formulário de entrada do Power BI Desktop
description: Saiba como é possível gerenciar o formulário de entrada inicial ao abrir o Power BI Desktop.
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 04/24/2018
ms.author: davidi
ms.openlocfilehash: 98bf9579ae7ee551634eed765138c0e78156464c
ms.sourcegitcommit: 998b79c0dd46d0e5439888b83999945ed1809c94
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/17/2018
---
# <a name="how-administrators-can-manage-the-power-bi-desktop-sign-in-form"></a>Como os administradores podem gerenciar o formulário de entrada do Power BI Desktop
Na primeira vez em que o Power BI Desktop é iniciado, é exibido um formulário de entrada. As informações podem ser preenchidas ou entre no Power BI para continuar. Os administradores podem gerenciar este formulário usando uma chave do Registro. 

![Formulário de entrada inicial para o Power BI Desktop](media/desktop-admin-sign-in-form/sign-in-form.png)

Os administradores podem usar a seguinte chave do Registro para desabilitar o formulário de entrada. Isso também pode ser enviado por push usando políticas globais para toda a organização.

```
Key: HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Power BI Desktop
valueName: ShowLeadGenDialog
```

Um valor de 0 desabilitará a caixa de diálogo.

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](http://community.powerbi.com/)

