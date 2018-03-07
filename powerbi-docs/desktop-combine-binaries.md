---
title: "Combinar binários no Power BI Desktop"
description: "Combinar fontes de dados binários com facilidade no Power BI Desktop"
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
LocalizationGroup: Transform and shape data
ms.openlocfilehash: 395562dfecba4657ffa906494f81532febb6a11f
ms.sourcegitcommit: 88c8ba8dee4384ea7bff5cedcad67fce784d92b0
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/24/2018
---
# <a name="combine-binaries-in-power-bi-desktop"></a>Combinar binários no Power BI Desktop
Uma abordagem eficiente para a importação de dados no **Power BI Desktop** é combinar vários arquivos, que têm o mesmo esquema, em uma única tabela lógica. Com a versão de novembro de 2016 do **Power BI Desktop** (e versões posteriores), essa abordagem conveniente e popular se tornou mais conveniente e mais expansiva, como descrito neste artigo.

Para iniciar o processo de combinação de binários da mesma pasta, selecione **Obter Dados > Arquivo > Pasta**.

![](media/desktop-combine-binaries/combine-binaries_1.png)

## <a name="previous-combine-binaries-behavior"></a>Comportamento anterior da operação Combinar binários
Antes da versão de novembro de 2016 do **Power BI Desktop**, era possível combinar alguns tipos de arquivo com a transformação **Combinar binários**, mas havia limitações:

* As transformações não eram consideradas para cada arquivo individual antes dos arquivos serem combinados em uma única tabela. Assim, geralmente, era necessário combinar arquivos e filtrar os *valores de cabeçalho* filtrando as linhas como parte do processo de edição.
* A transformação **Combinar binários** funcionava apenas para arquivos de *texto* ou *CSV* e não funcionava em outros formatos de arquivo com suporte, como pastas de trabalho do Excel, arquivos JSON e outros.

Os clientes solicitaram uma operação **Combinar binários** mais intuitiva e, portanto, a transformação foi aprimorada.

## <a name="current-combine-binaries-behavior"></a>Comportamento atual da operação Combinar binários
O **Power BI Desktop** agora manipula a operação **Combinar binários** com mais eficiência. Comece selecionando **Combinar binários** na guia de faixa de opções **Página Inicial** no **Editor de Consultas** ou na própria coluna.

![](media/desktop-combine-binaries/combine-binaries_2a.png)

A transformação **Combinar binários** agora se comporta da seguinte maneira:

* A transformação **Combinar binários** analisa cada arquivo de entrada e determina o formato de arquivo correto a ser usado, como *texto*, *pasta de trabalho do Excel* ou arquivo *JSON*.
* A transformação permite selecionar um objeto específico do primeiro arquivo, por exemplo, uma *pasta de trabalho do Excel*, para ser extraído.
  
  ![](media/desktop-combine-binaries/combine-binaries_3.png)
* Em seguida, a operação **Combinar binários** faz o seguinte automaticamente:
  
  * Cria uma consulta de exemplo que executa todas as etapas de extração necessárias em um único arquivo.
  * Cria uma *consulta de função* que parametriza a entrada de arquivo/binário para a *consulta de exemplo*. A consulta de exemplo e a consulta de função são vinculadas, para que as alterações à consulta de exemplo sejam refletidas na consulta de função.
  * Aplica a *consulta de função* à consulta original com binários de entrada (por exemplo, a consulta *Pasta*) para que ela aplique a consulta de função para entradas de binário em cada linha e expanda a extração de dados resultante como colunas de nível superior.
    
    ![](media/desktop-combine-binaries/combine-binaries_4.png)

Com o novo comportamento da operação **Combinar binários**, combine todos os binários de determinada pasta com facilidade, desde que eles tenham o mesmo tipo de arquivo e estrutura (por exemplo, as mesmas colunas).

Além disso, aplique etapas de transformação ou extração adicionais de forma fácil modificando a *consulta de exemplo* criada automaticamente, sem precisar se preocupar em modificar ou criar outras etapas da *consulta de função*; as alterações à *consulta de exemplo* são geradas automaticamente na *consulta de função* vinculada.

## <a name="next-steps"></a>Próximas etapas
Há todos os tipos de dados aos quais você pode se conectar usando o Power BI Desktop. Para obter mais informações sobre fontes de dados, confira os seguintes recursos:

* [Introdução ao Power BI Desktop](desktop-getting-started.md)
* [Fontes de dados no Power BI Desktop](desktop-data-sources.md)
* [Formatar e combinar dados com o Power BI Desktop](desktop-shape-and-combine-data.md)
* [Conectar-se a arquivos CSV no Power BI Desktop](desktop-connect-csv.md)   
* [Inserir dados diretamente no Power BI Desktop](desktop-enter-data-directly-into-desktop.md)   

