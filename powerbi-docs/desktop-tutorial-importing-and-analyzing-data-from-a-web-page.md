---
title: 'Tutorial: importar e analisar dados de uma página da Web sando o Power BI Desktop'
description: 'Tutorial: importar e analisar dados de uma página da Web sando o Power BI Desktop'
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: tutorial
ms.date: 06/05/2018
ms.author: davidi
LocalizationGroup: Learn more
ms.openlocfilehash: 32de597b594fe8b148a2b0471352e4784d596cec
ms.sourcegitcommit: 8ee0ebd4d47a41108387d13a3bc3e7e2770cbeb8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2018
ms.locfileid: "34813171"
---
# <a name="tutorial-analyze-web-page-data-using-power-bi-desktop"></a>Tutorial: analisar dados de página da Web usando o Power BI Desktop

Como fã de futebol de longa data, você deseja criar um relatório dos vencedores da relatar os vencedores Campeonato Europeu da UEFA (Eurocopa) ao longo dos anos. Com o Power BI Desktop, você pode importar esses dados de uma página da Web para um relatório e criar visualizações que mostram os dados. Neste tutorial, você aprenderá a usar o Power BI Desktop para:

- Conectar-se a uma fonte de dados da Web e navegar entre as tabelas disponíveis,
- Formatar e transformar dados no **Power Query Editor**,
- Nomear uma consulta e importá-la para um relatório do Power BI Desktop, e 
- Criar e personalizar um mapa e uma visualização de gráfico de pizza.

## <a name="connect-to-a-web-data-source"></a>Conectar-se a uma fonte de dados da Web

Você pode obter os dados dos vencedores da UEFA na tabela de resultados da página do Campeonato Europeu de Futebol na Wikipédia, em http://en.wikipedia.org/wiki/UEFA_European_Football_Championship. 

![Tabela de resultados da Wikipédia](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/webpage1.png)

Observe que as conexões Web somente são estabelecidas usando a autenticação básica. Os sites da Web que exigem autenticação podem não funcionar corretamente com o conector da Web.

Para importar os dados:

1. Na guia de faixa de opções **Início** do Power BI Desktop, clique na seta suspensa ao lado de **Obter Dados** e, em seguida, selecione **Web**.
   
   ![Faixa de opções Obter Dados de](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/get-data-web3.png) 
   
   >[!NOTE]
   >Também é possível selecionar o próprio item **Obter Dados** ou, ainda, selecionar **Obter Dados** na caixa de diálogo **Começar** do Power BI e, em seguida, selecionar **Web** na seção **Todos** ou **Outros** da caixa de diálogo **Obter Dados** e, então, selecionar **Conectar**.
   
2. Na caixa de diálogo **Da Web**, cole a URL `http://en.wikipedia.org/wiki/UEFA_European_Football_Championship` na caixa de texto **URL** e, em seguida, selecione **OK**.
   
    ![Caixa de diálogo Obter Dados de](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/get-data-web2.png)
   
   Depois de se conectar à página da Web da Wikipédia, a caixa de diálogo **Navegador** do Power BI mostra uma lista de tabelas disponíveis na página. Você pode selecionar qualquer um dos nomes de tabela para visualizar seus dados. A tabela **Resultados[editar]** tem os dados desejados, embora não estejam exatamente na forma que você quer. Você reformatará e limpará os dados antes de carregá-los em seu relatório. 
   
   ![Caixa de diálogo Navegador](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/tutorialimanaly_navigator.png)
   
   >[!NOTE]
   >O painel **Visualização** mostra a tabela mais recente selecionada, mas todas as tabelas selecionadas serão carregadas no **Power Query Editor** quando você selecionar **Editar** ou **Carregar**. 
   
3. Selecione a tabela **Resultados[editar]** na lista do **Navegador** e, em seguida, selecione **Editar**. 
   
   Uma visualização da tabela é aberta no **Power Query Editor**, no qual é possível aplicar transformações para limpar os dados. 
   
   ![Editor do Power Query](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/webpage3.png)
   
## <a name="shape-data-in-power-query-editor"></a>Formatar dados no Power Query Editor

Você quer tornar os dados mais fáceis de examinar exibindo apenas os anos e os países que venceram. Você pode usar o **Power Query Editor** para executar essas etapas de formatação e limpeza de dados.

Primeiro, remova todas as colunas, exceto por **Year** e **Final Winners** da tabela.

1. Na grade do **Power Query Editor**, selecione as colunas **Year** e **Final Winners** (mantenha a tecla **Ctrl** pressionada para selecionar vários itens).
   
2. Clique com o botão direito do mouse e selecione **Remover Outras Colunas** na lista suspensa ou selecione **Remover Colunas** > **Remover Outras Colunas** no grupo **Gerenciar Colunas** na guia de faixa de opções **Início** para remover todas as outras colunas da tabela. 
   
   ![Menu suspenso Remover Outras Colunas](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/get-data-web6.png) ou ![Faixa de opções Remover Outras Colunas](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/webpage4.png)

Em seguida, remova a palavra extra **Details** das células da coluna **Year**.

1. Selecione a coluna **Year** .
   
2. Clique com o botão direito do mouse e selecione **Substituir Valores** na lista suspensa ou selecione **Substituir Valores** no grupo **Transformar** na guia **Início** da faixa de opções (encontrado também no grupo **Qualquer Coluna** na guia **Transformar**). 
   
   ![Menu suspenso Substituir Valores](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/get-data-web7.png) ou ![Faixa de opções Substituir Valores](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/get-data-web8a.png)
   
3. Na caixa de diálogo **Substituir Valores**, digite **Details** na caixa de texto **Valor a Localizar**, deixe a caixa de texto **Substituir Por** vazia e, em seguida, selecione **OK** para excluir a palavra “Details” das entradas de **Year**.
   
   ![](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/webpage6.png)

Algumas células em **Year** contêm apenas a palavra "Year" em vez dos valores de ano. Você pode filtrar a coluna **Year** para exibir apenas linhas que não contêm a palavra “Year”. 

1. Selecione a seta suspensa de filtro na coluna **Year**.
   
2. Na lista suspensa, role para baixo e desmarque a caixa de seleção ao lado da opção **Year** e, em seguida, selecione **OK** para remover as linhas que têm apenas a palavra "Year" na coluna **Year**. 

   ![Filtrar dados](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/webpage7.png)

Agora que limpou os dados na coluna **Year**, você pode trabalhar na coluna **Final Winner**. Como estamos observando apenas os dados dos vencedores finais, você pode renomear esta coluna como **Country**. Para renomear a coluna:

1. Clique duas vezes ou toque e segure o cabeçalho da coluna **Final Winner** ou 
   - Clique com o botão direito do mouse no cabeçalho da coluna **Final Winners** e selecione **Renomear** no menu suspenso, ou 
   - Selecione a coluna **Final Winners** e selecione **Renomear** no grupo **Qualquer Coluna** na guia **Transformar** da faixa de opções. 
   
   ![Lista suspensa Renomear](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/webpage7a.png) ou ![Faixa de opções Renomear](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/get-data-web8.png)
   
2. Digite **Country** no cabeçalho e pressione **Enter** para renomear a coluna.

Você também deseja filtrar linhas como "2020", que têm valores nulos na coluna **País**. Você pode usar o menu de filtragem, como você fez com os valores de **Year** ou pode:

1. Clicar com o botão direito do mouse na célula **Country** na linha **2020**, que tem o valor *nulo*. 
2. Selecione **Filtros de Texto** > **Não é igual a** no menu de contexto para remover qualquer linha que contiver o valor da célula.
   
   ![Filtro de texto](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/get-data-web11.png)
   
## <a name="import-the-query-into-report-view"></a>Importar a consulta para a Exibição de Relatório

Agora que formatou os dados da maneira desejada, você está pronto para nomear sua consulta "Euro Cup Winners" e importá-la para seu relatório.

1. No painel **Config. Consulta**, na caixa de texto **Nome**, digite **Euro Cup Winners** e pressione **Enter**.
   
   ![Nomear a consulta](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/webpage8.png)

2. Selecione **Fechar e Aplicar** > **Fechar e Aplicar** na guia **Início** da faixa de opções.
   
   ![Fechar e Aplicar](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/webpage9.png)
   
A consulta é carregada na **Exibição de Relatório** do Power BI Desktop, podendo ser vista no painel **Campos**. 
   
   ![Painel Campos](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/webpage11.png)
>[!TIP]
>Você sempre pode voltar para o **Power Query Editor** para editar e refinar sua consulta:
>- Selecionando as reticências (**...**) de **Mais opções** ao lado de **Euro Cup Winners** no painel **Campos** e selecionando **Editar Consulta** na lista suspensa, ou
>- Selecionando **Editar Consultas** > **Editar Consultas** no grupo **Dados externos** da guia de faixa de opções **Início** na Exibição de Relatório. 

## <a name="create-a-visualization"></a>Criar uma visualização

Para criar uma visualização com base em seus dados: 

1. Selecione o campo **Country** no painel **Campos** ou arraste-o para a tela de relatório. O Power BI Desktop reconhece os dados como nomes de países e cria automaticamente uma visualização de **Mapa**. 
   
   ![Visualização de mapa](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/get-data-web14.png)
   
2. Amplie o mapa arrastando as alças nos cantos para que os nomes de todos os países vencedores fiquem visíveis.  

   ![Ampliar o mapa](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/webpage14.png)
   
3. O mapa mostra pontos de dados idênticos para todos os países que venceram um torneio da Eurocopa. Para fazer com que o tamanho de cada ponto de dados reflita a frequência com que o país venceu, arraste o campo **Year** para **Arrastar os campos de dados aqui** em **Tamanho** na parte inferior do painel **Visualizações**. O campo é alterado automaticamente para uma medida de **Contagem de Anos** e a visualização de mapa agora mostra pontos de dados maiores para os países que venceram mais torneios. 
   
   ![](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/webpage15.png)
   

## <a name="customize-the-visualization"></a>Personalizar a visualização

Como você pode ver, é muito fácil criar visualizações com base em seus dados. Também é fácil personalizar suas visualizações para apresentar melhor os dados das maneiras que você deseja. 

### <a name="format-the-map"></a>Formatar o mapa
Você pode alterar a aparência de uma visualização selecionando-a e, em seguida, selecionando o ícone de **Formato** (rolete de pintura) no painel **Visualizações**. Por exemplo, os pontos de dados "Germany" na visualização podem ser enganosos, porque a Alemanha Ocidental venceu dois torneios e a Alemanha venceu um e o mapa sobrepõe os dois pontos em vez de separá-los ou adicioná-los. Você pode colorir esses dois pontos de forma diferente para realçar isso. Você também pode optar por dar ao mapa um título mais descritivo e atrativo. 

1. Com a visualização selecionada, selecione o ícone **Formato** e, em seguida, selecione **Cores dos dados** para expandir as opções de cores de dados. 
   
   ![Formatar cores de dados](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/get-data-web15.png)
   
2. Defina **Mostrar Tudo** como **Ativado** e, em seguida, selecione o menu suspenso próximo a **West Germany** e escolha a cor amarela. 
   
   ![Alterar cor](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/get-data-web16.png)
   
3. Selecione **Título** para expandir as opções de título e, no campo **Texto do título**, digite **Euro Cup Winners** no lugar do título atual. 
4. Altere a **Cor da fonte** para vermelho, o **Tamanho do texto** para **12** e a **Família de fontes** para **Segoe (Negrito)**. 
   
   ![Formatar cores de dados](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/get-data-web17.png)
   

Agora, sua visualização de mapa é semelhante ao seguinte:

![Visualização de mapa formatada](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/get-data-web18.png)
   
### <a name="change-the-visualization-type"></a>Altere o tipo de visualização
É possível alterar o tipo de uma visualização selecionando-a e, em seguida, selecionando um ícone diferente na parte superior do painel **Visualização**. Por exemplo, sua visualização de mapa não tem os dados da União Soviética e da Tchecoslováquia, porque esses países não existem mais no mapa do mundo. Outro tipo de visualização, como um gráfico de pizza ou de mapa de árvore, pode ser mais precisa, porque mostra todos os valores. 

Para alterar o mapa para um gráfico de pizza, selecione-o e, em seguida, selecione o ícone **Gráfico de pizza** no painel **Visualização**. 
   
![](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/get-data-web19.png)

>[!TIP]
>- Você pode usar as opções de formatação de **Cores de dados** para deixar "Germany" e "West Germany" com a mesma cor. 
>- Para agrupar os países com mais vitórias no gráfico de pizza, selecione as reticências (**...**) no canto superior direito da visualização e, em seguida, selecione **Classificar por contagem de anos** na lista suspensa. 

O Power BI Desktop fornece uma experiência perfeita de ponta a ponta, desde a obtenção de dados por meio de uma ampla variedade de fontes de dados e a modelagem desses dados para atender às suas necessidades de análise, até a visualização de tais dados de maneiras avançadas e interativas. Quando seu relatório estiver pronto, você poderá [carregá-lo no Power BI](desktop-upload-desktop-files.md) e criar painéis baseados nele, que poderão ser compartilhados com outros usuários do Power BI.

## <a name="see-also"></a>Consulte também
* [Leia outros tutoriais do Power BI Desktop](http://go.microsoft.com/fwlink/?LinkID=521937)
* [Assista a vídeos do Power BI Desktop](http://go.microsoft.com/fwlink/?LinkID=519322)
* [Visite o Fórum do Power BI](http://go.microsoft.com/fwlink/?LinkID=519326)
* [Leia o Blog do Power BI](http://go.microsoft.com/fwlink/?LinkID=519327)

