---
title: Conectar-se a dados no Power BI Desktop
description: Conectar-se a dados no Power BI Desktop
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
ms.date: 12/06/2017
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 94e52d2d56cd7ba0ec04db47bc93dd18fc880f39
ms.sourcegitcommit: 5e1f7d2673efe25c47b9b9f315011055bfe92c8f
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/09/2018
---
# <a name="connect-to-data-in-power-bi-desktop"></a>Conectar-se a dados no Power BI Desktop
Com o Power BI Desktop você pode conectar-se facilmente ao mundo dos dados, que está em constante expansão. Se não tiver o Power BI Desktop, você pode [baixá-lo](http://go.microsoft.com/fwlink/?LinkID=521662) e instalá-lo.

Há *todos os tipos* de fontes de dados disponíveis no Power BI Desktop. A imagem a seguir mostra como conectar-se aos dados selecionando a faixa de opções **Arquivo** e **Obter Dados \> Mais**.

![](media/desktop-connect-to-data/getdatavid_smallv2.gif)

Neste exemplo, nos conectaremos a uma fonte de dados **Web** .

Imagine que você está se aposentando – você deseja morar onde há muito sol, uma quantia interessante de impostos e uma boa assistência médica. Ou… talvez você seja um analista de dados e queira essas informações para ajudar seus clientes - como, por exemplo, para ajudar seu cliente que fabrica capas de chuva a direcionar suas vendas para onde chove *muito*.

De qualquer modo, você encontra um recurso da Web que tenha dados interessantes sobre esses tópicos e muito mais:

[*http://www.bankrate.com/finance/retirement/best-places-retire-how-state-ranks.aspx*](http://www.bankrate.com/finance/retirement/best-places-retire-how-state-ranks.aspx)

Selecione**Obter Dados \> Web** e digite o endereço.

![](media/desktop-connect-to-data/connecttodata_3.png)

Ao selecionar **OK**, a funcionalidade **Consulta** do Power BI Desktop começa a trabalhar. O Power BI Desktop entra em contato com o recurso da Web e a janela **Navegador** retorna os resultados encontrados pela consulta nessa página da Web. Nesse caso, ela encontrou uma tabela (Tabela 0) e o Documento geral. Estamos interessados na tabela, então vamos selecioná-la na lista. A janela **Navegador** exibe uma visualização.

![](media/desktop-connect-to-data/datasources_fromnavigatordialog.png)

Neste ponto, podemos editar a consulta antes de carregar a tabela selecionando **Editar** na parte inferior da janela, ou podemos carregar a tabela.

Se selecionamos **Editar**, a tabela é carregada e o Editor de Consulta é iniciado. O painel **Configurações de Consulta** é exibido (se não for, é possível selecionar **Exibição** na faixa de opções e, em seguida, **Exibir \> Configurações de Consulta** para exibir o painel **Configurações de Consulta**). Eis aqui a aparência que isso tem.

![](media/desktop-connect-to-data/designer_gsg_editquery.png)

Todas essas pontuações são texto e não números, e precisamos que elas sejam números. Sem problemas – basta clicar com o botão direito do mouse no título da coluna e selecionar **Alterar Tipo \> Número Inteiro** para alterá-los. Para escolher mais de uma coluna, primeiro selecionamos uma coluna, mantemos pressionada a tecla **SHIFT**, selecionamos colunas adjacentes adicionais e clicamos com o botão direito do mouse em um título de coluna para alterar todas as colunas selecionadas. Use **CTRL** para selecionar colunas que não são adjacentes.

![](media/desktop-connect-to-data/designer_gsg_changedatatype.png)

Em **Configurações de Consulta**, as **Etapas Aplicadas** refletirão as alterações que foram feitas. Conforme você realiza alterações adicionais aos dados, o Editor de Consultas registrará essas alterações na seção **Etapas Aplicadas** e você poderá ajustar, revisitar, reorganizar ou excluí-las conforme necessário.

![](media/desktop-connect-to-data/designer_gsg_appliedsteps_changedtype.png)

Ainda podem ser feitas alterações adicionais à tabela depois de ela ser carregada, mas o que já fizemos é suficiente por enquanto. Quando terminamos, selecionamos **Fechar e Aplicar** na faixa de opções **Home** e o Power BI Desktop aplica nossas alterações e fecha o Editor de Consulta.

![](media/desktop-connect-to-data/connecttodata_closenload.png)

Com o modelo de dados carregado, na exibição de **Relatório** no Power BI Desktop, podemos começar criando visualizações arrastando campos para a tela.

![](media/desktop-connect-to-data/connecttodata_dragontoreportview.png)

Obviamente, esse é um modelo simples com uma única conexão de dados; a maioria dos relatórios do Power BI Desktop terá conexões a diferentes fontes de dados, modeladas para atender às suas necessidades, com relações que produzem um modelo de dados avançado. 

### <a name="next-steps"></a>Próximas etapas
Há inúmeras coisas que você pode fazer com o Power BI Desktop. Para obter mais informações sobre seus recursos, consulte as seguintes fontes:

* [Introdução ao Power BI Desktop](desktop-getting-started.md)
* [Visão geral de Consulta com o Power BI Desktop](desktop-query-overview.md)
* [Fontes de dados no Power BI Desktop](desktop-data-sources.md)
* [Formatar e combinar dados com o Power BI Desktop](desktop-shape-and-combine-data.md)
* [Tarefas comuns de consulta no Power BI Desktop](desktop-common-query-tasks.md)   

Deseja nos enviar comentários? Ótimo – use o item de menu **Enviar uma Ideia** no Power BI Desktop ou visite [Comentários da comunidade](http://community.powerbi.com/t5/Community-Feedback/bd-p/community-feedback). Aguardamos seu contato!

![](media/desktop-connect-to-data/sendfeedback.png)

