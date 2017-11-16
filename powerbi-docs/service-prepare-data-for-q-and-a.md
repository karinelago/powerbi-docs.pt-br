---
title: "Faça seus dados funcionarem bem com P e R no Power BI"
description: "Faça seus dados funcionarem bem com P e R no Power BI"
services: powerbi
documentationcenter: 
author: mihart
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
ms.date: 09/26/2017
ms.author: mihart
ms.openlocfilehash: 499c3beca9046af9336de6dfec96994004050986
ms.sourcegitcommit: 284b09d579d601e754a05fba2a4025723724f8eb
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/15/2017
---
# <a name="make-your-data-work-well-with-qa-in-power-bi"></a>Faça seus dados funcionarem bem com P e R no Power BI
Se você for uma pessoa que cria modelos de dados ou cria pastas de trabalho do Excel que serão usadas com o Power BI, continue lendo...

No Power BI, perguntas e respostas podem pesquisar dados estruturados e escolher a visualização certa para a pergunta, que é o que torna uma ferramenta interessante para uso.   

A P e R pode trabalhar em qualquer arquivo Excel carregado que tem tabelas, intervalos ou que contém um modelo do PowerPivot, porém, quanto mais otimizações e limpeza de dados você fizer, mais robusto será o desempenho da P e R. 

## <a name="how-qa-works"></a>Como funciona P e R
Perguntas e respostas tem um conjunto de habilidades de compreensão de linguagem natural principal que funcionam em seus dados. Possui a pesquisa de palavra-chave dependente de contexto para sua tabela, coluna e nomes de campos calculados do Excel. Em segundo lugar, tem conhecimento interno sobre como filtrar, classificar, agregar, agrupar e exibir dados. 

Por exemplo, em uma tabela do Excel com o nome "Vendas", com colunas "Produto", "Mês", "Unidades vendidas", "Vendas brutas" e "Lucro", você pode fazer perguntas sobre qualquer uma dessas entidades.  Você pode pedir para mostrar as vendas, ganho total por mês, classificar os produtos por unidades vendidas e muitas outras opções. Leia mais sobre os [tipos de perguntas que você pode fazer](http://blogs.msdn.com/b/powerbi/archive/2014/02/27/demystifying-power-bi-q-amp-a-part-1.aspx) e sobre como [fazer perguntas usando um modelo de perguntas](service-q-and-a.md), bem como os [tipos de visualização que você pode especificar em uma consulta da P e R](power-bi-visualization-types-for-reports-and-q-and-a.md).

## <a name="prepare-a-workbook-for-qa"></a>Preparar uma pasta de trabalho para P e R
Perguntas e respostas baseia-se nos nomes das tabelas, colunas e campos calculados para responder a perguntas específicas de dados, o que significa que você chamar as entidades na pasta de trabalho é importante!

Aqui estão algumas dicas para aproveitar ao máximo de perguntas e respostas em sua pasta de trabalho.

* Verifique se os dados estão em uma tabela do Excel. Veja [como criar uma tabela do Excel](https://support.office.com/article/Create-an-Excel-table-in-a-worksheet-e81aa349-b006-4f8a-9806-5af9df0ac664?ui=en-US&rs=en-US&ad=US).
* Verifique se os nomes das tabelas, colunas e campos calculados fazem sentido em português.
  
  Por exemplo, se você tiver uma tabela com dados de vendas, colo que o nome da tabela de "Vendas". Nomes de coluna como "Ano", "Produto", "Representante de vendas" e "Valor" funcionaram bem com perguntas e respostas.

> [!NOTE]
> Se sua pasta de trabalho tiver um modelo de dados do Power Pivot, você poderá fazer ainda mais otimizações. Leia mais em [Desmistificando a P e R do Power BI, parte 2](http://blogs.msdn.com/b/powerbi/archive/2014/02/27/demystifying-power-bi-q-amp-a-part-2.aspx) de nossa equipe interna de especialistas em linguagem natural.
> 
> 

## <a name="next-steps"></a>Próximas etapas
[P e R no Power BI](service-q-and-a.md)  
[Tutorial: Introdução a P e R do Power BI](power-bi-visualization-introduction-to-q-and-a.md)  
[Obter dados (para o Power BI)](service-get-data.md)  
[Power BI – conceitos básicos](service-basic-concepts.md)

Mais perguntas? [Experimente a Comunidade do Power BI](http://community.powerbi.com/)

