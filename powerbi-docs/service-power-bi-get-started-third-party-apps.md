---
title: Introdução do Power BI a aplicativos de terceiros
description: Introdução do Power BI a aplicativos de terceiros
author: markingmyname
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 08/10/2017
ms.author: maghan
LocalizationGroup: Get started
ms.openlocfilehash: 7ac6cee3331333b40119d6f5ab014b2e39d2ef23
ms.sourcegitcommit: 80d6b45eb84243e801b60b9038b9bff77c30d5c8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34251739"
---
# <a name="get-started-with-third-party-apps"></a>Introdução a aplicativos de terceiros
Com o Power BI, você pode usar um aplicativo criado por uma empresa ou indivíduo diferente da Microsoft. Por exemplo, você pode usar um aplicativo de terceiros que integra blocos Power BI em um aplicativo Web interno personalizado. Quando você usa um aplicativo de terceiros, será solicitado que você conceda a esse aplicativo determinadas permissões para sua conta e recursos do Power BI. É importante que você somente conceda permissões para aplicativos que você conhece e confia. Permissões para um aplicativo podem ser revogadas em qualquer momento. Veja [Revogar permissões de aplicativos de terceiros](#revoke).

Aqui estão os tipos de acesso que um aplicativo pode solicitar.

## <a name="power-bi-app-permissions"></a>Permissões de Aplicativo do Power BI
* **Exibir Todos os Dashboards**
  
  * Essa permissão fornece a um aplicativo a capacidade de exibir todos os dashboards aos quais você tem acesso. Isso inclui painéis que você tem, obtidos de pacotes de conteúdo e que foram compartilhados com você e estão em grupos aos quais você pertence. O aplicativo não pode fazer modificações ao dashboard. Entre outras coisas, essa permissão pode ser usada por um aplicativo para inserir o conteúdo do painel de controle em suas experiências.
* **Exibir Todos os Relatórios**
  
  * Essa permissão fornece a um aplicativo a capacidade de exibir todos os relatórios aos quais você tem acesso. Isso inclui painéis que você tem, obtidos de pacotes de conteúdo e em grupos aos quais você pertence. Parte da visualização do relatório significa que o aplicativo também pode ver os dados nele. O aplicativo não pode fazer modificações aos relatórios. Entre outras coisas, essa permissão pode ser usada por um aplicativo para inserir o conteúdo do relatório em suas experiências.
* **Exibir todos os conjuntos de dados**
  
  * Essa permissão permite a um aplicativo listar todos os conjuntos de dados aos quais você terá acesso. Isso inclui os conjuntos de dados que você tem, que você obteve de pacotes de conteúdo e que estão em grupos aos quais você pertence. Um aplicativo pode ver os nomes de todos os seus conjuntos de dados, bem como sua estrutura, incluindo nomes de tabela e coluna. Essa permissão concede direitos para ler os dados em um conjunto de dados. A permissão não dá permite ao aplicativo direitos para adicionar ou fazer alterações a um conjunto de dados.
* **Ler e gravar todos os conjuntos de dados**
  
  * Essa permissão permite a um aplicativo listar todos os conjuntos de dados aos quais você terá acesso. Isso inclui os conjuntos de dados que você tem, que você obteve de pacotes de conteúdo e que estão em grupos aos quais você pertence. Um aplicativo pode ver os nomes de todos os seus conjuntos de dados, bem como sua estrutura, incluindo nomes de tabela e coluna. Essa permissão concede direitos para ler e gravar os dados em um conjunto de dados. O aplicativo também pode criar novos conjuntos de dados ou fazer modificações aos existentes. Isso é normalmente usado por um aplicativo para enviar dados diretamente ao Power BI.
* **Exibir grupos de usuários**
  
  * Essa permissão permite a um aplicativo listar todos os grupos dos quais você participa. Ele pode usar essa permissão junto com algumas das outras permissões listadas para exibir ou atualizar o conteúdo de um grupo específico. O aplicativo não pode fazer modificações ao grupo em si.

<a name="revoke"/>

## <a name="revoke-third-party-app-permissions"></a>Revogar permissões de aplicativos de terceiros
Você pode revogar permissões para um aplicativo de terceiros indo para o site Meus aplicativos do Office 365.

No site **Meus aplicativos do Office 365** , aqui está como revogar permissões de terceiros:

1. Vá para o [site Meus aplicativos do Office 365](https://portal.office.com/myapps).
2. Na página **Meus aplicativos** , localize o aplicativo de terceiros.
3. Passe o mouse sobre o bloco do aplicativo, clique no botão **(…)** e, em seguida, clique em **Remover**.
   
   ![](media/service-power-bi-get-started-third-party-apps/remove.png)

