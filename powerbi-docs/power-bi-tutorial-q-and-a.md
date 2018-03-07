---
title: "Tutorial – usando perguntas e respostas em um dashboard ou em um relatório"
description: "Tutorial sobre como usar o Power BI P e r para criar novas visualizações em dashboards e em relatórios."
services: powerbi
documentationcenter: 
author: mihart
manager: kfile
editor: 
tags: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 01/17/2018
ms.author: mihart
LocalizationGroup: Ask questions of your data
ms.openlocfilehash: 44501e5447248164f6f04d4463213939975e18ae
ms.sourcegitcommit: 88c8ba8dee4384ea7bff5cedcad67fce784d92b0
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/24/2018
---
# <a name="tutorial-how-to-use-qa-to-create-visualizations-and-build-reports"></a>Tutorial: Como usar P e R para criar visualizações e relatórios
A [Visão geral de P e R](power-bi-q-and-a.md) apresentou você às P e R do Power BI e fez a distinção entre *consumidores* (que têm dashboards e relatórios compartilhados com eles) e *criadores* (proprietários de relatórios e conjuntos de dados subjacentes). A primeira parte deste tutorial é destinada principalmente a pessoas que consumem dashboards usando o serviço do Power BI. E a segunda parte é projetada para as pessoas que criam relatórios usando o serviço do Power BI ou Power BI Desktop. [A P e R e o Power BI Mobile](mobile-apps-ios-qna.md) e [a P e R e o Power BI Embedded](developer/qanda.md) são abordados em artigos separados.

P e R é interativo e até mesmo divertido e, mais frequentemente do que o contrário, uma pergunta levará a muitas outras conforme as visualizações revelam caminhos interessantes para buscar. Veja Amanda demonstrando o uso de P e R para criar visualizações, aprofundando-se nesses elementos visuais e fixando-os nos dashboards.

<iframe width="560" height="315" src="https://www.youtube.com/embed/qMf7OLJfCz8?list=PL1N57mwBHtN0JFoKSR0n-tBkUJHeMP2cP" frameborder="0" allowfullscreen></iframe>

## <a name="part-1-use-qa-on-a-dashboard-in-power-bi-service-apppowerbicom"></a>Parte 1: usar P e R em um dashboard no serviço do Power BI (app.powerbi.com)
Um dashboard contém blocos fixados de um ou mais conjuntos de dados, para que você possa fazer perguntas sobre os dados contidos em qualquer um desses conjuntos de dados. Para ver quais relatórios e conjuntos de dados foram usados para criar o dashboard, selecione **Exibir relacionados** na barra de menus.

![](media/power-bi-tutorial-q-and-a/power-bi-view-related.png)

A caixa de perguntas de P e R está localizada no canto superior esquerdo do dashboard e é nesse local que você digita sua pergunta usando seu idioma natural. P e R reconhece as palavras que você digita e descobre onde (o conjunto de dados) encontrar a resposta. P e R também ajuda a sua pergunta com preenchimento automático, ajuste e outros auxílios textuais e visuais.

![](media/power-bi-tutorial-q-and-a/powerbi-qna.png)

A resposta à sua pergunta é exibida como uma visualização interativa e atualizações como modificar a pergunta.

1. Abra um dashboard e coloque o cursor na caixa de perguntas. Mesmo antes de começar a digitar, a P e R exibe uma nova tela com sugestões para ajudá-lo a formar sua pergunta. Você verá os nomes das tabelas nos [conjuntos de dados subjacentes](service-get-data.md) e poderá até mesmo ver perguntas completas listadas se o proprietário de conjunto de dados tiver criado [perguntas em destaque](service-q-and-a-create-featured-questions.md).

   ![](media/power-bi-tutorial-q-and-a/powerbi-qna-cursor.png)

   Você sempre pode escolher uma dessas perguntas como ponto de partida e continuar a refinar a pergunta para encontrar a resposta específica que você está procurando. Ou use um nome de tabela para ajudá-lo com palavra em uma nova pergunta.

2. Selecione entre as opções de conjunto de dados ou comece a digitar sua própria pergunta e selecione uma das sugestões da lista suspensa.

   ![](media/power-bi-tutorial-q-and-a/powerbi-qna-list.png)

3. Ao digitar uma pergunta, o P e R do Power BI escolhe a melhor [visualização ](power-bi-visualization-types-for-reports-and-q-and-a.md)para exibir sua resposta; e a visualização muda dinamicamente à medida que você modifica a pergunta.

   ![](media/power-bi-tutorial-q-and-a/powerbi-qna-viz.png)

4. Quando você digita uma pergunta, o Power BI procura a melhor resposta em qualquer conjunto de dados que tenha um bloco nesse dashboard.  Se todos os blocos forem do *conjuntodedadosA*, sua resposta será proveniente do *conjuntodedadosA*.  Se houver blocos do *datasetA* e do *datasetB*, a P e R pesquisará a melhor resposta nesses dois conjuntos de dados.

   > [!TIP]
   > Por isso, tenha cuidado. Se você tiver apenas um bloco do *datasetA* e removê-lo do dashboard, a P e R deixará de ter acesso ao *datasetA*.
   >
   >
5. Quando estiver satisfeito com o resultado, [fixe a visualização em um dashboard](service-dashboard-pin-tile-from-q-and-a.md) selecionando o ícone para fixar no canto superior direito. Se o dashboard tiver sido compartilhado com você ou for parte de um aplicativo, não será possível fixar.

   ![](media/power-bi-tutorial-q-and-a/pbi_qna_finish-typing-question.jpg)

##    <a name="part-2-use-qa-in-a-report-in-power-bi-service-or-power-bi-desktop"></a>Parte 2: usar P e R em um relatório no serviço do Power BI ou no Power BI Desktop

Use P e R para explorar o conjunto de dados e adicionar visualizações ao relatório e aos dashboards. Um relatório se baseia em um único conjunto de dados e pode ser totalmente em branco ou conter páginas repletas de visualizações. Mas apenas o fato de um relatório estar em branco não significa que não exista nenhum dado para você explorar – o conjunto de dados é vinculado ao relatório e está esperando que você explore e crie visualizações.  Para ver qual conjunto de dados está sendo usado para criar um relatório, abra o relatório no modo de exibição de Leitura do serviço do Power BI e selecione **Exibir relacionados** na barra de menus.

![](media/power-bi-tutorial-q-and-a/power-bi-view-related.png)

Para usar P e R em relatórios, você deverá ter permissões de edição para o relatório e para o conjunto de dados subjacente. No [tópico Visão geral de P e R](power-bi-q-and-a.md), nos referimos a isso como um cenário de *criador*. Portanto, se você estiver, em vez disso, *consumindo* um relatório compartilhado com você, a P e R não estará disponível.

1. Abra um relatório no modo de exibição de Edição (serviço do Power BI) ou de Relatório (Power BI Desktop) e selecione **Fazer uma pergunta** na barra de menus.

    **Área de trabalho**    
    ![](media/power-bi-tutorial-q-and-a/power-bi-desktop-question.png)

    **Serviço**    
    ![](media/power-bi-tutorial-q-and-a/power-bi-service.png)

2. Uma caixa de perguntas de P e R é exibida na tela do relatório. No exemplo a seguir, a caixa de perguntas é exibida na parte superior de outra visualização. Isso é bom, mas pode ser melhor [adicionar uma página em branco ao relatório](power-bi-report-add-page.md) antes de fazer uma pergunta.

    ![](media/power-bi-tutorial-q-and-a/power-bi-ask-question.png)

3. Coloque o cursor na caixa de pergunta. Conforme você digita, a P e R exibe sugestões para ajudá-lo a formular a sua pergunta.

   ![](media/power-bi-tutorial-q-and-a/power-bi-q-and-a-suggestions.png)

4. Ao digitar uma pergunta, o P e R do Power BI escolhe a melhor [visualização ](power-bi-visualization-types-for-reports-and-q-and-a.md)para exibir sua resposta; e a visualização muda dinamicamente à medida que você modifica a pergunta.

   ![](media/power-bi-tutorial-q-and-a/power-bi-q-and-a-visual.png)

5. Quando você tiver a visualização que desejar, selecione ENTER. Para salvar a visualização com o relatório, selecione **Arquivo > Salvar**.

6. Interaja com a nova visualização. Não importa como você criou a visualização – a mesma interatividade, formatação e recursos estão disponíveis.

  ![](media/power-bi-tutorial-q-and-a/power-bi-q-and-a-ellipses.png)

  Se você criou a visualização no serviço do Power BI, você pode até mesmo [fixá-la a um dashboard](service-dashboard-pin-tile-from-q-and-a.md).

## <a name="tell-qa-which-visualization-to-use"></a>Informe ao P e R qual visualização deve ser usada.
Com P e R, você pode não apenas solicitar que seus dados falem por si próprios, mas também dizer ao Power BI como você deseja que a resposta seja exibida. Basta adicionar "como um <visualization type>" ao final da sua pergunta.  Por exemplo, "mostrar o volume de inventário pela fábrica como um mapa" e "mostrar inventário total como um cartão de crédito".  Experimente.

##  <a name="considerations-and-troubleshooting"></a>Considerações e solução de problemas
- Se você tiver conectado a um conjunto de dados usando uma conexão dinâmica ou um gateway, será necessário [habilitar a P e R para esse conjunto de dados](service-q-and-a-direct-query.md).

- Você abriu um relatório e não viu a opção de P e R. Se você está usando o serviço do Power BI, certifique-se de abrir o relatório no modo de exibição de Edição. Se você não pode abrir o modo de exibição de Edição, isso significa que você não tem permissões de edição para esse relatório e não poderá usar P e R com esse relatório específico.

## <a name="next-steps"></a>Próximas etapas
Voltar a [P e R no Power BI](power-bi-q-and-a.md)   
[Tutorial: usar perguntas e respostas com o exemplo de Vendas de Varejo](power-bi-visualization-introduction-to-q-and-a.md)   
[Dicas para fazer perguntas em P e R](service-q-and-a-tips.md)   
[Preparar uma pasta de trabalho para Perguntas e respostas](service-prepare-data-for-q-and-a.md)  
[Preparar um conjunto de dados local para P e R](service-q-and-a-direct-query.md)
[Fixar um bloco ao dashboard de P e R](service-dashboard-pin-tile-from-q-and-a.md)
