---
title: "Usar a segmentação de intervalo numérico no Power BI Desktop"
description: "Saiba como usar uma segmentação para restringir a intervalos numéricos no Power BI Desktop"
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
ms.date: 10/12/2017
ms.author: davidi
ms.openlocfilehash: 713497c8c684b34cbaaeafab84a7db1fc7d14c2a
ms.sourcegitcommit: 99cc3b9cb615c2957dde6ca908a51238f129cebb
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/13/2017
---
# <a name="use-the-numeric-range-slicer-in-power-bi-desktop"></a>Usar a segmentação de intervalo numérico no Power BI Desktop
Com a **segmentação de intervalo numérico**, você pode aplicar todos os tipos de filtros a qualquer coluna numérica no modelo de dados. Você pode optar por filtrar como **entre** números, **menor ou igual** a um número ou **maior ou igual** a um número. Embora possa parecer simples, essa é uma maneira muito eficiente de filtrar os dados.

![](media/desktop-slicer-numeric-range/slicer-numeric-range_2.png)

## <a name="using-the-numeric-range-slicer"></a>Usando a segmentação de intervalo numérico
Você pode usar a segmentação de intervalo numérico como qualquer outra segmentação de dados. Basta criar um visual de **segmentação** para o relatório e, em seguida, selecionar um valor numérico para o valor **Campo**. Na imagem a seguir, o campo *UnitPrice* é selecionado.

![](media/desktop-slicer-numeric-range/slicer-numeric-range_3.png)

Selecione o símbolo no canto superior direito da **segmentação de intervalo numérico** e um menu será exibido.

![](media/desktop-slicer-numeric-range/slicer-numeric-range_4.png)

Para o intervalo numérico, você pode selecionar uma das três seleções a seguir:

* Entre
* Menor ou igual a
* Maior ou igual a

Ao selecionar **Entre** no menu, um controle deslizante será exibido e você poderá filtrar os valores numéricos que estão entre os números. Além de usar a barra de controle deslizante, você pode clicar em qualquer caixa e digitar os valores. Isso é conveniente quando você deseja dividir em números inteiros específicos e a granularidade de movimentação da barra de segmentação dificulta encontrar exatamente esse número.

Na imagem a seguir, a página do relatório é filtrada por valores de *UnitPrice* que variam entre 500 e 1500.

![](media/desktop-slicer-numeric-range/slicer-numeric-range_5.png)

Quando selecionamos **menor ou igual a**, a alça esquerda (valor mais baixo) da barra de controle deslizante desaparece e somente podemos ajustar o limite superior da barra de controle deslizante. Na imagem a seguir, definimos a barra de controle deslizante para 497,17.

![](media/desktop-slicer-numeric-range/slicer-numeric-range_6.png)

Por fim, se selecionarmos **maior ou igual a**, a alça da barra de controle deslizante direita (valor mais alto) desaparecerá e poderemos ajustar o valor menor, conforme é mostrado na imagem a seguir. Agora apenas os itens com *UnitPrice* maior ou igual a 750,56 são exibidos nos visuais na página do relatório.

![](media/desktop-slicer-numeric-range/slicer-numeric-range_7.png)

## <a name="limitations-and-considerations"></a>Limitações e considerações
No momento, as seguintes considerações e limitações aplicam-se à **segmentação de intervalo numérico**

* No momento, a **segmentação de intervalo numérico** filtra todas as linhas subjacentes nos dados, não qualquer valor agregado. Por exemplo, se o campo *Valor de Vendas* for usado, cada transação com base em *Valor de Vendas* será filtrada, não a soma de *Valor de Vendas* de cada ponto de dados de um visual.
* No momento, isso não funciona com Medidas
* No momento, a **segmentação de intervalo numérico** somente está disponível no **Power BI Desktop**. Se um relatório que usa a **segmentação de intervalo numérico** for publicado para o **serviço do Power BI**, o filtro ainda será aplicado, mas será exibido como uma segmentação de lista.

