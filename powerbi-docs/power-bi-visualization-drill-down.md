---
title: "Faça uma visualização no Power BI"
description: "Este documento mostra como fazer drill down em uma visualização no serviço do Microsoft Power BI e no Power BI Desktop."
services: powerbi
documentationcenter: 
author: mihart
manager: kfile
backup: 
editor: 
tags: 
featuredvideoid: MNAaHw4PxzE
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 10/18/2017
ms.author: mihart
ms.openlocfilehash: 83c63ee2bed5ae7674223cf2fc3f9241308926e9
ms.sourcegitcommit: 284b09d579d601e754a05fba2a4025723724f8eb
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/15/2017
---
# <a name="drill-down-in-a-visualization-in-power-bi"></a>Faça uma visualização no Power BI
## <a name="drill-down-requires-a-hierarchy"></a>Fazer busca detalhada exige uma hierarquia
Quando um visual tem uma hierarquia, você pode fazer drill down para revelar detalhes adicionais. Por exemplo, você pode ter uma visualização que examina a contagem de medalhas Olímpicas por uma hierarquia composta de esportes, disciplina e eventos. Por padrão, a visualização mostraria a contagem de medalhas por esporte – ginástica, esqui, esportes aquáticos, etc. Mas como ela tem uma hierarquia, selecionar um dos elementos visual (como uma barra, linha ou bolhas), exibiria um quadro cada vez mais detalhado. Selecione o elemento **esportes aquáticos** para ver os dados por natação, mergulho e polo aquático.  Selecione o elemento **mergulho** para ver detalhes de trampolim, plataforma e eventos de mergulho sincronizado.

Você pode adicionar hierarquias para seus próprios relatórios, mas não para os relatórios que foram compartilhados com você.
Não sabe quais visualizações do Power BI contém uma hierarquia?  Passe o mouse sobre uma visualização e se você ver esses controles de análise nos cantos superiores, a visualização tem uma hierarquia.

![](media/power-bi-visualization-drill-down/power-bi-drill-icon4.png)  ![](media/power-bi-visualization-drill-down/power-bi-drill-icon2.png)  ![](media/power-bi-visualization-drill-down/power-bi-drill-icon3.png)
![](media/power-bi-visualization-drill-down/power-bi-drill-icon5.png) ![](media/power-bi-visualization-drill-down/power-bi-drill-icon6.png)  

As datas são um tipo exclusivo de hierarquia. Quando você adiciona um campo de data a uma visualização, o Power BI adiciona automaticamente uma hierarquia de tempo que contém ano, trimestre, mês e dia. Para obter mais informações, consulte [Hierarquias de visuais e comportamento de drill down](guided-learning/visualizations.yml#step-18) ou assista ao vídeo abaixo.

  <iframe width="560" height="315" src="https://www.youtube.com/embed/MNAaHw4PxzE?list=PL1N57mwBHtN0JFoKSR0n-tBkUJHeMP2cP" frameborder="0" allowfullscreen></iframe>

> [!NOTE]
> Para saber como criar hierarquias usando o Power BI Desktop, assista ao vídeo [Como criar e adicionar hierarquias](https://youtu.be/q8WDUAiTGeU)
> 
> 

## <a name="two-methods-to-drill-down"></a>Dois métodos de drill down
Há duas maneiras diferentes de fazer drill down (e drill up) na visualização.  Ambas são descritas neste artigo. Os dois métodos atingem o mesmo objetivo e, portanto, você pode usar o que mais gostar.

> [!NOTE]
> Para seguir adiante, [abra o exemplo de Análise de Varejo](sample-datasets.md) no serviço do Power BI e crie um mapa de árvore que examina **Total de unidades neste ano** (Valores) por **Região**, **Cidade**, **CEP** e **Nome** (Grupo).  
> 
> 

## <a name="method-1-for-drill-down"></a>Método 1 para drill down
Esse método usa os ícones de análise que aparecem nos cantos superiores da própria visualização.

1. No Power BI, abra um relatório no [Modo de Exibição de Leitura](service-report-open-in-reading-view.md) ou no [Modo de Exibição de Edição](service-reading-view-and-editing-view.md). A análise requer uma visualização com uma hierarquia. 
   
   Uma hierarquia é mostrada na animação abaixo.  A visualização tem uma hierarquia composta por região, cidade, CEP e nome de cidade. Cada região tem uma ou mais cidades, cada cidade tem um ou mais códigos postais, etc. Por padrão, a visualização exibe somente os dados da região, porque *Região* aparece em primeiro na lista.
   
   ![](media/power-bi-visualization-drill-down/power-bi-hierarcy-list.png)
2. Para habilitar o drill down, selecione o ícone de seta no canto superior direito da visualização. Quando o ícone estiver escuro, drill está habilitado. Se você não ativar a análise, a seleção de um elemento visual (como uma barra ou bolha) fará uma filtragem cruzada dos outros gráficos na página do relatório.    
   
   ![](media/power-bi-visualization-drill-down/power-bi-drill-icon.png)
3. Para fazer drill down de ***um campo por vez***, clique em um dos elementos na visualização. Em um gráfico de barras, isso significa clicar em uma das barras e em um mapa de árvore, isso significa clicar em uma das *folhas*. Observe que o título se altera conforme você faz drill down e drill up novamente. Nessa animação o titulo muda de "Total de unidades neste ano por região" para "Total unidades neste ano por região e cidade", para "Total de unidades neste ano por região, cidade e CEP" e para "Total de unidades neste ano por região, cidade, CEP e nome". E para fazer drill up, selecione o ícone **Fazer Drill Up** ![](media/power-bi-visualization-drill-down/power-bi-drill-icon5.png)no canto superior esquerdo da visualização conforme mostrado abaixo.
   
   ![](media/power-bi-visualization-drill-down/drill.gif)
4. Para fazer drill down de ***todos os campos de uma só vez***, selecione a seta dupla no canto superior esquerdo da visualização.
   
   ![](media/power-bi-visualization-drill-down/pbi_drillall.png)
5. Para fazer drill up e voltar, selecione a seta para cima no canto superior da visualização.
   
   ![](media/power-bi-visualization-drill-down/pbi_drillup2.png)

## <a name="method-2-for-drill-down"></a>Método 2 para drill down
Esse método usa a lista suspensa **Explorar** da barra de menus superior do Power BI.

1. No Power BI, abra um relatório no [Modo de Exibição de Leitura](service-report-open-in-reading-view.md) ou no [Modo de Exibição de Edição](service-reading-view-and-editing-view.md). A análise requer uma visualização com uma hierarquia. 
   
   Uma hierarquia é mostrada na imagem abaixo.  A visualização tem uma hierarquia composta por região, cidade, CEP e nome de cidade. Cada região tem uma ou mais cidades, cada cidade tem um ou mais códigos postais, etc. Por padrão, a visualização exibe somente os dados da região, porque *Região* aparece em primeiro na lista.
   
   ![](media/power-bi-visualization-drill-down/power-bi-hierarcy-list.png)
2. Para habilitar o drill down, selecione uma visualização para torná-la ativa e, na barra de menu superior do Power BI, selecione **Explorar** > **Fazer Drill Down**. O ícone de busca detalhada no canto superior direito da visualização altera-se para uma tela de fundo preta. ![](media/power-bi-visualization-drill-down/power-bi-drill-icon2.png)  
   
   ![](media/power-bi-visualization-drill-down/power-bi-explore2.png)
3. Uma vez habilitado, faça o drill down de um campo por vez, selecionando uma das folhas do mapa de árvore. Neste exemplo, selecionei a região chamada **NC** para ver o total de unidades vendidas neste ano, por cidade, na Carolina do Norte.
   
   ![](media/power-bi-visualization-drill-down/power-bi-drilldown-1.png)
4. Para fazer drill down de todos campos de uma só vez, selecione **Explorar** > **Mostrar Próximo Nível**.
   
   ![](media/power-bi-visualization-drill-down/power-bi-show-next-level.png)
5. Para fazer drill up, selecione **Explorar** > **Fazer Drill Up**.
   
   ![](media/power-bi-visualization-drill-down/power-bi-drill-up2.png)
6. Para ver os dados usados para criar o visual, selecione **Ver dados**. Os dados são exibidos no painel abaixo do visual. Esse painel permanecerá enquanto você continuar fazendo drill down no visual. Para obter mais informações, consulte [Mostrar dados usados para criar o visual](service-reports-show-data.md).

## <a name="considerations-and-limitations"></a>Considerações e limitações
* Se a adição de um campo de data a uma visualização não criar uma hierarquia, pode ser que o campo "data" não esteja realmente salvo como uma data. Se o conjunto de dados for seu, abra-o na exibição de *Dados* do Power BI Desktop, selecione a coluna que contém a data e, na guia de Modelagem, altere o **Tipo de Dados** para **Data** ou **Data/Hora**. Se o relatório foi compartilhado com você, entre em contato com o proprietário para solicitar a alteração.  
  
  ![](media/power-bi-visualization-drill-down/power-bi-change-data-type2.png)

## <a name="next-steps"></a>Próximas etapas
[Visualizações em relatórios do Power BI](power-bi-report-visualizations.md)

[Relatórios do Power BI](service-reports.md)

[Power BI – conceitos básicos](service-basic-concepts.md)

Mais perguntas? [Experimente a Comunidade do Power BI](http://community.powerbi.com/)

