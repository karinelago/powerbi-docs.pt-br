---
title: Configurações de exibição de página e configurações de visualização de página para um relatório
description: Configurações de exibição de página e configurações de visualização de página para um relatório
author: mihart
manager: kfile
ms.reviewer: ''
featuredvideoid: ''
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 12/24/2017
ms.author: mihart
LocalizationGroup: Reports
ms.openlocfilehash: af90ba6bcf85c07d2d046ed21f733ca7c16e3856
ms.sourcegitcommit: 998b79c0dd46d0e5439888b83999945ed1809c94
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/17/2018
---
# <a name="page-display-settings-in-a-power-bi-report"></a>A página exibe as configurações em um relatório do Power BI
Compreendemos que é essencial manter o pixel de layout de relatório perfeito. Às vezes, isso pode ser desafiador, porque você e seus colegas exibem esses relatórios em telas com taxas de proporção diferentes e tamanhos. 

O modo de exibição padrão é **Ajustar à página** e o tamanho de exibição padrão é **16:9**. Se você quiser bloquear uma taxa de proporção diferente ou quiser ajustar seu relatório de outra forma, há duas ferramentas para ajudá-lo: as configurações de ***Modo de Exibição da Página*** e de ***Tamanho da Página***.

<iframe width="560" height="315" src="https://www.youtube.com/embed/5tg-OXzxe2g" frameborder="0" allowfullscreen></iframe>


## <a name="where-to-find-page-view-settings-in-power-bi-service-and-power-bi-desktop"></a>Onde encontrar as Configurações de exibição de página no serviço do Power BI e no Power BI Desktop
As Configurações de exibição de página estão disponíveis no serviço do Power BI e no Power BI Desktop, mas a interface é um pouco diferente. As duas seções a seguir explicam onde você pode encontrar as Configurações de exibição em cada ferramenta do Power BI.

### <a name="in-power-bi-desktop"></a>No Power BI Desktop
No Modo de Exibição de Relatório, selecione a guia **Exibição** para abrir as Configurações de exibição de página, bem como as configurações de layout do telefone.

  ![painel Seleção](media/power-bi-report-display-settings/power-bi-desktop-view-settings.png)

### <a name="in-power-bi-service-apppowerbicom"></a>No serviço do Power BI (app.powerbi.com)
No serviço do Power BI, abra um relatório e selecione **Exibição** na barra de menus superior à esquerda.

![](media/power-bi-report-display-settings/power-bi-change-page-view.png)

As configurações de Exibição de Página estão disponíveis no [modo de exibição de Leitura e no modo de exibição de Edição](service-reading-view-and-editing-view.md). No Modo de Exibição de Edição, o proprietário de um relatório pode atribuir configurações de exibição de página para páginas de relatório individuais, e essas configurações são salvas com o relatório. Quando os colegas abrirem o relatório no Modo de Exibição de Leitura, verão a exibição das páginas do relatório usando as configurações do proprietário.  No Modo de Exibição de Leitura, colegas podem alterar *algumas* das Configurações de exibição de página, mas as alterações não são salvas ao sair do relatório.

##    <a name="page-view-settings"></a>Configurações de exibição de página
O primeiro conjunto de configurações do *Modo de Exibição da Página* controla a exibição das páginas do relatório com base na janela do navegador.  Escolha entre:

* **Ajustar à Página** (padrão): o conteúdo é dimensionado para um melhor ajuste à página
* **Ajustar à Largura**: o conteúdo é dimensionado para se ajustar na largura da página
* **Tamanho Real**: o conteúdo é exibido em tamanho normal

O segundo conjunto de configurações do *Modo de Exibição de Página* controla o posicionamento de objetos na tela do relatório.

* **Mostrar linhas de grade**: ativa linhas de grade para ajudar a posicionar objetos na tela do relatório
* **Ajustar à grade**: use com **Mostrar linhas de grade** para posicionar e alinhar os objetos na tela de relatório de modo preciso 
* **Bloquear objetos**: bloqueia todos os objetos na tela, de modo que eles não podem ser movidos ou redimensionados
* **Painel Seleção**: o painel Seleção lista todos os objetos na tela, e você pode decidir quais mostrar e quais ocultar

    ![painel Seleção](media/power-bi-report-display-settings/power-bi-selection-pane.png)



## <a name="page-size-settings"></a>Configurações de tamanho de página
![](media/power-bi-report-display-settings/power-bi--page-size.png)

As configurações de *Tamanho de Página* só ficam disponíveis para proprietários de relatório. No serviço do Power BI (app.powerbi.com), isso significa poder abrir o relatório no [Modo de Exibição de Edição](service-reading-view-and-editing-view.md). Essas configurações controlam a taxa de exibição e o tamanho real (em pixels) da tela do relatório.   

* proporção de 4:3
* proporção de 16:9 (padrão)
* Cortana
* Letra
* Personalizado (altura e largura em pixels)

## <a name="next-steps"></a>Próximas etapas
[Saiba como usar as configurações de Modo de Exibição de Página e Tamanho da Página em seus relatórios do Power BI](power-bi-change-report-display-settings.md).

Leia mais sobre [relatórios no Power BI](service-reports.md)

[Power BI – conceitos básicos](service-basic-concepts.md)

Mais perguntas? [Experimente a Comunidade do Power BI](http://community.powerbi.com/)

