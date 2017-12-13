---
title: "Criar um locatário do Azure Active Directory para usar com o Power BI"
description: "Saiba como criar um novo locatário do Azure AD (Azure Active Directory) para usar com seu aplicativo personalizado que usa APIs REST do Power BI."
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
ms.date: 11/30/2017
ms.author: mihart
ms.openlocfilehash: 22d939dbd0a582611f2f4e90e2306456376e211b
ms.sourcegitcommit: 910258a5ad8b6861e81ae02c57286db221c37375
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="create-an-azure-active-directory-tenant-to-use-with-power-bi"></a>Criar um locatário do Azure Active Directory para usar com o Power BI
Saiba como criar um novo locatário do Azure AD (Azure Active Directory) para usar com seu aplicativo personalizado que usa APIs REST do Power BI.

Um locatário é o representante de uma organização no Azure Active Directory. Ele é uma instância dedicada do serviço do Azure AD que uma organização recebe e detém quando se inscreve em um serviço de nuvem da Microsoft, como o Azure, Microsoft Intune ou Office 365. Cada locatário do Azure AD é diferente e separado de outros locatários do Azure AD.

Quando você tiver um locatário do Azure AD, será possível definir um aplicativo e atribuir permissões para ele possa usar as APIs REST do Power BI.

Sua organização talvez já tenha um locatário do Azure AD que você pode usar para seu aplicativo. É possível usar esse locatário para as necessidades do seu aplicativo ou é possível criar um novo locatário especificamente para o seu aplicativo. Este artigo examina como criar um novo locatário.

## <a name="create-an-azure-active-directory-tenant"></a>Crie um locatário do Azure Active Directory
Para integrar o Power BI em seu aplicativo personalizado, é necessário definir um aplicativo no Azure AD. Para fazer isso, é necessário um diretório dentro do Azure AD. Esse é o seu locatário. Se sua organização ainda não tiver um locatário, porque ela não está usando o Power BI ou o Office 365, [será necessário criar um](https://docs.microsoft.com/azure/active-directory/develop/active-directory-howto-tenant). Talvez seja necessário também criar um locatário se você não quiser que seu aplicativo se misture com o locatário da sua organização. Isso permite manter as coisas isoladas.

Ou talvez você apenas deseje criar um locatário para fins de testes.

Para criar um novo locatário do Azure AD, faça o seguinte.

1. Navegue até o [portal do Azure](https://portal.azure.com) e entre com uma conta que tenha uma assinatura do Azure.
2. Selecione o **ícone de mais (+)** e pesquise *Azure Active Directory*.
   
    ![](media/create-an-azure-active-directory-tenant/new-directory.png)
3. Selecione **Azure Active Directory** nos resultados da pesquisa.
   
    ![](media/create-an-azure-active-directory-tenant/new-directory2.png)
4. Selecione **Criar**.
5. Forneça um **nome para a organização** juntamente com o **nome de domínio inicial**. Em seguida, selecione **Criar**. Isso criará seu diretório.
   
    ![](media/create-an-azure-active-directory-tenant/organization-and-domain.png)
   
   > [!NOTE]
   > Seu domínio inicial fará parte de onmicrosoft.com. É possível adicionar outros nomes de domínio mais tarde. O diretório, de um locatário, pode ter vários domínios atribuídos a ele.
   > 
   > 
6. Após a conclusão da criação do seu diretório, marque a caixa de informações para gerenciar seu novo diretório.

Agora seu diretório foi criado. A seguir, adicionaremos um usuário ao locatário.

## <a name="create-some-users-in-your-azure-active-directory-tenant"></a>Crie alguns usuários em seu locatário do Azure Active Directory
Agora que temos um diretório, vamos criar pelo menos dois usuários. Um que seja um administrador global para o locatário e outro que seja o usuário mestre para ser inserido. Pense nisso como uma conta de serviço.

1. No portal do Azure, certifique-se de que estamos na saída do Azure Active Directory.
   
    ![](media/create-an-azure-active-directory-tenant/aad-flyout.png)
   
    Se você não estiver, selecione o ícone do Azure Active Directory na barra de serviços esquerda.
   
    ![](media/create-an-azure-active-directory-tenant/aad-service.png)
2. Em **Gerenciar**, selecione **Usuários e grupos**.
   
    ![](media/create-an-azure-active-directory-tenant/users-and-groups.png)
3. Selecione **Todos os usuários** e, em seguida, selecione **+ Novo usuário**.
4. Forneça um nome e um nome de usuário para este usuário. Esse será seu administrador global do locatário. Você também alterará a **Função do diretório** para *Administrador global*. Também é possível mostrar a senha temporária. Quando terminar, selecione **Criar**.
   
    ![](media/create-an-azure-active-directory-tenant/global-admin.png)
5. Você fará a mesma coisa novamente para um usuário regular em seu locatário. Isso também poderá ser usado para sua conta de inserção mestre. Dessa vez, para **Função do diretório**, a deixaremos como *Usuário*. Certifique-se de anotar a senha. Em seguida, selecione **Criar**.
   
    ![](media/create-an-azure-active-directory-tenant/pbiembed-user.png)
6. Inscreva-se no Power BI com sua conta de usuário criada na etapa 5. É possível fazer isso acessando [powerbi.com](https://powerbi.microsoft.com/get-started/) e selecionando **Experimente grátis** em *Power BI – Colaboração e compartilhamento em nuvem*.
   
    ![](media/create-an-azure-active-directory-tenant/try-powerbi-free.png)
   
    Quando você se inscrever, você será solicitado a experimentar o Power BI Pro gratuitamente por 60 dias. É possível optar por se tornar um usuário pro. Agora também será possível começar a desenvolver uma solução inserida se for isso o que você estiver procurando.
   
   > [!NOTE]
   > Certifique-se de inscrever-se com o endereço de email fornecido à conta de usuário.
   > 
   > 

## <a name="next-steps"></a>Próximas etapas
Agora que você tem um locatário do Azure AD, é possível usar esse locatário para testar itens no Power BI e/ou é possível avançar para inserir relatórios e dashboards do Power BI em seu aplicativo. Para obter mais informações sobre como inserir itens, consulte [Como inserir seus dashboards, relatórios e blocos do Power BI](embedding-content.md).

[O que é um diretório do Azure AD?](https://docs.microsoft.com/azure/active-directory/active-directory-whatis)  
[Como obter um locatário do Azure Active Directory](https://docs.microsoft.com/azure/active-directory/develop/active-directory-howto-tenant)  

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](http://community.powerbi.com/)

