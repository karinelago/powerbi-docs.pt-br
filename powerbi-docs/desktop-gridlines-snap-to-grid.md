---
title: "Use linhas de grade e ajuste de grade em relatórios do Power BI Desktop"
description: "Usar linhas de grade, ajustar à grade, ordem z, alinhamento e distribuição em relatórios do Power BI Desktop"
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
ms.date: 12/06/2017
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: 1b6b1a3ecda7d3f827975da8fcfec5d9d5b67023
ms.sourcegitcommit: 88c8ba8dee4384ea7bff5cedcad67fce784d92b0
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/24/2018
---
# <a name="use-gridlines-and-snap-to-grid-in-power-bi-desktop-reports"></a>Use linhas de grade e ajuste de grade em relatórios do Power BI Desktop
A tela de relatório do **Power BI Desktop** fornece linhas de grade que permitem que você alinhe adequadamente visuais em uma página de relatório e também fornece a funcionalidade de ajustar à grade para que os visuais em seus relatórios pareçam limpos, alinhados e com espaçamento uniforme.

No **Power BI Desktop**, também é possível ajustar a ordem z (avançar, recuar) de objetos em um relatório, bem como alinhar ou distribuir uniformemente os visuais selecionados na tela.

![](media/desktop-gridlines-snap-to-grid/snap-to-grid_0.png)

### <a name="enabling-gridlines-and-snap-to-grid"></a>Habilitando linhas de grade e ajuste de grade
Para habilitar as linhas de grade e o ajuste à grade, selecione a faixa de opções **Modo de Exibição**, habilite as caixas de seleção para **Mostrar linhas de grade** e **Ajustar objetos à grade.** Você pode selecionar uma ou ambas as caixas. Elas operam independentemente.

![](media/desktop-gridlines-snap-to-grid/snap-to-grid_1.png)

> [!NOTE]
> Se **Mostrar linhas de grade** e **Ajustar objetos na grade** estiverem desabilitadas, conecte-se a qualquer fonte de dados e elas serão habilitadas.
> 
> 

### <a name="using-gridlines"></a>Uso de linhas de grade
Linhas de grade são guias de elementos visuais que permitem que você veja se dois ou mais elementos visuais estão alinhados corretamente. Quando estiver tentando determinar se dois (ou mais) elementos visuais estão alinhados horizontalmente ou verticalmente, use as linhas de grade para determinar visualmente se suas bordas se alinham.

Você pode usar *CTRL + clique* para selecionar mais de um elemento visual por vez, que exibe as bordas de todos os elementos visuais selecionados, que ajuda você a ver facilmente se os elementos visuais estão alinhados corretamente.

![](media/desktop-gridlines-snap-to-grid/snap-to-grid_2.png)

#### <a name="using-gridlines-inside-visuals"></a>Usando linhas de grade dentro de visuais
No Power BI, também há linhas de grade dentro de visuais, que fornecem guias de visuais para comparação de valores e pontos de dados. A partir da versão de setembro de 2017 do **Power BI Desktop**, agora você pode gerenciar as linhas de grade nos visuais usando o cartão **Eixo X** ou **Eixo Y** (conforme apropriado, com base no tipo de visual), encontrado na seção **Formato** do painel **Visualizações**. Gerencie os seguintes elementos de linhas de grade dentro de um visual:

* Ativar ou desativar linhas de grade
* Alterar a cor das linhas de grade
* Ajustar o traço (a largura) das linhas de grade
* Selecionar o estilo de linha das linhas de grade no visual, como sólido, tracejado ou pontilhado

A modificação de alguns elementos das linhas de grade pode ser especialmente útil em relatórios nos quais são usadas telas de fundo escuras em visuais. A imagem a seguir mostra a seção *Linhas de grade* no cartão **Eixo X**.

![](media/desktop-gridlines-snap-to-grid/snap-to-grid_9.png)

### <a name="using-snap-to-grid"></a>Uso da grade de ajuste
Quando você habilita **Ajustar objetos à grade**, todos os elementos visuais na tela do **Power BI Desktop** que você move (ou redimensiona) são alinhados automaticamente para o eixo de grade mais próximo, tornando muito mais fácil garantir que dois ou mais elementos visuais estejam alinhados à mesma localização horizontal ou vertical ou o tamanho.

![](media/desktop-gridlines-snap-to-grid/snap-to-grid_3.png)

E isso é tudo para usar **linhas de grade** e **ajuste de grade** para garantir facilmente que os elementos visuais em seus relatórios estejam alinhados adequadamente.

### <a name="using-z-order-align-and-distribute"></a>Usando a ordem z, alinhar e distribuir
Também é possível gerenciar a ordem de frente para trás de elementos visuais em um relatório, frequentemente conhecida como o *ordem z* de elementos. Isso permite que você sobreponha visuais como você desejar. Em seguida, ajuste a ordem de frente para trás de cada elemento visual. Essa classificação é feita usando os botões **Avançar** e **Recuar**, encontrados na seção **Organizar** da faixa de opções **Formatar**, exibida assim que você seleciona um ou mais visuais na página (e não estará disponível se nenhum elemento visual for selecionado).

![](media/desktop-gridlines-snap-to-grid/snap-to-grid_4.png)

A faixa de opções **Formatar** também permite que você alinhe seus visuais de várias maneiras diferentes. Isso permite que você garanta que seus visuais sejam exibidos na página no alinhamento que você acredita ter melhor aparência e funcionamento.

![](media/desktop-gridlines-snap-to-grid/snap-to-grid_5.png)

Quando um elemento visual é selecionado, usar o botão **Alinhar** alinha esse elemento visual à borda (ou ao centro) da tela do relatório, conforme mostrado na imagem a seguir.

![](media/desktop-gridlines-snap-to-grid/snap-to-grid_6.png)

Quando dois ou mais visuais são selecionados, eles são alinhados juntos e usam o limite de alinhamento existente dos visuais para alinhamento. Por exemplo, com dois visuais selecionados e o botão *Alinhar à esquerda* selecionado, os visuais serão alinhados ao limite mais à esquerda de todos os visuais selecionados.

![](media/desktop-gridlines-snap-to-grid/snap-to-grid_7.png)

Também é possível distribuir seus visuais de maneira uniforme na tela do relatório, seja vertical ou horizontalmente. Basta usar o botão **Distribuir** da faixa de opções **Formatar**.

![](media/desktop-gridlines-snap-to-grid/snap-to-grid_8.png)

Com algumas seleções dessas linhas de grade, alinhamento e ferramentas de distribuição, seus relatórios terão a aparência que você desejar.

