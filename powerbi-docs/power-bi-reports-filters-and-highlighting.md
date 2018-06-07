---
title: Sobre filtros e realce em relatórios do Power BI
description: Sobre filtros e realce em relatórios do Power BI
author: mihart
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 05/26/2018
ms.author: mihart
LocalizationGroup: Reports
ms.openlocfilehash: 7239351a7a9486aeeab53e4ab7fc5c3c3e877ff6
ms.sourcegitcommit: 80d6b45eb84243e801b60b9038b9bff77c30d5c8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34561438"
---
# <a name="about-filters-and-highlighting-in-power-bi-reports"></a>Sobre filtros e realce em relatórios do Power BI
Os ***Filtros*** removem tudo, menos os dados que você deseja se concentrar.  O ***Realce*** não filtra, pois não remove dados, mas realça um subconjunto dos dados visíveis; os dados não realçados permanecem visíveis, mas esmaecidos.

Há muitas maneiras diferentes de filtrar e realçar relatórios no Power BI. Colocar todas essas informações em um artigo seria confuso, portanto, nós as dividimos assim:

* Introdução aos filtros e realce (o artigo que você está lendo agora)
* As maneiras pelas quais você pode [criar e usar filtros e realce em Modo de exibição de edição/relatórios que você tem](power-bi-report-add-filter.md). Quando você tem permissões de edição para um relatório, pode criar, modificar e excluir filtros e realce em relatórios.
* As maneiras pelas quais você pode [usar filtros e realce em um relatório compartilhado com você ou no Modo de exibição de edição](service-reading-view-and-editing-view.md). O que você pode fazer é mais limitado, mas o Power BI ainda oferece uma ampla variedade de opções de filtragem e realce.  
* [Um tour detalhado dos controles de filtro e realce disponíveis no Modo de exibição de edição](power-bi-how-to-report-filter.md) incluindo uma visão detalhada dos tipos de filtros (por exemplo, data e hora, numérico, texto) e a diferença entre as opções básicas e avançadas.
* Agora que você aprendeu como filtros e realce funcionam por padrão, [saiba como alterar a maneira pela qual as visualizações em uma página filtram e realçam umas às outras](service-reports-visual-interactions.md)

> [!TIP]
> Como o Power BI sabe de que forma os dados estão relacionados?  Ele usa as relações entre diferentes tabelas e campos no [modelo de dados](https://support.office.com/article/Create-a-Data-Model-in-Excel-87e7a54c-87dc-488e-9410-5c75dbcb0f7b?ui=en-US&rs=en-US&ad=US) subjacente para fazer os itens em uma página de relatório interagir uns com os outros.
> 
> 

## <a name="introduction-to-filters-and-highlighting-in-reports-using-the-filters-pane"></a>Introdução aos filtros e realce em relatórios usando o painel Filtros
 Este artigo apresenta a você a filtragem e o realce no serviço do Power BI.  Mas a experiência é quase exatamente igual no Power BI Desktop.  

![](media/power-bi-reports-filters-and-highlighting/power-bi-add-filter-reading-view.png)

Filtros e realce podem ser aplicadas usando o painel **Filtros** ou fazendo seleções diretamente no relatório (ad-hoc, consulte a parte inferior da página). O painel Filtros mostra as tabelas e os campos usados no relatório e os filtros aplicados, caso haja algum. Os filtros são divididos em **Nível de página**, **Nível de relatório**, **Detalhamento** e **Nível visual**.  Você só verá filtros no nível visual se tiver selecionado uma visualização na tela de relatório.

> [!TIP]
> Se o filtro tiver a palavra **Todos** ao lado, isso significará que todo o campo está sendo incluído como filtro.  Por exemplo, **Cadeia(Todos)** na captura de tela abaixo informa que essa página de relatório inclui dados sobre cadeias de armazenamento.  Por outro lado, o filtro de nível de relatório ou **FiscalYear é 2013 ou 2014** informa que o relatório inclui somente dados para os anos fiscais de 2013 e 2014.
> 
> 

## <a name="filters-in-reading-view-versus-editing-view"></a>Filtros no Modo de Exibição de Leitura versus Modo de Exibição de Edição
Há dois modos de interagir com relatórios: [modo de exibição de Leitura e modo de exibição de Edição](service-reading-view-and-editing-view.md).  E os recursos de filtragem disponíveis para você dependem do modo no qual você está.

* No Modo de Exibição de Edição é possível adicionar filtros de relatório, de página, de detalhamento e de visual. Quando você salvar o relatório, os filtros serão salvos com o relatório – mesmo se você os abrir em um aplicativo móvel. Pessoas olhando para o relatório no Modo de Exibição de Leitura podem interagir com os filtros que você adicionou, mas não podem adicionar novos filtros.
* Np Modo de Exibição de Leitura, você pode interagir com todos os filtros já existentes no relatório e salvar a seleção feita por você.  Mas você não poderá adicionar novos filtros.

### <a name="the-filters-pane-in-reading-view"></a>O painel Filtros no Modo de exibição de leitura
Se você só tiver acesso a um relatório no Modo de Exibição de Leitura, o painel Filtros terá uma aparência semelhante a esta:

![](media/power-bi-reports-filters-and-highlighting/power-bi-filter-reading-view.png)

Então, essa página do relatório tem 6 filtros de nível de página e 1 filtro de nível de relatório.

Para ver se existem filtros de nível de visual, selecione um visual. Na imagem abaixo, o gráfico de bolhas tem 6 filtros aplicados.

![](media/power-bi-reports-filters-and-highlighting/power-bi-filter-visual-level.png)

No Modo de exibição de leitura, explore os dados modificando os filtros existentes. As alterações que você fizer serão salvas com o relatório, mesmo se você abrir o relatório em um aplicativo móvel. Saiba como no artigo [Modo de Exibição de Leitura e Modo de Exibição de Edição no serviço do Power BI](service-reading-view-and-editing-view.md)

### <a name="the-filters-pane-in-editing-view"></a>O painel Filtros no Modo de exibição de edição
Quando você tem permissões do proprietário para um relatório e o abre no Modo de exibição de edição, vê que **Filtros** é apenas um dos vários painéis de edição disponíveis.

![](media/power-bi-reports-filters-and-highlighting/power-bi-add-filter-editing-view.png)

Ao passo que no Modo de exibição de leitura (acima) vemos que essa página do relatório tem 6 filtros de nível de página e 1 filtro de nível de relatório. E ao selecionar o gráfico de bolhas, veríamos que ele tem 6 filtros de nível de visual aplicados.

Mas, no Modo de Exibição de Edição, há muito mais que podemos fazer com filtros e realce. A principal diferença é que podemos adicionar novos filtros. Saiba como fazer isso e muito mais no artigo [Adicionar um filtro a um relatório](power-bi-report-add-filter.md)

## <a name="ad-hoc-filtering-and-highlighting"></a>Filtragem e realce ad hoc
Selecione um campo na tela de relatório para filtrar e realçar o restante da página. Selecione um espaço vazio no mesmo visual para removê-lo. Esse tipo de filtragem e realce é uma maneira divertida de explorar rapidamente os impactos dos dados. Para ajustar como esse tipo de filtragem cruzada e realce cruzado funciona, consulte [Interações visuais](service-reports-visual-interactions.md).

![](media/power-bi-reports-filters-and-highlighting/power-bi-adhoc-filter.gif)

Quando você sair do relatório, as alterações serão salvas. Para desfazer a filtragem e retornar às definições padrão de filtragem, divisão, análise e classificação configuradas pelo autor do relatório, selecione **Redefinir para padrão** na barra de menus superior.

![](media/power-bi-reports-filters-and-highlighting/power-bi-reset-to-default.png)

## <a name="next-steps"></a>Próximas etapas
[Interact with filters and highlighting (in Reading View)](service-reading-view-and-editing-view.md) (Interagir com os filtros e realce (no Modo de Exibição de Leitura))

[Add a filter to a report (in Editing View)](power-bi-report-add-filter.md) (Adicionar um filtro a um relatório (no Modo de Exibição de Edição))

[Faça um tour pelo painel Filtros do relatório](power-bi-how-to-report-filter.md)

[Alterar como elementos visuais de relatórios executam filtro cruzado e realce cruzado entre si](service-reports-visual-interactions.md)

Leia mais sobre [relatórios no Power BI](service-reports.md)

Mais perguntas? [Experimente a Comunidade do Power BI](http://community.powerbi.com/)

