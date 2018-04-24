---
title: Mapas preenchidos (coropléticos) no Power BI (tutorial)
description: Documentação – tutorial sobre como criar Mapas Coropléticos no Power BI
services: powerbi
documentationcenter: ''
author: mihart
manager: kfile
backup: ''
editor: ''
tags: ''
featuredvideoid: ''
qualityfocus: no
qualitydate: ''
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 04/11/2018
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: a6cddcf361072bdd265a94de9efd5dbc7ecf05c8
ms.sourcegitcommit: df94efc51f261113fa90ebdf3fe68dd149cc4936
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2018
---
# <a name="filled-maps-choropleths-in-power-bi-tutorial"></a>Mapas preenchidos (coropléticos) no Power BI (tutorial)
Um mapa coroplético usa sombreamento ou tonalidade ou padrões para exibir como um valor difere na proporção em uma localização geográfica ou região.  Exiba rapidamente essas diferenças relativas com sombreamento que varia de claro (menos frequente/inferior) para escuro (mais frequente/mais).    

![](media/power-bi-visualization-filled-maps-choropleths/large_map.png)

## <a name="what-is-sent-to-bing"></a>O que é enviado ao Bing
O Power BI é integrado ao Bing para fornecer as coordenadas de mapa padrão (um processo chamado geocódigo). Quando você cria uma visualização de mapa no serviço do Power BI ou no Power BI Desktop, os dados nos buckets **Local**, **Latitude** e **Longitude** (que estão sendo usados para criar essa visualização) são enviados ao Bing.

Você ou seu administrador talvez precise atualizar o firewall para permitir o acesso às URLs usadas pelo Bing para geocodificação.  Essas URLs são:
* https://dev.virtualearth.net/REST/V1/Locations
* https://platform.bing.com/geo/spatial/v1/public/Geodata
* https://www.bing.com/api/maps/mapcontrol

Para obter mais informações sobre os dados enviados ao Bing e ver dicas sobre como aumentar seu sucesso com o geocódigo, consulte [Dicas e truques para visualizações de mapa](power-bi-map-tips-and-tricks.md).

## <a name="when-to-use-a-filled-map"></a>Quando usar um mapa coroplético
Mapas coropléticos são uma ótima opção:

* para exibir informações quantitativas em um mapa.
* para mostrar as relações e os padrões espaciais.
* quando seus dados são padronizados.
* ao trabalhar com dados socioeconômicos.
* quando regiões definidas são importantes.
* para obter uma visão geral da distribuição entre os locais geográficos.

### <a name="prerequisites"></a>Pré-requisitos
- Serviço do Power BI ou Power BI Desktop
- Exemplo de Vendas e Marketing

Para acompanhar, o tutorial usa o serviço Power BI, não o Power BI Desktop.

## <a name="create-a-basic-filled-map"></a>Criar um mapa coroplético básico
Neste vídeo, Kim cria um mapa básico e o converte em um mapa coroplético.

<iframe width="560" height="315" src="https://www.youtube.com/embed/ajTPGNpthcg" frameborder="0" allowfullscreen></iframe>


1. Para criar seu próprio mapa coroplético, [baixe o exemplo Vendas e Marketing](sample-datasets.md) conectando-se ao Power BI e selecionando **Obter Dados \> Exemplos \> Vendas e Marketing \> Conectar**.
2. Quando a mensagem de êxito for exibida, selecione **Exibir conjunto de dados**.

   ![](media/power-bi-visualization-filled-maps-choropleths/power-bi-view-dataset.png)
3. O Power BI abre uma tela de relatório em branco no [Modo de Exibição de Edição](service-interact-with-a-report-in-editing-view.md).

    ![](media/power-bi-visualization-filled-maps-choropleths/power-bi-blank-canvas.png)
4. No painel Campos, selecione o campo **Área geográfica** \> **Estado**.    

   ![](media/power-bi-visualization-filled-maps-choropleths/img002.png)
5. [Converta o gráfico](power-bi-report-change-visualization-type.md) em um mapa coroplético. Observe que o **Estado** agora está no contêiner **Local**. O Bing Maps usa o campo no contêiner **Local** para criar o mapa.  O local pode ser uma variedade de locais válidos: países, estados, condados, cidades, CEPs ou outros códigos postais, etc. O Bing Maps fornece formas de mapa coroplético para locais em todo o mundo. Sem uma entrada válida no Local, o Power BI não pode criar o mapa coroplético.  

   ![](media/power-bi-visualization-filled-maps-choropleths/img003.png)
6. Filtre o mapa para exibir somente os Estados Unidos.

   a.  Na parte inferior do painel Visualizações, procure a área **Filtros** .

   b.  Passe o mouse sobre **Estado** e clique na divisa de expansão  
   ![](media/power-bi-visualization-filled-maps-choropleths/img004.png)

   c.  Coloque uma marca de seleção ao lado de **Todos** e remova a marca de seleção ao lado de **AK**.

   ![](media/power-bi-visualization-filled-maps-choropleths/img005.png)
7. Selecione **SalesFact** \> **Sentimento** para adicioná-la à seção **Saturação de cores** também. O campo na **Saturação de cores** controla bem o sombreamento do mapa.  
   ![](media/power-bi-visualization-filled-maps-choropleths/power-bi-color-saturation.png)
8. O mapa coroplético é sombreado em verde, com verde claro representando os números de sentimento inferiores e verde escuro representando o sentimento maior, mais positivo.  Aqui, destacamos o estado do Wyoming (WY) e vemos que o Sentimento é muito bom, 74.  
   ![](media/power-bi-visualization-filled-maps-choropleths/img007.png)
9. [Salve o relatório](service-report-save.md).

## <a name="highlighting-and-cross-filtering"></a>Realce e filtragem cruzada
Para obter informações sobre como usar o painel Filtros, veja [Adicionar um filtro a um relatório](power-bi-report-add-filter.md).

Realçar um local em um mapa coroplético faz a filtragem cruzada com outras visualizações na página do relatório e vice-versa.

Para acompanhar, copie e cole o Mapa coroplético na página **Sentimento** do relatório *Vendas e Marketing*.

1. No mapa coroplético, selecione um estado.  Isso destaca as outras visualizações na página. A seleção de **Texas**, por exemplo, mostra que o Sentimento é de 74, que Texas está no Distrito Central \#23 e que a maior parte do volume de vendas é proveniente dos segmentos Moderação e Conveniência.   
   ![](media/power-bi-visualization-filled-maps-choropleths/img008.png)
2. No gráfico de linhas, alterne entre **Não** e **Sim**. Isso filtra o Mapa Coroplético para mostrar o Sentimento para VanArsdel para a concorrência de VanArsdel.  
   ![](media/power-bi-visualization-filled-maps-choropleths/img009.gif)

## <a name="considerations-and-troubleshooting"></a>Considerações e solução de problemas
Dados de mapa podem ser ambíguos.  Por exemplo, há uma Paris, França, mas também há uma Paris, no Texas. Seus dados geográficos provavelmente são armazenados em colunas separadas – uma coluna de nomes de cidades, uma coluna de nomes de estado ou província, etc. – portanto, o Bing pode não ser capaz de dizer qual Paris é. Se o seu conjunto de dados já contém dados de latitude e longitude, o Power BI tem campos especiais para ajudar a tornar os dados do mapa inequívocos. Basta arrastar o campo que contém os dados de latitude na área Visualizações \> Latitude.  E faça o mesmo para os dados de longitude.  
![](media/power-bi-visualization-filled-maps-choropleths/pbi_latitude.png)

Se você tiver permissões para editar o conjunto de dados no Power BI Desktop, assista a este vídeo para obter ajuda e resolver a ambiguidade de mapa.

<iframe width="560" height="315" src="https://www.youtube.com/embed/Co2z9b-s_yM" frameborder="0" allowfullscreen></iframe>

Se você não tiver acesso a dados de latitude e longitude, [siga estas instruções para atualizar o conjunto de dados](https://support.office.com/article/Maps-in-Power-View-8A9B2AF3-A055-4131-A327-85CC835271F7).

Para obter mais ajuda com Visualizações de mapa, veja [Tips and tricks for map visualizations](power-bi-map-tips-and-tricks.md) (Dicas e truques para visualizações de mapa).

## <a name="next-steps"></a>Próximas etapas
[Adicionar o mapa coroplético como um bloco do dashboard (fixar o visual)](service-dashboard-tiles.md)    
 [Adicionar uma visualização a um relatório](power-bi-report-add-visualizations-i.md)  
 [Tipos de visualização no Power BI](power-bi-visualization-types-for-reports-and-q-and-a.md)    
 [Alterar o tipo de visualização que está sendo usado](power-bi-report-change-visualization-type.md)      
Mais perguntas? [Experimente a Comunidade do Power BI](http://community.powerbi.com/)
