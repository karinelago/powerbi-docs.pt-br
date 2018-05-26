---
title: O que é o Servidor de Relatórios do Power BI?
description: Tenha uma visão geral do Servidor de Relatórios do Power BI para entender como ele se encaixa no SSRS (Microsoft SQL Server Reporting Services) e no restante do Power BI.
keywords: ''
author: maggiesMSFT
ms.author: maggies
ms.date: 05/07/2018
ms.topic: overview
ms.service: powerbi
ms.component: powerbi-report-server
manager: kfile
ms.custom: mvc
ms.openlocfilehash: 1be2270074011f73c3d942677211dd99d18c6b2b
ms.sourcegitcommit: 638de55f996d177063561b36d95c8c71ea7af3ed
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/17/2018
---
# <a name="what-is-power-bi-report-server"></a>O que é o Servidor de Relatórios do Power BI?

O Servidor de Relatórios do Power BI é um servidor de relatórios local com um portal da Web no qual você pode exibir e gerenciar KPIs e relatórios, juntamente com as ferramentas para criar relatórios, relatórios paginados, relatórios móveis e KPIs do Power BI. Seus usuários podem acessar esses relatórios de maneiras diferentes: exibindo-os em um navegador da Web ou dispositivo móvel, ou como um email em sua caixa de entrada.

![Portal da Web do Servidor de Relatório do Power BI](media/get-started/power-bi-report-server-overview.png)

## <a name="comparing-power-bi-report-server"></a>Comparando o Servidor de Relatórios do Power BI 
O Servidor de Relatórios do Power BI é semelhante ao SQL Server Reporting Services e ao serviço do Power BI online, mas de maneiras diferentes. Assim como o serviço do Power BI, o Servidor de Relatórios do Power BI hospeda relatórios do Power BI (.PBIX) e arquivos do Excel. Assim como o Reporting Services, o Servidor de Relatórios do Power BI é local e hospeda relatórios paginados (.RDL). O Servidor de Relatórios do Power BI é um superconjunto do Reporting Services: tudo o que você pode fazer no Reporting Services, pode fazer com o Servidor de Relatórios do Power BI e mais, com a adição de suporte para relatórios do Power BI. Confira [Comparando o Servidor de Relatórios do Power BI e o serviço do Power BI](compare-report-server-service.md) para obter detalhes.

## <a name="licensing-power-bi-report-server"></a>Licenciando o Servidor de Relatórios do Power BI
O Servidor de Relatórios do Power BI está disponível por meio de duas licenças diferentes: [Power BI Premium](../service-premium.md) e [SQL Server Enterprise Edition](https://www.microsoft.com/sql-server/sql-server-2017-editions) com Software Assurance. Com uma licença do Power BI Premium, você pode criar uma implantação híbrida combinando recursos locais e na nuvem.  

## <a name="web-portal"></a>Portal da Web
O ponto de entrada do Servidor de Relatórios do Power BI é um portal da Web seguro que pode ser exibido em qualquer navegador moderno. Aqui, você pode acessar todos os seus relatórios e KPIs. O conteúdo no portal da Web é organizado em uma hierarquia de pastas tradicional. Em suas pastas, o conteúdo é agrupado por tipo: relatórios do Power BI, relatórios móveis, relatórios paginados e KPIs, além de pastas de trabalho do Excel, conjuntos de dados compartilhados e fontes de dados compartilhadas para serem usadas como blocos de construção para seus relatórios. Você pode marcar favoritos para exibi-los em uma única pasta. E é possível criar KPIs diretamente no portal da Web. 

![Portal da Web do Servidor de Relatório do Power BI](media/get-started/web-portal.png)

Dependendo de suas permissões, você poderá gerenciar o conteúdo no portal da Web. É possível agendar o processamento de relatórios, acessar relatórios sob demanda e assinar relatórios publicados. Também é possível aplicar sua própria [identidade visual](https://docs.microsoft.com/sql/reporting-services/branding-the-web-portal) personalizada ao seu portal da Web. 

Mais informações sobre o [portal da Web do Servidor de Relatórios do Power BI](https://docs.microsoft.com/sql/reporting-services/web-portal-ssrs-native-mode).

## <a name="power-bi-reports"></a>Relatórios do Power BI
Você cria relatórios do Power BI (.PBIX) com a versão do Power BI Desktop otimizada para o servidor de relatórios. Em seguida, você os publica e exibe no portal da Web em seu próprio ambiente.

![Relatórios do Power BI no Servidor de Relatórios do Power BI](media/get-started/powerbi-reports.png)

Um relatório do Power BI é uma exibição de um modelo de dados em várias perspectivas, com visualizações que representam diferentes descobertas e insights obtidos por meio desse modelo de dados.  Um relatório pode ter uma única visualização ou páginas repletas de visualizações. Dependendo de sua função, você pode ler e explorar relatórios ou pode criá-los para outras pessoas.

Instale o [Power BI Desktop otimizado para o Servidor de Relatórios do Power BI](quickstart-create-powerbi-report.md).

## <a name="paginated-reports"></a>Relatórios paginados
Relatórios paginados (.RDL) são relatórios com estilo de documento com visualizações, em que tabelas são expandidas horizontal e verticalmente para exibir todos os dados, continuando de página a página conforme necessário. Isso é ótimo para gerar documentos com layout fixo e pixels perfeitos otimizados para impressão, como arquivos PDF e Word.

![Relatórios paginados no Servidor de Relatórios do Power BI](media/get-started/paginated-reports.png)

É possível criar relatórios com aparência moderna usando o [Construtor de Relatórios](https://docs.microsoft.com/sql/reporting-services/report-builder/report-builder-in-sql-server-2016) ou o Report Designer no [SSDT (SQL Server Data Tools)](https://docs.microsoft.com/sql/reporting-services/tools/reporting-services-in-sql-server-data-tools-ssdt).

## <a name="reporting-services-mobile-reports"></a>Relatórios móveis do Reporting Services
Relatórios móveis se conectam a dados locais e têm um layout dinâmico que se adapta a diferentes dispositivos e às diferentes maneiras como você os armazena. Você os cria com o Publicador de Relatórios Móveis do SQL Server.

Mais informações sobre os [Relatórios móveis do Reporting Services](https://docs.microsoft.com/sql/reporting-services/mobile-reports/create-mobile-reports-with-sql-server-mobile-report-publisher). 

## <a name="report-server-programming-features"></a>Recursos de programação do Servidor de Relatório
Aproveite os recursos de programação do Servidor de Relatórios do Power BI para poder estender e personalizar sua funcionalidade de relatórios, com APIs para integrar ou estender dados e processamento de relatórios em aplicativos personalizados.

Mais [documentação do desenvolvedor do Servidor de Relatório](https://docs.microsoft.com/sql/reporting-services/reporting-services-developer-documentation).

## <a name="next-steps"></a>Próximas etapas
[Instalar o Servidor de Relatório do Power BI](install-report-server.md)  
[Instalar o Construtor de Relatórios](https://docs.microsoft.com/sql/reporting-services/install-windows/install-report-builder)  

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)


