---
title: Exibir KPIs e relatórios móveis do SSRS no aplicativo móvel do Windows 10 – Power BI
description: O aplicativo móvel Power BI para Windows 10 oferece acesso móvel dinâmico e habilitado para toque às suas informações corporativas locais importantes.
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-mobile
ms.topic: conceptual
ms.date: 10/13/2017
ms.author: maggies
ms.openlocfilehash: 7bbf03c35284924c415a9ae1348528ed80c3f2fe
ms.sourcegitcommit: 80d6b45eb84243e801b60b9038b9bff77c30d5c8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34295608"
---
# <a name="view-reporting-services-ssrs-mobile-reports-and-kpis-in-the-windows-10-power-bi-mobile-app"></a>Exibir KPIs e relatórios móveis do SSRS (Reporting Services) no aplicativo móvel do Power BI do Windows 10
O aplicativo móvel do Power BI para Windows 10 oferece acesso móvel dinâmico e habilitado para toque às suas informações corporativas locais importantes no SQL Server 2016 Reporting Services. 

![Relatórios móveis do Reporting Services](media/mobile-app-windows-10-ssrs-kpis-mobile-reports/power-bi-ssrs-mobile-report.png)

## <a name="first-things-first"></a>As coisas mais importantes primeiro
[Crie relatórios móveis do Reporting Services](https://msdn.microsoft.com/library/mt652547.aspx) com o Publicador de Relatórios Móveis do Microsoft SQL Server 2016 Enterprise Edition e publique-os no [portal da Web do Reporting Services](https://msdn.microsoft.com/library/mt637133.aspx). Crie KPIs diretamente no portal da Web. Organize-os em pastas e marque seus favoritos para que você possa encontrá-los com facilidade. 

Em seguida, no aplicativo móvel Power BI para Windows 10, exiba os KPIs e relatórios móveis, organizados em pastas ou coletados como favoritos. 

> [!NOTE]
> Seu dispositivo precisa estar executando o Windows 10. O aplicativo funciona melhor em dispositivos com pelo menos 1 GB de RAM e 8 GB de armazenamento interno.
> 
> 

## <a name="explore-samples-without-a-sql-server-2016-reporting-services-server"></a>Explorar amostras sem um servidor do SQL Server 2016 Reporting Services
Mesmo que você não tenha acesso a um portal da Web do Reporting Services, ainda é possível explorar os recursos de relatórios móveis do Reporting Services.

1. No dispositivo Windows 10, abra o aplicativo Power BI.
2. Toque no botão de navegação global ![Botão de navegação global](media/mobile-app-windows-10-ssrs-kpis-mobile-reports/powerbi_windows10_options_icon.png) no canto superior esquerdo.
3. Toque no ícone **Configurações** ![ícone Configurações](media/mobile-app-windows-10-ssrs-kpis-mobile-reports/power-bi-settings-icon.png), clique com o botão direito do mouse ou toque e segure em **Conectar-se ao servidor** e, depois, toque em **Exibir amostras**.
   
   ![Exibir exemplos de SSRS](media/mobile-app-windows-10-ssrs-kpis-mobile-reports/power-bi-win10-connect-ssrs-samples.png)
4. Abra a pasta Relatórios de Varejo ou Relatórios de Vendas para explorar seus KPIs e relatórios móveis.
   
   ![KPIs e relatórios móveis de exemplo](media/mobile-app-windows-10-ssrs-kpis-mobile-reports/power-bi-win10-ssrs-sample-kpis.png)

Navegue pelas amostras para interagir com KPIs e relatórios móveis.

## <a name="connect-to-a-reporting-services-report-server"></a>Conectar-se a um servidor de relatório do Reporting Services
1. Na parte inferior da barra de navegação esquerda, toque em **Configurações** ![ícone Configurações](media/mobile-app-windows-10-ssrs-kpis-mobile-reports/power-bi-settings-icon.png)
2. Toque em **Conectar ao servidor**.
3. Preencha o endereço do servidor e seu nome de usuário e senha. Use este formato para o endereço do servidor:
   
     `http://<servername>/reports` OU `https://<servername>/reports`
   
   > [!NOTE]
   > Inclua **http** ou **https** no início da cadeia de conexão.
   > 
   > 
   
    Toque em **Opção avançada** para dar um nome ao servidor, se desejar.
4. Toque na marca de seleção para se conectar. 
   
   Agora você pode ver o servidor na barra de navegação à esquerda.
   
   ![Servidor na barra de navegação esquerda](media/mobile-app-windows-10-ssrs-kpis-mobile-reports/power-bi-ssrs-mobile-report-server.png)
   
   >[!TIP]
   >Toque no ![botão Navegação global](media/mobile-app-windows-10-ssrs-kpis-mobile-reports/powerbi_windows10_options_icon.png) a qualquer momento para mudar entre seus relatórios móveis e dashboards do Reporting Services no serviço do Power BI. 
   > 

## <a name="view-reporting-services-kpis-and-mobile-reports-in-the-power-bi-app"></a>Exibir KPIs e relatórios móveis do Reporting Services no aplicativo Power BI
Os KPIs e relatórios móveis do Reporting Services são exibidos nas mesmas pastas em que estão contidos no portal da Web do Reporting Services.

![Pastas de relatórios](media/mobile-app-windows-10-ssrs-kpis-mobile-reports/power-bi-ssrs-mobile-report-folders.png)

* Toque em um KPI para vê-lo no modo de foco.
  
    ![KPI no modo de foco](media/mobile-app-windows-10-ssrs-kpis-mobile-reports/power-bi-ssrs-mobile-report-kpis.png)
* Toque em um relatório móvel para abri-lo e interagir com ele no aplicativo Power BI.
  
    ![Relatório móvel do Reporting Services](media/mobile-app-windows-10-ssrs-kpis-mobile-reports/power-bi-ssrs-mobile-report.png)

## <a name="view-your-favorite-kpis-and-reports"></a>Exibir seus KPIs e relatórios favoritos
Você pode marcar KPIs e relatórios móveis como favoritos no portal da Web do Reporting Services e exibi-los em uma pasta fácil em seu dispositivo Windows 10, juntamente com seus relatórios e dashboards favoritos do Power BI.

* Toque em **Favoritos**.
  
   ![Ícone Favoritos](media/mobile-app-windows-10-ssrs-kpis-mobile-reports/power-bi-ssrs-mobile-report-favorite-menu.png)
  
   Todos os seus favoritos do portal da Web são mostrados nesta página.
  
   ![Página Favoritos](media/mobile-app-windows-10-ssrs-kpis-mobile-reports/power-bi-windows-10-ssrs-favorites.png)

Leia mais sobre [favoritos nos aplicativos móveis do Power BI](mobile-apps-favorites.md).

## <a name="remove-a-connection-to-a-report-server"></a>Remover uma conexão a um servidor de relatório
Você pode estar conectado apenas a um servidor de relatório por vez no aplicativo móvel Power BI. Se você quiser se conectar a um servidor diferente, precisará desconectar-se do atual.

1. Na parte inferior da barra de navegação esquerda, toque em **Configurações** ![ícone Configurações](media/mobile-app-windows-10-ssrs-kpis-mobile-reports/power-bi-settings-icon.png).
2. Toque e segure o nome do servidor ao qual você não deseja se conectar.
3. Toque **Remover servidor**.
   
    ![Remover servidor](media/mobile-app-windows-10-ssrs-kpis-mobile-reports/power-bi-windows-10-ssrs-remove-server-menu.png)

## <a name="create-reporting-services-mobile-reports-and-kpis"></a>Criar KPIs e relatórios móveis do Reporting Services
Você não cria KPIs nem relatórios móveis do Reporting Services no aplicativo móvel do Power BI. Crie-os no Publicador de Relatórios Móveis do SQL Server e em um portal da Web do SQL Server 2016 Reporting Services.

* [Crie seus próprios relatórios móveis do Reporting Services](https://msdn.microsoft.com/library/mt652547.aspx) e publique-os em um portal da Web do Reporting Services.
* Criar [KPIs em um portal da Web do Reporting Services](https://msdn.microsoft.com/library/mt683632.aspx)

## <a name="next-steps"></a>Próximas etapas
* [Introdução ao aplicativo móvel do Power BI para Windows 10](mobile-windows-10-phone-app-get-started.md)  
* [Introdução ao Power BI](service-get-started.md)  
* Dúvidas? [Experimente perguntar à Comunidade do Power BI](http://community.powerbi.com/)

