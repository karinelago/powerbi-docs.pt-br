---
title: "Conectar-se à Central de Segurança do Azure com o Power BI"
description: "Central de Segurança do Azure para o Power BI"
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
ms.openlocfilehash: e26a26d7cba2ae3d68586a2e0dcdf87481009bd6
ms.sourcegitcommit: d803e85bb0569f6b357ba0586f5702c20d27dac4
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/19/2018
---
# <a name="connect-to-azure-security-center-with-power-bi"></a>Conectar-se à Central de Segurança do Azure com o Power BI
Obtenha informações sobre a segurança de carga de trabalho do Azure conectando seus dados de segurança do Azure ao Power BI. O Power BI cria automaticamente um painel e relatórios sobre seus dados da Central de Segurança do Azure, permitindo que você analise e explore os dados.

Conectar-se ao [Pacote de conteúdo da Central de Segurança do Azure](https://app.powerbi.com/getdata/services/azure-security-center) para Power BI.

## <a name="how-to-connect"></a>Como se conectar
1. Selecione **Obter Dados** na parte inferior do painel de navegação esquerdo.
   
   ![](media/service-connect-to-azure-security-center/getdata.png)
2. Na caixa **Serviços** , selecione **Obter**.
   
   ![](media/service-connect-to-azure-security-center/services.png)
3. Selecione **Central de Segurança do Azure** \>  **Obter**.
   
   ![](media/service-connect-to-azure-security-center/asc.png)
4. Especifique sua ID de assinatura. Veja detalhes sobre como [encontrar esses parâmetros](#FindingParams) abaixo.
   
   ![](media/service-connect-to-azure-security-center/params.png)
5. Para o **Método de Autenticação**, selecione **oAuth2** \> **Entrar**. Quando solicitado, insira suas credenciais do Azure.
   
    ![](media/service-connect-to-azure-security-center/creds.png)
6. Após a aprovação, o processo de importação será iniciado automaticamente. Quando concluído, um novo painel, relatório e modelo aparecerão no Painel de Navegação. Selecione o painel para exibir os dados importados por você.
   
     ![](media/service-connect-to-azure-security-center/dashboard.png)

**E agora?**

* Tente [fazer uma pergunta na caixa de P e R](power-bi-q-and-a.md) na parte superior do dashboard
* [Altere os blocos](service-dashboard-edit-tile.md) no dashboard.
* [Selecione um bloco](service-dashboard-tiles.md) para abrir o relatório subjacente.
* Enquanto seu conjunto de dados será agendado para ser atualizado diariamente, você pode alterar o agendamento de atualização ou tentar atualizá-lo sob demanda usando **Atualizar Agora**

## <a name="whats-included"></a>O que está incluído
O pacote de conteúdo inclui informações sobre estatísticas de segurança de recursos, análise de alerta e análise de prevenção.

## <a name="system-requirements"></a>Requisitos de sistema
Este pacote de conteúdo requer acesso a uma ID de assinatura com a Central de Segurança do Azure habilitada. Consulte mais detalhes na [Central de Segurança do Azure](https://portal.azure.com/#blade/Microsoft_Azure_Security/SecurityDashboardStartBladeV2) no Portal do Azure.

O pacote de conteúdo também exige que o usuário se conecte com uma conta organizacional (não uma conta pessoal).

<a name="FindingParams"></a>

## <a name="finding-parameters"></a>Localizando parâmetros
Há duas maneiras fáceis de localizar sua ID da Assinatura.

1. De https://portal.azure.com -&gt; Procurar -&gt; Assinaturas -&gt; ID da assinatura
2. De https://manage.windowsazure.com -&gt; Configurações -&gt; ID da assinatura

Sua ID da assinatura será um conjunto longo de números e caracteres, semelhantes ao exemplo da Etapa \#4 acima. 

## <a name="troubleshooting"></a>Solução de problemas
Os dados podem levar algum tempo para carregar dependendo do tamanho da sua conta. Se você encontrou um erro durante o logon, confirme os parâmetros e que a conta tem a Central de Segurança do Azure habilitada.

Se o pacote de conteúdo é carregado, mas não mostra nenhum dado, confirme se você está se conectando com uma conta organizacional. Embora contas pessoais tenham suporte da Central de Segurança do Azure, a API (e, portanto, o pacote de conteúdo) não retorna os valores esperados se o usuário se conecta com uma conta não organizacional. Forneça acesso a uma conta organizacional e tente se conectar novamente.

## <a name="next-steps"></a>Próximas etapas
[Introdução ao Power BI](service-get-started.md)

[Obter dados no Power BI](service-get-data.md)

