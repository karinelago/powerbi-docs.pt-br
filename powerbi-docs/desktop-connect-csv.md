---
title: Conectar-se a arquivos CSV no Power BI Desktop
description: Conecte-se facilmente e use dados de arquivos CSV no Power BI Desktop
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
ms.openlocfilehash: b8594dabcd4d0fa9e102f1ffe20456805833c02c
ms.sourcegitcommit: 284b09d579d601e754a05fba2a4025723724f8eb
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/15/2017
---
# <a name="connect-to-csv-files-in-power-bi-desktop"></a>Conectar-se a arquivos CSV no Power BI Desktop
Conectar-se a um arquivo *CSV* (valor separado por vírgula) no Power BI Desktop é muito semelhante à conexão a uma pasta de trabalho do Excel. Ambos são fáceis, e este artigo explica como se conectar a qualquer arquivo CSV ao qual você tem acesso.

Para começar, no Power BI Desktop, selecione **Obter Dados > CSV** na faixa de opções **Página Inicial**.

![](media/desktop-connect-csv/connect-to-csv_1.png)

Selecione o arquivo CSV na caixa de diálogo **Abrir** exibida.

![](media/desktop-connect-csv/connect-to-csv_2.png)

Quando você seleciona **Abrir**, o Power BI Desktop acessa o arquivo e determina alguns atributos de arquivo, como a origem do arquivo, tipo de delimitador e quantas linhas devem ser usadas para detectar os tipo de dados no arquivo.

Esses atributos de arquivo e as opções são mostrados nas seleções suspensas na parte superior da janela da caixa de diálogo **Importação de CSV**, mostrada abaixo. Você pode alterar essas configurações detectadas manualmente, escolhendo outra opção em qualquer um dos seletores suspensos.

![](media/desktop-connect-csv/connect-to-csv_3.png)

Quando estiver satisfeito com as seleções, selecione **Carregar** para importar o arquivo no Power BI Desktop ou **Editar** para abrir o **Editor de Consultas** e formatar ou transformar ainda mais os dados antes de importá-los.

Depois de carregar os dados no Power BI Desktop, você vê a tabela e suas colunas (que são apresentadas como Campos no Power BI Desktop) no painel **Campos** à direita da exibição de Relatório no Power BI Desktop.

![](media/desktop-connect-csv/connect-to-csv_4.png)

Isso é tudo o que você precisa fazer – os dados de seu arquivo CSV agora estão no Power BI Desktop.

Você pode usar esses dados no Power BI Desktop para criar visuais, relatórios, ou para interagir com quaisquer outros dados aos quais você queira se conectar e importar, por exemplo, pastas de trabalho do Excel, bancos de dados ou qualquer outra fonte de dados.

### <a name="next-steps"></a>Próximas etapas
Há todos os tipos de dados aos quais você pode se conectar usando o Power BI Desktop. Para obter mais informações sobre fontes de dados, confira os seguintes recursos:

* [Introdução ao Power BI Desktop](desktop-getting-started.md)
* [Fontes de dados no Power BI Desktop](desktop-data-sources.md)
* [Formatar e combinar dados com o Power BI Desktop](desktop-shape-and-combine-data.md)
* [Conectar-se a pastas de trabalho do Excel no Power BI Desktop](desktop-connect-excel.md)   
* [Inserir dados diretamente no Power BI Desktop](desktop-enter-data-directly-into-desktop.md)   

