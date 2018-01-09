---
title: "Layouts personalizados com conteúdo inserido do Power BI"
description: "Saiba mais sobre layouts personalizados ao inserir conteúdo do Power BI em seu aplicativo."
services: powerbi
documentationcenter: 
author: guyinacube
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
ms.date: 12/19/2017
ms.author: asaxton
ms.openlocfilehash: d4e9911dee525a5bf7b6ac8d024c41de24d2c9ba
ms.sourcegitcommit: a658b1c936e382f46a19eeb9cc26016cd7b1d756
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/20/2017
---
# <a name="custom-layouts"></a>Layouts personalizados


Use layouts personalizados para inserir um relatório com layout diferente daquele usado em um relatório original. A definição de um novo layout varia entre definir apenas um tamanho de página, controlando tamanhos visuais ou posição e visibilidade.

Para definir um layout personalizado, defina um objeto de layout personalizado e passe-o pelo objeto configurações na configuração de inserção. Além disso, defina LayoutType como Personalizado. Para saber mais, consulte [Detalhes da configuração de inserção](https://github.com/Microsoft/PowerBI-JavaScript/wiki/Embed-Configuration-Details).

```javascript
var embedConfig = {
    ...
    settings: {
            layoutType: models.LayoutType.Custom
    customLayout: {...}
    }
};
```

## <a name="object-definition"></a>Definição do objeto

```javascript
interface ICustomLayout {
  pageSize?: IPageSize;
  displayOption?: DisplayOption;
  pagesLayout?: PagesLayout;
}

enum PageSizeType {
  Widescreen,
  Standard,
  Cortana,
  Letter,
  Custom
}
interface IPageSize {
  type: PageSizeType;
}
interface ICustomPageSize extends IPageSize {
  width?: number;
  height?: number;
}

enum DisplayOption {
  FitToPage,
  FitToWidth,
  ActualSize
}
```

- `pageSize`: use o tamanho de página para controlar o tamanho da área da tela (ou seja, a área do relatório em branco).
- `displayOptions`: possíveis valores são: FitToWidth, FitToPage ou ActualSize. Controla como dimensionar a tela para se ajustar ao iframe.
- `pagesLayout`: controla o layout para cada visual. Consulte PagesLayout para obter mais detalhes.

## <a name="pages-layout"></a>Layout de páginas

Definir um objeto de layout de páginas é basicamente definir um layout de cada página e, para cada página, você define um layout para cada visual.
PageLayout é opcional. Se você não definir um layout de uma página, o layout padrão (que é salvo no relatório) será aplicado.

pagesLayout é um mapa do nome de página ao objeto PageLayout. Definição:

```javascript
type PagesLayout = { [key: string]: IPageLayout; };
```

PageLayout contém um mapa de layout visual, que mapeia o nome de cada visual para um objeto de layout visual:

```javascript
interface IPageLayout {
  visualsLayout: { [key: string]: IVisualLayout; };
}
```

## <a name="visual-layout"></a>Layout visual

Para definir um layout visual, passe uma nova posição e tamanho e um novo estado de visibilidade.

```javascript
interface IVisualLayout {
  x?: number;
  y?: number;
  z?: number;
  width?: number;
  height?: number;
  displayState?: IVisualContainerDisplayState;
}

interface IVisualContainerDisplayState {
  mode: VisualContainerDisplayMode;
}

enum VisualContainerDisplayMode {
  Visible,
  Hidden
}
```

- `x,y,z`: define a nova posição do visual.
- `width`, altura: define o novo tamanho do visual.
- `displayState`: define a visibilidade do visual.


## <a name="update-layout"></a>Atualizar layout

Você pode usar o método updateSettings para atualizar o layout do relatório em qualquer momento enquanto o relatório é carregado. Consulte [Atualizar Configurações](https://github.com/Microsoft/PowerBI-JavaScript/wiki/Update-Settings).

## <a name="code-example"></a>Exemplo de código

```javascript
// Get models. models contains enums that can be used.
var models = window['powerbi-client'].models;
    
var embedConfiguration = {
    type: 'report',
    id: '5dac7a4a-4452-46b3-99f6-a25915e0fe55',
    embedUrl: 'https://app.powerbi.com/reportEmbed',
    tokenType: models.TokenType.Embed,
    accessToken: 'H4...rf',
    settings: {
            layoutType: models.LayoutType.Custom
        customLayout: {
            pageSize: {
                type: models.PageSizeType.Custom,
                width: 1600,
                height: 1200
            },
            displayOption: models.DisplayOption.ActualSize,
            pagesLayout: {
                "ReportSection1" : {
                    visualsLayout: {
                        "VisualContainer1": {
                            x: 1,
                            y: 1,
                            z: 1,
                            width: 400,
                            height: 300,
                            displayState: {
                                mode: models.VisualContainerDisplayMode.Visible
                            }
                        },
                        "VisualContainer2": {
                            displayState: {
                                mode: models.VisualContainerDisplayMode.Hidden
                            }
                        },
                    }
                }
            }
        }
    }
};
     
// Get a reference to the embedded report HTML element
var embedContainer = document.getElementById('embedContainer');
 
// Embed the report and display it within the div container.
var report = powerbi.embed(embedContainer, embedConfiguration);

```


## <a name="see-also"></a>Consulte também

[Inserir painéis, relatórios e blocos do Power BI](embedding-content.md)   
[Perguntar à Comunidade do Power BI](https://community.powerbi.com/)

