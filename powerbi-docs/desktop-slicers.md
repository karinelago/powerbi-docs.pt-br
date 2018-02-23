---
title: "Usando segmentações de dados do Power BI Desktop"
description: "Você pode usar segmentações de dados no Power BI Desktop para filtrar, realçar e personalizar relatórios"
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
ms.date: 02/05/2018
ms.author: davidi
ms.openlocfilehash: 107b4eace4e5b10b52900a4d15110c8acad0f462
ms.sourcegitcommit: db37f5cef31808e7882bbb1e9157adb973c2cdbc
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/09/2018
---
# <a name="using-slicers-power-bi-desktop"></a>Usando segmentações de dados do Power BI Desktop

Você pode usar uma **segmentação de dados** no **Power BI Desktop** para filtrar os resultados de elementos visuais na página do seu relatório. E com as segmentações de dados, você pode ajustar facilmente o filtro que é aplicado ao interagir com a segmentação de dados em si. Você também pode especificar opções para como a segmentação de dados é exibida, e como interagir com ela. A imagem a seguir mostra uma segmentação de dados, com seu menu suspenso *tipo* visível. 

![](media/desktop-slicers/desktop-slicers_01.png)

Uma segmentação de dados pode ser mostrada em um dos vários tipos:

* List
* Lista suspensa
* Entre
* Menor ou igual a
* Maior ou igual a

Você pode adicionar uma segmentação de dados a um relatório clicando no elemento visual **segmentação de dados** no painel **Visualizações**.

![](media/desktop-slicers/desktop-slicers_02.png)

As segmentações de dados comportam-se da mesma forma no **Power BI Desktop** e no **serviço do Power BI**. Para ver um tutorial sobre como usar segmentações de dados, confira [segmentações de dados no serviço do Power BI (tutorial)](power-bi-visualization-slicers.md).

## <a name="synchronize-slicers-across-report-pages"></a>Sincronizar as segmentações de dados nas páginas do relatório

No **Power BI Desktop**, você pode sincronizar as segmentações de dados em várias páginas do relatório. Para sincronizar as segmentações de dados no painel **Exibição** na faixa de opções, selecione **Sincronizar segmentações de dados**. Quando você sincronizar as segmentações de dados, o painel **Sincronizar segmentações de dados** é exibido, conforme mostrado na imagem a seguir.

![](media/desktop-slicers/desktop-slicers_03.png)

No painel **Sincronizar segmentações de dados**, você pode especificar como a segmentação de dados deve ser sincronizada nas páginas do relatório. Você pode especificar se cada segmentação de dados deve ser **aplicada** a cada página de relatório individual e se a segmentação de dados deve ser **visível** em cada página de relatório individual.

Por exemplo, você pode colocar uma segmentação de dados na **Página 2** do seu relatório, conforme mostrado na imagem a seguir. Você pode selecionar se essa segmentação de dados deve ser *aplicada* a cada página selecionada e se essa segmentação de dados deve ser *visível* em cada página selecionada no relatório. Você pode aplicar qualquer combinação das duas a cada segmentação de dados. 

![](media/desktop-slicers/desktop-slicers_04.png)

Usar o link **Adicionar a todos** no painel aplica a segmentação de dados selecionada a todas as páginas no relatório.

Observe que as seleções mostradas no painel **Sincronizar segmentações de dados** aplicam apenas a *segmentação de dados selecionada*. Você pode aplicar várias segmentações de dados a várias páginas e usar o painel para definir como cada segmentação de dados é individualmente aplicada a várias páginas em seu relatório. 

Embora a seleção de segmentação de dados possa ser sincronizada, outras seleções, como estilos, edição e exclusão, *não* serão sincronizadas. 

## <a name="next-steps"></a>Próximas etapas

Você também pode estar interessado nos seguintes artigos:

* [Segmentação de dados no serviço do Power BI (tutorial)](power-bi-visualization-slicers.md)
* [Usar a segmentação de intervalo numérico no Power BI Desktop](desktop-slicer-numeric-range.md)
* [Usar uma segmentação e um filtro de datas relativas no Power BI Desktop](desktop-slicer-filter-date-range.md)

