---
title: Formatação de tabela condicional no Power BI Desktop
description: Aplicar formatação personalizada a tabelas
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 05/08/2018
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: 9599b40940c9d9cca254bb2ed2e87c161cce371f
ms.sourcegitcommit: 638de55f996d177063561b36d95c8c71ea7af3ed
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/17/2018
---
# <a name="conditional-formatting-in-tables"></a>Formatação condicional em tabelas
Com a formatação condicional para tabelas, você pode especificar cores personalizadas para a tela de fundo das células com base nos valores das células ou em outros valores ou campos, inclusive usando cores de gradiente. Para acessar a formatação condicional, em **Campos** também do painel **Visualizações** no Power BI Desktop, selecione a seta para baixo ao lado do valor em **Valores** que você deseja formatar (ou clique com o botão direito do mouse no campo). Você pode gerenciar somente a formatação condicional para campos na área **Valores** também em **Campos**.

![formatação condicional de tabela](media/desktop-conditional-table-formatting/table-formatting_1.png)

Na caixa de diálogo que aparece, você pode definir a cor, bem como os valores *Mínimo* e *Máximo*. Se selecionar a caixa **Divergente**, você também poderá configurar um valor opcional para o *Centro*.

![cores divergentes](media/desktop-conditional-table-formatting/table-formatting_2.png)

Você também pode basear o gradiente de cores em um campo do modelo de dados. Além disso, você pode especificar o tipo de agregação para o campo selecionado (o campo selecionado é especificado no campo **Aplicar cor a**, permitindo manter controle).

![cores base fora de um campo](media/desktop-conditional-table-formatting/table-formatting_2b.png)

Quando aplicada a uma tabela, a formatação personalizada aplicada usando as etapas descritas acima substitui quaisquer estilos de tabela personalizados aplicados a células formatadas condicionalmente.

![formatação de tabela](media/desktop-conditional-table-formatting/table-formatting_3.png)

Também é possível aplicar a formatação condicional a campos de data e de texto, desde que você escolha um valor numérico como a base da formatação. 

Para remover a formatação condicional de uma visualização, basta clicar com o botão direito do mouse no campo novamente e selecionar **Remover formatação condicional**.

![remover formatação de tabela](media/desktop-conditional-table-formatting/table-formatting_4.png)

