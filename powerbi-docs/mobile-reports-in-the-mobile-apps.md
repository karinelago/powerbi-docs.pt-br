---
title: Explorar relatórios nos aplicativos móveis do Power BI
description: Saiba mais sobre como exibir e interagir com relatórios nos aplicativos móveis do Power BI no telefone ou tablet. Você cria relatórios no serviço do Power BI ou Power BI Desktop e interage com eles nos aplicativos móveis.
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-mobile
ms.topic: conceptual
ms.date: 06/05/2018
ms.author: maggies
ms.openlocfilehash: 5b4d5ea7970dd44cfebadca6935452688515aef5
ms.sourcegitcommit: b25ae650643b0a62f33d7c1741307137b9cec316
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/05/2018
ms.locfileid: "34799408"
---
# <a name="explore-reports-in-the-power-bi-mobile-apps"></a>Explorar relatórios nos aplicativos móveis do Power BI
Aplica-se a:

| ![iPhone](media/mobile-reports-in-the-mobile-apps/ios-logo-40-px.png) | ![iPad](media/mobile-reports-in-the-mobile-apps/ios-logo-40-px.png) | ![Telefone Android](media/mobile-reports-in-the-mobile-apps/android-logo-40-px.png) | ![Tablet Android](media/mobile-reports-in-the-mobile-apps/android-logo-40-px.png) | ![Dispositivos Windows 10](media/mobile-reports-in-the-mobile-apps/win-10-logo-40-px.png) |
|:--- |:--- |:--- |:--- |:--- |
| iPhones |iPads |Telefones Android |Tablets Android |Dispositivos Windows 10 |

Um relatório do Power BI é uma exibição interativa de seus dados, com visuais representando diferentes descobertas e informações obtidas desses dados. A exibição de relatórios nos aplicativos móveis do Power BI é a terceira etapa de um processo de três etapas.

1. [Criar relatórios no Power BI Desktop](desktop-report-view.md). Você pode até mesmo [otimizar um relatório para telefones](mobile-apps-view-phone-report.md) no Power BI Desktop. 
2. Publique esses relatórios para o serviço do Power BI [(https://powerbi.com)](https://powerbi.com) ou [Servidor de Relatórios do Power BI](report-server/get-started.md).  
3. Em seguida, interagir com esses relatórios nos aplicativos móveis do Power BI.

## <a name="open-a-power-bi-report-in-the-mobile-app"></a>Abrir um relatório do Power BI no aplicativo móvel
Os relatórios do Power BI são armazenados em locais diferentes no aplicativo móvel, dependendo de onde eles foram obtidos. Eles podem estar em Aplicativos, Compartilhado comigo, Espaços de Trabalho (incluindo Meu Espaço de Trabalho) ou em um servidor de relatório. Às vezes, você percorre um dashboard relacionado para obter um relatório e, às vezes, ele é listado.

* Em um dashboard, toque nas reticências (...) no canto superior direito de um bloco > **Abrir relatório**.
  
  ![Abrir relatório](media/mobile-reports-in-the-mobile-apps/power-bi-android-open-report-tile.png)
  
  Nem todos os blocos têm a opção de serem abertos em um relatório. Por exemplo, os blocos criados por meio de uma pergunta na caixa de P e R não abrem relatórios quando você toca neles. 
  
  Em um telefone, o relatório é aberto no modo paisagem, a menos que seja [otimizado para exibição em um telefone](mobile-reports-in-the-mobile-apps.md#view-reports-optimized-for-phones).
  
  ![Relatório para telefone no modo paisagem](media/mobile-reports-in-the-mobile-apps/power-bi-iphone-report-landscape.png)

## <a name="view-reports-optimized-for-phones"></a>Exibir relatórios otimizados para telefones
Os autores de relatório do Power BI podem criar um layout de relatório especificamente otimizado para telefones. As páginas de relatório otimizadas para telefones têm funcionalidade adicionada: por exemplo, você pode fazer uma busca detalhada de visuais e classificá-los, além de acessar os [filtros que o autor do relatório adicionou à página do relatório](mobile-apps-view-phone-report.md#filter-the-report-page-on-a-phone). O relatório é aberto no seu telefone, filtrado para os valores filtrados no relatório na Web, com uma mensagem de que há filtros ativos na página. É possível alterar os filtros no seu telefone.

Em uma lista de relatórios, um relatório otimizado tem um ícone especial ![Ícone de relatório para telefone](media/mobile-reports-in-the-mobile-apps/power-bi-phone-report-icon.png):

![Abrir relatório para telefone](media/mobile-reports-in-the-mobile-apps/power-bi-android-phone-report.png)

Quando você exibe esse relatório em um telefone, ele é aberto no modo retrato.

![Relatório no modo de exibição de retrato](media/mobile-reports-in-the-mobile-apps/07-power-bi-phone-report-portrait.png)

 Um relatório pode ter uma combinação de páginas que são e não são otimizadas para telefones. Nesse caso, quando você percorre o relatório, a exibição será alternada de retrato para paisagem em cada página.

Leia mais sobre os [relatórios otimizados para exibição do telefone](mobile-apps-view-phone-report.md).

## <a name="use-slicers-to-filter-a-report"></a>Usar segmentações para filtrar um relatório
Ao criar um relatório no Power BI Desktop ou serviço Power BI, [adicione segmentações a uma página do relatório](power-bi-visualization-slicers.md). Você e seus colegas podem usar as segmentações para filtrar a página em um navegador e nos aplicativos móveis. Quando você exibir o relatório em um telefone, poderá ver e interagir com as segmentações em modo paisagem e em uma página otimizada para o modo de retrato do telefone. Se você selecionar um valor em uma segmentação ou filtro no navegador, o valor será selecionado quando você visualizar a página no aplicativo móvel também. Você verá uma mensagem informando que existem filtros ativos na página.  

* Quando você seleciona um valor em uma segmentação na página do relatório, ela filtra os outros visuais da página.
  
  ![Segmentação de relatório](media/mobile-reports-in-the-mobile-apps/power-bi-android-tablet-report-slicer.png)
  
  Nesta ilustração, a segmentação está filtrando o gráfico de colunas para mostrar apenas os valores de julho.

## <a name="cross-filter-and-highlight-a-report"></a>Realizar filtragem cruzada e destacar um relatório
Quando você seleciona um valor em um visual, ele não filtra os outros visuais. Ele realça os valores relacionados nos outros visuais.

* Toque em um valor de um visual.
  
  ![Realizar filtragem cruzada de uma página](media/mobile-reports-in-the-mobile-apps/power-bi-android-tablet-report-highlight.png)
  
  Tocar na coluna Grande de um visual realça os valores relacionados nos outros visuais. 

## <a name="sort-a-visual-on-an-ipad-or-a-tablet"></a>Classificar um visual em um iPad ou tablet
* Toque no gráfico, toque nas reticências (**...**) e toque no nome do campo.
  
   ![Classificar um visual](media/mobile-reports-in-the-mobile-apps/power-bi-android-tablet-report-sort.png)
* Para inverter a ordem de classificação, toque nas reticências (**...**) novamente e, depois, toque no mesmo nome de campo novamente.

## <a name="drill-down-and-up-in-a-visual"></a>Fazer drill down e up em um visual
Se o autor de um relatório tiver adicionado a funcionalidade de drill down a um visual, você poderá fazer drill down no visual para ver os valores que compõem uma parte dele. Você [adiciona o drill down em um visual](power-bi-visualization-drill-down.md) no Power BI Desktop ou no serviço do Power BI. 

* Toque em um ponto de dados em um visual para exibir sua dica de ferramenta. Se ele tiver drill down, a parte inferior da dica de ferramenta terá setas que podem ser tocadas. 
  
  ![Fazer drill down em um visual](media/mobile-reports-in-the-mobile-apps/power-bi-mobile-drill-down-tooltip.png)

* Para fazer drill up, toque na seta para cima na dica de ferramenta.
  
  ![Fazer drill up](media/mobile-reports-in-the-mobile-apps/power-bi-mobile-drill-up-tooltip.png)

* Você também pode fazer drill down em todos os pontos de dados em um visual. Abra-o no modo de foco, toque no ícone Explorar e, em seguida, escolha mostrar todos os próximos níveis ou expanda para mostrar o nível atual e o próximo.

   ![Fazer drill down em todos no Power BI](media/mobile-reports-in-the-mobile-apps/power-bi-drill-down-all.png)

## <a name="drill-through-from-one-page-to-another"></a>Fazer drill down de uma página para outra

Com o *detalhamento*, quando você toca em uma parte específica de um visual, o Power BI leva a uma página diferente no relatório, filtrada com o valor tocado. O autor de um relatório pode definir uma ou mais opções de detalhamento, cada uma levando a uma página diferente. Nesse caso, você pode escolher para qual delas deseja exibir o detalhamento. No exemplo a seguir, ao tocar o valor no medidor, você pode escolher entre o detalhamento de **gasto por área de negócios** ou de **planejamento por área de negócios**.

![Relatório detalhado do Power BI Mobile](media/mobile-reports-in-the-mobile-apps/power-bi-mobile-drill-through-it-spent-report.png)

Quando você faz o detalhamento, o botão Voltar retorna à página anterior do relatório.

Veja como [Adicionar o detalhamento no Power BI Desktop](desktop-drillthrough.md).

## <a name="next-steps"></a>Próximas etapas
* [Exibir e interagir com relatórios do Power BI otimizados para seu telefone](mobile-apps-view-phone-report.md)
* [Criar uma versão de um relatório otimizado para telefones](desktop-create-phone-report.md)
* Dúvidas? [Experimente perguntar à Comunidade do Power BI](http://community.powerbi.com/)

