---
title: Usando os botões no Power BI
description: Botões no Power BI Desktop permitem que você faça relatórios e painéis que se comportam como aplicativos e aprofunde o engajamento com usuários
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
ms.date: 04/04/2018
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: 7858c76703feb53ebb74bec998ecbebcba3994cc
ms.sourcegitcommit: c80fbf5b12754ce217cb47a17cb5400b1036a8f2
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2018
---
# <a name="using-buttons-in-power-bi"></a>Usando os botões no Power BI
Usar **botões** no Power BI permite que você crie relatórios e painéis que se comportam de modo semelhante a aplicativos e, assim, cria um ambiente envolvente para que os usuários possam focalizar, clicar em e interagir ainda mais com conteúdo do Power BI. Você pode adicionar botões a relatórios no **Power BI Desktop** e compartilhar ou publicar esses relatórios no serviço do Power BI para criar painéis que fornecem um comportamento de aplicativo para usuários.

![Botões no Power BI](media/desktop-buttons/desktop-buttons_01.png)

Os botões que você cria no **Power BI Desktop** estão disponíveis para uso em relatórios ou painéis publicados no **serviço do Power BI**.

## <a name="creating-buttons-in-reports"></a>Criação de botões em relatórios
Para criar um botão em um relatório do **Power BI Desktop**, na faixa de opções **Início**, selecione **Botões**. Feito isso, será exibido um menu suspenso, no qual você pode selecionar o botão desejado de uma coleção de opções, conforme mostrado na imagem a seguir. 

![Adicionar um controle de botão no Power BI Desktop](media/desktop-buttons/desktop-buttons_02.png)

Quando você cria um botão e o seleciona na tela de relatório, o painel **Visualizações** mostra várias maneiras de personalizar o botão de acordo com as suas necessidades. Por exemplo, você pode ativar ou desativar o **Texto do Botão** alternando o controle deslizante no cartão do painel **Visualizações**. Você também pode alterar o ícone do botão, o preenchimento do botão, o título e a ação executada quando os usuários clicam no botão em um relatório ou painel, entre outras propriedades.

![Formatar um botão no Power BI Desktop](media/desktop-buttons/desktop-buttons_03.png)

## <a name="set-button-properties-when-idle-hovered-over-or-selected"></a>Definir propriedades do botão quando ocioso, focalizado ou selecionado

Botões no Power BI têm três estados: padrão (como eles aparecem quando não focalizados ou selecionados), quando focalizados ou quando selecionados (conhecido como sendo *clicado*). Muitos dos cartões no painel **Visualizações** podem ser modificados individualmente com base em um desses três estados, fornecendo muita flexibilidade para personalizar os botões.

Os seguintes cartões no painel **Visualizações** permitem que você ajuste a formatação ou o comportamento de um botão com base em seus três estados:

* Texto do botão
* Ícone
* Contorno
* Preencher

Para selecionar como o botão deve ser exibido para cada estado, expanda um dos cartões e selecione na lista suspensa que aparece na parte superior do cartão. Na imagem a seguir, você vê o cartão **Contorno** expandido, com a lista suspensa selecionada para mostrar os três estados:

![Três estados de um botão no Power BI Desktop](media/desktop-buttons/desktop-buttons_04.png)


## <a name="select-the-action-for-a-button"></a>Selecionar a ação para um botão

Você pode selecionar qual ação é realizada quando o usuário seleciona um botão no Power BI. Você pode acessar as opções para ações de botão no cartão **Ação** no painel **Visualizações**.

![Ação de um botão no Power BI](media/desktop-buttons/desktop-buttons_05.png)

As opções de ações do botão são:

* Voltar
* Indicador
* P e R

A seleção de **Voltar** retorna o usuário para a página anterior do relatório. Isso é especialmente útil para páginas de detalhamento.

A seleção de **Indicador** apresenta a página do relatório associado a um indicador que está definido para o relatório atual. [Saiba mais sobre indicadores no Power BI](desktop-bookmarks.md). 

A seleção de **P e R** na lista suspensa apresenta uma janela **Explorador de P e R**. 

Determinados botões terão uma ação padrão selecionada automaticamente. Por exemplo, o tipo de botão **P e R** seleciona automaticamente **P e R** como a ação padrão. Saiba mais sobre o **Explorador de P e R** conferindo [esta postagem no blog](https://powerbi.microsoft.com/blog/power-bi-desktop-april-2018-feature-summary/#Q&AExplorer).

Experimente ou teste os botões que você cria para o relatório usando *CTRL+clique* no botão que você deseja usar. 

## <a name="next-steps"></a>Próximas etapas
Para obter mais informações sobre os recursos que são semelhantes ou interagem com botões, consulte os seguintes artigos:

* [Usar o detalhamento no Power BI Desktop](desktop-drillthrough.md)
* [Exibir um bloco do dashboard ou visual do relatório no modo de Foco](service-focus-mode.md)
* [Usar indicadores para compartilhar insights e criar histórias no Power BI](desktop-bookmarks.md)

