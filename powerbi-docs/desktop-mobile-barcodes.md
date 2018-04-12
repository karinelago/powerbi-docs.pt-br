---
title: Marcar um campo de código de barras no Power BI Desktop para os aplicativos móveis
description: Quando você marca um campo de código de barras em seu modelo no Power BI Desktop, é possível filtrar dados em busca de códigos de barras automaticamente no aplicativo do Power BI no iPhone.
services: powerbi
documentationcenter: ''
author: maggiesMSFT
manager: kfile
editor: ''
tags: ''
qualityfocus: no
qualitydate: ''
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 01/16/2018
ms.author: maggies
LocalizationGroup: Model your data
ms.openlocfilehash: 45cca153bbc65c5bad6c0f2ba8d41fbec4682ca5
ms.sourcegitcommit: c80fbf5b12754ce217cb47a17cb5400b1036a8f2
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2018
---
# <a name="tag-barcodes-in-power-bi-desktop-for-the-mobile-apps"></a>Marcar código de barras no Power BI Desktop para os aplicativos móveis
No Power BI Desktop, você pode [categorizar dados](desktop-data-categorization.md) em uma coluna e, portanto, o Power BI Desktop sabe como tratar valores em visuais de um relatório. Você também pode categorizar uma coluna como **Código de barras**. Quando você ou seus colegas [digitalizam um código de barras em um produto com o aplicativo do Power BI](mobile-apps-scan-barcode-iphone.md) no iPhone, você vê qualquer relatório que inclua esse código de barras. Ao abrir o relatório no aplicativo móvel, o Power BI filtra automaticamente o relatório para exibir os dados relacionados a esse código de barras.

1. No Power BI Desktop, mude para a Exibição de Dados.
2. Selecione uma coluna com dados de código de barras. Veja a lista de [formatos de código de barras com suporte](#supported-barcode-formats) abaixo.
3. Na guia **Modelagem**, Selecione **Categoria de Dados** > **Código de Barras**.
   
    ![Lista de categorias de dados](media/desktop-mobile-barcodes/power-bi-desktop-barcode.png)
4. Na exibição de Relatório, adicione esse campo aos visuais que serão filtrados pelo código de barras.
5. Salve o relatório e publique-o no serviço do Power BI.

Agora quando você abrir o scanner no [aplicativo do Power BI para iPhone](mobile-ios-ipad-iphone-apps.md) e digitalizar um código de barras, verá esse relatório na lista de relatórios. Ao abrir o relatório, seus visuais são filtrados pelo código de barras do produto digitalizado.

## <a name="supported-barcode-formats"></a>Formatos de código de barras com suporte
Estes serão os códigos de barras reconhecidos pelo Power BI se você conseguir marcá-los em um relatório do Power BI: 

* UPCECode 
* Code39Code  
* A39Mod43Code 
* EAN13Code 
* EAN8Code  
* 93Code  
* 128Code 
* PDF417Code 
* Interleaved2of5Code 
* ITF14Code 

## <a name="next-steps"></a>Próximas etapas
* [Digitalizar um código de barras do aplicativo Power BI em seu iPhone](mobile-apps-scan-barcode-iphone.md)
* [Problemas com a digitalização de código de barras em um iPhone](mobile-apps-scan-barcode-iphone.md#issues-with-scanning-a-barcode)
* [Categorização de dados no Power BI Desktop](desktop-data-categorization.md)  
* Dúvidas? [Experimente perguntar à Comunidade do Power BI](http://community.powerbi.com/)

