---
title: Capturando de informações adicionais de diagnóstico
description: Capturando de informações adicionais de diagnóstico
services: powerbi
documentationcenter: ''
author: mgblythe
manager: kfile
backup: ''
editor: ''
tags: ''
qualityfocus: no
qualitydate: ''
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 06/28/2017
ms.author: mblythe
LocalizationGroup: Troubleshooting
ms.openlocfilehash: 9aef989b4b61ce8c9d11fd4275d68c867791f644
ms.sourcegitcommit: 8552a34df8e6141eb704314c1a019992901d6e78
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2018
---
# <a name="capturing-additional-diagnostic-information"></a>Capturando de informações adicionais de diagnóstico
## <a name="capturing-additional-diagnostic-information-for-power-bi"></a>Capturar Informações de Diagnóstico Adicionais para o Power BI
Estas instruções fornecem duas opções possíveis para coletar manualmente as informações adicionais de diagnóstico do cliente Web Power BI.  Somente uma dessas opções deve ser seguida.

## <a name="network-capture---edge--internet-explorer"></a>Captura de rede – Edge e Internet Explorer
1. Navegue até [Power BI](https://app.powerbi.com) com o Edge ou Internet Explorer.
2. Abra as ferramentas de desenvolvedor do Edge pressionando F12.
3. Isso abrirá a janela de Ferramentas de Desenvolvedor: 
   
   ![](media/service-admin-capturing-additional-diagnostic-information-for-power-bi/edge-developer-tools.png)
4. Mude para a guia Rede. Ele listará o tráfego que já foi capturado. 
   
   ![](media/service-admin-capturing-additional-diagnostic-information-for-power-bi/edge-network-tab.png)
5. É possível navegar na janela e reproduzir qualquer problema que talvez você esteja enfrentando. Você pode ocultar e mostrar a janela de ferramentas de desenvolvedor a qualquer momento durante a sessão, pressionando F12.
6. Para interromper a captura, é possível selecionar o quadrado vermelho na guia Rede da área de ferramentas de desenvolvedor.
   
   ![](media/service-admin-capturing-additional-diagnostic-information-for-power-bi/edge-network-tab-stop.png)
7. Selecione o ícone de disquete para **Exportar como HAR**
   
   ![](media/service-admin-capturing-additional-diagnostic-information-for-power-bi/edge-network-tab-save.png)
8. Forneça um nome de arquivo e salve o arquivo HAR.
   
    O arquivo HAR contém todas as informações sobre solicitações de rede entre a janela do navegador e o Power BI.  Isso incluirá as IDs de atividade para cada solicitação, o carimbo de data/hora preciso para cada solicitação e qualquer informação de erro retornado ao cliente.  Este rastreamento também conterá os dados usados para preencher os elementos visuais mostrados na tela.
9. Você pode fornecer o arquivo HAR para dar suporte à análise.

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](http://community.powerbi.com/)

