---
title: "Noções básicas do portal da Web do Servidor de Relatórios do Power BI"
description: "Leia sobre como navegar e trabalhar no portal da Web do Servidor de Relatório do Power BI."
services: powerbi
documentationcenter: 
author: maggiesMSFT
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
ms.date: 10/12/2017
ms.author: maggies
ms.openlocfilehash: 7d59531bfed80e854bc19b1df00aaf9cce7144d6
ms.sourcegitcommit: 99cc3b9cb615c2957dde6ca908a51238f129cebb
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/13/2017
---
# <a name="navigating-the-power-bi-report-server-web-portal"></a>Navegando no portal da Web do Servidor de Relatórios do Power BI
O portal da Web do Servidor de Relatório do Power BI é um local para exibir, armazenar e gerenciar seus relatórios paginados, móveis e do Power BI e KPIs.

![Portal da Web do Servidor de Relatórios](media/getting-around/report-server-web-portal.png)

É possível exibir o portal da Web em qualquer navegador moderno. No portal da Web, os KPIs e os relatórios são organizados em pastas e é possível marcá-los como favoritos. Também é possível armazenar as pastas de trabalho do Excel lá. No portal da Web, é possível iniciar as ferramentas necessárias para criar relatórios:

* **Relatórios do Power BI** criados com o Power BI Desktop: exiba-os no portal da Web e os aplicativos móveis do Power BI.
* **Relatórios paginados** criados no Construtor de Relatórios: documentos com aparência moderna e layout fixo otimizados para impressão.
* **KPIs** criados diretamente no portal da Web.

No portal da web, é possível procurar as pastas do servidor de relatório ou pesquisar relatórios específicos. É possível exibir um relatório, suas propriedades gerais e cópias antigas do relatório capturadas no histórico de relatórios. Dependendo de suas permissões, talvez você também possa assinar relatórios para entrega em sua caixa de entrada de email ou em uma pasta compartilhada no sistema de arquivos.

## <a name="web-portal-tasks"></a>Tarefas do portal da Web
É possível usar o portal da Web para um número de tarefas, incluindo estes:

* Exibir, pesquisar, imprimir e assinar relatórios.
* Criar, proteger e manter a hierarquia de pastas para organizar itens no servidor.
* Configurar propriedades de execução do relatório, histórico de relatórios e parâmetros de relatório.
* Criar agendas e fontes de dados compartilhadas para tornar as agendas e as conexões da fonte de dados mais gerenciáveis.
* Criar assinaturas controladas aos dados para acumular relatórios em uma grande lista de destinatários.
* Criar relatórios vinculados para reutilizar um relatório existente de diferentes maneiras.
* Baixar e abrir ferramentas comuns como o Power BI Desktop (Servidor de Relatório), Construtor de Relatórios e Publicador de Relatórios Móveis.
* [Criar KPIs](https://docs.microsoft.com/sql/reporting-services/working-with-kpis-in-reporting-services).
* Enviar comentários ou fazer solicitações de recursos.
* [Criando a identidade visual do portal da Web](https://docs.microsoft.com/sql/reporting-services/branding-the-web-portal)
* [Trabalhando com KPIs](https://docs.microsoft.com/sql/reporting-services/working-with-kpis-in-reporting-services)
* [Trabalhando com conjuntos de dados compartilhados](https://docs.microsoft.com/sql/reporting-services/work-with-shared-datasets-web-portal)

## <a name="web-portal-roles-and-permissions"></a>Permissões e funções de portal da Web
O portal da Web é um aplicativo Web executado em um navegador. Quando você inicia o portal da Web, as páginas, links e opções exibidas variam de acordo com as permissões que você tem no servidor de relatório. Se você tiver sido atribuído a uma função com permissões completas, você terá acesso ao conjunto completo de páginas e menus de aplicativo para gerenciar um servidor de relatório. Se você tiver sido atribuído a uma função com permissões para exibir e executar relatórios, você só verá os menus e páginas necessários para esses atividades. É possível ter diferentes atribuições de função para diferentes servidores de relatório ou até mesmo para os vários relatórios e pastas em um único servidor de relatório.

## <a name="start-the-web-portal"></a>Iniciar o portal da Web
1. Abra seu navegador da Web.
   
    Veja esta lista de [navegadores e versões com suporte](browser-support.md).
2. Na barra de endereços, digite a URL do portal da Web.
   
    Por padrão, a URL é *http://[ComputerName]/reports*.
   
    O servidor de relatório pode ser configurado para usar uma porta específica. Por exemplo, *http://[ComputerName]:80/reports* ou *http://[ComputerName]:8080/reports*
   
    Você verá que o portal da Web agrupa itens nestas categorias:
   
   * KPIs
   * Relatórios móveis
   * Relatórios paginados
   * Relatórios do Power BI Desktop
   * Pastas de trabalho do Excel
   * Conjuntos de dados
   * Fontes de dados
   * Recursos

## <a name="create-and-edit-power-bi-desktop-reports-pbix-files"></a>Criar e editar relatórios do Power BI Desktop (arquivos .pbix)
É possível exibir, carregar, criar, organizar e gerenciar permissões para relatórios do Power BI Desktop no portal da Web.

### <a name="create-a-power-bi-desktop-report"></a>Criar um relatório do Power BI Desktop
1. Selecione **Novo** > **Relatório do Power BI**.
   
    ![Criar um novo relatório do Power BI](media/getting-around/report-server-web-portal-new-powerbi-report.png)
   
    O aplicativo do Power BI Desktop é aberto.
   
    ![Aplicativo Power BI Desktop](media/getting-around/report-server-powerbi-desktop-start.png)
2. Crie seu relatório do Power BI. Consulte [Início rápido: relatórios do Power BI](quickstart-create-powerbi-report.md) para obter detalhes.
3. Carregue seu relatório no servidor de relatório.

### <a name="edit-an-existing-power-bi-desktop-report"></a>Editar um relatório do Power BI Desktop existente
1. Selecione as reticências (**...** ) no canto superior direito do bloco do relatório > **Editar no Power BI Desktop**.
   
    ![Editar no Power BI Desktop](media/getting-around/report-server-web-portal-pbix-ellipsis.png)
   
    O aplicativo do Power BI Desktop é aberto.
2. Fazer as alterações e salvar... [como?]

## <a name="create-and-edit-paginated-reports-rdl-files"></a>Criar e editar relatórios paginados (arquivos .rdl)
É possível exibir, carregar, criar, organizar e gerenciar permissões para relatórios paginados no portal da Web.

### <a name="create-a-paginated-report"></a>Criar um relatório paginado
1. Selecione **Novo** > **Paginado relatório**.
   
    O aplicativo do Construtor de Relatórios é aberto.
   
    ![Novo relatório do Construtor de Relatórios](media/getting-around/report-server-report-builder-new.png)
2. Criar um relatório paginado. Consulte [Início rápido: relatórios paginados](quickstart-create-paginated-report.md) para obter detalhes.
3. Carregue seu relatório no servidor de relatório.

### <a name="edit-an-existing-paginated-report"></a>Editar um relatório paginado existente
1. Selecione as reticências (... ) no canto superior direito do bloco do relatório > **Editar no Construtor de Relatórios**.
   
    ![Editar no Construtor de Relatórios](media/getting-around/report-server-web-portal-rdl-ellipsis.png)
   
    O aplicativo do Construtor de Relatórios é aberto.
2. Faça suas alterações e salve.

## <a name="upload-and-organize-excel-workbooks"></a>Carregar e organizar pastas de trabalho do Excel
É possível carregar, organizar e gerenciar permissões para relatórios do Power BI Desktop e pastas de trabalho do Excel. Eles serão agrupados no portal da Web.

As pastas de trabalho são armazenadas em um Servidor de Relatório do Power BI, semelhante a outros arquivos de recurso. Selecionar uma das pastas de trabalho a baixa localmente em sua área de trabalho. É possível salvar as alterações feitas carregando-as novamente para o servidor de relatório.

## <a name="manage-items-in-the-web-portal"></a>Gerenciar itens no portal da Web
O Servidor de Relatório do Power BI oferece controle detalhado dos itens que você armazena no portal da Web. Por exemplo, é possível configurar as assinaturas, cache, instantâneos e segurança em relatórios paginados individuais.

1. Selecione as reticências (...) no canto superior direito de um item e, em seguida, selecione **Gerenciar**.
   
    ![Selecionar Gerenciar](media/getting-around/report-server-web-portal-manage-ellipsis.png)
2. Escolha a propriedade ou outro recurso que você deseja definir.
   
    ![Selecionar uma propriedade](media/getting-around/report-server-web-portal-manage-properties.png)
3. Selecione **Aplicar**.

Leia mais sobre como [trabalhar com assinaturas no portal da Web](https://docs.microsoft.com/sql/reporting-services/working-with-subscriptions-web-portal).

## <a name="tag-your-favorite-reports-and-kpis"></a>Marcar seus relatórios e KPIs favoritos
É possível marcar os relatórios e os KPIs que você deseja que sejam favoritos. Eles são mais fáceis de localizar porque são reunidos em uma única pasta de favoritos, no portal da Web e nos aplicativos móveis do Power BI. 

1. Selecione a elipse (**…**) no canto superior direito do KPI ou do relatório que você deseja tornar um favorito e selecione **Adicionar a favoritos**.
   
    ![Adicionar aos Favoritos](media/getting-around/report-server-web-portal-favorite-ellipsis.png)
2. Selecione **Favoritos** na faixa de opções do portal da web para vê-lo junto com os outros favoritos na página Favoritos no portal da web.
   
    ![Exibir Favoritos](media/getting-around/report-server-web-portal-favorites.png)
   
    Agora, nos aplicativos móveis do Power BI, você verá esses favoritos juntamente com seus dashboards favoritos do serviço do Power BI.
   
    ![Exibir Favoritos no aplicativo móvel](media/getting-around/power-bi-iphone-faves-report-server.png)

## <a name="hide-or-view-items-in-the-web-portal"></a>Ocultar ou exibir itens no portal da Web
É possível ocultar itens no portal da Web e optar por exibir itens ocultos.

### <a name="hide-an-item"></a>Ocultar um item
1. Selecione as reticências (...) no canto superior direito de um item e, em seguida, selecione **Gerenciar**.
   
    ![Selecionar gerenciar](media/getting-around/report-server-web-portal-manage-ellipsis.png)
2. Selecione **Ocultar este item**.
   
    ![Selecionar Ocultar](media/getting-around/report-server-web-portal-hide-property.png)
3. Selecione **Aplicar**.

### <a name="view-hidden-items"></a>Exibir itens ocultos
1. Selecione **Blocos** (ou **Lista**) no canto superior direito > **Mostrar itens ocultos**.
   
    Os itens são exibidos. Eles estão esmaecidos, mas ainda é possível abri-los e editá-los.
   
    ![Exibir itens ocultos](media/getting-around/report-server-web-portal-show-hidden-grayed.png)

## <a name="search-for-items"></a>Pesquisar itens
É possível entrar em uma equipe de pesquisa e você verá que tudo que puder acessar. Os resultados são categorizados nos KPIs, relatórios, conjuntos de dados e outros itens. Em seguida, é possível interagir com os resultados e adicioná-los aos seus favoritos.  

![Pesquisar itens](media/getting-around/report-server-web-portal-search.png)

## <a name="move-or-delete-items-in-list-view"></a>Mover ou excluir itens na exibição de lista
Por padrão, o portal da Web exibe seu conteúdo em exibição de bloco.

É possível mudar para a exibição de lista, em que é fácil mover ou excluir vários itens ao mesmo tempo. 

1. Selecione **Blocos** > **Lista**.
   
    ![Alternar modos de exibição](media/getting-around/report-server-web-portal-list-view.png)
2. Selecione os itens e, em seguida, selecione **Mover** ou **Excluir**.

## <a name="next-steps"></a>Próximas etapas
[Manual do usuário](user-handbook-overview.md)  
[Início rápido: relatórios paginados](quickstart-create-paginated-report.md)  
[Início rápido: relatórios do Power BI](quickstart-create-powerbi-report.md)

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)

