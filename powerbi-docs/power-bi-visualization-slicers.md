---
title: "Segmentações no Power BI (tutorial)"
description: "Tutorial: segmentações no Power BI"
services: powerbi
documentationcenter: 
author: mihart
manager: kfile
backup: 
editor: 
tags: 
featuredvideoid: zIZPA0UrJyA
qualityfocus: monitoring
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 05/30/2017
ms.author: mihart
ms.openlocfilehash: b6ce0c396f4a189489b97fe5cd86ab5cd8dbcc35
ms.sourcegitcommit: 284b09d579d601e754a05fba2a4025723724f8eb
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/15/2017
---
# <a name="slicers-in-power-bi-service-tutorial"></a>Segmentações de dados no serviço do Power BI (Tutorial)
O vice-presidente de vendas deseja observar um número de métricas, para toda a divisão e para cada gerente regional individualmente. Ela pode criar uma página de relatório separada para cada gerente ou ela pode usar uma segmentação de dados. Uma segmentação restringe a parte do conjunto de dados mostrado nas outras visualizações na página.  As segmentações são uma maneira alternativa de filtragem.

![](media/power-bi-visualization-slicers/slicer2.gif)

## <a name="when-to-use-a-slicer"></a>Quando usar uma segmentação
Segmentações de dados são uma ótima opção nas seguintes situações.

* Para exibir os filtros mais usados ou importantes na tela de relatório para facilitar o acesso.
* Para facilitar a exibição do estado atual filtrado sem precisar abrir uma lista suspensa para encontrar os detalhes da filtragem.
* Quando desejar ocultar colunas de que não precisa, mas ainda desejar poder usá-las para filtrar - isso torna as tabelas mais estreitas e mais limpas.
* Para criar relatórios mais objetivos, uma vez que as segmentações são objetos flutuantes, você pode colocá-las ao lado da parte interessante do relatório em que você deseja que os usuários se concentrem.

## <a name="create-a-slicer"></a>Criar uma segmentação
<iframe width="560" height="315" src="https://www.youtube.com/embed/zIZPA0UrJyA" frameborder="0" allowfullscreen></iframe>


1. Abra o [Exemplo de Análise de Varejo](sample-retail-analysis.md) em [Editar Exibição](service-interact-with-a-report-in-editing-view.md) e [adicionar uma nova página de relatório](power-bi-report-add-page.md).
2. No painel Campos, selecione **Distrito > Gerente Regional**.
   
    ![](media/power-bi-visualization-slicers/pbi_slicer_chartfirst.png)
3. Converta a visualização em uma segmentação. No painel de Visualizações, selecione o ícone de segmentação.
   
    ![](media/power-bi-visualization-slicers/pbi_slicer_select.png)

## <a name="format-the-slicer"></a>Formatar a segmentação
1. Com a segmentação selecionada, no painel Visualizações, selecione o ícone de rolo de tinta ![](media/power-bi-visualization-slicers/power-bi-paintroller.png) para exibir as opções de Formato.
2. Selecione **Geral > Cor de contorno**, escolha azul escuro e altere o **Peso** para **6**.
   
    ![](media/power-bi-visualization-slicers/pbi_slicer_outline2.png)
3. Em **Controles de Seleção**, por padrão, **Selecionar Tudo** está **Desativado** e **Seleção Única** está **Ativado**. Isso significa que preciso usar a tecla CTRL para selecionar mais de um nome por vez. Marque **Selecionar Tudo** como **Ativado** e **Seleção Única** como **Desativado**.
   
    ![](media/power-bi-visualization-slicers/pbi_slicer_selectioncontrols2.png)
   
   * Observe que a segmentação agora tem uma opção **Selecionar Tudo** na parte superior da lista. Ative/desative **Selecionar Tudo** para selecionar todos os nomes ou para não selecionar nenhum nome.
   * E agora você pode selecionar mais de um nome sem a necessidade de usar a tecla CTRL.
4. Em **Itens**, aumente o tamanho do texto para 14 pt.  Queremos ter certeza de que nossos colegas observem esta segmentação.
5. Por fim, defina **Cor da Fonte** como vermelho escuro.  Isso distinguirá os nomes selecionados dos nomes não selecionados em nossa segmentação.
   
    ![](media/power-bi-visualization-slicers/pbi_slicer_font2.png)
6. Divirta-se explorando as outras opções disponíveis para as segmentações.

## <a name="use-the-slicer-in-a-report"></a>Usar a segmentação em um relatório
1. Adicione algumas visualizações extras à página de relatórios ou abra o [relatório de exemplo de Análise de Varejo](sample-retail-analysis.md) e selecione a guia **Vendas Mensais do Distrito**.
   
    ![](media/power-bi-visualization-slicers/power-bi-retail-sample.png)
2. Segmente a página do relatório para Carlos. Observe como as outras visualizações são atualizadas para refletir essas seleções.
   
    ![](media/power-bi-visualization-slicers/slicer2.gif)
3. Classifique a segmentação em ordem alfabética por sobrenome do Gerente Regional.  Selecione as reticências (...) no canto superior direito da segmentação e escolha **Gerente Regional**.
   
    ![](media/power-bi-visualization-slicers/pbi_slicer_sort2.png)
   
    ![](media/power-bi-visualization-slicers/pbi_slicer_sorted.png)

## <a name="control-what-effect-the-slicer-has-on-other-visuals-on-the-page"></a>Controlar o efeito de segmentação de dados em outros elementos visuais na página
Você deseja que a segmentação de dados filtre somente alguns dos elementos visuais na página de relatório?  Use o controle **Interações visuais** para configurá-la.

**OBSERVAÇÃO**: se você não vir as **Interações Visuais**, procure pelo seu ícone ![](media/power-bi-visualization-slicers/power-bi-slicer-visual-interactions.png). Se não o vir também, verifique se você está no relatório [Modo de Exibição de Edição](service-reading-view-and-editing-view.md).

1. Selecione a segmentação para torná-la ativa e, na barra de menus, escolha **Interações de elementos visuais**.
   
    ![](media/power-bi-visualization-slicers/pbi-slicer-interactions.png)
2. Os controles de filtro serão exibidos acima de todos os outros elementos visuais na página. Se for necessário que a segmentação de dados filtre um visual, selecione o ícone **Filtro**.  Se a segmentação de dados não precisar ter nenhum efeito sobre o visual, selecione o ícone **Nenhum**.
   
    ![](media/power-bi-visualization-slicers/filter-controls.png)

Para obter mais informações, veja a seção [Interações visuais em um relatório do Power BI](service-reports-visual-interactions.md).

## <a name="considerations-and-troubleshooting-slicers-in-power-bi"></a>Considerações e solução de problemas com segmentações no Power BI
Há algumas limitações no uso de segmentações de dados no Power BI, que são as seguintes:

1. As segmentações de dados não dão suporte a campos de entrada.
2. Uma segmentação de dados única não pode ser usada em um relatório inteiro. Uma segmentação de dados afeta somente a página atual.
3. As segmentações de dados não podem ser anexadas a um dashboard.
4. Não há suporte para busca detalhada para segmentações de dados.    
5. As segmentações não dão suporte a filtros de nível Visual.

Você tem algumas ideias para melhorar o Power BI? [Envie uma ideia](https://ideas.powerbi.com/forums/265200-power-bi-ideas).

## <a name="next-steps"></a>Próximas etapas
 [Adicionar uma visualização a um relatório](power-bi-report-add-visualizations-i.md)

 [Tipos de visualização no Power BI](power-bi-visualization-types-for-reports-and-q-and-a.md)

 [Power BI – conceitos básicos](service-basic-concepts.md)

[Experimente – é gratuito!](https://powerbi.com/)

Mais perguntas? [Experimente a Comunidade do Power BI](http://community.powerbi.com/)

