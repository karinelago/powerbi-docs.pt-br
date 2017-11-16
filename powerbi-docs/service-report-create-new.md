---
title: "Criar um novo relatório por meio de um conjunto de dados "
description: "Criar um novo relatório do Power BI com base em um conjunto de dados."
services: powerbi
documentationcenter: 
author: mihart
manager: kfile
backup: 
editor: 
tags: 
qualityfocus: monitoring
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 10/28/2017
ms.author: mihart
ms.openlocfilehash: f4afb1eaa1b3012fdbdb0eff35e9eff695cc32e4
ms.sourcegitcommit: 99cc3b9cb615c2957dde6ca908a51238f129cebb
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/13/2017
---
# <a name="create-a-new-power-bi-report-by-importing-a-dataset"></a>Criar um novo relatório do Power BI importando um conjunto de dados
Você já leu [Relatórios no Power BI](service-reports.md) e agora deseja criar o seu próprio relatório. Há muitas maneiras diferentes para criar um relatório e, neste artigo, vamos começar criando um relatório muito básico com base em um conjunto de dados do Excel. Depois de compreender os fundamentos da criação de um relatório, as **Próximas etapas** no final vão direcioná-lo para tópicos mais avançados sobre relatórios.  

> **DICA**: para criar um relatório copiando um relatório existente, consulte [Copiar um relatório](power-bi-report-copy.md)
> 
> 

## <a name="import-the-dataset"></a>Importar o conjunto de dados
Esse método para a criação de um relatório começa com um conjunto de dados e uma tela de relatório em branco. Para acompanhar, [baixe o conjunto de dados de exemplo do Excel, Análise de Varejo](http://go.microsoft.com/fwlink/?LinkId=529778) e salve-o no OneDrive for Business (de preferência) ou localmente.

1. Criaremos o relatório em um espaço de trabalho do serviço do Power BI, portanto, selecione um espaço de trabalho existente ou crie um novo.
   
   ![](media/service-report-create-new/power-bi-workspaces2.png)
2. Na parte inferior da barra de navegação à esquerda, selecione **Obter dados**.
   
   ![](media/service-report-create-new/power-bi-get-data3.png)
3. Selecione **Arquivos** e navegue até o local em que você salvou o exemplo Análise de Varejo.
   
    ![](media/service-report-create-new/power-bi-select-files.png)
4. Para este exercício, selecione **Importar**.
   
   ![](media/service-report-create-new/power-bi-import.png)
5. Depois que o conjunto de dados for importado, selecione **Exibir conjunto de dados**.
   
   ![](media/service-report-create-new/power-bi-view-dataset.png)
6. Na verdade, exibir um conjunto de dados abre o editor de relatório.  Você verá uma tela em branco e as ferramentas de edição do relatório.
   
   ![](media/service-report-create-new/power-bi-blank-report.png)

> **DICA**: se você não estiver familiarizado com a tela de edição de relatório ou precisar de um lembrete, [Faça um tour pelo editor de relatório ](service-the-report-editor-take-a-tour.md) antes de continuar.
> 
> 

## <a name="add-a-radial-gauge-to-the-report"></a>Adicionar um Medidor Radial ao relatório
Agora que nosso conjunto de dados foi importado, vamos começar respondendo algumas perguntas.  Nossa CMO (Diretora de Marketing) quer saber se estamos próximos de alcançar as metas de vendas deste ano. Um Medidor é uma [boa opção de visualização](power-bi-report-visualizations.md) para exibir esse tipo de informação.

1. No painel Campos, selecione **Vendas** > **Vendas Deste Ano** > **Valor**.
   
    ![](media/service-report-create-new/power-bi-report-step1.png)
2. Converta o visual em um Medidor selecionando o modelo de Medidor ![](media/service-report-create-new/powerbi-gauge-icon.png) no painel **Visualizações**.
   
    ![](media/service-report-create-new/power-bi-report-step2.png)
3. Arraste **Vendas** > **Vendas Deste Ano** > **Meta** para a seção **Valor de Destino**. Parece que estamos muito perto de alcançar a nossa meta.
   
    ![](media/service-report-create-new/power-bi-report-step3.png)
4. Agora seria um bom momento para [salvar seu relatório](service-report-save.md).
   
   ![](media/service-report-create-new/powerbi-save.png)

## <a name="add-an-area-chart-and-slicer-to-the-report"></a>Adicionar um gráfico de área e uma segmentação de dados ao relatório
Nossa CMO tem algumas perguntas adicionais para respondermos. Ela gostaria de ver a comparação das vendas deste ano com as vendas do ano passado. E também desejaria ver os resultados por distrito.

1. Primeiro, vamos criar espaço em nossa tela. Selecione o Medidor e mova-o para o canto superior direito. Em seguida, pegue e arraste um dos cantos e torne-o menor.
2. Desmarque o medidor. No painel Campos, selecione **Vendas** > **Vendas Deste Ano** > **Valor** e selecione **Vendas** > **Vendas do Ano Passado**.
   
    ![](media/service-report-create-new/power-bi-report-step4.png)
3. Converta o visual em um Gráfico de área, selecionando o modelo de Gráfico de área ![](media/service-report-create-new/power-bi-areachart-icon.png) no painel **Visualizações**.
4. Selecione **Tempo** > **Período** para adicionar ao **Eixo** também.
   
    ![](media/service-report-create-new/power-bi-report-step5.png)
5. Para classificar a visualização, selecione as reticências e escolha **Classificar por Período**.
6. Agora vamos adicionar a segmentação de dados. Selecione uma área vazia na tela e escolha o modelo de segmentação de dados ![](media/service-report-create-new/power-bi-slicer-icon.png). Isso adiciona uma segmentação de dados vazia à nossa tela.
   
    ![](media/service-report-create-new/power-bi-report-step6.png)    
7. No painel Campos, selecione **Distrito** > **Distrito**. Mova e redimensione a segmentação de dados.
   
    ![](media/service-report-create-new/power-bi-report-step7.png)  
8. Use a segmentação de dados para procurar por padrões e insights por Distrito.
   
   ![](media/service-report-create-new/power-bi-slicer-video2.gif)  
9. Opcionalmente, você pode continuar adicionando visualizações.

## <a name="next-steps"></a>Próximas etapas
* [Criar uma cópia de um relatório](power-bi-report-copy.md)
* [Salvar o relatório](service-report-save.md)    
* [Adicionar uma nova página ao relatório](power-bi-report-add-page.md)  
* Saiba como [fixar visualizações em um dashboard](service-dashboard-pin-tile-from-report.md)    
* Mais perguntas? [Experimente a Comunidade do Power BI](http://community.powerbi.com/)

