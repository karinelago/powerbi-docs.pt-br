---
title: "Modo de Exibição de Leitura e Modo de Exibição de Edição no serviço do Power BI"
description: "Visão geral de alto nível das diferenças entre o Modo de Exibição de Leitura e o Modo de Exibição de Edição de relatórios de serviço do Power BI"
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
ms.date: 03/01/2018
ms.author: mihart
LocalizationGroup: Reports
ms.openlocfilehash: 6eca438c9e12d99f925aef864ed9b74e16ef30b7
ms.sourcegitcommit: 5e1f7d2673efe25c47b9b9f315011055bfe92c8f
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/09/2018
---
# <a name="reading-view-and-editing-view-in-power-bi-service-reports"></a>Modo de Exibição de Leitura e Modo de Exibição de Edição em relatórios de serviço do Power BI
No serviço do Power BI (não o Power BI Desktop), há dois modos para exibir e interagir com relatórios: Modo de Exibição de Leitura e Modo de Exibição de Edição. O modo de exibição de Leitura está disponível para todos os usuários e foi especialmente projetado para *consumidores de dados*, enquanto o modo de exibição de Edição só está disponível para *criadores* e proprietários de relatórios. 

![arte de criadores e de consumidores de relatório](media/service-reading-view-and-editing-view/power-bi-creators-consumers.png)

## <a name="report-reading-view"></a>Modo de exibição de Leitura do relatório

 O modo de exibição de Leitura é a sua maneira de explorar e interagir com o relatório – é uma forma divertida e segura de experimentar e conhecer seus dados. O modo de exibição de Leitura foi criado para *consumidores* de relatórios, aqueles que abrem relatórios em Aplicativos ou com quem os relatórios são [compartilhados](service-share-dashboards.md). O Modo de Exibição de Leitura garante que cada consumidor de um relatório específico esteja vendo o mesmo relatório, as mesmas visualizações, com os mesmos filtros aplicados.  Os consumidores podem interagir com os relatórios, mas não conseguem salvar alterações.

>**OBSERVAÇÃO**: há determinadas circunstâncias em que pode ser que os consumidores de relatório vejam dados diferentes devido ao nível de linha de segurança e a permissões de dados. 

## <a name="report-editing-view"></a>Modo de exibição de Edição do relatório

O modo de exibição de Edição só fica disponível para aqueles que criaram o relatório ou que são [coproprietários de um relatório, por serem um membro ou administrador de um espaço de trabalho do aplicativo](service-create-distribute-apps.md).

O modo de exibição de Edição foi projetado para *criadores* de relatórios. É o lugar em que os criadores importam e conectam-se a conjuntos de dados, exploram os dados e criam relatórios e dashboards. No modo de exibição de Edição, os *criadores* podem se aprofundar ainda mais em seus dados adicionando e removendo campos, alterando o tipo de visualização, criando novas visualizações e adicionando e excluindo visualizações e páginas do relatório. Eles podem então compartilhar os relatórios criados com colegas.

## <a name="reading-view-versus-editing-view"></a>Modo de exibição de Leitura versus modo de exibição de Edição
Este gráfico não lista todos os recursos de relatórios do serviço do Power BI. Lista somente as tarefas de relatório que não estão disponíveis no modo de exibição de Leitura **nem** no modo de exibição de Edição. 


|Tarefa  | Modo de exibição de leitura  | Modo de Exibição de Edição |
|-------------------------|-------|-------|
|**Relatórios, como um todo**  |
||||
| [Criar ou editar um relatório](service-report-create-new.md) | Não  | Sim |
| [Compartilhar um relatório](service-share-reports.md)| Sim | Sim e também pode gerenciar permissões, incluindo conceder permissões de *proprietário* a outras pessoas. |
| [Criar filtros persistentes (permanentes) no nível do visual, de detalhamento, no nível da página e no nível do relatório no painel Filtros](power-bi-report-add-filter.md) | Não  | Sim |
| [Usar o painel Filtros do relatório](power-bi-how-to-report-filter.md) | Sim, pode usar os filtros existentes, mas as alterações não são salvas com o relatório. | Sim |
| [Usar o painel Análise do relatório](service-analytics-pane.md) | Não | Sim |
| [Opções de **Exibição** do relatório](power-bi-report-display-settings.md) | Sim, com algumas exceções. | Sim, todas, incluindo linhas de grade, alinhamento e bloqueio. |
| [Criar um agendamento de atualização](refresh-data.md) | Não  | Sim |
| [Assinar um relatório](service-report-subscribe.md) | Sim | Não |
| [P e R – fazer perguntas em relatórios](power-bi-q-and-a.md) | Não  | Sim |
| [Exibir Métricas de uso ](service-usage-metrics.md) | Sim, na tela do relatório. | Sim, na lista do relatório (exibição de conteúdo) |
| [Exibição relacionada](service-related-content.md) | Sim, na tela do relatório. | Sim, na lista do relatório (exibição de conteúdo) |
| [Salvar um relatório](service-report-save.md) | Sim, mas apenas com **Salvar como**. | Sim |
| [Excluir um relatório](service-delete.md) | Não  | Sim |
|**Páginas de relatório** |
||||
| [Adicionar ou renomear uma página de relatório](power-bi-report-add-page.md)  | Não  | Sim  |
| [Duplicar uma página de relatório](power-bi-report-copy-paste-page.md) | Não  | Sim |
| [Excluir página de relatório](service-delete.md) | não | sim |
|**Trabalhando com visualizações de relatório**|
||||
| [Adicionar visualizações a um relatório](power-bi-report-add-visualizations-i.md) | Não  | Sim |
| [Adicionar caixas de texto e formas a um relatório](power-bi-reports-add-text-and-shapes.md) | Não  | Sim |
| [Usar o painel Formatação do relatório](service-the-report-editor-take-a-tour.md) | Não | Sim |
| [Definir interações visuais](service-reports-visual-interactions.md) | Não  | Sim |
| [Mostrar os dados usados para criar a visualização](service-reports-show-data.md) | Não  | Sim |
| [Configurar drilling](power-bi-visualization-drill-down.md) | Não  | Sim |
| [Alterar a visualização utilizada](power-bi-report-change-visualization-type.md) | Não | Sim|
| [Excluir uma visualização, caixa de texto ou forma](service-delete.md)| Não | Sim |


## <a name="navigating-between-editing-view-and-reading-view"></a>Navegando entre o Modo de Exibição de Edição e o Modo de Exibição de Leitura
Lembre-se de que somente o criador e os proprietários do relatório poderão abrir um relatório no modo de exibição de Edição.

1. Por padrão, geralmente um relatório é aberto no Modo de Exibição de Leitura. Você consegue saber se está no Modo de Exibição de Leitura, se vir uma opção para **Editar relatório**. Se a opção **Editar relatório** estiver acinzentada, você não tem permissões para abrir o relatório no Modo de Exibição de Edição.

   ![Editar relatório esmaecido](media/service-reading-view-and-editing-view/power-bi-edit-report-grey.png)

2. Se a opção **Editar relatório** não estiver acinzentada, selecione-a para abrir o relatório no Modo de Exibição de Edição. 
   
   ![Opção Editar relatório](media/service-reading-view-and-editing-view/power-bi-edit-report.png)
   
   Agora o relatório está no modo de exibição de Edição e usa as mesmas [configurações de vídeo](power-bi-report-display-settings.md) usadas por você na última vez no modo de exibição de Leitura.

2. Para retornar ao Modo de Exibição de Leitura, selecione **Modo de Exibição de Leitura** na barra de navegação superior.
   
    ![Opção Modo de exibição de leitura](media/service-reading-view-and-editing-view/power-bi-reading-view.png)



### <a name="next-steps"></a>Próximas etapas
Há muitas maneiras de interagir com um relatório no Modo de Exibição de Leitura, segmentando e repartindo os dados para descobrir informações e obter respostas às perguntas.  O próximo tópico, [Interagir com um relatório no modo de exibição de Leitura](service-interact-with-a-report-in-editing-view.md), descreve alguns desses aspectos detalhadamente.    
Voltar para [relatórios no Power BI](service-reports.md)    
Mais perguntas? [Experimente a Comunidade do Power BI](http://community.powerbi.com/) 

