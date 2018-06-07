---
title: Classificação por coluna no Power BI Desktop
description: Classificação por coluna no Power BI Desktop
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 05/17/2018
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: 42bd263f09acb8739830ac6e2280e7d5d0f86228
ms.sourcegitcommit: 80d6b45eb84243e801b60b9038b9bff77c30d5c8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34482074"
---
# <a name="sort-by-column-in-power-bi-desktop"></a>Classificação por coluna no Power BI Desktop
No **Power BI Desktop** e no **serviço do Power BI**, você pode alterar a aparência de um visual, classificando-o por diferentes campos de dados. Ao alterar a maneira como você classifica um visual, é possível realçar as informações que você deseja transmitir e garantir de que o visual reflita essa tendência (ou ênfase).

Se estiver usando dados numéricos (como valores de vendas) ou dados de texto (como nomes de estado), você pode classificar suas visualizações da forma que quiser e fazer com que elas tenham a aparência desejada.  O **Power BI** oferece muita flexibilidade para a classificação e menus rápidos para você usar. Em qualquer visual, selecione o menu de reticências (...) e, em seguida, o campo pelo qual você deseja classificar, conforme mostrado na imagem a seguir.

![Menu Mais opções](media/desktop-sort-by-column/sortbycolumn_2.png)

## <a name="more-depth-and-an-example"></a>Mais detalhes e um exemplo
Vamos tomar um exemplo com mais detalhes e ver como ele funciona no **Power BI Desktop**.

A visualização a seguir mostra os custos, quantidades e montantes pelo nome do fabricante. Esta é a aparência da visualização antes de fazermos qualquer classificação.

![Visualização inicial](media/desktop-sort-by-column/sortbycolumn_1.png)

Atualmente, o visual é classificado por **SalesQuantity** – podemos observar isso fazendo a correspondência entre a cor das barras ascendentes e a legenda, mas há uma maneira melhor de determinar a coluna de classificação atual: o menu de reticências (...) no canto superior direito do visual. Quando selecionamos as reticências, vemos o seguinte:

![Menu Mais opções](media/desktop-sort-by-column/sortbycolumn_2.png)

* O campo de classificação atual é **SalesQuantity**, indicado pelo fato de que **Classificar por SalesQuantity** está em negrito e tem uma barra amarela. 

* A direção de classificação atual é do menor para o maior, conforme mostrado pelo ícone pequeno **A/Z** (A acima de Z) e uma seta para baixo.

Examine o campo de classificação e a direção de forma independente nas duas próximas seções.

## <a name="selecting-which-column-to-use-for-sorting"></a>Selecionando a coluna a ser usada para classificação
A barra amarela ao lado de **Classificar por SalesQuantity** no menu **Mais opções** indica que o visual está classificado pela coluna **SalesQuantity**. Classificar por outra coluna é fácil – basta selecionar as reticências para mostrar o menu de reticências e selecionar outra coluna.

Na imagem a seguir, selecionamos *DiscountAmount* como a coluna segundo a qual queremos classificar. Essa coluna é uma das linhas no visual, e não uma das barras. Esta é a aparência após selecionarmos **Classificar por DiscountAmount**.

![Classificar por DiscoutAmount](media/desktop-sort-by-column/sortbycolumn_3.png)

Observe como o visual foi alterado. Agora, os valores são ordenados do mais alto de DiscountAmount, neste visual da Fabrikam Inc., para a Northwind Traders, que tem o valor mais baixo. 

Mas e se quisermos classificar em ordem crescente em vez de decrescente? A próxima seção mostra como é fácil faz isso.

## <a name="selecting-the-sort-order---smallest-to-largest-largest-to-smallest"></a>Selecionando a ordem de classificação - menor para o maior, maior para o menor
Quando examinamos de forma mais detalhada o menu **Opções** da imagem anterior, vemos que o ícone ao lado de **Classificar por DiscountAmount** mostra **Z/A** (Z sobre A). Observe:

![Classificar do maior para o menor](media/desktop-sort-by-column/sortbycolumn_4.png)

Quando **Z/A** é exibido, significa que o visual está sendo classificado pela coluna selecionada em ordem do maior valor para o menor. Quer mudar? Sem problemas – basta tocar ou clicar no ícone **Z/A** e a ordem de classificação é alterada para **A/Z** e o visual (com base na coluna selecionada) é classificado do menor valor para o maior.

Este é o nosso mesmo visual, desta vez depois de tocar no ícone **Z/A** no item de menu **Classificar por DiscountAmount** para alterar sua ordem. Observe que a Northwind Traders agora é o primeiro fabricante listado, e Fabrikam Inc. é o último – uma classificação oposta à anterior.

![Classificar do menor para o maior](media/desktop-sort-by-column/sortbycolumn_5.png)

É possível classificar segundo qualquer coluna incluída no visual – poderíamos facilmente selecionar SalesQuantity como a coluna segunda a qual queremos classificar, com **Classificar por SalesQuantity**, para mostrar os fabricantes com mais vendas primeiro e ainda manter as outras colunas no visual da forma como se aplicam ao fabricante. Veja o visual com essas configurações.

![Classificar por SalesQuantity](media/desktop-sort-by-column/sortbycolumn_6.png)

## <a name="sort-using-the-sort-by-column-button"></a>Classificar usando o botão Classificar por Coluna
Há outra maneira de classificar os dados, usando o botão **Classificar por Coluna** na faixa de opções **Modelagem**.

![Botão Classificar por Coluna](media/desktop-sort-by-column/sortbycolumn_8.png)

Essa abordagem de classificação exige que você selecione uma coluna no painel **Campos** e, em seguida, selecione o botão **Classificar por Coluna** para escolher como (por qual coluna) você deseja classificar seu visual. Você deve selecionar a coluna (campo) que deseja classificar no painel **Campos** para habilitar o botão **Classificar por Coluna**. Caso contrário, o botão ficará inativo.

Vejamos um exemplo comum: você tem dados de cada mês do ano e deseja classificá-los com base em ordem cronológica. As etapas a seguir mostram como fazer isso.

1. Primeiro, observe que quando o visual é selecionado, mas nenhuma coluna é selecionada no painel **Campos**, o botão **Classificar por Coluna** fica inativo (esmaecido).
   
   ![Botão Classificar por Coluna inativo](media/desktop-sort-by-column/sortbycolumn_9.png)

2. Quando selecionamos a coluna pela qual queremos classificar no painel **Campos**, o botão **Classificar por Coluna** se torna ativo.
   
   ![Botão Classificar por Coluna ativo](media/desktop-sort-by-column/sortbycolumn_10.png)
3. Agora, com o visual selecionado, podemos selecionar *MonthOfYear*, em vez do padrão (*MonthName*), e o visual classifica na ordem que queremos: por mês do ano.
   
   ![Menu Classificar por Coluna](media/desktop-sort-by-column/sortbycolumn_11.png)

E isso é tudo. Lembre-se de que você deve selecionar uma coluna no painel **Campos** para o botão **Classificar por Coluna** ficar ativo.

## <a name="getting-back-to-default-column-for-sorting"></a>Voltando à coluna padrão para classificação
Você pode classificar segundo qualquer coluna que desejar, mas pode haver ocasiões em que você deseja que o visual retorne à coluna de classificação padrão. Sem problemas. Para um visual que tem uma coluna de classificação selecionada (como já vimos, uma coluna de classificação selecionada tem uma barra amarela ao seu lado no menu de reticências), basta abrir o menu **Mais opções** e selecionar a coluna novamente, e a visualização retornará à coluna de classificação padrão.

Por exemplo, este é nosso gráfico anterior:

![Visualização inicial](media/desktop-sort-by-column/sortbycolumn_6.png)

Quando voltamos ao menu e selecionamos **SalesQuantity** novamente, o visual volta ao padrão de ordem alfabética por **Fabricante**, conforme mostra a imagem a seguir.

![Ordem de classificação padrão](media/desktop-sort-by-column/sortbycolumn_7.png)

Com tantas opções para classificar os visuais, criando exatamente o gráfico ou imagem que você deseja é fácil.

