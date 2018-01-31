---
title: Solucionar Problemas ao iniciar o Power BI Desktop
description: Solucionar Problemas ao iniciar o Power BI Desktop
services: powerbi
documentationcenter: 
author: davidiseminger
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
ms.date: 01/24/2018
ms.author: davidi
ms.openlocfilehash: 515832b9e6b737a942b08b491b78337d78398ee3
ms.sourcegitcommit: 7249ff35c73adc2d25f2e12bc0147afa1f31c232
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/25/2018
---
# <a name="resolve-issues-when-power-bi-desktop-will-not-launch"></a>Solucionar Problemas quando o Power BI Desktop não é iniciado
No **Power BI Desktop**, os usuários que instalaram e estão executando versões anteriores do **gateway de dados local do Power BI** podem ser impedidos de iniciar o Power BI Desktop, devido às restrições de políticas administrativas que o gateway local do Power BI estabeleceu nos pipes nomeados no computador local. 

## <a name="resolve-issues-with-the-on-premises-data-gateway-and-power-bi-desktop"></a>Resolver problemas com o gateway de dados local e o Power BI Desktop
Há três opções para resolver o problema associado ao gateway de dados local e habilitar o Power BI Desktop para inicialização:

### <a name="resolution-1-install-the-latest-version-of-power-bi-on-premises-data-gateway"></a>Resolução 1: instalar a versão mais recente do gateway de dados local do Power BI
A versão mais recente do gateway de dados local do Power BI não coloca restrições de pipe nomeado no computador local e permite que o Power BI Desktop seja iniciado corretamente. Se você precisar continuar usando o gateway de dados local do Power BI, esta é a resolução recomendada. Você pode baixar a versão mais recente do gateway de dados local do Power BI [neste local](https://go.microsoft.com/fwlink/?LinkId=698863). Observe que o link é um link de download direto para o executável da instalação.

### <a name="resolution-2-uninstall-or-stop-the-power-bi-on-premises-data-gateway-windows-service"></a>Resolução 2: desinstalar ou interromper o serviço Windows do gateway de dados local do Power BI
Se você não precisar mais do gateway de dados local do Power BI, é possível desinstalá-lo ou interromper o serviço Windows do gateway de dados local do Power BI, que remove a restrição de política e permite que o Power BI Desktop seja iniciado.

### <a name="resolution-3-run-power-bi-desktop-with-administrator-privilege"></a>Resolução 3: executar o Power BI Desktop com privilégios de administrador
Como alternativa, você pode iniciar com êxito Power BI Desktop como administrador, que também permite que o Power BI Desktop seja iniciado com êxito. Ainda é recomendável que você instale a versão mais recente do gateway de dados local do Power BI, conforme descrito anteriormente neste artigo.

## <a name="help-with-other-issues-when-launching-power-bi-desktop"></a>Ajuda com outros problemas ao iniciar o Power BI Desktop
Nos esforçamos para abordar o máximo possível de problemas que ocorrem com o **Power BI Desktop**. Examinamos regularmente os problemas que podem estar afetando muitos clientes, posteriormente incluindo-os em nossos artigos.

Se o problema ao iniciar o **Power BI Desktop** não estiver associado ao gateway de dados local ou se as resoluções anteriores não funcionarem, envie um incidente de suporte para o [suporte do Power BI](https://support.powerbi.com) (https://support.powerbi.com) que ajudará você a identificar e resolver o problema.

Para outros problemas que você pode encontrar no futuro com o **Power BI Desktop** (esperamos que não ocorra nenhum ou que sejam poucos), é útil ativar o rastreamento e coletar arquivos de log, para melhor isolar e identificar o problema. Para ativar o rastreamento, selecione **Arquivo > Opções e configurações > Opções** e, em seguida, selecione **Diagnóstico**, depois, marque **Habilitar o rastreamento** em *Opções de diagnóstico*. Estamos cientes de que o **Power BI Desktop** deve estar em execução para que essa opção seja configurada, o que é mais útil para futuros problemas associados à inicialização do **Power BI Desktop**.

