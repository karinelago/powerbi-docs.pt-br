---
title: Abrir um relatório no modo de exibição de Leitura ou no modo de exibição de Edição no serviço do Power BI
description: Abrir um relatório do Power BI na Exibição de Leitura ou no Modo de Exibição de Edição
services: powerbi
documentationcenter: ''
author: mihart
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
ms.date: 03/01/2018
ms.author: mihart
ms.openlocfilehash: 17921d1fe28a1b4c0640748123efe4b70982b18d
ms.sourcegitcommit: ae4d771b883b654358a6a94dd784ea9bdf3d3aa3
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/28/2018
---
# <a name="open-a-report-in-power-bi-service-apppowerbicom"></a>Abrir um relatório no serviço do Power BI (app.powerbi.com)
Os relatórios estão disponíveis no serviço do Power BI, Power BI Desktop, Power BI Mobile e até mesmo no Power BI Embedded. Este artigo se aplica à abertura de relatórios no ***serviço do Power BI***.

No serviço do Power BI, há dois modos para exibir e interagir com relatórios: [modo de exibição de Leitura e modo de exibição de Edição](service-reading-view-and-editing-view.md). O modo de exibição de Leitura está disponível para todos os usuários e foi projetado especialmente para *consumidores* de relatórios, enquanto o modo de exibição de Edição só está disponível para *criadores* e proprietários de relatórios. 

## <a name="open-a-report-from-a-workspace-via-the-reports-content-view-list"></a>Abrir um relatório por meio de um espaço de trabalho (pela lista de exibição de conteúdo **Relatórios**)

1. Inicie em um espaço de trabalho e selecione a guia **Relatórios** para exibir todos os relatórios nesse espaço de trabalho.  
   
   ![Guia Relatórios de um espaço de trabalho](media/service-report-open/power-bi-open-report.png)
2. Selecione o nome do relatório para abri-lo no modo de exibição de Leitura.  
   
    ![relatório em modo de exibição de Leitura](media/service-report-open/power-bi-reading-view.png)
3. Você pode [fazer muito mais no Modo de Exibição de Leitura](service-reading-view-and-editing-view.md).  Esse relatório de exemplo tem várias páginas. Portanto, comece a explorar selecionando cada guia na parte inferior da tela de relatório. 

## <a name="open-a-report-from-a-dashboard"></a>Abrir um relatório por meio de um dashboard
Há muitas outras maneiras de abrir um relatório. Por exemplo, você pode iniciar em um dashboard e selecionar um bloco que foi criado com base em um relatório.  A seleção do bloco abre o relatório no Modo de exibição de leitura. Para acompanhar, [abra o dashboard de exemplo de Vendas e Marketing](sample-datasets.md).

1. Abra um dashboard e selecione um bloco.

   Se você selecionar um bloco que foi [criado com a P e R](service-dashboard-pin-tile-from-q-and-a.md), a tela da P e R será aberta. Se você selecionar um bloco que foi [criado usando o widget **Adicionar bloco** do dashboard](service-dashboard-add-widget.md), você abrirá o assistente para editar esse widget.  

2.  Neste exemplo, selecionamos o bloco do gráfico de colunas “Total de Unidades Acumuladas no Ano...”.

    ![dashboard com bloco selecionado](media/service-report-open/power-bi-dashboard.png)

3.  O relatório associado é aberto no modo de exibição de Leitura. Observe que estamos na página “Categoria de Acumulado no Ano”. Essa é a página de relatório que contém o gráfico de colunas que selecionamos por meio do dashboard.

    ![abertura de relatório no modo de exibição de Leitura](media/service-report-open/power-bi-report.png)

4. Permaneça no modo de exibição de Leitura ou selecione **Editar relatório** para abrir o relatório no modo de exibição de Edição. Lembre-se de que somente aqueles com permissões de edição para esse relatório podem abri-lo no modo de exibição de Edição.

    ![Editor de relatório mostrando o ícone Editar relatório](media/service-report-open/power-bi-edit-report.png)

## <a name="create-a-brand-new-report-from-a-dataset"></a>Criar um novo relatório com base em um conjunto de dados
Outra maneira de abrir um relatório é por meio de um conjunto de dados. Quando você começar com um conjunto de dados, a tela de relatório estará em branco; portanto, esse método é recomendado para *criadores* de relatório interessados em criar um novo relatório com base em um conjunto de dados que possuem. Como o exemplo acima, para acompanhar, baixe o [aplicativo de exemplo de Vendas e Marketing](sample-datasets.md).

1. Inicie no espaço de trabalho que contém o conjunto de dados que você deseja usar como base para um relatório.

   ![painel de navegação esquerdo mostrando Espaços de trabalho de aplicativo](media/service-report-open/power-bi-workspace.png)

2. Selecione a guia **Conjuntos de Dados** para exibir a lista de todos os conjuntos de dados no espaço de trabalho. Isso é chamado a lista de exibição de conteúdo **Conjuntos de Dados**.
   
   ![lista de conjuntos de dados](media/service-report-open/power-bi-dataset.png)

1. Localize o conjunto de dados e selecione o ícone **Criar relatório** para abrir o conjunto de dados no modo de exibição de Edição. Caso não tenha permissões de edição para um conjunto de dados, você não poderá abri-lo. 
   
    ![conjunto de dados com ícone Criar relatório](media/service-report-open/power-bi-create-report.png)

3. O conjunto de dados é aberto no editor de relatório. Você verá os campos de dados exibidos à direita, à sua espera, para que você comece a explorar e criar visualizações. 

   ![tela de relatório](media/service-report-open/power-bi-blank-canvas.png)

##  <a name="still-more-ways-to-open-a-report"></a>Outras maneiras de abrir um relatório
Conforme você ficar mais familiarizado com a navegação no serviço do Power BI, descobrirá os fluxos de trabalho que funcionam melhor para você. Algumas outras maneiras de acessar relatórios:
- No painel de navegação esquerdo usando **Favoritos**, **Recentes**, **Aplicativos** e **Compartilhado comigo**. 
- Usando [Exibição relacionada](service-related-content.md)
- Em um email quando alguém [compartilha com você](service-share-reports.md) ou [define um alerta](service-set-data-alerts.md).    
- No [Centro de notificações](service-notification-center.md)    
- e muito mais

## <a name="next-steps"></a>Próximas etapas
Leia mais sobre [relatórios no Power BI](service-reports.md)

Mais perguntas? [Experimente a Comunidade do Power BI](http://community.powerbi.com/)  

