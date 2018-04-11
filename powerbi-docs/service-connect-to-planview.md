---
title: Conectar-se ao Planview Enterprise com o Power BI
description: Planview Enterprise para o Power BI
services: powerbi
documentationcenter: ''
author: SarinaJoan
manager: kfile
backup: maggiesMSFT
editor: ''
tags: ''
qualityfocus: no
qualitydate: ''
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 10/16/2017
ms.author: sarinas
LocalizationGroup: Connect to services
ms.openlocfilehash: 2376b639ad6a6ca843f997e52cedcce4c9832a7a
ms.sourcegitcommit: 88c8ba8dee4384ea7bff5cedcad67fce784d92b0
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/24/2018
---
# <a name="connect-to-planview-enterprise-with-power-bi"></a>Conectar-se ao Planview Enterprise com o Power BI
Com o pacote de conteúdo do Planview Enterprise, você pode visualizar seus dados de gerenciamento de trabalho e recursos de formas totalmente novas diretamente no Power BI. Use suas credenciais de logon do Planview Enterprise para ver de maneira interativa seus gastos de investimento de portfólio, entender os pontos em que você está acima e abaixo do orçamento e saber até que ponto seus projetos se alinham com suas prioridades estratégicas corporativas. Também é possível estender o painel e os relatórios prontos para uso para obter as informações mais importantes para você.

Conectar-se ao [pacote de conteúdo do Planview Enterprise no Power BI](https://app.powerbi.com/getdata/services/planview-enterprise)

>[!NOTE]
>Para importar dados do Planview Enterprise para o Power BI, você deve ser um usuário do Planview Enterprise com o recurso Visualizador de Portal de Relatório habilitado em sua função. Consulte abaixo os requisitos adicionais.

## <a name="how-to-connect"></a>Como se conectar
1. Selecione **Obter Dados** na parte inferior do painel de navegação esquerdo.
   
    ![](media/service-connect-to-planview/get.png)
2. Na caixa **Serviços** , selecione **Obter**.
   
    ![](media/service-connect-to-planview/services.png)
3. Na página do Power BI, selecione**Planview Enterprise** e, em seguida, selecione **Obter**:  
    ![](media/service-connect-to-planview/planview.png)
4. Na caixa de texto URL do Planview Enterprise, insira a URL do servidor do Planview Enterprise que deseja usar. Na caixa de texto Planview Enterprise Database, insira o nome do banco de dados do Planview Enterprise e clique em Avançar.  
    ![](media/service-connect-to-planview/params.png)
5. Na lista Método de Autenticação, selecione **Básico** se essa opção ainda não estiver marcada. Insira o **Nome de usuário** e a **Senha** de sua conta e selecione **Entrar**.  
   ![](media/service-connect-to-planview/creds.png)
6. No painel esquerdo, selecione Planview Enterprise na lista de painéis.  
     O Power BI importa os dados do Planview Enterprise para o painel. Observe que os dados podem levar algum tempo para carregar.  
    ![](media/service-connect-to-planview/dashboard.png)

**E agora?**

* Tente [fazer uma pergunta na caixa de P e R](power-bi-q-and-a.md) na parte superior do dashboard
* [Altere os blocos](service-dashboard-edit-tile.md) no dashboard.
* [Selecione um bloco](service-dashboard-tiles.md) para abrir o relatório subjacente.
* Enquanto seu conjunto de dados será agendado para ser atualizado diariamente, você pode alterar o agendamento de atualização ou tentar atualizá-lo sob demanda usando **Atualizar Agora**

## <a name="system-requirements"></a>Requisitos de sistema
Para importar dados do Planview Enterprise para o Power BI, você deve ser um usuário do Planview Enterprise com o recurso Visualizador de Portal de Relatório habilitado em sua função. Consulte abaixo os requisitos adicionais.

Este procedimento pressupõe que você já entrou na home page do Microsoft Power BI com uma conta do Power BI. Se você não tiver uma conta do Power BI, crie uma nova conta gratuita do Power BI na home page do Power BI e clique em Obter Dados.

## <a name="next-steps"></a>Próximas etapas:

[Introdução ao Power BI](service-get-started.md)

[Obter dados para o Power BI](service-get-data.md)