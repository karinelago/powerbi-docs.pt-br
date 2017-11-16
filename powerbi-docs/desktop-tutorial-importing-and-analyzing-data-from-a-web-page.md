---
title: "Tutorial: importando e analisando dados de uma página da Web com o Power BI Desktop"
description: "Tutorial: importando e analisando dados de uma página da Web com o Power BI Desktop"
services: powerbi
documentationcenter: 
author: davidiseminger
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
ms.date: 07/20/2017
ms.author: davidi
ms.openlocfilehash: 1ffbf698f3a53aa1075cf62f2e05467dcde73cee
ms.sourcegitcommit: 99cc3b9cb615c2957dde6ca908a51238f129cebb
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/13/2017
---
# <a name="analyzing-web-page-data-using-power-bi-desktop-tutorial"></a>Analisando dados de página da Web usando o Power BI Desktop (tutorial)
Neste tutorial, você aprenderá como importar uma tabela de dados de uma página da Web e criar um relatório para visualizar esses dados. Como parte desse processo, você navega pelas tabelas disponíveis em uma página da Web e aplica as etapas de transformação de dados para remodelar a tabela em um novo formato.

 Neste artigo:

* **Tarefa 1:** Conectar-se a uma fonte de dados da Web
* **Tarefa 2**: Formatar dados no modo de exibição de Consulta
  * Etapa 1: Remover Outras Colunas para exibir apenas as colunas de interesse
  * Etapa 2: Substituir Valores para limpar os valores em uma coluna selecionada
  * Etapa 3: Filtrar valores em uma coluna
  * Etapa 4: Renomear uma coluna
  * Etapa 5: Filtrar valores nulos em uma coluna
  * Etapa 6: Renomear uma consulta
  * Etapas de Consulta criadas
* **Tarefa 3:** Criar visualizações usando o modo de exibição de Relatório
  * Etapa 1: Carregar a consulta em seu relatório
  * Etapa 2: Criar uma visualização de Mapa

## <a name="task-1-connect-to-a-web-data-source"></a>Tarefa 1: Conectar-se a uma fonte de dados da Web
 Na tarefa 1, você importa uma tabela com a Síntese do Torneio na página do Campeonato Europeu de futebol da UEFA da Wikipédia, em: https://pt.wikipedia.org/wiki/Campeonato\_Europeu\_de\_Futebol

![](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/webpage1.png)

### <a name="add-a-wikipedia-page-data-source"></a>Adicionar uma fonte de dados de página da Wikipedia
1. No diálogo **Introdução** ou na **guia de faixa de opções Home**, selecione **Obter Dados**.
2. Isso abre a caixa de diálogo **Obter Dados** , na qual você pode escolher entre uma grande variedade de fontes de dados para importar dados no Power BI Desktop. Selecionaremos **Web** , que está disponível no grupo **Todas** ou **Outras** .
3. Na caixa de diálogo **Conteúdo da Web**, na caixa de texto **URL**, cole a URL da Wikipedia (https://pt.wikipedia.org/wiki/Campeonato\_Europeu\_de\_Futebol).
4. Clique em **OK**.

Depois de estabelecer uma conexão com a página da Web, você deve ver uma lista das tabelas disponíveis nessa página da Wikipédia na caixa de diálogo **Navegador** . Você pode clicar uma vez com o mouse em cada uma dessas tabelas para visualizar os respectivos dados.

No painel esquerdo **Navegador** , clique na tabela **Results[edit]** para obter os resultados do Resumo do Torneio, ou selecione a tabela **Results[edit]** e clique em **Editar**. Isso nos permitirá alterar essa tabela antes de carregá-la no Relatório, já que os dados não estão no formato que precisamos para nossa análise.

![](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/tutorialimanaly_navigator.png)

Isso fará com que uma visualização da tabela apareça no Modo de Exibição de Consulta, no qual é possível aplicar um conjunto de etapas de transformação para limpar os dados.

![](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/webpage3.png)

## <a name="task-2-shape-data-in-the-subject-table"></a>Tarefa 2: Formatar os dados na tabela da entidade
Agora que a tabela da entidade está selecionada para sua consulta de dados, você aprenderá a realizar diversas etapas de formatação e limpeza de dados.

**Etapa 1:** Remover Outras Colunas para exibir apenas as colunas de interesse

Nesta etapa, você removerá todas as colunas, exceto **Year** e **Final Winners**.

1. Na grade **Visualização de Consulta**, selecione as colunas **Year** e **Final Winners** (use **CTRL** + **Clique**).
2. Clique com o botão direito do mouse em um título de coluna na grade **Visualização de Consulta** e clique em **Remover Outras Colunas** para remover as colunas não selecionadas. É importante lembrar que essa operação também está disponível na guia de faixa de opções **Página Inicial** , no grupo **Gerenciar Colunas** .

![](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/webpage4.png)

**Etapa 2:** Substituir Valores para limpar os valores em uma coluna selecionada

Nesta etapa, você substituirá o sufixo Detalhes da coluna **Year** . Observe que esse sufixo é em uma nova linha, portanto, não é visível na visualização da tabela. No entanto, se clicar em uma das células com um valor numérico na coluna ano, você verá o valor total na exibição detalhada.

![](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/webpage5.png)

1. Selecione a coluna **Year** .
2. Na faixa de opções da **Visualização da Consulta** , clique em **Substituir Valores** na guia **Página Inicial** , ou clique com o botão direito do mouse na coluna **Year** e clique em **Substituir Valores** para substituir Detalhes por texto vazio.
3. Na caixa de diálogo **Substituir Valores** , digite Detalhes na caixa de texto **Valor a Encontrar** e deixe a caixa de texto **Substituir Por** vazia.
4. Clique em **OK**.

![](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/webpage6.png)

 **Etapa 3:** Filtrar valores em uma coluna

Nesta etapa, você filtrará a coluna **Year** para exibir linhas que não contêm “Year”.

1. Clique na seta do menu suspenso de filtragem na coluna **Year** .
2. No menu suspenso **Filtro** , limpe a opção **Ano** .
3. Clique em **OK**.

![](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/webpage7.png)

**Etapa 4:** Renomear uma coluna

Agora que limpamos os dados na coluna **Year** , vamos trabalhar na coluna **Final Winner** .

Já que estamos apenas observando a lista de vencedores, podemos renomear esta coluna como **Country**.

1. Selecione a coluna **Vencedor Final** na visualização de Consulta.
2. Na faixa de opções de **Visualização da Consulta** , na guia **Transformar** e no grupo **Qualquer Coluna** , você encontrará **Renomear**.
3. Isso tornará o nome da coluna editável. Renomearemos esta coluna como **Country**.

**Etapa 5:** Remover valores nulos em uma coluna por filtragem

Também precisamos filtrar os valores nulos na coluna **Country** . Para fazer isso podemos usar o menu de filtragem, conforme vimos na etapa 3; ou então podemos, como alternativa:

1. Clicar com o botão direito do mouse em uma das células na coluna **Country** que contêm um valor nulo.
2. Selecionar **Filtros de Texto -\> Não é Igual a** no menu de contexto.
3. Isso cria uma nova etapa de filtragem para remover as linhas com valores nulos na coluna **Country** .

**Etapa 6:** Nomear uma consulta

Nesta etapa, você nomeia sua consulta final **Vencedores da Eurocopa**.

1. No painel **Configurações de Consulta** , na caixa de texto **Nome** , digite **Vencedores da Eurocopa**.
   
   ![](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/webpage8.png)

## <a name="task-3-create-visualizations-using-the-report-view"></a>Tarefa 3: criar visualizações usando o Modo de Exibição de Relatório
Agora que convertemos os dados para o formato que precisamos para nossa análise, podemos carregar a tabela resultante em nosso Relatório e criar algumas visualizações.

**Etapa 1:** carregar a consulta em seu relatório

Para carregar os resultados da consulta no Power BI Desktop e criar um relatório, selecionamos **Fechar e Carregar** da faixa de opções **Home**.

![](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/webpage9.png)

Isso vai disparar a avaliação da consulta e o carregamento da saída da tabela no Relatório. No Power BI Desktop, selecione o ícone **Relatório** para ver o Power BI Desktop na exibição de Relatório.

![](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/webpage10.png)

Você pode ver os campos da tabela resultante no **painel Campos** à direita da **exibição de Relatório**.

![](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/webpage11.png)

**Etapa 2:** Criar uma visualização de Mapa

Para criar uma visualização, é possível arrastar campos da **lista Campos** e soltá-los na **tela Relatório**.

1. Arraste o campo **Country** e solte-o na **tela Relatório**. Isso criará uma nova visualização na **tela Relatório**. Nesse caso, já que temos uma lista de países, ele criará uma **visualização de Mapa**.
   
   ![](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/webpage12.png)
2. Podemos facilmente alterar o tipo de visualização clicando em um ícone diferente no painel **Visualização** .
   
   ![](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/webpage13.png)
3. Vamos continuar com o tipo de visualização **Mapa** para o Mapa. Também podemos redimensionar a visualização arrastando um de seus cantos para cima até o tamanho desejado.
   
   ![](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/webpage14.png)
4. Observe que, no momento, todos os pontos no mapa têm o mesmo tamanho. Queremos alterar isso para que os países que venceram mais torneios da Eurocopa sejam representados com um ponto maior no mapa. Para fazer isso, é possível arrastar o campo **Year** na **lista Campos** para a caixa **Valores** na parte inferior do **painel Campos**.
   
   ![](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/webpage15.png)

Como você pode ver, é muito fácil personalizar visualizações em seu relatório para apresentar os dados como você desejar. O Power BI Desktop fornece uma experiência perfeita de ponta a ponta, desde a obtenção de dados por meio de uma ampla variedade de fontes de dados e a modelagem desses dados para atender às suas necessidades de análise, até a visualização de tais dados de maneiras avançadas e interativas. Quando seu relatório estiver pronto, você poderá [carregá-lo no Power BI](desktop-upload-desktop-files.md) e criar painéis baseados nele, que poderão ser compartilhados com outros usuários do Power BI.

Isso conclui o tutorial **Importando dados da Web** . Você pode baixar [aqui](http://download.microsoft.com/download/1/4/E/14EDED28-6C58-4055-A65C-23B4DA81C4DE/Analyzing_Data_From_The_Web.pbix) o arquivo completo do Power BI Desktop.

## <a name="where-else-can-i-get-more-information"></a>Onde mais posso obter outras informações?
* [Leia outros tutoriais do Power BI Desktop](http://go.microsoft.com/fwlink/?LinkID=521937)
* [Assista a vídeos do Power BI Desktop](http://go.microsoft.com/fwlink/?LinkID=519322)
* [Visite o Fórum do Power BI](http://go.microsoft.com/fwlink/?LinkID=519326)
* [Leia o Blog do Power BI](http://go.microsoft.com/fwlink/?LinkID=519327)

