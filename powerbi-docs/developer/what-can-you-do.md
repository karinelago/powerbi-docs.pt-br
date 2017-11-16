---
title: O que os desenvolvedores podem fazer com o Power BI?
description: "O Power BI oferece uma ampla variedade de opções para desenvolvedores. Isso vai desde a inserção até elementos visuais personalizados e conjuntos de dados de streaming."
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
ms.date: 07/20/2017
ms.author: asaxton
ms.openlocfilehash: a10cd93a06d14e3e66fd9cce480dc0ec99e67aeb
ms.sourcegitcommit: 99cc3b9cb615c2957dde6ca908a51238f129cebb
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/13/2017
---
# <a name="what-can-developers-do-with-power-bi"></a>O que os desenvolvedores podem fazer com o Power BI?
O Power BI oferece uma ampla variedade de opções para desenvolvedores. Isso vai desde a inserção até elementos visuais personalizados e conjuntos de dados de streaming.

## <a name="embedding"></a>Inserção
O serviço do Power BI e Power BI Embedded no Azure estão sendo unidos para oferecer uma única API para inserir seus dashboards e relatórios. Isso significa que você terá uma superfície de API, um conjunto consistente de recursos e o acesso aos recursos mais recentes do Power BI, tais como dashboards, gateways e espaços de trabalho de aplicativo, ao inserir seu conteúdo. Para obter mais informações, consulte [Inserindo com o Power BI](embedding.md).

![](media/what-can-you-do/powerbi-embed-sample.png)

## <a name="custom-visuals"></a>Elementos visuais personalizados
Os elementos visuais personalizados permitem que você crie seus próprios elementos visuais para uso em relatórios do Power BI. Os elementos visuais personalizados são escritos em TypeScript, que é um superconjunto do JavaScript que dá suporte a alguns recursos avançados e acesso antecipado às funcionalidades do ES6/ES7. A aplicação de estilo do visual é realizada usando CSS (folhas de estilos em cascata). Para facilitar, usamos o pré-compilador LESS que dá suporte a alguns recursos avançados como aninhamento, variáveis, mesclagens, condições, loops, etc. Se não quiser usar esses recursos, escreva apenas o CSS simples no arquivo LESS.

Para obter mais informações sobre como desenvolver e publicar um elemento visual personalizado, consulte [Publicar elementos visuais personalizados na Office Store](office-store.md).

![](media/what-can-you-do/powerbi-custom-visual-store.png)

## <a name="push-data-into-power-bi"></a>Enviar dados por push ao Power BI
Você pode usar a API do Power BI para enviar dados por push a um conjunto de dados. Isso permite que você adicione uma linha a uma tabela dentro de um conjunto de dados. Assim, os novos dados podem ser mostrados em blocos em um dashboard e dentro de elementos visuais no seu relatório.

Para obter mais informações, consulte [Enviar dados por push a um dashboard](walkthrough-push-data.md)

## <a name="next-steps"></a>Próximas etapas
[Inserindo com o Power BI](embedding.md)  
[Como migrar o conteúdo da coleção do espaço de trabalho do Power BI Embedded para o Power BI](migrate-from-powerbi-embedded.md)  
[Repositório Git de API do JavaScript](https://github.com/Microsoft/PowerBI-JavaScript)  
[Repositório Git de C# do Power BI](https://github.com/Microsoft/PowerBI-CSharp)  
[Publicar visuais personalizados na Office Store](office-store.md)  
[Repositório Git de elementos visuais do Power BI](https://github.com/Microsoft/PowerBI-visuals)  
[Exemplo inserido do JavaScript](https://microsoft.github.io/PowerBI-JavaScript/demo/)  
[API do Power BI no Apiary](http://docs.powerbi.apiary.io/#)  
[White paper do Power BI Premium](https://aka.ms/pbipremiumwhitepaper)  
Mais perguntas? [Experimente a Comunidade do Power BI](http://community.powerbi.com/)

