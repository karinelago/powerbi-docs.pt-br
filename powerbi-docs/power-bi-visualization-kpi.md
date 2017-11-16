---
title: Visuais do KPI (tutorial)
description: criar um KPI no power bi
services: powerbi
documentationcenter: 
author: mihart
manager: kfile
backup: 
editor: 
tags: 
featuredvideoid: xmja6EpqaO0
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 08/09/2017
ms.author: mihart
ms.openlocfilehash: 23b322c9fbc4c203a5b20aa45bb41c2cb6cb7f0f
ms.sourcegitcommit: 99cc3b9cb615c2957dde6ca908a51238f129cebb
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/13/2017
---
# <a name="kpi-visuals-tutorial"></a>Visuais do KPI (tutorial)
Um KPI (Indicador Chave de Desempenho) é uma indicação visual que comunica a quantidade de progresso feito em relação a uma meta mensurável. Para obter mais informações sobre KPIs, veja [Microsoft Developer Network](https://msdn.microsoft.com/library/hh272050).

## <a name="when-to-use-a-kpi"></a>Quando usar um KPI
Os KPIs são uma ótima opção:

* para medir o progresso (no que estou adiantado ou atrasado?)
* para medir a distância para uma meta (o quão adiantado ou atrasado eu estou?)   

## <a name="kpi-visual-requirements"></a>Requisitos visuais do KPI
Um KPI se baseia em uma medida específica e é projetado para ajudá-lo a avaliar o status e o valor atual de uma métrica em relação a uma meta definida. Portanto, um visual de KPI requer uma medida *base* que é avaliada como um valor e uma medida ou um valor de *destino*, bem como um limite ou uma meta.

> [!NOTE]
> Atualmente, um conjunto de dados de KPI precisa conter valores de meta referente a um KPI. Se seu conjunto de dados não contiver um, será possível criar metas adicionando uma planilha do Excel com as metas ao seu modelo de dados ou ao arquivo PBIX.
> 
> 

## <a name="how-to-create-a-kpi"></a>Como criar um KPI
Para acompanhar, entre no Power BI e selecione **Obter Dados > Amostras > Amostra de Análise de Varejo**. Vamos criar um KPI que mede o progresso que fizemos para atingir uma meta de vendas.

Ou veja Will mostrando como criar elementos visuais de métrica únicos: medidores, cartões e KPIs.

<iframe width="560" height="315" src="https://www.youtube.com/embed/xmja6EpqaO0?list=PL1N57mwBHtN0JFoKSR0n-tBkUJHeMP2cP" frameborder="0" allowfullscreen></iframe>

1. Selecione **Vendas > Total de Unidades Deste Ano**.  Esse será o indicador.
2. Adicionar **Hora > Mês**.  Isso representará a tendência.
3. IMPORTANTE: classifique o gráfico por **Mês**. Depois de converter a visualização em um KPI, não haverá opção para classificar.
4. Converta o visual para um KPI selecionando o ícone do KPI do painel Visualização.
   
    ![](media/power-bi-visualization-kpi/power-bi-kpi-icon.png)
5. Adicione uma meta. Adicione as vendas do último ano como a meta. Arraste **Total de Unidades do Ano Passado** para o campo **Metas de destino**.
   
    ![](media/power-bi-visualization-kpi/power-bi-kpi.png)
6. Opcionalmente, formate o KPI selecionando o ícone de rolo de pintura para abrir o painel Formatação.
   
   * **Indicador** – controla as unidades de exibição e as casas decimais do indicador.
   * **Eixo de tendência**: quando definido como **Ativado**, o eixo de tendência é exibido como a tela de fundo do visual de KPI.  
   * **Metas** – quando definido como **Ativado**, o visual exibe a meta e a distância da meta como um percentual.
   * **Status** – alguns KPIs são considerados *melhores* para valores mais altos, enquanto outros são considerados *melhores* para valores mais baixos. Por exemplo, lucros VS. tempo de espera. Normalmente, um valor mais alto de ganhos é melhor em comparação com um valor mais alto de tempo de espera, que geralmente é considerado o pior. Essa alternância permite a seleção de um comportamento de KPI. A seleção de status usa **alto é melhor** como padrão.
7. Quando o KPI estiver como desejado, [fixe-o em um dashboard](service-dashboard-pin-tile-from-report.md).

Os KPIs também estão disponíveis nos seus dispositivos móveis, mantendo você sempre conectados à pulsação de seus negócios

## <a name="considerations-and-troubleshooting"></a>Considerações e solução de problemas
* Se seu KPI não se parecer com o mostrado acima, talvez seja necessário classificar por mês. Como os KPIs não têm uma opção de classificação, será necessário classificar por mês *antes* de converter sua visualização em um KPI.

## <a name="next-steps"></a>Próximas etapas
[Relatórios no Power BI](service-reports.md)

[Visualizações em relatórios do Power BI](power-bi-report-visualizations.md)

[Power BI – conceitos básicos](service-basic-concepts.md)

Mais perguntas? [Experimente a Comunidade do Power BI](http://community.powerbi.com/)

