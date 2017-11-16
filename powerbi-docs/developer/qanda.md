---
title: P e R no Power BI Embedded
description: "O Power BI Embedded oferece uma maneira de incorporar P e R em um aplicativo e permitir que os usuários façam perguntas usando um idioma natural."
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
ms.date: 10/18/2017
ms.author: asaxton
ms.openlocfilehash: 9f592c2a85794f6c7db5de37be2ffc7b276b8f6a
ms.sourcegitcommit: 99cc3b9cb615c2957dde6ca908a51238f129cebb
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/13/2017
---
# <a name="qa-in-power-bi-embedded"></a>P e R no Power BI Embedded
O Power BI Embedded oferece uma maneira de incorporar P e R em um aplicativo e permitir que os usuários façam perguntas usando um idioma natural e recebam respostas imediatas na forma de visuais como gráficos ou grafos.

![Pergunta interativa de P e R em um quadro inserido](media/qanda/embedded-qanda.gif)

Há dois modos de inserir P e R dentro do seu aplicativo: **interativa** e **apenas resultados**. O modo **interativo** permite que você digite perguntas e as faça ser exibidas no visual. Se você tiver uma pergunta salva ou uma pergunta de conjunto que deseja exibir, será possível usar o modo **apenas resultados** preenchendo a pergunta na configuração de inserção.

Veja a aparência do código JavaScript.

```
// Embed configuration used to describe the what and how to embed.
// This object is used when calling powerbi.embed within the JavaScript API.
// You can find more information at https://github.com/Microsoft/PowerBI-JavaScript/wiki/Embed-Configuration-Details.
var config= {
    type: 'qna',
    tokenType:   models.TokenType.Embed | models.TokenType.Aad,
    accessToken: access token value,
    embedUrl:    https://app.powerbi.com/qnaEmbed (groupId to be appended as query parameter if required),
    datasetIds:  array of requested data set ids (at the moment we support only one dataset),
    viewMode:    models.QnAMode.Interactive | models.QnAMode.ResultOnly,
    question:    optional parameter for Explore mode (QnAMode.Interactive) and mandatory for Render Result mode (QnAMode.ResultOnly)
};

// Get a reference to the embedded QNA HTML element
var qnaContainer = $('#qnaContainer')[0];

// Embed the QNA and display it within the div container.
var qna = powerbi.embed(qnaContainer, config);
```

## <a name="set-question"></a>Pergunta de conjunto
Se você usou o **modo de resultados** com uma pergunta de conjunto, é possível injetar mais perguntas no quadro e receber imediatamente as respostas delas substituindo o resultado anterior. Um novo visual é renderizado, correspondendo à nova pergunta.

Um exemplo dessa utilização seria uma lista de perguntas frequentes. O usuário poderia percorrer as perguntas e receber as respostas delas dentro da mesma parte inserida.

**Trecho de código para uso do SDK do JS:**  

```        
// Get a reference to the embedded Q&A HTML element
var qnaContainer = $('#qnaContainer')[0];

// Get a reference to the embedded Q&A.
qna = powerbi.get(qnaContainer);

qna.setQuestion("This year sales")
    .then(function (result) {
        …….
    })
    .catch(function (errors) {
        …….
    });
```

## <a name="visual-rendered-event"></a>Evento renderizado pelo visual
Para o modo **interativo**, o aplicativo pode ser notificado com um evento de alteração de dados cada vez que o visual renderizado é alterado para direcionar a consulta de entrada atualizada enquanto ela é digitada.

Escutar o evento *visualRendered* permite salvar perguntas para uso posterior. 

**Trecho de código para uso do SDK do JS:**  

```
// Get a reference to the embedded Q&A HTML element
var qnaContainer = $('#qnaContainer')[0];

// Get a reference to the embedded Q&A.
qna = powerbi.get(qnaContainer);

// qna.off removes a given event listener if it exists.
qna.off("visualRendered");

// qna.on will add an event listener.
qna.on("visualRendered", function(event) {
     …….
});
```

## <a name="embed-token"></a>Token de inserção
Crie um token de inserção de um conjunto de dados para iniciar uma parte de P e R. Para obter mais informações, consulte [Generate token for Q&A](https://msdn.microsoft.com/library/mt784614.aspx#qanda) (Gerar token para P e R).

## <a name="next-steps"></a>Próximas etapas
Para experimentar a inserção de P e R, confira o [exemplo de inserção do JavaScript](https://microsoft.github.io/PowerBI-JavaScript/demo/).

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](http://community.powerbi.com/)

