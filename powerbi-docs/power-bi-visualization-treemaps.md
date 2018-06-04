---
title: Mapas de árvore no Power BI
description: Mapas de árvore no Power BI
author: mihart
manager: kfile
ms.reviewer: ''
featuredvideoid: IkJda4O7oGs
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 01/23/2018
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: 8b3f49487677f00e1026c9eab813633f470e6b41
ms.sourcegitcommit: 80d6b45eb84243e801b60b9038b9bff77c30d5c8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34295343"
---
# <a name="treemaps-in-power-bi"></a>Mapas de árvore no Power BI
O treemaps exibe dados hierárquicos, como um conjunto de retângulos aninhados.  Cada nível da hierarquia é representado por um retângulo colorido (muitas vezes chamado uma "ramificação") que contém outros retângulos ("folhas").  O espaço dentro de cada retângulo é alocado com base no valor quantitativo que está sendo medido, os retângulos organizados em tamanho da parte superior esquerda (maior) para a parte inferior direita (menor).

![](media/power-bi-visualization-treemaps/pbi-nancy_viz_treemap.png)

Por exemplo, se eu estou analisando as minhas vendas, posso ter retângulos de nível superior (ramificações) para as categorias de roupas: **Urbana**, **Rural**, **Jovem**, e **Combinada**.  Meus retângulos de categoria contêm retângulos menores (folhas) para os fabricantes de roupas nessa categoria e esses retângulos menores são dimensionados e sombreados com base na quantidade de itens vendidos.  Na ramificação **Urbana** acima, muitas roupas Maximus foram vendidas, menos do que Natura e Fama e muito pouco Leo.  Portanto, a ramificação **Urbana** do meu Mapa de Árvore terá o retângulo maior para Maximus (no canto superior esquerdo), um retângulo um pouco menor para Natura e Fama, muitos outros retângulos representando todas as outras peças de roupa vendidas e um pequeno retângulo para Leo.  Além disso, poderei comparar a quantidade de itens vendidos nas outras categorias de roupas, comparando o tamanho e o sombreamento de cada nó folha: quanto maior o retângulo e mais escuro for o sombreamento, mais alto será o valor.

## <a name="when-to-use-a-treemap"></a>Quando usar um mapa de árvore
Os treemps são uma ótima opção:

* para exibir grandes quantidades de dados hierárquicos.
* Quando um gráfico de barras não puder lidar efetivamente com grande número de valores.
* para mostrar as proporções entre cada parte e o todo.
* para mostrar o padrão da distribuição da medida em cada nível das categorias na hierarquia.
* para mostrar atributos usando a codificação de cor e tamanho.
* para identificar padrões, exceções, colaboradores mais importantes e exceções.

### <a name="prerequisites"></a>Pré-requisitos
 - Serviço do Power BI ou Power BI Desktop
 - Exemplo de análise de varejo

## <a name="create-a-basic-treemap"></a>Criar um mapa de árvore básico
Deseja ver alguém criar um mapa de árvore primeiro?  Pule para 2:10 neste vídeo para assistir Amanda criar um mapa de árvore.

<iframe width="560" height="315" src="https://www.youtube.com/embed/IkJda4O7oGs" frameborder="0" allowfullscreen></iframe>

Se preferir, crie seu próprio mapa de árvore. Essas instruções usam o exemplo de análise de varejo. Para acompanhar, entre no serviço Power BI (não área de trabalho) e selecione **Obter Dados \> Exemplos \> Exemplo de Análise de Varejo \> Conectar\> Ir para o painel**. Criar uma visualização em um relatório requer permissões de edição para o conjunto de dados e o relatório. Felizmente, os exemplos do Power BI são editáveis. Mas, se alguém compartilhar um relatório com você, não será possível adicionar novas visualizações.

1. Selecione o bloco "Armazenamentos Totais" para abrir o relatório Exemplo de Análise de Varejo.    
2. Abra o [Modo de Exibição de Edição](service-interact-with-a-report-in-editing-view.md) e selecione a medida **Vendas** > **Vendas do Ano Passado**.   
   ![](media/power-bi-visualization-treemaps/treemapfirstvalue_new.png)   
3. Converta o gráfico em um mapa de árvore.  
   ![](media/power-bi-visualization-treemaps/treemapconvertto_new.png)   
4. Arraste **Item** > **Categoria** para a seção **Grupo**. O Power BI cria um mapa de árvore no qual o tamanho dos retângulos reflete o total de vendas e a cor representa a categoria.  Na essência que você criou uma hierarquia que descreve visualmente o tamanho relativo do total de vendas por categoria.  A categoria **Mens** categoria tem as maiores vendas e categoria **Hosiery** tem as mais baixos.   
   ![](media/power-bi-visualization-treemaps/treemapcomplete_new.png)   
5. Arraste **Repositório** > **Cadeia** para a seção **Detalhes** para concluir o mapa de árvore. Agora você pode comparar as vendas do ano passado por categoria e cadeia.   
   ![](media/power-bi-visualization-treemaps/treemap_addgroup_new.png)
   
   > [!NOTE]
   > Saturação da cor e os Detalhes não podem ser usados ao mesmo tempo.
   > 
   > 
5. Focalize uma área **Rede** para revelar a dica de ferramenta para essa parte da **Categoria**.  Por exemplo, focalizando **Lindseys** no retângulo **Juniors-040** revela a dica de ferramenta para a parte de Lindsey da categoria Juniors.  
   ![](media/power-bi-visualization-treemaps/treemaphoverdetail_new.png)
6. [Adicione o mapa de árvore como um bloco do dashboard (fixe o visual)](service-dashboard-tiles.md). 
7. [Salve o relatório](service-report-save.md).

## <a name="highlighting-and-cross-filtering"></a>Realce e filtragem cruzada
Para obter informações sobre como usar o painel Filtros, veja [Adicionar um filtro a um relatório](power-bi-report-add-filter.md).

Realçar uma Categoria ou Detalhes em um mapa de árvore filtra e destaca de forma cruzada as outras visualizações na página do relatório e vice-versa. Para acompanhar, adicione alguns elementos visuais à mesma página ou copie/cole o mapa de árvore em uma página de relatório que já tenha outros elementos visuais.

1. No mapa de árvore, selecione uma categoria ou uma cadeia de dentro de uma categoria.  Isso destaca de forma cruzada as outras visualizações na página. Selecionando **050-Shoes**, por exemplo, mostra que as vendas do ano passado de sapatos foram $3.640,471 com US $2.174.185 disso proveniente de Fashions Direct.  
   ![](media/power-bi-visualization-treemaps/treemaphiliting.png)

2. No gráfico de pizza das **Últimas vendas do ano por cadeia**, selecionar a fatia **Fashions Direct** realiza a filtragem cruzada de um mapa de árvore.  
   ![](media/power-bi-visualization-treemaps/treemapnoowl.gif)    

3. Para gerenciar como os gráficos são filtrados e realçados de forma cruzada entre si, veja [Interações de visualização em um relatório do Power BI](service-reports-visual-interactions.md)

## <a name="next-steps"></a>Próximas etapas
[ Fixar uma visualização em um dashboard](service-dashboard-pin-tile-from-report.md)  
[Power BI – conceitos básicos](service-basic-concepts.md)  

Mais perguntas? [Experimente a Comunidade do Power BI](http://community.powerbi.com/)  

