---
title: Conectar-se ao Azure Search com o Power BI
description: Azure Search para o Power BI
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
ms.openlocfilehash: d868c50a69381c1ef95a8b3a69590223eb066e90
ms.sourcegitcommit: 88c8ba8dee4384ea7bff5cedcad67fce784d92b0
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/24/2018
---
# <a name="connect-to-azure-search-with-power-bi"></a>Conectar-se ao Azure Search com o Power BI
A Análise de Tráfego do Azure Search permite que você monitore e entenda o tráfego para o serviço de Azure Search. O pacote de conteúdo de Azure Search para o Power BI fornece informações detalhadas sobre seus dados de pesquisa, incluindo Search, Indexação, Status do Serviço e a Latência dos últimos 30 dias. Mais detalhes podem ser encontrados na [postagem do blog do Azure](https://azure.microsoft.com/en-us/blog/analyzing-your-azure-search-traffic/).

Conectar-se ao [pacote de conteúdo do Azure Search](https://app.powerbi.com/getdata/services/azure-search) para o Power BI.

## <a name="how-to-connect"></a>Como se conectar
1. Selecione **Obter Dados** na parte inferior do painel de navegação esquerdo.
   
   ![](media/service-connect-to-azure-search/pbi_getdata.png) 
2. Na caixa **Serviços** , selecione **Obter**.
   
   ![](media/service-connect-to-azure-search/pbi_getservices.png) 
3. Selecione **Azure Search**\>**Obter**.
   
   ![](media/service-connect-to-azure-search/azuresearch.png)
4. Forneça o nome da conta de armazenamento de tabela na qual sua análise do Azure Search está armazenada.
   
   ![](media/service-connect-to-azure-search/params.png)
5. Selecione **Chave** como Mecanismo de Autenticação e forneça sua chave de conta de armazenamento. Clique em **Entrar** para iniciar o processo de carregamento.
   
   ![](media/service-connect-to-azure-search/creds.png)
6. Quando o carregamento for concluído, um novo painel, relatório e modelo aparecerão no Painel de Navegação. Selecione o painel para exibir os dados importados por você.
   
    ![](media/service-connect-to-azure-search/dashboard2.png)

**E agora?**

* Tente [fazer uma pergunta na caixa de P e R](power-bi-q-and-a.md) na parte superior do dashboard
* [Altere os blocos](service-dashboard-edit-tile.md) no dashboard.
* [Selecione um bloco](service-dashboard-tiles.md) para abrir o relatório subjacente.
* Enquanto seu conjunto de dados será agendado para ser atualizado diariamente, você pode alterar o agendamento de atualização ou tentar atualizá-lo sob demanda usando **Atualizar Agora**

## <a name="system-requirements"></a>Requisitos de sistema
O pacote de conteúdo de Azure Search exige que a Análise de Tráfego do Azure Search esteja habilitada na conta.

## <a name="troubleshooting"></a>Solução de problemas
Certifique-se de que o nome da conta de armazenamento seja fornecido corretamente com a chave de acesso completo. O nome da conta de armazenamento deve corresponder à conta configurada com a Análise de Tráfego do Azure Search.

## <a name="next-steps"></a>Próximas etapas
[Introdução ao Power BI](service-get-started.md)

[Power BI – conceitos básicos](service-basic-concepts.md)

