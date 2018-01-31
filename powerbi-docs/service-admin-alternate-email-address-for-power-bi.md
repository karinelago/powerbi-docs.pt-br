---
title: "Usando um endereço de email alternativo"
description: "Usando um endereço de email alternativo"
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
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 08/09/2017
ms.author: maghan
ms.openlocfilehash: dd9e146b22c95d8c915ea653ee287bb7a51e6b06
ms.sourcegitcommit: 6e693f9caf98385a2c45890cd0fbf2403f0dbb8a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2018
---
# <a name="using-an-alternate-email-address"></a>Usando um endereço de email alternativo
Por padrão, o endereço de email usado para inscrição no Power BI é usado para enviar atualizações sobre a atividade no Power BI.  Por exemplo, quando alguém enviar um convite de compartilhamento ele irá para esse endereço.

Às vezes, você pode querer que esses emails sejam entregues a um endereço de email alternativo em vez daquele usado originalmente para inscrever-se no Power BI.

## <a name="updating-through-office-365-personal-info-page"></a>Atualizando por meio da página de informações pessoais do Office 365
1. Vá para sua [página de informações pessoais do Office 365](https://portal.office.com/account/#personalinfo).  Se for solicitado, entre com o endereço de email e senha que você usa no Power BI.
2. Clique no link de edição na seção Detalhes de contato.  
   
   > [!NOTE]
   > Se você não vir um link de edição, isso significa que seu endereço de email é gerenciado pelo administrador do Office 365 e você precisará entrar em contato com eles para atualizar seu endereço de email.
   > 
   > 
   
   ![](media/service-admin-alternate-email-address-for-power-bi/contact-details.png)
3. No campo de email alternativo, digite o endereço de email para o qual você gostaria que as atualizações do Power BI sejam enviadas.

> [!NOTE]
> A alteração dessa configuração não afetará o endereço de email usado para enviar atualizações de serviço, boletins informativos e outras comunicações promocionais.  Eles sempre serão enviados ao endereço de email usado originalmente durante o registro no Power BI.
> 
> 

## <a name="updating-with-powershell"></a>Atualizando com o PowerShell
Como alternativa, você pode atualizar o endereço de email alternativo por meio do PowerShell para Azure Active Directory. Faça isso com o comando [Set-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser).

```
Set-AzureADUser -ObjectId john@contoso.com -OtherMails "otheremail@somedomain.com"
```

Para obter mais informações, consulte [Azure Active Directory PowerShell versão 2](https://docs.microsoft.com/powershell/azure/active-directory/install-adv2).

Mais perguntas? [Experimente a Comunidade do Power BI](http://community.powerbi.com/)

