---
title: Dados multidimensionais do Analysis Services no Power BI Desktop
description: Dados multidimensionais do Analysis Services no Power BI Desktop
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
ms.date: 01/24/2018
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 18f80073bf690cd6fc64f94d25f8aad8bf5044e1
ms.sourcegitcommit: 00b4911ab5fbf4c2d5ffc000a3d95b3149909c28
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2018
---
# <a name="connect-to-ssas-multidimensional-models-in-power-bi-desktop"></a>Conectar-se a modelos multidimensionais do SSAS no Power BI Desktop
Com o Power BI Desktop, você pode acessar **modelos Multidimensionais do SSAS**, normalmente chamados de **SSAS MD**.

Para se conectar a um banco de dados de **SSAS MD**, selecione **Obter Dados &gt; Banco de Dados &gt; Banco de Dados do SQL Server Analysis Services**, como mostrado na imagem a seguir:

![](media/desktop-ssas-multidimensional/ssas-multidimensional-2.png)

**Modelos Multidimensionais SSAS** no modo de Conexão dinâmica têm suporte no serviço do Power BI e no Power BI Desktop. Você também pode publicar e carregar relatórios que usam **Modelos Multidimensionais SSAS** no modo Dinâmico para o serviço do Power BI.

## <a name="capabilities-and-features-of-ssas-md"></a>Recursos e capacidades do SSAS MD
As seções a seguir descrevem os recursos e capacidades das conexões do Power BI e SSAS MD.

### <a name="tabular-metadata-of-multidimensional-models"></a>Metadados tabulares de modelos multidimensionais
A tabela a seguir mostra a correspondência entre objetos multidimensionais e os metadados tabulares que são retornados ao Power BI Desktop. O Power BI consulta o modelo para metadados tabulares e com base nos metadados retornados, executa consultas DAX apropriadas no Analysis Services quando você cria uma visualização como uma tabela, matriz, gráfico ou segmentação.

| Objeto multidimensional de BISM | Metadados tabulares |
| --- | --- |
| Cubo |Modelo |
| Dimensão do cubo |Tabela |
| Atributos de dimensão (Chaves, Nome) |Colunas |
| Grupo de medidas |Table |
| Medida |Medida |
| Medidas sem grupo de medidas associado |Na tabela chamada *Medidas* |
| Grupo de medidas -> relação da dimensão do cubo |Relação |
| Perspectiva |Perspectiva |
| KPI |KPI |
| Hierarquias usuário/pai-filho |Hierarquias |

### <a name="measures-measure-groups-and-kpis"></a>Medidas, grupos de medidas e KPIs
Os grupos de medidas em um cubo multidimensional são expostos no Power BI como tabelas com o sinal ∑ ao lado deles no painel **Campos** . As medidas calculadas que não têm um grupo de medidas associado são agrupadas em uma tabela especial chamada *Medidas* nos metadados tabulares.

Em um modelo multidimensional, você pode definir um conjunto de medidas ou KPIs em um cubo a ser localizado em uma *Pasta de exibição*, que pode ajudar a simplificar modelos complexos. O Power BI reconhece as Pastas de exibição nos metadados tabulares e mostra as medidas e KPIs dentro das Pastas de exibição. Os KPIs em bancos de dados multidimensionais dão suporte a *Valor*, *Meta*, *Gráfico de Status* e *Gráfico de Tendência*.

### <a name="dimension-attribute-type"></a>Tipo de atributo de dimensão
Os modelos multidimensionais também dão suporte à associação de atributos de dimensão com tipos de atributo de dimensão específicos. Por exemplo, uma dimensão **Geografia** em que os atributos de dimensão *Cidade*, *Estado/Província*, *País* e *CEP* têm tipos de geografia apropriados associados a eles é exposta nos metadados tabulares. O Power BI reconhece os metadados, permitindo a criação de visualizações de mapa. Você reconhecerá essas associações pelo ícone de *mapa* ao lado do elemento no painel **Campo** painel no Power BI.

O Power BI também pode renderizar imagens quando você fornece um campo contendo URLs (Uniform Resource Locator) das imagens. Você pode especificar esses campos como o tipo *ImageURL* tipo no SQL Server Data Tools (ou posteriormente no Power BI) e as informações de tipo são fornecidas para o Power BI nos metadados tabulares. O Power BI pode recuperar essas imagens da URL e exibi-las em elementos visuais.

### <a name="parent-child-hierarchies"></a>Hierarquias pai-filho
Os modelos multidimensionais dão suporte a hierarquias pai-filho, que são apresentadas como uma *hierarquia* nos metadados tabulares. Cada nível da hierarquia pai-filho é exposto como uma coluna oculta nos metadados tabulares. O atributo-chave da dimensão pai-filho não é exposto nos metadados tabulares.

### <a name="dimension-calculated-members"></a>Membros calculados da dimensão
Os modelos multidimensionais dão suporte à criação de vários tipos de *membros calculados*. Os dois tipos mais comuns de membros calculados são os seguintes:

* Membros calculados em hierarquias de atributos e não em um irmão de *Todos*
* Membros calculados em hierarquias de usuário

Os modelos multidimensionais expõem *membros calculados em hierarquias de atributo* como valores de uma coluna. Há algumas opções e restrições adicionais durante a exposição deste tipo de membro calculado:

* O atributo de dimensão pode ter um *UnknownMember* opcional
* Um atributo com membros calculados não pode ser o atributo-chave da dimensão, a menos que seja o único atributo da dimensão
* Um atributo com membros calculados não pode ser um atributo pai-filho

Os membros calculados de hierarquias de usuário não são expostos no Power BI. Em vez disso, você poderá se conectar a um cubo com membros calculados em hierarquias de usuário, mas não poderá ver os membros calculados se eles não atenderem às restrições mencionadas na lista com marcadores anterior.

### <a name="security"></a>Segurança
Os modelos multidimensionais dão suporte à segurança do nível da dimensão e da célula por meio de *Funções*. Quando você se conecta a um cubo com o Power BI, é autenticado e avaliado quanto às permissões apropriadas. Quando o usuário tem a *segurança de dimensão* aplicada, os respectivos membros da dimensão não são vistos pelo usuário no Power BI. No entanto, quando um usuário tem uma permissão de *segurança da célula* definida, em que determinadas células são restritas, esse usuário não pode se conectar ao cubo usando o Power BI.

## <a name="limitations-of-ssas-multidimensional-models-in-power-bi-desktop"></a>Limitações de modelos multidimensionais do SSAS no Power BI Desktop
Há algumas limitações no uso do **SSAS MD**:

* Os servidores devem executar o SQL Server 2012 SP1 CU4 ou versões posteriores do Analysis Services para que o conector do SSAS MD do Power BI Desktop funcione corretamente
* *Ações* e *Conjuntos Nomeados* não são expostos no Power BI, mas você ainda pode se conectar a cubos que também contêm *Ações* ou *Conjuntos Nomeados* e criar elementos visuais e relatórios.

## <a name="supported-features-of-ssas-md-in-power-bi-desktop"></a>Recursos com Suporte do SSAS MD no Power BI Desktop
Os seguintes recursos do SSAS MD têm suporte no Power BI Desktop:

* Há suporte para o consumo dos seguintes elementos nesta versão do **SSAS MD** (você pode obter [mais informações](https://msdn.microsoft.com/library/jj969574.aspx) sobre esses recursos):
  * Exibir pastas
  * Tendências de KPI
  * Membros padrão
  * Atributos de dimensão
  * Membros calculados da dimensão (devem ser um único membro real quando a dimensão tiver mais de um atributo; ele não pode ser o atributo de chave da dimensão, a menos que seja o único atributo, e não pode ser um atributo pai-filho)
  * Tipos de atributo de dimensão
  * Hierarquias
  * Medidas (com ou sem grupos de Medidas)
  * Medidas como variantes
  * KPIs
  * ImageUrls
  * Segurança da dimensão

