---
title: Perguntas frequentes sobre o Power BI Embedded
description: Navegue por uma lista de perguntas frequentes e respostas sobre o Power BI Embedded.
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
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 03/07/2018
ms.author: maghan
ms.openlocfilehash: 52ff1095c063be867354a23e0e8e4908a4b4e1d7
ms.sourcegitcommit: ee5d044db99e253c27816e0ea6bdeb9e39a2cf41
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/08/2018
---
# <a name="frequently-asked-questions-about-power-bi-embedded"></a>Perguntas frequentes sobre o Power BI Embedded

* Se você tiver outras dúvidas, [experimente perguntar à comunidade do Power BI](http://community.powerbi.com/).
* Ainda tem um problema? Visite a [página de suporte do Power BI](https://powerbi.microsoft.com/support/).

## <a name="general"></a>Geral

### <a name="what-is-power-bi-embedded"></a>O que é o Power BI Embedded?

O Microsoft Power BI Embedded permite que os desenvolvedores de aplicativos insiram relatórios, dashboards e blocos incríveis e totalmente interativos em aplicativos, sem o tempo e a despesa da criação de controles e de visualizações de dados desde o início.

### <a name="who-is-the-target-audience-for-power-bi-embedded"></a>Quem é o público-alvo do Power BI Embedded?

Os desenvolvedores e as empresas de software que fazem aplicativos próprios, conhecidas como ISVs (fornecedores independentes de software).

### <a name="how-is-power-bi-embedded-different-from-power-bi-the-service"></a>Qual a diferença entre o Power BI Embedded e o serviço do Power BI?

O Power BI Embedded é destinado aos ISVs ou aos desenvolvedores que criam aplicativos e desejam inserir elementos visuais neles para ajudar seus clientes a tomar decisões sem precisar criar uma solução de análise desde o início. A análise inserida permite que os usuários empresariais acessem os dados corporativos e executem consultas para gerar informações usando esses dados no aplicativo.

O Power BI, por outro lado, é uma solução de análise de software como serviço que fornece às organizações uma exibição única dos dados corporativos mais críticos.

### <a name="what-is-the-difference-between-power-bi-premium-and-power-bi-embedded"></a>Qual é a diferença entre o Power BI Premium e o Power BI Embedded?

A capacidade do Power BI Premium é direcionada a empresas que desejam uma solução de BI completa para fornecer uma exibição única da organização, dos parceiros, dos clientes e dos fornecedores. O Power BI Premium ajuda a organização na tomada de decisões. O Power BI Premium é um produto SaaS que permite aos usuários consumir conteúdo por meio do portal do Power BI, de aplicativos móveis e de aplicativos desenvolvidos internamente.

O Power BI Embedded é destinado aos ISVs ou aos desenvolvedores que criam aplicativos e desejam inserir elementos visuais neles. O Power BI Embedded ajuda os clientes a tomar decisões por ser destinado aos desenvolvedores de aplicativos, de modo que os clientes desses aplicativos, incluindo qualquer pessoa dentro ou fora da organização, podem consumir o conteúdo armazenado na capacidade do Power BI Embedded. O conteúdo da capacidade do Power BI Embedded não pode ser compartilhado por meio de publicação com um clique na Web nem no SharePoint, além de não ser compatível como os relatórios do SSRS.

### <a name="what-is-the-microsoft-recommendation-for-when-a-customer-should-buy-power-bi-premium-vs-power-bi-embedded"></a>Segundo a recomendação da Microsoft, quando os clientes devem comprar o Power BI Premium e quando devem comprar o Power BI Embedded?

A recomendação da Microsoft é que as empresas comprem o Power BI Premium (solução de BI de nuvem de autoatendimento de nível empresarial) e que os ISVs comprem o Power BI Embedded (componentes de análise inseridos habilitados para a nuvem). No entanto, não há restrições em relação a qual produto um cliente pode comprar.

Pode haver alguns casos em que um ISV (normalmente de grande porte) deseja usar uma SKU P para obter os benefícios adicionais do serviço do Power BI predefinido na organização, bem como inseri-los nos aplicativos. E claro, algumas empresas poderão decidir usar SKUs A no Azure se só estiverem interessadas em criar aplicativos de linha de negócios e em inserir análise neles, e não em usar o serviço do Power BI predefinido.

### <a name="how-many-embed-tokens-can-i-create"></a>Quantos tokens inseridos posso criar?

Tokens inseridos com licença PRO destinam-se para desenvolvimento e teste de desenvolvimento, portanto, o número de tokens inseridos que uma conta mestre do Power BI pode gerar é limitado. Você deve [adquirir uma capacidade](https://docs.microsoft.com/power-bi/developer/embedded-faq#technical) para incorporar em um ambiente de produção. Não há nenhum limite para a quantidade de tokens inseridos que você pode gerar quando uma capacidade é adquirida.

### <a name="when-will-power-bi-embedded-be-available-in-azure"></a>Quando o Power BI Embedded estará disponível no Azure?

O Power BI Embedded já está disponível.

## <a name="technical"></a>Técnico

### <a name="what-is-the-difference-between-the-a-skus-in-azure-and-the-em-skus-in-office-365"></a>Qual é a diferença entre os SKUs A no Azure e os SKUs EM no Office 365?

O PowerBI.com é uma solução empresarial que inclui muitas funcionalidades, como colaboração social, assinatura de email, etc., em uma oferta de software como serviço

O Power BI Embedded é um conjunto de APIs disponíveis para os desenvolvedores criarem uma solução de análise inserida em uma oferta de plataforma como serviço. Para o cenário de análise inserida, o PowerBI.com deve ser usado para ajudar ISVs e desenvolvedores a gerenciar o conteúdo da solução de análise inserida deles e as configurações de nível de locatário.

Veja aqui uma lista parcial das diferenças que você pode usar com cada um deles.

|Recurso  |Power BI Embedded<br>(SKUs A) |Capacidade do Power BI Premium<br>(SKUs EM)  |
|---------|---------|---------|
|Inserir artefatos de espaços de trabalho do aplicativo Power BI     |Capacidade do Azure |Capacidade do Office 365 |
|Licença do Power BI necessária para consumir relatórios |Não  |Sim |
|Consumir relatórios do Power BI em um aplicativo inserido |Sim  |Sim |
|Consumir relatórios do Power BI no SharePoint |Não |Sim |
|Consumir relatórios do Power BI no Teams |Não |Sim |

### <a name="power-bi-now-offers-three-skus-for-embedding-a-skus-em-skus-and-p-skus-which-one-should-i-purchase-for-my-scenario"></a>O Power BI agora oferece três SKUs para inserção: SKUs A, SKUs EM e SKUs P. Qual devo comprar para meu cenário?

|  |SKU A (Power BI Embedded)  |SKU EM (Power BI Premium)  |SKU P (Power BI Premium)  |
|---------|---------|---------|---------|
|Comprar     |Portal do Azure |Office |Office |
|Casos de uso |* Inserir conteúdo em aplicativo próprio |* Inserir conteúdo em aplicativo próprio<br>* Compartilhar conteúdo com usuários do Power BI Gratuito fora do PowerBI.com e inserir em outros aplicativos SaaS (SharePoint, Teams) |* Inserir conteúdo em aplicativo próprio<br>* Compartilhar conteúdo com usuários do Power BI Gratuito fora do PowerBI.com e inserir em outros aplicativos SaaS (SharePoint, Teams)<br>* Compartilhar conteúdo com usuários do Power BI Gratuito por meio do PowerBI.com  |
|Cobrança |A cada hora |Mensal |Mensal |
|Compromisso  |Sem compromisso |Anual  |Mensal/anual |
|Diferença |Elasticidade completa: pode aumentar/reduzir, pausar/retomar recursos no Portal do Azure ou por meio da API  |Pode ser usado para inserir conteúdo no SharePoint Online e no Microsoft Teams |Combine inserção em aplicativos e use a mesma capacidade do serviço do Power BI |

### <a name="what-are-the-prerequisites-to-create-a-pbie-capacity-in-azure"></a>Quais são os pré-requisitos para criar uma capacidade de PBIE no Azure?

- Você precisa entrar no seu diretório organizacional (não há suporte para contas MSA).
- Você precisa ter um locatário do Power BI, ou seja, pelo menos um usuário em seu diretório deve estar inscrito no Power BI. 
- Você precisa ter uma assinatura do Azure em seu diretório organizacional.

### <a name="how-can-i-monitor-capacity-consumption"></a>Como posso monitorar o consumo da capacidade?

O monitoramento pelo Azure é um roteiro de curto prazo. O recurso do Azure, o Power BI Embedded, incluirá o monitoramento de KPIs que mostrarão o uso e a integridade.

### <a name="will-my-capacity-scale-automatically-to-adjust-to-the-consumption-of-my-app"></a>Minha capacidade será dimensionada automaticamente para ajustar-se ao consumo de meu aplicativo?

Embora não haja dimensionamento automatizado no momento, todas as APIs podem ser dimensionadas a qualquer momento.

### <a name="what-is-the-authentication-model-for-power-bi-embedded"></a>Qual é o modelo de autenticação do Power BI Embedded?

O Power BI Embedded continuará a usar o Azure AD para autenticação do usuário mestre (um usuário licenciado designado do Power BI Pro), que autenticará o aplicativo no Power BI.

A autenticação e a autorização dos usuários do aplicativo serão implementadas pelo ISV, que poderá implementar uma autenticação própria para seus aplicativos.

Se você já tiver um locatário do Azure AD, será possível usar o diretório existente ou criar um novo locatário do Azure AD para a segurança do conteúdo do aplicativo inserido.

### <a name="how-is-power-bi-embedded-different-from-other-azure-services"></a>Qual a diferença entre o Power BI Embedded e os serviços do Azure?

O ISV/desenvolvedor deve ter uma conta do Power BI antes de comprar o Power BI Embedded no Azure. A região da implantação do Power BI Embedded é determinada pela conta do Power BI. Gerencie o recurso do Power BI Embedded no Azure para:

* Aumentar/reduzir
* Adicionar administradores de capacidade
* Pausar/retomar o serviço

Use o PowerBI.com para atribuir/cancelar a atribuição de espaços de trabalho à capacidade do Power BI Embedded.

### <a name="what-deploy-regions-are-supported"></a>Quais regiões de implantação são compatíveis?

Sudeste da Austrália, Sul do Brasil, Central do Canadá Central, Leste dos EUA 2, Índia Ocidental, Leste do Japão, Centro-Norte dos EUA, Europa Setentrional, Centro-Sul dos EUA, Sudeste Asiático, Sul do Reino Unido, Europa Ocidental, Oeste dos EUA e Oeste dos EUA 2.

### <a name="what-type-of-content-pack-data-can-be-embedded"></a>Que tipo de dados de pacote de conteúdo pode ser inserido?

**Dashboards** e **blocos** que são criados com base em conjuntos de dados de pacote de conteúdo *não podem* ser inseridos, porém **relatórios** criados com base em um conjunto de dados de pacote de conteúdo *podem* ser inseridos.

## <a name="licensing"></a>Licenças

### <a name="how-do-i-purchase-power-bi-embedded"></a>Como fazer para comprar o Power BI Embedded?

O Power BI Embedded está disponível por meio do Azure.

### <a name="how-power-bi-embedded-be-metered"></a>Como é feita a medição do Power BI Embedded?

O Power BI Embedded terá um medidor por hora.

### <a name="how-does-the-usage-of-power-bi-embedded-show-up-on-my-bill"></a>Como o uso do Power BI Embedded aparece na minha fatura?

O Power BI Embedded é cobrado em uma taxa por hora previsível com base nos tipos de nós implantados. Observe que enquanto o recurso estiver ativo, você será cobrado mesmo se não houver nenhum uso. Para interromper a cobrança, é necessário pausar ativamente o recurso. Pausar pode ser feito por meio do Azure ou por meio de APIs de ARM.

### <a name="what-happens-if-i-already-purchased-power-bi-premium-and-now-i-want-some-of-the-benefits-of-power-bi-embedded-in-azure"></a>O que acontece se já comprei o Power BI Premium e agora quero alguns dos benefícios do Power BI Embedded no Azure?

Os clientes continuarão a pagar pelas compras existentes do Power BI Premium até o término do prazo do contrato atual e, em seguida, poderão mudar as compras do Power BI Premium conforme necessário em tal momento.

### <a name="do-i-still-have-to-buy-power-bi-premium-to-get-access-to-power-bi-embedded"></a>Ainda preciso comprar o Power BI Premium para obter acesso ao Power BI Embedded?

Não, o Power BI Embedded inclui a capacidade baseada no Azure que você precisa para implantar e distribuir sua solução aos clientes.

### <a name="who-needs-a-power-bi-pro-license-for-power-bi-embedded-and-why"></a>Quem precisa de uma licença do Power BI Pro para o Power BI Embedded e por quê?

A licença do Power BI Pro é necessária para analistas que precisam adicionar relatórios a um Espaço de Trabalho do Power BI, para desenvolvedores que precisam usar as APIs REST e para administradores de locatários que precisam gerenciar o locatário e a capacidade do Power BI.

Uma vez que o Power BI Embedded permite o uso do portal do Power BI para gerenciar e validar o conteúdo inserido, a licença do Power BI Pro é necessária para autenticar o aplicativo no PowerBI.com para a obtenção do acesso aos relatórios nos repositórios corretos.

### <a name="can-i-get-started-for-free"></a>Posso começar gratuitamente?

Sim. Você pode usar os [créditos Azure](https://azure.microsoft.com/free/) para o Power BI Embedded.

### <a name="can-i-get-a-trial-experience-for-power-bi-embedded-in-azure"></a>Posso experimentar uma avaliação do Power BI Embedded no Azure?

Como o Power BI Embedded é parte do Azure, é possível usar o serviço com o [crédito de US$ 200 recebido durante a inscrição no Azure](https://azure.microsoft.com/free/).

### <a name="whats-the-purchase-commitment-for-power-bi-embedded"></a>O que é a confirmação de compra para o Power BI Embedded? 

Os clientes podem alterar o uso a cada hora. Não há nenhum compromisso mensal nem anual pelo serviço do Power BI Embedded.

### <a name="where-is-power-bi-embedded-available-us-government-germany-china-what-is-the-timing"></a>Onde o Power BI Embedded está disponível? No Governo dos EUA? Na Alemanha? Na China? Qual é a previsão?

O Power BI Embedded está disponível nas nuvens comerciais do Azure e na nuvem do governo dos EUA.  A disponibilidade de nuvem soberana para Alemanha e China será adicionada no futuro.

### <a name="is-power-bi-embedded-available-for-non-profits-and-educational"></a>O Power BI Embedded está disponível para entidades sem fins lucrativos e educacionais?

As entidades sem fins lucrativos e educacionais podem comprar o Azure. Não há nenhum preço especial para esses tipos de clientes no Azure.

Mais perguntas? [Experimente a Comunidade do Power BI](http://community.powerbi.com/)
