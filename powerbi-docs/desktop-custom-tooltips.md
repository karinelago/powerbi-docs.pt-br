---
title: Personalizando dicas de ferramenta no Power BI Desktop
description: Crie dicas de ferramenta personalizadas para visuais usando arrastar e soltar
services: powerbi
documentationcenter: 
author: davidiseminger
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
ms.date: 12/06/2017
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: f44f74934bbac345bef165492e83f6ce783b5513
ms.sourcegitcommit: 88c8ba8dee4384ea7bff5cedcad67fce784d92b0
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/24/2018
---
# <a name="customizing-tooltips-in-power-bi-desktop"></a>Personalizando Dicas de Ferramenta no Power BI Desktop
Dicas de ferramenta são uma maneira elegante de fornecer mais informações contextuais e detalhes sobre pontos de dados em um visual. A imagem a seguir mostra uma dica de ferramenta aplicada a um gráfico no Power BI Desktop.

![](media/desktop-custom-tooltips/custom-tooltips_1.png)

Quando uma visualização é criada, a dica de ferramenta padrão exibe a categoria e o valor do ponto de dados. Há muitas situações em poder personalizar as informações nas dicas de ferramenta seria útil e forneceria contexto e informações adicionais para usuários que veem o visual. Dicas de ferramentas personalizadas permitem que você especifique os pontos de dados adicionais que são exibidos como parte da dica de ferramenta.

## <a name="how-to-customize-tooltips"></a>Como personalizar dicas de ferramentas
Para criar uma dica de ferramenta personalizada, nos **Campos** do painel **Visualizações**, basta arrastar um campo para o bucket **Dicas de ferramenta**, mostrado na imagem a seguir. Na imagem a seguir, quatro campos foram colocados no bucket **Dicas de ferramenta**.

![](media/desktop-custom-tooltips/custom-tooltips_2.png)

Após as Dicas de ferramentas serem adicionadas ao campo, passar o mouse sobre um ponto de dados na visualização mostra os valores desses campos na dica de ferramenta.

![](media/desktop-custom-tooltips/custom-tooltips_3.png)

## <a name="customizing-tooltips-with-aggregation-or-quick-calcs"></a>Personalizando dicas de ferramenta com agregação ou Cálculos Rápidos
Você pode personalizar mais a dica de ferramenta selecionando uma função de agregação ou um *Cálculo Rápido*, selecionando a seta ao lado do campo no bucket **Dicas de ferramenta** e selecionando as opções disponíveis.

![](media/desktop-custom-tooltips/custom-tooltips_4.png)

Há muitas maneiras de personalizar **Dicas de ferramenta**, usando qualquer campo disponível no conjunto de dados, para transmitir informações e ideias rápidas para usuários que veem seus dashboards ou relatórios.

