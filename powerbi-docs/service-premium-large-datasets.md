---
title: Suporte ao Power BI Premium para grandes conjuntos de dados
description: Agora, o Power BI Premium dá suporte a conjuntos de dados de até 10 GB.
author: jocaplan
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-admin
ms.topic: conceptual
ms.date: 02/27/2018
ms.author: jocaplan
LocalizationGroup: Premium
ms.openlocfilehash: fa05fd6808ebe78d5d17e2ad3d93fbcf22f7d3c9
ms.sourcegitcommit: 80d6b45eb84243e801b60b9038b9bff77c30d5c8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34298586"
---
# <a name="power-bi-premium-support-for-large-datasets"></a>Suporte ao Power BI Premium para grandes conjuntos de dados

O Power BI Premium dá suporte a carregamentos de arquivos do Power BI Desktop (.pbix) até 10 GB de tamanho. Uma vez carregado, um conjunto de dados pode ser atualizado para até 12 GB de tamanho. Para usar um conjunto de dados grande, publique-o em um espaço de trabalho atribuído à capacidade Premium.
 
## <a name="best-practices"></a>Práticas recomendadas

Esta seção descreve as práticas recomendadas para trabalhar com grandes conjuntos de dados.

**Modelos grandes podem usar muitos recursos** na sua capacidade; é recomendável pelo menos um SKU de P1 para os modelos maiores que 1 GB. A tabela a seguir descreve os SKUs recomendados para vários tamanhos .pbix:


   |SKU  |Tamanho de .pbix   |
   |---------|---------|
   |P1    | < 3 GB        |
   |P2    | < 6 GB        |
   |P3    | até 10 GB   |



**Os arquivos .pbix representam dados em um estado altamente compactado**. Os dados provavelmente expandirão várias vezes quando carregados na memória e, a partir daí, eles podem expandir várias vezes mais durante a atualização de dados.

**A atualização agendada de grandes conjuntos de dados pode demorar muito tempo** e usar muitos recursos. Da mesma forma, não agende muitas atualizações sobrepostas. Observe também que o tempo limite para trabalhos de atualização agendada foi duplicado para quatro horas para todos os conjuntos de dados nesta capacidade.

**A carga inicial do relatório de grandes conjuntos de dados pode demorar muito tempo** se um período já transcorreu desde a última vez em que o conjunto de dados foi usado, porque o modelo foi carregado na memória da capacidade Premium. Uma barra de carregamento para relatórios demorados exibe o progresso do carregamento.

**Se você remover o espaço de trabalho da capacidade Premium**, o modelo e todos os relatórios e painéis associados não funcionarão.

**Enquanto as restrições de tempo e memória por consulta são muito maiores na capacidade Premium**, é altamente recomendável usar filtros e segmentações de dados para limitar os visuais para exibir apenas o que é necessário.

## <a name="next-steps"></a>Próximas etapas
[Power BI Premium – o que é?](service-premium.md)  
[Notas de versão do Power BI Premium](service-premium-release-notes.md)  
[White paper do Microsoft Power BI Premium](https://aka.ms/pbipremiumwhitepaper)  
[Planejando um white paper de implantação do Power BI Enterprise](https://aka.ms/pbienterprisedeploy)  
[Ativação da Avaliação Pro Estendida](service-extended-pro-trial.md)  

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)
