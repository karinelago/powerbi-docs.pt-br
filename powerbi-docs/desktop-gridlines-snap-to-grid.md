---
title: Use linhas de grade e ajuste de grade em relatórios do Power BI Desktop
description: Usar linhas de grade, ajustar à grade, ordem z, alinhamento e distribuição em relatórios do Power BI Desktop
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 4/19/2018
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: 7477fc19dda5aeb7729fbbde319faa0d930db179
ms.sourcegitcommit: 80d6b45eb84243e801b60b9038b9bff77c30d5c8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34289822"
---
# <a name="use-gridlines-and-snap-to-grid-in-power-bi-desktop-reports"></a>Use linhas de grade e ajuste de grade em relatórios do Power BI Desktop
A tela de relatório do **Power BI Desktop** fornece linhas de grade que permitem que você alinhe adequadamente visuais em uma página de relatório e use a funcionalidade de ajustar à grade para que os visuais em seus relatórios fiquem limpos, alinhados e com espaçamento uniforme.

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
As linhas de grade são guias visíveis que ajudam a alinhar os visuais. Quando você estiver tentando determinar se dois (ou mais) visuais estão alinhados horizontalmente ou verticalmente, use as linhas de grade para determinar visualmente se suas bordas estão alinhadas.

Use Ctrl + clique para selecionar mais de um visual de uma vez, o que exibe as bordas de todos os visuais selecionados e mostra se os visuais estão alinhados corretamente.

![](media/desktop-gridlines-snap-to-grid/snap-to-grid_2.png)

#### <a name="using-gridlines-inside-visuals"></a>Usando linhas de grade dentro de visuais
No Power BI também há linhas de grade dentro dos visuais que fornecem as guias visíveis para comparar valores e pontos de dados. A partir da versão de setembro de 2017 do **Power BI Desktop**, agora você pode gerenciar as linhas de grade nos visuais usando o cartão **Eixo X** ou **Eixo Y** (conforme apropriado, com base no tipo de visual), encontrado na seção **Formato** do painel **Visualizações**. Gerencie os seguintes elementos de linhas de grade dentro de um visual:

* Ativar ou desativar linhas de grade
* Alterar a cor das linhas de grade
* Ajustar o traço (a largura) das linhas de grade
* Selecionar o estilo de linha das linhas de grade no visual, como sólido, tracejado ou pontilhado

A modificação de alguns elementos das linhas de grade pode ser especialmente útil em relatórios nos quais são usadas telas de fundo escuras em visuais. A imagem a seguir mostra a seção **Linhas de grade** no cartão **Eixo y**.

![](media/desktop-gridlines-snap-to-grid/snap-to-grid_9.png)

### <a name="using-snap-to-grid"></a>Uso da grade de ajuste
Quando você habilita **Ajustar objetos à grade**, todos os elementos visuais na tela do **Power BI Desktop** que você move (ou redimensiona) são alinhados automaticamente para o eixo de grade mais próximo, tornando muito mais fácil garantir que dois ou mais elementos visuais estejam alinhados à mesma localização horizontal ou vertical ou o tamanho.

![](media/desktop-gridlines-snap-to-grid/snap-to-grid_3.png)

E isso é tudo para usar **linhas de grade** e **ajustar à grade** para garantir que os visuais em seus relatórios fiquem alinhados adequadamente.

### <a name="using-z-order-align-and-distribute"></a>Usando a ordem z, alinhar e distribuir
Você pode gerenciar a ordem de frente para trás dos visuais em um relatório, conhecida como *ordem z* de elementos. Este recurso permite sobrepor visuais da maneira que desejar e, em seguida, ajustar a ordem de frente para trás de cada um deles. É possível definir a ordem dos visuais usando os botões **Avançar** e **Recuar**, encontrado na seção **Organizar** da faixa de opções **Formato**. A faixa de opções **Formato** é exibida assim que você seleciona um ou mais visuais na página.

![](media/desktop-gridlines-snap-to-grid/snap-to-grid_4.png)

A faixa de opções **Formato** permite que você alinhe os visuais de várias maneiras diferentes, o que garante que eles sejam exibidos na página com o alinhamento que tenha a melhor aparência e funcionamento.

![](media/desktop-gridlines-snap-to-grid/snap-to-grid_5.png)

O botão **Alinhar** alinha um visual selecionado à borda (ou ao centro) da tela do relatório, conforme é mostrado na imagem a seguir.

![](media/desktop-gridlines-snap-to-grid/snap-to-grid_6.png)

Quando dois ou mais visuais são selecionados, eles são alinhados juntos e usam o limite de alinhamento existente dos visuais para o alinhamento. Por exemplo, se você selecionar dois visuais e escolher a opção **Alinhar à Esquerda**, eles serão alinhados ao limite mais à esquerda de todos os visuais.

![](media/desktop-gridlines-snap-to-grid/snap-to-grid_7.png)

Também é possível distribuir seus visuais de maneira uniforme na tela do relatório, seja vertical ou horizontalmente. Basta usar o botão **Distribuir** da faixa de opções **Formatar**.

![](media/desktop-gridlines-snap-to-grid/snap-to-grid_8.png)

Com algumas seleções dessas ferramentas de linhas de grade, alinhamento e distribuição, seus relatórios terão exatamente a aparência que você desejar.

