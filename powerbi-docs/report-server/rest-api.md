---
title: "Notas de versão do Servidor de Relatório do Power BI"
description: "A API REST fornece acesso por meio de programação aos objetos em um catálogo do Servidor de Relatórios do Power BI."
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
ms.date: 11/01/2017
ms.author: maghan
ms.openlocfilehash: ede77374fab911ed77a993cc705b8caa00e48bf0
ms.sourcegitcommit: eec6b47970bf69ed30638d1a20051f961ba792f2
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/06/2018
---
# <a name="develop-with-the-rest-apis-for-power-bi-report-server"></a>Desenvolver com as APIs REST do Servidor de Relatórios do Power BI
O Servidor de Relatórios do Power BI é compatível com as APIs REST (Transferência de Estado Representacional). As APIs REST são pontos de extremidade de serviço compatíveis com um conjunto de operações de HTTP (métodos), que fornecem acesso à criação, à recuperação, à atualização ou à exclusão para recursos em um servidor de relatório.

A API REST fornece acesso por meio de programação aos objetos em um catálogo do Servidor de Relatórios do Power BI. Os exemplos de objetos incluem pastas, relatórios, KPIs, fontes de dados, conjuntos de dados, planos de atualização, assinaturas e muito mais. Ao usar a API REST, é possível, por exemplo, navegar na hierarquia de pastas, descobrir o conteúdo de uma pasta ou baixar uma definição de relatório. Você também pode criar, atualizar e excluir objetos. Os exemplos de como trabalhar com objetos incluem carregar um relatório, executar um plano de atualização, excluir uma pasta e assim por diante.

## <a name="components-of-a-rest-api-requestresponse"></a>Componentes de uma solicitação/resposta da API REST
Um par solicitação/resposta da API REST pode ser dividido em cinco componentes:

* O **URI da solicitação**, que consiste em: `{URI-scheme} :// {URI-host} / {resource-path} ? {query-string}`. Embora o URI da solicitação seja incluído no cabeçalho da mensagem de solicitação, vamos chamá-lo separadamente aqui porque a maioria das linguagens ou das estruturas exige que ele seja passado separadamente da mensagem de solicitação.
  
  * Esquema de URI: indica o protocolo usado para transmitir a solicitação. Por exemplo, `http` ou `https`.
  * URI do host: especifica o nome de domínio ou o endereço IP do servidor, em que o ponto de extremidade de serviço REST está hospedado, como `myserver.contoso.com`.
  * Caminho do recurso: especifica o recurso ou a coleção de recursos, que pode incluir vários segmentos usados pelo serviço para determinar a seleção desses recursos. Por exemplo: `CatalogItems(01234567-89ab-cdef-0123-456789abcdef)/Properties` pode ser usado para obter as propriedades especificadas para o CatalogItem.
  * Cadeia de caracteres de consulta (opcional): fornece parâmetros adicionais simples, como os critérios de seleção de recursos ou a versão da API.
* Campos do cabeçalho da mensagem de solicitação HTTP:
  
  * Um [método HTTP](https://www.w3.org/Protocols/rfc2616/rfc2616-sec9.html) necessário (também conhecido como operação ou verbo), que informa o serviço que tipo de operação você está solicitando. As APIs REST do Reporting Services são compatíveis com os métodos DELETE, GET, HEAD, PUT, POST e PATCH.
  * Campos de cabeçalho adicionais opcionais, conforme exigido pelo método HTTP e o URI especificados.
* Campos do **corpo da mensagem de solicitação** HTTP, para fins de compatibilidade com a operação HTTP e URI. Por exemplo, as operações POST contêm objetos codificados em MIME passados como parâmetros complexos. Para as operações POST ou PUT, o tipo de codificação MIME para o corpo também deve ser especificado no cabeçalho da solicitação `Content-type`. Alguns serviços exigem que você use um tipo MIME específico, como `application/json`.
* Campos do **cabeçalho da mensagem de resposta** HTTP:
  
  * Um [código de status HTTP](http://www.w3.org/Protocols/HTTP/HTRESP.html), com intervalo de 2xx códigos de êxito e 4xx ou 5xx códigos de erro. Como alternativa, um código de status definido pelo serviço pode ser retornado, conforme indicado na documentação da API.
  * Campos de cabeçalho adicionais opcionais, conforme necessário para oferecer compatibilidade com a resposta da solicitação, como um cabeçalho de resposta `Content-type`.
* Campos do **corpo da mensagem de resposta** HTTP opcionais:
  
  * Objetos de resposta codificados em MIME são retornados no corpo da resposta HTTP, como uma resposta de um método GET retornando dados. Normalmente, esses objetos são retornados em um formato estruturado, como JSON ou XML, conforme indicado pelo cabeçalho de resposta `Content-type`.

## <a name="api-documentation"></a>Documentação da API
Uma API REST moderna necessita de uma documentação de API moderna. A API REST é baseada na especificação OpenAPI (também conhecida como a especificação swagger) e a documentação está disponível no [SwaggerHub](https://app.swaggerhub.com/apis/microsoft-rs/PBIRS/2.0). Além da documentação da API, o SwaggerHub ajuda a gerar uma biblioteca de clientes na linguagem desejada: JavaScript, TypeScript, C#, Java, Python, Ruby e muito mais.

## <a name="testing-api-calls"></a>Testando chamadas à API
O [Fiddler](http://www.telerik.com/fiddler) é uma ferramenta para testar mensagens de solicitação/resposta HTTP. O Fiddler é uma proxy de depuração Web gratuito que pode interceptar solicitações REST, o que facilita o diagnóstico das mensagens de solicitação/resposta HTTP.

## <a name="next-steps"></a>Próximas etapas
Examinar as APIs disponíveis no [SwaggerHub](https://app.swaggerhub.com/apis/microsoft-rs/PBIRS/2.0).

Os exemplos estão disponíveis no [GitHub](https://github.com/Microsoft/Reporting-Services). O exemplo inclui um aplicativo HTML5 baseado no TypeScript, no React e no webpack, juntamente com um exemplo do PowerShell.

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)

