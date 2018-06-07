---
title: Configurar o acesso do aplicativo móvel do Power BI iOS a um servidor de relatório remotamente
description: Saiba como configurar aplicativos móveis iOS remotamente para o seu servidor de relatório.
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-report-server
ms.topic: conceptual
ms.date: 05/22/2018
ms.author: maggies
ms.openlocfilehash: bbade67c9510b8d316364d991c09444712309514
ms.sourcegitcommit: 80d6b45eb84243e801b60b9038b9bff77c30d5c8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34722168"
---
# <a name="configure-power-bi-ios-mobile-app-access-to-a-report-server-remotely"></a>Configurar o acesso do aplicativo móvel do Power BI iOS a um servidor de relatório remotamente

Neste artigo, você aprenderá a usar a ferramenta MDM da sua organização para configurar o acesso de aplicativo móvel do Power BI iOS a um servidor de relatório. Para fazer isso, os administradores de TI criam uma política de configuração do aplicativo com as informações necessárias a serem enviadas por push ao aplicativo. 

 Em seguida, os usuários do aplicativo móvel do Power BI iOS podem se conectar com o servidor de relatório da organização mais facilmente, porque a conexão do servidor de relatório já está configurada. 


## <a name="create-the-app-configuration-policy-in-mdm-tool"></a>Criar a política de configuração do aplicativo na ferramenta MDM 

Como administrador, essas são as etapas a que seguir no Microsoft Intune para criar a política de configuração do aplicativo. As etapas e a experiência de criação da política de configuração de aplicativo podem ser diferentes em outras ferramentas MDM. 

1. Conecte a ferramenta MDM. 
2. Crie e nomeie uma nova política de configuração do aplicativo. 
3. Escolha os usuários para os quais essa política de configuração de aplicativo será distribuída. 
4. Crie pares chave-valor. 

A tabela a seguir indica os pares.

|Chave  |Tipo  |Descrição  |
|---------|---------|---------|
| com.microsoft.powerbi.mobile.ServerURL | Cadeia de caracteres | URL do Servidor de Relatório </br> Deve começar com http/https |
| com.microsoft.powerbi.mobile.ServerUsername | Cadeia de caracteres | [opcional] </br> O nome de usuário a ser usado para conectar o servidor. </br> Se não existir, o aplicativo solicitará ao usuário que digite o nome de usuário para a conexão.| 
| com.microsoft.powerbi.mobile.ServerDisplayName | Cadeia de caracteres | [opcional] </br> O valor padrão é "Servidor de relatório" </br> Um nome amigável usado no aplicativo para representar o servidor | 
| com.microsoft.powerbi.mobile.OverrideServerDetails | Boolean | O valor padrão é True </br> Se definido como "True", em seguida, isso substituirá qualquer definição de Servidor de Relatório que já esteja no dispositivo móvel (servidores existentes já configurados serão excluídos). </br> Substituir a definição para True também evita que o usuário remova essa configuração. </br> Se definido como "False", adicionará os valores enviados por push, mantendo as configurações atuais. </br> Se a mesma URL de servidor já estiver configurada no aplicativo móvel, o aplicativo manterá a configuração e não solicitará ao usuário uma nova autenticação para o mesmo servidor. |

Veja um exemplo de definição de política de configuração usando o Intune.

![Definição de configuração no Intune](media/configure-powerbi-mobile-apps-remote/power-bi-ios-remote-configuration-settings.png)

## <a name="end-users-connecting-to-a-report-server"></a>Conexão dos usuários finais com um servidor de relatório

Depois de publicar a política de configuração do aplicativo, usuários e dispositivos que pertencem à lista de distribuição definida para essa política terão a seguinte experiência quando iniciarem o aplicativo móvel do Power BI iOS. 

1. Uma mensagem informará que o aplicativo móvel está configurado com um servidor de relatório. Toque em **Entrar**.

    ![Entrar no servidor de relatório](media/configure-powerbi-mobile-apps-remote/power-bi-config-server-sign-in.png)

2.  Na página **Conectar-se ao servidor**, os detalhes do servidor de relatório já estão preenchidos. Eles tocam em **Conectar**.

    ![Detalhes do servidor de relatório preenchidos](media/configure-powerbi-mobile-apps-remote/power-bi-ios-remote-configure-connect-server.png)

3. Eles digitam uma senha para autenticar e, em seguida, tocam em **Entrar**. 

    ![Detalhes do servidor de relatório preenchidos](media/configure-powerbi-mobile-apps-remote/power-bi-config-server-address.png)

Agora, é possível exibir e interagir com as KPIs e os relatórios do Power BI armazenados no servidor de relatório.

## <a name="next-steps"></a>Próximas etapas
[Visão geral do administrador](admin-handbook-overview.md)  
[Instalar o Servidor de Relatório do Power BI](install-report-server.md)  

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)

