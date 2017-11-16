---
title: Reduza o tamanho de uma pasta de trabalho do Excel para exibi-lo no Power BI
description: Reduza o tamanho de uma pasta de trabalho do Excel para exibi-lo no Power BI
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
ms.date: 09/06/2017
ms.author: davidi
ms.openlocfilehash: 2d6d55b8b93ce23528490a3e72616806ebc09beb
ms.sourcegitcommit: 99cc3b9cb615c2957dde6ca908a51238f129cebb
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/13/2017
---
# <a name="reduce-the-size-of-an-excel-workbook-to-view-it-in-power-bi"></a>Reduza o tamanho de uma pasta de trabalho do Excel para exibi-lo no Power BI
Você pode carregar qualquer pasta de trabalho do Excel menor do que 1 GB no Power BI. Uma pasta de trabalho do Excel pode ter duas partes: um modelo de dados e o restante do relatório — conteúdo da planilha principal. Se o relatório atender os seguintes limites de tamanho, você pode salvá-lo no **OneDrive for Business**, conecte-o do Power BI e exiba-o no Excel Online:

* A pasta de trabalho como um todo pode ter até 1 GB.
* O conteúdo da planilha principal pode ser de até 10 MB.

## <a name="what-makes-core-worksheet-contents-larger-than-10-mb"></a>O que torna o conteúdo da planilha de núcleo maior do que 10 MB
Aqui estão alguns elementos que podem tornar os núcleo de conteúdos da planilha maior que 10 MB:

* Imagens.
* Células sombreadas. [Remova um formato de sombreamento de célula](https://support.office.com/article/Add-or-change-the-background-color-of-cells-ac10f131-b847-428f-b656-d65375fb815e).
* Planilhas coloridas. [Remova uma tela de fundo de folha](https://support.office.com/en-US/article/add-or-remove-a-sheet-background-3577a762-8450-4556-96a2-cc265abc00a8).
* Caixas de texto.
* Clip-art.

Considere remover esses elementos, se possível. 

Se o relatório tiver um modelo de dados, você terá algumas outras opções: 

* Remover dados de planilhas do Excel e armazená-lo no modelo de dados. Consulte "Remover dados de planilhas" abaixo para obter detalhes. 
* [Crie um Modelo de Dados com eficiência de memória](https://support.office.com/article/Create-a-memory-efficient-Data-Model-using-Excel-2013-and-the-Power-Pivot-add-in-951c73a9-21c4-46ab-9f5e-14a2833b6a70) para reduzir o tamanho geral do relatório.

Para fazer essas alterações, você precisa editar a pasta de trabalho no Excel.

Leia mais sobre [limites de tamanho do arquivo para pastas de trabalho do Excel no SharePoint Online](https://support.office.com/article/File-size-limits-for-workbooks-in-SharePoint-Online-9e5bc6f8-018f-415a-b890-5452687b325e).

## <a name="remove-data-from-worksheets"></a>Remover dados das planilhas
Se você importar dados para o Excel da guia Power Query ou os dados do Excel, a pasta de trabalho pode ter os mesmos dados em uma tabela do Excel e no modelo de dados. As tabelas grandes nas planilhas do Excel podem tornar o conteúdo da planilha de núcleo maior do que 10 MB. Remover a tabela no Excel e manter os dados no modelo de dados podem reduzir significativamente o conteúdo da planilha principal do relatório. 

Quando você importar dados para o Excel, siga estas dicas:

* **Power Query**: limpar a caixa **Carregar na planilha** .
  
  Os dados são importados apenas no modelo de dados, sem dados em planilhas do Excel.
* **Na guia de dados do Excel**, se você marcou anteriormente a **Tabela** no assistente de importação: vá para **Conexões existentes** \> clique na conexão \> **Apenas criar conexão**. Exclua a tabela ou tabelas criadas durante a importação inicial original.
* **Guia de dados na guia do Excel**: não verificar a **tabela** na caixa **Importar dados** .

## <a name="workbook-size-optimizer"></a>Otimizador de tamanho da pasta de trabalho
Se a sua pasta de trabalho contiver um modelo de dados, você poderá executar o otimizador de tamanho da pasta de trabalho para reduzir o tamanho da pasta de trabalho. [Baixe o Otimizador de Tamanho da Pasta de Trabalho](https://www.microsoft.com/en-us/download/details.aspx?id=38793).

## <a name="related-info"></a>Informações relacionadas
[Criar um Modelo de dados eficiente em memória](https://support.office.com/article/Create-a-memory-efficient-Data-Model-using-Excel-2013-and-the-Power-Pivot-add-in-951c73a9-21c4-46ab-9f5e-14a2833b6a70)

[Usar os links do OneDrive for Business no Power BI Desktop](desktop-use-onedrive-business-links.md)

