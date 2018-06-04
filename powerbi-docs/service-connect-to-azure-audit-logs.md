---
title: Conectar-se aos Logs de Auditoria do Azure com o Power BI
description: Logs de Auditoria do Azure para o Power BI
author: SarinaJoan
manager: kfile
ms.reviewer: maggiesMSFT
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 02/06/2018
ms.author: sarinas
LocalizationGroup: Connect to services
ms.openlocfilehash: 22020595b4f972f112f10e16fe7ae7d7fd4abed7
ms.sourcegitcommit: 80d6b45eb84243e801b60b9038b9bff77c30d5c8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34241717"
---
# <a name="connect-to-azure-audit-logs-with-power-bi"></a>Conectar-se aos Logs de Auditoria do Azure com o Power BI
Com o pacote de conteúdo de Logs de Auditoria do Azure, você pode analisar e visualizar as informações armazenadas nos logs de auditoria. O Power BI recupera seus dados, cria um painel inicial e cria relatórios com base nesses dados.

[Conecte-se ao pacote de conteúdo dos Logs de Auditoria do Azure](https://app.powerbi.com/getdata/services/azure-audit-logs) ou leia mais sobre a [integração dos Logs de Auditoria do Azure](https://powerbi.microsoft.com/integrations/azure-audit-logs) com o Power BI.

## <a name="how-to-connect"></a>Como se conectar
1. Selecione **Obter Dados** na parte inferior do painel de navegação esquerdo.  
   
    ![](media/service-connect-to-azure-audit-logs/getdata.png)
2. Na caixa **Serviços** , selecione **Obter**.  
   
    ![](media/service-connect-to-azure-audit-logs/services.png) 
3. Selecione **Logs de Auditoria do Azure** > **Obter**.  
   
   ![](media/service-connect-to-azure-audit-logs/azureauditlogs.png)
4. Quando solicitado, insira a **ID da assinatura do Azure**. Consulte detalhes sobre como localizar sua [ID da assinatura](#FindingParams) abaixo.   
   
    ![](media/service-connect-to-azure-audit-logs/parameters.png)
5. Para o **Método de Autenticação**, selecione **oAuth2** \> **Entrar**.
   
    ![](media/service-connect-to-azure-audit-logs/creds.png)
6. Insira suas credenciais de conta para concluir o processo de entrada.
   
    ![](media/service-connect-to-azure-audit-logs/login.png)
7. O Power BI recuperará seus dados do Log de Auditoria do Azure e criará um relatório e painel prontos para uso. 
   
    ![](media/service-connect-to-azure-audit-logs/dashboard.png)

**E agora?**

* Tente [fazer uma pergunta na caixa de P e R](power-bi-q-and-a.md) na parte superior do dashboard
* [Altere os blocos](service-dashboard-edit-tile.md) no dashboard.
* [Selecione um bloco](service-dashboard-tiles.md) para abrir o relatório subjacente.
* Enquanto seu conjunto de dados será agendado para ser atualizado diariamente, você pode alterar o agendamento de atualização ou tentar atualizá-lo sob demanda usando **Atualizar Agora**

## <a name="system-requirements"></a>Requisitos de sistema
O pacote de conteúdo de logs de Auditoria do Azure requer acesso aos Logs de Auditoria no Portal do Azure. Mais detalhes [aqui](https://azure.microsoft.com/documentation/articles/insights-debugging-with-events/).

<a name="FindingParams"></a>

## <a name="finding-parameters"></a>Localizando parâmetros
Há duas maneiras fáceis de localizar sua ID da Assinatura.

1. De https://portal.azure.com -&gt; Procurar -&gt; Assinaturas -&gt; ID da Assinatura
2. De https://manage.windowsazure.com -&gt; Configurações -&gt; ID da Assinatura

Sua ID da assinatura será um conjunto longo de números e caracteres, semelhantes ao exemplo da Etapa \#4 acima. 

## <a name="troubleshooting"></a>Solução de problemas
Se você estiver vendo um erro de credenciais ou de tentativa de atualização devido às credenciais inválidas, tente excluir todas as instâncias do pacote de conteúdo dos logs de Auditoria do Azure e reconectar.

## <a name="next-steps"></a>Próximas etapas
[Introdução ao Power BI](service-get-started.md)  
[Power BI – conceitos básicos](service-basic-concepts.md)  

