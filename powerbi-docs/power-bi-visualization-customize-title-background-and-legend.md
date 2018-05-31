---
title: Introdução à formatação de visualizações do Power BI
description: Personalizar o título, tela de fundo e legenda da visualização
author: mihart
manager: kfile
ms.reviewer: ''
featuredvideoid: IkJda4O7oGs
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 01/22/2018
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: d65281539bcc27ce24971a6da0945908ba65e754
ms.sourcegitcommit: 638de55f996d177063561b36d95c8c71ea7af3ed
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/17/2018
ms.locfileid: "34297091"
---
# <a name="customize-visualization-titles-legends-and-backgrounds"></a>Personalizar títulos, legendas e telas de fundo de visualizações
Neste tutorial, você aprenderá várias maneiras diferentes de personalizar as visualizações.   Há inúmeras opções para personalizar as visualizações e a melhor maneira de saber mais sobre todas elas é explorar o painel de formatação (selecione o ícone do rolo de tinta).  Para começar, este artigo mostrará como personalizar o título, a legenda e a tela de fundo de uma de visualização.  

Nem todas as visualizações podem ser personalizadas; [veja a lista completa](#list).  

Assista à Amanda personalizar visualizações em seu relatório (avance até 4:50 no vídeo). Em seguida, siga as instruções abaixo do vídeo para experimentar por conta própria com seus dados.

<iframe width="560" height="315" src="https://www.youtube.com/embed/IkJda4O7oGs" frameborder="0" allowfullscreen></iframe>

### <a name="prerequisites"></a>Pré-requisitos
- Serviço do Power BI ou Power BI Desktop
- Exemplo de análise de varejo

## <a name="customize-visualization-titles-in-reports"></a>Personalizar títulos de visualização em relatórios
Para acompanhar, entre no serviço Power BI (app.powerbi.com) e abra o relatório [Exemplo de Análise de Varejo](sample-datasets.md) no [Modo de Edição de Exibição](service-interact-with-a-report-in-editing-view.md).

> [!NOTE]
> Ao fixar uma visualização em um dashboard, ela se torna um bloco do dashboard.  Os próprios blocos também podem ser personalizados com [novos títulos e subtítulos, bem como hiperlinks, e podem ser redimensionados](service-dashboard-edit-tile.md).
> 
> 

1. Navegue até a página "Nossas Lojas" do relatório e selecione o gráfico de colunas "Abrir contagem de armazenamento por mês em aberto...".
2. No painel Visualizações, selecione o ícone de rolo de tinta para ver as opções de formatação.  Selecione **Título** para expandir essa seção.  
   
   ![](media/power-bi-visualization-customize-title-background-and-legend/power-bi-formatting-menu.png)
3. Ative e desative o  **Título** selecionando o controle deslizante Ativar (ou Desativar). Por enquanto, deixe em **Ativar**.  
   
   ![](media/power-bi-visualization-customize-title-background-and-legend/onoffslider.png)
4. Altere o **Texto do Título** digitando **Contagem de armazenamento por mês em aberto** no campo de texto.  
5. Altere a **Cor da fonte** para cor de laranja e a **Cor do Plano de Fundo** para amarelo.
   
   * Selecione o menu suspenso e escolha uma cor em **Cores do Tema**, **Cores Recentes**ou **Cores Personalizadas**.
   * Selecione o menu suspenso para fechar a janela de cores.  
     ![](media/power-bi-visualization-customize-title-background-and-legend/customizecolorpicker.png)
   
   Você sempre poderá voltar para as cores padrão selecionando **Reverter para o padrão** na janela de cores.
6. Aumente o tamanho do texto para 12.
7. A última personalização que faremos no título do gráfico é alinhá-lo no centro da visualização. A posição do título por padrão é alinhada à esquerda.  
   ![](media/power-bi-visualization-customize-title-background-and-legend/customizealign.png)
   
    Nesse ponto no tutorial, o **título** do gráfico de colunas deve ser assim:  
    ![](media/power-bi-visualization-customize-title-background-and-legend/tutorialprogress1.png)
   
    Para reverter toda a personalização de título que fizemos até agora, selecione **Reverter para Padrão**na parte inferior do painel de personalização **Título** .  
    ![](media/power-bi-visualization-customize-title-background-and-legend/revertall.png)

## <a name="customize-visualization-backgrounds"></a>Personalizar planos de fundo de visualização
Com o mesmo gráfico de coluna selecionado, expanda as opções de tela de fundo.

1. Ative e desative a tela de fundo selecionando o controle deslizante Ativar (ou Desativar). Por enquanto, deixe em **Ativar**.
2. Altere a cor da tela de fundo para 74% cinza.
   
   * Selecione o menu suspenso e escolha uma cor em **Cores do Tema**, **Cores Recentes** ou **Cores Personalizadas**.
   * Altere a Transparência para 74%.   
     ![](media/power-bi-visualization-customize-title-background-and-legend/power-bi-customize-background.png)
   
   Para reverter a personalização de tela de fundo do título que fizemos até agora, selecione **Reverter para padrão**na parte inferior do painel de personalização **Plano de fundo** .

## <a name="customize-visualization-legends"></a>Personalizar legendas de visualização
1. Abra a página **Visão geral** do relatório e selecione o gráfico "Variação das vendas totais por mês fiscal e gerente do distrito".
2. Na guia de Visualização, selecione o ícone de pincel para abrir o painel de formatação.  
3. Expanda as opções de **Legenda** .
   
      ![](media/power-bi-visualization-customize-title-background-and-legend/legend.png)
4. Ative e desative a legenda selecionando o controle deslizante Ativar (ou Desativar). Por enquanto, deixe em **Ativar**.
5. Mova a legenda para a esquerda da visualização.    
6. Adicione um título de legenda alternando o **Título** para **Ativado** e, no campo **Nome da legenda** , digitando **Gerentes**.
   ![](media/power-bi-visualization-customize-title-background-and-legend/legend-move.png)
   
   Para reverter toda a personalização de legenda que fizemos até agora, selecione **Reverter para Padrão**na parte inferior do painel de personalização **Legenda** .

<a name="list"></a>

## <a name="visualization-types-that-can-be-customized"></a>Tipos de visualização que podem ser personalizados
| Visualização | Título | Tela de fundo | Legenda |
|:--- |:--- |:--- |:--- |
| área |sim |sim |sim |
| barra |sim |sim |sim |
| cartão |sim |sim |n/a |
| cartão com várias linhas |sim |sim |n/a |
| coluna |sim |sim |sim |
| combinação |sim |sim |sim |
| rosca |sim |sim |sim |
| mapa coroplético |sim |sim |sim |
| funil |sim |sim |n/a |
| medidor |sim |sim |n/a |
| kpi |sim |sim |n/a |
| linha |sim |sim |sim |
| mapa |sim |sim |sim |
| matriz |sim |sim |n/a |
| pizza |sim |sim |sim |
| dispersão |sim |sim |sim |
| segmentação de dados |sim |sim |n/a |
| tabela |sim |sim |n/a |
| caixa de texto |não |sim |n/a |
| mapa de árvore |sim |sim |sim |
| cascata |sim |sim |sim |

## <a name="next-steps"></a>Próximas etapas
[Personalizar os eixos x e y](power-bi-visualization-customize-x-axis-and-y-axis.md)  
[Personalizar cores e propriedades de eixo](service-getting-started-with-color-formatting-and-axis-properties.md)  
[Power BI – conceitos básicos](service-basic-concepts.md)  
Mais perguntas? [Experimente a Comunidade do Power BI](http://community.powerbi.com/)

