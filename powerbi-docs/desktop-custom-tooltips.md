---
title: Personalizando dicas de ferramenta no Power BI Desktop
description: Crie dicas de ferramenta personalizadas para visuais usando arrastar e soltar
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 05/17/2018
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: 5dfd22f8b45253ece4ed8f699adec9abcaa1a8ed
ms.sourcegitcommit: 80d6b45eb84243e801b60b9038b9bff77c30d5c8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34721146"
---
# <a name="customizing-tooltips-in-power-bi-desktop"></a>Personalizando Dicas de Ferramenta no Power BI Desktop
Dicas de ferramenta são uma maneira elegante de fornecer mais informações contextuais e detalhes sobre pontos de dados em um visual. A imagem a seguir mostra uma dica de ferramenta aplicada a um gráfico no Power BI Desktop.

![Dica de ferramenta padrão](media/desktop-custom-tooltips/custom-tooltips-1.png)

Quando uma visualização é criada, a dica de ferramenta padrão exibe a categoria e o valor do ponto de dados. Há muitas situações em poder personalizar as informações nas dicas de ferramenta seria útil e forneceria contexto e informações adicionais para usuários que veem o visual. Dicas de ferramentas personalizadas permitem que você especifique os pontos de dados adicionais que são exibidos como parte da dica de ferramenta.

## <a name="how-to-customize-tooltips"></a>Como personalizar dicas de ferramentas
Para criar uma dica de ferramenta personalizada, nos **Campos** do painel **Visualizações**, basta arrastar um campo para o bucket **Dicas de ferramenta**, mostrado na imagem a seguir. Na imagem a seguir, dois campos foram colocados no bucket **Dicas de ferramenta**.

![Campos Adicionar dica de ferramenta](media/desktop-custom-tooltips/custom-tooltips-2.png)

Após as dicas de ferramentas serem adicionadas ao campo, passar o mouse sobre um ponto de dados na visualização mostra os valores desses campos na dica de ferramenta.

![Dica de ferramenta personalizada](media/desktop-custom-tooltips/custom-tooltips-3.png)

## <a name="customizing-tooltips-with-aggregation-or-quick-calcs"></a>Personalizando dicas de ferramenta com agregação ou Cálculos Rápidos
Você pode personalizar mais a dica de ferramenta selecionando uma função de agregação ou um *Cálculo Rápido*, selecionando a seta ao lado do campo no bucket **Dicas de ferramenta** e selecionando as opções disponíveis.

![Dica de ferramenta com o Cálculo Rápido](media/desktop-custom-tooltips/custom-tooltips-4.png)

Há muitas maneiras de personalizar **Dicas de ferramenta**, usando qualquer campo disponível no conjunto de dados, para transmitir informações e ideias rápidas para usuários que veem seus dashboards ou relatórios.

