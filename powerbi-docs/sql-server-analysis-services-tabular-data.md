---
title: "Dados dinâmicos do SQL Server Analysis Services no Power BI"
description: "Dados dinâmicos do SQL Server Analysis Services no Power BI. Isso é feito por meio de uma fonte de dados que foi configurada para um gateway corporativo."
services: powerbi
documentationcenter: 
author: markingmyname
manager: kfile
backup: 
editor: 
tags: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 08/10/2017
ms.author: maghan
ms.openlocfilehash: a2a0b2ae9f663f5bd2ba1c599f4f55232c0d1973
ms.sourcegitcommit: 6e693f9caf98385a2c45890cd0fbf2403f0dbb8a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2018
---
# <a name="sql-server-analysis-services-live-data-in-power-bi"></a>Dados dinâmicos do SQL Server Analysis Services no Power BI
No Power BI, há duas maneiras pelas quais você pode se conectar a um servidor do SQL Server Analysis Services dinâmico. Em **Obter dados**, você pode se conectar a um servidor do SQL Server Analysis Services ou se conectar [a um arquivo do Power BI Desktop](service-desktop-files.md) ou a uma [pasta de trabalho do Excel](service-excel-workbook-files.md) que já se conecta a um servidor do Analysis Services.

 >[!IMPORTANT]
 >* Para conectar-se a um servidor do Analysis Services, um gateway de dados local deverá ser instalado e configurado por um administrador. Para obter mais informações, veja [Gateway de dados local](service-gateway-onprem.md).
 >* Ao usar o gateway, seus dados permanecem locais.  Os relatórios criados com base nesses dados são salvos no serviço do Power BI. 
 >* [A consulta em linguagem natural por perguntas e respostas](service-q-and-a-direct-query.md) está na visualização para conexões dinâmicas do Analysis Services.

## <a name="to-connect-to-a-model-from-get-data"></a>Para conectar-se a um modelo em Obter dados
1. Em **Meu Espaço de Trabalho**, selecione **Obter dados**. Você também pode alterar para um espaço de trabalho de grupo, se houver um disponível.
   
   ![](media/sql-server-analysis-services-tabular-data/connecttoas_getdatabutton.png)
2. Selecione **Bancos de Dados e Mais**.
   
   ![](media/sql-server-analysis-services-tabular-data/connecttoas_getdata_1.png)
3. Selecione **SQL Server Analysis Services** > **Conectar**. 
   
   ![](media/sql-server-analysis-services-tabular-data/connecttoas_getdata_2.png)
4. Selecione um servidor. Se você não vir servidores listados aqui, isso significa que um gateway e uma fonte de dados não estão configurados, ou que sua conta não está listada na guia **Usuários** da fonte de dados no gateway. Verifique com o administrador.
5. Selecione o modelo ao qual você deseja se conectar. Ele pode ser Tabela ou Multidimensional.

Depois de se conectar ao modelo, ele será exibido no seu site do Power BI em **Meu Espaço de Trabalho/Conjuntos de Dados**. Se você fosse alternado para um espaço de trabalho de grupo, o conjunto de dados seria exibido dentro do grupo.

![](media/sql-server-analysis-services-tabular-data/connecttoas_dataset_5.png)

## <a name="dashboard-tiles"></a>Blocos de painel
Se você fixar visuais de um relatório no painel, os blocos fixos serão atualizados automaticamente a cada 10 minutos. Se os dados no servidor do Analysis Services local forem atualizados, os blocos serão atualizados automaticamente após 10 minutos.

## <a name="next-steps"></a>Próximas etapas
[Gateway de dados local](service-gateway-onprem.md)  
[Gerenciar fontes de dados do Analysis Services](service-gateway-enterprise-manage-ssas.md)  
[Solução de problemas do gateway de dados local](service-gateway-onprem-tshoot.md)  
Mais perguntas? [Experimente a Comunidade do Power BI](http://community.powerbi.com/)

