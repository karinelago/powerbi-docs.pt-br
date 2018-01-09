---
title: Fixar um bloco em um dashboard de P e R
description: "Documentação sobre como fixar um bloco em um dashboard do Power BI por meio da caixa de P e R"
services: powerbi
documentationcenter: 
author: mihart
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
ms.date: 12/20/2017
ms.author: mihart
ms.openlocfilehash: 8a876c5a05fcdadff1a874148f5d56465bcc8c62
ms.sourcegitcommit: 6ea8291cbfcb7847a8d7bc4e2b6abce7eddcd0ea
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/21/2017
---
# <a name="pin-a-tile-to-a-dashboard-from-qa"></a>Fixar um bloco em um dashboard de P e R
## <a name="how-to-pin-a-tile-from-qa"></a>Como fixar um bloco de P e R
P e R é a ferramenta de geração de relatórios ad hoc do Power BI. Precisa encontrar uma visão particular? Faça uma pergunta sobre os dados e receba uma resposta na forma de uma visualização.

P e R está disponível em painéis e relatórios. Neste artigo, abriremos P e R de um painel. Estão disponíveis painéis no serviço do Power BI, mas não no Power BI Desktop. Para acompanhar, abra o [painel de exemplo da Análise de Varejo](sample-retail-analysis.md).
> 
> 

1. Abra um [dashboard](service-dashboards.md) que tenha pelo menos um bloco fixado de um relatório. Quando você faz uma pergunta, o Power BI procura a resposta em qualquer conjunto de dados que tenha um bloco fixado a esse dashboard.  Para saber mais, veja [obter dados](service-get-data.md).
2. Na caixa de pergunta, na parte superior do painel, comece a digitar o que você deseja saber sobre os dados.  
   ![](media/service-dashboard-pin-tile-from-q-and-a/power-bi-question-box.png)
3. Por exemplo, ao digitar “vendas do ano passado por mês e território”...  
   ![](media/service-dashboard-pin-tile-from-q-and-a/power-bi-type-q-and-a.png)
   
   a caixa de perguntas oferece sugestões.
4. Para adicionar o gráfico ao dashboard como um bloco, selecione o pino ![](media/service-dashboard-pin-tile-from-q-and-a/pbi_pintile.png) no lado superior direito da tela.
5. Fixe o bloco em um painel existente ou em um novo painel. 

   ![](media/service-dashboard-pin-tile-from-q-and-a/power-bi-pin-to-dashboard.png)

   * Painel existente: selecione o nome do painel no menu suspenso. Suas opções serão limitadas apenas aos painéis no espaço de trabalho atual.
   * Novo dashboard: digite o nome do novo dashboard e ele será adicionado ao seu espaço de trabalho atual.
6. Selecione **Fixar**.
   
   Uma mensagem de êxito (perto do canto superior direito) informa que a visualização foi adicionada, como um bloco, ao dashboard.  
   
   ![](media/service-dashboard-pin-tile-from-q-and-a/power-bi-pin.png)
7. Selecione **Ir para o dashboard** para ver o novo bloco. Nele, é possível [renomear, redimensionar, adicionar um hiperlink, reposicionar o bloco e muito mais](service-dashboard-edit-tile.md) no dashboard. 
   
   ![](media/service-dashboard-pin-tile-from-q-and-a/power-bi-pinned.png)

## <a name="considerations-and-troubleshooting"></a>Considerações e solução de problemas
* Quando você começa a digitar uma pergunta, o P e R imediatamente começa a procurar a melhor resposta de todos os conjuntos de dados associados com o painel atual.  O “dashboard atual” é o dashboard listado na barra de navegação superior. Por exemplo, essa pergunta está sendo feita no dashboard de **exemplo Análise de Varejo**, que faz parte do espaço de trabalho de aplicativo **mihart**.
  
  ![](media/service-dashboard-pin-tile-from-q-and-a/power-bi-navbar.png)
* **Como a P e R sabe quais conjuntos de dados deverão ser usados**?  O P e R tem acesso a todos os conjuntos de dados que têm visualizações fixadas para esse painel.

## <a name="next-steps"></a>Próximas etapas
[Renomear, redimensionar, adicionar um hiperlink, reposicionar o bloco e muito mais](service-dashboard-edit-tile.md)    
[Exibir seu bloco do dashboard no Modo de foco](service-focus-mode.md)     
[Voltar a P e R no Power BI](service-q-and-a.md)  
Mais perguntas? [Experimente a Comunidade do Power BI](http://community.powerbi.com/)

