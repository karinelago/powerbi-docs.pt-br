---
title: "Power BI Premium – o que é?"
description: "O Power BI Premium é a capacidade dedicada para a sua organização ou equipe, oferecendo desempenho mais confiável e maiores volumes de dados sem exigir a compra de licenças por usuário."
services: powerbi
documentationcenter: 
author: markingmyname
manager: kfile
backup: 
editor: 
tags: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: get-started-article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 12/05/2017
ms.author: maghan
ms.openlocfilehash: eb2072b0beadf3f6f2cf702f35f56441bc38c7ff
ms.sourcegitcommit: 6e693f9caf98385a2c45890cd0fbf2403f0dbb8a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2018
---
# <a name="power-bi-premium---what-is-it"></a>Power BI Premium – o que é?
O Power BI Premium fornece recursos dedicados à execução de serviço do Power BI para sua organização ou equipe, oferecendo desempenho mais confiável e volumes de dados maiores. O Premium também permite a ampla distribuição de conteúdo sem a necessidade de adquirir licenças de usuário para visualizadores.

É possível usar o Power BI Premium atribuindo espaços de trabalho a uma capacidade Premium. *Capacidade de Premium* é um recurso dedicado para sua organização. Os espaços de trabalho que não foram atribuídos a uma capacidade Premium estarão em uma capacidade compartilhada.

*Capacidade compartilhada* é a experiência à qual você está acostumado com o Power BI, na qual as cargas de trabalho são executadas em recursos computacionais compartilhados por outros clientes. Na capacidade compartilhada, mais limites são colocados em usuários individuais para garantir a qualidade da experiência para todos os usuários.

[!INCLUDE [powerbi-premium-illustration](./includes/powerbi-premium-illustration.md)]

<iframe width="560" height="315" src="https://www.youtube.com/embed/lNQDkN0GXzU?rel=0&amp;showinfo=0" frameborder="0" allowfullscreen></iframe>

## <a name="capacity-tiers"></a>Níveis de capacidade
Há dois tipos de capacidade dentro do Power BI. Capacidade compartilhada e a capacidade do Power BI Premium. Veja quais são as diferenças entre eles.

|  | Capacidade compartilhada | Capacidade do Power BI Premium |
| --- | --- | --- |
| **Taxa de atualização** |8/dia |Não restrito |
| **Isolamento com hardware dedicado** |![](media/service-premium/not-available.png "Não disponível") |![](media/service-premium/available.png "Disponível") |
| **Distribuição do Enterprise para** ***todos os usuários*** | | |
| Aplicativos |![](media/service-premium/not-available.png "Não disponível") |![](media/service-premium/available.png "Disponível")<sup>1</sup> |
| API e controles inseridos |![](media/service-premium/not-available.png "Não disponível") |![](media/service-premium/available.png "Disponível")<sup>2</sup> |
| **Publicar relatórios locais do Power BI** |![](media/service-premium/not-available.png "Não disponível") |![](media/service-premium/available.png "Disponível") |

*<sup>1</sup> O consumo do usuário gratuito em aplicativos inclui exibir o conteúdo na web e em dispositivos móveis, usar P e R, Quick Insights, Cortana, exportar para CSV, Excel e PowerPoint.*  
*<sup>2</sup> Publicação Melhorias futuras chegando no Power BI Premium GA.*

### <a name="premium-capacity"></a>Capacidade Premium
Para começar a usar a capacidade do Power BI Premium, é necessário atribuir um espaço de trabalho a uma capacidade. Para obter mais informações sobre como atribuir um espaço de trabalho a uma capacidade Premium, consulte [Manage Power BI Premium (Gerenciar o Power BI Premium)](service-admin-premium-manage.md).

Quando o um espaço de trabalho apoiado com a capacidade Premium, é possível usufruir dos benefícios do Power BI Premium.

* Atualizações agendadas: anteriormente, os usuários tinham um limite de 8x atualizações agendadas com modelos importados. Essa limitação foi eliminada para conjuntos de dados nos espaços de trabalho Premium. Isso não se aplica às configurações de atualização de cache agendada para o DirectQuery. Elas continuam as mesmas entre as capacidades Premium e Compartilhada.
* Isolamento com hardware dedicado – em função da natureza da capacidade compartilhada, o desempenho dos seus relatórios e dashboards pode ser afetado pelas demandas de recursos de outras cargas de trabalho na capacidade, apesar de nossas garantias em relação a ele. Por outro lado, a Premium oferece desempenho mais consistente e confiável para suas cargas de trabalho ao isolá-las de cargas de trabalho não relacionadas.

Se um aplicativo for apoiado com a capacidade Premium (ou seja, ele foi publicado com base em um espaço de trabalho do aplicativo atribuído no momento à Premium), então o aplicativo publicado poderá ser usado por qualquer usuário da sua organização, independentemente da licença que eles tiverem. Isso significa que até mesmo usuários gratuitos do Power BI poderão usar esses aplicativos publicados.

### <a name="shared-capacity"></a>Capacidade compartilhada
Por padrão, o espaço de trabalho estará na capacidade compartilhada. Isso inclui o *Meu espaço de trabalho* pessoal juntamente com espaços de trabalho do aplicativo. Uma capacidade compartilhada é a experiência à qual você está acostumado com o Power BI, na qual as cargas de trabalho são executadas em recursos computacionais compartilhados por outros clientes.

<a name="premiumskus"/>

### <a name="premium-capacity-nodes"></a>Nós de capacidade Premium
O Power BI Premium está disponível em configurações de nó com diferentes capacidades de v-core. Para obter mais informações sobre custo e ofertas específicas de SKU, consulte [Power BI pricing (Preços do Power BI)](https://powerbi.microsoft.com/pricing/). Também está disponível uma [calculadora de custos](https://powerbi.microsoft.com/calculator/). Para obter informações sobre planejamento de capacidade de análise inserida, consulte [Planning a Power BI Enterprise Deployment whitepaper (Planejando um white paper de implantação do Power BI Enterprise)](https://aka.ms/pbienterprisedeploy).

* Os nós P podem ser usados para implantações inseridas ou de serviço
* Os nós EM podem ser usados apenas para implantações inseridas
* EM1 e EM2 
* Os links nesta tabela só funcionam corretamente para os usuários que são administradores globais do Office 365 - os outros usuários recebem um erro 404. 

| Nó de capacidade | Total de núcleos<br/>*(Back-end + front-end)* | Núcleos de back-end | Núcleos de front-end | Limites de conexão dinâmica/DirectQuery | Máx. de renderizações de página no horário de pico | Disponibilidade |
| --- | --- | --- | --- | --- | --- | --- |
| [EM1 (mês a mês)](https://portal.office.com/SubscriptionDetails?OfferId=4004702D-749C-4F74-BF47-3048F1833780&adminportal=1) |1 núcleo virtual |0,5 núcleo, 2,5 GB de RAM |0,5 núcleo |3,75 por segundo |150-300 |Disponível |
| [EM2 (mês a mês)](https://portal.office.com/SubscriptionDetails?OfferId=4004702D-749C-4F74-BF47-3048F1833780&adminportal=1) |2 núcleos virtuais |1 núcleo, 5 GB de RAM |1 núcleo |7,5 por segundo |301-600 |Disponível |
| [EM3 (mês a mês)](https://portal.office.com/SubscriptionDetails?OfferId=4004702D-749C-4F74-BF47-3048F1833780&adminportal=1) |4 núcleos virtuais |2 núcleos, 10 GB de RAM |2 núcleos | |601-1.200 |Disponível |
| [P1](https://portal.office.com/SubscriptionDetails?OfferId=b3ec5615-cc11-48de-967d-8d79f7cb0af1&adminportal=1) |8 v-cores |4 núcleos, 25 GB de RAM |4 núcleos |30 por segundo |1.201-2.400 |Disponível ([mês a mês](https://portal.office.com/SubscriptionDetails?OfferId=E4C8EDD3-74A1-4D42-A738-C647972FBE81&adminportal=1) também está disponível) |
| [P2](https://portal.office.com/SubscriptionDetails?OfferId=062F2AA7-B4BC-4B0E-980F-2072102D8605&adminportal=1) |16 v-cores |8 núcleos, 50 GB de RAM |8 núcleos |60 por segundo |2.401-4.800 |Disponível |
| [P3](https://portal.office.com/SubscriptionDetails?OfferId=40c7d673-375c-42a1-84ca-f993a524fed0&adminportal=1) |32 v-cores |16 núcleos, 100 GB de RAM |16 núcleos |120 por segundo |4.801-9.600 |Disponível |

* Os núcleos de front-end são responsáveis pelo gerenciamento de documentos de relatório, dashboard e serviço Web, gerenciamento de direitos de acesso, agendamento, APIs, carregamentos e downloads, e geralmente por tudo o que está relacionado à experiência do usuário.
* Os núcleos de back-end são responsáveis pelo trabalho pesado: processamento de consultas, gerenciamento de cache, execução de servidores R, atualização de dados, processamento de linguagem natural, alimentações em tempo real, renderizações de relatórios e imagens do servidor. Com os núcleos de back-end, também é reservada uma determinada quantidade de memória. Ter memória suficiente se tornar especialmente importante ao lidar com grandes modelos de dados ou com um grande número de conjuntos de dados ativos.

## <a name="power-bi-report-server"></a>Servidor de Relatório do Power BI
O Power BI Premium inclui o direito de executar Servidor de Relatório do Power BI local. Para obter mais informações, consulte [Introdução ao Servidor de Relatório do Power BI](report-server/get-started.md).

## <a name="next-steps"></a>Próximas etapas
[Perguntas Frequentes do Power BI Premium](service-premium-faq.md)  
[Notas de versão do Power BI Premium](service-premium-release-notes.md)  
[Como comprar o Power BI Premium](service-admin-premium-purchase.md)  
[Gerenciando o Power BI Premium](service-admin-premium-manage.md)  
[White paper do Microsoft Power BI Premium](https://aka.ms/pbipremiumwhitepaper)  
[Planejando um white paper de implantação do Power BI Enterprise](https://aka.ms/pbienterprisedeploy)  
[Administração do Power BI em sua organização](service-admin-administering-power-bi-in-your-organization.md)  

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)

