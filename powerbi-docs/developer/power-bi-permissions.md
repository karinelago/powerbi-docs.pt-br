---
title: Permissões do Power BI
description: Permissões do Power BI
author: markingmyname
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-developer
ms.topic: conceptual
ms.date: 09/05/2017
ms.author: maghan
ms.openlocfilehash: 4ba0e62dd8c9ba537f56c97489541591ec0bf2bc
ms.sourcegitcommit: 638de55f996d177063561b36d95c8c71ea7af3ed
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/17/2018
---
# <a name="power-bi-permissions"></a>Permissões do Power BI
## <a name="permission-scopes"></a>Escopos de permissão
As permissões do Power BI fornecem a um aplicativo a capacidade de executar determinadas ações em nome de um usuário. Todas as permissões devem ser aprovadas por um usuário para serem válidas.

| Nome de Exibição | Descrição | Valor do escopo |
| --- | --- | --- |
| Exibir todos os conjuntos de dados |O aplicativo pode exibir todos os conjuntos de dados para o usuário conectado e conjuntos de dados aos quais o usuário tem acesso. |Dataset.Read.All |
| Ler e gravar todos os conjuntos de dados |O aplicativo pode exibir e gravar em todos os conjuntos de dados para o usuário conectado e conjuntos de dados aos quais o usuário tem acesso. |Dataset.ReadWrite.All |
| Adicionar dados ao conjunto de dados de um usuário (versão prévia) |Dá acesso a um aplicativo para adicionar ou excluir linhas de conjunto de dados de um usuário. Essa permissão não concede ao aplicativo acesso aos dados do usuário. |Data.Alter_Any |
| Criar conteúdo (versão prévia) |O aplicativo pode criar automaticamente conteúdo e conjuntos de dados para um usuário. |Content.Create |
| Exibir grupos de usuários |O aplicativo pode exibir todos os grupos aos quais o usuário conectado pertence. |Group.Read |
| Exibir todos os grupos |O aplicativo pode exibir todos os grupos aos quais o usuário conectado pertence. |Group.Read.All |
| Exibir todos os painéis (visualização) |O aplicativo pode exibir todos os painéis para o usuário conectado e os painéis aos quais o usuário tem acesso. |Dashboard.Read.All |
| Exibir Todos os Relatórios (visualização) |O aplicativo pode exibir todos os relatórios para o usuário conectado e os relatórios aos quais o usuário tem acesso. O aplicativo também pode ver os dados nos relatórios, bem como sua estrutura. |Report.Read.All |
| Ler e gravar todos os relatórios |O aplicativo pode exibir e gravar em todos os relatórios para o usuário conectado e em todos relatórios a que o usuário tem acesso. Isso não fornece direitos para criar um novo relatório. |Report.ReadWrite.All |

Um aplicativo pode solicitar permissões ao tentar fazer logon na página do usuário pela primeira vez ao passar as permissões solicitadas no parâmetro de escopo da chamada. Se as permissões são concedidas, um token de acesso será retornado ao aplicativo, o qual poderá ser usado em chamadas de API futuras. O acesso pode ser usado somente por um aplicativo específico.

> [!NOTE]
> As APIs do Power BI ainda se referem aos espaços de trabalho do aplicativo como grupos. As referências a grupos significam que você está trabalhando com espaços de trabalho do aplicativo.
> 
> 

## <a name="requesting-permissions"></a>Solicitando permissões
Embora você possa chamar a API para autenticar com um nome de usuário e senha, para executar ações em nome de outro usuário, será necessário solicitar permissões que o usuário aprovará e enviará o token de acesso resultante em todas as chamadas futuras. Para este processo, seguiremos o protocolo [OAuth 2.0](http://oauth.net/2/) padrão. Embora a implementação real possa variar, o fluxo do OAuth para o Power BI tem os seguintes elementos:

* **Interface do Usuário de Logon** - Trata-se de uma interface do usuário que o desenvolvedor pode evocar para solicitar permissões. Ela requer que o usuário faça logon se ainda não o tiver feito. O usuário também precisa aprovar as permissões que o aplicativo está solicitando. A janela de logon lançará um código de acesso ou uma mensagem de erro para uma URL de redirecionamento que é fornecida.
  * Uma URL de redirecionamento padrão deve ser fornecida pelo Power BI para ser usada por aplicativos nativos.
* **Código de Autorização** - Os Códigos de Autorização são retornados aos aplicativos Web após o logon por meio do parâmetros de URL na URL de redirecionamento. Como eles estão nos parâmetros, há alguns riscos de segurança. Os aplicativos Web terão de trocar o código de autorização por um Token de Autorização
* **Token de Autorização** - São usados para autenticar chamadas de API em nome de outro usuário. Eles terão escopo para um aplicativo específico. Os tokens têm um tempo de vida definido e quando expiram precisam ser atualizados.
* **Atualizar Token** - Quando os tokens expiram, há um processo para atualizá-los.

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](http://community.powerbi.com/)

