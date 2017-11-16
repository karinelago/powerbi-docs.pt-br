---
title: "Definir filtros geográficos no Power BI Desktop para os aplicativos móveis"
description: "Quando você define a filtragem geográfica em seu modelo no Power BI Desktop, é possível filtrar os dados para sua localização automaticamente nos aplicativos móveis do Power BI."
services: powerbi
documentationcenter: 
author: maggiesMSFT
manager: kfile
editor: 
tags: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 07/18/2017
ms.author: maggies
ms.openlocfilehash: ac03f3e97c2e2cef7d4f083e5b835aa4c87de633
ms.sourcegitcommit: 99cc3b9cb615c2957dde6ca908a51238f129cebb
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/13/2017
---
# <a name="set-geographic-filters-in-power-bi-desktop-for-the-mobile-apps"></a>Definir filtros geográficos no Power BI Desktop para os aplicativos móveis
No Power BI Desktop, você pode [categorizar dados geográficos](desktop-data-categorization.md) de uma coluna e, portanto, o Power BI Desktop sabe como tratar valores em visuais de um relatório. Como um benefício extra, quando você ou seus colegas exibem esse relatório nos aplicativos móveis do Power BI, o Power BI fornece automaticamente filtros geográficos que correspondem à sua localização. 

Por exemplo, digamos que você seja um gerente de vendas que vai viajar para atender a seus clientes e deseja filtrar rapidamente a receita e o total de vendas do cliente específico que você pretende visitar. Você deseja dividir os dados para sua localização atual, seja por estado, cidade ou um endereço real. Mais tarde, se você tiver algum tempo, desejará visitar outros clientes localizados nas proximidades. É possível [filtrar o relatório por sua localização para encontrar os clientes](mobile-apps-geographic-filtering.md).

> [!NOTE]
> Só será possível filtrar por localização no aplicativo móvel se os nomes geográficos no relatório estiverem em inglês &#150; por exemplo, “New York City” ou “Germany”.
> 
> 

## <a name="identify-geographic-data-in-your-report"></a>Identificar dados geográficos em seu relatório
1. No Power BI Desktop, mude para a Exibição de Dados ![Ícone de Exibição de dados](media/desktop-mobile-geofiltering/pbi_desktop_data_icon.png).
2. Selecione uma coluna com dados geográficos &#151; por exemplo, uma coluna Cidade.
   
    ![Coluna Cidade](media/desktop-mobile-geofiltering/power-bi-desktop-geo-column.png)
3. Na guia **Modelagem**, selecione **Categoria de Dados** e a categoria correta &#151; neste exemplo, **Cidade**.
   
    ![Caixa de categoria de dados](media/desktop-mobile-geofiltering/power-bi-desktop-geo-category.png)
4. Continue definindo as categorias de dados geográficos de todos os outros campos no modelo. 
   
   > [!NOTE]
   > É possível definir várias colunas para cada categoria de dados em um modelo, mas se você fizer isso, o modelo não poderá filtrar por localização geográfica no aplicativo móvel do Power BI. Para usar a filtragem geográfica nos aplicativos móveis, defina apenas uma coluna para cada categoria de dados &#151; por exemplo, apenas uma coluna **Cidade**, uma coluna **Estado ou Província** e uma coluna **País**. 
   > 
   > 

## <a name="create-visuals-with-your-geographic-data"></a>Criar visuais com seus dados geográficos
1. Mude para o modo de exibição de relatório ![Ícone de Exibição de Relatório](media/desktop-mobile-geofiltering/power-bi-desktop-report-icon.png), e crie visuais que usam os campos geográficos em seus dados. 
   
    ![Relatório com o mapa](media/desktop-mobile-geofiltering/power-bi-desktop-geo-report.png)
   
    Neste exemplo, o modelo também contém uma coluna calculada que traz a cidade e o estado juntos em uma coluna. Leia sobre a [criação de colunas calculadas no Power BI Desktop](desktop-calculated-columns.md).
   
    ![Campo Cidade + Estado](media/desktop-mobile-geofiltering/power-bi-desktop-city-state-column.png)
2. Publique o relatório no serviço do Power BI.

## <a name="view-the-report-in-power-bi-mobile-app"></a>Exibir o relatório no aplicativo móvel do Power BI
1. Abra o relatório em qualquer um dos [aplicativos móveis do Power BI](mobile-apps-for-mobile-devices.md).
2. Se você estiver em uma localização geográfica que tem dados no relatório, você poderá filtrá-los automaticamente para a sua localização.
   
    ![Filtro de replicação geográfica no aplicativo móvel](media/desktop-mobile-geofiltering/power-bi-mobile-geo-map-set-filter.png)

Leia mais sobre [filtrar um relatório por localização nos aplicativos móveis do Power BI](mobile-apps-geographic-filtering.md).

## <a name="next-steps"></a>Próximas etapas
* [Categorização de dados no Power BI Desktop](desktop-data-categorization.md)  
* Dúvidas? [Experimente perguntar à Comunidade do Power BI](http://community.powerbi.com/)

