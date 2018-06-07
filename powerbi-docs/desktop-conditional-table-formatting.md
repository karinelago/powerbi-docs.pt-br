---
title: Formatação de tabela condicional no Power BI Desktop
description: Aplicar formatação personalizada a tabelas
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 05/17/2018
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: 70aa61d6a02bea1b7058a68b20718008ace1b8c8
ms.sourcegitcommit: 80d6b45eb84243e801b60b9038b9bff77c30d5c8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34480878"
---
# <a name="conditional-formatting-in-tables"></a>Formatação condicional em tabelas 
Com a formatação condicional para tabelas, você pode especificar cores personalizadas para as células com base nos valores das células ou em outros valores ou campos, inclusive usando cores de gradiente. Também é possível exibir valores de célula com barras de dados. 

Para acessar a formatação condicional, em **Campos** também do painel **Visualizações** no Power BI Desktop, selecione a seta para baixo ao lado do valor em **Valores** que você deseja formatar (ou clique com o botão direito do mouse no campo). Você pode gerenciar somente a formatação condicional para campos na área **Valores** também em **Campos**.

![Menu Formatação condicional](media/desktop-conditional-table-formatting/table-formatting-0-popup-menu.png)

As seções a seguir descrevem cada uma dessas três opções de formatação condicional. Uma ou mais opções podem ser combinadas em uma única coluna de tabela.

> [!NOTE]
> Quando aplicada a uma tabela, a formatação condicional substitui quaisquer estilos de tabela personalizados aplicados a células formatadas condicionalmente.

Para remover a formatação condicional de uma visualização, basta clicar com o botão direito do mouse no campo novamente e selecionar **Remover formatação condicional** e o tipo de formatação a ser removida.

![Menu Remover formatação condicional](media/desktop-conditional-table-formatting/table-formatting-1-remove.png)

## <a name="background-color-scales"></a>Escalas de cores da tela de fundo

Selecionar **Formatação condicional** e **Escalas de cor da tela de fundo** exibe a caixa de diálogo a seguir.

![Caixa de diálogo Escalas de cor da tela de fundo](media/desktop-conditional-table-formatting/table-formatting-1-default-dialog.png)

É possível selecionar um campo do modelo de dados para basear as cores definindo **Cor baseada em** nesse campo. Além disso, você pode especificar o tipo de agregação para o campo selecionado com o valor **Resumo**. O campo a ser colorido é especificado no campo **Aplicar cor a**. Assim, você tem o controle. É possível aplicar a formatação condicional a campos de data e de texto, desde que você escolha um valor numérico como a base da formatação.

![Cor baseada em campo](media/desktop-conditional-table-formatting/table-formatting-1-apply-color-to.png)

Para usar valores de cor discretos para intervalos de valor, selecione **Colorir por regras**. Para usar um espectro de cores, deixe **Colorir por regras** desmarcado. 

![Caixa de diálogo Escalas de cor da tela de fundo](media/desktop-conditional-table-formatting/table-formatting-1-color-by-rules-dialog.png)

### <a name="color-by-rules"></a>Colorir por regras

Quando você seleciona **Colorir por regras**, é possível inserir um ou mais intervalos de valores, cada um com um conjunto de cores.  Cada intervalo de valor começa com uma condição de *valor If*, uma condição de valor *and* e uma cor.

![Intervalo de valor de Colorir por regras](media/desktop-conditional-table-formatting/table-formatting-1-color-by-rules-if-value.png)

Células de tabela com valores em cada intervalo são preenchidas com determinada cor. Há três regras na figura a seguir.

![Exemplo de Colorir por regras](media/desktop-conditional-table-formatting/table-formatting-1-color-by-rules.png)

A tabela de exemplo agora tem esta aparência:

![Tabela de exemplo com Colorir por regras](media/desktop-conditional-table-formatting/table-formatting-1-color-by-rules-table.png)


### <a name="color-minimum-to-maximum"></a>Valores mínimo e máximo de cor

Você pode configurar os valores *mínimo* e *máximo* e as cores. Se selecionar a caixa **Divergente**, você também poderá configurar um valor opcional para o *Centro*.

![Botão Divergente](media/desktop-conditional-table-formatting/table-formatting-1-diverging.png)

A tabela de exemplo agora tem esta aparência:

![Tabela de exemplo com cores divergentes](media/desktop-conditional-table-formatting/table-formatting-1-diverging-table.png)

## <a name="font-color-scales"></a>Escalas de cores de fonte

Selecionar **Formatação condicional** e **Escalas de cores de fonte** exibe a caixa de diálogo a seguir. Essa caixa de diálogo é semelhante a **Escalas de cor da tela de fundo**, mas altera a cor da fonte em vez da cor da tela de fundo da célula.

![Caixa de diálogo Escalas de cores de fonte](media/desktop-conditional-table-formatting/table-formatting-2-diverging.png)

A tabela de exemplo agora tem esta aparência:

![Tabela de exemplo com escalas de cores de fonte](media/desktop-conditional-table-formatting/table-formatting-2-table.png)

## <a name="data-bars"></a>Barras de dados

Selecionar **Formatação condicional** e **Barras de dados** exibe a caixa de diálogo a seguir. 

![Caixa de diálogo Barras de dados](media/desktop-conditional-table-formatting/table-formatting-3-default.png)

Por padrão, a opção **Mostrar somente a barra** é desmarcada e, portanto, a célula da tabela mostra a barra e o valor real.

![Tabela de exemplo com barras de dados e valores](media/desktop-conditional-table-formatting/table-formatting-3-default-table.png)

Se opção **Mostrar somente a barra** estiver marcada, a célula da tabela mostrará apenas a barra.

![Tabela de exemplo com apenas as barras de dados](media/desktop-conditional-table-formatting/table-formatting-3-default-table-bars.png)
