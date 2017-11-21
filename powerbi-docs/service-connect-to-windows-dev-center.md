---
title: Conectar-se ao Centro de Desenvolvimento do Windows com o Power BI
description: Centro de Desenvolvimento do Windows para o Power BI
services: powerbi
documentationcenter: 
author: joeshoukry
manager: kfile
backup: maggiesMSFT
editor: 
tags: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 10/16/2017
ms.author: yshoukry
ms.openlocfilehash: d88e10b4ee2e76444fccec0edabddd2a123d6b62
ms.sourcegitcommit: 284b09d579d601e754a05fba2a4025723724f8eb
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/15/2017
---
# <a name="connect-to-windows-dev-center-with-power-bi"></a>Conectar-se ao Centro de Desenvolvimento do Windows com o Power BI
Explore e monitore seus dados de análise de aplicativo do Centro de Desenvolvimento do Windows no Power BI com o pacote de conteúdo do Power BI. Os dados serão atualizados automaticamente uma vez por dia.

Conecte-se ao [pacote de conteúdo do Centro de Desenvolvimento do Windows](https://app.powerbi.com/getdata/services/devcenter) para Power BI.

## <a name="how-to-connect"></a>Como se conectar
1. Selecione **Obter Dados** na parte inferior do painel de navegação esquerdo.
   
   ![](media/service-connect-to-windows-dev-center/getdata.png)
2. Na caixa **Serviços** , selecione **Obter**.
   
   ![](media/service-connect-to-windows-dev-center/services.png)
3. Selecione **Centro de Desenvolvimento do Windows** \> **Conectar**.
   
   ![](media/service-connect-to-windows-dev-center/windowsdev.png)
4. Insira a ID do aplicativo de um aplicativo que você possui e clique em Avançar. Veja detalhes sobre como [encontrar esses parâmetros](#FindingParams) abaixo.
   
   ![](media/service-connect-to-windows-dev-center/params.png)
5. Para o **Método de Autenticação**, selecione **oAuth2** \> **Entrar**. Quando solicitado, insira as credenciais do Azure Active Directory associadas à sua conta do Centro de Desenvolvimento do Windows (mais detalhes em [Requisitos de Sistema](#Requirements)).
   
    ![](media/service-connect-to-windows-dev-center/creds.png)
   
    ![](media/service-connect-to-windows-dev-center/creds2.png)
6. Após a aprovação, o processo de importação será iniciado automaticamente. Quando concluído, um novo painel, relatório e modelo aparecerão no Painel de Navegação. Selecione o painel para exibir os dados importados e escolha um bloco para navegar até os relatórios subjacentes.
   
    ![](media/service-connect-to-windows-dev-center/dashboard.png)
   
    ![](media/service-connect-to-windows-dev-center/report.png)

**E agora?**

* Tente [fazer uma pergunta na caixa de P e R](service-q-and-a.md) na parte superior do dashboard
* [Altere os blocos](service-dashboard-edit-tile.md) no dashboard.
* [Selecione um bloco](service-dashboard-tiles.md) para abrir o relatório subjacente.
* Enquanto seu conjunto de dados será agendado para ser atualizado diariamente, você pode alterar o agendamento de atualização ou tentar atualizá-lo sob demanda usando **Atualizar Agora**

## <a name="whats-included"></a>O que está incluído
O pacote de conteúdo do Power BI do Centro de Desenvolvimento inclui dados de análise de seu aplicativo e aquisições de IAP, classificações, resenhas e integridade do aplicativo. Os dados são limitados aos últimos 3 meses e é uma janela móvel, portanto as datas inclusas serão atualizadas à medida que o conjunto de dados for atualizado.

<a name="Requirements"></a>

## <a name="system-requirements"></a>Requisitos de sistema
Este pacote de conteúdo requer pelo menos um aplicativo publicado na Windows Store e uma conta do Centro de Desenvolvimento do Windows (mais detalhes [aqui](https://msdn.microsoft.com/windows/uwp/publish/manage-account-users)).

<a name="FindingParams"></a>

## <a name="finding-parameters"></a>Localizando parâmetros
Você pode encontrar a ID de um aplicativo acessando a página Identidade do aplicativo em Gerenciamento do aplicativo.

A ID do aplicativo está no final de sua URL da Windows 10 Store, https://www.microsoft.com/store/apps/ **{applicationId}**

## <a name="next-steps"></a>Próximas etapas
[Introdução ao Power BI](service-get-started.md)

[Obter dados no Power BI](service-get-data.md)

