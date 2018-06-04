---
title: Aplicativo Power BI para Realidade Misturada (versão prévia)
description: Veja seus dashboards e relatórios no aplicativo Power BI para Realidade Misturada, estejam eles imersos no mundo virtual ou no seu ambiente.
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-mobile
ms.topic: conceptual
ms.date: 03/13/2018
ms.author: maggies
ms.openlocfilehash: 32ef06cfdefe4ff1554cfe5f449d69583569f158
ms.sourcegitcommit: 80d6b45eb84243e801b60b9038b9bff77c30d5c8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34721422"
---
# <a name="power-bi-for-mixed-reality-app-preview"></a>Aplicativo Power BI para Realidade Misturada (versão prévia)
Veja seus dashboards e relatórios no aplicativo Power BI para Realidade Misturada enquanto imersos no mundo virtual, ou coloque-os em locais específicos no seu ambiente. 

Baixe a edição de versão prévia do aplicativo Power BI para Realidade Misturada da Windows Store para ver seus dashboards e relatórios. Interaja com eles no mundo virtual e selecione aqueles que você deseja colocar. 

## <a name="two-views-windows-classic-and-holographic"></a>Dois modos de exibição: holográfico e clássico do Windows

O Power BI para Realidade Misturada baseia-se no aplicativo móvel do Windows Power BI com funcionalidades adicionais exclusivas para realidade misturada. Quando você inicia o Power BI para Realidade Misturada, você está neste modo de exibição "clássico" do Windows do Power BI. Nesse modo de exibição, você pode navegar entre os dashboards e relatórios aos quais você tem acesso. Quando você encontrar o item desejado, você poderá mudar do modo de exibição clássico do Windows para a experiência holográfica. 


## <a name="windows-classic-view-basics"></a>Noções básicas do modo de exibição clássico do Windows

Se você não está familiarizado com a experiência de realidade misturada, esta seção é para você. Interagir com um aplicativo de realidade misturada é diferente de interagir com um computador ou até mesmo com um tablet ou telefone. Na exibição clássica do Windows, aplicativos realidade misturada respondem a um conjunto de gestos e comandos de voz que substituem o tradicional mouse e teclado ou o toque de telefone. 

**Fechar e abrir dedos indicador e polegar**

Fechar e abrir dedos indicador e polegar é o gesto mais básico que você precisa saber para interagir com quase todos os aplicativos de realidade misturada. Você toca o polegar e o dedo indicador juntos com sua mão mantida em pé, semelhante a um clique de mouse ou um toque no telefone.  

![Gesto de fechar e abrir dedos indicador e polegar de realidade misturada](media/mobile-mixed-reality-app/power-bi-hololens-airtap.png)

No Power BI, você usa um gesto fechar e abrir dedos indicador e polegar no aplicativo clássico do Windows em qualquer lugar em que você usaria um clique do mouse. Você pode fechar e abrir dedos indicador e polegar para abrir um dashboard ou relatório no espaço de trabalho, ou então fazer esse mesmo gesto em parte de um visual para filtrar ou realizar o realce cruzado de outros visuais e assim por diante.

![Fechar e abrir dedos indicador e polegar no Power BI](media/mobile-mixed-reality-app/power-bi-hololens-airtap-hand.png) 

Leia mais sobre [gestos de mão da Microsoft na realidade misturada](https://developer.microsoft.com/windows/mixed-reality/gestures).

**Fixar um item** 

Feche e abra os dedos indicador e polegar no ícone **Fixar** ![Ícone fixar](media/mobile-mixed-reality-app/power-bi-hololens-pin.png) para fixar um dashboard ou relatório do modo de exibição clássico do Windows para o modo de exibição holográfico. Você pode fixar um número de itens no modo de exibição holográfico. 

**Mudar para o modo de exibição holográfico**

Depois de você fixar itens no modo de exibição clássico do Windows, você fecha e abre os dedos indicador e polegar no ícone **Tela Inteira** ![Ícone de tela inteira](media/mobile-mixed-reality-app/power-bi-hololens-fullscreen.png) para mudar para o modo de exibição holográfico. 


## <a name="holographic-view-basics"></a>Noções básicas do modo de exibição holográfico

Agora que você está no modo de exibição holográfico, todos os artefatos que você fixou estão em seu cinto de encaixe. Você pode colocar esses itens fixados em locais específicos no espaço físico — por exemplo, ao lado do equipamento descrito pelo item. No modo de exibição holográfico, os comandos de voz complementam os gestos de mão. Aqui estão alguns comandos de voz comuns.

**"Siga-me"** 

Pegue um artefato do Power BI fazendo com que ele fique em seu campo de visão principal e siga seu foco até que você o coloque em algum lugar.

**"Encaixe"** 

Use o comando "encaixe" para colocar um artefato em seu cinto de encaixe do Power BI, de modo que ele seguirá você, fora de seu campo de visão principal, para um acesso fácil.

**"Colocar aqui"**

Esse comando coloca um dashboard ou relatório em uma parede ou um objeto, ou então flutuando no espaço.

![Colocando um dashboard no espaço](media/mobile-mixed-reality-app/power-bi-hololens-place-visuals.png)

**"Ir para página inicial"**

Diga "ir para página inicial" para retornar à exibição clássica do Windows do Power BI. 

**"Remover"**

Use este comando para remover um artefato do modo de exibição holográfico.

**"Remover tudo"** 

Use este comando para remover todos os artefatos do modo de exibição holográfico.


## <a name="scan-a-report-qr-code-in-holographic-view"></a>Digitalizar um código QR de relatório no modo de exibição holográfico

Você pode examinar o código QR para um relatório no modo de exibição holográfico, assim como você pode [digitalizar códigos QR com os aplicativos móveis do Power BI](mobile-apps-qr-code.md) para iPhone e Android.

- Enquanto estiver no modo de exibição holográfico, mantenha o foco em um código QR. O Power BI abre o relatório associado a esse código QR.

## <a name="limitations-and-considerations"></a>Limitações e considerações

Há algumas limitações e considerações para o modo de exibição holográfico.

- Você não vê o realce ou filtragem cruzada que você pode ter definido no modo de exibição clássico do Windows.
- O modo de exibição de seus relatórios e dashboards fixados é particular. Atualmente, não damos suporte a experiências compartilhadas.
- Os dashboards e relatórios são atualizados a cada 45 segundos, conforme os dados sofrem alterações.


## <a name="next-steps"></a>Próximas etapas

- [Obter dados do mundo real com os aplicativos móveis do Power BI](mobile-apps-data-in-real-world-context.md)

 



