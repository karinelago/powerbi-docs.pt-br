---
title: Histogramas
description: Histogramas
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 05/02/2018
ms.author: davidi
LocalizationGroup: Visualizations
ms.openlocfilehash: 43ecdccbbe44721d4205ebc05d9d8406eed7e68b
ms.sourcegitcommit: 80d6b45eb84243e801b60b9038b9bff77c30d5c8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34298034"
---
# <a name="histograms"></a>Histogramas
Há várias maneiras de criar histogramas no Power BI. Nós começaremos com a mais simples e continuar a partir daí.

## <a name="simple-histograms"></a>Histogramas simples
Para começar, determine qual consulta contém o campo no qual você deseja criar um histograma.  Use a opção *Referência* da consulta para criar uma nova consulta e nomeie-a como *FieldName Histogram*. Use a opção **Agrupar por** na faixa de opções **Transformar** e selecione a agregação **contagem de linhas** . Verifique se o tipo de dados é um número para a coluna agregada resultante. Em seguida, você pode visualizar esses dados na página de relatórios. Essa abordagem é rápida e fácil de criar, mas não funciona bem se você tiver muitos pontos de dados e não permitir a varredura entre elementos visuais.

## <a name="defining-buckets-to-build-a-histogram"></a>Definindo buckets para criar um histograma
Determine qual consulta contém o campo no qual você deseja criar um histograma. Use a opção *Referência* da consulta para criar uma nova consulta e nomeie-a como *FieldName*.  Agora, defina os buckets com uma regra. Use a opção **Adicionar Coluna Personalizada** na faixa de opções **Adicionar Coluna** e crie uma regra personalizada.

![](media/service-histograms/powerbi-service-histograms_1.png)

Verifique se o tipo de dados é um número para a coluna agregada resultante. Agora você pode usar a técnica de agrupamento descrita em **Histogramas Simples** (no início deste artigo) para chegar ao histograma. Essa opção trata de mais pontos de dados, mas ainda não ajuda com a varredura.

## <a name="defining-a-histogram-that-supports-brushing"></a>Definindo um histograma que dá suporte à varredura
Varredura é quando os elementos visuais são vinculados para que, quando um usuário selecionar um ponto de dados em um elemento visual, os outros elementos visuais na página do relatório realcem ou filtrem pontos de dados relacionados ao ponto de dados selecionado.  Como estamos manipulando dados no momento da consulta, precisaremos criar uma relação entre tabelas e garantir que saibamos qual item detalhado se relaciona ao bucket no histograma e vice-versa.

Inicie o processo usando a opção *Referência* na consulta que contém o campo no qual você deseja criar um histograma.  Nomeie a nova consulta *Buckets*.  Para este exemplo, vamos chamar a consulta original de *Detalhes*.  Em seguida, remova todas as colunas, exceto a coluna que você usará como o bucket do histograma.  Agora, use o recurso *Remover Duplicatas* na consulta, no menu de atalho ao selecionar a coluna, para que os valores restantes sejam os valores exclusivos na coluna. Se você tiver números decimais, primeiro você poderá usar a dica para definir buckets para criar um histograma para obter um conjunto gerenciável de buckets.  Agora, verifique os dados mostrados na visualização da consulta. Se você vir valores nulos ou em branco, você precisará corrigi-los antes de criar uma relação. Veja “Criando relações quando os dados contêm valores nulos ou em branco”. Usar essa abordagem pode ser problemático devido à necessidade de classificação. Para que os buckets sejam classificados corretamente, veja “Ordem de classificação: fazem com que as categorias apareçam na ordem desejada”. 

> [!NOTE]
> É útil pensar sobre a ordem de classificação antes de compilar visuais.   
> 
> 

A próxima etapa do processo é definir uma relação entre as consultas de *Buckets* e *Detalhes* na coluna de buckets.  No *Power BI Desktop*, selecione *Gerenciar Relações* na faixa de opções.  Crie uma relação em que *Buckets* está na tabela esquerda e *Detalhes* na tabela direita e selecione o campo que você está usando para o histograma. 

A última etapa é criar o histograma. Arraste o campo Bucket da tabela *Buckets* . Remova o campo padrão do gráfico de colunas resultante.  Agora, na tabela *Detalhes* , arraste o campo do histograma até o mesmo elemento visual. No contêiner do campo, altere a agregação padrão para Contar. O resultado é o histograma. Se você criar outro elemento visual como um treemap da tabela de Detalhes, selecione um ponto de dados no treemap para ver o histograma realçado e mostrá-lo para o ponto de dados selecionado em relação à tendência de todo o conjunto de dados.

