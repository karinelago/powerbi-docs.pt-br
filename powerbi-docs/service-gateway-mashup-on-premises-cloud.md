---
title: Mesclar ou acrescentar fontes de dados locais e na nuvem
description: Use o gateway de dados local para mesclar ou acrescentar fontes de dados locais e na nuvem na mesma consulta.
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-gateways
ms.topic: conceptual
ms.date: 06/06/2018
ms.author: mblythe
LocalizationGroup: Gateways
ms.openlocfilehash: 3550a3fc0cfc51b61e1d7e51a50c2a36325f2388
ms.sourcegitcommit: 49570ab8f5b5cd5bab4cd388f4281b1372bcb80b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/09/2018
ms.locfileid: "35250561"
---
# <a name="merge-or-append-on-premises-and-cloud-data-sources"></a>Mesclar ou acrescentar fontes de dados locais e na nuvem

O gateway de dados local permite mesclar ou acrescentar fontes de dados locais e na nuvem na mesma consulta. Isso é útil quando você deseja fazer mashup de dados de várias fontes sem precisar usar consultas separadas.

## <a name="prerequisites"></a>Pré-requisitos

- Um [gateway instalado](service-gateway-install.md) em um computador local.
- Um arquivo do Power BI Desktop com consultas que combinam fontes de dados locais e na nuvem.

1. No canto superior direito do serviço do Power BI, selecione o ícone de engrenagem ![Configurações](media/service-gateway-mashup-on-premises-cloud/icon-gear.png)  >  **Gerenciar gateways**.

    ![Gerenciar gateways](media/service-gateway-mashup-on-premises-cloud/manage-gateways.png)

2. Selecione o gateway que você deseja configurar.

3. Em **Configurações do Cluster de Gateway**, selecione **Permitir que as fontes de dados na nuvem do usuário sejam atualizadas por meio deste cluster de gateway** > **Aplicar**.

    ![Atualizar por meio deste cluster de gateway](media/service-gateway-mashup-on-premises-cloud/refresh-gateway-cluster.png)

4. Nesse cluster de gateway, adicione alguma [fonte de dados local](service-gateway-enterprise-manage-scheduled-refresh.md#add-a-data-source) usada em suas consultas. Você não precisa adicionar as fontes de dados na nuvem aqui.

4. Carregue no serviço do Power BI o seu arquivo do Power BI Desktop com as consultas que combinam fontes de dados locais e na nuvem.

5. Na página **Configurações do conjunto de dados** do novo conjunto de dados:

    - Para a fonte local, selecione o gateway associado a essa fonte de dados.

    - Em **Credenciais da fonte de dados**, edite as credenciais da fonte de dados na nuvem, conforme o necessário.

    ![Configurações do conjunto de dados](media/service-gateway-mashup-on-premises-cloud/dataset-settings.png)

6. Com o conjunto de credenciais de nuvem, agora você pode atualizar o conjunto de dados usando a opção **Atualizar agora** ou agendá-la para atualizar periodicamente.


## <a name="next-steps"></a>Próximas etapas

Para saber mais sobre a atualização dados para gateways, confira [Usando a fonte de dados para atualização agendada](service-gateway-enterprise-manage-scheduled-refresh.md#using-the-data-source-for-scheduled-refresh).