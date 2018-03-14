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
ms.date: 02/26/2018
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: fb834c92953c2cafcbca77bc1b3828b385755bca
ms.sourcegitcommit: 743e44fc8730fea0f7149916080b0c6d7eb6359d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/28/2018
---
# <a name="drill-down-in-a-visualization-in-power-bi"></a>Faça uma visualização no Power BI
## <a name="drill-down-requires-a-hierarchy"></a>Fazer busca detalhada exige uma hierarquia
Quando um visual tem uma hierarquia, você pode fazer drill down para revelar detalhes adicionais. Por exemplo, você pode ter uma visualização que examina a contagem de medalhas Olímpicas por uma hierarquia composta de esportes, disciplina e eventos. Por padrão, a visualização mostraria a contagem de medalhas por esporte – ginástica, esqui, esportes aquáticos e assim por diante. Mas como ela tem uma hierarquia, selecionar um dos elementos visuais (como uma barra, linha ou bolhas), exibiria um quadro cada vez mais detalhado. Selecione o elemento **esportes aquáticos** para ver os dados por natação, mergulho e polo aquático.  Selecione o elemento **mergulho** para ver detalhes de trampolim, plataforma e eventos de mergulho sincronizado.

É possível adicionar hierarquias a relatórios que você tem, mas não aos compartilhados com você.
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
Há duas maneiras de fazer drill down (e drill up) em sua visualização.  Ambas são descritas neste artigo. Os dois métodos atingem o mesmo objetivo e, portanto, você pode usar o que mais gostar.

> [!NOTE]
> Para seguir adiante, [abra o exemplo de Análise de Varejo](sample-datasets.md) no serviço do Power BI e crie um mapa de árvore que examina **Total de unidades neste ano** (Valores) por **Região**, **Cidade**, **CEP** e **Nome** (Grupo).  
> 
> 

## <a name="method-one-for-drill-down"></a>Método Um para drill down
Esse método usa os ícones de análise que aparecem nos cantos superiores da própria visualização.

1. No Power BI, abra um relatório no [modo de exibição de Leitura ou no modo de exibição de Edição](service-reading-view-and-editing-view.md). A análise requer uma visualização com uma hierarquia. 
   
   Uma hierarquia é mostrada na animação abaixo.  A visualização tem uma hierarquia composta por região, cidade, CEP e nome de cidade. Cada região tem uma ou mais cidades, cada cidade tem um ou mais códigos postais e assim por diante. Por padrão, a visualização exibe somente os dados da região, porque *Região* aparece em primeiro na lista.
   
   ![](media/power-bi-visualization-drill-down/power-bi-hierarcy-list.png)
2. Para habilitar o drill down, selecione o ícone de seta no canto superior direito da visualização. Quando o ícone estiver escuro, drill está habilitado. Se você não ativar a análise, a seleção de um elemento visual (como uma barra ou bolha) fará uma filtragem cruzada dos outros gráficos na página do relatório.    
   
   ![](media/power-bi-visualization-drill-down/power-bi-drill-icon.png)
3. Para fazer drill down de **um campo por vez**, selecione um dos elementos da visualização. Em um gráfico de barras, isso significa clicar em uma das barras. Em um mapa de árvore, isso significa clicar em uma das **folhas**. Observe que o título se altera conforme você faz drill down e drill up novamente. Nessa animação, ele muda de "Total de unidades neste ano por território" para "Total de unidades neste ano por território e cidade" e, em seguida, para "Total de unidades neste ano por Território, Cidade e CEP" para "Total de unidades neste ano por Território, Cidade, CEP e Nome. E para fazer drill up de volta, selecione o ícone **Fazer drill up** ![](media/power-bi-visualization-drill-down/power-bi-drill-icon5.png) no canto superior esquerdo da visualização conforme mostrado abaixo.
   
   ![](media/power-bi-visualization-drill-down/drill.gif)
4. Para fazer drill down de ***todos os campos de uma só vez***, selecione a seta dupla no canto superior esquerdo da visualização.
   
   ![](media/power-bi-visualization-drill-down/pbi_drillall.png)
5. Para fazer drill up de volta, selecione a seta para cima no canto superior esquerdo da visualização.
   
   ![](media/power-bi-visualization-drill-down/pbi_drillup2.png)

## <a name="method-two-for-drill-down"></a>Método Dois para fazer drill down
Esse método usa a lista suspensa **Explorar** da barra de menus superior do Power BI.

1. No Power BI, abra um relatório no [modo de exibição de Leitura ou no modo de exibição de Edição](service-reading-view-and-editing-view.md). A análise requer uma visualização com uma hierarquia. 
   
   Uma hierarquia é mostrada na imagem abaixo.  A visualização tem uma hierarquia composta por região, cidade, CEP e nome de cidade. Cada região tem uma ou mais cidades, cada cidade tem um ou mais códigos postais e assim por diante. Por padrão, a visualização exibe somente os dados da região, porque *Região* aparece em primeiro na lista.
   
   ![](media/power-bi-visualization-drill-down/power-bi-hierarcy-list.png)
2. Para habilitar o drill down, selecione uma visualização para torná-la ativa e, na barra de menus superior do Power BI, selecione **Explorar** > **drill down**. O ícone de drill down no canto superior direito da visualização é alterado para uma tela de fundo preta. ![](media/power-bi-visualization-drill-down/power-bi-drill-icon2.png)  
   
   ![](media/power-bi-visualization-drill-down/power-bi-explore2.png)
3. Uma vez habilitado, faça o drill down de um campo por vez, selecionando uma das folhas do mapa de árvore. Neste exemplo, o território denominado **NC** é selecionado para ver o total de unidades vendidas neste ano, por cidade, na Carolina do Norte.
   
   ![](media/power-bi-visualization-drill-down/power-bi-drilldown-1.png)
4. Para fazer drill down de todos campos de uma só vez, selecione **Explorar** > **Mostrar Próximo Nível**.
   
   ![](media/power-bi-visualization-drill-down/power-bi-show-next-level.png)
5. Para fazer drill up, selecione **Explorar** > **Fazer Drill Up**.
   
   ![](media/power-bi-visualization-drill-down/power-bi-drill-up2.png)

6. Para ver os dados em uso para criar o visual, selecione **Ver dados**. Os dados são exibidos em um painel embaixo do visual. Esse painel permanecerá enquanto você continuar fazendo drill down no visual. Para obter mais informações, consulte [Mostrar dados usados para criar o visual](service-reports-show-data.md).

## <a name="understanding-the-hierarchy-axis-and-hierarchy-group"></a>Noções básicas de eixo de hierarquia e grupo de hierarquias
É possível pensar no eixo de hierarquia e no grupo de hierarquias como os mecanismos que podem ser usados para aumentar e diminuir a granularidade dos dados que você deseja exibir. Todos os dados que podem ser organizados em categorias e subcategorias são qualificados como tendo uma hierarquia. Isso, obviamente, inclui as datas e horas.

É possível criar uma visualização no Power BI para ter uma hierarquia selecionando um ou mais campos de dados a serem adicionados ao contêiner **Eixo** ou ao contêiner **Grupo**, juntamente com os dados que você deseja examinar como campos de dados no contêiner **Valores**. Você saberá se seus dados forem hierárquicos se os ícones de Modo de análise forem exibidos nos cantos superiores esquerdo e direito de sua visualização. 

Essencialmente, é conveniente pensar em dois tipos de dados hierárquicos:
- Dados de data e hora – se você tiver um campo de dados com um tipo de dados DateTime, já terá os dados hierárquicos. O Power BI cria automaticamente uma hierarquia para qualquer campo de dados cujos valores podem ser analisados em uma estrutura [DateTime](https://msdn.microsoft.com/library/system.datetime.aspx). Só é necessário adicionar um campo DateTime ao contêiner **Eixo** ou **Grupo**.
- Dados categóricos – se os dados forem derivados de coleções que contenham subcoleções ou, caso contrário, tenham linhas de dados que compartilham valores comuns, você terá dados hierárquicos.

O Power BI permite expandir em um subconjunto ou em todos. É possível fazer drill down em seus dados para ver um subconjunto único em cada nível ou para ver todos os subconjuntos simultaneamente em cada nível. Por exemplo, é possível fazer drilldown de um ano específico ou ver todos os resultados de cada ano à medida que você percorre a hierarquia. Por outro lado, é possível fazer drill up da mesma maneira.

As seções a seguir descrevem como fazer drill down do modo de exibição mais alto, médio e mais baixo.

### <a name="hierarchical-data-and-time-data"></a>Dados hierárquicos e dados de tempo
Neste exemplo, acompanhe o [exemplo de Análise de varejo](sample-datasets.md) e crie uma visualização de gráfico de colunas empilhadas que examina **Mês** (Eixo) por **TotalSales** (Valores).  

Embora o campo de dados Eixo seja **Mês**, ele ainda cria uma categoria **Ano** no contêiner **Eixo**. Isso ocorre, porque o Power BI fornece a estrutura DateTime completa para todos os valores que ela lê. A parte superior da hierarquia mostra os dados do ano.

![](media\power-bi-visualization-drill-down/power-bi-hierarchical-axis-datetime-1.png)

Com o modo de drill down ativado, clique na barra no gráfico para descer um nível da hierarquia. Você verá três barras para os dados dos trimestres disponíveis. Em seguida, nos ícones do canto superior esquerdo, escolha **Expandir todo o campo um nível abaixo na hierarquia**. Em seguida, faça novamente para obter o nível mais baixo da hierarquia, que mostra os resultados para cada mês.

![](media\power-bi-visualization-drill-down/power-bi-hierarchical-axis-datetime-2.png)

Além da visualização, é possível ver a hierarquia refletida nos dados renderizados para cada relatório. A tabela a seguir mostra os resultados de **Mostrar dados** em um relatório que faz drill down de um único mês ou de todos os meses. 

Observe que os dados são os mesmos para relatórios trimestrais e anuais, mas, depois de fazer drill down para o nível de detalhe especificado para **Valores**, será possível ver como o único relatório fica mais específico e como o relatório de "todos os meses" tem mais dados.


|Modo de expansão|Ano|Trimestre|Mês|Dia|
| ---|:---:|:---:|:---:|---|
|Único|![](media\power-bi-visualization-drill-down/power-bi-hierarchical-year.png)|![](media\power-bi-visualization-drill-down/power-bi-hierarchical-quarter.png)|![](media\power-bi-visualization-drill-down/power-bi-hierarchical-one-month.png)|![](media\power-bi-visualization-drill-down/power-bi-hierarchical-one-day.png)|
|Tudo|![](media\power-bi-visualization-drill-down/power-bi-hierarchical-year.png)|![](media\power-bi-visualization-drill-down/power-bi-hierarchical-quarter.png)|![](media\power-bi-visualization-drill-down/power-bi-hierarchical-all-month.png)|![](media\power-bi-visualization-drill-down/power-bi-hierarchical-all-day.png)|


### <a name="hierarchical-category-data"></a>Dados de categoria hierárquica
Os dados que foram modelados de coleções e subcoleções são hierárquicos. Um bom exemplo disso são os dados de localização. Considere uma tabela em uma fonte de dados cujas colunas são País, Estado, Cidade e CEP. Dados que compartilham o mesmo País, Estado e Cidade são hierárquicos.

Neste exemplo, acompanhe o [exemplo de Análise de varejo](sample-datasets.md). Crie uma visualização de gráfico de colunas empilhadas que examina **Total de unidades deste ano** (Valores) por **Território**, **Cidade**, **PostalCode** e **Nome** (Grupo).  

![](media\power-bi-visualization-drill-down/power-bi-hierarchical-axis-category-1.png)

Com o modo de drill down ativado, nos ícones do canto superior esquerdo, escolha **Expandir todo o campo um nível abaixo na hierarquia** três vezes.
Você deve estar no nível mais baixo da hierarquia, que mostra os resultados de Território, Cidade e CEP.

![](media\power-bi-visualization-drill-down/power-bi-hierarchical-axis-category-2.png)

Além da visualização, é possível ver a hierarquia refletida nos dados renderizados para cada relatório. A tabela a seguir mostra os resultados de **Mostrar dados** em um relatório que faz drill down de um único território ou de todos os territórios. À medida que você faz drill down, é possível ver como o único relatório fica mais específico e como o relatório de "todos os territórios" tem mais dado.


| Modo de expansão|Região|Cidade|CEP|Nome|
| ---|:---:|:---:|:---:|---|
|Único|![](media\power-bi-visualization-drill-down/power-bi-hierarchical-territory.png)|![](media\power-bi-visualization-drill-down/power-bi-hierarchical-one-territory-city.png)|![](media\power-bi-visualization-drill-down/power-bi-hierarchical-one-territory-city-postal.png)|![](media\power-bi-visualization-drill-down/power-bi-hierarchical-one-territory-city-postal-name.png)|
|Tudo|![](media\power-bi-visualization-drill-down/power-bi-hierarchical-territory.png)|![](media\power-bi-visualization-drill-down/power-bi-hierarchical-all-territory-city.png)|![](media\power-bi-visualization-drill-down/power-bi-hierarchical-all-territory-city-postal.png)|![](media\power-bi-visualization-drill-down/power-bi-hierarchical-all-territory-city-postal-name.png)|


## <a name="considerations-and-limitations"></a>Considerações e limitações
* Se a adição de um campo de data a uma visualização não criar uma hierarquia, pode ser que o campo "data" não esteja realmente salvo como uma data. Se o conjunto de dados for seu, abra-o na exibição de *Dados* do Power BI Desktop, selecione a coluna que contém a data e, na guia de Modelagem, altere o **Tipo de Dados** para **Data** ou **Data/Hora**. Se o relatório foi compartilhado com você, entre em contato com o proprietário para solicitar a alteração.  
  
  ![](media/power-bi-visualization-drill-down/power-bi-change-data-type2.png)

## <a name="next-steps"></a>Próximas etapas
[Visualizações em relatórios do Power BI](power-bi-report-visualizations.md)

[Relatórios do Power BI](service-reports.md)

[Power BI – conceitos básicos](service-basic-concepts.md)

Mais perguntas? [Experimente a Comunidade do Power BI](http://community.powerbi.com/)

