---
title: "Segmentações no Power BI (tutorial)"
description: "Tutorial: segmentações no Power BI"
services: powerbi
documentationcenter: 
author: mihart
manager: kfile
backup: 
editor: 
tags: 
featuredvideoid: zIZPA0UrJyA
qualityfocus: monitoring
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 03/05/2018
ms.author: v-thepet
LocalizationGroup: Visualizations
ms.openlocfilehash: cfa4c0f17c67a036b7d01744da1b5247345c493a
ms.sourcegitcommit: 4217430c3419046c3a90819c34f133ec7905b6e7
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2018
---
# <a name="slicers-in-power-bi-tutorial"></a>Segmentações no Power BI (tutorial)
Uma vice-presidente de vendas deseja observar diversas métricas de toda a divisão e de cada gerente regional individualmente. Ela pode criar um relatório separado para cada gerente ou ela pode usar uma segmentação. Uma segmentação restringe a parte do conjunto de dados que é mostrada nas outras visualizações de um relatório. As segmentações são uma maneira alternativa de filtragem.

Este tutorial usa o [Exemplo de análise de varejo](sample-retail-analysis.md) gratuito para ajudá-lo a criar e formatar uma segmentação e usá-la para filtrar um relatório. Divirta-se ao descobrir maneiras de formatar e usar segmentações. 

![segmentação de dados](media/power-bi-visualization-slicers/slicer2.gif)

## <a name="when-to-use-a-slicer"></a>Quando usar uma segmentação
As segmentações são uma ótima opção quando você deseja:

* Exibir os filtros mais usados ou importantes na tela do relatório para facilitar o acesso.
* Facilitar a exibição do estado atual filtrado sem precisar abrir uma lista suspensa. 
* Filtrar por colunas que são desnecessárias e que ficam ocultas nas tabelas de dados.
* Criar relatórios mais específicos, colocando as segmentações ao lado de visuais importantes.

As segmentações do Power BI têm as seguintes limitações:

- As segmentações de dados não dão suporte a campos de entrada.
- As segmentações de dados não podem ser anexadas a um dashboard.
- Não há suporte para busca detalhada para segmentações de dados.
- As segmentações não são compatíveis com filtros de nível de visual.

## <a name="create-a-slicer"></a>Criar uma segmentação

Este tutorial usa uma segmentação de lista. Tipos de dados numéricos e de data/hora podem ter segmentações de intervalo. Consulte [Usar a segmentação de intervalo numérico no Power BI Desktop](desktop-slicer-numeric-range.md) ou o vídeo a seguir para obter mais informações sobre como criar e usar segmentações de intervalo.
<iframe width="560" height="315" src="https://www.youtube.com/embed/zIZPA0UrJyA" frameborder="0" allowfullscreen></iframe>

1. No Power BI Desktop ou no serviço do Power BI, abra o [Exemplo de análise de varejo](sample-retail-analysis.md) em [Modo de Exibição de Edição](service-interact-with-a-report-in-editing-view.md) e [adicionar uma nova página de relatório](power-bi-report-add-page.md).
2. No painel Campos, em Distrito, selecione **Gerente regional** para criar uma nova visualização.
    
    ![novo gráfico](media/power-bi-visualization-slicers/1-new-vis.png)
    
3. Selecione o ícone **Segmentação** ![ícone segmentação](media/power-bi-visualization-slicers/slicer-icon.png) no painel de Visualizações para converter a nova visualização em uma segmentação. 
    
    ![converter em segmentação](media/power-bi-visualization-slicers/2-slicer.png)

Você também pode selecionar o ícone de Segmentação para criar uma nova segmentação e, em seguida, selecionar ou arrastar um campo de dados para a caixa Campo para preenchê-la.

>[!TIP]
>Você pode classificar itens da lista de segmentação por valores de dados. Para classificar os itens da segmentação em ordem alfabética inversa, selecione as reticências (...) no canto superior direito da segmentação e escolha **Classificar por gerente regional**. A configuração está em ordem alfabética crescente por padrão, mas pode ser alternada entre crescente e decrescente. 

## <a name="format-the-slicer"></a>Formatar a segmentação
Aplique formatação visual à segmentação de Gerente regional.
1. Com a segmentação selecionada, no painel Visualizações, selecione o ícone Formatar ![](media/power-bi-visualization-slicers/power-bi-paintroller.png) para exibir os controles de formatação. 
    
    ![formatação](media/power-bi-visualization-slicers/3-format.png)
    
2. Clique nas setas de lista suspensa ao lado de cada categoria para exibir e editar as opções. 

### <a name="general-options"></a>Opções gerais
1. Selecione vermelho em **Cor do contorno** e altere a **Espessura do contorno** para "2". Isso define a cor e a espessura dos contornos ou sublinhados do cabeçalho e do item, quando habilitados. 
2. Em Orientação, Vertical é o padrão ao criar uma segmentação de lista vertical com caixas de seleção antes dos itens. Selecione **Horizontal** para produzir uma segmentação com itens organizados na horizontal. A orientação horizontal pode produzir várias organizações de texto, botões ou blocos, dependendo do tamanho da segmentação e da forma e formatação do item. 
    
    ![horizontal](media/power-bi-visualization-slicers/4-horizontal.png)
    
3. Ative o layout **Dinâmico**. Isso altera o tamanho e a disposição dos itens da segmentação horizontal para coincidir com a forma e o tamanho da segmentação. Em um tamanho muito pequeno, a segmentação se torna um ícone de filtro. 
    
    ![dinâmico](media/power-bi-visualization-slicers/5-responsive.png)
    
    >[!NOTE]
    >As alterações de layout dinâmico podem substituir a formatação específica de cabeçalho e de item que você definiu. 
    
4. Defina a posição e o tamanho da segmentação com precisão numérica em **Posição X**, **Posição Y**, **Largura** e **Altura**, ou mova e redimensione a segmentação diretamente na tela, para produzir diferentes tamanhos de item e organizações, como uma linha horizontal de botões. 

    ![botões horizontais](media/power-bi-visualization-slicers/6-buttons.png)

Consulte [Criar uma segmentação dinâmica que possa ser redimensionada no Power BI](power-bi-slicer-filter-responsive.md) para obter mais informações sobre formatação dinâmica e orientação horizontal.

### <a name="selection-controls-options"></a>Opções de Controles de Seleção
1. A opção Mostrar Selecionar Tudo fica desativada por padrão. **Ative-a** para adicionar um item Selecionar Tudo à segmentação, permitindo a seleção e anulação de seleção de todos os itens quando pressionado. Quando todos os itens estão selecionados, clicar em um item anula a respectiva seleção, funcionando como um filtro do tipo "não-é". 
    
    ![selecionar tudo](media/power-bi-visualization-slicers/7-select-all.png)
    
2. A Seleção única fica ativada por padrão. Basta clicar em cada item para selecioná-lo e manter a tecla CTRL pressionada ao clicar em vários itens para selecioná-los. **Desative** a Seleção única para permitir a seleção de vários itens sem manter a tecla CTRL pressionada. Se você clicar em cada item novamente, anulará a seleção. 

### <a name="header-options"></a>Opções de cabeçalho
O cabeçalho fica Ativado por padrão, mostrando o nome do campo de dados na parte superior da segmentação. 
1. Formate o texto do cabeçalho para usar a **Cor da fonte** vermelha, o **Tamanho do texto** em 14 pontos e a **Família de fontes** Arial Black. 
2. Em Contorno, escolha **Somente inferior** para produzir um sublinhado com o tamanho e a cor definidos nas Opções gerais. 

### <a name="item-options"></a>Opções de item
1. Formate o texto e a tela de fundo do item para usar a **Cor da fonte** preta, a **Tela de fundo** vermelha clara, o **Tamanho do texto** em 10 pontos e a **Família de fontes** Arial. 
2. Em Contorno, escolha **Quadro** para desenhar uma borda ao redor de cada item com o tamanho e cor definidos nas Opções gerais. 
    
    ![formatado](media/power-bi-visualization-slicers/8-formatted.png)
    
    >[!TIP]
    >- Com a Orientação Horizontal, os itens desmarcados mostram as cores do texto e da tela de fundo selecionados, enquanto que os itens selecionados usam o padrão do sistema, geralmente telas de fundo de cor preta, com texto em branco. 
    >- Com a Orientação Vertical, os itens sempre mostram as cores definidas e as caixas de seleção ficam sempre pretas quando selecionadas. 

### <a name="other-formatting-options"></a>Outras opções de formatação
As outras opções de formatação ficam desativadas por padrão. Quando **Ativadas**: 
- **Título:** adiciona e formata um título (além do cabeçalho e independente dele) na parte superior da segmentação. 
- **Tela de fundo:** adiciona uma cor da tela de fundo para a segmentação geral e define a transparência.
- **Fixar proporção:** retém a forma da segmentação se ela for redimensionada.
- **Borda:** adiciona uma borda de 1 pixel em torno da segmentação e define sua cor. (Essa borda da segmentação é separada e não é afetada pelas configurações do Contorno Geral). 

## <a name="sync-and-use-the-slicer-on-other-pages"></a>Sincronizar e usar a segmentação em outras páginas
Começando com a atualização de fevereiro de 2018 do Power BI, você pode sincronizar uma segmentação e usá-la em uma ou em todas as páginas de um relatório. 
1. Com a segmentação Gerente Regional selecionada, no menu Exibir, selecione **Sincronizar segmentações** no Power BI Desktop ou ative o **Painel sincronizar segmentações** no serviço do Power BI. O painel Sincronizar Segmentações é exibido. 
    
    ![sincronizar segmentações](media/power-bi-visualization-slicers/9-sync-slicers.png)
    
2. Na primeira coluna, selecione **Visão geral** e as outras páginas com as quais você deseja que a segmentação se sincronize, ou clique em **Adicionar a todos** para fazer com que a segmentação se sincronize com todas as páginas do relatório.  
3. Na próxima coluna, selecione **Visão geral** e as outras páginas nas quais você deseja que a segmentação fique visível. 
4. Mude para a página **Visão geral** e observe a segmentação e seus efeitos sobre os outros visuais da página. 
    - Selecione e remova a seleção de itens diferentes e observe como os outros visuais na página se alteram. A seleção de itens em qualquer página reflete em todas as páginas sincronizadas.
    - Altere o tamanho, a forma, a posição e/ou a formatação da segmentação na página de Visão geral. A formatação da segmentação em outras páginas sincronizadas não é alterada. 

### <a name="control-which-page-visuals-are-affected-by-the-slicer"></a>Controlar quais visuais da página são afetados pela segmentação
Por padrão, uma segmentação em uma página de relatório afeta todas as outras visualizações nessa página. Use **Interações Visuais** para impedir que algumas visualizações de página sejam afetadas.

1. Na página **Visão geral**, com a segmentação selecionada:
    - No Power BI Desktop, clique no menu Formatar, em Ferramentas Visuais, e selecione **Editar interações**.
    - No serviço do Power BI, selecione a lista suspensa **Interações visuais**, na barra de menus, e ative **Editar interações**. 
    
    Os controles de filtro são exibidos acima de todos os outros visuais na página. ![controles de filtro](media/power-bi-visualization-slicers/filter-controls.png)
    
2. Selecione o ícone **Nenhum** acima de um visual para fazer com que a segmentação pare de filtrá-lo. Selecione o ícone **Filtrar** para que a segmentação de dados inicie a filtragem do visual novamente. 

Consulte [Interações visuais em um relatório do Power BI](service-reports-visual-interactions.md) para obter mais informações sobre como editar interações.

## <a name="next-steps"></a>Próximas etapas
[Experimente – é gratuito!](https://powerbi.com/)

Você tem algumas ideias para melhorar o Power BI? [Envie uma ideia](https://ideas.powerbi.com/forums/265200-power-bi-ideas).

Mais perguntas? [Experimente a Comunidade do Power BI](http://community.powerbi.com/)

[Adicionar uma visualização a um relatório](power-bi-report-add-visualizations-i.md)

[Tipos de visualização no Power BI](power-bi-visualization-types-for-reports-and-q-and-a.md)

[Power BI – conceitos básicos](service-basic-concepts.md)

