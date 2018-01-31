---
title: "Inserir um relatório usando um iFrame"
description: "Instalar o próprio Servidor de Relatórios do Power BI é muito rápido. Do download a instalação e configuração, você deve entrar em funcionamento em poucos minutos."
services: powerbi
documentationcenter: 
author: markingmyname
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
ms.date: 11/09/2017
ms.author: maghan
ms.openlocfilehash: 56835bfb25c8c930099fadf710137f69fa89fc2e
ms.sourcegitcommit: 6e693f9caf98385a2c45890cd0fbf2403f0dbb8a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2018
---
# <a name="quickstart-embed-a-power-bi-report-using-an-iframe-and-url-parameters"></a>Início rápido: inserir um relatório do Power BI usando um iFrame e parâmetros de URL

É possível inserir qualquer relatório usando um iFrame em seu aplicativo. 

## <a name="url-parameter"></a>Parâmetro da URL

Para qualquer URL de um relatório, é possível adicionar um parâmetro querystring de `?rs:Embed=true`.

Por exemplo:

```
http://myserver/reports/powerbi/Sales?rs:embed=true
```

Isso funcionará em todos os tipos de relatório no Servidor de Relatório do Power BI.

## <a name="iframe"></a>iFrame

Quando tiver sua URL, você poderá criar um iFrame em uma página da Web para hospedar o relatório.

Por exemplo:

```
<iframe width="800" height="600" src="http://myserver/reports/powerbi/Sales?rs:embed=true" frameborder="0" allowFullScreen="true"></iframe>
```

## <a name="url-filter"></a>Filtro de URL

Adicione um parâmetro de cadeia de caracteres de consulta à URL para filtrar os dados retornados no relatório do Power BI.

A sintaxe é razoavelmente simples; comece com a URL do relatório, adicione um ponto de interrogação e, em seguida, a sintaxe do filtro.

URL?filter=***Table***/***Field*** eq '***value***'

Lembre-se do seguinte:

- Nomes de **Tabela** e **Campo** diferenciam maiúsculas de minúsculas, o **valor** não.
- Filtre um relatório com campos ocultos na exibição do relatório.
- O **Valor** deve estar entre aspas simples.
- O tipo de campo deve ser uma cadeia de caracteres.
- Nomes de tabelas e campos não podem conter espaços.

###  <a name="example-filter-on-a-field"></a>Exemplo: Filtrar em um campo

Veja o exemplo de [Amostra de análise de varejo](../sample-datasets.md). Digamos que esta é a URL para o relatório, no servidor de relatórios, em uma pasta chamada "power bi":

```
https://report-server/reports/power-bi/Retail-Analysis-Sample
```

Você verá que a visualização de mapa na amostra da Análise de varejo mostra repositórios na Carolina do Norte e outros estados.

![Visualização de mapa de amostra da análise de varejo](media/quickstart-embed/report-server-retail-analysis-sample-map.png)

*NC* é um valor da Carolina do Norte armazenado no campo **Território** da tabela **Repositório**. Para filtrar o relatório para mostrar dados somente de repositórios na Carolina do Norte, acrescente o seguinte à URL:

?filter=Store/Territory eq 'NC'

Agora relatório é filtrado para a Carolina do Norte; todas as visualizações na página de relatório mostram dados apenas da Carolina do Norte.

![Visualizações filtradas de amostra da análise de varejo](media/quickstart-embed/report-server-retail-analysis-sample-filtered-map.png)

### <a name="create-a-dax-formula-to-filter-on-multiple-values"></a>Criar uma fórmula DAX para filtrar vários valores

Outra maneira de filtrar em vários campos é criar uma coluna calculada no Power BI Desktop que concatena dois campos em um único valor. A partir daí, é possível filtrar nesse valor.

Por exemplo, a amostra de Análise de varejo tem dois campos: Território e Cadeia. No Power BI Desktop, [crie uma nova coluna calculada](../desktop-tutorial-create-calculated-columns.md) (campo) chamada TerritoryChain. Lembre-se que o nome do **Campo** não pode conter espaços. Veja a seguir a fórmula DAX da coluna.

TerritoryChain = [Territory] & "-" & [Chain]

Publique o relatório no Servidor de Relatórios do Power BI e, em seguida, use a cadeia de caracteres de consulta de URL para filtrar e exibir dados somente de repositórios Lindseys na Carolina do Norte.

```
https://report-server/reports/power-bi/Retail-Analysis-Sample?filter=Store/TerritoryChain eq 'NC-Lindseys'

```

## <a name="next-steps"></a>Próximas etapas

[Início rápido: criar um relatório do Power BI para o Servidor de Relatório do Power BI](quickstart-create-powerbi-report.md)  
[Início rápido: criar um relatório paginado para o Servidor de Relatório do Power BI](quickstart-create-paginated-report.md)  

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)