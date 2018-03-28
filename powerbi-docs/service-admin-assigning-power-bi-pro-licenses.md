---
title: Atribuir licenças do Power BI Pro
description: Atribuir licenças do Power BI Pro
services: powerbi
documentationcenter: ''
author: markingmyname
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
ms.date: 03/22/2018
ms.author: maghan
LocalizationGroup: Administration
ms.openlocfilehash: 010f99922e2e9d43bbb192fe53eabb17a6af43f3
ms.sourcegitcommit: 1fe3ababba34c4e7aea08adb347ec5430e0b38e4
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/22/2018
---
# <a name="assigning-power-bi-pro-licenses"></a>Atribuir licenças do Power BI Pro

Os administradores podem optar entre uma variedade de portais de gerenciamento e cmdlets do PowerShell para atribuir licenças do Power BI Pro a usuários. O gerenciamento de licenças do Power BI é feito pelo Azure AD (Azure Active Directory).

* Os proprietários de assinatura do Azure podem usar a folha Azure Active Directory no [Portal do Azure](https://ms.portal.azure.com/#@microsoft.onmicrosoft.com/dashboard/private/39bc3cf7-31a4-43f6-954c-f2d69ca2f0). 

* Os administradores globais e os administradores de contas de usuário podem usar o [Centro de administração do Office 365](https://portal.office.com/AdminPortal/Home#/homepage).

## <a name="managing-power-bi-pro-licenses-in-the-azure-portal"></a>Gerenciar licenças do Power BI Pro no Portal do Azure

O Power BI usa o Azure AD como um serviço básico. O Azure AD armazena as contas de usuário e grupos, armazenando simultaneamente outras configurações, tais como informações sobre produtos adquiridos.

### <a name="assigning-licenses-to-individual-user-accounts"></a>Atribuir licenças a contas de usuário individuais

Siga estas etapas para atribuir licenças Pro a contas de usuário individuais, se você é um proprietário de assinatura do Azure:

1. Navegue até o [Portal do Azure](https://ms.portal.azure.com/#@microsoft.onmicrosoft.com/dashboard/private/39bc3cf7-31a4-43f6-954c-f2d69ca2f0). 

2. Na barra de navegação à esquerda, clique no Azure Active Directory.

    ![image](media/service-assigning-power-bi-pro-licenses/service-assigning-power-bi-pro-licenses-01.png)

3. Na folha do Azure Active Directory, clique em Licenças.

    ![image](media/service-assigning-power-bi-pro-licenses/service-assigning-power-bi-pro-licenses-02.png)

4. Na folha Licenças, clique em todos os produtos e clique em Power BI Pro para ver a lista de usuários licenciados.

    ![image](media/service-assigning-power-bi-pro-licenses/service-assigning-power-bi-pro-licenses-03.png)

5. Clique em Atribuir para adicionar uma licença do Power BI Pro para uma conta de usuário adicional.

    ![image](media/service-assigning-power-bi-pro-licenses/service-assigning-power-bi-pro-licenses-04.png)

> [!NOTE]
> Embora a maioria dos aspectos de licenciamento possam ser gerenciados, não é possível comprar licenças do Power BI Pro no Portal do Azure. Use o Centro de administração do Office 365 para comprar uma assinatura do Power BI Pro. Para obter mais informações, consulte [Comprando o Power BI Pro](https://docs.microsoft.com/en-us/power-bi/service-admin-purchasing-power-bi-pro).
>

## <a name="managing-power-bi-pro-licenses-in-the-office-365-admin-center"></a>Gerenciar licenças do Power BI Pro no Centro de administração do Office 365

Se você é um administrador global, é no Centro de administração do Office 365 que você pode comprar uma assinatura do Power BI Pro e gerenciar as licenças associadas para a organização.

Siga estas etapas para atribuir licenças Pro a contas de usuário individuais, se você é um administrador do Centro de administração do Office 365:

1. Navegue até o centro de administração do Office 365

2. No painel de navegação esquerdo, expanda Usuários e, em seguida, clique em Usuários ativos.

    ![image](media/service-assigning-power-bi-pro-licenses/service-assigning-power-bi-pro-licenses-05.png)

3. Selecione um ou vários usuários e, em seguida, clique em Editar licenças de produto.

    ![image](media/service-assigning-power-bi-pro-licenses/service-assigning-power-bi-pro-licenses-06.png)

4. No Power BI Pro, mude a configuração para Ativa e, em seguida, clique em Salvar.

    ![image](media/service-assigning-power-bi-pro-licenses/service-assigning-power-bi-pro-licenses-07.png)

5. Em Status para as contas selecionadas, verifique se a licença do Power BI Pro foi atribuída com êxito.

    ![image](media/service-assigning-power-bi-pro-licenses/service-assigning-power-bi-pro-licenses-08.png)

> [!NOTE]
> Se as licenças de sua assinatura acabaram, adicione mais delas expandindo Cobrança no painel de navegação esquerdo e, em seguida, clicando em Assinaturas. Selecione a assinatura do Power BI Pro na página Assinaturas e, em seguida, clique em Adicionar/Remover licenças.
>

## <a name="next-steps"></a>Próximas etapas
[Power BI Pro em sua organização](service-admin-power-bi-pro-in-your-organization.md)
</br>
[Ativação da Avaliação Pro Estendida](service-extended-pro-trial.md)
</br>
[Contrato de Serviço do Power BI para usuários individuais](https://powerbi.microsoft.com/terms-of-service/)
</br>
[Comunicado do Power BI Premium](https://aka.ms/pbipremium-announcement)
</br>
[Encontrar usuários do Power BI que entraram](service-admin-access-usage.md)

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)