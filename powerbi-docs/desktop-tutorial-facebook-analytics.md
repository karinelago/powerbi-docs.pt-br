---
title: 'Tutorial: análise do Facebook com o Power BI Desktop'
description: 'Tutorial: análise do Facebook com o Power BI Desktop'
services: powerbi
documentationcenter: ''
author: davidiseminger
manager: kfile
backup: ''
editor: ''
tags: ''
qualityfocus: no
qualitydate: ''
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 05/02/2018
ms.author: davidi
LocalizationGroup: Learn more
ms.openlocfilehash: fe4764de01a490d8d6948a8ab6aa6f09c5a85dbc
ms.sourcegitcommit: f679c05d029ad0765976d530effde744eac23af5
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="tutorial-facebook-analytics-using-power-bi-desktop"></a>Tutorial: análise do Facebook com o Power BI Desktop

Neste tutorial, você aprenderá a importar dados do Facebook e usá-los no Power BI Desktop. Você vai se conectar e importar dados da página do Facebook do Power BI, aplicará transformações aos dados importados e usará os dados nas visualizações do relatório.

## <a name="connect-to-a-facebook-page"></a>Conectar-se a uma página do Facebook

Este tutorial usa dados da [página do Facebook do Microsoft Power BI](https://www.facebook.com/microsoftbi) (*https://www.facebook.com/microsoftbi*). Você não precisa de credenciais especiais para se conectar e importar dados dessa página, com exceção de uma conta pessoal do Facebook.

1. Abra o Power BI Desktop e selecione **Obter dados** na caixa de diálogo **Introdução**, ou na guia **Página Inicial** da faixa de opções, selecione **Obter Dados** e, em seguida, selecione **Mais...** .
   
2. Na caixa de diálogo **Obter Dados**, selecione **Facebook** no grupo **Serviços Online** e, em seguida, selecione **Conectar**.
   
   ![Obter dados](media/desktop-tutorial-facebook-analytics/t_fb_getdataother.png)
   
   Surge uma caixa de diálogo para alertar você sobre os riscos de uso de um serviço de terceiros.
   
   ![Aviso de terceiros](media/desktop-tutorial-facebook-analytics/t_fb_connectingtotps.png)
   
3. Selecione **Continuar**. A caixa de diálogo **Facebook** é exibida.
   
4. Digite ou cole o nome da página **microsoftbi** na caixa de texto **Nome de usuário**, selecione **Postagens** na lista suspensa **Conexão** e selecione **OK**.
   
   ![Conectar-se](media/desktop-tutorial-facebook-analytics/2.png)
   
5. Quando receber a solicitação por credenciais, entre em sua conta do Facebook e permita acesso ao Power BI por meio de sua conta.
   
   ![Credenciais](media/desktop-tutorial-facebook-analytics/facebookcredentials.png)

   Após a conexão com a página do Power BI no Facebook, você terá uma visualização dos dados de **postagens** da página. 
   
   ![Visualização dos dados](media/desktop-tutorial-facebook-analytics/t_fb_1-loadpreview.png)
   
## <a name="shape-and-transform-the-imported-data"></a>Formatar e transformar os dados importados

Você quer ver e mostrar quais postagens têm mais comentários ao longo do tempo, mas percebe na visualização de dados de **Postagens** que os dados de **created_time** estão difíceis de ler e entender, e não há dado de comentários. Você precisa limpar e formatar os dados para aproveitá-los ao máximo. Você pode usar o **Editor do Power Query** do Power BI Desktop para editar os dados, antes ou depois de importá-los para o Power BI Desktop. 

### <a name="split-the-datetime-column"></a>Dividir a coluna de data e hora

Primeiro, separe os valores de data e hora na coluna **created_time** para facilitar a leitura. 

1. Na visualização de dados do Facebook, selecione **Editar**. 
   
   ![Edição da visualização dos dados](media/desktop-tutorial-facebook-analytics/t_fb_1-editpreview.png)
   
   O **Editor do Power Query** do Power BI Desktop é aberto em uma nova janela e exibe a visualização de dados da página do Power BI no Facebook. 
   
   ![Editor do Power Query](media/desktop-tutorial-facebook-analytics/t_fb_1-intoqueryeditor.png)
   
2. Selecione a coluna **created_time**. Observe que, no momento, ela é do tipo de dados Texto, indicado por um ícone **ABC** no cabeçalho da coluna. Clique com o botão direito no cabeçalho e selecione **Dividir Coluna > Por Delimitador** na lista suspensa, ou selecione **Dividir Coluna > Por Delimitador** em **Transformar** na guia Página inicial da faixa de opções.  
   
   ![Dividir coluna por delimitador](media/desktop-tutorial-facebook-analytics/delimiter1.png)
   
3. Na caixa de diálogo **Dividir Coluna por Delimitador**, selecione **Personalizado** na lista suspensa, digite **T** (o caractere que inicia a parte de hora dos valores de created_time) no campo de entrada e selecione **OK**. 
   
   ![Caixa de diálogo Dividir Coluna por Delimitador](media/desktop-tutorial-facebook-analytics/delimiter2.png)
   
   A coluna se divide em duas contendo as cadeias de caracteres antes e depois do delimitador **T**, e recebem o nome de **created_time.1** e **created_time.2**, respectivamente. Observe que o Power BI detectou e alterou automaticamente os tipos de dados para **Data** na primeira coluna e **Hora** na segunda, e formatou os valores de data e hora para facilitar a leitura.
   
4. Renomeie as colunas clicando duas vezes no cabeçalho de cada uma delas, ou selecionando cada coluna e, depois, selecionando **Renomear** no Grupo **Qualquer Coluna** da guia **Transformar** da faixa de opções e digitando novos cabeçalhos de coluna **created_date** e **created_time**, respectivamente.
   
   ![Novas colunas de data e hora](media/desktop-tutorial-facebook-analytics/delimiter3.png)
   
### <a name="expand-the-nested-column"></a>Expandir a coluna aninhada

Agora que os dados de data e hora estão ao seu gosto, você exporá os dados de comentários expandindo uma coluna aninhada. 

1. Selecione a coluna **object_link** e selecione o ![ícone de expansão](media/desktop-tutorial-facebook-analytics/14.png) para abrir a caixa de diálogo **Expandir/Agregar**. Selecione **connections** e depois **OK**. 
   
   ![Expandir object_link](media/desktop-tutorial-facebook-analytics/expand1.png)
   
   O título da coluna muda para **object_link.connections**.
2. Selecione novamente o ![ícone de expansão](media/desktop-tutorial-facebook-analytics/14.png) na parte superior da coluna **object_link.connections**, selecione **comments** e depois **OK**. O título da coluna muda para **object_link.connections.comments**.
   
3. Selecione o ![ícone de expansão](media/desktop-tutorial-facebook-analytics/14.png) na parte superior da coluna **object_link.connections.comments** e desta vez selecione **Agregar**, em vez de Expandir, na caixa de diálogo. Selecione **Nº de Contagem de id** e depois **OK**. 
   
   ![Agregar comentários](media/desktop-tutorial-facebook-analytics/expand2.png)
   
   Agora, a coluna exibe o número de comentários para cada mensagem. 
   
4. Renomeie a coluna **Contagem de object_link.connections.comments.id** para **Número de comentários**.
   
5. Selecione a seta para baixo ao lado do cabeçalho **Número de comentários** e selecione **Classificar em Ordem Decrescente** para ver as Postagens com mais comentários primeiro. 
   
   ![Comentários por mensagem](media/desktop-tutorial-facebook-analytics/data-fixed.png)
   
### <a name="review-query-steps"></a>Rever as etapas de consulta

À medida que você molda e transforma os dados no **Editor do Power Query**, cada etapa é registrada na área **Etapas Aplicadas** do painel **Config. Consulta** no lado direito da janela do Editor do Power Query. Você pode percorrer novamente as Etapas Aplicadas para ver as alterações exatas feitas, e editar, excluir ou reorganizá-las se for necessário (embora isso possa ser arriscado, pois alterar as etapas anteriores pode invalidar as etapas posteriores). 

Depois de aplicar todas as transformações de dados, as Etapas Aplicadas devem estar assim:
   
   ![Etapas Aplicadas](media/desktop-tutorial-facebook-analytics/applied-steps.png)
   
   >[!TIP]
   >As Etapas Aplicadas são formadas por fórmulas escritas na **Linguagem do Power Query**, também conhecida como linguagem **M**. Para ver e editar as fórmulas, selecione **Editor Avançado** no grupo **Consulta** da guia Página Inicial da faixa de opções. 

### <a name="import-the-transformed-data"></a>Importar os dados transformados

Quando você estiver satisfeito com os dados, selecione **Fechar e Aplicar** > **Fechar e Aplicar** na guia Página Inicial da faixa de opções para importá-los no Power BI Desktop. 
   
   ![Fechar e Aplicar](media/desktop-tutorial-facebook-analytics/t_fb_1-loadandclose.png)
   
   Uma caixa de diálogo exibirá o progresso do carregamento dos dados no modelo de dados do Power BI Desktop. 
   
   ![Carregar dados](media/desktop-tutorial-facebook-analytics/t_fb_1-loading.png)
   
   Após o carregamento dos dados, eles aparecem na visualização do Relatório como uma nova Consulta na lista Fields.
   
   ![Nova consulta](media/desktop-tutorial-facebook-analytics/fb-newquery.png)
   
## <a name="use-the-data-in-report-visualizations"></a>Usar os dados nas visualizações de relatório 

Agora que você importou os dados da página do Facebook, conseguirá obter informações sobre seus dados de forma ágil e fácil usando as visualizações. Criar uma visualização é fácil. Basta selecionar um campo ou arrastá-lo da lista **Fields** para a tela do relatório.

### <a name="create-a-bar-chart"></a>Criar um gráfico de barras

1. Na visualização de Relatório do Power BI Desktop, selecione **message** na lista Fields, ou arraste-o para a tela. Uma tabela com todas as mensagens de postagem é exibida na tela. 
   
   ![Nova consulta](media/desktop-tutorial-facebook-analytics/table-viz.png)
   
2. Com a tabela selecionada, selecione também **Number of comments** na lista Fields, ou arraste-o para a tabela. 
   
3. Selecione o ícone **Gráfico de barras empilhadas** no painel Visualizações. A tabela muda para um gráfico de barras mostrando o número de comentários por postagem. 
   
   ![Gráfico de barras](media/desktop-tutorial-facebook-analytics/barchart1.png)
   
4. Selecione as reticências (...) no canto superior direito da visualização e selecione **Classificar por Número de comentários** para classificar a tabela por número decrescente de comentários. 
   
   ![Classificar por número de comentários](media/desktop-tutorial-facebook-analytics/barchart2.png)
   
5. Observe que a maioria dos comentários foi associada a mensagens **Em branco** (essas postagens podem ter sido histórias, links, vídeos ou outro conteúdo diferente de texto). Para filtrar a linha Em branco, selecione **message (all)** em **Filtros** na parte inferior do painel de Visualizações, selecione **Selecionar tudo** e, depois, selecione **Em branco** para cancelar a seleção dessa opção. A entrada em Filtros muda para **message is not (Blank)**, e a linha Em branco desaparece da visualização do gráfico. 
   
   ![Filtrar em branco](media/desktop-tutorial-facebook-analytics/barchart3.png)
   
### <a name="format-the-chart"></a>Formatar o gráfico

A visualização está ficando mais interessante, mas não dá para ver muito do texto da postagem no gráfico. Para mostrar mais do texto da postagem:

1. Usando as alças na visualização do gráfico, redimensione o gráfico até o tamanho máximo. 
   
2. Com o gráfico selecionado, selecione o **ícone de Formato** (rolo de pintura) no painel de Visualizações.
   
3. Selecione a seta para baixo ao lado de **Eixo Y** e arraste o controle deslizante ao lado de **Tamanho máximo** totalmente para a direita (50%). 
4. Reduza também o **Tamanho do texto** para **10**, para caber mais texto.
   
   ![Alterações de formatação](media/desktop-tutorial-facebook-analytics/barchart4.png)
   
   Agora, o gráfico mostra mais conteúdo da postagem. 
   
   ![Mostrar mais postagens](media/desktop-tutorial-facebook-analytics/barchart5.png)
   
O eixo X (número de comentários) do gráfico não mostra os valores exatos, e a parte de baixo do gráfico parece uma bagunça. Em vez disso, você decide usar rótulos de dados. 

1. Selecione o ícone de Formato e, depois, selecione o controle deslizante ao lado de **Eixo x** para **Desativá-lo**. 
   
2. Selecione o controle deslizante ao lado de **Rótulos de dados** para **Ativá-los**. Agora o gráfico mostra o número exato de comentários para cada postagem.
   
   ![Aplicar rótulos de dados](media/desktop-tutorial-facebook-analytics/barchart6.png)
   
### <a name="edit-the-data-type"></a>Editar o tipo de dados

Muito melhor, mas todos os rótulos de dados tem uma casa decimal **,0**, o que é perturbador e enganoso, já que **Número de postagens** deve ser um número inteiro. Você precisa mudar o tipo de dados da coluna **Número de postagens** para Número Inteiro.

1. Para editar o tipo de dados, clique com botão direito em **Consulta1** na lista Fields, ou passe o mouse sobre ele e selecione as reticências **Mais opções** (...), depois selecione **Editar Consulta**. Você também pode selecionar **Editar Consultas** na área **Dados externos** da guia Página Inicial na faixa de opções e, depois, selecionar **Editar Consultas** na lista suspensa. O **Editor do Power Query** do Power BI Desktop é aberto em uma janela separada.
   
   ![Editar consulta na lista Fields](media/desktop-tutorial-facebook-analytics/editquery1.png)     ![Editar consultas na faixa de opções](media/desktop-tutorial-facebook-analytics/t_fb_editquery.png)
   
2. No Editor do Power Query, selecione a coluna **Número de comentários** e altere o tipo de dados para **Número Inteiro**: 
   - Selecionando o ícone **1.2** próximo ao cabeçalho da coluna **Número de comentários** e selecionando **Número Inteiro** no menu suspenso, ou
   - Clicando duas vezes no cabeçalho da coluna e selecionando **Alterar Tipo > Número Inteiro**, ou
   - Selecionando **Tipo de dados: Número Decimal** no grupo **Transformar** da guia Página Inicial, ou no grupo **Qualquer Coluna** da guia **Transformar**, e selecionando **Número Inteiro**.
   
   O ícone no cabeçalho da coluna muda para **123**, indicando um tipo de dados de Número Inteiro.
   
   ![Alterar tipo de dados](media/desktop-tutorial-facebook-analytics/change-datatype.png)
   
3. Selecione **Fechar e Aplicar**, ou apenas **Aplicar** para aplicar as alterações, mantendo a janela do Editor do Power Query aberta. Após o carregamento das alterações, os rótulos de dados no gráfico se tornam números inteiros. 
   
   ![Gráfico com números inteiros](media/desktop-tutorial-facebook-analytics/vis-3.png)
   
### <a name="create-a-date-slicer"></a>Criar uma segmentação de dados de data

Você quer visualizar a quantidade de comentários em postagens ao longo do tempo. É possível criar uma visualização de segmentação de dados para filtrar os dados do gráfico de acordo com períodos diferentes. 

1. Clique em uma área em branco da tela e selecione o **ícone de Segmentação de dados** no painel de Visualizações. Uma visualização de segmentação de dados em branco é exibida. 
   
   ![Selecionar o ícone de segmentação de dados](media/desktop-tutorial-facebook-analytics/slicer1.png)
   
2. Selecione o campo **created_date** na lista Fields, ou arraste-o para a nova segmentação de dados. A segmentação de dados muda para um controle deslizante de intervalo de datas, com base no tipo de dados de Data do campo.
   
   ![Segmentação de controle deslizante de intervalo de datas](media/desktop-tutorial-facebook-analytics/slicer2.png)
   
3. Mova as alças do controle deslizante para selecionar intervalos de datas diferentes e observe a filtragem resultante dos dados do gráfico. Também é possível selecionar os campos de data na segmentação de dados e digitar datas específicas, ou escolhê-las em um calendário pop-up.
    
   ![Segmentar os dados](media/desktop-tutorial-facebook-analytics/slicer3.png)
   
### <a name="format-the-visualizations"></a>Formatar as visualizações

Você decide dar o gráfico um título mais descritivo e atrativo. 

1. Com o gráfico selecionado, selecione o ícone **Formato** e selecione a seta suspensa para expandir **Título**.
2. Altere o **Texto do título** para **Comentários por postagem**. 
3. Selecione a seta suspensa ao lado de **Cor da fonte** e selecione uma cor verde para corresponder às barras verdes da visualização.
4. Aumente o **Tamanho do texto** para **10** e altere a **Família de fontes** para **Segoe (Negrito)**.

![Formatar título do gráfico](media/desktop-tutorial-facebook-analytics/formatting1.png)

Experimente outras opções e configurações de formatação para mudar a aparência de suas visualizações. 

![Visualizações](media/desktop-tutorial-facebook-analytics/vis-1.png)

## <a name="create-more-visualizations"></a>Criar mais visualizações

Como você pode ver, é fácil personalizar visualizações em seu relatório para apresentar os dados como você quer. Por exemplo, tente usar os dados importados do Facebook para criar este gráfico de linhas mostrando o número de comentários ao longo do tempo.

![Gráfico de linhas](media/desktop-tutorial-facebook-analytics/moreviz.png)

O Power BI Desktop fornece uma experiência perfeita de ponta a ponta, desde a obtenção de dados por meio de uma ampla variedade de fontes de dados e a modelagem desses dados para atender às suas necessidades de análise, até a visualização de tais dados de maneiras avançadas e interativas. Quando seu relatório estiver pronto, você poderá [carregá-lo no serviço do Power BI](desktop-upload-desktop-files.md) e criar painéis baseados nele, que poderão ser compartilhados com outros usuários do Power BI.

## <a name="next-steps"></a>Próximas etapas
* [Leia outros tutoriais do Power BI Desktop](http://go.microsoft.com/fwlink/?LinkID=521937)
* [Assista a vídeos do Power BI Desktop](http://go.microsoft.com/fwlink/?LinkID=519322)
* [Visite o Fórum do Power BI](http://go.microsoft.com/fwlink/?LinkID=519326)
* [Leia o Blog do Power BI](http://go.microsoft.com/fwlink/?LinkID=519327)

