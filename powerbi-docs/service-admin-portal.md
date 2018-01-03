---
title: "Portal de administração do Power BI"
description: "O portal de administração permite o gerenciamento de locatário do Power BI em sua organização. Inclui itens como métricas de uso, o acesso ao centro de administração do Office 365 e configurações."
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
ms.date: 11/27/2017
ms.author: asaxton
ms.openlocfilehash: d831363d6afa88aa94d78776f59f81ba8ba96299
ms.sourcegitcommit: 85302d577895e779466df55aa02e5785ab2e3138
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/18/2017
---
# <a name="power-bi-admin-portal"></a>Portal de administração do Power BI

O portal de administração permite o gerenciamento de locatário do Power BI em sua organização. Inclui itens como métricas de uso, o acesso ao centro de administração do Office 365 e configurações.

O Gerenciamento de locatário do Power BI para sua empresa é feito por meio do portal de administração do Power BI. O portal de administração é acessível a todos os usuários que são administradores globais no Office 365 ou que receberam a função de administrador de serviços do Power BI. Para obter mais informações sobre a função de administrador de serviços do Power BI, consulte [Noções básicas sobre a função de administrador do Power BI](service-admin-role.md).

Todos os usuários verão **Portal de administração** no ícone de engrenagem. Se não forem administradores, eles verão apenas a seção **Configurações Premium** e verão somente as capacidades que têm direitos para gerenciar.

## <a name="how-to-get-to-the-admin-portal"></a>Como obter o portal de administração

Sua conta deve ser marcada como **Administrador Global** no Office 365 ou no Azure Active Directory ou ter recebido a função de administrador de serviços do Power BI, para obter acesso ao portal de administração do Power BI. Para obter mais informações sobre a função de administrador de serviços do Power BI, consulte [Noções básicas sobre a função de administrador do Power BI](service-admin-role.md). Para acessar o portal de administração do Power BI, faça o seguinte:

1. Selecione a engrenagem de configurações na parte superior direita do serviço do Power BI.
2. Selecione **Portal de Administração**.

![](media/service-admin-portal/powerbi-admin-settings.png)

No portal, há cinco guias. Elas estão descritas abaixo.

* [Métricas de uso](#usage-metrics)
* [Usuários](#users)
* [Logs de auditoria](#audit-logs)
* [Configurações de locatário](#tenant-settings)
* [Configurações Premium](#premium-settings)
* [Códigos de inserção](#embed-codes)

![](media/service-admin-portal/powerbi-admin-landing-page.png)

## <a name="usage-metrics"></a>Métricas de uso
A primeira guia, no portal de administração, é **Métricas de uso**. O relatório de métricas de uso permite monitorar o uso no Power BI para sua organização. Ele também fornece a capacidade de ver quais usuários e grupos são mais ativos no Power BI para sua organização.

> [!NOTE]
> Na primeira vez que acessar o dashboard ou depois de visitar novamente após um longo período de não exibição do dashboard, você provavelmente encontrará uma tela de carregamento enquanto carregamos o dashboard.

Quando o painel for carregado, você encontrará suas seções de blocos. A primeira seção inclui dados de uso para usuários individuais e a segunda seção tem informações semelhantes para grupos em sua organização.

Aqui está uma análise do que você vê em cada bloco:

* Contagem distinta de todos os painéis, relatórios e conjuntos de dados no espaço de trabalho do usuário
  
    ![](media/service-admin-portal/powerbi-admin-usage-metrics-number-tiles.png)

* Painel mais consumido pelo número de usuários que podem acessá-lo. Por exemplo, se você tem um painel que compartilhou com 3 usuários e também o adiciona a um pacote de conteúdo com dois usuários conectados a ele, sua contagem é 6 (1 + 3 + 2)
  
    ![](media/service-admin-portal/powerbi-admin-usage-metrics-top-dashboards.png)

* Os conteúdo mais populares aos quais os usuários estão conectados. Isso pode ser qualquer coisa que os usuários podem acessar através do processo Obter Dados, portanto, pacotes de conteúdo SaaS, pacotes de conteúdo organizacional, arquivos ou bancos de dados de conteúdo.
  
    ![](media/service-admin-portal/powerbi-admin-usage-metrics-top-connections.png)

* Uma exibição de seus principais usuários sobre quantos painéis eles têm, incluindo painéis criados por eles mesmos e painéis compartilhados com eles.
  
    ![](media/service-admin-portal/powerbi-admin-usage-metrics-top-users-dashboards.png)

* Uma exibição de seus principais usuários com base em quantos relatórios eles têm
  
    ![](media/service-admin-portal/powerbi-admin-usage-metrics-top-users-reports.png)

A segunda seção mostra o mesmo tipo de informação, mas com base em grupos. Isso permitirá que você veja quais grupos em sua organização são mais ativos e quais tipos de informações eles estão usando.

Com essas informações, você poderá obter informações reais de como as pessoas estão usando o Power BI em toda a organização e ser capaz de reconhecer esses usuários e grupos, que são muito ativos na sua organização.

## <a name="users"></a>Usuários

A segunda guia, no portal de administração, **Gerenciar usuários**. Gerenciamento de usuário, para o Power BI, é feito no centro de administração do Office 365, esta seção permite que você chegue rapidamente à área para gerenciar usuários, administradores e grupos no Office 365.

![](media/service-admin-portal/powerbi-admin-manage-users.png)

Quando você clicar em **Ir para o Centro de Administração do O365**, vá diretamente para a página de aterrissagem do centro de administração do Office 365 para gerenciar os usuários do seu locatário.

![](media/service-admin-portal/powerbi-admin-o365-admin-center.png)

## <a name="audit-logs"></a>Logs de auditoria

A terceira guia, no portal de administração, é **Logs de auditoria**. Os logs estão localizados no Centro de Conformidade e Segurança do Office 365. Esta seção permite acessar rapidamente essa área no Office 365. 

Para obter mais informações sobre logs de auditoria, consulte [Auditoria do Power BI em sua organização](service-admin-auditing.md)

## <a name="tenant-settings"></a>Configurações de locatário

A terceira guia, no portal de administração, é **Configurações de locatário**. As configurações de locatário oferecem mais controle sobre quais recursos são disponibilizados para sua organização. Se você tiver dúvidas relacionadas a dados confidenciais, alguns dos nossos recursos poderão não ser adequados para sua organização, ou talvez você queira apenas que um determinado recurso esteja disponível para um grupo específico. Se esse for o caso, você pode desativá-lo em seu locatário.

![](media/service-admin-portal/powerbi-admin-tenant-settings.png)

> [!NOTE]
> Pode levar até 10 minutos para que a configuração entre em vigor para todos em seu locatário.

As configurações podem ter três estados com base nas configurações que você forneceu.

### <a name="disabled-for-the-entire-organization"></a>Desabilitado para toda a organização

Você pode desabilitar um recurso e fazer isso de forma que os usuários não poderão usá-lo.

![](media/service-admin-portal/powerbi-admin-tenant-settings-disabled.png)

### <a name="enabled-for-the-entire-organization"></a>Habilitado para toda a organização

Você pode habilitar um recurso para toda a organização, o que permitirá que todos os usuários tenham acesso a esse recurso.

![](media/service-admin-portal/powerbi-admin-tenant-settings-enabled.png)

### <a name="enabled-for-a-subset-of-the-organization"></a>Habilitado para um subconjunto da organização

Você também pode habilitar um recurso para uma parte de sua organização. Isso pode ocorrer de algumas formas diferentes. Você pode habilitá-lo para toda a organização, exceto para um grupo específico de usuários.

![](media/service-admin-portal/powerbi-admin-tenant-settings-enabled-except.png)

Você também pode habilitar o recurso apenas para um grupo específico de usuários e também desabilitá-lo para um grupo de usuários. Isso garantiria que determinados usuários não tivessem acesso ao recurso, mesmo se estivessem no grupo permitido.

![](media/service-admin-portal/powerbi-admin-tenant-settings-enabled-except2.png)

## <a name="export-and-sharing-settings"></a>Configurações de exportação e compartilhamento

### <a name="share-content-to-external-users"></a>Compartilhar conteúdo com usuários externos

Os usuários da organização podem compartilhar dashboards com usuários fora da organização.

![](media/service-admin-portal/powerbi-admin-sharing-external.png)

### <a name="publish-to-web"></a>Publicar na Web

Os usuários na organização podem publicar relatórios na Web. [Saiba mais](service-publish-to-web.md)

![](media/service-admin-portal/powerbi-admin-publish-to-web.png)

Os usuários verão diferentes opções na interface do usuário conforme a configuração de Publicar na Web.

|Recurso |Habilitado para toda a organização |Desabilitado para toda a organização |Especificar grupos de segurança   |
|---------|---------|---------|---------|
|**Publicar na Web** no menu **Arquivo** do relatório.|Habilitado para todos|Não visível para todos|Visível somente para usuários ou grupos autorizados.|
|**Gerenciar códigos de inserção** em **Configurações**|Habilitado para todos|Habilitado para todos|Habilitado para todos<br><br>Opção * **Excluir** somente para usuários ou grupos autorizados.<br>* **Obter códigos** habilitados para todos.|
|**Códigos de inserção** no portal de administração|O status refletirá o seguinte:<br>* Ativo<br>* Sem suporte<br>* Bloqueado|O status exibirá **Desabilitado**|O status refletirá o seguinte:<br>* Ativo<br>* Sem suporte<br>* Bloqueado<br><br>Se um usuário não estiver autorizado conforme a configuração do locatário, o status exibirá **violado**.|
|Relatórios publicados existentes|Tudo habilitado|Tudo desabilitado|Os relatórios continuam a ser renderizados para todos.|

### <a name="export-data"></a>Exportar dados

Os usuários na organização podem exportar dados de um bloco ou visualização. [Saiba mais](power-bi-visualization-export-data.md)

![](media/service-admin-portal/powerbi-admin-export-data.png)

> [!NOTE]
> Desabilitar a opção **Exportar dados** também impedirá os usuários de usar o recurso **Analisar no Excel**, bem como de usar a conexão dinâmica do serviço do Power BI.

### <a name="export-reports-as-powerpoint-presentations"></a>Exportar relatórios como apresentações do PowerPoint

Os usuários na organização podem exportar relatórios do Power BI como arquivos do PowerPoint. [Saiba mais](service-publish-to-powerpoint.md)

![](media/service-admin-portal/powerbi-admin-powerpoint.png)

### <a name="print-dashboards-and-reports"></a>Imprimir dashboards e relatórios

Os usuários na organização podem imprimir dashboards e relatórios. [Saiba mais](service-print.md)

![](media/service-admin-portal/powerbi-admin-print-dashboard.png)

![](media/service-admin-portal/powerbi-admin-print-report.png)

## <a name="content-pack-settings"></a>Configurações do pacote de conteúdo

### <a name="publish-content-packs-to-the-entire-organization"></a>Publicar pacotes de conteúdo em toda a organização

Os usuários na organização podem publicar pacotes de conteúdo em toda a organização.

![](media/service-admin-portal/powerbi-admin-publish-entire-org.png)

### <a name="create-template-organizational-content-packs"></a>Criar pacotes de conteúdos organizacionais de modelo

Os usuários na organização podem criar pacotes de conteúdo de modelo que usam conjuntos de dados criados em uma fonte de dados no Power BI Desktop.

## <a name="integration-settings"></a>Configurações de integração

### <a name="ask-questions-about-data-using-cortana"></a>Faça perguntas sobre dados usando a Cortana
Os usuários na organização podem fazer perguntas sobre seus dados usando a Cortana.

> [!NOTE]
> Essa configuração se aplica a toda a organização e não pode ser limitada a grupos específicos.

### <a name="use-analyze-in-excel-with-on-premises-datasets"></a>Usar a opção Analisar no Excel com conjuntos de dados locais
Os usuários na organização podem usar o Excel para exibir e interagir com conjuntos de dados locais do Power BI. [Saiba mais](service-analyze-in-excel.md)

> [!NOTE]
> Ao desabilitar a opção **Exportar dados**, os usuários também serão impedidos de usar o recurso **Analisar no Excel**.

### <a name="user-arcgis-maps-for-power-bi-preview"></a>Usuário do ArcGIS Maps para o Power BI (Versão prévia)

Os usuários na organização podem usar a visualização dos Mapas do ArcGIS para o Power BI (Versão prévia) fornecida pelo Esri. [Saiba mais](power-bi-visualization-arcgis.md)

## <a name="r-visuals-settings"></a>Configurações de elementos visuais do R

### <a name="interact-with-an-dshare-r-visuals"></a>Interagir e compartilhar elementos visuais do R

Os usuários na organização podem interagir e compartilhar elementos visuais criados com scripts do R. [Saiba mais](service-r-visuals.md)

> [!NOTE]
> Essa configuração se aplica a toda a organização e não pode ser limitada a grupos específicos.

## <a name="audit-settings"></a>Configurações de auditoria

### <a name="create-audit-logs-for-internal-activity-auditing-and-compliance"></a>Criar registos de auditoria para fins de auditoria de atividade interna e de conformidade

Os usuários na organização podem usar a auditoria para monitorar as ações executadas no Power BI por outros usuários na organização. [Saiba mais](service-admin-auditing.md)

Essa configuração deve ser habilitada para que as entradas de log de auditoria sejam registradas.

> [!NOTE]
> Essa configuração se aplica a toda a organização e não pode ser limitada a grupos específicos.

## <a name="dashboard-settings"></a>Configurações do dashboard

### <a name="data-classification-for-dashboards"></a>Classificação de dados para dashboards

Os usuários na organização podem marcar dashboards com classificações indicando os níveis de segurança do dashboard. [Saiba mais](service-data-classification.md)

> [!NOTE]
> Essa configuração se aplica a toda a organização e não pode ser limitada a grupos específicos.

## <a name="developer-settings"></a>Configurações do desenvolvedor

### <a name="embed-content-in-apps"></a>Inserir conteúdo em aplicativos

Usuários da organização podem inserir relatórios e dashboards do Power BI em aplicativos de SaaS (software como serviço). Desabilitar essa configuração impedirá que os usuários usem as APIs REST para inserir conteúdo do Power BI em seus aplicativos.

## <a name="premium-settings"></a>Configurações Premium

A guia de Configurações Premium permite que você gerencie qualquer capacidade Premium do Power BI que tiver sido comprada para sua organização. Todos os usuários em sua organização verão a guia de Configurações Premium, mas eles só verão conteúdo dentro dela se forem atribuídos como **Administradores de capacidade** ou se forem um usuário com permissões de atribuição. Se um usuário não tiver nenhuma permissão, ele verá a seguinte mensagem de erro.

![](media/service-admin-portal/premium-settings-no-access.png "Sem acesso às configurações Premium")

Para obter mais informações sobre como gerenciar as configurações Premium, consulte [Gerenciar o Power BI Premium](service-admin-premium-manage.md).

## <a name="embed-codes"></a>Códigos de inserção

![Códigos de inserção dentro do portal de administração do Power BI](media/service-admin-portal/embed-codes.png)

Como administrador, você pode exibir os códigos de inserção que são gerados para seu locatário. Você possui as ações de exibir o relatório e excluir o código de inserção para revogá-lo.

## <a name="next-steps"></a>Próximas etapas

[Noções básicas sobre a função de administrador do Power BI](service-admin-role.md)  
[Auditoria do Power BI em sua organização](service-admin-auditing.md)  
[Gerenciar o Power BI Premium](service-admin-premium-manage.md)  
[Administração do Power BI em sua organização](service-admin-administering-power-bi-in-your-organization.md)  

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](http://community.powerbi.com/)