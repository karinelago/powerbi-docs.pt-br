---
title: Otimizar um visual do Power BI para qualquer tamanho
description: "Aprenda a otimizar os visuais no Power BI Desktop e no serviço do Power BI para os aplicativos de telefone do Power BI."
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
LocalizationGroup: Create reports
ms.openlocfilehash: 4c80048213b20365102bcb9c6842c342d8b9052b
ms.sourcegitcommit: 88c8ba8dee4384ea7bff5cedcad67fce784d92b0
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/24/2018
---
# <a name="optimize-a-power-bi-visual-for-any-size"></a>Otimizar um visual do Power BI para qualquer tamanho
Você pode definir os visuais em seu dashboard ou relatório para serem *responsivos*, para mudarem dinamicamente para exibir o máximo de dados e insight, independentemente do tamanho da tela.

Como um visual muda de tamanho, o Power BI prioriza a exibição de dados, por exemplo, removendo o preenchimento e movendo a legenda para a parte superior do visual automaticamente, para que ele continue informativo mesmo quando fica menor. A capacidade de resposta é especialmente útil em visuais no aplicativo móvel do Power BI em telefones.

![Redimensionamento do visual responsivo](media/desktop-create-responsive-visuals/power-bi-responsive-visual.gif)

É possível ativar a capacidade de resposta para qualquer visual com eixos X e Y e segmentações.

## <a name="turn-on-responsiveness-in-power-bi-desktop"></a>Ativar a capacidade de resposta no Power BI Desktop
1. No Power BI Desktop, na guia **Exibir**, certifique-se de que você está no **Layout da área de trabalho**.
   
    ![Ícone de Layout da Área de Trabalho](media/desktop-create-responsive-visuals/power-bi-desktop-layout.png)
2. Selecione um visual e no painel **Visualizações**, selecione a seção **Formatar**.
3. Expanda **Geral** > deslize a opção **Responsivo** para a posição **Ativo**.
   
    ![Responsivo ativado](media/desktop-create-responsive-visuals/power-bi-turn-responsive-on.png)
   
     Agora quando você [criar um relatório otimizado para o telefone](desktop-create-phone-report.md) e adicionar esse visual, ele será redimensionado com sutileza.

## <a name="turn-on-responsiveness-in-the-power-bi-service"></a>Ativar a capacidade de resposta no serviço do Power BI
Ativar a capacidade de resposta de um visual em um relatório do serviço do Power BI. Você precisa ser capaz de editar o relatório.

1. Em um relatório no serviço do Power BI ([https://powerbi.com](https://powerbi.com)), selecione **Editar Relatório**.
2. Selecione um visual e no painel **Visualizações**, selecione a seção **Formatar**.
3. Expanda **Geral** > deslize a opção **Responsivo** para a posição **Ativo**.
   
    ![Responsivo ativado](media/desktop-create-responsive-visuals/power-bi-turn-responsive-on.png)
   
     Agora quando você [criar uma exibição para telefone de um dashboard](service-create-dashboard-mobile-phone-view.md) e adicionar esse visual, ele será redimensionado com sutileza.

## <a name="next-steps"></a>Próximas etapas
* [Criar relatórios otimizados para os aplicativos de telefone do Power BI](desktop-create-phone-report.md)
* [Criar uma exibição de telefone de um dashboard no Power BI](service-create-dashboard-mobile-phone-view.md)
* [Exibir relatórios do Power BI otimizados para seu telefone](mobile-apps-view-phone-report.md)
* Mais perguntas? [Experimente perguntar à Comunidade do Power BI](http://community.powerbi.com/)

