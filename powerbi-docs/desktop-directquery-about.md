---
title: Usando o DirectQuery no Power BI
description: Entender o uso do DirectQuery com o Power BI
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
ms.date: 01/24/2018
ms.author: davidi
ms.openlocfilehash: 0d6d66016663ed0e12d8f3da854ec1e9f7da7eae
ms.sourcegitcommit: 7249ff35c73adc2d25f2e12bc0147afa1f31c232
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/25/2018
---
# <a name="using-directquery-in-power-bi"></a>Usando o DirectQuery no Power BI
Você pode conectar-se a todos os tipos de fontes de dados diferentes ao usar o **Power BI Desktop** ou o **serviço do Power BI**, e você pode fazer essas conexões de dados de maneiras diferentes. Você pode *importar* dados ao Power BI, que é a maneira mais comum de se obter dados ou pode se conectar diretamente aos dados em seu repositório fonte original, o que é conhecido como **DirectQuery**. Este artigo descreve o **DirectQuery** e seus recursos, incluindo os seguintes tópicos:

* Diferentes opções de conectividade para o DirectQuery
* Orientação para quando você deve considerar o uso do DirectQuery em vez da importação
* Desvantagens do uso do DirectQuery
* Melhor prática para o uso do DirectQuery

Em resumo, a melhor prática para o uso da importação em vez do DirectQuery é a seguinte:

* Você deve **importar** dados ao Power BI sempre que possível. Isso aproveita o mecanismo de consulta de alto desempenho do Power BI e proporciona uma experiência altamente interativa e cheia de recursos sobre seus dados.
* Se suas metas não puderem ser atendidas com a importação de dados, considere o uso do **DirectQuery**. Por exemplo, se os dados estão frequentemente em alteração e os relatórios devem refletir os dados mais recentes, o DirectQuery pode ser a melhor opção. No entanto, o uso do DirectQuery geralmente só será possível quando a fonte de dados subjacente puder fornecer consultas interativas (menos de 5 segundos) para a consulta típica de agregação e for capaz de lidar com o carregamento de consulta que será gerada. Além disso, a lista de limitações que acompanham o uso do DirectQuery deverá ser considerada com cuidado para garantir que suas metas ainda possam ser atendidas.

O conjunto de recursos oferecidos pelo Power BI para ambos os modos de conectividade – importação e DirectQuery – evoluirá ao longo do tempo. Isso incluirá o fornecimento de mais flexibilidade ao usar dados importados, de maneira que a importação possa ser usada em mais casos, bem como a eliminação de algumas das desvantagens do uso do DirectQuery. Independentemente das melhorias, ao usar o DirectQuery o desempenho da fonte de dados subjacente sempre será uma consideração importante. Se essa fonte de dados subjacente estiver lenta, o uso do DirectQuery para essa fonte ficará impraticável.

Este tópico aborda o DirectQuery com o Power BI e não o SQL Server Analysis Services. O DirectQuery também é um recurso do **SQL Server Analysis Services** e muitos dos detalhes descritos abaixo se aplicam ao seu uso, mas também há diferenças importantes. Para obter informações sobre o uso do DirectQuery com o SQL Server Analysis Services, consulte [o white paper que fornece detalhes sobre o DirectQuery no SQL Server Analysis Services 2016](http://download.microsoft.com/download/F/6/F/F6FBC1FC-F956-49A1-80CD-2941C3B6E417/DirectQuery%20in%20Analysis%20Services%20-%20Whitepaper.pdf).  

Este artigo concentra-se no fluxo de trabalho recomendado para o DirectQuery, em que o relatório é criado no **Power BI Desktop**, mas também abrange a conexão diretamente no **serviço do Power BI**.

## <a name="power-bi-connectivity-modes"></a>Modos de conectividade do Power BI
O Power BI se conecta a um número muito grande de fontes de dados diferentes, abrangendo:

* Serviços online (Salesforce, Dynamics 365 e outros)
* Bancos de dados (SQL Server, Access, Amazon Redshift e outros)
* Arquivos simples (Excel, JSON e outros)
* Outras fontes de dados (Spark, sites, Microsoft Exchange e outros)

Para essas fontes, geralmente é possível importar os dados no Power BI. Para algumas delas também é possível conectar-se usando o DirectQuery. O conjunto exato de fontes que dá suporte ao DirectQuery está descrito no artigo [Fontes de dados com suporte pelo DirectQuery](desktop-directquery-data-sources.md). Mais fontes serão habilitadas para o DirectQuery no futuro, concentrando-se principalmente em fontes que possam proporcionar um bom desempenho de consulta interativa.

O **SQL Server Analysis Services** é um caso especial. Ao se conectar ao SQL Server Analysis Services, você poderá optar por importar os dados ou usar uma *conexão dinâmica*.  O uso de uma conexão dinâmica é semelhante ao DirectQuery, em que nenhum dado é importado e a fonte de dados subjacente é sempre consultada para atualizar um visual, mas uma *conexão dinâmica* é diferente em muitos outros aspectos, portanto, um termo diferente (*dinâmica* versus *DirectQuery*) é usado.

Essas três opções para conectar-se aos dados – **importação**, **DirectQuery** e **conexão dinâmica** – serão explicadas em detalhes nas seções a seguir.

### <a name="import-connections"></a>Conexões de importação
Ao usar **Obter Dados** no **Power BI Desktop** para se conectar a uma fonte de dados como o SQL Server e você escolher **Importação**, o comportamento dessa conexão será da seguinte maneira:

* Durante a experiência **Obter Dados** inicial, cada conjunto de tabelas selecionadas definirá uma consulta que retornará um conjunto de dados (essas consultas podem ser editadas antes de carregar os dados, por exemplo, para aplicar filtros, agregar os dados ou unir tabelas diferentes).
* Após o carregamento, todos os dados definidos por essas consultas serão importados para o cache do Power BI.
* Com a criação de um visual no **Power BI Desktop**, os dados importados serão consultados. O repositório do Power BI garantirá que a consulta seja muito rápida e, assim, todas as alterações no visual serão refletidas imediatamente.
* As alterações nos dados subjacentes não serão refletidas em nenhum visual. É necessário *Atualizar*, momento em que os dados serão importados novamente.
* Após a publicação do relatório (o arquivo .pbix) no **serviço do Power BI**, um conjunto de dados é criado e carregado no serviço do Power BI.  Os dados importados são incluídos no conjunto de dados. Em seguida, é possível configurar a atualização agendada desses dados, por exemplo, para importar os dados novamente todos os dias. Dependendo da localização da fonte de dados original, poderá ser necessário configurar um gateway de dados local.
* Ao abrir um relatório existente no **serviço do Power BI** ou criar um novo relatório, os dados importados serão consultados novamente, garantindo a interatividade.
* Páginas inteiras de relatório ou visuais podem ser fixadas como blocos de dashboard. Os blocos serão atualizados automaticamente sempre que o conjunto de dados subjacente for atualizado.  

### <a name="directquery-connections"></a>Conexões do DirectQuery
Ao usar **Obter Dados** no **Power BI Desktop** para se conectar a uma fonte de dados e você escolher **DirectQuery**, o comportamento dessa conexão será da seguinte maneira:

* Durante a experiência **Obter Dados** inicial, a fonte é selecionada. Para fontes relacionais, isso significa que um conjunto de tabelas é selecionado e cada uma ainda define uma consulta que retorna um conjunto de dados de forma lógica. Para fontes multidimensionais, como SAP BW, somente a fonte é selecionada.
* No entanto, após o carregamento, os dados não serão realmente importados no repositório do Power BI. Em vez disso, após a criação de um visual no **Power BI Desktop**, as consultas serão enviadas à fonte de dados subjacente para recuperar os dados necessários. Dessa forma, o tempo levado para atualizar o visual dependerá do desempenho da fonte de dados subjacente.
* As alterações nos dados subjacentes não serão imediatamente refletidas em nenhum visual existente. Ainda será preciso Atualizar, momento em que as consultas necessárias serão reenviadas para cada visual e o visual será atualizado conforme a necessidade.
* Com a publicação do relatório no **serviço do Power BI**, isso resultará novamente em um Conjunto de dados no serviço do Power BI, assim como acontece na importação. No entanto, *nenhum dado* será incluído nesse conjunto de dados.
* Ao abrir um relatório existente no **serviço do Power BI** ou criar um novo relatório, a fonte de dados subjacente será novamente consultada para recuperar os dados necessários. Dependendo da localização da fonte de dados original, poderá ser necessário configurar um gateway de dados local, assim como é necessário para o modo de Importação caso os dados sejam atualizados.
* Páginas inteiras de relatório ou visuais podem ser fixadas como blocos de Dashboard. Para garantir que a abertura de um dashboard seja rápida, os blocos são atualizados automaticamente em um agendamento (por exemplo, a cada hora). A frequência dessa atualização pode ser controlada para refletir a frequência com que os dados são alterados e qual a importância de se ver os dados mais recentes. Assim, ao abrir um dashboard, os blocos refletirão os dados de acordo com o momento da última atualização e não necessariamente as alterações mais recentes feitas na fonte subjacente. Um dashboard aberto sempre poderá ser atualizado para garantir que os dados mais recentes sejam exibidos.    

### <a name="live-connections"></a>Conexões dinâmicas
Ao se conectar ao **SSAS** (SQL Server Analysis Services), há uma opção para importar dados ou conectar-se dinamicamente ao modelo de dados selecionado. Se você selecionar **importação**, isso definirá uma consulta em relação a essa fonte externa do SSAS e os dados serão importados normalmente. Se você optar por **conectar-se dinamicamente**, não haverá nenhuma consulta definida e todo o modelo externo será mostrado na lista de campos. Se você selecionar **DirectQuery**, as consultas serão enviadas para a fonte externa do SSAS enquanto os visuais estiverem sendo criados. No entanto, ao contrário do DirectQuery, isso não faz sentido na criação de um novo *modelo*; em outras palavras, não é possível definir novas colunas calculadas, hierarquias, relações e assim por diante. Em vez disso, você está simplesmente se conectando diretamente ao modelo SSAS externo.

A situação descrita no parágrafo anterior aplica-se à conexão com as seguintes fontes, exceto que não há nenhuma opção para importar os dados:

* Conjuntos de dados do Power BI (por exemplo, ao se conectar a um conjunto de dados do Power BI que foi criado anteriormente e publicado no serviço, com a finalidade de criar um novo relatório com base nele)
* Common Data Services

O comportamento de relatórios com base em SSAS, após a publicação no **serviço do Power BI**, é semelhante aos relatórios do DirectQuery das seguintes maneiras:

* Ao abrir um relatório existente no **serviço do Power BI** ou criar um novo relatório, a fonte subjacente do SSAS será consultada (possivelmente exigindo um gateway de dados local)
* Os blocos de dashboard serão atualizados automaticamente de acordo com um agendamento (como a cada hora ou qualquer frequência que seja definida)

No entanto, também há diferenças importantes, incluindo que, para conexões dinâmicas, a identidade do usuário que abre o relatório sempre será passada para a fonte de dados subjacente do SSAS.

Deixando essas comparações de lado, vamos nos concentrar apenas no **DirectQuery** no restante deste artigo.

## <a name="when-is-directquery-useful"></a>Quando o DirectQuery é útil?
A tabela a seguir descreve cenários nos quais se conectar com o DirectQuery poderia ser especialmente útil, inclusive casos em que manter os dados na fonte original seria considerado benéfico. A descrição inclui uma discussão sobre a disponibilidade do cenário especificado no Power BI.

| Limitação | Descrição |
| --- | --- |
| Dados com alterações frequentes e a necessidade de relatórios quase que "em tempo real" |Os modelos com os dados importados podem ser atualizados, no máximo, uma vez a cada hora. Portanto, se os dados estiverem continuamente em alteração e for necessário que os relatórios mostrem os dados mais recentes, o uso da Importação com a atualização agendada poderá simplesmente não atender a essas necessidades. Observe também que é possível transmitir os dados diretamente para o Power BI, apesar da existência de limites de suporte aos volumes de dados nesse caso. <br/> <br/> Com o uso do DirectQuery, por outro lado, abrir ou atualizar um relatório ou dashboard sempre mostrará os dados mais recentes da fonte. Além disso, os blocos de dashboard podem ser atualizados com mais frequência (tão frequentemente quanto a cada 15 minutos). |
| Os dados são muito grandes |Se os dados forem muito grandes, certamente não será possível importá-los em sua totalidade. O DirectQuery, por outro lado, não exige grande transferência de dados, pois ele é consultado no local. <br/> <br/> No entanto, dados grandes poderiam indicar também que o desempenho das consultas nessa fonte subjacente seria muito lento (como discutido na seção *Implicações do uso do DirectQuery* mais adiante neste artigo). Além disso, é claro que nem sempre é necessário importar a totalidade dos dados detalhados. Em vez disso, os dados podem ser agregados previamente durante a importação (e o **Editor de Consultas** serve justamente para facilitar esse processo). Em última análise, seria possível importar exatamente os dados de agregação necessários para cada visual. Assim, embora o DirectQuery seja a abordagem mais simples para dados grandes, você deve sempre ter em mente que a importação de dados agregados poderá oferecer uma solução, caso a fonte subjacente esteja muito lenta. |
| Regras de segurança são definidas na fonte subjacente |Para a importação dos dados, o Power BI se conectará à fonte de dados usando as credenciais atuais do usuário (no Power BI Desktop) ou as credenciais definidas como parte da configuração da atualização agendada (no serviço do Power BI). Assim, na publicação e compartilhamento desse relatório, deverá haver cuidado para que o compartilhamento seja feito somente com usuários com permissão para ver os mesmos dados ou para definir a Segurança em Nível de Linha como parte desse conjunto de dados. <br/> <br/> Idealmente, como o DirectQuery sempre consulta a fonte subjacente, isso permitiria que qualquer segurança nessa fonte subjacente fosse aplicada. No entanto, atualmente o Power BI sempre se conectará com a fonte subjacente usando as mesmas credenciais que seriam usadas para a importação. <br/> <br/> Assim, até que o Power BI permita que a identidade do consumidor do relatório seja transmitida para a fonte subjacente, o DirectQuery não oferece nenhuma vantagem em relação a segurança da fonte de dados. |
| Houver aplicação de restrições de soberania de dados |Algumas organizações têm políticas de soberania de dados, resultando na impossibilidade de que os dados deixem o local da organização. Uma solução baseada na importação claramente apresentaria problemas. Por outro lado, com o DirectQuery os dados permanecem na fonte subjacente. <br/> <br/> No entanto, deve-se observar que, mesmo com o DirectQuery, alguns caches de dados no nível do visual são mantidos no serviço do Power BI (devido a atualização agendada dos blocos). |
| A fonte de dados subjacente é uma fonte OLAP contendo medidas |Se a fonte de dados contiver *medidas *(como SAP HANA ou SAP Business Warehouse), a importação dos dados ocasionará outros problemas. Isso significa que os dados importados estão em um determinado nível de agregação, conforme definido pela consulta. Por exemplo, tomemos a medida TotalSales por Classe, Ano e Cidade. Nesse caso, se um visual for criado com solicitação de dados em um nível mais alto de agregação (como TotalSales por Ano), haverá uma agregação adicional do valor agregado. Isso é tranquilo no caso de medidas aditivas (como Sum, Min), mas é um problema para medidas não aditivas (como Average, DistinctCount). <br/> <br/> Para facilitar a obtenção dos dados de agregação corretos diretamente da fonte (conforme a necessidade de um visual específico), seria necessário enviar consultas por visual, como no DirectQuery. <br/> <br/> Ao conectar-se com o SAP BW (Business Warehouse), a escolha do DirectQuery permite esse tratamento das medidas. O suporte ao SAP BW é abordado mais detalhadamente em [DirectQuery e SAP BW](desktop-directquery-sap-bw.md). <br/> <br/> No entanto, atualmente o DirectQuery trata o SAP HANA como uma fonte relacional e, portanto, fornecerá um comportamento semelhante à importação. Isso é abordado mais detalhadamente em [DirectQuery e SAP HANA](desktop-directquery-sap-hana.md). |

Portanto, em resumo, considerando os recursos atuais do DirectQuery no Power BI, os cenários em que ele oferece benefícios são os seguintes:

* Dados com alterações frequentes e a necessidade de relatórios quase que "em tempo real"
* Manipulação de dados muito grandes, sem a necessidade de agregação prévia
* Houver aplicação de restrições de soberania de dados
* A fonte é multidimensional contendo medidas (como o SAP BW)

Observe que os detalhes na lista anterior são relacionados com o uso somente do Power BI. Em vez disso, sempre há a opção de usar um modelo externo do SQL Server Analysis Services (ou do Azure Analysis Services) para importar dados e, em seguida, usar o Power BI para se conectar a esse modelo. Embora essa abordagem exija habilidades adicionais, ela oferece maior flexibilidade. Por exemplo, volumes muito maiores de dados podem ser importados e não há nenhuma restrição na frequência com que os dados podem ser atualizados.

## <a name="implications-of-using-directquery"></a>Implicações do uso do DirectQuery
O uso do **DirectQuery** tem implicações potencialmente negativas, conforme detalhado nesta seção. Algumas dessas limitações são ligeiramente diferentes de acordo com a fonte exata que está sendo usada. Isso será indicado sempre que aplicável e tópicos separados abordarão as fontes que são significativamente diferentes.  

### <a name="performance-and-load-on-the-underlying-source"></a>Desempenho e carregamento na fonte subjacente
Ao usar o **DirectQuery**, a experiência geral dependerá muito do desempenho da fonte de dados subjacente. Se a atualização de cada visual (por exemplo, depois de alterar um valor de segmentação de dados) demorasse alguns segundos (< 5s), a experiência seria razoável, ainda que fosse um pouco morosa em comparação com a resposta imediata que estamos acostumados ao importar os dados no Power BI. Se, em vez disso, a lentidão da fonte significar que os elementos visuais individuais demorarão mais do que isso (dezenas de segundos), a experiência se tornará muito ruim, possivelmente até ao ponto de as consultas atingirem o tempo limite.

Juntamente com o desempenho da fonte subjacente, deverá ser feita uma consideração cuidadosa em relação ao carregamento que será colocada sobre ela (que, é claro, geralmente afetará o desempenho). Como discutido mais detalhadamente abaixo, cada usuário que abre um relatório compartilhado e cada bloco de dashboard que é atualizado periodicamente, enviarão, pelo menos, uma consulta por visual à fonte subjacente. Esse fato exige que a fonte seja capaz de lidar com esse carregamento de consulta, mantendo, ao mesmo tempo, um desempenho razoável.

### <a name="limited-to-a-single-source"></a>Limitado a uma única fonte
Ao importar dados, é possível combinar dados de várias fontes em um único modelo, por exemplo, para unir facilmente alguns dados de um banco de dados do SQL Server corporativo com alguns dados locais mantidos em um arquivo do Excel. Isso não é possível ao usar o DirectQuery. Ao selecionar o DirectQuery para uma fonte, somente será possível usar dados dessa única fonte (como um único banco de dados do SQL Server).

### <a name="limited-data-transformations"></a>Transformações de dados limitadas
Da mesma forma, há limitações nas transformações de dados que podem ser aplicadas no **Editor de Consultas**. Com os dados importados, um conjunto sofisticado de transformações pode ser facilmente aplicado para limpar e formatar novamente os dados antes de usá-los para criar visuais (como a análise de documentos JSON ou a transformação de dados orientados em forma coluna para dados orientados em forma de linha). Essas transformações são mais limitadas no DirectQuery. Primeiro, ao se conectar a uma fonte OLAP, como o SAP Business Warehouse, nenhuma transformação poderá ser definida e todo o "modelo" externo será obtido da fonte. Para fontes relacionais como o SQL Server, ainda é possível definir um conjunto de transformações por consulta, mas essas transformações são limitadas por questões de desempenho. Quaisquer dessas transformações precisarão ser aplicadas a cada consulta à fonte subjacente, ao invés de uma vez a cada atualização dos dados, portanto são limitadas àquelas transformações que possam ser convertidas razoavelmente em uma única consulta nativa. Se você usa uma transformação que é muito complexa, você receberá um erro que terá que ser excluído ou o modelo terá que ser mudado para o modo de Importação.

Além disso, a consulta resultante da caixa de diálogo **Obter Dados** ou do **Editor de Consultas** será usada em uma subseleção dentro de consultas geradas e enviada para recuperar os dados necessários a um visual. Portanto, a consulta definida no Editor de Consultas deverá ser válida nesse contexto. Em particular, isso significa não será possível usar uma consulta com Expressões de Tabela Comum, nem que invoque Procedimentos armazenados.

### <a name="modelling-limitations"></a>Limitações de modelagem
O termo *modelagem*, nesse contexto, significa o ato de refinar e enriquecer os dados brutos, como parte da criação de um relatório que os utiliza. Os exemplos incluem:

* Definir relações entre tabelas
* Adicionar novos cálculos (colunas calculadas e medidas)
* Renomear e ocultar colunas e medidas
* Definir hierarquias
* Definir a formatação, a ordem de classificação e o resumo padrão de uma coluna
* Agrupar ou realizar clustering de valores

Ao usar o **DirectQuery**, muitos desses aprimoramentos de modelo ainda poderão ser realizados e certamente ainda haverá o princípio de que os dados brutos estarão sendo aprimorados para melhorar o consumo posterior. No entanto, há alguns recursos de modelagem que não estão disponíveis ou são limitados ao usar o DirectQuery. Geralmente, as limitações são aplicadas para evitar problemas de desempenho. O conjunto de limitações que são comuns a todas as fontes de DirectQuery estão na lista com marcadores abaixo. Limitações adicionais podem ser aplicadas a fontes individuais, conforme descrito em *Detalhes específicos da fonte de dados*, que encontra-se próximo ao final deste artigo.

* **Nenhuma hierarquia de data interna:** ao importar dados, cada coluna de date/datetime também terá uma hierarquia de data interna disponível por padrão. Por exemplo, ao importar uma tabela de pedidos de vendas, que inclui uma coluna OrderDate e utilizar essa coluna em um visual, será possível escolher o nível apropriado (ano, mês, dia) a ser usado. Essa hierarquia interna de data não está disponível ao usar o modo DirectQuery. No entanto, observe que se a tabela Date estiver disponível na fonte subjacente (como é comum em muitos data warehouses), as funções de Inteligência de Dados Temporais do DAX poderão ser usadas normalmente.
* **Limitações em colunas calculadas:** as colunas calculadas são limitadas a serem intra-linha e, sendo assim, só podem fazer referência a valores de outras colunas da mesma tabela, sem o uso de quaisquer funções de agregação. Além disso, as funções escalares do DAX (como LEFT()) que são permitidas serão limitadas àquelas que simplesmente podem ser enviadas por push à fonte subjacente e, portanto, variarão de acordo com os recursos exatos da fonte. As funções para as quais não há suporte não serão listadas no preenchimento automático durante a criação do DAX para uma coluna calculada e resultarão em um erro se forem usadas.
* **Não há suporte para funções DAX pai-filho:** no modelo DirectQuery, não é possível usar a família de funções DAX PATH(), que geralmente manipulam estruturas Pai-Filho (como gráfico de contas ou hierarquias de funcionários).
* **Limitações (por padrão) para medidas:** por padrão, as funções e expressões DAX que podem ser usadas em medidas são restritas. Novamente, o preenchimento automático restringirá as funções listadas e ocorrerá um erro se uma função ou expressão inválida for usada. O motivo é simplesmente para garantir que, por padrão, as medidas sejam restritas a medidas simples que, por si mesmas, tenham pouca probabilidade de causar problemas de desempenho. Os usuários avançados podem optar por ignorar essa limitação selecionando **Arquivo > Opções** e, em seguida, **Configurações > Opções > DirectQuery** e, por fim, selecionar a opção *Permitir medidas sem restrições no modo DirectQuery*. Quando essa opção for selecionada, qualquer expressão DAX válida para uma medida poderá ser usada. No entanto, os usuários devem estar cientes de que algumas expressões que funcionam bem quando os dados são importados podem resultar em consultas muito lentas à fonte de back-end quando estiverem no modo DirectQuery.
  
  * Por exemplo, por padrão:
    
    * Seria possível criar uma medida que simplesmente totalizasse a quantidade de vendas:
      
          SalesAmount = SUMX(Web_Sales, [ws_sales_price]* [ws_quantity])
    * *Não* seria possível criar uma medida que, em seguida, calculasse a média de SalesAmount sobre todos os itens:
      
          AverageItemSalesAmount = AVERAGEX('Item', [SalesAmount])
    
    O motivo é que essa medida poderia resultar em baixo desempenho se houvesse um grande número de itens.
* **Não há suporte para tabelas calculadas:** a capacidade de definir uma tabela calculada usando uma expressão DAX não tem suporte no modo DirectQuery.
* **A filtragem de relação é limitada a uma única direção:** ao usar o DirectQuery, não é possível definir a direção do Filtro Cruzado em uma relação como "Ambas". Por exemplo, com as três tabelas abaixo, não seria possível criar um visual mostrando cada Customer[Gender] e o número de Product[Category] comprados por cada um. O uso dessa filtragem bidirecional é descrito [neste white paper detalhado](http://download.microsoft.com/download/2/7/8/2782DF95-3E0D-40CD-BFC8-749A2882E109/Bidirectional cross-filtering in Analysis Services 2016 and Power BI.docx) (o white paper apresenta exemplos no contexto do SQL Server Analysis Services, mas os pontos fundamentais se aplicam igualmente ao Power BI).
  
  ![](media/desktop-directquery-about/directquery-about_01.png)
  
  Novamente, o limite é imposto devido às implicações de desempenho. Uma aplicação especialmente importante disso é ao definir a Segurança em Nível de Linha como parte do relatório, pois um padrão comum é ter uma relação de muitos para muitos entre os usuários e as entidades às quais eles podem acessar e é necessário o uso de filtragem bidirecional para impor isso. No entanto, a filtragem bidirecional para modelos do DirectQuery deve ser usada com cuidado, com especial atenção a qualquer impacto negativo no desempenho.  
* **Sem Clustering:** ao usar o DirectQuery, não é possível usar a funcionalidade de Clustering para localizar grupos automaticamente

### <a name="reporting-limitations"></a>Limitações de relatórios
Quase todos os recursos de relatórios têm suporte para modelos do DirectQuery. Sendo assim, desde que a fonte subjacente ofereça um nível adequado de desempenho, o mesmo conjunto de visualizações poderá ser usado. No entanto, há algumas limitações importantes em alguns dos recursos oferecidos no **serviço do Power BI** depois que um relatório é publicado, conforme descrito nos seguintes marcadores:

* **Não há suporte para os Insights Rápidos:** o Power BI pesquisa diferentes subconjuntos do conjunto de dados durante a aplicação de um conjunto de algoritmos sofisticados para descobrir informações que possam ser interessantes. Dada a necessidade de consultas de desempenho muito alto, essa funcionalidade não está disponível em conjuntos de dados que usam o DirectQuery.
* **Não há suporte para P e R:** as P e R do Power BI permitem explorar seus dados usando recursos intuitivos em idioma natural e receber as respostas na forma de quadros e gráficos. No entanto, atualmente não há suporte em conjuntos de dados que usam o DirectQuery.
* **O uso de Explorar no Excel provavelmente resultará em desempenho insatisfatório:** é possível explorar seus dados usando a funcionalidade de "Explorar no Excel" em um conjunto de dados. Isso permitirá que Tabelas dinâmicas e Gráficos dinâmicos sejam criados no Excel. Embora haja suporte para essa funcionalidade em conjuntos de dados que usam o DirectQuery, o desempenho será geralmente mais lento do que na criação de visuais no Power BI e, portanto, se o uso do Excel for importante para os seus cenários, isso deverá ser considerado em sua decisão de usar o DirectQuery.

### <a name="security"></a>Segurança
Conforme discutido anteriormente neste artigo, um relatório que utiliza o **DirectQuery** sempre usará as mesmas credenciais fixas para se conectar à fonte de dados subjacente, após publicar no **serviço do Power BI**. Novamente, observe que isso refere-se especificamente ao DirectQuery e não às conexões dinâmicas ao SQL Server Analysis Services, que são diferentes nesse sentido. Portanto, imediatamente após a publicação de um relatório do DirectQuery, será necessário configurar as credenciais do usuário que serão usadas. Até que isso seja feito, a abertura do relatório no serviço do Power BI poderá resultar em um erro.

Depois que as credenciais do usuário forem fornecidas, elas serão usadas, *independentemente do usuário que abre o relatório*. Nesse sentido, isso é exatamente como nos dados importados, em que cada usuário vê os mesmos dados, a menos que a Segurança em Nível de Linha tenha sido definida como parte do relatório. Portanto, deverá haver a mesma atenção no compartilhamento do relatório, caso haja regras de segurança definidas na fonte subjacente.

### <a name="behavior-in-the-power-bi-service"></a>Comportamento no serviço do Power BI
Esta seção descreve o comportamento de um relatório do **DirectQuery** no **serviço do Power BI**, principalmente para sermos capazes de entender o grau de carregamento que será colocado na fonte de dados de back-end, dado o número de usuários com os quais o relatório e o dashboard serão compartilhados, a complexidade do relatório e se a Segurança em Nível de Linha foi definida no relatório.

#### <a name="reports--opening-interacting-with-editing"></a>Relatórios – abrir, interagir, editar
Quando um relatório é aberto, todos os visuais na página atualmente visível são atualizados. Cada visual geralmente exigirá pelo menos uma consulta à fonte de dados subjacente. Alguns visuais podem exigir mais de uma consulta (por exemplo, se mostra valores de agregação de duas tabelas de fatos diferentes ou se contém uma medida mais complexa ou se contém totais de uma medida não aditiva, como Count Distinct). Mover para uma nova página causará a atualização desse visuais, resultando em um novo conjunto de consultas à fonte subjacente.

Cada interação do usuário no relatório pode resultar na atualização de visuais. Por exemplo, a seleção de um valor diferente em uma segmentação de dados exigirá o envio de um novo conjunto de consultas para atualizar todos os visuais afetados. O mesmo é verdadeiro ao clicar em um visual para realizar destaques cruzados de outros visuais ou alterar um filtro.  

Da mesma forma, é claro, a edição de um novo relatório exige o envio de consultas para cada etapa no caminho para se produzir o visual final desejado.

Há o cache de alguns resultados, de modo que a atualização de um visual seja instantânea, caso os mesmos resultados tenham sido recentemente obtidos. Esses caches não são compartilhados entre usuários, caso haja qualquer Segurança em Nível de Linha definida como parte do relatório.

#### <a name="dashboard-refresh"></a>Atualização do dashboard
Visuais individuais ou páginas inteiras podem ser fixados como blocos no dashboard. Assim, os blocos com base em conjuntos de dados do **DirectQuery** são atualizados automaticamente de acordo com um agendamento, resultando no envio de consultas à fonte de dados de back-end. Por padrão, isso ocorre a cada hora, mas pode ser configurado como parte das configurações do conjunto de dados para ocorrer entre semanalmente e a cada 15 minutos.

Se nenhuma Segurança em Nível de Linha for definida no modelo, isso significará que cada bloco deverá ser atualizado uma vez e os resultados compartilhados entre todos os usuários. Se a Segurança em Nível de Linha for definida, poderá ocorrer um grande efeito multiplicador – cada bloco exige que consultas separadas por usuário sejam enviadas à fonte subjacente.  

Assim, um dashboard com dez blocos, compartilhado com 100 usuários, criado em um conjunto de dados com o uso de **DirectQuery** com Segurança em Nível de Linha e configurado para ser atualizado a cada 15 minutos, poderá resultar em, pelo menos, 1000 consultas sendo enviadas a cada 15 minutos à fonte de back-end.

Portanto, deverá ser dada uma consideração especial em relação ao uso da Segurança em Nível de Linha e da configuração do agendamento de atualização.

#### <a name="timeouts"></a>Tempo limite
Um tempo limite de quatro minutos é aplicado às consultas individuais no **serviço do Power BI** e consultas que demoram mais do que isso simplesmente falharão. Como enfatizado anteriormente, é recomendável que o DirectQuery seja usado para fontes que forneçam desempenho próximo ao da consulta interativa, portanto, esse limite se destina a impedir problemas de tempos de execução excessivamente longos.

### <a name="other-implications"></a>Outras implicações
Outras implicações gerais do uso de **DirectQuery** são as seguintes:

* **Se os dados estiverem se alterando, será necessário atualizar para garantir que os dados mais recentes sejam mostrados:** dado o uso de caches, não há nenhuma garantia de que o visual esteja sempre mostrando os dados mais recentes. Por exemplo, um visual pode mostrar as transações do dia anterior. Então, devido a uma alteração de segmentação de dados, ele poderá ser atualizado para mostrar as transações dos últimos dois dias, incluindo algumas transações muito recentes que acabaram de chegar. Ao retornar a segmentação de dados ao seu valor original, os valores previamente obtidos armazenados em cache seriam exibidos novamente e isso não incluiria a transação recentemente chegada que foi vista antes.
  
  Selecionar Atualizar limpará todos os caches e atualizará todos os visuais na página para exibir os dados mais recentes.
* **Se os dados estiverem se alterando, não haverá nenhuma garantia da consistência entre os visuais:** visuais diferentes, sejam na mesma página ou em páginas diferentes, podem ser atualizados em momentos diferentes. Portanto, se os dados na fonte subjacente estiverem sendo alterados, não haverá nenhuma garantia de que cada visual estará mostrando os dados no mesmo ponto do tempo. Na verdade, considerando que, às vezes, mais de uma consulta é necessária para um único visual (por exemplo, para obter os detalhes e os totais), não há garantia de consistência, mesmo em um único visual. Essa garantia exigiria a sobrecarga da atualização de todos os visuais sempre que qualquer visual fosse atualizado, junto com o uso de recursos caros como o Isolamento do Instantâneo na fonte de dados subjacente.
  
  Esse problema poderá ser reduzido em grande parte ao selecionar novamente Atualizar, o que atualizará todos os visuais da página. E observe que, mesmo com o uso do modo de Importação, há um problema semelhante para garantir consistência, caso seja feita a importação de dados de mais de uma tabela.
* **A atualização no Power BI Desktop é necessária para refletir as alterações de metadados:** depois que um relatório é publicado, a Atualização simplesmente atualizará os visuais no relatório. Se o esquema da fonte subjacente for alterado, essas alterações não serão aplicadas automaticamente para alterar os campos disponíveis na lista de campos. Portanto, se tabelas ou colunas foram removidas da fonte subjacente, isso poderá resultar em falha de consulta após a atualização. Abrir o relatório no Power BI Desktop e escolher Atualizar vai causar a atualização dos campos no modelo para que as alterações sejam refletidas.
* **Limite de um milhão de linhas retornadas em qualquer consulta:** há um limite fixo de um milhão de linhas colocado no número de linhas que podem ser retornadas em qualquer consulta única à fonte subjacente. Isso geralmente não tem nenhuma implicação prática e os visuais em si não vão exibir essa quantidade de pontos. No entanto, o limite poderá ocorrer nos casos em que Power BI não estiver otimizando totalmente as consultas enviadas e houver algum resultado intermediário que esteja sendo solicitado que exceda o limite. Isso também poderá ocorrer durante a criação de um visual, no caminho para um estado final mais razoável. Por exemplo, a inclusão de Customer e TotalSalesQuantity alcançaria esse limite, se houvesse mais de 1 milhão de clientes, até que algum filtro fosse aplicado.
  
  O erro retornado seria "O conjunto de resultados de uma consulta a uma fonte de dados externa excedeu o tamanho máximo permitido de '1000000' linhas".
* **Não é possível alterar do modo Importação para o modo DirectQuery:** observe que, embora seja geralmente possível mudar um modelo do modo DirectQuery para o modo de importação, isso significará que todos os dados necessários deverão ser importados. Também não é possível mudar de volta (principalmente devido ao conjunto de recursos sem suporte no modo DirectQuery). Os modelos do DirectQuery em fontes multidimensionais, como SAP BW, também não podem ser alternados de DirectQuery para importação, devido ao tratamento completamente diferente das medidas externas.

## <a name="directquery-in-the-power-bi-service"></a>DirectQuery no serviço do Power BI
Todas as fontes têm suporte no **Power BI Desktop**. Algumas fontes também estão disponíveis diretamente de dentro do **serviço do Power BI**. Por exemplo, é possível que um usuário empresarial use o Power BI para conectar seus dados no Salesforce e obtenha imediatamente um dashboard, sem usar o **Power BI Desktop**.

Apenas duas das fontes habilitadas do DirectQuery estão disponíveis diretamente no serviço:

* Spark
* SQL Data Warehouse do Azure

No entanto, é altamente recomendável que qualquer uso de **DirectQuery** nessas duas fontes inicie no **Power BI Desktop**. A razão é que, quando a conexão é estabelecida inicialmente no **serviço do Power BI**, muitas limitações importantes serão aplicadas, o que significa que, enquanto que o início tenha sido fácil (começando no serviço do Power BI), haverá limitações em qualquer aperfeiçoamento adicional do relatório resultante (por exemplo, não será possível criar cálculos ou usar muitos recursos analíticos ou até mesmo atualizar os metadados para refletirem as alterações ao esquema subjacente).   

## <a name="guidance-for-using-directquery-successfully"></a>Diretrizes para usar o DirectQuery com êxito
Se você pretende usar o **DirectQuery**, esta seção fornece algumas diretrizes de alto nível de como garantir o sucesso. As diretrizes desta seção são derivadas das implicações do uso do DirectQuery descritas neste artigo.

### <a name="backend-data-source-performance"></a>Desempenho de fonte de dados de back-end
É altamente recomendável validar que os visuais simples possam ser atualizados em um tempo razoável. A atualização deverá acontecer dentro de 5 segundos para que a experiência interativa seja razoável. Certamente, se os visuais estiverem demorando mais de 30 segundos, será muito provável que outros problemas ocorrerão após a publicação do relatório, tornando a solução impraticável.

Se as consultas estiverem lentas, o primeiro ponto de investigação será o exame das consultas que estão sendo enviadas à fonte subjacente e o motivo do desempenho de consulta observado. Este tópico não aborda a grande variedade de melhores práticas de otimização de banco de dados em todo o conjunto de possíveis fontes subjacentes, mas aplica-se às práticas padronizadas de banco de dados que são adequadas à maioria das situações:

* Os relacionamentos com base em colunas de inteiros geralmente têm melhor desempenho que uniões em colunas de outros tipos de dados
* Os índices apropriados devem ser criados, o que geralmente exige a utilização de índices de repositório de coluna nas fontes que dão suporte a eles (por exemplo, o SQL Server).
* Todas as estatísticas necessárias na fonte devem ser atualizadas

### <a name="model-design-guidance"></a>Diretrizes de design de modelo
Ao definir o modelo, considere o seguinte:

* **Evite consultas complexas no Editor de Consultas.** A consulta que é definida no Editor de Consultas será convertida em uma única consulta SQL, que será incluída na subseleção de todas as consultas enviadas a essa tabela. Se essa consulta for complexa, poderá resultar em problemas de desempenho em todas as consultas enviadas. A consulta SQL real de um conjunto de etapas pode ser obtida através da seleção da última etapa no Editor de Consultas e a escolha de *Exibir Consulta Nativa* no menu de contexto.
* **Mantenha as medidas simples.** Pelo menos inicialmente, é recomendável limitar as medidas a agregações simples. Depois, se elas forem executadas de forma satisfatória, medidas mais complexas poderão ser definidas, mantendo atenção ao desempenho de cada uma delas.
* **Evite relações em colunas calculadas.** Isso é particularmente relevante para bancos de dados nos quais é necessário realizar uniões de várias colunas. Atualmente o Power BI não permite que uma relação seja baseada em várias colunas, como a FK/PK. A solução comum é concatenar as colunas usando uma coluna calculada e basear a união nessa coluna. Embora essa solução seja razoável para os dados importados, no caso do **DirectQuery** ela resultará em uma junção em uma expressão que geralmente impede o uso de quaisquer índices, levando a um desempenho insatisfatório. A única solução alternativa é realmente materializar as várias colunas em uma única coluna no banco de dados subjacente.
* **Evite relações em colunas uniqueidentifier.** O Power BI não dá suporte nativo ao tipo de dados uniqueidentifier. Portanto, a definição de uma relação entre colunas do tipo uniqueidentifier resultará em uma consulta com uma união envolvendo uma Cast. Novamente, isso geralmente levará ao desempenho insatisfatório. Até que esse caso seja especificamente otimizado, a única solução alternativa seria materializar colunas de um tipo alternativo no banco de dados subjacente.
* **Ocultar a coluna *to* em relações.** A coluna *to* nas relações (geralmente a chave primária na tabela *to*) deve ser ocultada, para que não apareça na lista de campos e, portanto, não possa ser usada em visuais. Geralmente, as colunas em que as relações se baseiam são, na verdade, *colunas do sistema* (por exemplo, chaves alternativas em um data warehouse) e ocultar essas colunas é sempre uma boa prática. Caso a coluna tenha significado, introduza uma coluna calculada que seja visível e que tenha uma expressão simples de ser igual à chave primária. Por exemplo:
  
      ProductKey_PK   (Destination of a relationship, hidden)
      ProductKey (= [ProductKey_PK],   visible)
      ProductName
      ...
  
  A razão para isso é para simplesmente evitar um problema de desempenho que possa ocorrer, caso um visual inclua a coluna de chave primária.
* **Examine todos os usos de colunas calculadas e alterações de tipo de dados.** O uso desses recursos não é necessariamente prejudicial, pois eles resultam em consultas enviadas à fonte subjacente contendo expressões em vez de referências simples a colunas que, novamente, podem resultar em índices não utilizados.  
* **Evite o uso de filtragem cruzada bi-direcional em relações (na versão prévia).**
* **Experimente com a configuração *Pressupor integridade referencial*.** A configuração *Pressupor integridade referencial* em relações permite que as consultas usem instruções INNER JOIN em vez de OUTER JOIN. Isso geralmente melhora o desempenho de consulta, embora dependa de especificidades da fonte de dados.
* **Não use a filtragem de dados relativos no Editor de Consultas.** É possível definir a filtragem de data relativa no Editor de Consultas. Por exemplo, para filtrar as linhas em que a data esteja nos últimos 14 dias.
  
  ![](media/desktop-directquery-about/directquery-about_02.png)
  
  No entanto, isso será convertido em um filtro com base na data fixada, como no momento em que a consulta foi criada. Isso pode ser observado através da visualização da consulta nativa.
  
  ![](media/desktop-directquery-about/directquery-about_03.png)
  
  Certamente esse não era o resultado que se esperava. Em vez disso, para garantir que o filtro seja aplicado com base na data do momento em que o relatório é executado, aplique o filtro no relatório como um Filtro de Relatório. Atualmente, isso seria realizado por meio da criação de uma coluna calculada, calculando o número de dias atrás (usando a função DAX DATE()) e, em seguida, usando essa coluna calculada em um filtro.

### <a name="report-design-guidance"></a>Diretrizes de design de relatório
Ao criar um relatório usando uma conexão do DirectQuery, observe as seguintes diretrizes:

* **Aplicar filtros primeiro:** sempre aplique todos os filtros necessários no início da criação de um visual. Por exemplo, em vez de arrastar na TotalSalesAmount e ProductName e, em seguida, filtrar para um determinado ano, aplique o filtro em Year no início. Isso porque cada etapa da criação de um visual enviará uma consulta e, embora seja possível fazer uma alteração antes que a primeira consulta seja concluída, isso ainda manterá o carregamento desnecessário na fonte subjacente. Ao aplicar os filtros no início, as consultas intermediárias serão geralmente menos dispendiosas. Além disso, deixar de aplicar os filtros no início poderá resultar no alcance do limite de 1 milhão de linhas mencionado acima.
* **Limitar o número de visuais em uma página:** quando uma página é aberta (ou alguma segmentação ou filtro de nível de página é alterado), todos os visuais em uma página são atualizados. Também há um limite no número de consultas que são enviadas em paralelo, assim, conforme o número de visuais aumenta, alguns desses visuais serão atualizados em série, aumentando o tempo necessário para atualizar a página inteira. Por esse motivo é recomendado limitar o número de visuais em uma única página e, em vez disso, ter mais páginas mais simples.
* **Considerar desativar a interação entre visuais:** por padrão, as visualizações em uma página de relatório podem ser usadas para realizar filtro cruzado e destaque cruzado de outras visualizações na página. Por exemplo, ao selecionar "1999" no gráfico de pizza, é realizado o destaque cruzado do gráfico de colunas para mostrar as vendas por categoria para "1999".                                                                  
  
  ![](media/desktop-directquery-about/directquery-about_04.png)
  
  No entanto, essa interação pode ser controlada conforme descrito [neste artigo](service-reports-visual-interactions.md). No DirectQuery, essas filtragens cruzadas e destaques cruzados exigem o envio de consultas à fonte subjacente, portanto a interação deverá ser desligada, se o tempo necessário para responder às seleções do usuário for exageradamente longo.
* **Considerar compartilhar somente o relatório:** há diferentes maneiras de compartilhar conteúdo após a publicação no **serviço do Power BI**. No caso de DirectQuery, é aconselhável considerar o compartilhamento somente do relatório concluído, em vez de permitir que outros usuários criem novos relatórios (e, potencialmente, encontrem problemas de desempenho para os visuais específicos que eles criarem).

Além da lista de sugestões acima, observe que cada uma das seguintes funcionalidades de relatório poderá causar problemas de desempenho:

* **Filtros de medidas:** visuais que contém medidas (ou agregações de colunas) podem conter filtros nessas medidas. Por exemplo, o visual abaixo mostra SalesAmount por Categoria, incluindo somente as categorias com mais de 20 milhões em vendas.
  
  ![](media/desktop-directquery-about/directquery-about_05.png)
  
  Isso resultará no envio de duas consultas à fonte subjacente:
  
  * A primeira consulta recuperará as Categorias que atendem à condição (vendas > 20 milhões)
  * Em seguida, a segunda consulta recuperará os dados necessários para o visual, incluindo as Categorias que atendem à condição na cláusula WHJERE.  
  
  Isso geralmente é bem executado, se houver centenas ou milhares de categorias como neste exemplo. O desempenho poderá ser prejudicado se o número de categorias for muito maior (e, na verdade, a consulta falhará se houver mais de um milhão categorias que atendem à condição, devido ao limite de um milhão de linhas discutido anteriormente).
* **Filtros TopN:** filtros avançados podem ser definidos para filtrar somente os N valores mais importantes (ou menos importantes) classificados por alguma medida, por exemplo, para incluir somente as 10 categorias mais importantes no visual acima. Novamente, isso resultará no envio de duas consultas à fonte subjacente. No entanto, a primeira consulta retornará todas as categorias da fonte subjacente e, em seguida, os TopN serão determinados com base nos resultados retornados. Dependendo da cardinalidade da coluna envolvida, isso poderá causar problemas de desempenho (ou falhas de consulta devido ao limite de 1 milhão de linhas).
* **Mediana:** geralmente, qualquer agregação (Sum, Count Distinct e assim por diante) é enviada por push à fonte subjacente. No entanto, isso não é verdade para a Mediana, pois geralmente não há suporte para essa agregação na fonte de subjacente. Nesses casos, os dados de detalhes são recuperados da fonte subjacente e a Mediana é calculada com base nos resultados retornados. Isso é razoável quando a mediana for calculada em um número relativamente pequeno de resultados, mas os problemas de desempenho (ou falhas de consulta devido ao limite de 1 milhão de linhas) ocorrerão se a cardinalidade for grande.  Por exemplo, População do País Mediana seria razoável, mas Preço de Vendas Mediana ce não.
* **Filtros de texto avançados ("contém" e similares):** ao filtrar em uma coluna de texto, a filtragem avançada permite o uso de filtros como "contém", "começa com" e assim por diante. Esses filtros certamente poderão causar degradação no desempenho para algumas fontes de dados. Especificamente, o filtro "contém" padrão não deve ser usado se o que é realmente necessário é uma correspondência exata ("é" ou "não é"). Embora os resultados possam ser os mesmos, dependendo dos dados reais, o desempenho poderá ser drasticamente diferente devido ao uso de índices.
* **Segmentações de várias seleções:** por padrão, as segmentações permitem que seja realizada apenas uma única seleção. A permissão de seleção múltipla em filtros poderá causar alguns problemas de desempenho, porque quando usuário seleciona um conjunto de itens na segmentação (por exemplo, os dez produtos nos quais ele está interessado), cada nova seleção resultará no envio de consultas à fonte de back-end. Embora o usuário possa selecionar o próximo item antes da conclusão da consulta, isso resultará em carregamento extra na fonte subjacente.

### <a name="diagnosing-performance-issues"></a>Diagnosticar problemas de desempenho
Esta seção descreve como diagnosticar problemas de desempenho ou obter informações mais detalhadas para permitir que os relatórios sejam otimizados.

É altamente recomendável que qualquer diagnóstico de problemas de desempenho comece no **Power BI Desktop**, em vez de no **serviço do Power BI**. Isso porque é comum que os problemas de desempenho sejam simplesmente baseados no nível de desempenho da fonte subjacente e esses problemas são mais facilmente identificados e diagnosticados no ambiente bem mais isolado do **Power BI Desktop**, eliminando inicialmente alguns componentes (como o gateway do Power BI). Somente se for identificado que os problemas de desempenho não estão presentes com o Power BI Desktop, o foco de investigação deverá ser nas particularidades do relatório no serviço do Power BI.

Da mesma forma, recomenda-se primeiro tentar isolar os problemas a um visual individual, em vez de muitos visuais em uma página.

Portanto, digamos que essas etapas (nos parágrafos anteriores desta seção) foram realizadas – agora temos um único visual em uma página no **Power BI Desktop** que ainda está lento. Para determinar as consultas que são enviadas pelo Power BI Desktop à fonte subjacente é possível exibir informações de diagnóstico/rastreamento que possam ser emitidas por essa fonte. Esses rastreamentos também podem conter informações úteis sobre os detalhes de como a consulta foi executada e como ela pode ser melhorada.

Além disso, mesmo na ausência desses rastreamentos da fonte, é possível exibir as consultas enviadas pelo Power BI, juntamente com seus tempos de execução, conforme descrito a seguir.

#### <a name="determining-the-queries-sent-by-power-bi-desktop"></a>Determinando as consultas enviadas pelo Power BI Desktop
Por padrão, o **Power BI Desktop** registra eventos durante uma determinada sessão em um arquivo de rastreamento chamado FlightRecorderCurrent.trc.

Para algumas fontes do **DirectQuery**, esse log inclui todas as consultas enviadas à fonte de dados subjacente (as fontes de DirectQuery restantes serão incluídas no futuro). As fontes que enviam consultas ao log são as seguintes:

* SQL Server
* Banco de dados SQL do Azure
* SQL Data Warehouse do Azure
* Oracle
* Teradata
* SAP HANA

O arquivo de rastreamento pode ser encontrado na pasta **AppData** do usuário atual:

    \<User>\AppData\Local\Microsoft\Power BI Desktop\AnalysisServicesWorkspaces

Aqui está uma maneira fácil de acessar essa pasta: no **Power BI Desktop** selecione **Arquivo > Opções e configurações > Opções** e, em seguida, selecione **Diagnóstico**. A janela de diálogo a seguir será exibida:

![](media/desktop-directquery-about/directquery-about_06.png)

Ao selecionar o link *Abrir pastas de rastreamento* em **Opções de Diagnóstico**, a pasta a seguir é aberta:

    \<User>\AppData\Local\Microsoft\Power BI Desktop\Traces

Ao navegar até a pasta pai, o conteúdo da pasta pai exibirá a pasta contendo *AnalysisServicesWorkspaces*, com uma subpasta do espaço de trabalho para cada instância aberta do **Power BI Desktop**. Essas subpastas são nomeadas com um sufixo de inteiro, como *AnalysisServicesWorkspace2058279583*.

Dentro dessa pasta há uma subpasta *\Data* que contém o arquivo de rastreamento FlightRecorderCurrent.trc da sessão atual do Power BI. A pasta de espaço de trabalho correspondente é excluída quando a sessão associada do Power BI Desktop é encerrada.

Os arquivos de rastreamento podem ser lidos usando a ferramenta **SQL Server Profiler**, que está disponível como um download gratuito como parte do **SQL Server Management Studio**. Você pode obtê-la [neste local](https://msdn.microsoft.com/library/mt238290.aspx).

Depois de baixar e instalar o **SQL Server Management Studio**, execute o **SQL Server Profiler**.

![](media/desktop-directquery-about/directquery-about_07.png)

Para abrir o arquivo de rastreamento, execute as seguintes etapas:

1. No **SQL Server Profiler** selecione **Arquivo > Abrir > Arquivo de rastreamento**
2. Insira o caminho até o arquivo de rastreamento da sessão atualmente aberta do Power BI, como abaixo:
   
         C:\Users\<user>\AppData\Local\Microsoft\Power BI Desktop\AnalysisServicesWorkspaces\AnalysisServicesWorkspace2058279583\Data
3. Abra o FilghtRecorderCurrent.trc

Todos os eventos da sessão atual são exibidos. Um exemplo anotado está mostrado abaixo, destacando os grupos de eventos. Cada grupo tem o seguinte:

* Um evento *Início da Consulta* e um *Término da Consulta*, que representam o início e término de uma consulta DAX gerada pela interface do usuário (por exemplo, de um visual ou do preenchimento de uma lista de valores no filtro de interface do usuário)
* Um ou mais pares de eventos *Início do DirectQuery* e *Término do DirectQuery*, que representam uma consulta enviada à fonte de dados subjacente, como parte da avaliação da consulta DAX.

Observe que várias consultas DAX podem ser executadas em paralelo, portanto os eventos de grupos diferentes podem ser intercalados. O valor da ActivityID pode ser usado para determinar quais eventos pertencem ao mesmo grupo.

![](media/desktop-directquery-about/directquery-about_08.png)

Outras colunas de interesse são as seguintes:

* **TextData:** os detalhes textuais do evento. Para eventos de "Início/Término da Consulta"eles serão a consulta DAX. Para eventos de "Início/Término do DirectQuery", eles serão a consulta SQL enviada à fonte subjacente. O TextData do evento atualmente selecionado também será exibido na região da parte inferior.
* **EndTime:** quando o evento foi concluído.
* **Duration:** o tempo, em milissegundos, necessário para executar a consulta DAX ou SQL.
* **Error:** indica se ocorreu um erro (caso em que o evento também será exibido em vermelho).

Observe que, na imagem acima, algumas das colunas menos interessantes foram estreitadas para permitir que as colunas interessantes sejam vistas com maior facilidade.

A abordagem recomendada para capturar um rastreamento para ajudar a diagnosticar um problema de desempenho potencial é a seguinte:

* Abra uma única sessão do **Power BI Desktop** (para evitar confusão de várias pastas de espaço de trabalho)
* Realize o conjunto de ações desejadas no **Power BI Desktop**. Inclua algumas ações adicionais, para garantir que os eventos desejados sejam liberados no arquivo de rastreamento.
* Abra o **SQL Server Profiler** e examine o rastreamento, conforme descrito anteriormente. Lembre-se de que o arquivo de rastreamento será excluído com o fechamento do **Power BI Desktop**. Além disso, as ações adicionais no Power BI Desktop não aparecerão imediatamente – o arquivo de rastreamento deve ser fechado e aberto novamente para que os novos eventos sejam vistos.
* Mantenha as sessões individuais razoavelmente pequenas (dez segundos de ações e não centenas) para facilitar a interpretação do arquivo de rastreamento (e porque há um limite no tamanho do arquivo de rastreamento, portanto, para sessões muito longas, há uma possibilidade de que eventos recentes sejam descartados).

#### <a name="understanding-the-form-of-query-sent-by-power-bi-desktop"></a>Noções básicas sobre a forma da consulta enviada pelo Power BI Desktop
O formato geral das consultas criadas e enviadas pelo **Power BI Desktop** utiliza subseleções para cada uma das tabelas referenciadas, em que a subseleção é de acordo com a definição da consulta no **Editor de Consultas**. Por exemplo, suponha as seguintes tabelas TPC-DS no SQL Server:

![](media/desktop-directquery-about/directquery-about_09.png)

Considere a consulta a seguir:

![](media/desktop-directquery-about/directquery-about_10.png)

Essa consulta tem como resultado o seguinte visual:

![](media/desktop-directquery-about/directquery-about_11.png)

A atualização desse visual resultará na consulta SQL mostrada após o parágrafo abaixo. Como você pode ver, há três subseleções para Web Sales, Item e Date_dim, e cada uma delas retorna todas as colunas na respectiva tabela, embora, na realidade, apenas quatro colunas sejam referenciadas pelo visual. Essas consultas nas subseleções (elas estão sombreadas) são exatamente o resultado das consultas definidas no **Editor de Consultas**. O uso de subseleções dessa maneira não afetou o desempenho das fontes de dados com suporte pelo DirectQuery até o momento. As fontes de dados como o SQL Server simplesmente otimizam as referências a outras colunas.

Um motivo de o Power BI empregar esse padrão é porque a consulta SQL usada pode ser fornecida diretamente pelo analista, sendo usada "como fornecida", sem uma tentativa de reescrevê-la.

![](media/desktop-directquery-about/directquery-about_12.png)

## <a name="next-steps"></a>Próximas etapas
Este artigo descreve aspectos do **DirectQuery** que são comuns entre todas as fontes de dados. Há determinados detalhes que são específicos a fontes individuais. Consulte os tópicos a seguir que abrangem fontes específicas:

* [DirectQuery e SAP HANA](desktop-directquery-sap-hana.md)
* [DirectQuery e SAP BW](desktop-directquery-sap-bw.md)

Para obter mais informações sobre o **DirectQuery**, confira os seguintes recursos:

* [Fontes de dados com suporte do DirectQuery](desktop-directquery-data-sources.md)

