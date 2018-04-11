---
title: Espaço de Trabalho Arquivado do Power BI
description: Espaço de Trabalho Arquivado do Power BI depois de gerenciar locatários do Office 365
services: powerbi
documentationcenter: ''
author: mgblythe
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
ms.date: 06/28/2017
ms.author: mblythe
LocalizationGroup: Administration
ms.openlocfilehash: 254857072df2b06fbdeb2af0a53d262e98f8f254
ms.sourcegitcommit: 8552a34df8e6141eb704314c1a019992901d6e78
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2018
---
# <a name="power-bi-archived-workspace"></a>Espaço de Trabalho Arquivado do Power BI
Com o Power BI, qualquer pessoa pode inscrever-se e começar a usar o serviço em alguns minutos.  Posteriormente, o departamento de TI da sua organização pode optar por assumir o gerenciamento do Power BI para usuários em sua organização.  Se esse controle ocorrer, você se beneficiará do gerenciamento central de usuários e permissões em sua organização e você poderá tirar proveito do logon simplificado usando o mesmo nome de usuário e senha utilizados para outros serviços em sua organização. 

Qualquer conteúdo que tenha sido criado antes do início do gerenciamento do Power BI por seu departamento de TI será colocado em um Espaço de Trabalho Arquivado do Power BI, que pode ser acessado na barra de navegação à esquerda do [Power BI](https://app.powerbi.com).  Você deve começar a criação de conteúdo novo Power BI em Meu Espaço de Trabalho, que é protegido e gerenciado pelo departamento de TI da sua organização.  O espaço de trabalho arquivado continuará a existir, mas há restrições sobre as ações que podem ser executadas no conteúdo do Espaço de Trabalho Arquivado.  Para remover essas restrições, você precisará migrar o conteúdo do seu Espaço de Trabalho Arquivado para o Meu Espaço de Trabalho, gerenciado pelo departamento de TI.

## <a name="restrictions-in-your-archived-workspace"></a>Restrições em seu Espaço de Trabalho Arquivado
Nenhum conteúdo será excluído do Espaço de Trabalho Arquivado.  Você pode continuar a obter dados, criar relatórios e painéis e atualizar conjuntos de dados.  Usuários existentes com os quais você compartilhou conteúdo ainda poderão exibir o conteúdo em seu Espaço de Trabalho Arquivado.

No entanto, há algumas restrições sobre o conteúdo em seu Espaço de Trabalho Arquivado:

* **OneDrive for Business.**  Não será mais possível obter dados para conjuntos de dados ou atualizá-los por meio do OneDrive for Business no Espaço de Trabalho Arquivado.  Se você tentar se conectar a essa fonte, você receberá um aviso.
* **Compartilhando dashboards.**  Não é possível compartilhar dashboards com outros usuários por meio do Espaço de Trabalho Arquivado.  Todos os usuários que já têm acesso continuarão a exibir painéis compartilhados, acessando seu Espaço de Trabalho Arquivado.
* **Criando grupos.**  Não é possível criar grupos no Espaço de Trabalho Arquivado.
* **Acesso em aplicativos móveis do Power BI.**  Embora você ainda possa exibir o conteúdo na Web no Espaço de Trabalho Arquivado, esse conteúdo não aparecerá mais nos aplicativos móveis do Power BI.

## <a name="migrating-content-in-your-archived-workspace"></a>Migração de conteúdo no Espaço de Trabalho Arquivado
Para continuar a usar o Power BI, você deve criar o novo conteúdo no Meu Espaço de Trabalho, gerenciado pelo departamento de TI.   Você também deve planejar migrar qualquer conteúdo em seu Espaço de Trabalho Arquivado para o Meu Espaço de Trabalho.  Como migrar o conteúdo depende do tipo de conteúdo:

* **Conjuntos de dados do Excel ou do Power BI Desktop.**  Migre esses conjuntos de dados alternando do Espaço de Trabalho Arquivado para Meu Espaço de Trabalho e carregue novamente o arquivo do Excel ou do Power BI Desktop clicando no botão “Meus Dados”.  Se você configurar a atualização agendada, você precisará reconfigurar as configurações para o novo conjunto de dados no Meu Espaço de Trabalho.
* **Outros conjuntos de dados.**  Alterne para Meu Espaço de Trabalho e clique no botão Obter Dados para se reconectar a todos os outros conjuntos de dados criados no Espaço de Trabalho Arquivado.  Talvez seja necessário inserir novamente as informações de conexão ou segurança.
* **Relatórios.**  Os relatórios contidos em arquivos do Excel ou do Power BI Desktop ou os relatórios instalados como parte de pacotes de conteúdo serão recriados automaticamente depois que você carregar novamente o arquivo do Excel ou do Power BI Desktop correspondente ou se reconectar ao pacote de conteúdo.  Se você criar seus próprios relatórios por meio do serviço Power BI, você precisará recriar esses relatórios no Meu Espaço de Trabalho.
* **Dashboards.**  Dashboards instalados como parte dos pacotes de conteúdo serão recriados automaticamente quando você se reconectar ao pacote de conteúdo no Meu Espaço de Trabalho.  Se você criar seus próprios painéis por meio do serviço Power BI, você precisará recriar esses painéis no Meu Espaço de Trabalho.

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](http://community.powerbi.com/)

