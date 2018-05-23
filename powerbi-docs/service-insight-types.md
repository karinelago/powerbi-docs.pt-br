---
title: Tipos de Insights com suporte para o Power BI
description: Quick Insights e View Insights com o Power BI.
author: mihart
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 03/02/2018
ms.author: mihart
LocalizationGroup: Dashboards
ms.openlocfilehash: 44b59019f1955258716e23fb2dd55182134cc6a2
ms.sourcegitcommit: 998b79c0dd46d0e5439888b83999945ed1809c94
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/17/2018
---
# <a name="types-of-insights-supported-by-power-bi"></a>Tipos de Insights com suporte para o Power BI
## <a name="how-does-insights-work"></a>Como o Insights funciona?
O Power BI pesquisa com rapidez diferentes subconjuntos do conjunto de dados durante a aplicação de um conjunto de algoritmos sofisticados para descobrir informações que possam ser interessantes. Ele examina ao máximo possível um conjunto de dados no período de tempo designado.

Você pode executar insights em um conjunto de dados ou bloco de painel.   

## <a name="what-types-of-insights-can-we-find"></a>Que tipos de informações é possível encontrar?
Estes são alguns dos algoritmos que usamos:

## <a name="category-outliers-topbottom"></a>Exceções de categoria (superior/inferior)
Realça os casos em que, para uma medida no modelo, um ou dois membros de uma dimensão têm valores muito mais altos do que outros membros da dimensão.  

![Exemplo de exceções de categoria](media/service-insight-types/pbi_auto_insight_types_category_outliers.png)

## <a name="change-points-in-a-time-series"></a>Alterar os pontos em uma série temporal
Realça os casos em que há alterações significativas nas tendências em uma série temporal de dados.

![Exemplo de alterar pontos em uma série temporal](media/service-insight-types/pbi_auto_insight_types_changepoint.png)

## <a name="correlation"></a>Correlação
Detecta os casos em que várias medidas mostram uma correlação entre si quando plotadas em uma dimensão no conjunto de dados.

![Exemplo de correlação](media/service-insight-types/pbi_auto_insight_types_correlation.png)

## <a name="low-variance"></a>Baixa variância
Detecta os casos em que os pontos de dados não estão distantes da média.

![Exemplo de baixa variância](media/service-insight-types/power-bi-low-variance.png)

## <a name="majority-major-factors"></a>Maioria (Principais fatores)
Encontra casos em que a maioria de um valor total pode ser atribuída a um único fator quando dividida por outra dimensão.  

![Exemplo de principais fatores](media/service-insight-types/pbi_auto_insight_types_majority.png)

## <a name="overall-trends-in-time-series"></a>Tendências gerais na série temporal
Detecta as tendências ascendentes ou descendentes em dados de série temporal.

![Exemplo de tendências gerais na série temporal](media/service-insight-types/pbi_auto_insight_types_trend.png)

## <a name="seasonality-in-time-series"></a>Periodicidade na série temporal
Encontra padrões periódicos nos dados de série temporal, como periodicidade semanal, mensal ou anual.

![Exemplo de sazonalidade](media/service-insight-types/pbi_auto_insight_types_seasonality_new.png)

## <a name="steady-share"></a>Compartilhamento constante
Realça os casos em que há uma correlação de pai-filho entre o compartilhamento de um valor do filho em relação ao valor geral do pai em uma variável contínua.

![Exemplo de compartilhamento constante](media/service-insight-types/pbi_auto_insight_types_steadyshare.png)

## <a name="time-series-outliers"></a>Exceções da série temporal
Para dados em uma série temporal, detecta quando há datas ou horas específicas com valores significativamente diferentes dos outros valores de data/hora.

![Exemplo de exceções da série temporal](media/service-insight-types/pbi_auto_insight_types_time_series_outliers.png)

## <a name="next-steps"></a>Próximas etapas
[Insights do Power BI](service-insights.md)

Se você é proprietário de um conjunto de dados, [otimize-o para Insights](service-insights-optimize.md)

Mais perguntas? [Experimente a Comunidade do Power BI](http://community.powerbi.com/)

