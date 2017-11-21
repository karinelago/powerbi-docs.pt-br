---
title: Obter dados de arquivos
description: Saiba como obter dados do Excel, CSV e Power BI Desktop e inseri-los no Power BI
services: powerbi
documentationcenter: 
author: davidiseminger
manager: kfile
backup: 
editor: 
tags: 
qualityfocus: complete
qualitydate: 04/01/2016
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 07/20/2017
ms.author: davidi
ms.openlocfilehash: 08ea8e51c177defeae9ff1f63b73196d1e7ba35a
ms.sourcegitcommit: 284b09d579d601e754a05fba2a4025723724f8eb
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/15/2017
---
# <a name="get-data-from-files"></a>Obter dados de arquivos
![](media/service-get-data-from-files/file_icons.png)

No Power BI, é possível conectar-se a dados e relatórios ou importá-los por meio de três tipos de arquivos.

* Microsoft Excel (.xlsx ou .xlsm)
* Power BI Desktop (.pbix)
* Valores Separados por Vírgula (.csv)

## <a name="what-does-get-data-from-a-file-really-mean"></a>O que significa, de fato, obter dados de um arquivo?
No Power BI, os dados explorados são provenientes de um conjunto de dados. Mas, para ter um conjunto de dados, primeiro você precisa obter dados. Neste artigo, nosso foco será em como obter dados de arquivos.

Para entender melhor a importância de conjuntos de dados e como podemos obter dados para eles, vamos tomar como exemplo um automóvel. Entre no carro, sente-se e observe o dashboard. Isso é muito semelhante a sentar-se em frente ao computador e observar um dashboard no Power BI. O dashboard mostra a você tudo o que seu carro está fazendo: até que ponto o motor está acelerando, a temperatura, qual marcha está sendo usada, etc.

No Power BI, um conjunto de dados é como o motor do carro. O conjunto de dados fornece os dados, as métricas e as informações que são exibidas no dashboard do Power BI. Evidentemente, o motor, ou o conjunto de dados, precisa de combustível, e no Power BI, esse combustível são os dados. O carro tem um tanque de combustível que abastece o motor com gasolina. Da mesma que ocorre no Power BI, você precisa de um tanque de combustível com dados que possam ser alimentados no conjunto de dados. Em nosso caso, esse tanque de combustível é um arquivo do Power BI Desktop, um arquivo de pasta de trabalho do Excel ou um arquivo .CSV.

Podemos até ir um pouco mais longe. Um tanque de combustível de um carro deve ser enchido com gasolina. A gasolina para nosso arquivo do Power BI Desktop, Excel ou .CSV são os dados de outra fonte de dados. Obtemos dados de outra fonte de dados e os inserimos em um arquivo do Excel, Power BI Desktop ou .CSV. Se for uma pasta de trabalho do Excel ou um arquivo .CSV, poderemos inserir linhas de dados manualmente. Ou podemos nos conectar a uma fonte de dados externa para consultar e carregar dados em nosso arquivo. Assim que tivermos um arquivo com alguns dados, podemos inseri-los no Power BI como um conjunto de dados.

> [!NOTE]
> Os dados em pastas de trabalho do Excel devem estar em uma tabela ou no modelo de dados para serem importados pelo Power BI.
> 
> 

## <a name="where-your-file-is-saved-makes-a-difference"></a>O local em que o arquivo é salvo faz a diferença
**Local** - Caso o arquivo seja salvo em uma unidade local no computador ou em outro local em sua organização, por meio do Power BI, é possível *importar* o arquivo para o Power BI. Na verdade, o arquivo permanecerá na unidade local; portanto, o arquivo completo não é, de fato, importado para o Power BI. O que realmente ocorre é que um novo conjunto de dados é criado no site do Power BI e os dados e, em alguns casos, o modelo de dados, são carregados nesse conjunto de dados. Se o arquivo tiver relatórios, eles serão exibidos no site do Power BI em Relatórios.

**OneDrive - Business** – Caso você tenha o OneDrive for Business e entre com a mesma conta usada para o logon no Power BI, essa será, sem dúvida, a maneira mais efetiva de manter seu trabalho no Excel, no Power BI Desktop ou em um arquivo .CSV em sincronia com seu conjunto de dados, seus relatórios e dashboards no Power BI. Visto que tanto o Power BI quanto o OneDrive ficam na nuvem, o Power BI se conecta ao seu arquivo no OneDrive em intervalos aproximados de sessenta minutos. Caso sejam encontradas alterações, o conjunto de dados, os relatórios e os dashboards serão atualizados automaticamente no Power BI.

**OneDrive - Personal** – Caso os arquivos sejam salvos em sua própria conta do OneDrive, você aproveitará vários dos mesmos benefícios que teria com o OneDrive for Business. A maior diferença é que, na primeira conexão ao arquivo (usando Obter Dados > Arquivos > OneDrive – Personal), será necessário entrar no OneDrive com sua conta da Microsoft, que, normalmente, é diferente daquela usada para fazer logon no Power BI. Ao entrar no OneDrive com sua conta da Microsoft, certifique-se de selecionar a opção Mantenha-me conectado. Dessa forma, o Power BI poderá se conectar ao seu arquivo em intervalos aproximados de sessenta minutos e garantir que o conjunto de dados no Power BI está em sincronia.

**SharePoint – Sites de Equipe** – Salvar seus arquivos do Power BI Desktop no SharePoint – Sites de Equipe é muito semelhante a salvá-los no OneDrive for Business. A maior diferença nesse caso é como você se conecta ao arquivo do Power BI. É possível especificar uma URL ou conectar-se à pasta raiz.

## <a name="ready-to-get-started"></a>Pronto para começar?
Veja os seguintes artigos para saber mais sobre como inserir seu arquivo no Power BI.

* [Obter dados de arquivos de pasta de trabalho do Excel](service-excel-workbook-files.md)
* [Obter dados de arquivos do Power BI Desktop](service-desktop-files.md)
* [Obter dados de arquivos de Valores separados por vírgula](service-comma-separated-value-files.md)

