---
title: "Início rápido: instalar o Servidor de Relatório do Power BI"
description: "Instalar o próprio Servidor de Relatórios do Power BI é muito rápido. Do download a instalação e configuração, você deve entrar em funcionamento em poucos minutos."
services: powerbi
documentationcenter: 
author: guyinacube
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
ms.date: 06/28/2017
ms.author: maghan
ms.openlocfilehash: 934b4d3f2da44a161cd76d14c9f042aaf697f26d
ms.sourcegitcommit: eec6b47970bf69ed30638d1a20051f961ba792f2
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/06/2018
---
# <a name="quickstart-install-power-bi-report-server"></a>Início rápido: instalar o Servidor de Relatório do Power BI
Instalar o próprio Servidor de Relatório do Power BI é muito rápido. Do download a instalação e configuração, você deve entrar em funcionamento em poucos minutos.

Esta é uma visão geral de como instalar um servidor de relatório, se você apenas desejar entrar em funcionamento com um novo servidor. Para obter mais informações detalhadas sobre como instalar o servidor de relatório, consulte [Install Power BI Report Server (Instalar o Servidor de Relatório do Power BI)](install-report-server.md).

 **Baixe** ![baixe](media/quickstart-install-report-server/download.png "baixe")

Para baixar o Servidor de Relatório do Power BI, acesse [On-premises reporting with Power BI Report Server (Relatórios locais com o Servidor de Relatório do Power BI)](https://powerbi.microsoft.com/report-server/). Para o Power BI Desktop otimizado para o Servidor de Relatório do Power BI, acesse o [Centro de Download da Microsoft](https://go.microsoft.com/fwlink/?linkid=837581).

![dica](media/quickstart-install-report-server/fyi-tip.png "dica") Para ver as notas de versão atuais, consulte [Power BI Report Server – Release notes (Servidor de Relatório do Power BI – Notas de versão)](release-notes.md).

<iframe width="640" height="360" src="https://www.youtube.com/embed/zacaEb9A4F0?showinfo=0" frameborder="0" allowfullscreen></iframe>

## <a name="before-you-begin"></a>Antes de começar
Antes de instalar o Servidor de Relatório do Power BI, é recomendável que você examine os [Requisitos de hardware e de software para a instalação do Servidor de Relatório do Power BI](system-requirements.md).

## <a name="step-1-download"></a>Etapa 1: download
Baixe os arquivos de instalação, para o Servidor de Relatório do Power BI, localmente. Para baixar o Servidor de Relatório do Power BI, acesse o [Centro de Download da Microsoft](https://go.microsoft.com/fwlink/?linkid=839351).

![Baixar o Servidor de Relatório do Power BI](media/quickstart-install-report-server/download-pbireportserver.png)

## <a name="step-2-run-installer"></a>Etapa 2: executar o instalador
Execute o arquivo PowerBIReportServer.exe que você baixou e percorra as telas de instalação. Você terá a oportunidade de selecionar o caminho de instalação, bem como selecionar a edição que deseja instalar. É possível escolher entre uma avaliação expira em 180 dias, uma edição de desenvolvedor ou fornecer uma chave do produto (Product Key).

![Instalar o Servidor de Relatório do Power BI](media/quickstart-install-report-server/pbireportserver-install.png)

## <a name="step-3-configure-the-server"></a>Etapa 3: configurar o servidor
Depois de concluir a instalação, você executará o gerenciador de configurações para concluir a configuração do servidor. Será necessário criar um banco de dados de catálogo ReportServer, bem como confirmar o portal da Web e as URLs de serviço Web.

![Configurar o Servidor de Relatório do Power BI](media/quickstart-install-report-server/pbireportserver-configure.png)

## <a name="step-4-browse-to-web-portal"></a>Etapa 4: navegar até o portal da Web
Agora que tudo foi configurado, você poderá abrir um navegador para o portal da web do seu servidor. Por padrão, será `http://localhost/reports`. Você também poderá procurar usando o nome do computador em vez de usar o localhost por padrão, supondo que nenhum tipo de firewall esteja te bloqueando.

![Portal da Web do Servidor de Relatório do Power BI](media/quickstart-install-report-server/web-portal.png)

## <a name="next-steps"></a>Próximas etapas
[Manual do administrador](admin-handbook-overview.md)  
[Como encontrar a chave do produto (Product Key) do servidor de relatório](find-product-key.md)  
[Instalar o Servidor de Relatório do Power BI](install-report-server.md)  
[Instalar o Power BI Desktop otimizado para o Servidor de Relatório do Power BI](install-powerbi-desktop.md)  
[Suporte do navegador para o Servidor de Relatório do Power BI](browser-support.md)

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)

