---
title: "Como os administradores podem gerenciar o formulário de entrada do Power BI Desktop"
description: "Saiba como é possível gerenciar o formulário de entrada inicial ao abrir o Power BI Desktop."
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
ms.date: 01/24/2018
ms.author: davidi
ms.openlocfilehash: 519f8b56b5086292addf577d969a707a6d6efcc8
ms.sourcegitcommit: 7249ff35c73adc2d25f2e12bc0147afa1f31c232
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/25/2018
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

