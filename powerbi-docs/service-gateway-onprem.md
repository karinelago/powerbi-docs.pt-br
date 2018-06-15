---
title: Gateway de dados local
description: Esta é uma visão geral do Gateway de dados local para o Power BI. É possível usar este gateway para trabalhar com fontes de dados do DirectQuery. Você também pode usar este gateway para atualizar conjuntos de dados de nuvem com dados locais.
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 06/05/2018
ms.author: mblythe
LocalizationGroup: Gateways
ms.openlocfilehash: c91e257d79e9d16fa5a7a58b696d58aefaaaaf92
ms.sourcegitcommit: 8ee0ebd4d47a41108387d13a3bc3e7e2770cbeb8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2018
ms.locfileid: "34812803"
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

## <a name="download-and-install-the-on-premises-data-gateway"></a>Baixar e instalar o Gateway de dados local
Para baixar o gateway, selecione **Gateway de Dados** no menu Downloads. Baixe o [Gateway de dados local](http://go.microsoft.com/fwlink/?LinkID=820925). 

Observe que a atualização do gateway de dados local é realizada reinstalando o gateway, conforme descrito nesta seção. Ao atualizar o gateway (reinstalando-o), as configurações do gateways existentes são mantidas.

![](media/service-gateway-onprem/powerbi-download-data-gateway.png)

<!-- Shared Install steps Include -->
[!INCLUDE [gateway-onprem-install-include](./includes/gateway-onprem-install-include.md)]

## <a name="install-the-gateway-in-personal-mode"></a>Instalar o gateway no modo pessoal
> [!NOTE]
> A versão pessoal do gateway somente funciona com o Power BI.


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

## <a name="limitations-and-considerations"></a>Limitações e considerações
* No momento, não há suporte para a [Proteção de Informações do Azure](https://docs.microsoft.com/en-us/microsoft-365/enterprise/protect-files-with-aip
)
* No momento, não há suporte para o [Access Online](https://products.office.com/en-us/access)

## <a name="tenant-level-administration"></a>Administração de nível de locatário 

Não há no momento nenhum único local em que os administradores de locatários podem gerenciar todos os gateways que outros usuários têm instalados e configurados.  Se você é um administrador de locatários, recomendamos que você peça aos usuários em sua organização que lhe adicionem como um administrador para cada gateway que instalarem. Isso permite que você gerencie todos os gateways na sua organização por meio da página de Configurações de Gateway ou pelos [comandos do PowerShell](https://docs.microsoft.com/power-bi/service-gateway-high-availability-clusters#powershell-support-for-gateway-clusters). 

## <a name="enabling-outbound-azure-connections"></a>Habilitando as conexões de saída do Azure 
O gateway de dados local se baseia no Barramento de Serviço do Azure para conectividade de nuvem e, de forma correspondente, estabelece conexões de saída com a região do Azure associada. Por padrão, esse é o local do seu locatário do Power BI. Confira [Onde está localizado meu locatário do Power BI?](https://powerbi.microsoft.com/en-us/documentation/powerbi-admin-where-is-my-tenant-located/)
Se um firewall estiver bloqueando as conexões de saída, será necessário configurá-lo para permitir conexões de saída do gateway de dados local com a região do Azure associada. Confira [Microsoft Azure Datacenter IP Ranges](https://www.microsoft.com/en-us/download/details.aspx?id=41653) para obter detalhes sobre os intervalos de endereço IP de cada data center do Azure.
> [!NOTE]
> Os intervalos de endereço IP podem mudar ao longo do tempo, portanto, baixe as informações mais recentes regularmente. 

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

