---
title: Criar uma segmentação responsiva que você possa redimensionar no Power BI
description: Saiba como criar uma segmentação responsiva que você possa redimensionar para se ajustar ao seu relatório
services: powerbi
documentationcenter: ''
author: maggiesMSFT
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
ms.date: 12/08/2017
ms.author: maggies
LocalizationGroup: Create reports
ms.openlocfilehash: f70ebae419c83e359f950d7b1180809d3e25b59e
ms.sourcegitcommit: 493f160d04ed411ff4741c599adc63ba1f65230f
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/07/2018
---
# <a name="create-a-responsive-slicer-you-can-resize-in-power-bi-preview"></a>Criar uma segmentação responsiva que você possa redimensionar no Power BI (versão prévia)

As segmentações responsivas são redimensionadas para se ajustar a qualquer espaço no seu relatório. Com segmentações responsivas, redimensione-as para diferentes tamanhos e formas, de horizontal para quadrado e vertical, e os valores na segmentação são reorganizadas como você faria. No Power BI Desktop e no serviço do Power BI, você pode fazer segmentações horizontais e segmentações de data/intervalo responsivas. Segmentações de data/intervalo também têm áreas de toque aprimoradas para facilitar a alteração com a ponta do dedo. Crie segmentações responsivas pequenas ou grandes; elas também são redimensionadas automaticamente para se ajustar bem a relatórios no serviço do Power BI e também em aplicativos móveis do Power BI. 

![Segmentações responsivas podem ter uma variedade de formas](media/power-bi-slicer-filter-responsive/responsive-slicer-gif.gif)

## <a name="create-a-slicer"></a>Criar uma segmentação

A primeira etapa para criar uma segmentação dinâmica é criar uma segmentação básica. 

1. Selecione o ícone **Segmentação**, ![ícone Segmentação](media/power-bi-slicer-filter-responsive/power-bi-slicer-icon.png) no painel **Visualizações**.
2. Arraste o campo que você deseja filtrar para **Campo**.

    ![Adicionar um campo à segmentação](media/power-bi-slicer-filter-responsive/power-bi-slicer-field.png)

## <a name="convert-to-a-horizontal-slicer"></a>Converter em uma segmentação horizontal

1. Com a segmentação selecionada, no painel **Visualizações**, selecione a guia **Formato**.
2. Expanda a seção **Geral**. Para **Orientação**, selecione **Horizontal**.

    ![Configurar a segmentação para horizontal](media/power-bi-slicer-filter-responsive/power-bi-slicer-horizontal.png) 

1.  É provável que você queira deixá-la mais larga, para mostrar mais valores.

     ![Deixar a segmentação mais larga](media/power-bi-slicer-filter-responsive/power-bi-slicer-wide-horizontal.png)

## <a name="make-it-responsive-and-experiment-with-it"></a>Torná-la responsiva e experimentar com ela

Esta etapa é fácil. 

1. À direita, em **Orientação** na seção **Geral** da guia **Formato**, deslize **Responsiva (versão prévia)** para **Ligado**.  

    ![A segmentação já é responsiva](media/power-bi-slicer-filter-responsive/power-bi-slicer-wide-responsive.png)

1. Agora você pode brincar com ela. Arraste os cantos para deixá-la baixa, alta, larga e estreita. Se você a fizer pequena o suficiente, ela se tornará apenas um ícone de filtro.

    ![Segmentação responsiva tão pequena que é um ícone de filtro](media/power-bi-slicer-filter-responsive/power-bi-slicer-small-filter-icon.png)

## <a name="add-it-to-a-phone-report-layout"></a>Adicioná-la a um layout de relatório do telefone

No Power BI Desktop, crie um layout de telefone para cada página de um relatório. Se uma página tiver um layout de telefone, ela será exibida em um celular no modo retrato. Caso contrário, você precisará exibi-la no modo paisagem. 

1. No menu **Exibir**, selecione **Layout do Telefone**.

     ![Ícone de layout para telefone, menu Exibir](media/power-bi-slicer-filter-responsive/power-bi-phone-layout-menu.png)
    
1. Arraste todos os visuais que você deseja no relatório do telefone para a grade. Quando você arrasta a segmentação responsiva, deixe-a do tamanho desejado – nesse caso, um ícone de filtro.

    ![Adicionar a segmentação ao layout de relatório do telefone](media/power-bi-slicer-filter-responsive/power-bi-slicer-phone-layout.png)

Leia mais sobre a criação de [relatórios otimizados para aplicativos móveis do Power BI](desktop-create-phone-report.md).

## <a name="make-a-time-or-range-slicer-responsive"></a>Tornar uma segmentação de tempo ou intervalo responsiva

Siga as mesmas etapas para fazer com que uma segmentação de tempo ou de intervalo se torne responsiva. Depois de definir **Responsiva** como **Ligado**, observe alguns aspectos:

- Visuais otimizam a ordem das caixas de entrada dependendo do tamanho permitido na tela. 
- A exibição do elemento de dados é otimizada para tornar a segmentação o mais útil possível, com base no tamanho permitido na tela. 
- Novo guidões arredondados nos controles deslizantes otimizam interações de toque. 
- Quando um visual fica muito pequeno para ser útil, ele se torna um ícone que representa o tipo de visual em seu lugar. Para interagir com ele, toque duas vezes para abri-lo no modo de foco. Isso economiza espaço valioso na página de relatório sem perder a funcionalidade.

## <a name="next-steps"></a>Próximas etapas

- [Segmentações no serviço do Power BI](power-bi-visualization-slicers.md)
- Mais perguntas? [Experimente perguntar à Comunidade do Power BI](http://community.powerbi.com/)