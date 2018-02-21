---
title: Conectar-se ao Office365Mon com o Power BI
description: Office365Mon para o Power BI
services: powerbi
documentationcenter: 
author: SarinaJoan
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
ms.author: sarinas
ms.openlocfilehash: ffff9747e9c24efd51c3ae3d10714de590170523
ms.sourcegitcommit: c24e5d7bd1806e0d637e974b5143ab5125298fc6
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/19/2018
---
# <a name="connect-to-office365mon-with-power-bi"></a>Conectar-se ao Office365Mon com o Power BI
Analisar seus dados de desempenho de integridade e interrupções do Office 365 é fácil com o Power BI e o pacote de conteúdo Office365Mon. O Power BI recupera seus dados, incluindo investigações de integridade e interrupções e, em seguida, compila um painel e relatórios prontos para uso com base em tais dados.

Conectar-se ao [pacote de conteúdo Office365Mon](https://app.powerbi.com/groups/me/getdata/services/office365mon) para Power BI.

>[!NOTE]
>Uma conta de administrador do Office365Mon é necessária para conectar e carregar o pacote de conteúdo do Power BI.

## <a name="how-to-connect"></a>Como se conectar
1. Selecione **Obter Dados** na parte inferior do painel de navegação esquerdo.
   
   ![](media/service-connect-to-office365mon/pbi_getdata.png)
2. Na caixa **Serviços** , selecione **Obter**.
   
   ![](media/service-connect-to-office365mon/pbi_getservices.png) 
3. Selecione **Office365Mon** \> **Obter**.
   
   ![](media/service-connect-to-office365mon/o365mon.png)
4. Para o Método de Autenticação, selecione **oAuth2** \> **Entrar**.
   
   Quando solicitado, insira suas credenciais de administrador do Office365Mon e siga o processo de autenticação.
   
   ![](media/service-connect-to-office365mon/creds.png)
   
   ![](media/service-connect-to-office365mon/creds2.png)
5. Após o Power BI importar os dados, você verá novos elementos (painel, relatório e conjunto de dados) no painel de navegação esquerdo. Novos itens são marcados com um asterisco amarelo \*; selecione a entrada do Office365Mon.
   
   ![](media/service-connect-to-office365mon/dashboard4.png)

**E agora?**

* Tente [fazer uma pergunta na caixa de P e R](power-bi-q-and-a.md) na parte superior do dashboard
* [Altere os blocos](service-dashboard-edit-tile.md) no dashboard.
* [Selecione um bloco](service-dashboard-tiles.md) para abrir o relatório subjacente.
* Enquanto seu conjunto de dados será agendado para ser atualizado diariamente, você pode alterar o agendamento de atualização ou tentar atualizá-lo sob demanda usando **Atualizar Agora**

## <a name="troubleshooting"></a>Solução de problemas
Se você receber um erro **"falha no logon"** depois de usar suas credenciais de assinatura do Office365Mon para fazer logon, a conta sendo usada não tem permissões para recuperar os dados do Office365Mon de sua conta. Verifique se que ela é uma conta de administrador e tente novamente.

## <a name="next-steps"></a>Próximas etapas
[Introdução ao Power BI](service-get-started.md)

[Obter dados para o Power BI](service-get-data.md)

