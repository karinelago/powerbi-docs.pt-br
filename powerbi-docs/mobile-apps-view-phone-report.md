---
title: "Exibir relatórios do Power BI otimizados para seu telefone"
description: "Leia sobre a interação com páginas de relatório otimizadas para exibição em aplicativos do Power BI."
services: powerbi
documentationcenter: 
author: maggiesMSFT
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
ms.date: 01/04/2018
ms.author: maggies
ms.openlocfilehash: 4f3441e2f933ee8964fc77e3166aeede97bcfba9
ms.sourcegitcommit: 25489cf87c31fc107a5337fa1dd36506897c4bbb
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/05/2018
---
# <a name="view-power-bi-reports-optimized-for-your-phone"></a>Exibir relatórios do Power BI otimizados para seu telefone

Aplica-se a:

| ![iPhone](media/mobile-apps-view-phone-report/ios-logo-40-px.png) | ![Telefone Android](media/mobile-apps-view-phone-report/android-logo-40-px.png) |
|:--- |:--- |
| iPhones |Telefones Android |

Quando você cria um relatório do Power BI no Power BI Desktop, você também pode [criar uma versão desse relatório otimizada para exibição](desktop-create-phone-report.md) no aplicativo do Power BI em um telefone.

Em seguida, quando você abrir um relatório do Power BI em um telefone, o Power BI detectará se o relatório foi otimizado para telefones e abrirá automaticamente o relatório otimizado no modo de exibição de retrato.

![Relatório no modo retrato](media/mobile-apps-view-phone-report/07-power-bi-phone-report-portrait.png)

Se um relatório otimizado para telefone não existir, o relatório será aberto, mas no modo de exibição de paisagem não otimizada. Mesmo em um relatório otimizado para telefones, se você mudar a orientação do telefone, o relatório será aberto na exibição não otimizada com o layout original do relatório. Se somente algumas páginas forem otimizadas, você encontrará uma mensagem na exibição de retrato, indicando que o relatório está disponível em paisagem.

![Página de relatório não otimizada](media/mobile-apps-view-phone-report/06-power-bi-phone-report-page-not-optimized.png)

Todos os outros recursos de relatórios do Power BI ainda funcionam em relatórios otimizados para telefones. Leia mais sobre o que você pode fazer em:

* [Relatórios sobre iPhones](mobile-reports-in-the-mobile-apps.md). 
* [Relatórios sobre telefones Android](mobile-reports-in-the-mobile-apps.md).

## <a name="filter-the-report-page-on-a-phone"></a>Filtrar a página de relatório em um telefone
Se um relatório otimizado para telefone tiver filtros definidos, quando ele for exibido em um telefone, será possível utilizar esses filtros. 

1. Toque no ícone de filtro ![Ícone de filtro do telefone](media/mobile-apps-view-phone-report/power-bi-phone-filter-icon.png) na parte inferior da página. 
2. Use a filtragem básica ou avançada para ver os resultados em que você está interessado.
   
    ![Filtro avançado do relatório de telefone do BI do telefone](media/mobile-apps-view-phone-report/power-bi-iphone-advanced-filter-toronto.gif)

## <a name="cross-highlight-visuals"></a>Elementos visuais com realce cruzado
Elementos visuais com realce cruzado em relatórios de telefone funcionam da mesma forma que no serviço do Power BI e nos relatórios em telefones no modo paisagem: ao selecionar seus dados em um elemento visual, dados relacionados são realçados em outros elementos visuais nessa página.

Leia mais sobre [filtragem e realce no Power BI](power-bi-reports-filters-and-highlighting.md).

## <a name="select-visuals"></a>Selecionar elementos visuais
Em relatórios de telefone quando você seleciona um elemento visual, o relatório realça o elemento visual e foca nele, neutralizando gestos da tela.

Com o visual selecionado, você executar ações como rolar no elemento visual. Para cancelar a seleção de um elemento visual, basta tocar em qualquer parte fora da área do elemento visual.

## <a name="open-visuals-in-focus-mode"></a>Abrir elementos visuais em modo de foco
Os relatórios de telefone também oferecem um modo de foco para que você possa obter uma exibição maior de um único visual e possa explorar o visual e o relatório.

* Em um relatório de telefone, toque no botão de reticências (**...** ) no canto superior direito de um visual > **Expandir para o modo de foco**.
  
    ![Expandir para o modo de foco](media/mobile-apps-view-phone-report/power-bi-phone-report-focus-mode.png)

O que você faz no modo de foco é levado para a tela e vice-versa, para uma experiência de exploração direta. Por exemplo, se você realçar um valor em um elemento visual e depois retorna para o relatório inteiro, o relatório como um todo será filtrado para o valor realçado no elemento visual.

Algumas ações somente são possíveis no modo de foco, devido às restrições de tamanho de tela:

* **Detalhar** as informações exibidas em um visual. Leia mais sobre como [fazer drill-down e up](mobile-apps-view-phone-report.md#drill-down-in-a-visual) em um relatório de telefone abaixo.
* **Classifique** os valores no elemento visual.
* **Reverter**: desmarque as etapas de exploração que você efetuou em um elemento visual e reverter para a definição estabelecida quando o relatório foi criado.
  
    Para limpar toda a exploração de um visual, toque no botão de reticências (**...** ) > **Reverter**.
  
    ![Reverter](media/mobile-apps-view-phone-report/power-bi-phone-report-revert-levels.png)
  
    A reversão está disponível no nível do relatório; desmarque todas as explorações de todos os elementos visuais ou no visual nível, desmarcando toda a exploração do elemento visual específico selecionado.   

## <a name="drill-down-in-a-visual"></a>Fazer drill down em um visual
Se os níveis hierárquicos forem definidos em um visual, você poderá fazer drill down nas informações detalhadas exibidas em um visual e, em seguida, fazer backup. [Adicione o drill-down em um visual](power-bi-visualization-drill-down.md) no serviço do Power BI ou no Power BI Desktop. O drill-down funciona apenas em relatórios do Power BI otimizados para telefone quando você os exibe em um telefone. 

1. Em um relatório em um telefone, toque no botão de reticências (**...** ) no canto superior direito > **Expandir para o modo de foco**.
   
    ![Expandir para o modo de foco](media/mobile-apps-view-phone-report/power-bi-phone-report-focus-mode.png)
   
    Neste exemplo, as barras mostram os valores de estados.
2. Toque no ícone Explorar ![ícone Explorar](media/mobile-apps-view-phone-report/power-bi-phone-report-explore-icon.png) no canto inferior esquerdo.
   
    ![Modo de exploração](media/mobile-apps-view-phone-report/power-bi-phone-report-explore-mode.png)
3. Toque em **Mostrar o próximo nível** ou em **Expandir para o próximo nível**.
   
    ![Expandir para o próximo nível](media/mobile-apps-view-phone-report/power-bi-phone-report-expand-levels.png)
   
    Agora as barras mostram os valores para as cidades.
   
    ![Níveis expandidos](media/mobile-apps-view-phone-report/power-bi-phone-report-expanded-levels.png)
4. Se você tocar na seta no canto superior esquerdo, você voltará ao relatório de telefone com os valores ainda expandidos para um nível inferior.
   
    ![Ainda expandido para um nível inferior](media/mobile-apps-view-phone-report/power-bi-back-to-phone-report-expanded-levels.png)
5. Para voltar ao nível original, toque no botão de reticências (**...** ) novamente > **Reverter**.
   
    ![Reverter](media/mobile-apps-view-phone-report/power-bi-phone-report-revert-levels.png)

## <a name="next-steps"></a>Próximas etapas
* [Criar relatórios otimizados para os aplicativos de telefone do Power BI](desktop-create-phone-report.md)
* [Criar uma exibição de telefone de um dashboard no Power BI](service-create-dashboard-mobile-phone-view.md)
* [Criar visuais responsivos otimizados para qualquer tamanho](desktop-create-responsive-visuals.md)
* Mais perguntas? [Experimente perguntar à Comunidade do Power BI](http://community.powerbi.com/)

