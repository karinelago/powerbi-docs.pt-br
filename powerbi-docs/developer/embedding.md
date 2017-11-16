---
title: "Inserção com o Power BI"
description: "O Power BI oferece APIs para inserir seus dashboards e relatórios em aplicativos."
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
ms.date: 10/05/2017
ms.author: asaxton
ms.openlocfilehash: 36eb4231b6b3d3278d571722bde731051ffdf05e
ms.sourcegitcommit: 99cc3b9cb615c2957dde6ca908a51238f129cebb
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/13/2017
---
# <a name="embedding-with-power-bi"></a>Inserção com o Power BI
O Power BI oferece APIs para inserir seus dashboards e relatórios em aplicativos. As APIs do Power BI oferece um conjunto consistente de recursos e o acesso aos recursos mais recentes do Power BI, tais como dashboards, gateways e espaços de trabalho de aplicativo, ao inserir seu conteúdo.

## <a name="a-single-api"></a>Uma única API
Há dois cenários principais ao inserir conteúdo do Power BI. Inserção para sua organização e para seus clientes. A API REST do Power BI permite os dois cenários. Isso permitirá a você inserir dashboards e relatórios em seu aplicativo personalizado, usando a mesma API para atender à organização ou os clientes. Você pode se beneficiar das APIs REST e do JavaScript para suas necessidades de inserção.

Para exibir uma amostra de como a inserção funciona, consulte a [amostra de inserção do JavaScript](https://microsoft.github.io/PowerBI-JavaScript/demo/).

## <a name="embedding-for-your-organization"></a>Inserção para a organização
A inserção para a organização permite que você estenda o serviço do Power BI. Isso exigirá que o usuário final do seu aplicativo faça logon no serviço do Power BI quando desejar exibir o conteúdo. Depois que alguém na organização conectar, esse usuário só terá acesso aos dashboards e relatórios que foram compartilhados com ele no serviço do Power BI. 

*Exemplos de inserção para a organização incluem o aplicativo Web interno, a Web Part do SharePoint Online e integração do Microsoft Teams.*

Para inserir para a organização, consulte o seguinte:

* [Integrar um painel em um aplicativo](integrate-dashboard.md)
* [Integrar um bloco em um aplicativo](integrate-tile.md)
* [Integrar um relatório em um aplicativo](integrate-report.md)

Recursos de autoatendimento, como editar, salvar e muito mais, estão disponíveis por meio de [API JavaScript](https://github.com/Microsoft/PowerBI-JavaScript) ao inserir para usuários do Power BI.

## <a name="embedding-for-your-customers"></a>Inserção para os clientes
A inserção para os clientes fornece a capacidade de inserir os dashboards e relatórios a usuários que não têm uma conta do Power BI. Os clientes não precisam saber nada sobre o Power BI. É necessário ter pelo menos uma conta Power BI Pro. Essa conta do Power BI Pro atuará como uma conta mestre do seu aplicativo. Pense nisso como uma conta de proxy. A conta do Power BI Pro também permite a geração de tokens de inserção que fornecem acesso a dashboards e relatórios no serviço do Power BI. 

*Um exemplo de inserção para os clientes é um aplicativo de ISV sendo vendido para outras empresas.*

![Fluxo de inserção ao inserir para os clientes](media/embedding/powerbi-embed-flow.png)

Para inserir dashboards, relatórios e blocos, você usaria as mesmas APIs que usaria para inserir para a organização.

> [!IMPORTANT]
> Embora a inserção seja dependente do serviço do Power BI, não há uma dependência do Power BI para os clientes. Eles não precisa inscrever-se no Power BI para exibir o conteúdo inserido em seu aplicativo.
> 
> 

Quando você estiver pronto para passar para a produção, seu espaço de trabalho do aplicativo deverá ser atribuído a uma capacidade. O Power BI Embedded, no Microsoft Azure, oferece a capacidade para usar com seus aplicativos.

Para obter detalhes sobre como inserir, consulte [Como inserir seus dashboards, relatórios e blocos do Power BI](embedding-content.md).

Se você estiver usando o serviço de Coleção de Espaços de Trabalho do Power BI no Azure, consulte [Migrar o conteúdo do serviço de Coleção de Espaços de Trabalho do Power BI do Azure](migrate-from-powerbi-embedded.md) para obter informações sobre como migrar o conteúdo.

## <a name="next-steps"></a>Próximas etapas
[Como inserir seus dashboards, relatórios e blocos do Power BI](embedding-content.md)  
[Como migrar o conteúdo da coleção do espaço de trabalho do Power BI Embedded para o Power BI](migrate-from-powerbi-embedded.md)  
[Power BI Premium – o que é?](../service-premium.md)  
[Repositório Git de API do JavaScript](https://github.com/Microsoft/PowerBI-JavaScript)  
[Repositório Git de C# do Power BI](https://github.com/Microsoft/PowerBI-CSharp)  
[Exemplo inserido do JavaScript](https://microsoft.github.io/PowerBI-JavaScript/demo/)  
[White paper de planejamento de capacidade de análise inserida](https://aka.ms/pbiewhitepaper)  
[White paper do Power BI Premium](https://aka.ms/pbipremiumwhitepaper)  

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](http://community.powerbi.com/)

