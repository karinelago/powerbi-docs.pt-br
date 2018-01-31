---
title: Ver dados e registros em visuais do Power BI Desktop
description: Usar os recursos Ver Dados e Ver Registros do Power BI Desktop para analisar os detalhes
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
ms.date: 01/24/2018
ms.author: davidi
ms.openlocfilehash: a61a5d46c2f663ff7e8388a862f5649487504092
ms.sourcegitcommit: 7249ff35c73adc2d25f2e12bc0147afa1f31c232
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/25/2018
---
# <a name="use-see-data-and-see-records-in-power-bi-desktop"></a>Use Ver Dados e Ver Registros no Power BI Desktop
No **Power BI Desktop**, é possível analisar em detalhes qualquer visual e ver uma representação textual dos dados ou dos elementos de dados individuais para um visual selecionado. Esses recursos às vezes são chamados de *clickthrough*, *drill-through* ou *drill-through em detalhes*.

É possível usar **Ver Registros** para exibir as linhas subjacentes de um elemento de dados selecionado de um visual ou use **Ver Dados** para exibir uma versão textual dos valores usados no visual. Há algumas limitações para usar **Ver Dados** e **Ver Registros**, discutidas no fim deste artigo.

![](media/desktop-see-data-see-records/see-data-see-records_1.png)

## <a name="using-see-data-in-power-bi-desktop"></a>Usando Ver Dados no Power BI Desktop
O botão **Ver Dados** está localizado na guia **Dados/Analisar** na seção **Ferramentas Visuais** da faixa de opções.

![](media/desktop-see-data-see-records/see-data-see-records_2.png)

Também é possível **Ver Dados** clicando com o botão direito do mouse em um visual e, em seguida, selecionando **Ver Dados** no menu exibido.

![](media/desktop-see-data-see-records/see-data-see-records_3.png)

> [!NOTE]
> É necessário focalizar um ponto de dados no visual para que o menu de clique com o botão direito do mouse fique disponível.
> 
> 

Quando você seleciona **Ver Dados**, o **Power BI Desktop** enfoca o visual e os dados selecionados e dedica o espaço da tela para exibir a representação visual e textual dos dados. O visual é exibido na metade superior da tela, e os dados são mostrados na metade inferior, conforme mostrado na imagem a seguir. Essa é a exibição *horizontal*.

![](media/desktop-see-data-see-records/see-data-see-records_4.png)

Também é possível mudar para uma *exibição vertical* (ou voltar para *exibição horizontal*), selecionando o ícone no canto superior direito.

![](media/desktop-see-data-see-records/see-data-see-records_5.png)

Para retornar ao relatório, selecione **< Voltar ao Relatório** no canto superior esquerdo da tela.

![](media/desktop-see-data-see-records/see-data-see-records_6.png)

## <a name="using-see-records-in-power-bi-desktop"></a>Usando Ver Registros no Power BI Desktop
Também é possível enfocar um elemento de dados em um visual e detalhar os dados atrás dele. Quando um visual é selecionado, há duas maneiras de usar **Ver Registros**; você pode habilitar o botão de alternância **Ver Registros** na faixa de opções **Dados/Analisar** e, em seguida, clicar em um elemento de dados ou você pode clicar com o botão direito do mouse em um elemento de dados e selecionar **Ver Registros** no menu exibido.

![](media/desktop-see-data-see-records/see-data-see-records_7.png)

> [!NOTE]
> Se o visual selecionado não for compatível com **Ver Registros**, o botão na faixa de opções ficará acinzentado.
> 
> 

Quando **Ver Registros** estiver selecionado, o **Power BI Desktop** enfocará esse elemento de dados individual e dedicará a área da tela para exibir os dados para esse elemento, conforme mostrado na imagem a seguir.

![](media/desktop-see-data-see-records/see-data-see-records_8.png)

Para retornar ao relatório, selecione o botão **Voltar ao Relatório** no canto superior esquerdo da tela.

## <a name="limitations"></a>Limitações
Há algumas limitações a serem consideradas ao usar **Ver Dados** ou **Ver Registros**:

* Há suporte apenas para os seguintes tipos de visual:
  * **Barra**
  * **Coluna**
  * **Mapa**
  * **Mapa de Árvore**
  * **Mapa Coroplético**
  * **Pizza**
  * **Rosca**
  * **Funil**
* Não é possível usar **Ver Registros** quando seu visual usa uma medida calculada
* Não é possível usar **Ver Registros** quando conectado a um modelo MD (multidimensional) dinâmico

## <a name="next-steps"></a>Próximas etapas
Há todos os tipos de recursos para gerenciamento de dados e formatação do relatório no **Power BI Desktop**. Confira os seguintes recursos para alguns exemplos:

* [Usar agrupamento e compartimentalização no Power BI Desktop](desktop-grouping-and-binning.md)
* [Usar linhas de grade, ajustar à grade, ordem z, alinhamento e distribuição em relatórios do Power BI Desktop](desktop-gridlines-snap-to-grid.md)

