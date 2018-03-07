---
title: "Visualizações de cartão (também conhecido como blocos de números grandes)"
description: "Criar uma Visualização de cartão no Power BI"
services: powerbi
documentationcenter: 
author: mihart
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
ms.date: 12/24/2017
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: f38f3bb19be268cba4745c88aa98d09c080c773e
ms.sourcegitcommit: 88c8ba8dee4384ea7bff5cedcad67fce784d92b0
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/24/2018
---
# <a name="card-visualizations"></a>Visualizações de cartão
Às vezes, um único número é a coisa mais importante que você deseja acompanhar no seu painel ou relatório do Power BI, como as vendas totais, a fatia de mercado ano após ano ou o total de oportunidades. Esse tipo de visualização é chamado de *Cartão*. Assim como em quase todas as visualizações nativas do Power BI, os cartões podem ser criados usando o editor de relatório ou P e R.

![visualização de cartão](media/power-bi-visualization-card/pbi_opptuntiescard.png)

## <a name="create-a-card-using-the-report-editor"></a>Criar um cartão usando o editor de relatório
Essas instruções usam o exemplo de análise de varejo. Para acompanhar, [baixe o exemplo](sample-datasets.md) do serviço do Power BI (app.powerbi.com) ou do Power BI Desktop.   

1. Inicie uma [página de relatório em branco](power-bi-report-add-page.md) e selecione o campo **Armazenar** \> **Contagem de armazenamento aberto**. Caso esteja usando o serviço do Power BI, você precisará abrir o relatório no [Modo de Exibição de Edição](service-interact-with-a-report-in-editing-view.md).

    O Power BI cria um gráfico de colunas com um número.

   ![](media/power-bi-visualization-card/pbi_rptnumbertilechart.png)
2. No painel de Visualizações, selecione o ícone de cartão.

   ![](media/power-bi-visualization-card/pbi_changechartcard.png)
6. Focalize sobre o cartão e selecione o ícone de pino ![](media/power-bi-visualization-card/pbi_pintile.png) para adicionar a visualização ao painel.

   ![](media/power-bi-visualization-card/power-bi-pin-icon.png)
7. Fixe o bloco em um painel existente ou em um novo painel.

   * Painel existente: selecione o nome do painel no menu suspenso.
   * Novo painel: digite o nome do novo painel.
8. Selecione **Fixar**.

   Uma mensagem de Êxito (perto do canto superior direito) informa que a visualização foi adicionada, como um bloco, ao painel.

   ![](media/power-bi-visualization-card/power-bi-pin-success-message.png)
9. Selecione **Ir para o dashboard**. Nele, você pode [editar e mover](service-dashboard-edit-tile.md) a visualização fixada.


## <a name="create-a-card-from-the-qa-question-box"></a>Criar um cartão a partir de uma caixa de perguntas de P e R
A caixa pergunta de P e R é a maneira mais fácil de fazer um Cartão. A caixa de pergunta de P e R está disponível no serviço do Power BI (app.powerbi.com) de um painel ou relatório. As etapas abaixo descrevem como criar um Cartão a partir de um painel do serviço do Power BI. Se você deseja criar um cartão usando um P e R no Power BI Desktop, [siga estas instruções](https://powerbi.microsoft.com/en-us/blog/power-bi-desktop-december-feature-summary/#QandA) para a versão prévia do P e R para relatórios do Desktop.

1. Crie um [dashboard](service-dashboards.md) e [obtenha dados](service-get-data.md). Este exemplo usa a [amostra Análise de Oportunidade](sample-opportunity-analysis.md).

1. Na parte superior do painel, comece a digitar o que você deseja saber sobre os dados na caixa de pergunta. 

   ![](media/power-bi-visualization-card/power-bi-q-and-a-box.png)

>**DICA**: em um relatório de serviço do Power BI, no [Modo de Exibição de Edição](service-reading-view-and-editing-view.md), selecione **Fazer uma pergunta** na barra de menus superior. Em um relatório do Power BI Desktop, encontre algum espaço aberto e clique duas vezes para abrir uma caixa de pergunta.

3. Por exemplo, digite “número de oportunidades” na caixa de pergunta.

   ![](media/power-bi-visualization-card/power-bi-q-and-a.png)

   A caixa da pergunta o ajuda dando sugestões e reformulações e, por fim, exibe o número total.  
4. Selecione o ícone de pino ![](media/power-bi-visualization-card/pbi_pintile.png) no canto superior direito para adicionar o cartão ao painel.

   ![](media/power-bi-visualization-card/power-bi-pin.png)
5. Fixe o cartão, com um bloco, em um painel existente ou novo.

   * Painel existente: selecione o nome do painel no menu suspenso. Suas opções serão limitadas apenas aos dashboards no espaço de trabalho atual.
   * Novo dashboard: digite o nome do novo dashboard e ele será adicionado ao seu espaço de trabalho atual.
6. Selecione **Fixar**.

   Uma Mensagem de êxito (perto do canto superior direito) informa que a visualização foi adicionada, como um bloco, ao painel.  

   ![](media/power-bi-visualization-card/power-bi-success.png)
7. Selecione **Ir para o dashboard** para ver o novo bloco. Nele, é possível [renomear, redimensionar, adicionar um hiperlink, reposicionar o bloco e muito mais](service-dashboard-edit-tile.md) no dashboard.

   ![](media/power-bi-visualization-card/power-bi-pinned.png)

## <a name="considerations-and-troubleshooting"></a>Considerações e solução de problemas
- Se uma caixa de perguntas não for exibida, entre em contato com o administrador do sistema ou de locatário.    
- Se você estiver usando a área de trabalho e, ao clicar duas vezes em um espaço vazio de um relatório, o P e R não abrir, você precisará ativá-lo.  Selecione **Arquivo > Opções e Configurações > Opções > Recursos de versão prévia > P e R** e reinicie o Desktop.


## <a name="next-steps"></a>Próximas etapas
[Blocos de Dashboard no Power BI](service-dashboard-tiles.md)

[Dashboards no Power BI](service-dashboards.md)

[Power BI – conceitos básicos](service-basic-concepts.md)

Mais perguntas? [Experimente a Comunidade do Power BI](http://community.powerbi.com/)
