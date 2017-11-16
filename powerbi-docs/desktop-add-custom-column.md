---
title: Adicionar uma coluna personalizada no Power BI Desktop
description: Criar rapidamente uma nova coluna personalizada no Power BI Desktop
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
ms.date: 10/12/2017
ms.author: davidi
ms.openlocfilehash: 22e66bfef84753054ac65062b2b08cbdd5572088
ms.sourcegitcommit: 284b09d579d601e754a05fba2a4025723724f8eb
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/15/2017
---
# <a name="add-a-custom-column-in-power-bi-desktop"></a>Adicionar uma coluna personalizada no Power BI Desktop
Você pode adicionar facilmente uma nova coluna personalizada de dados ao modelo usando o **Editor de Consultas** no **Power BI Desktop**. É possível criar e renomear sua coluna personalizada usando botões fáceis para criar [fórmulas M](https://msdn.microsoft.com/library/mt270235.aspx) que definam a coluna personalizada. A fórmula M tem um [conjunto de conteúdo de referência de função abrangente](https://msdn.microsoft.com/library/mt779182.aspx). 

![](media/desktop-add-custom-column/add-custom-column_01.png)

A criação de uma coluna personalizada é outra **Etapa Aplicada** à consulta criada no **Editor de Consultas**, o que significa que ela pode ser alterada, movida mais cedo ou mais tarde ou modificada a qualquer momento.

## <a name="use-query-editor-to-add-a-new-custom-column"></a>Usar o Editor de consultas para adicionar uma nova coluna personalizada
Para criar uma nova coluna personalizada, inicie o **Editor de Consultas**. Para fazer isso, selecione **Editar consultas** na faixa de opções **Início** no **Power BI Desktop**.

![](media/desktop-add-custom-column/add-column-from-example_02.png)

Uma vez que o **Editor de Consultas** é iniciado e você tem alguns dados carregados, pode adicionar uma coluna personalizada selecionando a guia **Adicionar Coluna** na faixa de opções e, em seguida, selecionando **Coluna Personalizada**.

![](media/desktop-add-custom-column/add-custom-column_02.png)

Quando você faz isso, a janela **Adicionar Coluna Personalizada** é exibida, o que é discutido na seção a seguir.

## <a name="the-add-custom-column-window"></a>A janela Adicionar Coluna Personalizada
Na janela **Adicionar Coluna Personalizada**, você vê a lista de campos disponíveis no painel à direita, o nome da coluna personalizada na parte superior (é possível renomeá-la apenas digitando um novo nome na caixa de texto) e a [fórmula **M**](https://msdn.microsoft.com/library/mt779182.aspx) que você cria (ou grava) com base na inserção de campos da direita, na adição de operadores e na criação da fórmula na qual sua nova coluna personalizada será definida. 

![](media/desktop-add-custom-column/add-custom-column_03.png)

## <a name="create-formulas-for-your-custom-column"></a>Criar fórmulas para a coluna personalizada
Você pode selecionar um campo na lista **Colunas disponíveis:** à direita e selecionar **<< Inserir** para adicioná-las à fórmula da coluna personalizada. Você pode também simplesmente clicar duas vezes em uma coluna na lista para adicioná-la.

Ao digitar a fórmula e compilar sua coluna, na parte inferior da janela você verá um indicador informando, em tempo real (conforme você digita), se os erros de sintaxe são detectados. Se tudo correr bem, você verá uma marca de seleção verde.

![](media/desktop-add-custom-column/add-custom-column_04.png)

Mas se houver algum tipo de erro na sintaxe, você verá um ícone de aviso amarelo, juntamente com o erro detectado e um link que coloca o cursor (da fórmula) onde o erro é detectado.

![](media/desktop-add-custom-column/add-custom-column_05.png)

Quando você seleciona **OK**, a coluna personalizada é adicionada ao modelo e a etapa **Personalizada Adicionada** é adicionada às **Etapas Aplicadas** da consulta.

![](media/desktop-add-custom-column/add-custom-column_06.png)

Se você clicar duas vezes na etapa **Personalizada Adicionada** no painel **Etapas Aplicadas**, a janela **Adicionar Coluna Personalizada** será exibida novamente, com a fórmula da coluna personalizada criada já carregada e pronta modificação, se necessário.

## <a name="using-the-advanced-editor-for-custom-columns"></a>Usando o editor avançado para colunas personalizadas
Você também pode criar uma coluna personalizada (e modificar qualquer etapa de sua consulta, a esse respeito) usando o **Editor Avançado**. Em **Editor de Consultas** selecione a guia **Exibir** e, em seguida, selecione **Editor Avançado** para exibir o **Editor Avançado**.

![](media/desktop-add-custom-column/add-custom-column_07.png)

O **Editor Avançado** lhe dá total controle sobre sua consulta.

## <a name="next-steps"></a>Próximas etapas
Existem outras maneiras de criar uma coluna personalizada, incluindo a criação de uma coluna com base nos exemplos fornecidos no **Editor de Consultas**. Consulte o seguinte artigo para obter mais informações sobre como criar colunas personalizadas com base em exemplos:

* [Adicionar uma coluna de um exemplo no Power BI Desktop](desktop-add-column-from-example.md)
* [Introdução à linguagem de fórmula M](https://msdn.microsoft.com/library/mt270235.aspx)
* [Referência da função M](https://msdn.microsoft.com/library/mt779182.aspx)  

