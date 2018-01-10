---
title: "Criar um dashboard do Power BI de um relatório"
description: "Criar um dashboard do Power BI de um relatório"
services: powerbi
documentationcenter: 
author: mihart
manager: kfile
backup: 
editor: 
tags: 
featuredvideoid: 
qualityfocus: 
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 05/09/2017
ms.author: mihart
ms.openlocfilehash: 67cc9508d71fa29303d09e8901294a2d6b7f8a56
ms.sourcegitcommit: 804ee18b4c892b7dcbd7d7d5d987b16ef16fc2bb
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/09/2018
---
# <a name="create-a-power-bi-dashboard-from-a-report"></a>Criar um dashboard do Power BI de um relatório
Você já leu [Dashboards no Power BI](service-dashboards.md) e agora deseja criar o seu próprio. Há várias maneiras diferentes de criar um dashboard de controle – de um relatório, desde o início, de um conjunto de dados, duplicando um dashboard existente e muito mais.  Este tópico e vídeo mostram como criar um novo dashboard fixando visualizações de um relatório existente.

> **OBSERVAÇÃO**: os dashboards são um recurso do serviço do Power BI, não do Power BI Desktop. Os dashboards não podem ser criados em dispositivos móveis Power BI, mas podem ser [exibidos e compartilhados](mobile-apps-view-dashboard.md).
> 
> 

![](media/service-dashboard-create/power-bi-completed-dashboard-small.png)

## <a name="video-create-a-dashboard-by-pinning-visuals-and-images-from-a-report"></a>Vídeo: criar um dashboard fixando visuais e imagens de um relatório
Veja a Amanda criar um novo dashboard fixando visualizações de um relatório. Em seguida, tente você mesmo, usando o exemplo de análise de compras, seguindo as etapas abaixo do vídeo.

<iframe width="560" height="315" src="https://www.youtube.com/embed/lJKgWnvl6bQ" frameborder="0" allowfullscreen></iframe>

## <a name="import-a-dataset-with-a-report"></a>Importar um conjunto de dados com um relatório
Vamos importar um dos conjuntos de dados de exemplo do Power BI e usá-lo para criar nosso novo dashboard. O exemplo que usaremos é uma pasta de trabalho do Excel com duas planilhas do PowerView. Quando o Power BI importar a pasta de trabalho, ele adicionará um conjunto de dados e também um relatório ao seu espaço de trabalho.  O relatório é criado automaticamente das planilhas do PowerView.

1. [Clique neste link](http://go.microsoft.com/fwlink/?LinkId=529784) para baixar e salvar o arquivo de Excel de exemplo de análise de compras. É recomendável salvá-lo em seu OneDrive for Business.
2. Abra o serviço do Power BI no seu navegador (app.powerbi.com).
3. Selecione um espaço de trabalho existente ou crie um novo espaço de trabalho do aplicativo.
4. No painel de navegação esquerdo, selecione **Obter Dados**.
   
    ![](media/service-dashboard-create/power-bi-get-data3.png)
5. Selecione **Arquivos**.
   
   ![](media/service-dashboard-create/power-bi-select-files.png)
6. Navegue até o local em que você salvou o arquivo do Excel de exemplo de análise de compras. Selecione-o e escolha **Conectar**.
   
   ![](media/service-dashboard-create/power-bi-connectnew.png)
7. Para este exercício, selecione **Importar**.
   
    ![](media/service-dashboard-create/power-bi-import.png)
8. Quando a mensagem de êxito for exibida, selecione o **x** para fechá-la.
   
   ![](media/service-dashboard-create/power-bi-view-datasetnew.png)

### <a name="open-the-report-and-pin-some-tiles-to-a-dashboard"></a>Abra o relatório e fixe alguns blocos em um dashboard
1. Permanecendo no mesmo espaço de trabalho, selecione a guia **Relatórios**. O relatório importado recentemente é exibido com um asterisco amarelo. Selecione o nome do relatório para abri-lo.
   
    ![](media/service-dashboard-create/power-bi-reports.png)
2. O relatório é aberto no [Modo de exibição de leitura](service-reading-view-and-editing-view.md). Observe que ele tem duas guias na parte inferior: Análise de desconto e Visão geral de gastos. Cada guia representa uma página do relatório.
   
    ![](media/service-dashboard-create/power-bi-reading-view.png)
3. Passe o mouse sobre uma visualização para revelar as opções disponíveis. Para adicionar a visualização a um dashboard, selecione o ícone ![](media/service-dashboard-create/power-bi-pin-icon.png) de fixação.
   
    ![](media/service-dashboard-create/power-bi-hover.png)
4. Como estamos criando um novo dashboard, selecione a opção **Novo painel** e dê um nome. 
   
   ![](media/service-dashboard-create/power-bi-pin-tile.png)
5. Ao selecionar **Fixar**, o Power BI criará o novo dashboard no espaço de trabalho atual. Quando a mensagem **Fixado ao painel** for exibida, selecione **Ir para o dashboard**. Se for solicitado salvar o relatório, escolha **Salvar**.
   
     ![](media/service-dashboard-create/power-bi-pin-success.png)
6. O Power BI abre o novo dashboard e há um bloco – a visualização que acabamos de fixar. 
   
   ![](media/service-dashboard-create/power-bi-pinned.png)
7. Para retornar ao relatório, selecione o bloco. Fixe mais alguns blocos ao novo dashboard. Desta vez, quando a janela **Fixar no Painel** for exibida, selecione **Painel Existente**.  
   
   ![](media/service-dashboard-create/power-bi-existing-dashboard.png)

Parabéns! Você criou seu primeiro dashboard! Agora que você tem um dashboard, há muito mais que você pode fazer com ele.  Tente uma das **próximas etapas** sugeridas abaixo ou comece a testar e explorar por conta própria.   

## <a name="next-steps"></a>Próximas etapas
* [Redimensionar e mover blocos](service-dashboard-edit-tile.md)
* [Tudo sobre blocos de dashboard](service-dashboard-tiles.md)
* [Compartilhar seu dashboard criando um aplicativo](service-create-distribute-apps.md)
* [Power BI – conceitos básicos](service-basic-concepts.md)
* [Dashboards no Power BI](service-dashboards.md)
* [Dicas para projetar um ótimo dashboard](service-dashboards-design-tips.md)

Mais perguntas? [Experimente a Comunidade do Power BI](http://community.powerbi.com/)

