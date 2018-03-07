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
ms.date: 02/05/2018
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: cd266118fa560b3d637a85b352f8c1f03d137ec6
ms.sourcegitcommit: 88c8ba8dee4384ea7bff5cedcad67fce784d92b0
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/24/2018
---
# <a name="directquery-and-sap-hana"></a>DirectQuery e SAP HANA
Você pode se conectar a fontes de dados do **SAP HANA** diretamente usando o **DirectQuery**. Há duas opções ao se conectar ao HANA:

* **Tratar HANA como uma fonte de dados multidimensional (padrão):** atualmente em versão prévia e a nova configuração padrão. Nesse caso, o comportamento será semelhante a quando o Power BI conecta-se a outras fontes multidimensionais, como SAP Business Warehouse ou Analysis Services. Ao se conectar ao HANA usando essa configuração, um único modo de cálculo ou analítico é selecionado e todas as medidas, hierarquias e atributos dessa exibição estarão disponíveis na lista de campos. Como os visuais são criados, os dados de agregação serão sempre recuperados do HANA. Essa é a abordagem recomendada e normal.

* **Tratar HANA como uma fonte de dados relacional:** nesse caso, o Power BI trata HANA como uma fonte de dados relacional. Isso oferece maior flexibilidade, mas é importante ter cuidado para garantir que as medidas sejam agregadas conforme o esperado e para evitar problemas de desempenho.

A abordagem usada para conectar é determinada por uma opção de ferramenta global, que é configurada selecionando **Arquivo > Opções e configurações** e **Opções > DirectQuery**, em seguida, selecionando a opção  **Tratar HANA como uma fonte de dados relacional**, conforme mostrado na imagem a seguir. 

![](media/desktop-directquery-sap-hana/directquery-sap-hana_01a.png)

Observe que o **Conector do SAP HANA** está atualmente em **Versão prévia**e deve ser habilitado antes de a opção mencionada anteriormente estar visível. Para habilitar a nova experiência de visualização do SAP HANA, selecione-o em **Opções > Versão Prévia dos Recursos**, conforme mostrado na imagem a seguir.

![](media/desktop-directquery-sap-hana/directquery-sap-hana_01b.png)

A opção para tratar HANA como uma fonte de dados relacional controla a abordagem usada para as *novas* conexões criadas. Isso não tem efeito sobre as conexões existentes do HANA no relatório atual, nem nas conexões em outros relatórios que estejam abertos. Portanto, se a opção estiver atualmente desmarcada, após a adição de uma nova conexão com o HANA usando **Obter Dados**, essa conexão será feita considerando HANA uma fonte de dados multidimensional. No entanto, se um relatório diferente for aberto e que também se conectar a HANA, esse relatório continuará se comportando de acordo com a opção definida *no momento em que ele foi criado*. Isso significa que todos os relatórios que se conectam a HANA que foram criados antes de fevereiro de 2018 continuarão a tratar HANA como uma fonte de dados relacional. 

As duas abordagens constituem um comportamento muito diferente, e não é possível alternar um relatório existente de uma abordagem para a outra. 

Vamos ver cada uma dessas duas abordagens com mais detalhes, uma de cada vez.

## <a name="treat-hana-as-a-multi-dimensional-source-default"></a>Tratar HANA como uma fonte de dados multidimensional (padrão)

Este é o comportamento padrão e está atualmente em versão prévia. Para habilitar esse recurso de versão prévia, siga as etapas descritas na seção anterior para habilitar a opção de versão prévia. 

Quando o recurso de **Versão prévia** está habilitado em **Opções > Recursos de visualização** (confira a seção anterior para conhecer as etapas sobre como definir essa configuração), todas as novas conexões para o HANA usam esse método de conexão por padrão, tratando HANA como uma fonte de dados multidimensional. Para tratar uma conexão para HANA como uma fonte de dados relacional, você deverá selecionar **Arquivo > Opções e configurações** e marcar a caixa em **DirectQuery > Tratar HANA como uma fonte de dados relacional**. Embora esse recurso esteja em **Versão prévia**, os relatórios criados usando a abordagem multidimensional *não poderão* ser publicados no serviço do Power BI, e fazer isso resultará em erros quando o relatório for aberto dentro do serviço do Power BI.  

Ao se conectar ao HANA como uma fonte multidimensional, o seguinte se aplicará:

* No **Navegador de Obter Dados**, uma única exibição do HANA pode ser selecionada. Não é possível selecionar atributos ou medidas individuais. Não há nenhuma consulta definida no momento da conexão, que é diferente de importar dados ou ao usar o DirectQuery ao tratar HANA como uma fonte de dados relacional. Isso também significa que não é possível usar uma consulta SQL de HANA diretamente ao selecionar esse método de conexão.

* Todas as medidas, hierarquias e atributos do modo de exibição selecionado serão exibidos na lista de campos. 

* Como uma medida é usada em um elemento visual, o HANA será consultado para recuperar o valor da medida no nível de agregação necessário para o elemento visual. Portanto, ao lidar com medidas não aditivas (contadores, proporção e assim por diante) todas as agregações serão executadas pelo HANA e nenhuma outra agregação será executada pelo Power BI. 

* Para garantir que os valores de agregação corretos sempre possam ser obtidos do HANA, determinadas restrições deverão ser impostas. Por exemplo, não é possível adicionar colunas calculadas ou combinar dados de vários modos de exibição do HANA dentro do mesmo relatório. 

Tratar HANA como uma fonte multidimensional não oferece uma flexibilidade maior do que a fornecida pela abordagem *relacional* alternativa, mas é mais simples e garante valores de agregação corretos ao lidar com medidas do HANA mais complexas, além de geralmente resultar em um melhor desempenho. 

A lista **Campo** incluirá todas as medidas, atributos e hierarquias da exibição do HANA. Observe os comportamentos a seguir que são aplicados ao usar esse método de conexão:

* Qualquer atributo que estiver incluído em pelo menos uma hierarquia ficará oculto por padrão. No entanto, eles podem ser vistos se necessário, selecionando **Exibir oculto** do menu de contexto na lista de campos. No mesmo menu de contexto, eles podem ficar visíveis, se isso for necessário.

* No HANA, um atributo pode ser definido para usar outro atributo como seu rótulo. Por exemplo, **Produto** (com valores 1,2,3 e assim por diante) pode usar **ProductName** (com os valores Bicicleta,Camisa,Luvas e assim por diante) como seu rótulo. Nesse caso, um campo único **Produto** será mostrado na lista de campos, cujos valores serão os rótulos de Bicicleta,Camisa,Luvas e assim por diante, mas que será classificado por e com a exclusividade determinada pelos valores de chave 1,2,3. Uma coluna oculta **Product.Key** também é criada, permitindo o acesso aos valores de chave subjacentes se for necessário. 

Todas as variáveis definidas no HANA subjacente serão exibidas no momento da conexão e os valores necessários poderão ser inseridos. Esses valores podem ser alterados posteriormente selecionando **Editar Consultas** na faixa de opções e **Editar Variáveis** no menu suspenso exibido. 

As operações de modelagem permitidas são mais restritivas do que em geral ao usar o DirectQuery, devido à necessidade de garantir que os dados de agregação corretos sempre possam ser obtidos do HANA. No entanto, é possível fazer várias adições e alterações, incluindo a definição de medidas, renomeação e ocultação de campos e definição de formatos de exibição. Todas essas mudanças serão preservadas na atualização e as alterações não conflitantes feitas ao modo de exibição do HANA serão aplicadas. 

### <a name="additional-modelling-restrictions"></a>Restrições de modelagem adicionais

As principais restrições de modelagem adicionais ao se conectar ao SAP HANA usando o DirectQuery (trate como uma fonte de dados multidimensional) são as seguintes: 

* **Não há suporte para colunas calculadas:** a capacidade de criar colunas calculadas fica desabilitada. Isso também significa que o Agrupamento e o Clustering, que criam colunas calculadas, não estão disponíveis.
* **Limitações adicionais para medidas:** há limitações adicionais impostas sobre as expressões DAX que podem ser usadas em medidas para refletir o nível de suporte oferecido pelo SAP HANA.
* **Sem suporte para definição de relações:** apenas uma única exibição pode ser consultada dentro de um relatório e, dessa forma, não há suporte para definição de relações.
* **Não há Exibição de Dados:** a **Exibição de Dados** normalmente exibe dados com nível de detalhe nas tabelas. Dada a natureza das fontes de OLAP como o SAP HANA, essa exibição não está disponível com o SAP HANA.
* **Os detalhes das colunas e das medidas são fixos:** a lista de colunas e medidas vistas na lista de campos são fixas segundo a fonte subjacente e não podem ser modificadas. Por exemplo, não é possível excluir uma coluna ou alterar seu tipo de dados (no entanto, é possível renomeá-la).
* **Limitações adicionais no DAX:** há limitações adicionais no DAX que podem ser usadas em definições de medida para refletir as limitações na fonte. Por exemplo, não é possível usar uma função de agregação em uma tabela.

### <a name="additional-visualization-restrictions"></a>Restrições de visualização adicionais

Há algumas restrições nos elementos visuais ao se conectar ao SAP HANA usando o DirectQuery (trate como fonte de dados multidimensional): 
* **Não há agregação de colunas:** não é possível alterar a agregação para uma coluna em um visual; ela sempre é *Não Resumir*.

## <a name="treat-hana-as-a-relational-source"></a>Tratar HANA como uma fonte de dados relacional 

Ao escolher essa opção para se conectar ao HANA como uma fonte de dados relacional, outras flexibilidades adicionais ficam disponíveis. Por exemplo, você pode criar colunas calculadas, incluir dados de vários modos de exibição do HANA e criar relações entre as tabelas resultantes. No entanto, ao usar o SAP HANA dessa maneira, é importante entender determinados aspectos de como as conexões são tratadas, para garantir o seguinte: 

* os resultados correspondam ao esperado quando o modo de exibição do SAP HANA contiver medidas não aditivas (por exemplo, contagens distintas ou médias, em vez de somas simples).
* as consultas resultantes sejam eficientes

É útil começar esclarecendo o comportamento de uma fonte relacional, como um SQL Server, quando a consulta definida em **Obter Dados** ou no **Editor de Consultas** executar uma agregação. No exemplo a seguir, uma consulta definida no **Editor de Consultas** retorna o preço médio segundo o *ProductID*.  

![](media/desktop-directquery-sap-hana/directquery-sap-hana_01.png)

Se os dados estiverem sendo importados para o Power BI (em vez de usar o DirectQuery), aconteceria o seguinte:

* Os dados são importados no nível de agregação definido pela consulta criada no **Editor de Consultas**. Por exemplo, preço médio por produto. Isso resulta em uma tabela com duas colunas, *ProductID* e *AveragePrice*, que podem ser usadas em visuais.
* Em um visual, qualquer agregação subsequente (como *Sum*, *Average*, *Min*, entre outras) é executada nos dados importados. Por exemplo, incluir *AveragePrice* em um visual usará a agregação *Sum* por padrão e retornará a soma de *AveragePrice* para cada *ProductID* – que nesse caso de exemplo seria 13,67. O mesmo se aplica a qualquer função de agregação alternativa (como *Min*, *Average* etc) usada no visual. Por exemplo, *Average* de *AveragePrice* retorna a média de 6,66, 4 e 3, que é igual a 4,56 e não a média de *Price* nos 6 registros na tabela subjacente, que é 5,17.
  
Se o **DirectQuery** (nessa mesma fonte relacional) estiver sendo usado em vez da Importação, a mesma semântica se aplica e os resultados seriam exatamente os mesmos:  

* Considerando a mesma consulta, logicamente os mesmos dados seriam apresentados para a camada de relatório, embora os dados não tenham sido de fato importados.

* Em um visual, qualquer agregação subsequente (*Sum*, *Average*, *Min*, entre outras) é executada mais uma vez na tabela lógica da consulta. E mais uma vez, um visual contendo *Average* de *AveragePrice* retornará o mesmo valor de 4,56.
  
Agora vamos considerar SAP HANA, quando a conexão é tratada como uma fonte relacional. O Power BI pode trabalhar com *Exibições Analíticas* e *Exibições de Cálculo* no SAP HANA, que podem conter medidas. Ainda hoje a abordagem do SAP HANA segue os mesmos princípios descritos anteriormente nesta seção: a consulta definida em **Obter Dados** ou no **Editor de Consultas** determinará os dados disponíveis e qualquer agregação subsequente em um visual será feita nos dados e o mesmo se aplica à Importação e ao DirectQuery.  
No entanto, devido à natureza do HANA, a consulta definida na caixa de diálogo inicial de **Obter Dados** ou do **Editor de Consultas** sempre é uma consulta de agregação e geralmente inclui medidas em que a agregação real que será usada é definida pela exibição do HANA.

O equivalente do exemplo do SQL Server acima é que há uma exibição do HANA contendo *ID*, *ProductID*, *DepotID* e medidas incluindo *AveragePrice*, definida no modo de exibição como *Média do Preço*.  
    
Se, na experiência **Obter Dados**, tiverem sido feitas seleções de **ProductID** e da medida **AveragePrice**, isso define uma consulta no modo de exibição, solicitando esses dados agregados (no exemplo anterior, para manter a simplicidade, é usado um pseudo-SQL, que não coincide exatamente com a sintaxe do HANA SQL). Em seguida, agregações adicionais definidas em um visual agregam ainda mais os resultados de tal consulta. Novamente, conforme descrito acima para o SQL Server, isso se aplica tanto ao caso da Importação quanto ao DirectQuery. Observe que no caso do DirectQuery, a consulta de **Obter Dados** ou do **Editor de Consultas** será usada em uma subseleção dentro de uma única consulta enviada ao HANA e, portanto, não se trata de um caso em que todos os dados seriam lidos antes de serem ainda mais agregados.  

Todas essas considerações e comportamentos exigem as seguintes considerações importantes ao usar o DirectQuery no HANA:  

* é necessário prestar atenção a qualquer outra agregação executada nos visuais, sempre que a medida no HANA for não aditiva (por exemplo, não for um simples *Sum*, *Min* ou *Max*).

* Em **Obter Dados** ou no **Editor de Consultas**, somente as colunas obrigatórias devem ser incluídas para recuperar os dados necessários, refletindo o fato de que o resultado será uma consulta, que deverá ser uma consulta razoável que possa ser enviada ao HANA. Por exemplo, se dezenas de colunas tiverem sido selecionadas, com a ideia de que elas poderão ser necessárias em visuais posteriores, então até mesmo para o DirectQuery um visual simples significará que a consulta de agregação usada na subseleção conterá essas dezenas de colunas, o que geralmente levará a um desempenho muito ruim.
  
Vejamos um exemplo. No exemplo a seguir, selecionar cinco colunas (**CalendarQuarter**, **Color**, **LastName**, **ProductLine**, **SalesOrderNumber**) na caixa de diálogo **Obter Dados**, junto com a medida *OrderQuantity*, significa que, mais tarde, a criação de um visual simples contendo Min OrderQuantity resultará na seguinte consulta SQL para o HANA. O sombreado é a subseleção, contendo a consulta de **Obter Dados** / **Editor de Consultas**. Se essa subseleção levar a um resultado com cardinalidade muito alta, é provável que o desempenho resultando do HANA seja ruim.  

![](media/desktop-directquery-sap-hana/directquery-sap-hana_03.png)

   
Por causa deste comportamento, recomendamos que os itens selecionados em **Obter Dados** ou no **Editor de Consultas** sejam limitados aos itens que são necessárias, ainda assim resultando em uma consulta razoável para o HANA.  

## <a name="best-practices"></a>Práticas recomendadas 

Para ambas as abordagens para se conectar ao SAP HANA, as recomendações para usar o DirectQuery também se aplicam ao HANA, especialmente as relacionadas a garantir o bom desempenho. Essas recomendações estão descritas detalhadamente no artigo [Usando o DirectQuery no Power BI](desktop-directquery-about.md).
   
## <a name="limitations"></a>Limitações

A lista a seguir descreve todos os recursos do SAP HANA que não têm suporte completo ou recursos que têm comportamento diferente ao usar o Power BI. 

* **Hierarquias de pai/filho** – hierarquias pai/filho não estarão visíveis no Power BI.
Isso ocorre porque o Power BI acessa o HANA usando a interface do SQL e as hierarquias de pai/filho não podem ser totalmente acessadas por meio do SQL.
* **Outros metadados de hierarquia** – a estrutura básica das hierarquias é exibida no Power BI; no entanto, alguns metadados de hierarquia (como controlar o comportamento de hierarquias desbalanceadas) não terão efeito.
Novamente, isso é devido a limitações impostas pela interface do SQL.
* **Conexão usando SSL** – você não pode se conectar a instâncias do SAP HANA configuradas para usar SSL.
O suporte para modos de exibição de atributo do Power BI pode se conectar aos modos de exibição analítico e cálculo, mas não pode se conectar diretamente aos modos de exibição de atributo.
* **Suporte para objetos de catálogo** – o Power BI não pode se conectar aos objetos de catálogo.
* **Alterar para variáveis após publicar** – você não pode alterar os valores para as variáveis do HANA diretamente no serviço do Power BI, após o relatório ser publicado. 
 
## <a name="known-issues"></a>Problemas conhecidos 
A lista a seguir descreve todos os problemas conhecidos ao se conectar ao SAP HANA (DirectQuery) usando o Power BI. 

* **Problema do HANA ao consultar contadores e outras medidas** – dados incorretos são retornados do HANA se estiver conectando a uma exibição analítica e uma medida de contador e algumas outras medidas de proporção, e estão incluídos no mesmo elemento visual. Isso é abordado pela observação 2128928 do SAP (resultados inesperados ao consultar uma coluna calculada e um contador). A medida de proporção estará incorreta nesse caso. 

* **Várias colunas do Power BI de coluna única do HANA** – para alguns modos de exibição de cálculo, onde uma coluna do HANA é usada em mais de uma hierarquia, o HANA expõe isso como dois atributos separados. Isso resulta em duas colunas que estão sendo criadas no Power BI.  No entanto, essas colunas estão ocultos por padrão e todas as consultas que envolvem hierarquias ou as colunas diretamente comportam-se corretamente. 
 
## <a name="next-steps"></a>Próximas etapas

Para obter mais informações sobre o DirectQuery, confira os seguintes recursos:

* [DirectQuery no Power BI](desktop-directquery-about.md)
* [Fontes de dados com suporte do DirectQuery](desktop-directquery-data-sources.md)
* [DirectQuery e SAP BW](desktop-directquery-sap-bw.md)
* [Gateway de dados local](service-gateway-onprem.md)

