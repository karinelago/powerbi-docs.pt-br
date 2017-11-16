---
title: "Definir alertas de dados no serviço do Power BI"
description: "Saiba como definir alertas para notificá-lo quando os dados em seus dashboards forem alterados além dos limites definidos por você no serviço do Microsoft Power BI."
services: powerbi
documentationcenter: 
author: mihart
manager: kfile
backup: 
editor: 
tags: 
featuredvideoid: JbL2-HJ8clE
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 08/06/2017
ms.author: mihart
ms.openlocfilehash: cfbd7d124784b15b432921554c8ac5bbe321846c
ms.sourcegitcommit: 99cc3b9cb615c2957dde6ca908a51238f129cebb
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/13/2017
---
# <a name="data-alerts-in-power-bi-service"></a>Alertas de dados no serviço do Power BI
Defina alertas para notificá-lo quando os dados em seus dashboards forem alterados além dos limites definidos por você. Os alertas só podem ser configurados em blocos fixos de visuais de relatório e apenas em medidores, KPIs e cartões. Os alertas podem ser definidos em visuais criados de conjuntos de dados de streaming que foram fixados de um relatório para um dashboard, mas não podem ser definidos em blocos de streaming criados diretamente no dashboard usando **Adicionar bloco** > **Dados de streaming personalizados**. Apenas você poderá ver os alertas que definir, mesmo se compartilhar seu dashboard. Os alertas de dados são totalmente sincronizados nas plataformas; defina e exiba alertas de dados [nos aplicativos móveis do Power BI](mobile-set-data-alerts-in-the-mobile-apps.md) e no serviço do Power BI. Eles não estão disponíveis no Power BI Desktop. Os alertas podem até mesmo ser [automatizados e integrados com o Microsoft Flow](https://flow.microsoft.com) - [experimente por conta própria](service-flow-integration.md).

![](media/service-set-data-alerts/powerbi-alert-types-new.png)

> [!WARNING]
> Notificações de alerta controladas por dados fornecem informações sobre seus dados. Se você exibir os dados do Power BI em um dispositivo móvel e esse dispositivo for roubado, será recomendável usar o serviço do Power BI para desligar todas as regras de alerta controladas por dados.
> 
> 

## <a name="set-data-alerts-in-power-bi-service"></a>Defina alertas de dados no serviço do Power BI
Veja Amanda adicionando alguns alertas a blocos em seu dashboard. Em seguida, siga as instruções passo a passo abaixo do vídeo para testá-la por conta própria.

<iframe width="560" height="315" src="https://www.youtube.com/embed/JbL2-HJ8clE" frameborder="0" allowfullscreen></iframe>

Este exemplo usa um bloco de cartões do dashboard de exemplo de Análise de Varejo.

1. Iniciar em um dashboard. Em um medidor, KPI ou bloco de cartão do dashboard, selecione as reticências.
   
   ![](media/service-set-data-alerts/powerbi-card.png)
2. Selecione o ícone de sino ![](media/service-set-data-alerts/power-bi-bell-icon.png) para adicionar um ou mais alertas para o **Total de repositórios**.
   
   ![](media/service-set-data-alerts/powerbi-set-alert.png)
3. Para começar, verifique se o controle deslizante está definido como **Ligado** e dê um título ao seu alerta. Os títulos ajudam a reconhecer facilmente seus alertas.
   
   ![](media/service-set-data-alerts/powerbi-alert-title.png)
4. Role para baixo e insira os detalhes do alerta.  Neste exemplo, criaremos um alerta que nos notifica uma vez por dia caso o número do total de repositórios ultrapasse 100. Os alertas serão exibidos em nossa Central de Notificações. Além disso, o Power BI vai nos enviar um email.
   
   ![](media/service-set-data-alerts/powerbi-set-alert-details.png)
5. Selecione **Salvar**.

## <a name="receiving-alerts"></a>Recebendo alertas
Quando os dados que estão sendo controlados atingem um dos limites que você definiu, várias coisas acontecerão. Primeiro, o Power BI verifica se passou mais de uma hora ou mais de 24 horas (dependendo da opção selecionada) desde o envio do último alerta. Enquanto os dados estiverem acima do limite, você receberá um alerta.

Em seguida, o Power BI enviará um alerta para o centro de notificações e, como opção, para o email. Cada alerta contém um link direto com seus dados. Selecione o link para ver o bloco relevante em que você pode explorar, compartilhar e aprender mais.  

1. Se tiver definido que o alerta deve lhe enviar um email, você verá algo parecido com isto na Caixa de Entrada.
   
   ![](media/service-set-data-alerts/powerbi-alerts-email.png)
2. O Power BI adiciona uma mensagem à sua **Central de Notificações** e adiciona um novo ícone de alerta no bloco aplicável.
   
   ![](media/service-set-data-alerts/powerbi-alert-notifications.png)
3. Abra a Central de Notificações para ver os detalhes do alerta.
   
    ![](media/service-set-data-alerts/powerbi-alert-notfication.png)
   
   > [!NOTE]
   > Os alertas funcionam somente em dados que estão atualizados. Depois que os dados são atualizados, o Power BI verifica se foi definido um alerta para esses dados. Se os dados atingirem um limite de alerta, um alerta será disparado.
   > 
   > 

## <a name="managing-alerts"></a>Gerenciando alertas
Existem três maneiras de gerenciar seus alertas: no próprio bloco do dashboard, no menu Configurações do Power BI e em um bloco individual no [aplicativo móvel do Power BI no iPhone](mobile-set-data-alerts-in-the-mobile-apps.md) ou no [aplicativo móvel do Power BI para Windows 10](mobile-set-data-alerts-in-the-mobile-apps.md).

### <a name="from-the-tile-itself"></a>No próprio bloco
1. Se você precisar alterar ou remover um alerta para um bloco, abra novamente a janela **Gerenciar alertas** selecionando o ícone de sino ![](media/service-set-data-alerts/power-bi-bell-icon.png). Todos os alertas definidos para esse bloco são exibidos.
   
    ![](media/service-set-data-alerts/powerbi-see-alerts.png).
2. Para modificar um alerta, selecione a seta à esquerda do nome do alerta.
   
    ![](media/service-set-data-alerts/powerbi-see-alerts-arrow.png).
3. Para excluir um alerta, selecione a lixeira à direita do nome do alerta.
   
      ![](media/service-set-data-alerts/powerbi-see-alerts-delete.png)

### <a name="from-the-power-bi-settings-menu"></a>No menu de configurações do Power BI
1. Selecione o ícone de engrenagem na barra de menus do Power BI.
   
    ![](media/service-set-data-alerts/powerbi-gear-icon.png).
2. Em **Configurações**, selecione **Alertas**.
   
    ![](media/service-set-data-alerts/powerbi-alert-settings.png)
3. Aqui, é possível ativar e desativar alertas, abrir a janela **Gerenciar alertas** para fazer alterações ou excluir o alerta.

## <a name="tips-and-troubleshooting"></a>Dicas e solução de problemas
* Atualmente, não há suporte para alertas para blocos do Bing ou blocos de cartões com medidas de data/hora.
* Os alertas funcionam apenas com tipos de dados numéricos.
* Os alertas funcionam somente em dados que estão atualizados. Eles não funcionam em dados estáticos.
* Os alertas só funcionarão em conjuntos de dados de streaming se você criar um visual de relatório de KPI/cartão/medidor e fixá-lo no dashboard.

## <a name="next-steps"></a>Próximas etapas
[Criar um Microsoft Flow que inclui um alerta de dados](service-flow-integration.md)    
[Definir alertas de dados em seu dispositivo móvel](mobile-set-data-alerts-in-the-mobile-apps.md)    
[Introdução ao Power BI](service-get-started.md)    
Mais perguntas? [Experimente perguntar à Comunidade do Power BI](http://community.powerbi.com/)

