---
title: Instalar um gateway para o Power BI
description: Saiba como instalar um gateway para se conectar a dados locais no Power BI.
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-gateways
ms.topic: conceptual
ms.date: 04/18/2018
ms.author: mblythe
LocalizationGroup: Gateways
ms.openlocfilehash: 936e794b187366e91cf550c16379216ddf1fbf36
ms.sourcegitcommit: 80d6b45eb84243e801b60b9038b9bff77c30d5c8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34298540"
---
# <a name="install-a-gateway-for-power-bi"></a>Instalar um gateway para o Power BI

O Power BI Gateway é um software que você instala em uma rede local; ele facilita o acesso aos dados nessa rede. Conforme descrito na [visão geral](service-gateway-getting-started.md), você pode instalar um gateway no modo pessoal ou padrão (recomendado). No modo padrão, você pode instalar um gateway autônomo ou adicionar um gateway a um *cluster*, que é recomendado para alta disponibilidade. Neste artigo, mostramos como instalar um gateway padrão e, em seguida, adicionar outro gateway para criar um cluster.

Se você não estiver inscrito no Power BI, [inscreva-se para uma avaliação gratuita](https://app.powerbi.com/signupredirect?pbi_source=web) antes de começar.


## <a name="download-and-install-a-gateway"></a>Baixar e instalar um gateway

O gateway é executado no computador em que você o instala, portanto instale-o em um computador que sempre esteja ligado. Para você obter melhor desempenho e confiabilidade, recomendamos que o computador esteja em uma rede com fio em vez de uma sem fio.

1. No serviço do Power BI no canto superior direito, selecione o **ícone baixar** ![ícone Baixar](media/service-gateway-install/icon-download.png) > **Gateway de Dados**.

    ![Gateway de Dados](media/service-gateway-install/data-gateway.png)

2. Na página de download, selecione o botão **BAIXAR GATEWAY**.

3. Selecione **Avançar**.     

    ![Instalador do gateway de dados](media/service-gateway-install/gateway-installer.png)

4. Selecione **Gateway de dados local (recomendado)** > **Avançar**.

    ![Tipo de gateway](media/service-gateway-install/gateway-type.png)

5. Mantenha o caminho de instalação padrão e aceite os termos > **Instalar**.

    ![Caminho de Instalação](media/service-gateway-install/install-path.png)

6. Insira a conta usada para entrar no Power BI > **Entrar**.

    ![Endereço de email](media/service-gateway-install/email-address.png)

    O gateway está associado à sua conta do Power BI e você gerencia gateways de dentro do serviço do Power BI. Agora, você está conectado à sua conta.

7. Selecione **Registrar um novo gateway neste computador** > **Avançar**.

    ![Registrar gateway](media/service-gateway-install/register-gateway.png)

8. Insira um nome para o gateway (deve ser exclusivo na locatário) e uma chave de recuperação. Você precisará dessa chave se quiser recuperar ou mover seu gateway. Selecione **Configurar**.

    ![Configurar gateway](media/service-gateway-install/configure-gateway.png)

    Observe a opção **Adicionar a um cluster existente do gateway**. Vamos usar essa opção na próxima seção do artigo.

9. Examine as informações na janela final. Observe que o gateway está disponível para o Power BI e também o PowerApps e o Flow, porque eu uso a mesma conta para os três. Selecione **Fechar**.

    ![Tela de resumo](media/service-gateway-install/summary-screen.png)

Agora que instalou com êxito um gateway, você pode adicionar outro gateway para criar um cluster.


## <a name="add-another-gateway-to-create-a-cluster"></a>Adicionar outro gateway para criar um cluster

Um cluster permite que os administradores de gateway evitem ter um ponto único de falha para o acesso a dados local. Se o gateway primário não estiver disponível, as solicitações de dados serão encaminhadas para o segundo gateway que você adicionar e assim por diante. Você pode instalar apenas um gateway padrão em um computador, portanto, você precisa instalar o segundo gateway do cluster em um computador diferente. Isso faz sentido porque você quer ter redundância no cluster.

Os clusters de gateway de alta disponibilidade requerem a atualização de novembro de 2017 para o gateway de dados locais, ou posterior.

1. Baixe o gateway para outro computador e instale-o.

2. Após entrar na sua conta do Power BI, registre o gateway. Selecione **Adicionar a um cluster existente**. Em **Clusters de gateway disponíveis**, selecione o primeiro gateway que você instalou (o *gateway primário*) e insira a chave de recuperação do gateway. Selecione **Configurar**.

    ![Adicionar um gateway a um cluster](media/service-gateway-install/add-cluster.png)


## <a name="next-steps"></a>Próximas etapas

[Gerenciar o Power BI Gateway](service-gateway-manage.md)

Mais perguntas? [Experimente a Comunidade do Power BI](http://community.powerbi.com/)