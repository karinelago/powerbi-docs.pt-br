---
title: Usar o DirectQuery no Power BI Desktop
description: "Use o DirectQuery, também chamado de Conexão dinâmica, no Power BI Desktop"
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
ms.date: 12/25/2017
ms.author: davidi
ms.openlocfilehash: d3643ae398c037c375c8e67360794047a6f66ed7
ms.sourcegitcommit: 7bf22bb1136fdb0f962422e16e837187f090827c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/01/2018
---
# <a name="use-directquery-in-power-bi-desktop"></a>Usar o DirectQuery no Power BI Desktop
Com o **Power BI Desktop**, ao se conectar à fonte de dados, sempre é possível importar uma cópia dos dados para o **Power BI Desktop**. Para algumas fontes de dados, uma abordagem alternativa está disponível: conectar-se diretamente à fonte de dados usando o **DirectQuery**.

## <a name="supported-data-sources"></a>Fontes de dados para as quais há suporte
Para obter uma lista completa de fontes de dados que dão suporte ao **DirectQuery**, consulte [Data sources supported by DirectQuery (Fontes de dados com suporte do DirectQuery)](desktop-directquery-data-sources.md).

## <a name="how-to-connect-using-directquery"></a>Como se conectar usando o DirectQuery
Quando você usa **Obter Dados** para se conectar a uma fonte de dados com suporte do **DirectQuery**, a janela de conexão deixa você selecionar como deseja se conectar.  

![](media/desktop-use-directquery/directquery_2a.png)

As diferenças entre a seleção de **Importar** e **DirectQuery** são as seguintes:

**Importar** – as tabelas e as colunas selecionadas são importadas para o **Power BI Desktop**. Conforme você cria ou interage com uma visualização, o **Power BI Desktop** usa os dados importados. Você deve atualizar os dados, o que importa o conjunto de dados completo novamente, para ver todas as alterações ocorridas nos dados subjacentes desde a importação inicial ou a atualização mais recente.

**DirectQuery** – nenhum dado é importado ou copiado para o **Power BI Desktop**. Para fontes relacionais, as tabelas e colunas selecionadas aparecem na lista **Campos**. Para fontes multidimensionais, como SAP Business Warehouse, as dimensões e medidas do cubo selecionado aparecem na lista **Campos**. Conforme você cria ou interage com uma visualização, o **Power BI Desktop** consulta a fonte de dados subjacente, o que significa que você sempre está exibindo dados atuais.

Muitas transformações de dados e modelagem de dados estão disponíveis ao usar o **DirectQuery**, embora com algumas limitações. Ao criar ou interagir com uma visualização, a fonte subjacente deve ser consultada e o tempo necessário para atualizar a visualização depende do desempenho da fonte de dados subjacente. Quando os dados necessários para atender à solicitação foram solicitados recentemente, o Power BI Desktop usa os dados recentes para reduzir o tempo necessário para exibir a visualização. A seleção de **Atualizar** na faixa de opções **Página Inicial** garantirá que todas as visualizações sejam atualizadas com os dados atuais.

O artigo [Power BI e DirectQuery](desktop-directquery-about.md) descreve **DirectQuery** em detalhes. Além disso, consulte as seções a seguir para obter mais informações sobre os benefícios, limitações e considerações importantes ao usar o **DirectQuery**.

## <a name="benefits-of-using-directquery"></a>Benefícios do uso do DirectQuery
Há alguns benefícios de usar o **DirectQuery**:

* O **DirectQuery** permite criar visualizações de conjuntos de dados muito grandes, em casos em que de outro modo seria impraticável importar primeiro todos os dados com pré-agregação
* Alterações de dados subjacentes podem exigir uma atualização de dados e, para alguns relatórios, a necessidade de exibir os dados atuais pode exigir transferências de dados grandes, tornando impraticável uma nova importação de dados. Por outro lado, os relatórios do **DirectQuery** sempre usam dados atuais
* A limitação do conjunto de dados de 1 GB *não* se aplica ao **DirectQuery**

## <a name="limitations-of-directquery"></a>Limitações do DirectQuery
Atualmente, há algumas limitações no uso do **DirectQuery**:

* Todas as tabelas devem vir de um banco de dados individual
* Se a consulta do **Editor de Consultas** for excessivamente complexa, ocorrerá um erro. Para corrigir esse erro, é necessário excluir a etapa que apresenta problemas no **Editor de Consultas** ou *importar* os dados em vez de usar o **DirectQuery**. Para fontes multidimensionais, como SAP Business Warehouse, não há nenhum **Editor de Consultas**
* A filtragem de relação é limitada a uma única orientação, em vez de ambas as orientações (embora seja possível habilitar a filtragem cruzada em ambas as orientações para o **DirectQuery** como um recurso de versão prévia). Para fontes multidimensionais, como SAP Business Warehouse, não há nenhuma relação definida no modelo
* Os recursos de inteligência de tempo não estão disponíveis no **DirectQuery**. Por exemplo, o tratamento especial de colunas de data (ano, trimestre, mês, dia e assim por diante) não é suportado no modo **DirectQuery**.
* Por padrão, as limitações são colocadas em expressões DAX permitidas em medidas; veja o parágrafo a seguir (após esta lista com marcadores) para obter mais informações
* Há um limite de 1 milhão de linhas para retornar dados ao usar **DirectQuery**. Isso não afeta as agregações ou os cálculos usados para criar o conjunto de dados retornado usando **DirectQuery**, somente as linhas retornadas. Por exemplo, você pode agregar 10 milhões de linhas com a consulta é executada na fonte de dados e retornar, com precisão, os resultados desta agregação para o Power BI usando o **DirectQuery** desde que os dados retornados para o Power BI sejam menores do que 1 milhão de linhas. Se mais de 1 milhão de linhas fossem retornadas do **DirectQuery**, o Power BI retornaria um erro.

Para garantir que as consultas enviadas à fonte de dados subjacente têm um desempenho aceitável, por padrão, são impostas limitações às medidas. Os usuários avançados podem optar por ignorar essa limitação selecionando **Arquivo > Opções** e, em seguida, **Configurações > Opções e configurações > DirectQuery** e, por fim, selecionando a opção *Permitir medidas sem restrições no modo DirectQuery*. Quando essa opção for selecionada, qualquer expressão DAX válida para uma medida poderá ser usada. No entanto, os usuários devem estar cientes de que algumas expressões que funcionam muito bem quando os dados são importados podem resultar em consultas muito lentas à fonte de back-end quando estiverem no modo DirectQuery.

## <a name="important-considerations-when-using-directquery"></a>Considerações importantes ao usar o DirectQuery
Os três pontos a seguir devem ser levados em consideração ao usar o **DirectQuery**:

* **Desempenho e carga** - Todas as solicitações do **DirectQuery** são enviadas para o banco de dados de origem para que o tempo necessário para atualizar um visual dependa de quanto tempo essa fonte de back-end leva para responder com os resultados da consulta (ou consultas). O tempo de resposta recomendado (com os dados solicitados sendo retornados) para usar o **DirectQuery** para elementos visuais é de cinco segundos ou menos, com um tempo de resposta de resultados máximo recomendado de 30 segundos. Se levar mais, e a experiência de um usuário consumindo o relatório se tornará muito ruim. Além disso, depois que um relatório é publicado para o serviço do Power BI, qualquer consulta que levar mais tempo do que alguns minutos atingirá o tempo limite e o usuário receberá um erro.
  
  Carregar o banco de dados de origem também deve ser considerado, com base no número de usuários do Power BI que consumirá o relatório publicado. Usar a *Segurança em Nível de Linha* (RLS -Row Level Security) pode ter um impacto significativo também; um bloco de painel não RLS compartilhado por vários usuários resulta em uma única consulta ao banco de dados, mas usar a RLS em um bloco de painel geralmente significa que a atualização de um bloco exige uma consulta *por usuário*, aumentando significativamente a carga no banco de dados de origem e afetando potencialmente o desempenho.
  
  O Power BI cria consultas que são tão eficientes quanto possível. Em determinadas situações, no entanto, a consulta gerada pode não ser eficiente o suficiente para evitar que a atualização falhe. Um exemplo dessa situação é quando uma consulta gerada recuperaria um número excessivamente grande de linhas (mais de 1 milhão) da fonte de dados back-end, na qual ocorre o seguinte erro:
  
      The resultset of a query to external data source has exceeded
      the maximum allowed size of '1000000' rows.
  
  Essa situação pode ocorrer com um gráfico simples que inclui uma coluna de cardinalidade muito alta, com a opção de agregação definida como *Não resumir*. O visual precisa ter somente colunas com uma cardinalidade abaixo de 1 milhão ou deve ter aplicados os filtros apropriados.
* **Segurança** - Todos os usuários que utilizam um relatório publicado, conectem-se à fonte de dados de back-end usando as credenciais inseridas após a publicação para o serviço do Power BI. Essa é a mesma situação de quando dados são importados: todos os usuários veem os mesmos dados, independentemente das regras de segurança definidas na fonte de back-end. Os clientes que desejam ter a segurança por usuário implementam com fontes do DirectQuery e usam a RLS. [Saiba mais sobre a RLS](service-admin-rls.md).
* **Recursos com suporte** - Nem todos os recursos do **Power BI Desktop** têm suporte no modo **DirectQuery**, ou têm algumas limitações. Além disso, há alguns recursos no serviço do Power BI (como *Quick Insights*) que não estão disponíveis para conjuntos de dados que usam o **DirectQuery**. Como tal, a limitação desses recursos ao usar o **DirectQuery** deve ser levada em consideração ao determinar se irá usar o **DirectQuery**.   

## <a name="publish-to-the-power-bi-service"></a>Publicar no serviço do Power BI
Os relatórios criados com o **DirectQuery** podem ser publicados no Serviço do Power BI.

Se a fonte de dados usada não precisar do **gateway de dados local** (**Banco de Dados SQL do Azure**, **SQL Data Warehouse do Azure** ou **Redshift**), as credenciais deverão ser fornecidas antes que o relatório publicado seja exibido no serviço do Power BI.

Você pode fornecer credenciais, selecionando o ícone de engrenagem **Configurações** no Power BI e, em seguida, selecionar **Configurações**.

![](media/desktop-use-directquery/directquery_3.png)

O Power BI exibe a janela **Configurações** . Lá, selecione a guia **Conjuntos de dados** , escolha o conjunto de dados que usa o **DirectQuery**e selecione **Editar credenciais**.

![](media/desktop-use-directquery/directquery_4.png)

Até que as credenciais sejam fornecidas, abrir um relatório publicado ou explorar um conjunto de dados criado com uma conexão do **DirectQuery** com os resultados dessas fontes de dados resultará em um erro.

Para fontes de dados diferentes de **Banco de Dados SQL do Azure**, **SQL Data Warehouse do Azure** e **Redshift** que usam o DirectQuery, um **gateway de dados local** deve ser instalado e a fonte de dados deve ser registrada para estabelecer uma conexão de dados. É possível [saber mais sobre o gateway de dados local](http://go.microsoft.com/fwlink/p/?LinkID=627094).

## <a name="next-steps"></a>Próximas etapas
Para obter mais informações sobre o **DirectQuery**, confira os seguintes recursos:

* [DirectQuery no Power BI](desktop-directquery-about.md)
* [Fontes de dados com suporte do DirectQuery](desktop-directquery-data-sources.md)
* [DirectQuery e SAP BW](desktop-directquery-sap-bw.md)
* [DirectQuery e SAP HANA](desktop-directquery-sap-hana.md)
* [Gateway de dados local](service-gateway-onprem.md)

