---
title: Combinar arquivos (binários) no Power BI Desktop
description: Combinar facilmente fontes de dados de arquivos (binários) no Power BI Desktop
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 04/24/2018
ms.author: davidi
LocalizationGroup: Transform and shape data
ms.openlocfilehash: 7a0a4f6296df351272a69ca30c8a8c08e1f9bcbc
ms.sourcegitcommit: 638de55f996d177063561b36d95c8c71ea7af3ed
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/17/2018
---
# <a name="combine-files-binaries-in-power-bi-desktop"></a>Combinar arquivos (binários) no Power BI Desktop
Uma abordagem eficiente para a importação de dados no **Power BI Desktop** é combinar vários arquivos, que têm o mesmo esquema, em uma única tabela lógica. Com a versão de novembro de 2016 do **Power BI Desktop** (e versões posteriores), essa abordagem conveniente e popular se tornou mais conveniente e mais expansiva, como descrito neste artigo.

Para iniciar o processo de combinação de arquivos da mesma pasta, selecione **Obter Dados > Arquivo > Pasta**.

![](media/desktop-combine-binaries/combine-binaries_1.png)

## <a name="previous-combine-files-binaries-behavior"></a>Comportamento anterior de combinar arquivos (binários)
Antes da versão de novembro de 2016 do **Power BI Desktop**, essa funcionalidade era chamada de **Combinar binários**, e era possível combinar certos tipos de arquivo com a transformação **combinar binários**, mas havia limitações:

* As transformações não eram consideradas para cada arquivo individual antes dos arquivos serem combinados em uma única tabela. Assim, geralmente, era necessário combinar arquivos e filtrar os *valores de cabeçalho* filtrando as linhas como parte do processo de edição.
* A transformação **Combinar binários** funcionava apenas para arquivos de *texto* ou *CSV* e não funcionava em outros formatos de arquivo com suporte, como pastas de trabalho do Excel, arquivos JSON e outros.

Os clientes solicitaram uma operação **combinar binários** mais intuitiva e, portanto, a transformação foi aprimorada e renomeada como **combinar arquivos**.

## <a name="current-combine-files-behavior"></a>Comportamento atual de combinar arquivos
Agora, o **Power BI Desktop** manipula a operação **combinar arquivos** com mais eficiência. Comece selecionando **combinar arquivos** na guia de faixa de opções **Página Inicial** no **Editor de Consultas** ou na própria coluna.

![](media/desktop-combine-binaries/combine-binaries_2a.png)

A transformação **combinar arquivos** agora se comporta da seguinte maneira:

* A transformação **combinar arquivos** analisa cada arquivo de entrada e determina o formato de arquivo correto a ser usado, como *texto*, *pasta de trabalho do Excel* ou arquivo *JSON*.
* A transformação permite selecionar um objeto específico do primeiro arquivo, por exemplo, uma *pasta de trabalho do Excel*, para ser extraído.
  
  ![](media/desktop-combine-binaries/combine-binaries_3.png)
* Depois, **combinar arquivos** executa automaticamente estas consultas:
  
  * Cria uma consulta de exemplo que executa todas as etapas de extração necessárias em um único arquivo.
  * Cria uma *consulta de função* que parametriza a entrada de arquivo/binário para a *consulta de exemplo*. A consulta de exemplo e a consulta de função são vinculadas, para que as alterações à consulta de exemplo sejam refletidas na consulta de função.
  * Aplica a *consulta de função* à consulta original com binários de entrada (por exemplo, a consulta *Pasta*) para que ela aplique a consulta de função para entradas de binário em cada linha e expanda a extração de dados resultante como colunas de nível superior.
    
    ![](media/desktop-combine-binaries/combine-binaries_4.png)

Com o novo comportamento da operação **combinar arquivos**, combine todos os arquivos de determinada pasta com facilidade, desde que eles tenham o mesmo tipo de arquivo e estrutura (por exemplo, as mesmas colunas).

Além disso, aplique etapas de transformação ou extração adicionais de forma fácil modificando a *consulta de exemplo* criada automaticamente, sem precisar se preocupar em modificar ou criar outras etapas da *consulta de função*. As alterações à *consulta de exemplo* são geradas automaticamente na *consulta de função* vinculada.

## <a name="next-steps"></a>Próximas etapas
Há todos os tipos de dados aos quais você pode se conectar usando o Power BI Desktop. Para obter mais informações sobre fontes de dados, confira os seguintes recursos:

* [Introdução ao Power BI Desktop](desktop-getting-started.md)
* [Fontes de dados no Power BI Desktop](desktop-data-sources.md)
* [Formatar e combinar dados com o Power BI Desktop](desktop-shape-and-combine-data.md)
* [Conectar-se a arquivos CSV no Power BI Desktop](desktop-connect-csv.md)   
* [Inserir dados diretamente no Power BI Desktop](desktop-enter-data-directly-into-desktop.md)   

