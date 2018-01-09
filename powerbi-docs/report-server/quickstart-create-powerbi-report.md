---
title: "Início rápido: criar um relatório do Power BI para o Servidor de Relatório do Power BI"
description: "Saiba como criar um relatório do Power BI para o Servidor de Relatório do Power BI em algumas etapas simples."
services: powerbi
documentationcenter: 
author: maggiesMSFT
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
ms.date: 12/15/2017
ms.author: maggies
ms.openlocfilehash: c8b07e8c2370f7a1694b18a87b2704a7f164f79f
ms.sourcegitcommit: ea247cb3cfc1cac076d4b076c1ad8e2fc37e15a1
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/19/2017
---
# <a name="quickstart-create-a-power-bi-report-for-power-bi-report-server"></a>Início rápido: criar um relatório do Power BI para o Servidor de Relatório do Power BI
É possível armazenar e gerenciar relatórios do Power BI localmente no portal da Web do Servidor de Relatórios do Power BI, do mesmo modo que você pode armazenar relatórios do Power BI na nuvem no serviço do Power BI (https://powerbi.com). Você cria e edita relatórios no Power BI Desktop e, em seguida, publica-os no portal da Web. Em seguida, os leitores de relatório em sua organização poderão exibi-los em um navegador ou em um aplicativo móvel do Power BI em um dispositivo móvel.

![Relatório do Power BI no Portal da Web](media/quickstart-create-powerbi-report/report-server-powerbi-report.png)

Aqui estão quatro etapas rápidas para começar.

## <a name="step-1-install-power-bi-desktop-optimized-for-power-bi-report-server"></a>Etapa 1: Instalar o Power BI Desktop otimizado para o Servidor de Relatórios do Power BI

Se você já tiver criado relatórios do Power BI no Power BI Desktop, então você está quase pronto para criar relatórios do Power BI para o Servidor de Relatórios do Power BI. É recomendável instalar a versão do Power BI Desktop otimizado para o Servidor de Relatório do Power BI para saber que o servidor e o aplicativo estão sempre em sincronia. É possível ter ambas as versões do Power BI Desktop no mesmo computador.

1. No portal da Web do servidor de relatórios, selecione a seta **Baixar** > **Power BI Desktop**.

    ![Baixe o Power BI Desktop no portal da Web](media/quickstart-create-powerbi-report/report-server-download-web-portal.png)

    Ou você pode ir diretamente para o [Microsoft Power BI Desktop](https://go.microsoft.com/fwlink/?linkid=861076) (Otimizado para o Servidor de Relatórios do Power BI - Outubro de 2017) no Centro de Download da Microsoft.

2. Na página do Centro de Download, selecione **Baixar**.

3. Dependendo do seu computador, selecione:

    - **PBIDesktopRS.msi** (a versão de 32 bits) ou

    - **PBIDesktopRS_x64.msi** (a versão de 64 bits).

4. Depois de baixar o instalador, execute o Assistente de Instalação do Power BI Desktop (Outubro de 2017).

2. No final da instalação, marque **Iniciar o Power BI Desktop agora**.
   
    Ele é iniciado automaticamente e você está pronto para começar. Você pode saber que tem a versão correta, porque "Power BI Desktop (Outubro de 2017)" consta na barra de título.

    ![Power BI Desktop versão de outubro de 2017](media/quickstart-create-powerbi-report/report-server-desktop-october-2017-version.png)

3. Se você não estiver familiarizado com o Power BI Desktop, considere assistir aos vídeos na tela de boas-vindas.
   
    ![Tela inicial do Power BI Desktop](media/quickstart-create-powerbi-report/report-server-powerbi-desktop-start.png)

## <a name="step-2-select-a-data-source"></a>Etapa 2: selecionar uma fonte de dados
Você pode conectar-se a uma variedade de fontes de dados. Leia mais sobre como [se conectar a fontes de dados](connect-data-sources.md).

1. Na tela de boas-vindas, selecione **Obter dados**.
   
    Na guia **Início**, selecione **Obter dados**.
2. Selecione a fonte de dados, neste exemplo, **Analysis Services**.
   
    ![Selecionar fonte de dados](media/quickstart-create-powerbi-report/report-server-get-data-ssas.png)
3. Preencha **Servidor** e, opcionalmente, **Banco de dados**. Certifique-se de que **Conectar em tempo real** está selecionado > **OK**.
   
    ![Nome do servidor](media/quickstart-create-powerbi-report/report-server-ssas-server-name.png)
4. Escolha o servidor de relatório em que você salvará seus relatórios.
   
    ![Seleção de servidor de relatório](media/quickstart-create-powerbi-report/report-server-select-server.png)

## <a name="step-3-design-your-report"></a>Etapa 3: criar seu relatório
Veja a parte divertida: você precisa criar visuais que ilustrem seus dados.

Por exemplo, é possível criar um gráfico de funil de clientes e agrupar valores por renda anual.

![Projetar um relatório](media/quickstart-create-powerbi-report/report-server-create-funnel.png)

1. Em **Visualizações**, selecione **Gráfico de funil**.
2. Arraste o campo a ser contado para o vão **Valores**. Se não for um campo numérico, o Power BI Desktop o torna automaticamente uma *Contagem* do valor.
3. Arraste o campo ao grupo para o vão **Grupo**.

Ler mais sobre como [projetar um relatório do Power BI](../desktop-report-view.md).

## <a name="step-4-save-your-report-to-the-report-server"></a>Etapa 4: salvar seu relatório no servidor de relatório
Quando seu relatório estiver pronto, salve-o no Servidor de Relatórios do Power BI que você escolheu na etapa 2.

1. No menu **Arquivo**, selecione **Salvar como** > **Servidor de Relatório do Power BI**.
   
    ![Salvar no servidor de relatório](media/quickstart-create-powerbi-report/report-server-save-as-powerbi-report-server.png)
2. Agora é possível exibi-lo no portal da Web.
   
    ![Exibir o relatório no portal da Web](media/quickstart-create-powerbi-report/report-server-powerbi-report.png)

## <a name="considerations-and-limitations"></a>Considerações e limitações
Os relatórios no Servidor de Relatório do Power BI e no serviço do Power BI (http://powerbi.com) agem praticamente da mesma maneira, mas alguns recursos são diferentes.

### <a name="in-a-browser"></a>Em um navegador
Os relatórios do Servidor de Relatório do Power BI dão suporte a todas as visualizações, inclusive:

* Elementos visuais personalizados

Os relatórios do Servidor de Relatório do Power BI não dão suporte a:

* Visuais do R
* Mapas ArcGIS
* Trilhas
* Recursos de visualização do Power BI Desktop

### <a name="in-the-power-bi-mobile-apps"></a>Nos aplicativos móveis do Power BI
Os relatórios do Servidor de Relatório do Power BI dão suporte a toda a funcionalidade básica nos [aplicativos móveis do Power BI](../mobile-apps-for-mobile-devices.md), incluindo:

* [Layout de relatório de telefone](../desktop-create-phone-report.md): é possível otimizar um relatório para os aplicativos móveis do Power BI. Em seu telefone celular, os relatórios otimizados têm um ícone especial chamado ![Ícone de layout de relatório para telefone](media/quickstart-create-powerbi-report/power-bi-rs-mobile-optimized-icon.png) e um layout.
  
    ![Relatórios otimizado para telefones](media/quickstart-create-powerbi-report/power-bi-rs-mobile-optimized-report.png)

Os relatórios do Servidor de Relatório do Power BI não dão suporte a estes recursos nos aplicativos móveis do Power BI:

* Visuais do R
* Mapas ArcGIS
* Elementos visuais personalizados
* Trilhas
* Filtragem geográfica ou códigos de barra

## <a name="next-steps"></a>Próximas etapas
### <a name="power-bi-desktop"></a>Power BI Desktop
Há muitos recursos excelentes para criar relatórios no Power BI Desktop. Esses links são um bom ponto de partida.

* [Introdução ao Power BI Desktop](../desktop-getting-started.md)
* Aprendizado guiado: [Introdução ao Power BI Desktop](../guided-learning/gettingdata.yml#step-2)

### <a name="power-bi-report-server"></a>Servidor de Relatório do Power BI
* [Instalar o Power BI Desktop otimizado para o Servidor de Relatório do Power BI](install-powerbi-desktop.md)  
* [Manual do usuário do Servidor de Relatório do Power BI](user-handbook-overview.md)  

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)