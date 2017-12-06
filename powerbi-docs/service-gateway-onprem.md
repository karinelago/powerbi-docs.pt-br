---
title: Gateway de dados local
description: "Esta é uma visão geral do gateway de dados local para o Power BI. É possível usar este gateway para trabalhar com fontes de dados do DirectQuery. Você também pode usar este gateway para atualizar conjuntos de dados de nuvem com dados locais."
services: powerbi
documentationcenter: 
author: davidiseminger
manager: kfile
backup: 
editor: 
tags: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: powerbi
ms.date: 11/27/2017
ms.author: davidi
ms.openlocfilehash: 4693349715e7a38ae936318e9a8750e0b2f3fab0
ms.sourcegitcommit: 7742f952c20695dfb475f74965c0065b02c01521
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/29/2017
---
# <a name="on-premises-data-gateway"></a>Gateway de dados local
O gateway de dados local atua como uma ponte, fornecendo uma transferência de dados rápida e segura entre os dados locais (dados que não estão na nuvem) e os serviços do Power BI, Microsoft Flow, Aplicativos Lógicos e PowerApps.

Você pode usar um único gateway com diferentes serviços ao mesmo tempo. Se você estiver usando o Power BI, bem como o PowerApps, um único gateway poderá ser usado para ambos. Ele depende da conta que você usa para entrar.

> [!NOTE]
> O gateway de dados local implementa a compactação de dados e a criptografia de transporte em todos os modos.
> 
> 

<!-- Shared Requirements Include -->
[!INCLUDE [gateway-onprem-requirements-include](./includes/gateway-onprem-requirements-include.md)]

### <a name="limitations-of-analysis-services-live-connections"></a>Limitações das conexões dinâmicas do Analysis Services
Você pode usar uma conexão dinâmica em instâncias de tabela ou multidimensionais.

| **Versão do servidor** | **SKU necessário** |
| --- | --- |
| 2012 SP1 CU4 ou posterior |Business Intelligence e SKU Enterprise |
| 2014 |Business Intelligence e SKU Enterprise |
| 2016 |SKU Standard ou superior |

* Não há suporte para a Formatação no Nível de Célula nem para recursos de conversão.
* Ações e Conjuntos Nomeados não são expostos no Power BI, mas você ainda pode se conectar a cubos multidimensionais que também contêm Ações ou Conjuntos Nomeados e criar visuais e relatórios.

<!-- Shared Install steps Include -->
[!INCLUDE [gateway-onprem-datasources-include](./includes/gateway-onprem-datasources-include.md)]

## <a name="download-and-install-the-on-premises-data-gateway"></a>Baixar e instalar o gateway de dados local
Para baixar o gateway, selecione **Gateway de Dados** no menu Downloads. Baixe o [gateway de dados local](http://go.microsoft.com/fwlink/?LinkID=820925).

![](media/service-gateway-onprem/powerbi-download-data-gateway.png)

<!-- Shared Install steps Include -->
[!INCLUDE [gateway-onprem-install-include](./includes/gateway-onprem-install-include.md)]

## <a name="install-the-gateway-in-personal-mode"></a>Instalar o gateway no modo pessoal
> [!NOTE]
> O modo pessoal só funcionará com o Power BI.
> 
> 

Depois que o gateway pessoal for instalado, você precisará iniciar o **Assistente de Configuração do Power BI Gateway – Personal**.

![](media/service-gateway-onprem/personal-gateway-launch-configuration.png)

Em seguida, você precisará entrar no Power BI para registrar o gateway no serviço de nuvem.

![](media/service-gateway-onprem/personal-gateway-signin.png)

Você também precisará fornecer o nome de usuário do Windows e a senha com a qual o serviço Windows será executado. Você pode especificar uma conta do Windows diferente da sua. O serviço do gateway será executado por meio dessa conta.

![](media/service-gateway-onprem/personal-gateway-windows-service.png)

Após a conclusão da instalação, você precisará ir para seus conjuntos de dados no Power BI e verificar se as credenciais foram inseridas para suas fontes de dados locais.

<a name="credentials"></a>

## <a name="storing-encrypted-credentials-in-the-cloud"></a>Armazenando credenciais criptografadas na nuvem
Quando você adiciona uma fonte de dados ao gateway, é necessário fornecer credenciais para essa fonte de dados. Todas as consultas à fonte de dados serão executadas com essas credenciais. As credenciais são criptografadas com segurança, usando a criptografia assimétrica, para que elas não possam ser descriptografadas na nuvem antes de serem armazenadas lá. As credenciais são enviadas para o computador que executa o gateway, no local em que são descriptografados quando as fontes de dados são acessadas.

<!-- Account and Port information -->
[!INCLUDE [gateway-onprem-accounts-ports-more](./includes/gateway-onprem-accounts-ports-more.md)]

<!-- How the gateway works -->
[!INCLUDE [gateway-onprem-how-it-works-include](./includes/gateway-onprem-how-it-works-include.md)]

## <a name="troubleshooting"></a>Solução de problemas
Se você tiver problemas ao instalar e configurar um gateway, veja [Solução de problemas do gateway de dados local](service-gateway-onprem-tshoot.md). Se você achar que está tendo um problema com seu firewall, confira a seção [proxy ou firewall](service-gateway-onprem-tshoot.md#firewall-or-proxy) no artigo de solução de problemas.

Caso ache que está tendo problemas de proxy com o gateway, veja [Definindo as configurações de proxy dos gateways do Power BI](service-gateway-proxy.md).

## <a name="next-steps"></a>Próximas etapas
[Gerenciar sua fonte de dados – Analysis Services](service-gateway-enterprise-manage-ssas.md)  
[Gerenciar sua fonte de dados – SAP HANA](service-gateway-enterprise-manage-sap.md)  
[Gerenciar sua fonte de dados – SQL Server](service-gateway-enterprise-manage-sql.md)  
[Gerenciar sua fonte de dados – Oracle](service-gateway-onprem-manage-oracle.md)  
[Gerenciar sua fonte de dados – Importar/Atualização agendada](service-gateway-enterprise-manage-scheduled-refresh.md)  
[Detalhes sobre o gateway de dados local](service-gateway-onprem-indepth.md)  
[Gateway de dados local (modo pessoal) – a nova versão do gateway pessoal](service-gateway-personal-mode.md)
[Definindo as configurações de proxy do gateway de dados local](service-gateway-proxy.md)  
Mais perguntas? [Experimente a Comunidade do Power BI](http://community.powerbi.com/)

