---
title: O que posso fazer com a API do Power BI
description: O que posso fazer com a API do Power BI
author: markingmyname
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-developer
ms.topic: conceptual
ms.date: 05/25/2018
ms.author: maghan
ms.openlocfilehash: 8a688f46a46dbb1015629c7785d96b62d4f8df26
ms.sourcegitcommit: 8ee0ebd4d47a41108387d13a3bc3e7e2770cbeb8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2018
ms.locfileid: "34813218"
---
# <a name="what-can-developers-do-with-the-power-bi-api"></a>O que os desenvolvedores podem fazer com a API do Power BI?
O Power BI exibe painéis interativos e que podem ser criados e atualizados por meio de várias fontes de dados diferentes em tempo real. Ao usar qualquer linguagem de programação que dá suporte a chamadas REST, você pode criar aplicativos que se integram a um painel do Power BI em tempo real. Você também pode integrar blocos do Power BI e relatórios a aplicativos.

Os desenvolvedores também podem criar suas próprias visualizações de dados, que podem ser usadas em dashboards e relatórios interativos. 

Aqui estão algumas das coisas que você pode fazer com as APIs do Power BI.

| **Para fazer isso** | **Clique aqui** |
| --- | --- |
| Inserir dashboards, relatórios e blocos para usuários do Power BI e usuários que não têm o Power BI (o aplicativo possui dados) |[Como inserir seus dashboards, relatórios e blocos do Power BI](embedding-content.md) |
| Estender um fluxo de trabalho de negócios existente para enviar por push dados de chave a um painel do Power BI. |[Enviar dados por push a um dashboard](walkthrough-push-data.md) |
| Autentique-se no Power BI. |[Autenticar-se no Power BI](get-azuread-access-token.md) |
| Criar um visual personalizado. |[Usar ferramentas de desenvolvedor para criar visuais personalizados](../service-custom-visuals-getting-started-with-developer-tools.md) |

> [!NOTE]
> As APIs do Power BI ainda se referem aos espaços de trabalho do aplicativo como grupos. As referências a grupos significam que você está trabalhando com espaços de trabalho do aplicativo.
> 
> 

## <a name="power-bi-developer-samples"></a>Exemplos para Desenvolvedores do Power BI
Os exemplos para desenvolvedores do Power BI incluem itens para inserir dashboards, relatórios e blocos.

[Exemplos para Desenvolvedores do Power BI](https://github.com/Microsoft/PowerBI-Developer-Samples)

* Exemplos em **O aplicativo possui os dados** são para inserção com usuários que não têm o Power BI.
* Exemplos em **O usuário possui os dados** são para inserção com usuários do Power BI.

## <a name="github-repositories"></a>Repositórios GitHub
* [SDK do .NET](https://github.com/Microsoft/PowerBI-CSharp)
* [API do JavaScript](https://github.com/Microsoft/PowerBI-JavaScript)
* [Visuais personalizados](https://github.com/Microsoft/PowerBI-visuals)

## <a name="developer-tools"></a>Ferramentas de desenvolvedor
Veja a seguir as ferramentas que você pode usar para ajudar no desenvolvimento de itens do Power BI.

É possível acessar a [Ferramenta de experiência de integração](https://aka.ms/embedsetup) para começar rapidamente e baixar um aplicativo de exemplo sobre como inserir conteúdo do Power BI.

Escolha a solução certa para você:
* A [inserção para clientes](embedding.md#embedding-for-your-customers) fornece a capacidade de inserir os dashboards e relatórios para usuários que não têm uma conta do Power BI. Execute a solução [Inserir para clientes](https://aka.ms/embedsetup/AppOwnsData).
* A [inserção para a organização](embedding.md#embedding-for-your-organization) permite que você estenda o serviço do Power BI. Execute a solução [Inserir para a organização](https://aka.ms/embedsetup/UserOwnsData).

Para obter um exemplo completo de como usar a API JavaScript, use a [ferramenta de Playground](https://microsoft.github.io/PowerBI-JavaScript/demo). Trata-se de uma maneira rápida de experimentar diferentes tipos de exemplos do Power BI Embedded. Você também pode obter mais informações sobre a API de JavaScript, visitando a página da [wiki PowerBI-JavaScript](https://github.com/Microsoft/powerbi-javascript/wiki).

## <a name="next-steps"></a>Próximas etapas
[Enviar dados por push a um conjunto de dados](walkthrough-push-data.md)  
[Introdução às ferramentas de desenvolvedor de visuais personalizados](../service-custom-visuals-getting-started-with-developer-tools.md) 
[Referência da API REST do Power BI](https://docs.microsoft.com/rest/api/power-bi/)  

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](http://community.powerbi.com/)