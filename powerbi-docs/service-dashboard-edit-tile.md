---
title: Editar um bloco do dashboard
description: Este tutorial usa seu de criação de um bloco e anexando a um dashboard, para aprender como editar esse bloco do dashboard – redimensionar, mover, renomear, fixar, excluir, adicionar hiperlink.
services: powerbi
documentationcenter: ''
author: mihart
manager: kfile
backup: ''
editor: ''
tags: ''
featuredvideoid: lJKgWnvl6bQ
qualityfocus: no
qualitydate: ''
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 03/02/2018
ms.author: mihart
LocalizationGroup: Dashboards
ms.openlocfilehash: ca83151f2dbf0f69926ad1920c3323a0070e5e06
ms.sourcegitcommit: 493f160d04ed411ff4741c599adc63ba1f65230f
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/07/2018
---
# <a name="edit-or-remove-a-dashboard-tile"></a>Editar ou remover um bloco do dashboard

## <a name="dashboard-owners-versus-dashboard-consumers"></a>Dashboard *proprietários* versus dashboard *consumidores*
Quando você cria ou é proprietário de um dashboard, você tem várias opções para alterar a aparência e o comportamento padrão dos blocos nesse dashboard. Use as configurações e estratégias a seguir para criar a experiência de *consumo* de dashboard para seus colegas.  Selecionar um bloco abrirá o relatório subjacente, uma URL personalizada ou um dashboard diferente? Talvez você [adicionará um bloco que exibe um vídeo ou dados de streaming](service-dashboard-add-widget.md)? E você pode até mesmo [criar um bloco que contém segmentações interativas](service-dashboard-pin-live-tile-from-report.md). Como um *criador*, você tem várias opções. 

<iframe width="560" height="315" src="https://www.youtube.com/embed/lJKgWnvl6bQ" frameborder="0" allowfullscreen></iframe>

Este artigo aborda o seguinte.

* [Criar uma visualização e fixá-la em um dashboard](#create)
* [Mover um bloco](#move)
* [Redimensionar um bloco](#resize)
* [Renomear um bloco](#rename)
* [Adicionar um hiperlink a um bloco](#hyperlink)
* [Fixar um bloco em um dashboard diferente](#different)
* [Excluir um bloco](#delete)
  
 > [!TIP]
 > Para alterar a visualização mostrada no próprio bloco, exclua o bloco e adicione um novo [bloco de dashboard](service-dashboard-tiles.md).
 > 

 ### <a name="prerequisites"></a>Pré-requisitos
 1. Para acompanhar, abra o serviço do Power BI (não o Power BI Desktop) e [baixe o exemplo de Análise de Gastos de TI](sample-it-spend.md). Quando a mensagem de "Êxito" for exibida, selecione **Ir para o dashboard**.

- - -
<a name="create"></a>

## <a name="create-a-new-visualization-and-pin-it-to-the-dashboard"></a>Criar uma nova visualização e fixá-la no dashboard
1. No dashboard Análise de Gastos de TI, selecione o bloco "Valor" para abrir o relatório.

    ![Bloco Valor](media/service-dashboard-edit-tile/power-bi-amount-tile.png)

2. Abra o relatório no modo de exibição de Edição, selecionado **Editar Relatório** da barra de menu superior.

3. Adicione uma nova página de relatório selecionando o sinal de mais (+) na parte inferior do relatório.

    ![ícone de adição](media/service-dashboard-edit-tile/power-bi-add-page.png)

4. No painel CAMPOS, selecione **Fato > Valor** e **Área de Negócios > Área de Negócios**.
 
5. No painel VISUALIZAÇÕES, selecione o ícone de Gráfico de rosca para converter a visualização em um Gráfico de rosca.

    ![Painel Visualizações](media/service-dashboard-edit-tile/power-bi-donut-chart.png)

5. Selecione o ícone de fixar e fixe o gráfico de rosca no dashboard de exemplo de Análise de Gastos de TI.

   ![passar o mouse sobre o bloco](media/service-dashboard-edit-tile/power-bi-pin.png)

6. Quando a mensagem de "Êxito" for exibida, selecione **Ir para o dashboard**. Será solicitado que você salve suas alterações. Selecione **Salvar**.

- - -
<a name="move"></a>

## <a name="move-the-tile"></a>Mover o bloco
No dashboard, localize o novo bloco. Selecione e mantenha o bloco para arrastá-la a um novo local na tela do painel.

- - -
<a name="resize"></a>

## <a name="resize-the-tile"></a>Redimensionar o bloco
Você pode fazer muitos tamanhos diferentes de bloco - de unidades e bloco 1x1 até 5x5. Selecione e arraste a alça (no canto inferior direito) para redimensionar o bloco.

![vídeo](media/service-dashboard-edit-tile/pbigif_resizetile4.gif)

- - -
## <a name="the-ellipses--menu"></a>O menu de reticências (...)

1. Selecione as reticências (...) no canto superior direito do bloco. 
   
   ![reticências do bloco](media/service-dashboard-edit-tile/power-bi-tile.png)

2. Passe o mouse sobre o bloco "Conta" e selecione as reticências para exibir as opções. As opções disponíveis variarão por tipo de bloco.  Por exemplo, as opções disponíveis para um bloco dinâmico são diferentes das opções disponíveis para um bloco de visualização padrão. Além disso, se um dashboard tiver sido compartilhado com você (e você não for o proprietário), você terá menos opções.

   ![menu de opções de reticências](media/service-dashboard-edit-tile/power-bi-tile-menu-new.png)

3. Selecione **Editar detalhes** para abrir a janela "Detalhes do bloco". 

    Altere o título e o comportamento padrão do bloco.  Por exemplo, você pode decidir que, quando um *consumidor* seleciona um bloco, em vez de abrir o relatório que foi usado para criar esse bloco, um novo dashboard é exibido em vez disso.  
   


<a name="rename"></a>

### <a name="rename-the-tile"></a>Renomear o bloco
Na parte superior da janela "Detalhes do bloco", altere **Título** para **Valor gasto**.

![Janela Detalhes do bloco](media/service-dashboard-edit-tile/power-bi-tile-title.png)


<a name="hyperlink"></a>

### <a name="change-the-default-hyperlink"></a>Alterar o hiperlink padrão
Por padrão, selecionar um bloco geralmente levará você ao relatório em que ele foi criado ou para a P e R (se o bloco tiver sido criado na P e R). Para vincular a uma página da Web, a outro dashboard ou relatório (no mesmo espaço de trabalho), a um relatório do SSRS ou a outro conteúdo online, adicione um link personalizado.

1. Sob o título Funcionalidade, selecione **Definir link personalizado**.

2. Selecione **Link para um dashboard ou relatório no espaço de trabalho atual** e selecione-o no menu suspenso.  Neste exemplo, você selecionou o dashboard de exemplo de Recursos Humanos. Se você ainda não tiver esse exemplo no espaço de trabalho, você poderá adicioná-la e voltar a esta etapa ou selecionar um dashboard diferente. 

    ![Caixa de diálogo Funcionalidade](media/service-dashboard-edit-tile/power-bi-custom-link.png)

3. Selecione **Aplicar**.

4. O novo título é exibido no bloco.  Além disso, quando você seleciona o bloco, o Power BI abre o dashboard Recursos Humanos. 

    ![título do bloco](media/service-dashboard-edit-tile/power-bi-title.png)

<a name="different"></a>

### <a name="pin-the-tile-to-a-different-dashboard"></a>Fixar o bloco em um painel diferente
1. No menu suspenso de reticências, selecione **Fixar bloco** ![ícone fixar](media/service-dashboard-edit-tile/pinnooutline.png).
2. Decida em que local fixar uma duplicata deste bloco em um dashboard existente ou em um novo dashboard. 
   
   ![Caixa de diálogo Fixar no dashboard](media/service-dashboard-edit-tile/pbi_pintoanotherdash.png)
3. Selecione **Fixar**.

<a name="delete"></a>

### <a name="delete-the-tile"></a>Excluir o bloco
1. Para remover permanentemente um bloco de um dashboard, selecione **Excluir bloco** ![ícone excluir](media/service-dashboard-edit-tile/power-bi-delete-tile-icon.png) no menu suspenso de reticências. 

2. Excluir um bloco não excluirá a visualização subjacente. Abra o relatório subjacente, selecionando o bloco "Valor". Abra a última página em seu relatório para ver que a visualização original não foi excluída do relatório. 

- - -
## <a name="next-steps"></a>Próximas etapas
[Blocos de Dashboard no Power BI](service-dashboard-tiles.md)

[Dashboards no Power BI](service-dashboards.md)

[Power BI – conceitos básicos](service-basic-concepts.md)

Mais perguntas? [Experimente a Comunidade do Power BI](http://community.powerbi.com/)

