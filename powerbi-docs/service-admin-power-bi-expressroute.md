---
title: Power BI e ExpressRoute
description: Power BI e ExpressRoute
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-admin
ms.topic: conceptual
ms.date: 05/02/2018
ms.author: davidi
LocalizationGroup: Administration
ms.openlocfilehash: 3438fcb1fed71345454d1e518a3d87487b884f38
ms.sourcegitcommit: 638de55f996d177063561b36d95c8c71ea7af3ed
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/17/2018
---
# <a name="power-bi-and-expressroute"></a>Power BI e ExpressRoute
Com o **Power BI** e o **ExpressRoute**, é possível criar uma conexão de rede privada de sua organização para o Power BI (ou usando as instalações de colocação de um ISP), ignorando a Internet para proteger melhor seus dados e conexões confidenciais do Power BI.

O **ExpressRoute** é um serviço do Azure que permite criar conexões privadas entre datacenters do Azure (nos quais o Power BI reside) e sua infraestrutura local ou criar conexões privadas entre datacenters do Azure e seu ambiente de colocação.

![](media/service-admin-power-bi-expressroute/pbi_expressroute_1.png)

É possível obter [mais informações sobre a Rota Expressa](https://azure.microsoft.com/services/expressroute/) ou sobre [como se inscrever](https://azure.microsoft.com/pricing/details/expressroute/).

> [!NOTE]
> O Power BI é compatível com o modo de emparelhamento Público, conforme descrito nestas [Perguntas frequentes](https://docs.microsoft.com/azure/expressroute/expressroute-faqs).
> 
> 

## <a name="power-bi-expressroute-exceptions"></a>Exceções da Rota Expressa para o Power BI
O Power BI está em conformidade com o ExpressRoute, exceto nos casos em que o Power BI recebe ou envia dados pela Internet pública. Em geral, essas exceções específicas incluem dados estáticos, como arquivos de configuração do navegador baixados por meio do nó mais próximo da **CDN (Rede de Distribuição de Conteúdo)**. Existem algumas exceções generalizadas que se aplicam ao Power BI, em contraste com outras que são específicas do serviço ou do recurso. Veja cada uma delas nas seções a seguir.

### <a name="overall-exceptions-to-power-bi-and-expressroute"></a>Exceções gerais ao Power BI e ao ExpressRoute
Uma exceção ao **Power BI** e ao **ExpressRoute** significa que os dados transmitidos para ou do Power BI são enviados pela Internet pública, em vez de ser transmitidos pelo link privado do ExpressRoute.

As duas exceções gerais ao Power BI com o uso do ExpressRoute são:

* Arquivos estáticos baixados por meio da **CDN (Rede de Distribuição de Conteúdo)** e de sites
* Dados **telemétricos** enviados pela Internet pública

O Power BI usa várias **CDNs (Redes de Distribuição de Conteúdo)** ou sites para distribuir com eficiência o conteúdo estático necessário e os arquivos aos usuários com base na localidade geográfica pela Internet pública. Esses arquivos estáticos incluem downloads de produtos (como o **Power BI Desktop**, o **gateway de dados local** ou os **Pacotes de Conteúdo do Power BI** de vários provedores de serviço independentes), arquivos de configuração do navegador usados para iniciar e estabelecer quaisquer conexões posteriores com o Power BI, bem como a página inicial de logon seguro do Power BI – as credenciais reais são enviadas somente pelo ExpressRoute.   

Alguns **dados telemétricos** também são enviados pela Internet pública e pelo ExpressRoute. Os dados telemétricos incluem estatísticas de uso e dados semelhantes, que são transmitidos aos serviços usados para monitorar o uso e a atividade.

### <a name="power-bi-saas-application-and-expressroute"></a>Aplicativo SaaS do Power BI e ExpressRoute
Quando um usuário inicia uma conexão com o serviço do Power BI (powerbi.com ou por meio do Cortana), Página de Aterrissagem do Power BI, a página de logon e os arquivos estáticos que preparam o navegador para se conectar e interagir com o Power BI são recuperados de uma CDN ou de sites, que se conectam pela Internet pública.

Assim que o logon é estabelecido, as interações de dados posteriores do Power BI ocorrem no ExpressRoute, com exceção de determinados recursos e serviços que dependem de dados da Internet pública:

* O **mapeamento de visuais** exige a conexão e transmissão de dados para o serviço do Bing Virtual Earth ou o serviço de geocódigo do Bing, cada um deles estabelecido pela Internet pública.
* A integração do Power BI com o **Cortana** exige acesso ao Bing pela Internet pública.
* Quando **links personalizados** são adicionados por um usuário, como um widget de imagem ou vídeo, o Power BI solicita dados com base no link fornecido pelo usuário, cujo uso do ExpressRoute é opcional.
* Os usuários podem enviar **comentários para o Power BI** em texto (e, opcionalmente, imagens) por meio do mecanismo de comentários do User Voice, que usa a Internet pública para transmissão.
* O **provedor de conteúdo do Bing Notícias** baixa o conteúdo do Bing usando a Internet pública.
* Ao se conectar a **aplicativos** (por exemplo, pacotes de conteúdo), geralmente, os usuários devem inserir credenciais e configurações usando as páginas fornecidas pelo provedor de SaaS. O uso do ExpressRoute por essas páginas é opcional.

| Atividade do usuário | Destino |
| --- | --- |
| Página de aterrissagem (antes do logon) |`maxcdn.bootstrapcdn.com ; ajax.aspnetcdn.com ; netdna.bootstrapcdn.com ; cdn.optimizely.com; google-analytics.com ` |
| Logon |`*.mktoresp.com ; *.aadcdn.microsoftonline-p.com ; *.msecnd.com ; *.localytics.com ; ajax.aspnetcdn.com` |
| Dashboard, relatórios, gerenciamento de conjunto de dados (incluindo mapas e geocódigo) |`*.localytics.com ; *.virtualearth.net ; platform.bing.com; powerbi.microsoft.com; c.microsoft.com; app.powerbi.com; *.powerbi.com; dc.services.visualstudio.com ` |
| Suporte |`support.powerbi.com ; powerbi.uservoice.com ; go.microsoft.com ` |

### <a name="power-bi-desktop-and-expressroute"></a>Power BI Desktop e ExpressRoute
O Power BI Desktop também está em conformidade com o ExpressRoute, exceto pelos recursos descritos na seguinte lista:

* As **notificações de atualização**, usadas para detectar se os usuários têm a versão mais recente do Power BI Desktop, são enviadas pela Internet pública.
* Alguns **dados telemétricos** são enviados pela Internet pública.
* O **mapeamento de visuais** exige a conexão e transmissão de dados para o serviço do **Bing Virtual Earth** ou o serviço de **geocódigo do Bing**, cada um deles estabelecido pela Internet pública.
* O recurso **Obter Dados** de várias fontes de dados, como **Web** ou provedores de SaaS de terceiros usa a Internet pública para enviar esses dados.

### <a name="power-bi-paas-and-expressroute"></a>PaaS do Power BI e ExpressRoute
O Power BI oferece APIs e outros recursos baseados em plataforma que permitem aos desenvolvedores criar soluções e aplicativos personalizados do Power BI. Os seguintes serviços, além dos dados telemétricos e da CDN discutidos anteriormente neste tópico, são usados durante a transmissão de dados de PaaS do Power BI pela Internet pública:

| Atividade de PaaS | Destinos adicionais utilizados |
| --- | --- |
| Inserção pública (telemetria) |`c1.microsoft.com` |
| Visuais personalizados (CDN) |`*.azureedge.net` |

Alguns **visuais personalizados** são criados por terceiros, enquanto outros são criados pela Microsoft. O uso do ExpressRoute por eles é opcional.

### <a name="power-bi-mobile-and-expressroute"></a>Power BI Mobile e ExpressRoute
Este documento não aborda o uso de aplicativos móveis do Power BI.  

### <a name="on-premises-data-gateway-and-expressroute"></a>Gateway de dados local e ExpressRoute
Quando um **gateway de dados local** é usado com o Power BI, as transmissões ocorrem em conformidade com o ExpressRoute, com exceção das atividades do usuário documentadas na seção **Aplicativo SaaS do Power BI e ExpressRoute** encontradas neste tópico.  

