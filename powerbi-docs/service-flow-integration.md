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
ms.date: 01/22/2018
ms.author: mihart
ms.openlocfilehash: edae145e8eef6dfe7a2c4cea3a7f467f6f7961a9
ms.sourcegitcommit: c3be4de522874fd73fe6854333b379b85619b907
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2018
---
# <a name="microsoft-flow-and-power-bi"></a>Microsoft Flow e Power BI

[Microsoft Flow](https://flow.microsoft.com/en-us/documentation/getting-started) é uma oferta de SaaS para automatizar os fluxos de trabalho entre o número crescente de serviços SaaS e aplicativos nos quais os usuários empresariais dependem. Com o Flow, é possível automatizar tarefas integrando seus aplicativos e serviços favoritos (incluindo o Power BI) para obter notificações, sincronizar os arquivos, coletar dados e muito mais. Tarefas repetitivas se tornam fácil com a automação do fluxo de trabalho.

[Começar a usar o Flow agora.](https://flow.microsoft.com/documentation/getting-started)

Assista a Sirui criar um Fluxo que envia um email detalhado para colegas quando um alerta do Power BI é disparado. Em seguida, siga as instruções passo a passo abaixo do vídeo para testá-la por conta própria.

<iframe width="560" height="315" src="https://www.youtube.com/embed/YhmNstC39Mw" frameborder="0" allowfullscreen></iframe>

## <a name="create-a-flow-that-is-triggered-by-a-power-bi-data-alert"></a>Criar um fluxo disparado por um alerta de dados do Power BI

### <a name="prerequisites"></a>Pré-requisitos
Este tutorial mostra como criar dois fluxos diferentes; um de um modelo e um do zero. Para acompanhar, [crie um alerta de dados no Power BI](service-set-data-alerts.md), crie uma conta gratuita no Slack e [inscreva-se no Microsoft Flow](https://flow.microsoft.com/en-us/#home-signup) (é gratuito!).

## <a name="create-a-flow-that-uses-power-bi---from-a-template"></a>Criar um fluxo que usa Power BI de um modelo
Nesta tarefa, usaremos um modelo para criar um fluxo simples que é disparado por um alerta de dados do Power BI (notificação).

1. Entre no Microsoft Flow (flow.microsoft.com).
2. Selecione **Meus fluxos**.
   
   ![](media/service-flow-integration/power-bi-my-flows.png)
3. Selecione **Criar do modelo**.
   
    ![](media/service-flow-integration/power-bi-template.png)
4. Use a caixa Pesquisar para localizar modelos do Power BI e selecione **Enviar um email para qualquer público quando um alerta de dados do Power BI for disparado > Continuar**.
   
    ![](media/service-flow-integration/power-bi-flow-alert.png)


### <a name="build-the-flow"></a>Criar o fluxo
Este modelo tem um gatilho (alerta de dados do Power BI para novas medalhas olímpicas para Irlanda) e uma ação (enviar um email). Conforme você seleciona um campo, o Flow exibe conteúdo dinâmico que pode ser incluído.  Nesse exemplo, incluímos o valor e a URL do bloco no corpo da mensagem.

![](media/service-flow-integration/power-bi-template1.png)

1. No menu suspenso do gatilho, selecione um alerta de dados do Power BI. Selecione **Nova medalha para a Irlanda**. Para saber como criar um alerta, consulte [Alertas de dados no Power BI](service-set-data-alerts.md).
   
   ![](media/service-flow-integration/power-bi-trigger-flow.png)
2. Insira um ou mais endereços de email válido e, em seguida, selecione **Editar** (mostrado abaixo) ou **Adicionar conteúdo dinâmico**. 
   
   ![](media/service-flow-integration/power-bi-flow-email.png)

3. O Flow cria um título e uma mensagem que você pode guardar ou modificar. Todos os valores que você definiu quando criou o alerta no Power BI estão disponíveis para uso: basta colocar o cursor e selecionar na área cinza realçada. 

   ![](media/service-flow-integration/power-bi-flow-email-default.png)

1.  Por exemplo, se você tiver criado um título do alerta no Power BI dizendo **Ganhamos outra medalha**, poderá selecionar **Título do alerta** para adicionar esse texto ao campo Assunto do email.

    ![](media/service-flow-integration/power-bi-flow-message.png)

    E você pode aceitar o corpo do email padrão ou criar seu próprio. O exemplo acima contém algumas modificações na mensagem.

1. Ao terminar, selecione **Criar fluxo** ou **Salvar fluxo**.  O fluxo é criado e avaliado.  O Flow avisa se encontrar erros.
2. Se forem encontrados erros, selecione **Editar fluxo** para corrigi-los, caso contrário, selecione **Feito** para executar o novo fluxo.
   
   ![](media/service-flow-integration/power-bi-flow-running.png)
5. Quando o alerta de dados for disparado, um email será enviado para os endereços que você indicou.  
   
   ![](media/service-flow-integration/power-bi-flow-email2.png)

## <a name="create-a-flow-that-uses-power-bi---from-scratch-blank"></a>Criar um fluxo que usa o Power BI do zero (em branco)
Nesta tarefa, criaremos um fluxo simples do zero que é disparado por um alerta de dados do Power BI (notificação).

1. Entre no Microsoft Flow.
2. Selecione **Meus fluxos** > **Criar em branco**.
   
   ![](media/service-flow-integration/power-bi-my-flows.png)
3. Use a caixa Pesquisar para localizar um gatilho do Power BI e selecione **Power BI – quando um alerta orientado a dados for disparado**.

### <a name="build-your-flow"></a>Criar seu fluxo
1. No menu suspenso, selecione o nome do alerta.  Para saber como criar um alerta, consulte [Alertas de dados no Power BI](service-set-data-alerts.md).
   
    ![](media/service-flow-integration/power-bi-totalstores2.png)
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

## <a name="next-steps"></a>Próximas etapas
* [Introdução ao Microsoft Flow](https://flow.microsoft.com/en-us/documentation/getting-started/)
* [Definir alertas de dados no serviço do Power BI](service-set-data-alerts.md)
* [Definir alertas de dados no seu iPhone](mobile-set-data-alerts-in-the-mobile-apps.md)
* [Definir alertas de dados no aplicativo móvel do Power BI para Windows 10](mobile-set-data-alerts-in-the-mobile-apps.md)
* Mais perguntas? [Experimente a Comunidade do Power BI](http://community.powerbi.com/)

