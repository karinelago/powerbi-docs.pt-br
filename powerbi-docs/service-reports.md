---
title: "Relatórios no Power BI"
description: "Relatórios no Power BI"
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
ms.date: 01/08/2018
ms.author: mihart
ms.openlocfilehash: baa94483b8174d62d0f7e27d726bb59dbb0b4c10
ms.sourcegitcommit: 804ee18b4c892b7dcbd7d7d5d987b16ef16fc2bb
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/09/2018
---
# <a name="reports-in-power-bi"></a>Relatórios no Power BI
## <a name="what-is-a-power-bi-report"></a>O que é um relatório do Power BI?
Um ***relatório*** do Power BI é uma exibição de um conjunto de dados em várias perspectivas, com visualizações que representam as diferentes descobertas e informações obtidas por meio desse conjunto de dados.  Um relatório pode ter uma única visualização ou páginas repletas de visualizações. Dependendo da sua função de trabalho, você pode ser alguém que *cria* relatórios e/ou você pode ser alguém que *consome* ou usa relatórios.

![](media/service-reports/reportview.png)

Esse relatório tem 3 páginas (ou guias) e estamos exibindo a página de Visão geral de vendas de lojas. Nesta página estão 6 visualizações diferentes e um título de página. As visualizações podem ser *fixadas* em dashboards e, quando essa visualização fixada é selecionada, ela abre o relatório do qual ela foi fixada.

Se for novo no Power BI, você poderá obter uma boa base lendo o tópico [Conceitos básicos do Power BI](service-basic-concepts.md)

Os relatórios são um recurso do serviço do Power BI e do Power BI Desktop. A experiência de trabalhar com relatórios é quase idêntica. No entanto, para dispositivos móveis, você não pode criar relatórios, mas você pode [exibir, compartilhar e fazer anotações em relatórios](mobile-reports-in-the-mobile-apps.md).

## <a name="advantages-of-reports"></a>Vantagens dos relatórios
Os relatórios são baseados em um único conjunto de dados. Cada uma das visualizações em um relatório representa uma informação preciosa. E as visualizações não estáticas. Você pode adicionar e remover dados, alterar os tipos de visualização e aplicar filtros e segmentações de dados ao se aprofundar nos dados para descobrir informações e procurar respostas. Como um dashboard, mas mais do que isso, um relatório é altamente interativo e altamente personalizável e as visualizações são atualizadas conforme os dados subjacente se alteram.

## <a name="dashboards-versus-reports"></a>Dashboards versus relatórios
Os [dashboards](service-dashboards.md) costumam ser confundidos com relatórios, pois eles também são telas preenchidas com visualizações. Mas existem algumas diferenças importantes.  

| **Funcionalidade** | **Dashboards** | **Relatórios** |
| --- | --- | --- |
| Páginas |Uma página |Uma ou mais páginas |
| Fontes de dados |Um ou mais relatórios e um ou mais conjuntos de dados por dashboard |Um único conjunto de dados por relatório |
| Disponível no Power BI Desktop |Não |Sim, pode criar e exibir relatórios na área de trabalho |
| Fixação |Pode fixar visualizações existentes (blocos) somente do dashboard atual a outros dashboards |Pode fixar visualizações (como blocos) a qualquer um dos seus dashboards. Pode fixar páginas de relatório inteiras a qualquer um dos seus dashboards. |
| Assinatura |Não é possível assinar um dashboard |É possível assinar páginas de relatório |
| Filtragem |Não é possível filtrar ou fatiar |Diferentes maneiras de filtrar, realçar e fatiar |
| Definir alertas |Pode criar alertas para enviar por email quando determinadas condições forem atendidas |Não |
| Recurso |Pode definir um dashboard como o dashboard "em destaque" |Não é possível criar um relatório em destaque |
| Consultas de linguagem natural |Disponível no dashboard |Não está disponível nos relatórios |
| Pode alterar o tipo de visualização |Não. Na verdade, se o proprietário de um relatório alterar o tipo de visualização do relatório, a visualização fixada no dashboard não será atualizada |Sim |
| Pode ver campos e tabelas do conjunto de dados subjacentes |Não. Pode exportar dados, mas não consegue ver tabelas e campos no dashboard de controle em si. |Sim. Pode ver as tabelas de conjunto de dados e os campos e valores. |
| Pode criar visualizações |Limitado a adicionar widgets ao dashboard usando "Adicionar bloco" |Pode criar muitos tipos diferentes de elementos visuais, adicionar elementos visuais personalizados, editar elementos visuais e muito mais com permissões de edição |
| Personalização |Pode fazer várias coisas com as visualizações (blocos), como mover e organizar, redimensionar, adicionar links, renomear, excluir e exibir a tela inteira. Mas os dados e as visualizações em si são somente leitura. |No modo de exibição de Leitura, você pode publicar, inserir, filtrar, exportar, baixar como .pbix, exibir conteúdo relacionado, gerar códigos QR, analisar no Excel e muito mais.  No modo de exibição de Edição, você pode fazer tudo o que foi mencionado até o momento e muito mais. |

## <a name="report-creators-and-report-consumers"></a>***Criadores*** de relatório e ***consumidores*** de relatório
Dependendo da função, você pode ser alguém que cria relatórios para seu próprio uso ou para compartilhar com colegas. Você deseja saber como criar e compartilhar relatórios. Ou pode ser alguém que recebe os relatórios de outras pessoas. Você deseja saber como entender e interagir com os relatórios.

Aqui estão alguns tópicos, por função, para ajudá-lo a começar.

### <a name="if-you-will-be-creating-and-sharing-reports"></a>Se você for criar e compartilhar relatórios
* Comece com um [tour pelo serviço do Power BI](service-basic-concepts.md) para saber em que local encontrar relatórios e ferramentas de relatório.
* Faça um tour pelo [editor de relatório](service-the-report-editor-take-a-tour.md).
* Saiba como [criar um relatório de um conjunto de dados](service-report-create-new.md).
* [Saiba como usar filtros de nível de relatório, de página e de visualização](power-bi-how-to-report-filter.md)
* Descubra todas as diferentes maneiras de [compartilhar um relatório com colegas](service-share-dashboards.md).

### <a name="if-you-will-be-receiving-and-consuming-reports"></a>Se você for receber e consumir relatórios
* Comece com um [tour pelo serviço do Power BI](service-basic-concepts.md) para saber em que local encontrar relatórios e ferramentas de relatório.
* Saiba como [abrir um relatório](service-report-open.md) e toda a interação disponível em [Modo de exibição de leitura](service-reading-view-and-editing-view.md).
* Familiarize-se com relatórios fazendo um tour em um dos nossos [exemplos](sample-tutorial-connect-to-the-samples.md).  
* Não precisa mais do relatório? Você pode [removê-lo](service-delete.md).
* Para ver qual conjunto de dados o relatório está usando e quais dashboards tem blocos fixados do relatório, [exiba o conteúdo relacionado](service-related-content.md).

> [!TIP]
> Se você não encontrar o que está procurando aqui, use o Sumário à esquerda para procurar todos os tópicos de *relatório*.
> 
> 

## <a name="next-steps"></a>Próximas etapas
[Introdução ao Power BI](service-get-started.md) 

[Power BI – conceitos básicos](service-basic-concepts.md)

Mais perguntas? [Experimente a Comunidade do Power BI](http://community.powerbi.com/)

