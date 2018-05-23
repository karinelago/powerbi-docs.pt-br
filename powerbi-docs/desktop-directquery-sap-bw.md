---
title: DirectQuery e SAP BW (Business Warehouse) no Power BI
description: Considerações sobre o uso do DirectQuery com o SAP Business Warehouse (BW)
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 03/07/2018
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: a8fde13b0beeb57fb5d25aa35002358f04ab6cad
ms.sourcegitcommit: 638de55f996d177063561b36d95c8c71ea7af3ed
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/17/2018
---
# <a name="directquery-and-sap-business-warehouse-bw"></a>DirectQuery e SAP Business Warehouse (BW)
Você pode se conectar a fontes de dados do **SAP Business Warehouse (BW)** diretamente usando o **DirectQuery**. Devido à natureza de OLAP/multidimensional do SAP BW, há várias diferenças importantes entre o DirectQuery com o SAP BW e com fontes relacionais, como o SQL Server. Essas diferenças são resumidas da seguinte maneira:

* No **DirectQuery** com fontes relacionais, há um conjunto de consultas (conforme definido na caixa de diálogo **Obter Dados** ou **Editor de Consultas**) que definem logicamente os dados que estão disponíveis na lista de campos. Esse *não* é o caso ao se conectar a uma fonte OLAP, como o SAP BW. Em vez disso, ao se conectar ao servidor SAP usando **Obter Dados**, apenas a consulta do BEx ou do Infocube será selecionada. Em seguida, todos os valores-chave e dimensões da consulta do BEx/Infocube selecionada estarão disponíveis na lista de campos.   
* De maneira semelhante, não há nenhum **Editor de Consultas** ao se conectar ao SAP BW. As configurações da fonte de dados (por exemplo, o nome do servidor) podem ser alteradas selecionando **Editar Consultas > Configurações da fonte de dados**. As configurações de qualquer parâmetro podem ser alteradas selecionando **Editar Consultas > Gerenciar Parâmetros**.
* Devido à natureza única das fontes OLAP, há restrições adicionais (para modelagem e visualizações) que se aplicam, além das restrições normais impostas ao DirectQuery. Essas restrições são descritas posteriormente neste artigo.

Além disso, é *extremamente importante* entender que muitos recursos do SAP BW não têm suporte no Power BI e que, devido à natureza da interface pública com o SAP BW, há casos importantes em que os resultados vistos por meio do Power BI não corresponderão àqueles vistos usando uma ferramenta SAP. Tais limitações são descritas posteriormente neste artigo. Essas limitações e diferenças de comportamento devem ser analisadas atentamente, a fim de garantir que os resultados vistos por meio do Power BI, conforme retornados pela interface pública do SAP, sejam interpretados corretamente.  

> [!NOTE]
> A capacidade de usar o DirectQuery no SAP BW estava em versão prévia até a atualização de março de 2018 do Power BI Desktop. Durante a versão prévia, comentários e sugestões de melhorias solicitaram uma alteração que afeta relatórios que foram criados com essa versão prévia. Agora a versão GA (disponibilidade geral) do DirectQuery no SAP BW foi lançada, você *deve* descartar todos os relatórios existentes (baseados na versão prévia) que usam o DirectQuery no SAP BW, criados com a versão de pré-lançamento. Em relatórios criados com a versão de pré-lançamento do DirectQuery no SAP BW, ocorrerão erros ao invocar a Atualização, como resultado da tentativa de atualizar os metadados com as alterações no cubo subjacente do SAP BW. Refaça esses relatórios usando um relatório em branco, com a versão GA do DirectQuery no SAP BW. 

## <a name="additional-modeling-restrictions"></a>Restrições de modelagem adicionais
As principais restrições de modelagem adicionais ao se conectar ao SAP BW usando o DirectQuery no Power BI são as seguintes:

* **Não há suporte para colunas calculadas:** a capacidade de criar colunas calculadas fica desabilitada. Isso também significa que o Agrupamento e o Clustering, que criam colunas calculadas, não estão disponíveis.
* **Limitações adicionais para medidas:** há limitações adicionais impostas sobre as expressões DAX que podem ser usadas em medidas para refletir o nível de suporte oferecido pelo SAP BW.
* **Não há suporte para definição de relações:** as relações são inerentes na fonte externa do SAP e relações adicionais não podem ser definidas no modelo.
* **Não há Exibição de Dados:** a **Exibição de Dados** normalmente exibe dados com nível de detalhe nas tabelas. Dada a natureza das fontes de OLAP como o SAP BW, essa exibição não está disponível com o SAP BW.
* **Os detalhes das colunas e das medidas são fixos:** a lista de colunas e medidas vistas na lista de campos são fixas segundo a fonte subjacente e não podem ser modificadas. Por exemplo, não é possível excluir uma coluna ou alterar seu tipo de dados (no entanto, é possível renomeá-la).
* **Limitações adicionais no DAX:** há limitações adicionais no DAX que podem ser usadas em definições de medida para refletir as limitações na fonte. Por exemplo, não é possível usar uma função de agregação em uma tabela.

## <a name="additional-visualization-restrictions"></a>Restrições de visualização adicionais
As principais restrições de visualização adicionais ao se conectar ao SAP BW usando o DirectQuery no Power BI são as seguintes:

* **Não há agregação de colunas:** não é possível alterar a agregação para uma coluna em um visual; ela sempre é *Não Resumir*
* **A filtragem de medidas fica desabilitada:** a filtragem de medidas fica desabilitada para refletir o suporte oferecido pelo SAP BW.
* **Seleção múltipla e incluir/excluir:** a capacidade fazer a seleção múltipla de pontos de dados em um visual ficará desabilitada se os pontos representarem valores de mais de uma coluna. Por exemplo, dado um gráfico de barras que mostra Vendas por país, com a Categoria na Legenda, não seria possível selecionar o ponto relativo a (EUA, Bicicletas) e (França, Roupas). Da mesma forma, não seria possível selecionar o ponto relativo a (EUA, Bicicletas) e excluí-lo do visual. As duas limitações são impostas para refletir o suporte oferecido pelo SAP BW.

## <a name="support-for-sap-bw-features"></a>Suporte para recursos do SAP BW
A tabela a seguir lista todos os recursos do SAP BW que não têm suporte completo ou que têm comportamento diferente ao usar o Power BI.   

| Recurso | Descrição |
| --- | --- |
| Cálculos locais |Cálculos locais definidos em uma Consulta do BEx alteram os números com relação à forma como eles são exibidos por meio de ferramentas como o BEx Analyzer. No entanto, eles não são refletidos nos números retornados pelo SAP por meio da interface pública do MDX. <br/> <br/> **Dessa forma, os números vistos em um visual do Power BI não necessariamente corresponderão aos números de um visual correspondente em uma ferramenta SAP.**<br/> <br/>  Por exemplo, ao se conectar a um cubo de consulta de uma consulta do BEx que define a agregação como Acumulada (ou seja, a soma parcial), o Power BI receberia os números base, ignorando essa configuração.  Um analista certamente poderia, então, aplicar um cálculo de soma parcial localmente no Power BI, mas precisaria ter cuidado com a forma como os números seriam interpretados se isso não fosse feito. |
| Agregações |Em alguns casos (especialmente ao lidar com várias moedas), os números agregados retornados pela interface pública do SAP não correspondam àqueles mostrados por ferramentas SAP. <br/> <br/> **Dessa forma, os números vistos em um visual do Power BI não necessariamente corresponderão aos números de um visual correspondente em uma ferramenta SAP.** <br/> <br/> Por exemplo, valores totais relativos a moedas diferentes seriam mostrados como "*" no BEx Analyzer, mas o total seria retornado pela interface pública do SAP, sem nenhuma informação de que esse número agregado não significa nada. Assim, o número (agregando, digamos, US$, EUR e AUD) seria exibido pelo Power BI. |
| Formatação de moeda |Nenhuma formatação de moeda (por exemplo, US$ 2.300 ou AUD 4000) será refletida no Power BI. |
| Unidades de medida |Unidades de medida (por exemplo, 230 KG) não são refletidas no Power BI. |
| Chave versus texto (curto, médio, longo) |Para uma característica do SAP BW como o CostCenter, a lista de campos mostrará uma única coluna Centro de Custo.  Usar essa coluna exibirá o texto padrão.  Exibindo os campos ocultos, também será possível ver a coluna de nome exclusivo (que retorna o nome exclusivo atribuído pelo SAP BW e é a base da exclusividade).<br/> <br/>  A chave e outros campos de texto não estão disponíveis. |
| Várias hierarquias de uma característica |No **SAP**, uma característica pode ter várias hierarquias. Em ferramentas como o BEx Analyzer, quando uma característica é incluída em uma consulta, o usuário pode selecionar a hierarquia a ser usada. <br/> <br/> No **Power BI**, as diversas hierarquias podem ser vistas na lista de campos como hierarquias diferentes na mesma dimensão.  No entanto, selecionar vários níveis de duas hierarquias diferentes na mesma dimensão fará com que dados vazios sejam retornados pelo SAP. |
| Tratamento de hierarquias desbalanceadas |![](media/desktop-directquery-sap-bw/directquery-sap-bw_01.png) |
| Fator de escala/inverter sinal |No SAP, um valor-chave pode ter um fator de escala (por exemplo, 1000) definido como uma opção de formatação, o que significa que toda a exibição será dimensionada segundo esse fator. <br/> <br/> Da mesma forma, ele pode ter uma propriedade definida que inverte o sinal. O uso de tal valor-chave no Power BI (em um visual ou como parte de um cálculo) fará com que o número sem a escala seja usado (e com que o sinal não seja invertido). O fator de escala subjacente não está disponível. Em visuais do Power BI, as unidades de escala mostradas no eixo (K, M, B) podem ser controladas como parte da formatação do visual. |
| Hierarquias em que os níveis apareceram/desaparecerem dinamicamente |Inicialmente, ao se conectar ao SAP BW, as informações nos níveis de uma hierarquia serão recuperadas, resultando em um conjunto de campos na lista de campos. Isso é armazenado em cache e, se o conjunto de níveis for alterado, o conjunto de campos não será alterado até que Atualizar seja invocado. <br/> <br/> Isso só é possível no **Power BI Desktop**. Essa Atualização para refletir as alterações nos níveis não pode ser invocada no serviço do Power BI após a publicação. |
| Filtro padrão |Uma consulta do BEx pode incluir Filtros padrão, que serão aplicados automaticamente pelo SAP BEx Analyzer. Eles não são expostos e, portanto, o uso equivalente no Power BI não aplicará os mesmo filtros por padrão. |
| Valores-chave ocultos |Uma consulta do BEx pode controlar a visibilidade dos Valores-chave e aqueles que estiverem ocultos não aparecerão no SAP BEx Analyzer. Isso não é refletido pela API pública e, portanto, esses valores-chave ocultos ainda aparecerão na lista de campos. No entanto, depois eles podem ser ocultados no Power BI. |
| Formatação numérica |Nenhuma formatação numérica (número de posições decimais, ponto decimal etc.) será refletida automaticamente no Power BI. No entanto, depois é possível controlar essa formatação no Power BI. |
| Controle de versão de hierarquia |O SAP BW permite que diferentes versões de uma hierarquia sejam mantidas, por exemplo, a hierarquia de centro de custo de 2007 versus a de 2008. Somente a versão mais recente estará disponível no Power BI, uma vez que as informações sobre versões não são expostas pela API pública. |
| Hierarquias dependentes do tempo |Ao usar o Power BI, as hierarquias dependentes do tempo são avaliadas na data atual. |
| Conversão de moeda |O SAP BW dá suporte à conversão de moeda com base em taxas mantidas no cubo. Tais funcionalidades não são expostas pela API pública e, portanto, não estão disponíveis no Power BI. |
| Ordem de classificação |A ordem de classificação (por texto ou por chave) de uma característica pode ser definida no SAP. Essa ordem de classificação não é refletida no Power BI. Por exemplo, os meses podem aparecer como "Abril", "Agosto" e assim por diante. <br/> <br/> Não é possível alterar essa ordem de classificação no Power BI. |
| Nomes técnicos |Em **Obter Dados**, os nomes (descrições) de características/medidas e os nomes técnicos podem ser vistos. A lista de campos conterá apenas os nomes (descrições) das características/medidas. |
| Atributos |Não é possível acessar os atributos de uma característica no Power BI. |
| Configuração de idioma do usuário final |A localidade usada para se conectar ao SAP BW é definida como parte dos detalhes da conexão e não reflete a localidade do consumidor do relatório final. |
| Variáveis de texto |O SAP BW permite que os nomes de campos contenham espaços reservados para variáveis (por exemplo, "Dados reais de $YEAR$") que, por sua vez, seriam substituídas pelo valor selecionado. Por exemplo, o campo aparecerá como "Dados reais de 2016" em ferramentas BEx se o ano 2016 tiver sido selecionado para a variável. <br/> <br/> O nome da coluna no Power BI não será alterado dependendo do valor de variável e, portanto, será exibido como "Dados reais de $YEAR$".  No entanto, depois o nome da coluna pode ser alterado no Power BI. |
| Variáveis de saída do cliente | Essas variáveis não são expostas pela API pública e, portanto, não têm suporte no Power BI. |
| Estruturas de característica | As estruturas de característica na fonte de dados do SAP BW subjacente resultarão em uma 'explosão' de medidas sendo expostas no Power BI. Por exemplo, com duas medidas, Vendas e Custos, e uma estrutura de característica que contém Orçamento e Real, quatro medidas serão expostas: Vendas.Orçamento, Vendas.Real, Custos.Orçamento e Custos.Real. |


## <a name="next-steps"></a>Próximas etapas
Para obter mais informações sobre o DirectQuery, confira os seguintes recursos:

* [DirectQuery no Power BI](desktop-directquery-about.md)
* [Fontes de dados com suporte do DirectQuery](desktop-directquery-data-sources.md)
* [DirectQuery e SAP HANA](desktop-directquery-sap-hana.md)

