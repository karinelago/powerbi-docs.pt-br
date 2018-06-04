---
title: Comparando o Servidor de Relatórios do Power BI e o serviço do Power BI
description: Este artigo compara os recursos do Servidor de Relatórios do Power BI e o serviço do Power BI.
keywords: ''
author: maggiesMSFT
ms.author: maggies
ms.date: 05/07/2018
ms.topic: overview
ms.service: powerbi
ms.component: powerbi-report-server
manager: kfile
ms.custom: mvc
ms.openlocfilehash: c47722fda28fc45289858f082a0838f583b53dbb
ms.sourcegitcommit: 80d6b45eb84243e801b60b9038b9bff77c30d5c8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34296769"
---
# <a name="comparing-power-bi-report-server-and-the-power-bi-service"></a>Comparando o Servidor de Relatórios do Power BI e o serviço do Power BI

O Servidor de Relatórios do Power BI e o serviço do Power BI têm muitas semelhanças e algumas diferenças importantes. Esta tabela explica qual é qual.

| Recursos | Servidor de Relatório do Power BI | Serviço do Power BI | Observações
|---------|---------|---------|---------|
| Implantação | Local ou nuvem hospedada | Nuvem | O Servidor de Relatórios do Power BI pode ser implantado em VMs do Azure (nuvem hospedada) se licenciado por meio do Power BI Premium
| Dados de origem | Nuvem e/ou local | Nuvem e/ou local |  
| Licença | Power BI Premium ou EE do SQL Server com SA | Power BI Pro e/ou Power BI Premium |  
| Ciclo de vida | Política de ciclo de vida moderna | Serviço totalmente gerenciado |  
| Ciclo de lançamento | Uma vez a cada 4 meses | Uma vez por mês | Correções e recursos mais recentes são fornecidos para o serviço do Power BI primeiro. A maior parte das funcionalidades principais é fornecida para o Servidor de Relatórios do Power BI nas próximas versões; alguns recursos são destinados somente ao serviço do Power BI.
| Criar relatórios do Power BI no Power BI Desktop | Sim | Sim |  
| Criar relatórios do Power BI no navegador | Não | Sim |  
| Gateway necessário | Não | Sim para fontes de dados locais |  
| Streaming em tempo real | Não | Sim | [Streaming em tempo real no Power BI](../service-real-time-streaming.md)
| Dashboards | Não | Sim | [Dashboards no serviço do Power BI](../service-dashboards.md) 
| Distribuir grupo de relatórios usando aplicativos | Não | Sim | [Criar e publicar aplicativos com dashboards e relatórios](../service-create-distribute-apps.md) 
| Pacotes de Conteúdo | Não | Sim | [Pacotes de conteúdo organizacional: introdução](../service-organizational-content-pack-introduction.md) 
| Conectar-se a serviços como o Salesforce | Não | Sim | [Conectar-se aos serviços que você usa](../service-connect-to-services.md) com o serviço do Power BI
| P e R | Não | Sim | [P e R no serviço do Power BI e Power BI Desktop](../power-bi-q-and-a.md) 
| Insights rápidos | Não | Sim | [Gerar automaticamente as informações sobre os dados com o Power BI](../service-insights.md) 
| Analisar no Excel | Não | Sim | [Analisar no Excel](../service-analyze-in-excel.md) 
| Relatórios paginados | Sim | Não | Relatórios paginados não estão disponíveis no serviço do Power BI, mas você pode [fixar itens de relatório paginados a dashboards do Power BI](https://docs.microsoft.com/sql/reporting-services/pin-reporting-services-items-to-power-bi-dashboards)
| Aplicativos móveis do Power BI | Sim | Sim | [Visão geral de aplicativos móveis no Power BI](../mobile-apps-for-mobile-devices.md) 
| Mapas do ARC GIS | Não | Sim | [Mapas do ArcGIS no serviço do Power BI e no Power BI Desktop pelo ESRI](../power-bi-visualization-arcgis.md)
| Assinaturas de email para relatórios do Power BI | Não | Sim | [Assinar um relatório ou dashboard](../service-report-subscribe.md) no serviço do Power BI 
| Assinaturas de email para relatórios paginados | Sim | Não | [Entrega de email no Reporting Services](https://docs.microsoft.com/sql/reporting-services/subscriptions/e-mail-delivery-in-reporting-services)  
| Alertas de dados | Não | Sim | [Alertas de dados](../service-set-data-alerts.md) no serviço do Power BI
| Segurança em nível de linha | Somente por meio da fonte de dados no modo DirectQuery | Disponível nos modos de DirectQuery (fonte de dados) e de Importação | [RLS (segurança em nível de linha)](../service-admin-rls.md) com o Power BI 
| Modo de tela inteira | Não | Sim | [Modo de tela inteira](../service-fullscreen-mode.md) no serviço do Power BI 
| Colaboração avançada com o Office 365 | Não | Sim | [Colaborar em um espaço de trabalho de aplicativo](../service-collaborate-power-bi-workspace.md) com o Office 365 
| Visuais do R | Não | Sim | [Criar visuais do R](../service-r-visuals.md) no serviço do Power BI  
| Recursos de versão prévia | Não | Sim | [Aceitar recursos de visualização do serviço](../service-preview-features.md) do Power BI 
| Elementos visuais personalizados | Sim | Sim | [Elementos visuais personalizados no Power BI](../power-bi-custom-visuals.md) 
| Power BI Desktop | Versão otimizada para o Servidor de Relatório, disponível para download com o Servidor de Relatório | Versão otimizado para o serviço do Power BI, disponível na Windows Store | [Power BI Desktop para o servidor de relatório](https://powerbi.microsoft.com/report-server/) <br><br> [Power BI Desktop para o serviço do Power BI](http://aka.ms/pbidesktopstore)

## <a name="next-steps"></a>Próximas etapas
[Instalar o Servidor de Relatório do Power BI](install-report-server.md)  



