---
title: Solucionar problemas de atualização
description: Solucionar problemas de atualização
services: powerbi
documentationcenter: ''
author: davidiseminger
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
ms.date: 01/24/2018
ms.author: davidi
LocalizationGroup: Data refresh
ms.openlocfilehash: d94e25b78edef2aefaa5e63c788e5f11dc948791
ms.sourcegitcommit: 1fe3ababba34c4e7aea08adb347ec5430e0b38e4
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/22/2018
---
# <a name="troubleshooting-refresh-scenarios"></a>Solucionar problemas de atualização
Aqui você pode encontrar informações sobre cenários diferentes que você pode encontrar ao atualizar dados no serviço Power BI.

> [!NOTE]
> Se você encontrar um cenário que não esteja listado abaixo e que esteja causando problemas, solicite ajuda no [site da comunidade](http://community.powerbi.com/) ou crie um [tíquete de suporte](https://powerbi.microsoft.com/support/).
> 
> 

## <a name="refresh-using-web-connector-doesnt-work-properly"></a>A atualização usando o conector da Web não funciona corretamente
Se você tiver um script de conector da Web usando a função [**Web.Page**](https://msdn.microsoft.com/library/mt260924.aspx) e tiver atualizado o seu conjunto de dados ou relatório após 18 de novembro de 2016, será preciso usar um gateway para que a atualização funcione corretamente.

## <a name="unsupported-data-source-for-refresh"></a>Fonte de dados sem suporte para atualização
Ao configurar um conjunto de dados, é possível receber um erro indicando que o conjunto de dados usa uma fonte de dados sem suporte para atualização. Para obter detalhes, consulte [Troubleshooting unsupported data source for refresh](service-admin-troubleshoot-unsupported-data-source-for-refresh.md) (Solucionando problemas de fonte de dados sem suporte para atualização)

## <a name="dashboard-doesnt-reflect-changes-after-refresh"></a>O painel de controle não reflete as alterações após a atualização
Aguarde cerca de 10 a 15 minutos para a atualização ser refletida nos blocos do painel.  Se ainda não aparecer, novamente fixe a visualização para o painel.

## <a name="gatewaynotreachable-when-setting-credentials"></a>GatewayNotReachable ao definir credenciais
Você pode encontrar GatewayNotReachable durante a tentativa de definir credenciais para uma fonte de dados. Isso pode ser o resultado de um gateway desatualizado.  Instale o gateway mais recente e tente novamente.

## <a name="processing-error-the-following-system-error-occurred-type-mismatch"></a>Erro de processamento: o seguinte erro de sistema ocorreu: tipos incompatíveis
Isso pode ser um problema com o script M em seu arquivo Power BI Desktop ou pasta de trabalho em Excel.  Também pode ser devido a uma versão do Power BI Desktop.

## <a name="tile-refresh-errors"></a>Erros de atualização de bloco
Para obter uma lista de erros que podem ser encontrados em blocos de dashboard, bem como explicações, veja [Solucionar problemas de erros de bloco](refresh-troubleshooting-tile-errors.md).

## <a name="refresh-fails-when-updating-data-from-sources-that-use-aad-oauth"></a>Falha na atualização ao atualizar dados de fontes que usam o OAuth do AAD
O token OAuth do AAD (**Azure Active Directory**), usado por diversas fontes de dados, expira em cerca de uma hora. Você pode se deparar com situações em que o carregamento de dados demora mais do que a expiração do token (mais de uma hora), já que o serviço do Power BI espera por até duas horas ao carregar dados. Nessa situação, o processo de carregamento de dados pode falhar com um erro de credenciais.

Fontes de dados que usam o OAuth do AAD incluem **Microsoft Dynamics CRM Online**, **SPO** (SharePoint Online) e outras. Se você estiver se conectando a essas fontes de dados e obtiver uma falha de credenciais quando o carregamento de dados demorar mais de uma hora, esse poderá ser o motivo.

A Microsoft está investigando uma solução que permita que o processo de carregamento de dados atualize o token e continue. No entanto, se sua instância do Dynamics CRM Online ou do SharePoint Online (ou outra fonte de dados de OAuth do AAD) é tão grande que possa alcançar o limite de carregamento de dados de duas horas, você também poderá enfrentar um problema de tempo de limite de carregamento de dados do serviço do Power BI.

Observe também que, para a atualização funcionar corretamente, ao conectar-se a uma fonte de dados do **SharePoint Online** usando o AAD OAuth, você deverá usar a mesma conta usada para entrar no **serviço do Power BI**.

## <a name="uncompressed-data-limits-for-refresh"></a>Limites de dados descompactados para atualização
O tamanho máximo de conjuntos de dados importados para o **serviço do Power BI** é de 1 GB. Esses conjuntos de dados são altamente compactados para garantir o alto desempenho. Além disso, na capacidade compartilhada, o serviço impõe um limite de 10 GB para a quantidade de dados descompactados que são processados durante a atualização. Esse limite leva em consideração a compactação e, portanto, é muito maior que 1 GB. Conjuntos de dados no Power BI Premium não estão sujeitos a esse limite. Se a atualização no serviço do Power BI falhar por esse motivo, reduza a quantidade de dados que estão sendo importados para o Power BI e tente novamente.

## <a name="scheduled-refresh-timeout"></a>Tempo limite de atualização agendada
A atualização agendada para os conjuntos de dados importados atinge o tempo limite após duas horas. Esse tempo limite é aumentado para cinco horas em conjuntos de dados em espaços de trabalho **Premium**. Se estiver recebendo esse limite, considere a possibilidade de reduzir o tamanho ou a complexidade do conjunto de dados ou dividir o conjunto de dados em partes menores.

## <a name="next-steps"></a>Próximas etapas
[Atualização de dados](refresh-data.md)  
[Solução de problemas do gateway de dados local](service-gateway-onprem-tshoot.md)  
[Solução de problemas do Gateway do Power BI – Pessoal](service-admin-troubleshooting-power-bi-personal-gateway.md)  

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](http://community.powerbi.com/)

