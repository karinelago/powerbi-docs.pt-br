---
title: Visão geral do programa de pacote de conteúdo do serviço do Power BI
description: Programa de certificação do pacote de conteúdo
author: markingmyname
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-developer
ms.topic: conceptual
ms.date: 02/20/2018
ms.author: maghan
ms.openlocfilehash: cfb9727a41d602ce14bfd2a403a87e82d2f0e94d
ms.sourcegitcommit: 80d6b45eb84243e801b60b9038b9bff77c30d5c8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34290627"
---
# <a name="overview-of-the-power-bi-service-content-pack-program"></a>Visão geral do programa de pacote de conteúdo do serviço do Power BI
Um pacote de conteúdo é um conjunto de conteúdos prontos que permite que os usuários obtenham informações sobre uma fonte imediatamente. Um pacote de conteúdo normalmente se concentra em um cenário de negócios específico, fornecendo informações sobre uma função, domínio ou fluxo de trabalho.

Os ISVs podem criar pacotes de conteúdo de modelo que permitem que os clientes se conectem e instanciem com suas próprias contas. Como especialistas de domínio, eles podem desbloquear os dados de forma que eles sejam facilmente consumíveis por usuários empresariais. Os pacotes de conteúdo oferecem monitoramento e análise ad hoc para seus clientes sem investir pesadamente em uma infraestrutura de relatório. 

Esses pacotes de conteúdo de modelo criados pelo ISV podem ser enviados para a equipe do Power BI para ficarem publicamente disponíveis na galeria de pacotes de conteúdo do Power BI (app.powerbi.com/getdata/services) e no Microsoft AppSource (appsource.microsoft.com). Um exemplo da experiência de pacote de conteúdo público pode ser encontrada [aqui](template-content-pack-experience.md).

## <a name="overview"></a>Visão Geral
O processo geral para desenvolver e enviar um pacote de conteúdo de modelo envolve várias etapas.

 ![Processo](media/service-content-pack-overview/developer-content-pack-overview.png)

1. [Examine os requisitos](#requirements) e verifique se você os atendeu
2. [Criar conteúdo](template-content-pack-authoring.md#queries) no Power BI Desktop
3. [Criar um painel](template-content-pack-authoring.md#dashboard) no PowerBI.com
4. [Testar o pacote de conteúdo](template-content-pack-testing.md) em sua organização
5. [Enviar](template-content-pack-testing.md#submission) o conteúdo ao Power BI para publicação

<a name="requirements"></a>

## <a name="requirements"></a>Requisitos
Para criar e enviar um pacote de conteúdo a ser publicado no serviço do PowerBI e do AppSource, você deve atender aos seguintes requisitos:

* Você tem um aplicativo de SaaS usado por usuários de negócios.
* Seu aplicativo de SaaS tem dados de usuário que podem ser visualizados no Power BI.
* Seu aplicativo de SaaS tem uma API que é acessível pela Internet pública. O ideal é que a API seja baseada em uma API baseada em REST ou em um feed OData. Os pacotes de conteúdo do Power BI dão suporte a vários tipos de autenticação, como autenticação básica, OAuth 2.0 e chave de API. 
* Seu aplicativo SaaS é aprovado para publicação de um pacote de conteúdo. Envie sua solicitação para pbiservicesapps@microsoft.com. Examinaremos cada envio de acordo com a relevância e o uso esperado. 
* Contrato de parceiro assinado. Você fará isso na [etapa de envio](template-content-pack-testing.md#submission).

Examine a seção sobre [criação](template-content-pack-authoring.md) para obter mais detalhes sobre os requisitos técnicos.

## <a name="business-scenario"></a>Cenário de negócios
Os pacotes de conteúdo fornecem informações e métricas voltadas para um cenário comercial específico. Compreender seu público-alvo e os benefícios que ele receberá com o pacote de conteúdo ajudará a garantir que seus usuários tenham êxito com o conteúdo que você fornece.

### <a name="tips"></a>Dicas
* Identifique seu público-alvo e a tarefa que ele está tentando realizar  
* Concentre-se em um determinado período (últimos 90 dias) ou últimos N resultados  
* Importe somente as tabelas/colunas relacionadas ao seu cenário  
* Considere a possibilidade de oferecer mais de um pacote de conteúdo para cenários separados e diferentes  

## <a name="frequently-asked-questions"></a>Perguntas frequentes
**Como terceiro, posso criar um pacote de conteúdo do serviço do Power BI para um aplicativo de SaaS que não possuo?**

É necessário assinar um contrato de parceiro com o proprietário do aplicativo de SaaS antes de publicar um pacote de conteúdo no serviço. Como terceiro, será necessário facilitar a assinatura de um contrato de parceiro com o proprietário do aplicativo SaaS.

**Não tenho uma API de desenvolvedor pública para meu serviço. Mesmo assim, posso criar um pacote de conteúdo do serviço do Power BI que receba os dados diretamente do armazenamento de dados?**

Não, os pacotes de conteúdo de serviço do Power BI exigem uma API de desenvolvedor que esteja acessível pela Internet pública.

**Que tipo de APIs têm suporte nos pacotes de conteúdo do serviço e com quais tipos de autenticação elas funcionam?**

Os pacotes de conteúdo do serviço do Power BI dão suporte a API REST ou feed OData. O Power BI pode trabalhar com vários tipos de autenticação, incluindo autenticação básica, OAuth2.0 e chave de API da Web. Mais detalhes sobre os requisitos técnicos no artigo [Criando](template-content-pack-authoring.md#dashboard).

**Tenho um pacote de conteúdo publicado no Power BI. Como atualizá-lo?**

Os pacotes de conteúdo publicados podem ser atualizados uma vez por mês. Solicitações de atualização enviadas para o [pbiservicesapps@microsoft.com](mailto:pbiservicesapps@microsoft.com) antes do último dia do mês atual serão publicadas na primeira semana do mês seguinte.

**Tenho mais dúvidas sobre os pacotes de conteúdo do serviço. Como contatar vocês?**

Fique à vontade para enviar suas perguntas por email para [pbiservicesapps@microsoft.com](mailto:pbiservicesapps@microsoft.com)

## <a name="support"></a>Suporte
Para obter suporte durante o desenvolvimento, use [https://powerbi.microsoft.com/support](https://powerbi.microsoft.com/support). Ele é monitorado e gerenciado ativamente. Os incidentes com clientes chegam rapidamente à equipe apropriada.

## <a name="next-step"></a>Próxima etapa
[Criação](template-content-pack-authoring.md)

