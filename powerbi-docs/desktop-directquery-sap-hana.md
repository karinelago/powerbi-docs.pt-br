---
title: DirectQuery para SAP HANA no Power BI
description: "Considerações ao usar o DirectQuery com SAP HANA"
services: powerbi
documentationcenter: 
author: davidiseminger
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
ms.date: 10/12/2017
ms.author: davidi
ms.openlocfilehash: d6f863df59d7374c792f1e1ac16db3a04ad99d87
ms.sourcegitcommit: 284b09d579d601e754a05fba2a4025723724f8eb
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/15/2017
---
# <a name="directquery-and-sap-hana"></a>DirectQuery e SAP HANA
Você pode se conectar a fontes de dados do **SAP HANA** diretamente usando o **DirectQuery**.

Ao usar o **SAP HANA**, é importante entender alguns aspectos de como as conexões com ele são tratadas, para garantir que:

* os resultados correspondam ao esperado quando o modo de exibição do SAP HANA contiver medidas não aditivas (por exemplo, contagens distintas ou médias, em vez de somas simples)
* as consultas resultantes sejam eficientes

É útil começar reservando um momento para esclarecer o comportamento de uma fonte relacional, como um **SQL Server**, quando a consulta definida em **Obter Dados** ou no **Editor de Consultas** executar uma agregação. No exemplo a seguir, uma consulta definida no **Editor de Consultas** retorna o preço médio segundo o **ProductID**.

![](media/desktop-directquery-sap-hana/directquery-sap-hana_01.png)

Se os dados estiverem sendo importados para o Power BI (em vez de usar o DirectQuery), aconteceria o seguinte:

* Os dados são importados no nível de agregação definido pela consulta criada no **Editor de Consultas**. Por exemplo, preço médio por produto. Isso resulta em uma tabela com duas colunas, *ProductID* e *AveragePrice*, que podem ser usadas em visuais.
* Em um visual, qualquer agregação subsequente (como *Sum*, *Average*, *Min*, entre outras) é executada nos dados importados.  Por exemplo, incluir *AveragePrice* em um visual usará a agregação *Sum* por padrão e retornará a soma de *AveragePrice* para cada *ProductID* – que nesse caso seria 13,67. O mesmo se aplica a qualquer função de agregação alternativa (como *Min*, *Average* etc) usada no visual. Por exemplo, *Average* de *AveragePrice* retorna a média de 6,66, 4 e 3, que é igual a 4,56 e *não* a média de *Price* nos 6 registros na tabela subjacente, que é 5,17.

Se o **DirectQuery** estiver sendo usado em vez da Importação, a mesma semântica se aplica e os resultados seriam exatamente os mesmos:

* Considerando a mesma consulta, logicamente os mesmos dados seriam apresentados para a camada de relatório, embora os dados não tenham sido de fato importados.
* Em um visual, qualquer agregação subsequente (*Sum*, *Average*, *Min*, entre outras) é executada mais uma vez na tabela lógica da consulta. E mais uma vez, um visual contendo *Average* de *AveragePrice* retornará o mesmo valor de 4,56.

Agora, vamos considerar o **SAP HANA**. O Power BI pode trabalhar com *Exibições Analíticas* e *Exibições de Cálculo* no SAP HANA, que podem conter medidas. Ainda hoje a abordagem do SAP HANA segue os mesmos princípios descritos anteriormente: a consulta definida em **Obter Dados** ou no **Editor de Consultas** determinará os dados disponíveis e, em seguida, qualquer agregação subsequente em um visual será feita nos dados e o mesmo se aplica à Importação e ao DirectQuery.

No entanto, devido à natureza do HANA, a consulta definida na caixa de diálogo inicial de **Obter Dados** ou do **Editor de Consultas** sempre é uma consulta de agregação e geralmente inclui medidas em que a agregação real que será usada é definida pela exibição do HANA.

O equivalente do exemplo do SQL Server acima é que há uma exibição do HANA contendo **ID**, **ProductID**, **DepotID** e medidas incluindo **AveragePrice**, definida no modo de exibição como **Média do Preço**.

![](media/desktop-directquery-sap-hana/directquery-sap-hana_02.png)

Se, na experiência **Obter Dados**, tiverem sido feitas seleções de **ProductID** e da medida **AveragePrice**, isso define uma consulta no modo de exibição, solicitando esses dados agregados (no exemplo acima, para manter a simplicidade, ~e usado um pseudo-SQL, que não coincide exatamente com a sintaxe do HANA SQL). Em seguida, agregações adicionais definidas em um visual agregam ainda mais os resultados de tal consulta. Novamente, conforme descrito acima para o **SQL Server**, isso se aplica tanto ao caso da Importação quanto ao DirectQuery. Observe que no caso do DirectQuery, a consulta de **Obter Dados** ou do **Editor de Consultas** será usada em uma subseleção dentro de uma única consulta enviada ao HANA e, portanto, não se trata de um caso em que todos os dados seriam lidos antes de serem ainda mais agregados.

Isso leva às seguintes considerações importantes quanto ao uso do DirectQuery no HANA:

* é necessário prestar atenção a qualquer outra agregação executada nos visuais, sempre que a medida no HANA for não aditiva (por exemplo, não for um simples *Sum*, *Min* ou *Max*).
* Em **Obter Dados** ou no **Editor de Consultas**, somente as colunas obrigatórias devem ser incluídas para recuperar os dados necessários, refletindo o fato de que o resultado será uma consulta, que deverá ser uma consulta razoável que possa ser enviada ao HANA. Por exemplo, se dezenas de colunas tiverem sido selecionadas, com a ideia de que elas poderão ser necessárias em visuais posteriores, então até mesmo para o DirectQuery um visual simples significará que a consulta de agregação usada na subseleção conterá essas dezenas de colunas, o que geralmente levará a um desempenho muito ruim.

Vejamos um exemplo. No exemplo a seguir, selecionar cinco colunas (CalendarQuarter, Color, LastName, ProductLine, SalesOrderNumber) na caixa de diálogo **Obter Dados**, junto com a medida OrderQuantity, significa que, mais tarde, a criação de um visual simples contendo Min OrderQuantity resultará na seguinte consulta SQL para o HANA. A parte sombreada é a subseleção, contendo a consulta de **Obter Dados** / **Editor de Consultas**. Se essa subseleção levar a um resultado com cardinalidade muito alta, é provável que o desempenho resultando do HANA seja ruim.

![](media/desktop-directquery-sap-hana/directquery-sap-hana_03.png)

Por isso, é recomendável que os itens selecionados em **Obter Dados** ou no **Editor de Consultas** sejam limitados aos itens que são necessárias, ainda assim resultando em uma consulta razoável para o HANA.

### <a name="next-steps"></a>Próximas etapas
Para obter mais informações sobre o DirectQuery, confira os seguintes recursos:

* [DirectQuery no Power BI](desktop-directquery-about.md)
* [Fontes de dados com suporte do DirectQuery](desktop-directquery-data-sources.md)
* [DirectQuery e SAP BW](desktop-directquery-sap-bw.md)
* [Gateway de dados local](service-gateway-onprem.md)

