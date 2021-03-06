---
title: Filtragem cruzada bidirecional no Power BI Desktop
description: Habilitar a filtragem cruzada usando o DirectQuery no Power BI Desktop
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 04/24/2018
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: a584d61e1f2f55c244b453e6c086f3222217ee9a
ms.sourcegitcommit: 638de55f996d177063561b36d95c8c71ea7af3ed
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/17/2018
---
# <a name="bidirectional-cross-filtering-using-directquery-in-power-bi-desktop"></a>Filtragem cruzada bidirecional usando o DirectQuery no Power BI Desktop

Ao filtrar tabelas para criar a exibição de dados apropriada, os criadores de relatório (e modeladores de dados) enfrentam desafios ao determinar como a filtragem é aplicada a um relatório; o contexto de filtro de uma tabela foi mantido em um lado da relação, mas não no outro, exigindo, muitas vezes, fórmulas DAX complexas para obter os resultados desejados.

Com a filtragem cruzada bidirecional, os criadores de relatório (e modeladores de dados) agora têm mais controle sobre como os filtros são aplicados ao trabalhar com tabelas relacionadas, permitindo que eles sejam aplicados em *ambos* os lados de uma relação de tabela. Isso é realizado com a propagação do contexto de filtro em uma segunda tabela relacionada do outro lado de uma relação de tabela.

Um [white paper detalhado](http://download.microsoft.com/download/2/7/8/2782DF95-3E0D-40CD-BFC8-749A2882E109/Bidirectional%20cross-filtering%20in%20Analysis%20Services%202016%20and%20Power%20BI.docx) que explica a filtragem cruzada bidirecional no Power BI Desktop está disponível (também aborda o SQL Server Analysis Services 2016, que tem o mesmo comportamento).

* Baixar o white paper [Bidirectional cross-filtering for Power BI Desktop](http://download.microsoft.com/download/2/7/8/2782DF95-3E0D-40CD-BFC8-749A2882E109/Bidirectional%20cross-filtering%20in%20Analysis%20Services%202016%20and%20Power%20BI.docx) (Filtragem cruzada bidirecional para o Power BI Desktop)

### <a name="enabling-bidirectional-cross-filtering-for-directquery"></a>Habilitando a filtragem cruzada bidirecional para o DirectQuery

Para habilitar a filtragem cruzada, na caixa de diálogo **Editar Relação** de uma relação, selecione o seguinte:

* A **Direção do filtro cruzado** deve ser definida como **Ambos**
* A opção **Aplicar filtro de segurança em ambas as direções** também deve ser selecionada
  
  ![](media/desktop-bidirectional-filtering/bidirectional-filtering_2.png)

> [!NOTE]
> Ao criar fórmulas DAX de filtragem cruzada no Power BI Desktop, use *UserPrincipalName* (que é geralmente o mesmo logon do usuário, como *joe@contoso.com*), em vez de *UserName*. Assim, você poderá precisar criar uma tabela relacionada que mapeia *UserName* (ou EmployeeID, por exemplo) para *UserPrincipleName*.
> 
> 

Para obter mais informações e exemplos de como funciona a filtragem cruzada bidirecional, confira o [white paper](http://download.microsoft.com/download/2/7/8/2782DF95-3E0D-40CD-BFC8-749A2882E109/Bidirectional%20cross-filtering%20in%20Analysis%20Services%202016%20and%20Power%20BI.docx) mencionado anteriormente neste artigo.

