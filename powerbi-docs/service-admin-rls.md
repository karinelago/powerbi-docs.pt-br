---
title: "RLS (segurança em nível de linha) com o Power BI"
description: "Como configurar a segurança em nível de linha para conjuntos de dados importados e DirectQuery para o serviço do Power BI."
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
ms.tgt_pltfrm: na
ms.workload: powerbi
ms.date: 08/11/2017
ms.author: asaxton
ms.openlocfilehash: ea51308d533dc97af9d06855d004b5bacc376247
ms.sourcegitcommit: 99cc3b9cb615c2957dde6ca908a51238f129cebb
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/13/2017
---
# <a name="row-level-security-rls-with-power-bi"></a>RLS (segurança em nível de linha) com o Power BI
<iframe width="560" height="315" src="https://www.youtube.com/embed/67fK0GoVQ80?showinfo=0" frameborder="0" allowfullscreen></iframe>

A RLS (segurança em nível de linha) com o Power BI pode ser usada para restringir o acesso a dados para determinados usuários. Os filtros restringem os dados no nível da linha. É possível definir filtros nas funções.

É possível configurar a RLS de modelos de dados importados para o Power BI com o Power BI Desktop. Você também pode configurar RLS em conjuntos de dados que estão usando DirectQuery, como o SQL Server. Anteriormente, você conseguia apenas implementar a RLS nos modelos do Analysis Services local fora do Power BI. Para as conexões dinâmicas do Analysis Services, configure a Segurança em nível de linha no modelo local. A opção de segurança não será exibida para conjuntos de dados com conexão dinâmica.

[!INCLUDE [include-short-name](./includes/rls-desktop-define-roles.md)]

[!INCLUDE [include-short-name](./includes/rls-desktop-view-as-roles.md)]

## <a name="manage-security-on-your-model"></a>Gerenciar a segurança no modelo
Para gerenciar a segurança no modelo de dados, é necessário fazer o seguinte.

1. Selecione as **reticências (...)** para um conjunto de dados.
2. Selecione **Segurança**.
   
   ![](media/service-admin-rls/rls-security.png)

Você será levado à página da RLS para adicionar membros a uma função criada no Power BI Desktop. Somente os proprietários do conjunto de dados verão a opção Segurança disponível. Se o conjunto de dados está em um Grupo, somente os Administradores do grupo encontrarão a opção de segurança. 

Você só pode criar ou modificar funções no Power BI Desktop.

## <a name="working-with-members"></a>Trabalhando com membros
### <a name="add-members"></a>Adicionar membros
É possível adicionar um membro à função digitando o endereço de email, o nome do usuário, o grupo de segurança ou a lista de distribuição que você deseja adicionar. Esse membro deve estar em sua organização. Não é possível adicionar Grupos criados no Power BI.

![](media/service-admin-rls/rls-add-member.png)

Você também pode ver quantos membros fazem parte da função pelo número entre parênteses ao lado do nome da função ou ao lado de Membros.

![](media/service-admin-rls/rls-member-count.png)

### <a name="remove-members"></a>Remover membros
É possível remover membros selecionando o X ao lado do nome. 

![](media/service-admin-rls/rls-remove-member.png)

## <a name="validating-the-role-within-the-power-bi-service"></a>Validando a função no serviço do Power BI
Você pode validar que a função definida está funcionando corretamente ao testar a função. 

1. Selecione as **reticências (...)** ao lado da função.
2. Selecione **Testar dados como função**

![](media/service-admin-rls/rls-test-role.png)

Então, você verá os relatórios que estão disponíveis para essa função. Os painéis de controle não são apresentados nessa exibição. Na barra azul acima, você verá o que está sendo aplicado.

![](media/service-admin-rls/rls-test-role2.png)

Você pode testar outras funções ou uma combinação de funções, selecionando **Exibindo agora como**.

![](media/service-admin-rls/rls-test-role3.png)

Você pode optar por exibir dados como uma pessoa específica ou pode selecionar uma combinação de funções disponíveis para validar que estão funcionando. 

Para retornar à exibição normal, selecione **Voltar à Segurança de Nível de Linha**.

[!INCLUDE [include-short-name](./includes/rls-usernames.md)]

## <a name="using-rls-with-app-workspaces-in-power-bi"></a>Usando RLS com espaços de trabalho do aplicativo no Power BI
Se você publicar seu relatório do Power BI Desktop em um espaço de trabalho do aplicativo no serviço do Power BI, as funções serão aplicadas aos membros somente leitura. Será necessário indicar que os membros só podem exibir o conteúdo do Power BI nas configurações de espaço de trabalho do aplicativo.

> [!WARNING]
> Se você tiver configurado o espaço de trabalho do aplicativo para que os membros tenham permissões de edição, as funções RLS não serão aplicadas a eles. Os usuários poderão ver todos os dados.
> 
> 

![](media/service-admin-rls/rls-group-settings.png)

[!INCLUDE [include-short-name](./includes/rls-limitations.md)]

[!INCLUDE [include-short-name](./includes/rls-faq.md)]

## <a name="next-steps"></a>Próximas etapas
[RLS (segurança em nível de linha) com o Power BI Desktop](desktop-rls.md)  

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](http://community.powerbi.com/)

