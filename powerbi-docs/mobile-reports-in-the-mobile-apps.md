---
title: "Explorar relatórios nos aplicativos móveis do Power BI"
description: "Saiba mais sobre como exibir e interagir com relatórios nos aplicativos móveis do Power BI no telefone ou tablet. Você cria relatórios no serviço do Power BI ou Power BI Desktop e interage com eles nos aplicativos móveis. "
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
ms.date: 10/13/2017
ms.author: maggies
ms.openlocfilehash: 3515a57f88db1c8a7b12706680c0aade8b2cdbfa
ms.sourcegitcommit: 284b09d579d601e754a05fba2a4025723724f8eb
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/15/2017
---
# <a name="explore-reports-in-the-power-bi-mobile-apps"></a>Explorar relatórios nos aplicativos móveis do Power BI
Aplica-se a:

| ![iPhone](media/mobile-reports-in-the-mobile-apps/ios-logo-40-px.png) | ![iPad](media/mobile-reports-in-the-mobile-apps/ios-logo-40-px.png) | ![Telefone Android](media/mobile-reports-in-the-mobile-apps/android-logo-40-px.png) | ![Tablet Android](media/mobile-reports-in-the-mobile-apps/android-logo-40-px.png) | ![Dispositivos Windows 10](media/mobile-reports-in-the-mobile-apps/win-10-logo-40-px.png) |
|:--- |:--- |:--- |:--- |:--- |
| iPhones |iPads |Telefones Android |Tablets Android |Dispositivos Windows 10 |

Um relatório do Power BI é uma exibição interativa de seus dados, com visuais representando diferentes descobertas e informações obtidas desses dados. A exibição de relatórios nos aplicativos móveis do Power BI é a terceira etapa de um processo de três etapas.

1. [Criar relatórios no Power BI Desktop](desktop-report-view.md). Você pode até mesmo [otimizar um relatório para telefones](mobile-apps-view-phone-report.md) no Power BI Desktop. 
2. Publicar esses relatórios no serviço do Power BI [(https://powerbi.com)](https://powerbi.com) ou no [Servidor de Relatório do Power BI](report-server/get-started.md).  
3. Em seguida, interagir com esses relatórios nos aplicativos móveis do Power BI.

## <a name="open-a-power-bi-report-in-the-mobile-app"></a>Abrir um relatório do Power BI no aplicativo móvel
Os relatórios do Power BI são armazenados em locais diferentes no aplicativo móvel, dependendo de onde eles foram obtidos. Eles podem estar em Aplicativos, Compartilhado comigo, Espaços de Trabalho (incluindo Meu Espaço de Trabalho) ou em um servidor de relatório. Às vezes, você percorre um dashboard relacionado para obter um relatório e, às vezes, ele é listado.

* Em um dashboard, toque nas reticências (...) no canto superior direito de um bloco > **Abrir relatório**.
  
  ![Abrir relatório](media/mobile-reports-in-the-mobile-apps/power-bi-android-open-report-tile.png)
  
  Nem todos os blocos têm a opção de serem abertos em um relatório. Por exemplo, os blocos criados por meio de uma pergunta na caixa de P e R não abrem relatórios quando você toca neles. 
  
  Em um telefone, o relatório é aberto no modo paisagem, a menos que seja [otimizado para exibição em um telefone](mobile-reports-in-the-mobile-apps.md#view-reports-optimized-for-phones).
  
  ![Relatório para telefone no modo paisagem](media/mobile-reports-in-the-mobile-apps/power-bi-iphone-report-landscape.png)

## <a name="view-reports-optimized-for-phones"></a>Exibir relatórios otimizados para telefones
Os autores de relatório do Power BI podem criar um layout de relatório especificamente otimizado para telefones. Em uma lista de relatórios, um relatório otimizado tem um ícone especial ![Ícone de relatório para telefone](media/mobile-reports-in-the-mobile-apps/power-bi-phone-report-icon.png):

![Abrir relatório para telefone](media/mobile-reports-in-the-mobile-apps/power-bi-android-phone-report.png)

Quando você exibe esse relatório em um telefone, ele é aberto no modo retrato.

![Relatório no modo de exibição de retrato](media/mobile-reports-in-the-mobile-apps/07-power-bi-phone-report-portrait.png)

Um relatório pode ter uma combinação de páginas que são e não são otimizadas para telefones. Nesse caso, quando você percorre o relatório, a exibição será alternada de retrato para paisagem em cada página.

Leia mais sobre os [relatórios otimizados para exibição do telefone](mobile-apps-view-phone-report.md).

## <a name="use-slicers-to-filter-a-report-page"></a>Usar segmentações para filtrar uma página de relatório
Ao criar um relatório no serviço do Power BI [(https://powerbi.com)](https://powerbi.com), tenha em mente que, em um telefone, não é possível ver o painel Filtros, mas é possível [consultar segmentações em uma página de relatório](power-bi-visualization-slicers.md). Adicione segmentações a um relatório, de forma que você e seus colegas possam usar as segmentações para filtrar a página em um telefone.

* Quando você seleciona um valor em uma segmentação na página do relatório, ela filtra os outros visuais da página.
  
  ![Segmentação de relatório](media/mobile-reports-in-the-mobile-apps/power-bi-android-tablet-report-slicer.png)
  
  Nesta ilustração, a segmentação está filtrando o gráfico de colunas para mostrar apenas os valores de julho.

## <a name="cross-filter-and-highlight-a-power-bi-report-page"></a>Realizar filtragem cruzada e destacar uma página de relatório do Power BI
Quando você seleciona um valor em um visual, ele não filtra os outros visuais. Ele realça os valores relacionados nos outros visuais.

* Toque em um valor de um visual.
  
  ![Realizar filtragem cruzada de uma página](media/mobile-reports-in-the-mobile-apps/power-bi-android-tablet-report-highlight.png)
  
  Tocar na coluna Grande de um visual realça os valores relacionados nos outros visuais. 

## <a name="sort-a-visual-on-an-ipad-or-a-tablet"></a>Classificar um visual em um iPad ou tablet
* Toque no gráfico, toque nas reticências (**...**) e toque no nome do campo.
  
   ![Classificar um visual](media/mobile-reports-in-the-mobile-apps/power-bi-android-tablet-report-sort.png)
* Para inverter a ordem de classificação, toque nas reticências (**...**) novamente e, depois, toque no mesmo nome de campo novamente.

## <a name="drill-down-and-up-in-a-visual-on-an-ipad-or-a-tablet"></a>Fazer drill down e drill up em um visual em um iPad ou tablet
Se um autor de relatório tiver adicionado essa funcionalidade a um visual, em um iPad ou tablet, você poderá fazer drill down em um visual para ver os valores que compõem uma parte dele. Você [adiciona o drill down em um visual](power-bi-visualization-drill-down.md) no Power BI Desktop ou no serviço do Power BI. 

> [!NOTE]
> Atualmente, o drill down não funciona em mapas no iPad ou em tablets.
> 
> 

* Toque em um visual. Se ele tiver setas para cima e para baixo nos cantos superiores ![Ícones de Drill up e Drill down](media/mobile-reports-in-the-mobile-apps/power-bi-mobile-drill-up-down.png), então você poderá fazer drill down. Para fazer drill down em um valor, toque na seta no canto superior direito e, em seguida, toque em um valor do visual &#151; nesse caso, na bolha FD-04 azul-escura.
  
  ![Fazer drill down em um visual](media/mobile-reports-in-the-mobile-apps/power-bi-mobile-drill-down-one.png)
* Para fazer drill up novamente, toque na seta para cima no canto superior esquerdo.
  
  ![Fazer drill up](media/mobile-reports-in-the-mobile-apps/power-bi-mobile-drill-up.png)

## <a name="go-back-to-my-workspace"></a>Voltar para Meu Espaço de Trabalho
* Toque na seta ao lado do nome do relatório > toque em **Meu Espaço de Trabalho**.
  
  ![Retornar para a parte superior](media/mobile-reports-in-the-mobile-apps/power-bi-iphone-report-back.png)

## <a name="next-steps"></a>Próximas etapas
* [Exibir e interagir com relatórios do Power BI otimizados para seu telefone](mobile-apps-view-phone-report.md)
* [Criar uma versão de um relatório otimizado para telefones](desktop-create-phone-report.md)
* Dúvidas? [Experimente perguntar à Comunidade do Power BI](http://community.powerbi.com/)

