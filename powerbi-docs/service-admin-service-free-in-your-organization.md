---
title: "Power BI (gratuito) em sua organização"
description: "Este artigo examina as opções para o Power BI (gratuito) de uma perspectiva organizacional. Se você for o Administrador do seu locatário, ele mostrará como gerenciar as inscrições gratuitas."
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
ms.date: 09/05/2017
ms.author: maghan
ms.openlocfilehash: ec039ab195e2112654ac7f3057d54ecb60c21058
ms.sourcegitcommit: 6e693f9caf98385a2c45890cd0fbf2403f0dbb8a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2018
---
# <a name="power-bi-free-in-your-organization"></a>Power BI (gratuito) em sua organização
Isso examinará como a oferta do Power BI (gratuito) pode ser usada dentro da sua organização. Uma organização significa que você tem um locatário e pode gerenciar usuários e serviços dentro desse locatário. Como administrador, você pode controlar a atribuição de licença ou permitir que os usuários se inscrevam como um indivíduo. Vamos examinar a licença do Power BI (gratuito) e como você pode controlar inscrição individual.

## <a name="individual-sign-up-versus-license-assignment"></a>Inscrição individual versus atribuição de licença
Os usuários de sua organização podem obter acesso ao Power BI de duas maneiras diferentes. Eles podem se inscrever individualmente no Power BI ou você pode atribuir uma licença do Power BI a eles dentro do Portal de administração do Office 365.

Permitir a inscrição individual reduz a carga, dos administradores da organização, permitindo que os usuários que estejam interessados no Power BI se inscrevam gratuitamente.

Para obter mais controle, você pode bloquear a inscrição individual e atribuir licenças do Power BI por conta própria no Centro de administração do Office 365. Isso permite que você seja específico quanto a quem pode acessar quais serviços dentro da sua organização. Essa também é uma ótima opção se você precisa lidar com a auditoria e precisa saber exatamente quem pode usar o que.

## <a name="how-to-get-the-unlimited-license-block"></a>Como obter o bloco de licenças ilimitadas
No Centro de administração do Office 365, em **Cobrança** > **Licenças**, você pode ou não ver o Power BI (gratuito) com licenças ilimitadas.

![](media/service-admin-service-free-in-your-organization/unlimited-licenses.png)

Este bloco de licenças será exibido após a primeira vez que alguém se inscreve no Power BI como um indivíduo. Durante esse processo, este bloco de licenças é anexado à sua organização e uma licença é atribuída ao usuário que está se inscrevendo.

Se você estiver bloqueando inscrições de usuário individuais e ninguém tiver se inscrito, você não verá esse bloco de licenças. Você pode permitir inscrições de usuário individuais e ter uma inscrição de usuário ou pode obter licenças gratuitas por meio do fluxo do Office 365 de adição de assinatura, que será comentado a seguir.

Quando o bloco de licença do Power BI (gratuito) estiver disponível, você pode atribuir essas licenças aos seus usuários. Para obter mais informações sobre como atribuir licenças, consulte [Atribuir licenças a usuários no Office 365 ](https://support.office.com/article/Assign-or-unassign-licenses-for-Office-365-for-business-997596b5-4173-4627-b915-36abac6786dc).

## <a name="getting-free-licenses-via-add-subscription-within-office-365"></a>Obtendo licenças gratuitas por meio da adição de assinatura no Office 365
1. Navegue até o [Centro de administração do Office 365](https://portal.office.com/admin/default.aspx).
2. No painel de navegação esquerdo, selecione **Cobrança** > **Assinaturas**.
3. Selecione **Adicionar assinaturas +** no lado direito.
4. Em Outros Planos, passe o mouse sobre a **elipse (...)** para o Power BI (gratuito) e selecione **Comprar agora**.
   
    ![](media/service-admin-service-free-in-your-organization/buy-powerbi-free.png)
5. Insira o número de licenças que você deseja adicionar e selecione **Fazer check-out agora** ou em **Adicionar ao carrinho**.
   
   > [!NOTE]
   > É possível adicionar mais licenças em uma data posterior, se necessário.
   > 
   > 
6. Insira as informações necessárias no fluxo de check-out.

Não há nenhuma compra ao usar essa abordagem, embora seja necessário inserir suas informações de cartão de crédito para cobrança ou optar por ser faturado.

Se você decidir posteriormente que deseja adicionar mais licenças, pode voltar para **Adicionar assinaturas**, e selecionar **Alterar a quantidade de licenças** para o Power BI (gratuito).

![](media/service-admin-service-free-in-your-organization/change-license-quantity.png)

Agora você pode atribuir essas licenças para seus usuários. Para obter mais informações sobre como atribuir licenças, consulte [Atribuir licenças a usuários no Office 365 ](https://support.office.com/article/Assign-or-unassign-licenses-for-Office-365-for-business-997596b5-4173-4627-b915-36abac6786dc).

## <a name="enable-or-disable-individual-user-sign-up-in-azure-active-directory"></a>Habilitar ou desabilitar a inscrição de usuário individual no Azure Active Directory
Como administrador, você pode optar por habilitar ou desabilitar as inscrições de usuário individuais como parte do AAD (Azure Active Directory). Se você souber como usar os comandos do PowerShell do AAD, pode habilitar ou desabilitar, assinaturas ad hoc por conta própria. [Saiba mais](https://technet.microsoft.com/library/jj151815.aspx)

A configuração do AAD que controla isso é **AllowAdHocSubscriptions**. A maioria dos locatários terá essa configuração definida como true, o que significa que ela está habilitada. Se você adquiriu o Power BI por meio de um parceiro, ela pode estar definida como false por padrão, o que significa que ela está desabilitada.

1. Você precisa entrar primeiro no Azure Active Directory usando sua credencial do Office 365. Na primeira linha, serão solicitadas suas credenciais. Na segunda linha, você será conectado ao Azure Active Directory.
   
     $msolcred = get-credential   connect-msolservice -credential $msolcred
   
   ![](media/service-admin-service-free-in-your-organization/aad-signin.png)
2. Quando você estiver conectado, pode emitir o comando a seguir para ver para que seu locatário está configurado atualmente.
   
     Get-MsolCompanyInformation | fl AllowAdHocSubscriptions
3. Você pode usar esse comando para habilitar ($true) ou desabilitar ($false) o AllowAdHocSubscriptions.
   
     Set-MsolCompanySettings -AllowAdHocSubscriptions $true

> [!NOTE]
> Esse bloqueio impede que novos usuários na sua organização inscrevam no Power BI. Os usuários que se inscrevem para o Power BI antes da desabilitação de novas inscrições para sua organização ainda manterão suas licenças.
> 
> 

## <a name="next-steps"></a>Próximas etapas
[Inscrição de autoatendimento no Power BI](service-self-service-signup-for-power-bi.md)  
[Compra do Power BI Pro](service-admin-purchasing-power-bi-pro.md)  
[Inscrever-se no Power BI (gratuito) com um locatário do Azure Active Directory personalizado](developer/create-an-azure-active-directory-tenant.md)  
[Power BI Premium – o que é?](service-premium.md)  
[White paper do Power BI Premium](https://aka.ms/pbipremiumwhitepaper)  

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](http://community.powerbi.com/)

