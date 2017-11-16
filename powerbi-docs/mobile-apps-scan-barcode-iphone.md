---
title: "Digitalizar um código de barras com um iPhone no aplicativo móvel do Power BI"
description: "A digitalização de códigos de barras no mundo real o leva para as informações de BI filtradas no aplicativo móvel do Power BI."
services: powerbi
documentationcenter: 
author: maggiesMSFT
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
ms.date: 10/13/2017
ms.author: maggies
ms.openlocfilehash: 7ae11cf40620b4170823ca518a9c7c37c8c4dd61
ms.sourcegitcommit: 99cc3b9cb615c2957dde6ca908a51238f129cebb
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/13/2017
---
# <a name="scan-a-barcode-with-your-iphone-from-the-power-bi-mobile-app"></a>Digitalizar um código de barras com seu iPhone no aplicativo móvel do Power BI
A digitalização de códigos de barras no mundo real o leva para as informações de BI filtradas no aplicativo móvel do Power BI.

![](media/mobile-apps-scan-barcode-iphone/power-bi-barcode-scanner.png)

Digamos que um colega tenha [marcado um campo de código de barras em um relatório do Power BI Desktop](desktop-mobile-barcodes.md) e compartilhou esse relatório com você. 

Quando você digitaliza o código de barras de um produto com o scanner no aplicativo do Power BI no iPhone, você vê o relatório (ou a lista de relatórios) com esse código de barras. Você pode abrir o relatório no iPhone, filtrado nesse código de barras.

## <a name="scan-a-barcode-with-the-power-bi-scanner"></a>Digitalizar um código de barras com o scanner do Power BI
1. No aplicativo móvel do Power BI, abra o menu de navegação principal ![](media/mobile-apps-scan-barcode-iphone/pbi_iph_navmenu.png) na parte superior esquerda. 
2. Role para baixo até **Scanner** e selecione-o. 
   
    ![](media/mobile-apps-scan-barcode-iphone/power-bi-scanner.png)
3. Se a câmera não estiver habilitada, você precisa aprovar o aplicativo do Power BI para usar a câmera. Essa é uma única aprovação. 
4. Aponte o scanner para um código de barras em um produto. 
   
    Você verá uma lista dos relatórios associados a esse código de barras.
5. Toque no nome do relatório para abri-lo no iPhone, filtrado automaticamente nesse código de barras.

## <a name="filter-by-other-barcodes-while-in-a-report"></a>Filtrar por outros códigos de barras enquanto estiver em um relatório
Ao observar um relatório filtrado por um código de barras no iPhone, é recomendável filtrar o mesmo relatório por um código de barras diferente.

* Se o ícone de código de barras tiver um filtro ![](media/mobile-apps-scan-barcode-iphone/power-bi-barcode-filtered-icon-black.png), o filtro estará ativo e o relatório já será filtrado por um código de barras. 
* Se o ícone não contiver um filtro ![](media/mobile-apps-scan-barcode-iphone/power-bi-barcode-unfiltered-icon.png), o filtro não estará ativo e o relatório não será filtrado por um código de barras. 

De qualquer forma, toque no ícone para abrir um pequeno menu com um scanner flutuante.

* Focalize o scanner no novo item para alterar o filtro do relatório para um valor de código de barras diferente. 
* Selecione **Limpar filtro de código de barras** para voltar ao relatório não filtrado.
* Selecione **Filtrar por códigos de barras recentes** para mudar o filtro de relatório para um dos códigos de barras digitalizados na sessão atual.

## <a name="issues-with-scanning-a-barcode"></a>Problemas com a digitalização de um código de barras
Aqui estão algumas mensagens que você poderá ver quando digitalizar um código de barras em um produto.

### <a name="couldnt-filter-report"></a>“Não foi possível filtrar o relatório...”
O relatório que você escolher filtrar baseia-se em um modelo de dados que não inclui esse valor de código de barras. Por exemplo, o produto “água mineral” não está incluído no relatório.  

### <a name="allsome-of-the-visuals-in-the-report-dont-contain-any-value"></a>Todos/alguns dos visuais no relatório não contém nenhum valor
O valor de código de barras digitalizado já existe em seu modelo, mas todos ou alguns dos visuais no relatório não contêm esse valor e, portanto, a filtragem retornará um estado vazio. Tente procurar em outras páginas do relatório ou editar seus relatórios no Power BI Desktop para que ele contenha esse valor 

### <a name="looks-like-you-dont-have-any-reports-that-can-be-filtered-by-barcodes"></a>“Parece que você não tem relatórios que possam ser filtrados por códigos de barras”.
Isso significa que você não tem nenhum relatório habilitado para código de barras. O scanner de código de barras pode filtrar apenas relatórios que têm uma coluna marcada como **Código de barras**.  

Verifique se você ou o proprietário do relatório marcou uma coluna como **Código de barras** no Power BI Desktop. Saiba mais sobre como [marcar um campo de código de barras no Power BI Desktop](desktop-mobile-barcodes.md)

### <a name="couldnt-filter-report---looks-like-this-barcode-doesnt-exist-in-the-report-data"></a>“Não foi possível filtrar o relatório – parece que esse código de barras não existe nos dados do relatório.”
O relatório que você escolher filtrar baseia-se em um modelo de dados que não inclui esse valor de código de barras. Por exemplo, o produto “água mineral” não está incluído no relatório. Você poderá digitalizar um produto diferente, escolher outro relatório (se houver mais de um relatório disponível) ou exibir o relatório não filtrado. 

## <a name="next-steps"></a>Próximas etapas
* [Marcar um campo de código de barras no Power BI Desktop](desktop-mobile-barcodes.md)
* [Blocos de Dashboard no Power BI](service-dashboard-tiles.md)
* [Dashboards no Power BI](service-dashboards.md)

