---
title: "Administrando o Power BI em sua organização"
description: "Administrando o Power BI em sua organização"
services: powerbi
documentationcenter: 
author: guyinacube
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
ms.date: 09/05/2017
ms.author: asaxton
ms.openlocfilehash: 3ee74e9a7f2f174b37e582089e0d9a1d6c433831
ms.sourcegitcommit: 284b09d579d601e754a05fba2a4025723724f8eb
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/15/2017
---
# <a name="administering-power-bi-in-your-organization"></a>Administrando o Power BI em sua organização
Microsoft Power BI permite aos usuários visualizar dados, compartilhar descobertas e colaborar de novas maneiras intuitivas. Para saber mais, consulte [Introdução ao Power BI](service-get-started.md).

A administração do Power BI pode ocorrer em vários locais. Aqui estão dois locais comuns.

> [!NOTE]
> Sua conta deve ser marcada como **Administrador Global** no Office 365 ou no Azure Active Directory ou ter recebido a função de administrador de serviços do Power BI, para obter acesso ao portal de administração do Power BI. Para obter mais informações sobre a função de administrador de serviços do Power BI, consulte [Noções básicas sobre a função de administrador do Power BI](service-admin-role.md).
> 
> 

* [Portal de administração do Power BI](https://app.powerbi.com/admin-portal)
* [Centro de administração do Office 365](https://portal.office.com/adminportal/home)

Para obter mais informações sobre a função de administrador de serviços do Power BI, consulte [Noções básicas sobre a função de administrador do Power BI](service-admin-role.md).

## <a name="whats-in-this-article"></a>O que você encontrará neste artigo
**Inscrever-se no Power BI**

* [Como os usuários podem se inscrever no Power BI?](#how-do-users-sign-up-for-power-bi)
* [Como usuários individuais em minha organização podem se inscrever?](#how-do-individual-users-in-my-organization-sign-up)
* [Como impedir que os usuários ingressem em meu locatário existente do Office 365?](#how-can-i-prevent-users-from-joining-my-existing-office-365-tenant)
* [Como permitir que usuários ingressem em meu locatário existente do Office 365?](#how-can-i-allow-users-to-join-my-existing-office-365-tenant)
* [Como posso verificar se tenho o bloqueio ativado em meu locatário?](#how-do-i-verify-if-i-have-the-block-on-in-the-tenant)
* [Como impedir que meus usuários existentes comecem a usar o Power BI?](#how-can-i-prevent-my-existing-users-from-starting-to-use-power-bi)
* [Como posso permitir que meus usuários existentes se inscrevam no Power BI?](#how-can-i-allow-my-existing-users-to-sign-up-for-power-bi)

**Administração do Power BI**

* [Como isso mudará minha maneira de gerenciar identidades dos usuários em minha organização hoje?](#how-will-this-change-the-way-i-manage-identities-for-users-in-my-organization-today)
* [Como podemos gerenciar o Power BI?](#how-do-we-manage-power-bi)
* [Qual é o processo para gerenciar um locatário criado pela Microsoft para meus usuários?](#what-is-the-process-to-manage-a-tenant-created-by-Microsoft-for-my-users)
* [Se eu tiver vários domínios, poderei controlar o locatário do Office 365 ao qual os usuários serão adicionados?](#if-i-have-multiple-domains-can-i-control-the-office-365-tenant-that-users-are-added-to)
* [Como remover o Power BI para usuários que já se inscreveram?](#how-do-i-remove-power-bi-for-users-that-already-signed-up)
* [Como posso saber se novos usuários ingressaram em meu locatário?](#how-do-i-know-when-new-users-have-joined-my-tenant)
* [Devo estar preparado para outras questões?](#are-there-any-additional-things-i-should-be-prepared-for)
* [Ele é gratuito? Serei ser cobrado por essas licenças?](#is-this-free-will-i-be-charged-for-these-licenses)
* [Onde está localizado meu locatário do Power BI?](#where-is-my-power-bi-tenant-located)

**Segurança no Power BI**

* [O Power BI atende aos requisitos de conformidade regional, nacional e específicos do setor?](#does-power-bi-meet-national-regional-and-industry-specific-compliance-requirements)
* [Como funciona a segurança no Power BI?](#how-does-security-work-in-power-bi?)

## <a name="sign-up-for-power-bi"></a>Inscrever-se no Power BI
### <a name="how-do-users-sign-up-for-power-bi"></a>Como os usuários podem se inscrever para obter o Power BI?
Você pode se inscrever para o Power BI pelo [site do Power BI](https://powerbi.microsoft.com). Você também pode se inscrever na página de serviços de compra no centro de administração do Office 365. Quando um administrador se inscreve para o Power BI, ele pode atribuir licenças de usuário para usuários que devem ter acesso.

Além disso, usuários individuais em sua organização poderão se inscrever no Power BI por meio do [site do Power BI](https://powerbi.microsoft.com). Quando um usuário de sua organização se inscreve para o Power BI, ele recebe automaticamente uma licença do Power BI. [Saiba mais](service-self-service-signup-for-power-bi.md)

### <a name="how-do-individual-users-in-my-organization-sign-up"></a>Como usuários individuais em minha organização podem se inscrever?
Há três cenários que podem se aplicar aos usuários em sua organização:

Cenário 1: sua organização já tem um ambiente existente do Office 365 e o usuário que está se inscrevendo no Power BI já tem uma conta do Office 365.
Neste cenário, se um usuário já tiver uma conta do trabalho ou da escola no locatário (por exemplo, contoso.com), mas ainda não tiver o Power BI, a Microsoft simplesmente ativará o plano para essa conta e o usuário será notificado automaticamente sobre como usar o serviço do Power BI.

Cenário 2: sua organização tem um ambiente existente do Office 365 e o usuário que está se inscrevendo no Power BI não tem uma conta do Office 365.
Nesse cenário, o usuário tem um endereço de email no domínio da sua organização (por exemplo, contoso.com), mas ainda não tem uma conta do Office 365. Nesse caso, o usuário pode se inscrever para o Power BI e receberá automaticamente uma conta. Isso permite o acesso do usuário ao serviço do Power BI. Por exemplo, se uma funcionária chamada Nancy usar seu endereço de email de trabalho (por exemplo, Nancy@contoso.com) para se inscrever, a Microsoft adicionará a Nancy automaticamente como um usuário no ambiente do Office 365 do Contoso e ativará o Power BI para essa conta.

Cenário 3: sua organização não tem um ambiente do Office 365 conectado a seu domínio de email.
Sua organização não precisa tomar ações administrativas para tirar proveito do Power BI. Usuários serão adicionados a um novo diretório de usuário somente em nuvem e você terá a opção de assumir o controle como administrador do locatário e gerenciá-los.

> [!IMPORTANT]
> Se sua organização tiver vários domínios de email e você preferir que todas as extensões de endereço de email estejam no mesmo locatário, adicione todos os domínios de endereço de email a um locatário do Azure Active Directory antes de todos os usuários se inscreverem. Não há nenhum mecanismo automatizado para mover os usuários entre locatários depois que eles foram criados. Para obter mais informações sobre esse processo, consulte [Se eu tiver vários domínios, posso controlar o locatário do Office 365 ao qual os usuários são adicionados?](#if-i-have-multiple-domains-can-i-control-the-office-365-tenant-that-users-are-added-to) posteriormente neste artigo e [Adicionar seu domínio ao Office 365](https://support.office.com/article/Add-your-users-and-domain-to-Office-365-6383f56d-3d09-4dcb-9b41-b5f5a5efd611) online.
> 
> 

### <a name="how-can-i-prevent-users-from-joining-my-existing-office-365-tenant"></a>Como impedir que os usuários ingressem em meu locatário existente do Office 365?
Há etapas que você pode tomar, como administrador, para impedir que os usuários ingressem em seu locatário existente do Office 365. Se você fizer esse bloqueio, as tentativas de usuários para se inscrever falharão e eles serão direcionados a entrar em contato com o administrador da organização. Você não precisa repetir esse processo se você já tiver desabilitado a distribuição automática de licenças (por exemplo, Office 365 Education para Estudantes, Docentes e Funcionários).

Estas etapas exigem o uso do Windows PowerShell. Para começar com o Windows PowerShell, consulte o [Guia de introdução ao PowerShell](http://go.microsoft.com/fwlink/p/?LinkID=286814).

Para executar as etapas a seguir, você deverá instalar a última versão de 64 bits do [Módulo do Azure Active Directory para Windows PowerShell](http://go.microsoft.com/fwlink/p/?LinkID=236297).

Após clicar no link, selecione **Executar** para executar o pacote de instalação.

**Desabilitar o ingresso automático do locatário**: use este comando do Windows PowerShell para impedir que novos usuários ingressem em um locatário gerenciado:

* Para desabilitar o ingresso automático no locatário para novos usuários:
  
    $msolcred = get-credential   connect-msolservice -credential $msolcred
  
    Set-MsolCompanySettings -AllowEmailVerifiedUsers $false
* Para habilitar o ingresso automático no locatário para novos usuários:
  
    $msolcred = get-credential   connect-msolservice -credential $msolcred
  
    Set-MsolCompanySettings -AllowEmailVerifiedUsers $true

> [!NOTE]
> Esse bloqueio impede que novos usuários na sua organização inscrevam no Power BI. Os usuários que se inscrevem para o Power BI antes da desabilitação de novas inscrições para sua organização ainda manterão suas licenças. Consulte a seção [Como é Possível Remover Licenças?] para obter instruções sobre como remover o acesso ao Power BI para usuários que se inscreveram anteriormente no serviço.
> 
> 

### <a name="how-can-i-allow-users-to-join-my-existing-office-365-tenant"></a>Como permitir que usuários ingressem em meu locatário existente do Office 365?
Para permitir que os usuários ingressem no locatário, execute o comando oposto, conforme descrito na pergunta acima.

Para executar as etapas a seguir, você deverá instalar a última versão de 64 bits do [Módulo do Azure Active Directory para Windows PowerShell](http://go.microsoft.com/fwlink/p/?LinkID=236297).

    $msolcred = get-credential
    connect-msolservice -credential $msolcred

    Set-MsolCompanySettings -AllowEmailVerifiedUsers $true

### <a name="how-do-i-verify-if-i-have-the-block-on-in-the-tenant"></a>Como posso verificar se tenho o bloqueio ativado em meu locatário?
Use o seguinte script do PowerShell.

Para executar as etapas a seguir, você deverá instalar a última versão de 64 bits do [Módulo do Azure Active Directory para Windows PowerShell](http://go.microsoft.com/fwlink/p/?LinkID=236297).

    $msolcred = get-credential
    connect-msolservice -credential $msolcred

    Get-MsolCompanyInformation | fl allow*

### <a name="how-can-i-prevent-my-existing-users-from-starting-to-use-power-bi"></a>Como impedir que meus usuários existentes comecem a usar o Power BI?
Há etapas que você pode tomar, como administrador, para impedir que os usuários se inscrevam no Power BI. Se você fizer esse bloqueio, as tentativas de usuários para se inscrever falharão e eles serão direcionados a entrar em contato com o administrador da organização. Você não precisa repetir esse processo se você já tiver desabilitado a distribuição automática de licenças (por exemplo, Office 365 Education para Estudantes, Docentes e Funcionários). [Saiba mais](service-admin-service-free-in-your-organization.md#enable-or-disable-individual-user-sign-up-in-azure-active-directory)

A configuração do AAD que controla isso é **AllowAdHocSubscriptions**. A maioria dos locatários terá essa configuração definida como true, o que significa que ela está habilitada. Se você adquiriu o Power BI por meio de um parceiro, ela pode estar definida como false por padrão, o que significa que ela está desabilitada.

Para executar as etapas a seguir, você deverá instalar a última versão de 64 bits do [Módulo do Azure Active Directory para Windows PowerShell](http://go.microsoft.com/fwlink/p/?LinkID=236297).

1. Você precisa entrar primeiro no Azure Active Directory usando sua credencial do Office 365. Na primeira linha, serão solicitadas suas credenciais. Na segunda linha, você será conectado ao Azure Active Directory.
   
     $msolcred = get-credential   connect-msolservice -credential $msolcred
2. Quando você estiver conectado, pode emitir o comando a seguir para ver para que seu locatário está configurado atualmente.
   
     Get-MsolCompanyInformation | fl AllowAdHocSubscriptions
3. Você pode usar esse comando para habilitar ($true) ou desabilitar ($false) o AllowAdHocSubscriptions.
   
     Set-MsolCompanySettings -AllowAdHocSubscriptions $true

> [!NOTE]
> O sinalizador AllowAdHocSubscriptions é usado para controlar vários recursos de usuários em sua organização, inclusive a capacidade de inscrição dos usuários no Serviço do Rights Management. Alterar esse sinalizador afetará todos esses recursos.
> 
> 

### <a name="how-can-i-allow-my-existing-users-to-sign-up-for-power-bi"></a>Como posso permitir que meus usuários existentes se inscrevem no Power BI?
Para permitir que os usuários existentes se inscrevam no Power BI, execute o comando listado para a pergunta anterior, mas em vez de false, passe true.

Para executar as etapas a seguir, você deverá instalar a última versão de 64 bits do [Módulo do Azure Active Directory para Windows PowerShell](http://go.microsoft.com/fwlink/p/?LinkID=236297).

1. Você precisa entrar primeiro no Azure Active Directory usando sua credencial do Office 365. Na primeira linha, serão solicitadas suas credenciais. Na segunda linha, você será conectado ao Azure Active Directory.
   
     $msolcred = get-credential   connect-msolservice -credential $msolcred
2. Quando você estiver conectado, pode emitir o comando a seguir para ver para que seu locatário está configurado atualmente.
   
     Get-MsolCompanyInformation | fl AllowAdHocSubscriptions
3. Você pode usar esse comando para habilitar ($true) ou desabilitar ($false) o AllowAdHocSubscriptions.
   
     Set-MsolCompanySettings -AllowAdHocSubscriptions $true

> [!NOTE]
> O sinalizador AllowAdHocSubscriptions é usado para controlar vários recursos de usuários em sua organização, inclusive a capacidade de inscrição dos usuários no Serviço do Rights Management. Alterar esse sinalizador afetará todos esses recursos.
> 
> 

## <a name="administration-of-power-bi"></a>Administração do Power BI
### <a name="how-will-this-change-the-way-i-manage-identities-for-users-in-my-organization-today"></a>Como isso mudará minha maneira de gerenciar identidades dos usuários em minha organização hoje?
Se sua organização já tiver um ambiente existente do Office 365, e todos os usuários na organização tiverem contas do Office 365, o gerenciamento de identidades não mudará.

Se sua organização já tiver um ambiente existente do Office 365, mas nem todos os usuários na organização tiverem contas do Office 365, criaremos um usuário no locatário e atribuiremos licenças com base no endereço de email do trabalho ou da escola do usuário. Isso significa que o número de usuários que você está gerenciando em qualquer momento específico crescerá conforme os usuários em sua organização se inscreverem no serviço.

Se você estiver gerenciando seu diretório local e usar o AD FS (Serviços de Federação do Active Directory), a Microsoft não adicionará usuários a seu locatário, e os usuários que tentarem ingressar no locatário receberão uma mensagem para contatar o administrador da organização.

Se sua organização não tiver um ambiente do Office 365 conectado a seu domínio de email, não haverá modificações em como você gerencia identidades. Usuários serão adicionados a um novo diretório de usuário somente em nuvem e você terá a opção de assumir o controle como administrador do locatário e gerenciá-los.

### <a name="how-do-we-manage-power-bi"></a>Como podemos gerenciar o Power BI?
O Power BI fornece um portal de administração que permite que você exiba estatísticas de uso, fornece um link para o centro de administração do Office 365 para gerenciar usuários e grupos e a capacidade de controlar configurações de locatário. 

> [!NOTE]
> Sua conta deve ser marcada como um **Administrador Global**, no Office 365 ou no Azure Active Directory, para obter acesso ao portal de administração do Power BI.
> 
> 

Para obter mais informações, confira [Portal de Administração do Power BI](service-admin-portal.md).

### <a name="what-is-the-process-to-manage-a-tenant-created-by-microsoft-for-my-users"></a>Qual é o processo para gerenciar um locatário criado pela Microsoft para meus usuários?
Se um locatário for criado pela Microsoft, você poderá solicitá-lo e gerenciá-lo seguindo estas etapas:

1. Ingresse no locatário, inscrevendo-se para o Power BI e usando um domínio de endereço de email que corresponda ao domínio de locatário que você deseja gerenciar. Por exemplo, se a Microsoft criar o locatário contoso.com, você precisará ingressar no locatário com um endereço de email que termine com @contoso.com.
2. Solicite o controle de administração, verificando a propriedade do domínio: quando estiver no locatário, você poderá se autopromover à função de *Administrador Global*, verificando a propriedade de domínio. Para se conectar, siga essas etapas:
   
   1. Vá para [https://portal.office.com](https://portal.office.com).
   2. Selecione o ícone do aplicativo iniciador no canto superior esquerdo e escolha **Admin**.
   3. Leia as instruções na página **Tornar-se o administrador** e escolha **Sim, quero ser o administrador**.
      
      > [!NOTE]
      > Se esta opção não for exibida, já existirá um administrador do Office 365 em vigor.
      > 
      > 

### <a name="if-i-have-multiple-domains-can-i-control-the-office-365-tenant-that-users-are-added-to"></a>Se eu tiver vários domínios, poderei controlar o locatário do Office 365 ao qual os usuários serão adicionados?
Se você não fizer nada, será criado um locatário para cada domínio e subdomínio de email de usuários.

Se você quiser que todos os usuários estejam no mesmo locatário independentemente de suas extensões de endereço de email:

* Crie um locatário de destino antecipadamente ou use um locatário existente e adicione todos os domínios e subdomínios existentes que você quer que sejam consolidados nesse locatário. Em seguida, todos os usuários com endereços de email terminados nesses domínios e subdomínios ingressarão automaticamente no locatário de destino ao se inscreverem.

> [!IMPORTANT]
> Não há nenhum mecanismo automatizado com suporte para mover os usuários entre locatários depois que eles foram criados. Para saber mais sobre a adição de domínios a um único locatário do Office 365, consulte [Adicionar usuários e domínio ao Office 365](https://support.office.com/article/Add-your-users-and-domain-to-Office-365-6383f56d-3d09-4dcb-9b41-b5f5a5efd611).
> 
> 

### <a name="how-do-i-remove-power-bi-for-users-that-already-signed-up"></a>Como remover o Power BI para usuários que já se inscreveram?
Se um usuário se inscrever no Power BI, mas você não quiser mais que ele tenha acesso ao Power BI, será possível remover a licença do Power BI para esse usuário.

1. Navegue até o centro de administração do Office 365
2. Na barra de navegação à esquerda, selecione **Usuários** > **Usuários ativos**.
3. Localize o usuário cuja licença você deseja remover, selecione seu nome > **Editar**.
4. Na página de detalhes do usuário, clique em **Licenças** na barra de navegação à esquerda.
5. Desmarque **Power BI (gratuito)** ou **Power BI Pro**, dependendo de qual licença é aplicada à sua conta.
6. Selecione **Salvar**.

> [!NOTE]
> Você também pode executar o gerenciamento de licenças em massa a usuários. Para fazer isso, selecione vários usuários e selecione **Editar**.
> 
> 

### <a name="how-do-i-know-when-new-users-have-joined-my-tenant"></a>Como posso saber se novos usuários ingressaram em meu locatário?
Os usuários que ingressarem em seu locatário como parte desse programa receberão uma licença exclusiva, que você poderá filtrar dentro no painel do usuário ativo, no painel do administrador.

Para criar esse novo modo de exibição no centro de administração do Office 365, vá para **Usuários** > **Usuários Ativos** e no menu **Selecionar uma Exibição**, selecione **Nova Exibição**. Nomeie o novo modo de exibição e, em **Licença atribuída**, selecione **Power BI (gratuito)** ou **Power BI Pro**. Você só pode ter uma licença por exibição. Se você tiver licenças **Power BI (gratuito)** e **Power BI Pro** em sua organização, você precisa criar dois modos de exibição. Depois que o novo modo de exibição tiver sido criado, você poderá ver todos os usuários em seu locatário que registraram no programa.

### <a name="are-there-any-additional-things-i-should-be-prepared-for"></a>Devo estar preparado para outras questões?
Você pode perceber um aumento nas solicitações de redefinição de senha. Para obter informações sobre esse processo, consulte [Redefinir a senha do usuário](https://support.office.com/article/Reset-a-users-password-7a5d073b-7fae-4aa5-8f96-9ecd041aba9c).

Você pode remover um usuário do seu locatário pelo processo padrão no centro de administração do Office 365. No entanto, se o usuário ainda tiver um endereço de email ativo de sua organização, ele poderá reingressar, a menos que você bloqueie o ingresso de todos os usuários.

### <a name="is-this-free-will-i-be-charged-for-these-licenses"></a>Ele é gratuito? Serei ser cobrado por essas licenças?
As licenças do **Power BI (gratuito)** são para a versão gratuita do Power BI. Se você estiver interessado em recursos adicionais, veja a [versão do Power BI Pro](service-premium.md).

### <a name="where-is-my-power-bi-tenant-located"></a>Onde está localizado meu locatário do Power BI?
Para aprender a descobrir onde o locatário do Power BI está localizado, também conhecida como uma região de dados, veja [Onde está localizado meu locatário do Power BI?](service-admin-where-is-my-tenant-located.md)

## <a name="security-in-power-bi"></a>Segurança no Power BI
### <a name="does-power-bi-meet-national-regional-and-industry-specific-compliance-requirements"></a>O Power BI atende aos requisitos de conformidade regional, nacional e específicos do setor?
Para saber mais sobre a conformidade do Power BI, consulte o [Microsoft Trust Center](http://go.microsoft.com/fwlink/?LinkId=785324).

### <a name="how-does-security-work-in-power-bi"></a>Como funciona a segurança no Power BI?
O Power BI foi criado de acordo com a base do Office 365, que por sua vez baseia-se nos serviços do Azure, como o Azure Active Directory. Para obter uma visão geral da arquitetura do Power BI, consulte [Segurança do Power BI](service-admin-power-bi-security.md). 

## <a name="next-steps"></a>Próximas etapas
[Portal de administração do Power BI](service-admin-portal.md)  
[Noções básicas sobre a função de administrador do Power BI](service-admin-role.md)  
[Inscrição de autoatendimento no Power BI](service-self-service-signup-for-power-bi.md)  
[Power BI (gratuito) em sua organização](service-admin-service-free-in-your-organization.md)  
[Compra do Power BI Pro](service-admin-purchasing-power-bi-pro.md)  
[Power BI Premium – o que é?](service-premium.md)  
[Como comprar o Power BI Premium](service-admin-premium-purchase.md)  
[Gerenciamento de contas de usuário do Office 365](https://technet.microsoft.com/library/office-365-user-account-management.aspx)  
[Gerenciamento de grupo do Office 365](https://support.office.com/Article/Find-help-about-Groups-in-Office-365-7a9b321f-b76a-4d53-b98b-a2b0b7946de1)  
[Gerenciar seu grupo no Power BI e no Office 365](service-manage-app-workspace-in-power-bi-and-office-365.md)  
[White paper do Power BI Premium](https://aka.ms/pbipremiumwhitepaper)  

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](http://community.powerbi.com/)

