---
title: "Tutorial: integração do Power BI com o Microsoft Flow"
description: Aprenda a criar fluxos disparados por alertas de dados do Power BI.
services: powerbi
documentationcenter: 
author: mihart
manager: kfile
backup: 
editor: 
tags: 
featuredvideoid: YhmNstC39Mw
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 10/30/2017
ms.author: mihart
ms.openlocfilehash: 387f6bf9f9022fedf1266c32da3d61d3035e7d90
ms.sourcegitcommit: 99cc3b9cb615c2957dde6ca908a51238f129cebb
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/13/2017
---
# <a name="microsoft-flow-and-power-bi"></a>Microsoft Flow e Power BI
## <a name="what-is-microsoft-flow"></a>O que é o Microsoft Flow?
[Microsoft Flow](https://flow.microsoft.com/en-us/documentation/getting-started) é uma oferta de SaaS para automatizar os fluxos de trabalho entre o número crescente de serviços SaaS e aplicativos nos quais os usuários empresariais dependem. Com o Flow, é possível automatizar tarefas integrando seus aplicativos e serviços favoritos (incluindo o Power BI) para obter notificações, sincronizar os arquivos, coletar dados e muito mais. Tarefas repetitivas se tornam fácil com a automação do fluxo de trabalho.

[Começar a usar o Flow agora.](https://flow.microsoft.com/documentation/getting-started)

Assista a Sirui criar um Fluxo que envia um email detalhado para colegas quando um alerta do Power BI é disparado. Em seguida, siga as instruções passo a passo abaixo do vídeo para testá-la por conta própria.

<iframe width="560" height="315" src="https://www.youtube.com/embed/YhmNstC39Mw" frameborder="0" allowfullscreen></iframe>

## <a name="create-a-flow-that-is-triggered-by-a-power-bi-data-alert"></a>Criar um fluxo disparado por um alerta de dados do Power BI
Este tutorial mostra como criar dois fluxos diferentes; um de um modelo e um do zero. Para acompanhar, [crie um alerta de dados no Power BI](service-set-data-alerts.md) e [inscreva-se no Microsoft Flow](https://flow.microsoft.com/en-us/#home-signup) (é gratuito!).

## <a name="create-a-flow-that-uses-power-bi---from-a-template"></a>Criar um fluxo que usa Power BI de um modelo
Nesta tarefa, usaremos um modelo para criar um fluxo simples que é disparado por um alerta de dados do Power BI (notificação).

1. Entre no Microsoft Flow (flow.microsoft.com).
2. Selecione **Meus fluxos**.
   
   ![](media/service-flow-integration/power-bi-my-flows.png)
3. Selecione **Criar do modelo**.
   
    ![](media/service-flow-integration/power-bi-template.png)
4. Use a caixa Pesquisar para localizar modelos de Power BI e selecione **Postar uma mensagem em um canal Slack quando um alerta de dados do Power BI for disparado**.
   
    ![](media/service-flow-integration/power-bi-template2.png)
5. Selecione **Usar este modelo**.
   
   ![](media/service-flow-integration/power-bi-use-template.png)
6. Se solicitado, conecte-se ao Slack e ao Power BI selecionando **Entrar** e, em seguida, siga as instruções. Uma marca de seleção verde permite saber o que você está conectado.  Depois de confirmar suas conexões, selecione **Continuar**.
   
   ![](media/service-flow-integration/power-bi-flow-signin.png)

### <a name="build-the-flow"></a>Criar o fluxo
Este modelo tem um gatilho (alerta de dados do Power BI para novas medalhas olímpicas para Irlanda) e uma ação (postar uma mensagem para a o Slack). Conforme você seleciona um campo, o Flow exibe conteúdo dinâmico que pode ser incluído.  Nesse exemplo, incluímos o valor e a URL do bloco no corpo da mensagem.

![](media/service-flow-integration/power-bi-flow-template.png)

1. No menu suspenso do gatilho, selecione um alerta de dados do Power BI. Selecione **Nova medalha para a Irlanda**. Para saber como criar um alerta, consulte [Alertas de dados no Power BI](service-set-data-alerts.md).
   
   ![](media/service-flow-integration/power-bi-trigger-flow.png)
2. Para postar no Slack, digite o nome do canal e texto da mensagem (você também pode selecionar a mensagem padrão que o Flow cria). Observe o conteúdo dinâmico que incluímos no campo de texto da mensagem.
   
   > [!NOTE]
   > Inclua "@" no início do nome do canal.  Por exemplo, se o canal Slack for chamado “channelA”, insira "@channelA" no Flow.
   > 
   > 
   
   ![](media/service-flow-integration/power-bi-flow-slacker.png)
3. Ao terminar, selecione **Criar fluxo** ou **Salvar fluxo**.  O fluxo é criado e avaliado.  O Flow avisa se encontrar erros.
4. Se forem encontrados erros, selecione **Editar fluxo** para corrigi-los, caso contrário, selecione **Feito** para executar o novo fluxo.
   
   ![](media/service-flow-integration/power-bi-flow-running.png)
5. Abra sua conta do Slack para ver a mensagem.  
   
   ![](media/service-flow-integration/power-bi-slack-message.png)

## <a name="create-a-flow-that-uses-power-bi---from-scratch-blank"></a>Criar um fluxo que usa o Power BI do zero (em branco)
Nesta tarefa, criaremos um fluxo simples do zero que é disparado por um alerta de dados do Power BI (notificação).

1. Entre no Microsoft Flow.
2. Selecione **Meus fluxos** > **Criar em branco**.
   
   ![](media/service-flow-integration/power-bi-my-flows.png)
3. Use a caixa Pesquisar para encontrar um gatilho do Power BI e selecione **Disparar um fluxo com um alerta controlado por dados do Power BI**.

### <a name="build-your-flow"></a>Criar seu fluxo
1. No menu suspenso, selecione o nome do alerta.  Para saber como criar um alerta, consulte [Alertas de dados no Power BI](service-set-data-alerts.md).
   
    ![](media/service-flow-integration/power-bi-totalstores.png)
2. Selecione **Nova etapa** > **Adicionar uma ação**.
   
   ![](media/service-flow-integration/power-bi-new-step.png)
3. Pesquise por **Outlook** e selecione **Criar evento**.
   
   ![](media/service-flow-integration/power-bi-create-event.png)
4. Preencha os campos no evento. Conforme você seleciona um campo, o Flow exibe conteúdo dinâmico que pode ser incluído.
   
   ![](media/service-flow-integration/power-bi-flow-event.png)
5. Selecione **Criar fluxo** quando terminar.  O Flow salva e avalia o fluxo. Se não houver nenhum erro, selecione **Feito** para executar esse fluxo.  O novo fluxo é adicionado à página **Meus fluxos**.
   
   ![](media/service-flow-integration/power-bi-flow-running.png)
6. Quando o fluxo for disparado pelo alerta de dados do Power BI, você receberá uma notificação de eventos do Outlook semelhante a esta.
   
    ![](media/service-flow-integration/power-bi-flow-notice.png)

### <a name="next-steps"></a>Próximas etapas
* [Introdução ao Microsoft Flow](https://flow.microsoft.com/en-us/documentation/getting-started/)
* [Definir alertas de dados no serviço do Power BI](service-set-data-alerts.md)
* [Definir alertas de dados no seu iPhone](mobile-set-data-alerts-in-the-mobile-apps.md)
* [Definir alertas de dados no aplicativo móvel do Power BI para Windows 10](mobile-set-data-alerts-in-the-mobile-apps.md)
* Mais perguntas? [Experimente a Comunidade do Power BI](http://community.powerbi.com/)

