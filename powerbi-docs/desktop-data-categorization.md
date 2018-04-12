---
title: Categorização de dados no Power BI Desktop
description: Categorização de dados no Power BI Desktop
services: powerbi
documentationcenter: ''
author: davidiseminger
manager: kfile
backup: ''
editor: ''
tags: ''
qualityfocus: no
qualitydate: ''
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 12/06/2017
ms.author: davidi
LocalizationGroup: Model your data
ms.openlocfilehash: cc66655e49860160b43afa5d1acb688c37468212
ms.sourcegitcommit: c80fbf5b12754ce217cb47a17cb5400b1036a8f2
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2018
---
# <a name="data-categorization-in-power-bi-desktop"></a>Categorização de dados no Power BI Desktop
No **Power BI Desktop**, você pode especificar a Categoria de Dados para uma coluna de modo que o Power BI Desktop saiba como deve tratar seus valores em uma visualização.

Quando o Power BI Desktop importa dados, ele não apenas obtém os dados em si, mas também informações como os nomes de tabela e coluna, se trata-se ou não de uma chave primária, etc.  Com essas informações, o Power BI Desktop faz algumas suposições sobre como oferecer a você uma boa uma experiência padrão ao criar uma visualização. 

Veja um exemplo: quando o Power BI Desktop detectar que uma coluna tem valores numéricos, você provavelmente desejará agregá-la de algum modo para que ela seja colocada na área Valores. Ou, para uma coluna com valores de data e hora, ele pressupõe que você provavelmente a usará como um eixo de hierarquia de tempo em um gráfico de linhas.

No entanto, existem alguns casos que são um pouco mais difíceis, como geografia. Considere esta tabela de uma planilha do Excel:

![](media/desktop-data-categorization/datacategorizationtable.png)

O Power BI Desktop deve tratar os códigos na coluna GeoCode como uma abreviação para um País ou um Estado dos EUA?  Isso não está claro, porque um código como esse pode significar qualquer uma dessas opções.  Por exemplo, AL pode significar Alabama ou Albânia, AR pode significar Arkansas ou Argentina, CA pode significar Califórnia ou no Canadá. Isso faz diferença quando vamos traçar um gráfico de nosso campo GeoCode em um mapa.  O Power BI Desktop deve mostrar uma imagem do mundo com os países realçados ou uma imagem dos Estados Unidos com os estados realçados?  Você pode especificar uma Categoria de Dados para dados exatamente como esses. A categorização de dados refina ainda mais as informações que o Power BI Desktop pode usar para oferecer as melhores visualizações.  

**Para especificar uma Categoria de dados**

1. Na Exibição de Relatório ou de Dados, na lista **Campos** , selecione o campo que você deseja classificar por uma categorização diferente.
2. Na faixa de opções, na guia **Modelagem**, clique na lista suspensa **Categoria de Dados:**.  Isso mostra a lista de categorias de dados possíveis que você pode escolher para a coluna.  Algumas seleções podem ser desabilitadas se não funcionarem com o tipo de dados atual da coluna.  Por exemplo, se uma coluna for um tipo de dados binário, o Power BI Desktop não permite que você escolha categorias de dados geográficos. 

![](media/desktop-data-categorization/datacategorization.gif)

E isso é tudo!  Qualquer comportamento que se acumula normalmente para um elemento visual agora funcionará automaticamente.  

Talvez você também esteja interessado em saber mais sobre a [filtragem geográfica para aplicativos móveis do Power BI](desktop-mobile-geofiltering.md).

