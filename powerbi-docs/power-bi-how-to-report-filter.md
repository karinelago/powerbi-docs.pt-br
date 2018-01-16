---
title: "Faça um tour pelo painel Filtros do Power BI"
description: "Como usar filtros de relatório"
services: powerbi
documentationcenter: 
author: mihart
manager: kfile
backup: 
editor: 
tags: 
qualityfocus: monitoring
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 10/29/2017
ms.author: mihart
ms.openlocfilehash: da3d4359fab37d1c5ee5f9d214cc5dba0fa9b680
ms.sourcegitcommit: 804ee18b4c892b7dcbd7d7d5d987b16ef16fc2bb
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/09/2018
---
# <a name="take-a-tour-of-the-report-filters-pane"></a>Faça um tour pelo painel Filtros do relatório
Este artigo oferece uma visão mais detalhada do painel Filtros do relatório. Você verá o painel no Modo de exibição de edição e no Modo de exibição de leitura em relatórios do Power BI.

Há muitas maneiras diferentes de filtrar dados no Power BI. Recomendamos que você leia [Sobre filtros e realce](power-bi-reports-filters-and-highlighting.md) primeiro.

## <a name="working-with-filters"></a>Trabalhar com filtros
Os relatórios podem ser abertos no [modo de exibição de Edição ou no modo de exibição de Leitura](service-reading-view-and-editing-view.md). No Modo de exibição de edição, os proprietários podem [adicionar filtros a um relatório](power-bi-report-add-filter.md) e esses filtros são salvos com o relatório. As pessoas que visualizam o relatório no modo de exibição de Leitura podem interagir com os filtros, mas não podem salvar as alterações de filtro no relatório.

## <a name="filters-in-reading-view"></a>Filtros no Modo de exibição de leitura
Quando um relatório é aberto no Modo de exibição de leitura, o painel Filtros é exibido no lado direito da tela do relatório. Caso não veja o painel, selecione a seta no canto superior direito para expandi-lo.

Neste exemplo, selecionamos um visual que tem 6 filtros. A página de relatório também tem filtros, listados sob o título **Filtros de nível de página**. Há um [Filtro de detalhamento](power-bi-report-add-filter.md) e o relatório inteiro também tem um filtro: **FiscalYear** é 2013 ou 2014.

![](media/power-bi-how-to-report-filter/power-bi-filter-list.png)

Alguns filtros têm a palavra **Todos** ao seu lado, o que significa que todos os valores estão sendo incluído no filtro.  Por exemplo, **Cadeia(Todos)** na captura de tela abaixo informa que essa página de relatório inclui dados sobre cadeias de armazenamento.  Por outro lado, o filtro de nível de relatório ou **FiscalYear é 2013 ou 2014** informa que o relatório inclui somente dados para os anos fiscais de 2013 e 2014.

Qualquer pessoa que exibir este relatório pode interagir com esses filtros.

* Exiba os detalhes do filtro focalizando e selecionando a seta ao lado do filtro.
  
   ![](media/power-bi-how-to-report-filter/power-bi-expan-filter.png)
* Altere o filtro, por exemplo, altere **Lindseys** para **Fashions Direct**.
  
     ![](media/power-bi-how-to-report-filter/power-bi-filter-chain.png)
* Exclua o filtro selecionando o **x** ao lado do nome do filtro.
  
  A exclusão de um filtro o remove da lista, mas não exclui os dados do relatório.  Por exemplo, se você excluir o filtro **FiscalYear é 2013 ou 2014**, os dados do ano fiscal ainda permanecerão no relatório, mas ele não será mais filtrado para mostrar somente 2013 e 2014; mostrará todos os anos fiscais contidos nos dados.  No entanto, depois de excluir o filtro, você não poderá modificá-lo novamente, já que ele é removido da lista. Uma opção melhor é limpar o filtro selecionando o ícone de borracha ![](media/power-bi-how-to-report-filter/power-bi-eraser-icon.png).
  
  ![](media/power-bi-how-to-report-filter/power-bi-delete-filter.png)

## <a name="filters-in-editing-view"></a>Filtros no Modo de exibição de edição
Quando um relatório é aberto no Modo de exibição de edição, o painel Filtros é exibido no lado direito da tela do relatório na metade inferior do **Painel de visualização**. Caso não veja o painel, selecione a seta no canto superior direito para expandi-lo.

![](media/power-bi-how-to-report-filter/power-bi-all-filters.png).  

Se nenhum visual for selecionado na tela, o painel Filtros exibirá apenas os filtros que se aplicam à página inteira do relatório ou a todo o relatório e a qualquer filtro de detalhamento (se tiverem sido definidos). No exemplo abaixo, nenhum visual foi selecionado e não existem filtros de nível de página nem de detalhamento, mas há um filtro de nível de relatório.  

![](media/power-bi-how-to-report-filter/power-bi-no-visual.png)  

Se um visual é selecionado na tela, você também verá os filtros que se aplicam a apenas àquele visual:   

![](media/power-bi-how-to-report-filter/power-bi-visual-filters.png)

Para exibir opções de um filtro específico, selecione a seta para baixo ao lado do nome do filtro.  No exemplo abaixo, o filtro de nível de relatório é definido como 2013 e 2014. E este é um exemplo de **filtragem básica**.  Para exibir as opções avançadas, selecione **Filtragem Avançada**.

![](media/power-bi-how-to-report-filter/pbi_filterlistdropdown.jpg)

## <a name="clear-a-filter"></a>Limpar um filtro
 No modo de filtragem avançado ou básico, selecione o ícone de borracha ![](media/power-bi-how-to-report-filter/pbi_erasericon.jpg) para restaurar o filtro. 

## <a name="add-a-filter"></a>Adicionar um filtro
* No Modo de Edição de Exibição, adicione um filtro a um visual, página, detalhamento ou relatório selecionando um campo no painel Campos e arrastando-o para o filtro apropriado, no qual você verá as palavras **Arrastar campos aqui**. Após a adição de um campo como um filtro, ajuste-o usando os controles de filtragem Básica e Avançada (descritos abaixo).

Arrastar um novo campo na área Filtro de nível visual não adicionará esse campo ao visual, mas permitirá que você filtre esse visual com o novo campo. No exemplo a seguir, **Cadeia** é adicionado como um novo filtro para o visual. Observe que apenas adicionar **Cadeia** como um filtro não altera o visual até que você use os controles Básico ou Avançado de filtragem.

    ![](media/power-bi-how-to-report-filter/power-bi-visual-filter.gif)

* Todos os campos usados para criar uma visualização também estão disponíveis como filtros. Primeiro, selecione um visual para ativá-lo. Os campos usados no visual são listados no painel Visualizações (se você estiver no Modo de Edição de Exibição) e no painel Filtros sob o título de **Filtros de nível visual**.
  
   ![](media/power-bi-how-to-report-filter/power-bi-visual-filter.png)  
  
   Ajuste todos os campos usando os controles de filtragem Básica e Avançada (descritos abaixo).

## <a name="types-of-filters-text-field-filters"></a>Tipos de filtros: filtros de campo de texto
### <a name="list-mode"></a>Modo de lista
Marcar uma caixa de seleção ou selecionar ou demarcar o valor. A caixa de seleção **Todos** pode ser usada para alternar o estado de todas as caixas de seleção ativadas ou desativadas. As caixas de seleção representam todos os valores disponíveis para esse campo.  À medida que você ajusta o filtro, o ajuste é atualizado para refletir suas escolhas. 

![](media/power-bi-how-to-report-filter/pbi_restatement.png)

Observe como a reformulação agora diz "é Amarilla ou Carretera"

### <a name="advanced-mode"></a>Modo avançado
Selecione **Filtragem avançada** para alternar para o modo avançado. Use as caixas de texto e controles de lista suspensa para identificar quais campos serão incluídos. Escolhendo entre **E** e **Ou**, você pode criar expressões de filtro complexas. Selecione o botão **Aplicar filtro** ao definir os valores desejados.  

![](media/power-bi-how-to-report-filter/aboutfilters.png)

## <a name="types-of-filters-numeric-field-filters"></a>Tipos de filtros: filtros de campo numérico
### <a name="list-mode"></a>Modo de lista
Se os valores são finitos, selecionar o nome do campo exibe uma lista.  Veja **Filtros de campo de texto** &gt; **Modo de lista** acima para obter ajuda sobre como usar caixas de seleção.   

### <a name="advanced-mode"></a>Modo avançado
Se os valores são infinitos ou representam um intervalo, selecionar o nome do campo abre o modo de filtro avançado. Use a lista suspensa e as caixas de texto para especificar um intervalo de valores que você deseja ver. 

![](media/power-bi-how-to-report-filter/pbi_dropdown-and-text.png)

Escolhendo entre **E** e **Ou**, você pode criar expressões de filtro complexas. Selecione o botão **Aplicar filtro** ao definir os valores desejados.

## <a name="types-of-filters-date-and-time"></a>Tipos de filtros: data e hora
### <a name="list-mode"></a>Modo de lista
Se os valores são finitos, selecionar o nome do campo exibe uma lista.  Veja **Filtros de campo de texto** &gt; **Modo de lista** acima para obter ajuda sobre como usar caixas de seleção.   

### <a name="advanced-mode"></a>Modo avançado
Se os valores de campo representam a data ou hora, você pode especificar uma hora de início/término quando usar os filtros de data/hora.  

![](media/power-bi-how-to-report-filter/pbi_date-time-filters.png)

## <a name="next-steps"></a>Próximas etapas
[Filtros e realce em relatórios](power-bi-reports-filters-and-highlighting.md)  
[Interação com os filtros e realce no relatório de exibição de leitura](service-reading-view-and-editing-view.md)  
[Criar filtros no Modo de exibição de edição do relatório](power-bi-report-add-filter.md)  
[Alterar como elementos visuais de relatórios executam filtro cruzado e realce cruzado entre si](service-reports-visual-interactions.md)

Leia mais sobre [relatórios no Power BI](service-reports.md)  
[Power BI – conceitos básicos](service-basic-concepts.md)

Mais perguntas? [Experimente a Comunidade do Power BI](http://community.powerbi.com/)

