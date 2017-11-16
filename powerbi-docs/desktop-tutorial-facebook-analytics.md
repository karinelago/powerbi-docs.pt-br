---
title: "Tutorial: análise do Facebook com o Power BI Desktop"
description: "Tutorial: análise do Facebook com o Power BI Desktop"
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
ms.date: 09/06/2017
ms.author: davidi
ms.openlocfilehash: 3642a252467d504b61eb81f82d0b96f64a24f22b
ms.sourcegitcommit: 99cc3b9cb615c2957dde6ca908a51238f129cebb
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/13/2017
---
# <a name="tutorial-facebook-analytics-using-power-bi-desktop"></a>Tutorial: análise do Facebook com o Power BI Desktop
Neste tutorial, você aprenderá a importar e visualizar dados do **Facebook**. Durante o tutorial, você aprenderá como se conectar a uma página específica do Facebook (a página do Power BI), seguir as etapas de transformação de dados e criar algumas visualizações.

Aqui estão as etapas que você seguirá:

* **Tarefa 1:** conectar-se a uma página do Facebook
* **Tarefa 2**: criar visualizações usando a visualização de Relatório
  
  * **Etapa 1**: criar uma visualização de Treemap
* **Tarefa 3**: formatar dados na Visualização da Consulta
  
  * **Etapa 1**: dividir a coluna de data e hora em duas
  * **Etapa 2**: adicionar um valor agregado de uma tabela relacionada
* **Tarefa 4**: criar visualizações adicionais com a exibição de Relatório
  
  * **Etapa 1**: carregar a consulta em seu relatório
  * **Etapa 2**: criar um Gráfico de linhas e um Gráfico de barras

## <a name="task-1-connect-to-a-facebook-page"></a>**Tarefa 1: conectar-se a uma página do Facebook**
Nesta tarefa, você importará dados de um site do [Facebook do Microsoft Power BI](https://www.facebook.com/microsoftbi) (está é a URL: *https://www.facebook.com/microsoftbi )*.

Qualquer pessoa pode se conectar a essa página e seguir essas etapas - nenhuma credencial especial (além de sua própria conta do Facebook, que você usa nesta etapa) é necessária.

![](media/desktop-tutorial-facebook-analytics/1.png)

1. No diálogo **Introdução** ou na **guia de faixa de opções Página Inicial**, selecione **Obter Dados.**
2. O diálogo **Obter Dados** é exibido, permitindo que você selecione entre todos os tipos de fontes de dados. Selecione **Facebook** do grupo **Outros** .
   
   ![](media/desktop-tutorial-facebook-analytics/t_fb_getdataother.png)
   
   Quando você seleciona **Conectar**, um diálogo é exibido para alertá-lo sobre os riscos de uso de um serviço de terceiros.
   
   ![](media/desktop-tutorial-facebook-analytics/t_fb_connectingtotps.png)
3. Quando você seleciona Continuar, a caixa de diálogo **Facebook** é exibida, em que você pode colar o nome da página (**microsoftbi**) na caixa de texto **Nome de usuário** . Selecione **Postagens** no menu suspenso **Conexão** .
   
   ![](media/desktop-tutorial-facebook-analytics/2.png)
4. Clique em **OK**.
5. Quando solicitado que você forneça credenciais, entre usando sua conta do Facebook e permita acesso ao Power BI por meio de sua conta.
   
   ![](media/desktop-tutorial-facebook-analytics/facebookcredentials.png)

Depois de estabelecer uma conexão com a página, você verá os dados sendo carregados no modelo. 

![](media/desktop-tutorial-facebook-analytics/t_fb_1-loadpreview.png)

Lá, o **Editor de Consultas** exibe os dados. O **Editor de Consultas** faz parte do Power BI Desktop, mas é carregado em uma janela separada, e é nela em que você executa todas as transformações em suas conexões de dados.

![](media/desktop-tutorial-facebook-analytics/t_fb_1-intoqueryeditor.png)

Quando os dados estiverem da maneira desejada, você poderá carregá-los no Power BI Desktop. Selecione **Carregar e Fechar** na faixa de opções **Página Inicial**.

![](media/desktop-tutorial-facebook-analytics/t_fb_1-loadandclose.png)

Você verá um diálogo que exibe o andamento do carregamento dos dados no modelo de dados do Power BI Desktop.

![](media/desktop-tutorial-facebook-analytics/t_fb_1-loading.png)

Uma vez carregado, você será levado para a exibição de **Relatório** , no qual as colunas da tabela são listadas na lista **Campos** à direita.

![](media/desktop-tutorial-facebook-analytics/fbdesigner1.png)

## <a name="task-2-create-visualizations-using-the-report-view"></a>**Tarefa 2: criar visualizações usando o Modo de exibição de relatório**
Agora que você descarregou os dados da página, você poderá rápida e facilmente obter informações sobre seus dados usando visualizações.

**Etapa 1:** criar uma visualização de Treemap

É fácil criar uma visualização: basta arrastamos um campo da **lista Campos** e o soltarmos na **tela Relatório.**

Arraste o campo **Tipo** para a tela **Relatório** . O Power BI Desktop cria uma nova visualização na **tela Relatório**. Em seguida, arraste **tipo** de **Campos** (o mesmo campo que você acabou de arrastar para a tela **Relatório** ) para a área **Valor** para criar uma visualização **Barra** .

![](media/desktop-tutorial-facebook-analytics/fbdesigner2.png)

Podemos facilmente alterar o tipo de visualização selecionando um ícone diferente no painel **Visualização** . Vamos alterar o tipo para um **Treemap** selecionando seu ícone em **Visualizações**, como mostrado na imagem a seguir.

![](media/desktop-tutorial-facebook-analytics/fbdesigner3.png)

Em seguida, vamos adicionar uma legenda e alterar a cor de um ponto de dados. Selecione o ícone **Formato** no painel **Visualizações** ; o ícone **Formato** parece com um pincel.

![](media/desktop-tutorial-facebook-analytics/fbdesigner3a.png)

Quando você seleciona a seta para baixo ao lado de **Legenda**, a seção é expandida para mostrar como personalizar a legenda da visualização selecionada. Nesse caso, fizemos as seguintes seleções:

* movemos o controle deslizante **Legenda** para **Ligado** para que uma legenda fosse exibida
* selecionamos **Direita** no menu suspenso **Posição da Legenda**
* movemos o controle deslizante **Título** para **Ligado** para que um título para a legenda fosse exibido
* digitamos **tipo** para o título da legenda

Na imagem a seguir, essas configurações já foram feitas e são refletidas na visualização.

![](media/desktop-tutorial-facebook-analytics/fbdesigner3b.png)

Em seguida, vamos alterar a cor de um dos pontos de dados. O ponto de dados do link deve ser azul, para que esteja mais próximo da cor comum de hiperlinks.

Selecione a seta ao lado de **Cores dos Dados** para expandir essa seção. Os pontos de dados são mostrados, com setas de seleção ao lado de cada cor que nos permitem selecionar uma cor diferente para cada ponto de dados.

![](media/desktop-tutorial-facebook-analytics/fbdesigner3c.png)

Ao clicar na seta para baixo da caixa de cores ao lado de qualquer ponto de dados, um diálogo de seleção de cores será exibido, permitindo que você escolha uma cor. Nesse caso, escolheremos azul-claro.

![](media/desktop-tutorial-facebook-analytics/fbdesigner3d.png)

Essa é uma melhor opção. Na imagem a seguir, você pode ver como a cor será aplicada ao ponto de dados na visualização, e que a legenda também será atualizada automaticamente, assim como a sua cor na seção **Cores dos Dados** .

![](media/desktop-tutorial-facebook-analytics/fbdesigner3e.png)

## <a name="task-3-shape-data-in-the-table"></a>**Tarefa 3: formatar dados na tabela**
Agora que você importou a tabela selecionada e começará a visualizá-la, você pode perceber que precisa realizar diversas etapas de formatação e limpeza de dados para aproveitar ao máximo seus dados.

**Etapa 1:** dividir a coluna de data e hora em duas

Nesta etapa, você dividirá a coluna **created\_time** para obter os valores de data e hora. Sempre que estiver no Power BI Desktop e desejar modificar uma consulta existente, você precisará iniciar o **Editor de Consultas**. Para fazer isso, selecione **Editar Consultas** na guia **Página Inicial** .

![](media/desktop-tutorial-facebook-analytics/t_fb_editquery.png)

1. Na grade **Editor de Consultas**, role para a direita até encontrar a coluna **created\_time**
2. Clique com o botão direito do mouse em um título de coluna na grade **Visualização de Consulta** e clique em **Dividir Coluna \> Por Delimitador** para dividir as colunas. Escolha **Personalizado** no menu suspenso do delimitador e insira **“T”**. É importante lembrar que essa operação também está disponível na guia de faixa de opções **Página Inicial**, no grupo **Gerenciar Colunas**.
   
   ![](media/desktop-tutorial-facebook-analytics/9.png)
   
   ![](media/desktop-tutorial-facebook-analytics/10.png)
3. Renomeie as colunas criadas para **created\_date** e **created\_time**, respectivamente.
4. Selecione a nova coluna **created\_time**, **** e na faixa de opções **Visualização da Consulta**, navegue até a guia **Adicionar Coluna** e selecione **Hora\> Hora** no grupo **De Data e Hora**. Isso adicionará uma nova coluna que é apenas o componente de hora da hora.
   
   ![](media/desktop-tutorial-facebook-analytics/11.png)
5. Altere o tipo da nova coluna **Hora** para **Número Inteiro** navegando até a guia **Página Inicial** e selecionando o menu suspenso **Tipo de Dados** ou clicando com o botão direito do mouse na coluna e selecionando **Transformar \> Número Inteiro**.
   
   ![](media/desktop-tutorial-facebook-analytics/12.png)

**Etapa 2:** adicionar um valor agregado de uma tabela relacionada

Nesta etapa, você adiciona a contagem de compartilhamentos por meio do valor aninhado para que você possa usá-lo nas visualizações.

1. Continue a rolagem à direita até ver a coluna **compartilhamentos** . O valor aninhado indica que precisamos realizar outra transformação para obter os valores reais.
2. Na parte superior direito do título da coluna, selecione o ícone ![](media/desktop-tutorial-facebook-analytics/14.png) para abrir o construtor **Expandir/Agregar**. Selecione **contagem** e clique em **OK**. Isso adicionará a contagem dos compartilhamentos para cada linha em nossa tabela.
   
   ![](media/desktop-tutorial-facebook-analytics/15.png)
   
   Após o carregamento dos dados, renomeie a coluna para **compartilhamentos** clicando duas vezes no nome da coluna, clicando com botão direito do mouse na coluna ou na faixa de opções **exibição de Consulta** , e selecione **Renomear** na guia **Visualização da Consulta** e no grupo **Qualquer Coluna** .
3. Por fim, altere o tipo da nova coluna **compartilhamentos** para **Número Inteiro**. Com a coluna selecionada, o tipo pode ser alterado clicando com o botão direito do mouse na coluna e selecionando **Transformar \> Número Inteiro** ou **** navegando até a guia **Página Inicial** e selecionando o menu suspenso **Tipo de Dados**.

### <a name="query-steps-created"></a>Etapas de Consulta criadas
Conforme você realiza transformações na Visualização da Consulta, as etapas de consulta são criadas e listadas no painel **Configurações de Consulta** , na lista **ETAPAS APLICADAS** . Cada etapa de consulta tem uma fórmula de Consulta correspondente, também conhecida como a linguagem “M”.

![](media/desktop-tutorial-facebook-analytics/16.png)

| Tarefa | Etapa de consulta | Fórmula |
| --- | --- | --- |
| Conectar-se a uma fonte do Facebook |Fonte |Facebook.Graph (&quot;https://graph.facebook.com/microsoftbi/posts&quot;) |
| **Dividir Colunas** para obter os valores de que você precisa |Dividir Coluna por Delimitador |Table.SplitColumn  (Source,&quot;created_time&quot;,Splitter.SplitTextByDelimiter(&quot;T&quot;),{&quot;created_time.1&quot;, &quot;created_time.2&quot;}) |
| **Alterar Tipo** das novas colunas (etapa automática) |Tipo Alterado |Table.TransformColumnTypes  (#&quot;Split Column by Delimiter&quot;,{{&quot;created_time.1&quot;, type date}, {&quot;created_time.2&quot;, type time}}) |
| **Renomear **uma coluna**** |Colunas Renomeadas |Table.RenameColumns  (#&quot;Changed Type&quot;,{{&quot;created_time.1&quot;, &quot;created_date&quot;}, {&quot;created_time.2&quot;, &quot;created_time&quot;}}) |
| **Inserir **uma coluna**** |Hora Inserida |Table.AddColumn  (#&quot;Renamed Columns&quot;, &quot;Hour&quot;, each Time.Hour([created_time]), type number) |
| **Alterar tipo ** |Changed Type1 |Table.TransformColumnTypes  (#&quot;Inserted Hour&quot;,{{&quot;Hour&quot;, type text}}) |
| **Expandir os **valores em uma tabela aninhada**** |Expandir compartilhamentos |Table.ExpandRecordColumn  (#&quot;Changed Type1&quot;, &quot;shares&quot;, {&quot;count&quot;}, {&quot;shares.count&quot;}) |
| **Renomear **a coluna**** |Renamed Columns1 |Table.RenameColumns  (#&quot; Expand shares&quot;,{{&quot;shares.count&quot;, &quot;shares&quot;}}) |
| **Alterar tipo** |Changed Type2 |Table.TransformColumnTypes  (#&quot;Renamed Columns1&quot;,{{&quot;shares&quot;, Int64.Type}}) |

## <a name="task-4-create-additional-visualizations-using-the-report-view"></a>**Tarefa 4: criar visualizações adicionais com a exibição de Relatório**
Agora que convertemos os dados para o formato que precisamos para o restante da nossa análise, podemos carregar a tabela resultante em nosso Relatório e criar visualizações adicionais.

**Etapa 1:** carregar a consulta em seu relatório

Para carregar os resultados da consulta no relatório, precisamos selecionar **Carregar e Fechar** do **Editor de Consultas**. Isso carregará nossas alterações no Power BI Desktop e fechará o **Editor de Consultas**.

![](media/desktop-tutorial-facebook-analytics/t_fb_1-loadandclose.png)

No Power BI Desktop, precisamos garantir que estamos na exibição de **Relatório** . Selecione o ícone superior da barra à esquerda no Power BI Desktop.

![](media/desktop-tutorial-facebook-analytics/17.png)

**Etapa 2:** criar um Gráfico de linhas e um Gráfico de barras

Para criar uma visualização, é possível arrastar campos da **lista Campos** e soltá-los na **tela Relatório**.

1. Arraste o campo **compartilhamentos** para a tela **Relatório** , o que cria um gráfico de barras. Em seguida, arraste created_date para o gráfico para que o Power BI Desktop altere a visualização para um \_Gráfico de **Linhas**.
   
   ![](media/desktop-tutorial-facebook-analytics/19.png)
2. Em seguida, arraste o campo **compartilhamentos** e solte-o na **tela Relatório**. Agora, arraste o campo **Hora** para a seção **eixo** na **Lista Campos**.
   
   ![](media/desktop-tutorial-facebook-analytics/20.png)
3. Podemos facilmente alterar o tipo de visualização clicando em um ícone diferente no painel **Visualização** . A seta na imagem abaixo aponta para o ícone **Gráfico de Barras** .
   
   ![](media/desktop-tutorial-facebook-analytics/21.png)
4. Altere o tipo de visualização para **Gráfico de Barras**.
5. O **Gráfico de Barras** é criado, mas esse não é o eixo que queremos – queremos que ele seja classificado na outra direção (de alto para baixo). Selecione a seta para baixo ao lado de **Eixo Y** para expandir essa seção. Precisamos alterar o tipo de eixo de **Contínuo** para **Categórico**, para que ele seja classificado da forma como desejamos (a imagem abaixo mostra o eixo antes de fazermos a seleção - confira a próxima imagem para ver a aparência que desejamos para ele).

![](media/desktop-tutorial-facebook-analytics/22.png)

Essa é uma melhor opção. E agora temos três visualizações nesta página, que podemos dimensionar da forma desejada para preencher a página de relatório.

![](media/desktop-tutorial-facebook-analytics/23.png)

Como você pode ver, é fácil personalizar visualizações em seu relatório para apresentar os dados como você desejar. O Power BI Desktop fornece uma experiência perfeita de ponta a ponta, desde a obtenção de dados por meio de uma ampla variedade de fontes de dados e a modelagem desses dados para atender às suas necessidades de análise, até a visualização de tais dados de maneiras avançadas e interativas. Quando seu relatório estiver pronto, você poderá [carregá-lo no Power BI](desktop-upload-desktop-files.md) e criar painéis baseados nele, que poderão ser compartilhados com outros usuários do Power BI.

Você pode baixar o resultado final deste tutorial [aqui](http://download.microsoft.com/download/1/4/E/14EDED28-6C58-4055-A65C-23B4DA81C4DE/FacebookAnalytics.pbix)

### <a name="where-else-can-i-get-more-information"></a>Onde mais posso obter outras informações?
* [Leia outros tutoriais do Power BI Desktop](http://go.microsoft.com/fwlink/?LinkID=521937)
* [Assista a vídeos do Power BI Desktop](http://go.microsoft.com/fwlink/?LinkID=519322)
* [Visite o Fórum do Power BI](http://go.microsoft.com/fwlink/?LinkID=519326)
* [Leia o Blog do Power BI](http://go.microsoft.com/fwlink/?LinkID=519327)



