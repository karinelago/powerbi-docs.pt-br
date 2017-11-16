---
title: "Visualizações de tabela em relatórios e dashboards do Power BI (Tutorial)"
description: "Dicas para trabalhar com visualizações de tabela em relatórios e painéis do Power BI, incluindo como redimensionar larguras de coluna."
services: powerbi
documentationcenter: 
author: mihart
manager: kfile
backup: 
editor: 
tags: 
featuredvideoid: 
qualityfocus: 
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 10/27/2017
ms.author: mihart
ms.openlocfilehash: e4a2e162ca193af756e7182fb118bc7e72d38d28
ms.sourcegitcommit: 99cc3b9cb615c2957dde6ca908a51238f129cebb
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/13/2017
---
# <a name="working-with-tables-in-power-bi-reports-and-dashboards-tutorial"></a>Trabalhando com tabelas em relatórios e painéis do Power BI (Tutorial)
Uma tabela é uma grade que contém dados relacionados em uma série de lógica de linhas e colunas. Ela também pode conter cabeçalhos e linhas de totais. As tabelas funcionam bem com comparações quantitativas em que você observa muitos valores de uma única categoria. Por exemplo, esta tabela exibe 5 medidas diferentes para a **Categoria**.

![](media/power-bi-visualization-tables/table.png)

## <a name="when-to-use-a-table"></a>Quando usar uma tabela
As tabelas são uma ótima opção:

* para ver e comparar dados detalhados e valores exatos (em vez de representações visuais)
* para exibir dados em um formato tabular
* para exibir dados numéricos por categorias   

> [!NOTE]
> Se uma tabela tiver muitos valores, considere a possibilidade de convertê-la em uma matriz e/ou utilizar a análise detalhada.
> 
> 

## <a name="create-a-table"></a>Criar uma tabela
Para acompanhar, entre no Power BI e selecione **Obter Dados > Amostras > Amostra de Análise de Varejo**. Vamos criar a tabela mostrada acima para exibir valores de vendas por categoria de item.

1. Em **Meu espaço de trabalho**, selecione a guia Conjuntos de dados e role para baixo até o conjunto de dados Exemplo de Análise de Varejo recém-criado.  Selecione o ícone **Criar relatório**.
   
    ![](media/power-bi-visualization-tables/power-bi-create-report.png)
2. No editor de relatórios, selecione **Item** > **Categoria**.  O Power BI cria automaticamente uma tabela que lista todas as categorias.
   
    ![](media/power-bi-visualization-tables/power-bi-table1.png)
3. Selecione **Vendas > Preço da unidade médio**, **Vendas > Vendas do último ano** e **Vendas > Vendas deste ano** e escolha todas as três opções (Valor, Meta, Status).   
4. No painel de Visualizações, localize a seção **Valores** e arraste e solte os valores até que a ordem das colunas do gráfico correspondam à primeira imagem nesta página.  A seção Valores deve ficar com esta aparência.
   
    ![](media/power-bi-visualization-tables/power-bi-table2.png)
5. Fixe a tabela ao painel, selecionando o ícone de fixar  
   
     ![](media/power-bi-visualization-tables/pbi_pintile.png)

## <a name="format-the-table"></a>Formatar a tabela
Há muitas maneiras de formatar uma tabela e nós só abordaremos algumas delas. Uma ótima maneira de conhecer outras opções de formatação é abrir o painel Formatação (ícone de rolo de pintura ![](media/power-bi-visualization-tables/power-bi-format.png)) e explorar.

* Experimente formatar a grade de tabela. Aqui nós adicionamos uma grade vertical azul, adicionamos espaço às linhas, aumentamos a estrutura de tópicos e o tamanho do texto um pouco.
  
    ![](media/power-bi-visualization-tables/power-bi-table-grid2-new.png)
  
    ![](media/power-bi-visualization-tables/power-bi-table-grid3.png)
* Para os cabeçalhos da coluna, alteramos a cor da tela de fundo, adicionamos uma estrutura de tópicos e aumentamos o tamanho da fonte. 
  
    ![](media/power-bi-visualization-tables/power-bi-table-column.png)
  
    ![](media/power-bi-visualization-tables/power-bi-table-column2.png)
* E depois de uma formatação adicional, veja nossa tabela definitiva. Como há muitas opções de formatação, a melhor maneira de aprender é começar com uma tabela básica, abrir o painel de formatação ![](media/power-bi-visualization-tables/power-bi-format.png) e começar a explorar. 
  
    ![](media/power-bi-visualization-tables/power-bi-table-format.png)

### <a name="conditional-formatting"></a>Formatação condicional
Um tipo de formatação é conhecido como *formatação condicional* e aplica-se a campos em **Valores** no painel **Visualizações** no serviço do Power BI ou Desktop. 

Com a formatação condicional para tabelas, você pode especificar as cores da tela de fundo de células personalizadas e as cores das fontes com base nos valores da célula, inclusive usando cores de gradiente. 

1. No painel **Visualizações** no serviço do Power BI ou Desktop, selecione a seta para baixo ao lado do valor em **Valores** que você deseja formatar (ou clique com o botão direito do mouse no campo). Você pode gerenciar somente a formatação condicional para campos na área **Valores** também em **Campos**.
   
    ![](media/power-bi-visualization-tables/power-bi-conditional-formatting-background.png)
2. Selecione **Escalas de cores da tela de fundo**. Na caixa de diálogo que aparece, você pode definir a cor, bem como os valores *Mínimo* e *Máximo*. Se selecionar a caixa **Divergente**, você também poderá configurar um valor opcional para o *Centro*.
   
    ![](media/power-bi-visualization-tables/power-bi-conditional-formatting-background2.png)
   
    Vamos aplicar uma formatação personalizada aos valores de Preço unitário médio. Selecione **Divergente**, adicione algumas cores e escolha **OK**. 
   
    ![](media/power-bi-visualization-tables/power-bi-conditional-formatting-data-background.png)
3. Adicione um novo campo à tabela que tem valores positivos e negativos.  Selecione **Campos > Variação do Total de Vendas**. 
   
    ![](media/power-bi-visualization-tables/power-bi-conditional-formatting2.png)
4. Adicione formatação condicional de barra de dados selecionando a seta para baixo ao lado de **Variação do Total de Vendas** e escolhendo **Formatação condicional > Barras de dados**.
   
    ![](media/power-bi-visualization-tables/power-bi-conditional-formatting-data-bars.png)
5. Na caixa de diálogo exibida, defina cores para **barra positiva**, **barra negativa**, marque a caixa de seleção ao lado de **Mostrar apenas a barra** e faça outras alterações desejadas.
   
    ![](media/power-bi-visualization-tables/power-bi-data-bars.png)
   
    Quando você seleciona **OK**, as barras de dados substituem os valores numéricos na tabela, facilitando a verificação.
   
    ![](media/power-bi-visualization-tables/power-bi-conditional-formatting-data-bars2.png)
6. Para remover a formatação condicional de uma visualização, basta clicar com o botão direito do mouse no campo novamente e selecionar **Remover formatação condicional**.

> [!TIP]
> A formatação condicional também está disponível no painel Formatação (ícone de rolo de tinta). Selecione o valor a ser formatado e, em seguida, defina **Escalas de cores** ou **Barras de dados** como Ativado para aplicar as configurações padrão ou, para personalizar as configurações, selecione **Controles avançados**.
> 
> 

## <a name="adjust-the-column-width-of-a-table"></a>Ajustar a largura da coluna de uma tabela
Às vezes, o Power BI vai truncar um título de coluna em um relatório e em um painel. Para mostrar todo o nome da coluna, passe o mouse sobre o espaço à direita do título para revelar as setas duplas, selecionar e arrastar.

![](media/power-bi-visualization-tables/resizetable.gif)

Mais perguntas? [Experimente a Comunidade do Power BI](http://community.powerbi.com/)

