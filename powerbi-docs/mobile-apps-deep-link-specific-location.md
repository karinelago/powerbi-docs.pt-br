---
title: Criar um link para um local específico nos aplicativos móveis do Power BI
description: Saiba como criar um link profundo para um painel, bloco ou relatório específico no aplicativo móvel do Power BI com um Uniform Resource Identifier (URI).
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-mobile
ms.topic: conceptual
ms.date: 10/13/2017
ms.author: maggies
ms.openlocfilehash: 3be6882219e23a2d22ee03e6805ce3a1e8e08b8f
ms.sourcegitcommit: 80d6b45eb84243e801b60b9038b9bff77c30d5c8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34297712"
---
# <a name="create-a-link-to-a-specific-location-in-the-power-bi-mobile-apps"></a>Criar um link para um local específico nos aplicativos móveis do Power BI
Você pode criar e usar um Uniform Resource Identifier (URI) para vincular a um local específico (um *link profundo*) dentro dos aplicativos móveis do Power BI em todas as plataformas móveis: iOS, dispositivos Android e Windows 10.

Links de URI podem apontar diretamente para relatórios, painéis e blocos.

O destino do link profundo determina o formato do URI. Siga estas etapas para criar links profundos para locais diferentes. 

## <a name="open-the-power-bi-mobile-app"></a>Abra o aplicativo móvel de Power BI
Use esse URI para abrir o aplicativo móvel do Power BI em qualquer dispositivo:

    mspbi://app/


## <a name="open-to-a-specific-dashboard"></a>Abrir em um painel específico
Esse URI abre o aplicativo móvel do Power BI em painel específico:

    mspbi://app/OpenDashboard?DashboardObjectId=<36-character-dashboard-id>

Para localizar a ID de objeto de 36 caracteres do painel, navegue até o painel específico no serviço do Power BI (https://powerbi.com). Por exemplo, veja a seção realçada desta URL:

https://powerbi.com/groups/me/dashboards/**61b7e871-cb98-48ed-bddc-6572c921e270**

Se o painel estiver em um grupo diferente do grupo Meu Espaço de Trabalho, adicione `&GroupObjectId=<36-character-group-id>` antes ou após a ID do painel. Por exemplo, 

mspbi://app/OpenDashboard?DashboardObjectId=e684af3a-9e7f-44ee-b679-b9a1c59b5d60 **&GroupObjectId=8cc900cc-7339-467f-8900-fec82d748248**

Observe o E comercial (&) entre os dois.

## <a name="open-to-a-specific-tile-in-focus"></a>Abrir em um bloco específico em foco
Esse URI abre um bloco específico em foco no aplicativo móvel do Power BI:

    mspbi://app/OpenTile?DashboardObjectId=<36-character-dashboard-id>&TileObjectId=<36-character-tile-id>

Para localizar a ID de objeto de 36 caracteres, do painel e do bloco, navegue até o painel específico no serviço do Power BI (https://powerbi.com) e abra o bloco em modo de foco. Por exemplo, veja as seções realçadas desta URL:

https://powerbi.com/groups/me/dashboards/**3784f99f-b460-4d5e-b86c-b6d8f7ec54b7**/tiles/**565f9740-5131-4648-87f2-f79c4cf9c5f5**/infocus

Para este bloco, o URI seria:

    mspbi://app/OpenTile?DashboardObjectId=3784f99f-b460-4d5e-b86c-b6d8f7ec54b7&TileObjectId=565f9740-5131-4648-87f2-f79c4cf9c5f5

Observe o E comercial (&) entre os dois.

Se o painel estiver em um grupo diferente do grupo Meu Espaço de Trabalho, adicione `&GroupObjectId=<36-character-group-id>`

## <a name="open-to-a-specific-report"></a>Abra em um relatório específico
Esse URI abre um relatório específico no aplicativo móvel do Power BI:

    mspbi://app/OpenReport?ReportObjectId=<36-character-report-id>

Para localizar a ID de objeto de 36 caracteres do relatório, navegue até o relatório específico no serviço do Power BI (https://powerbi.com). Por exemplo, veja a seção realçada desta URL:

https://powerbi.com/groups/me/reports/**df9f0e94-31df-450b-b97f-4461a7e4d300**

## <a name="open-to-a-specific-report-page"></a>Abrir em uma página específica do relatório
Esse URI abre uma página de relatório específico no aplicativo móvel do Power BI:

    mspbi://app/OpenReport?ReportObjectId=<36-character-report-id>&reportPage=ReportSection<number>

A página do relatório é chamada "ReportSection" seguida por um número. Novamente, abra o relatório no serviço do Power BI (https://powerbi.com) e navegue até a página específica do relatório. 

Por exemplo, veja a seção realçada desta URL:

https://powerbi.com/groups/me/reports/df9f0e94-31df-450b-b97f-4461a7e4d300/**ReportSection11**

## <a name="open-in-full-screen-mode"></a>Abrir no modo de tela inteira
Adicione o parâmetro em negrito para abrir em um relatório específico no modo de tela inteira:

    mspbi://app/OpenReport?ReportObjectId=<36-character-report-id>**&openFullScreen=true**

Por exemplo: 

mspbi://app/OpenReport?ReportObjectId=500217de-50f0-4af1-b345-b81027224033&openFullScreen=true

## <a name="add-context-optional"></a>Adicionar contexto (opcional)
Você também pode adicionar contexto na cadeia de caracteres. Em seguida, se precisar entrar em contato conosco, podemos usar esse contexto para filtrar nossos dados para seu aplicativo. Adicione `&context=<app-name>` ao link

Por exemplo, veja a seção realçada desta URL: 

https://powerbi.com/groups/me/reports/df9f0e94-31df-450b-b97f-4461a7e4d300/**&context=SlackDeepLink**

## <a name="next-steps"></a>Próximas etapas
Seus comentários nos ajudam a decidir o que implementar no futuro, portanto, não se esqueça de votar em outros recursos que você gostaria de ver em aplicativos móveis do Power BI. 

* [Aplicativos do Power BI para dispositivos móveis](mobile-apps-for-mobile-devices.md)
* Siga @MSPowerBI no Twitter
* Participe da conversa na [Comunidade do Power BI](http://community.powerbi.com/)
* [Introdução ao Power BI](service-get-started.md)

