---
title: "P e R de introdução ao Power BI (tutorial)"
description: "Tutorial: introdução com P e R no serviço do Power BI usando o exemplo Análise de Varejo"
services: powerbi
documentationcenter: 
author: mihart
manager: kfile
backup: 
editor: 
tags: 
qualityfocus: 
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 09/25/2017
ms.author: mihart
ms.openlocfilehash: 2038fb5bd4a21235c3026c8506ae30b8c3e287e4
ms.sourcegitcommit: 99cc3b9cb615c2957dde6ca908a51238f129cebb
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/13/2017
---
# <a name="get-started-with-power-bi-qa-tutorial"></a>P e R de introdução ao Power BI (tutorial)
## <a name="tutorial-use-power-bi-qa-with-the-retail-analysis-sample"></a>Tutorial: usar o P e R do Power BI com o exemplo de Análise de Varejo
Às vezes, a maneira mais rápida de obter uma resposta de seus dados é fazer uma pergunta usando o idioma natural.  Neste tutorial, examinaremos 2 formas diferentes de criar a mesma visualização: compilá-la em um relatório e fazer uma pergunta com perguntas e respostas.  

## <a name="method-1-using-the-report-editor"></a>Método 1: usando o editor de relatórios
1. Em seu espaço de trabalho do Power BI, selecione **Obter Dados** \> **Amostras** \> **Amostra de Análise de Varejo** > **Conectar**.
   
    ![](media/power-bi-visualization-introduction-to-q-and-a/power-bi-dashboard.png)
2. O painel contém um bloco de gráfico de área para "Vendas do último ano e vendas deste ano”.  Selecione este bloco. 
   
   * Se este bloco foi criado com perguntas e respostas, selecionar o bloco vai abrir o P e R. 
   * Mas esse bloco foi criado em um relatório, portanto o relatório é aberto para a página que contém esta visualização.
3. Abra o relatório no modo Exibir Edição selecionado **Editar Relatório**.  Se você não for proprietário de um relatório, não terá a opção para abri-lo no modo de exibição de edição.
   
    ![](media/power-bi-visualization-introduction-to-q-and-a/power-bi-edit-report.png)
4. Selecione o gráfico de área e examinar as configurações do painel **Campos** .  O criador do relatório criou esse gráfico selecionando esses três valores (**Hora > FiscalMonth**, **Vendas > Vendas Deste Ano**, **Vendas > Vendas do Ano Passado > Valor**) e organizando-os nas seções **Eixo** e **Valores**.
   
    ![](media/power-bi-visualization-introduction-to-q-and-a/gnatutorial_3-new.png)

## <a name="method-2-using-qa"></a>Método 2: usando perguntas e respostas
Como podemos criar esse mesmo gráfico de linha usando perguntas e respostas?

![](media/power-bi-visualization-introduction-to-q-and-a/power-bi-qna.png)

1. Navegue de volta para o dashboard de exemplo Análise de Varejo.
2. Use a linguagem natural, digite de forma semelhante na caixa de pergunta:
   
   **quais foram as vendas deste ano e as vendas do ano passado por mês como um gráfico de área**
   
   Ao digitar uma pergunta, o P e R do Power BI escolhe a melhor visualização para exibir sua resposta, e a visualização muda dinamicamente, na medida em que você modifica a pergunta. Além disso, P e R e ajuda a formatar sua pergunta com sugestões, preenchimento automático e a correção ortográfica.
   
   Quando você terminar de digitar sua pergunta, o resultado será exatamente o mesmo gráfico que vimos no relatório.  Mas criá-lo dessa maneira era muito mais rápido!
   
   ![](media/power-bi-visualization-introduction-to-q-and-a/powerbi-qna-areachart.png)
3. De modo semelhante ao trabalho com relatórios, na P e R, você tem acesso aos painéis Visualizações, Filtros e Campos.  Abra esses painéis para explorar e modificar ainda mais seu visual.
4. Fixar o gráfico para o painel de controle, selecione o ícone de pino ![](media/power-bi-visualization-introduction-to-q-and-a/pinnooutline.png).

## <a name="next-steps"></a>Próximas etapas
[Que tipo de perguntas posso fazer em P e R?](service-q-and-a.md)

[P e R no Power BI](service-q-and-a.md)

[Faça seus dados funcionarem bem com P e R no Power BI](service-prepare-data-for-q-and-a.md)

[preparo de uma pasta de trabalho para P e R](service-prepare-data-for-q-and-a.md)

Mais perguntas? [Experimente a Comunidade do Power BI](http://community.powerbi.com/)

