---
title: Criar pacotes de conteúdo de modelo no Power BI
description: Criação do pacote de conteúdo de modelo
author: markingmyname
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-developer
ms.topic: conceptual
ms.date: 10/09/2017
ms.author: maghan
ms.openlocfilehash: f3f3343122857cbf06c0004d2a3e5e5247f07e48
ms.sourcegitcommit: 638de55f996d177063561b36d95c8c71ea7af3ed
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/17/2018
---
# <a name="author-template-content-packs-in-power-bi"></a>Criar pacotes de conteúdo de modelo no Power BI
A criação de um pacote de conteúdo de modelo usa o Power BI Desktop e o PowerBI.com. Há quatro componentes para seu pacote de conteúdo:

* As consultas permitem que você [conecte](../desktop-connect-to-data.md) e [transforme](../desktop-query-overview.md) os dados e defina [parâmetros](https://powerbi.microsoft.com/blog/deep-dive-into-query-parameters-and-power-bi-templates/)  
* O modelo de dados para criar [relações](../desktop-create-and-manage-relationships.md), [medidas](../desktop-measures.md), e melhorias de perguntas e respostas  
* As [páginas](../desktop-report-view.md) de relatório, que incluem visuais e filtros para fornecer informações sobre seus dados  
* O [painel](../service-dashboards.md) e os [blocos](../service-dashboard-create.md) oferecem uma visão geral das informações incluídas  

Talvez você esteja familiarizado com cada uma das partes como recursos existentes no Power BI. Ao criar um pacote de conteúdo, há mais coisas a levar em consideração com relação a cada aspecto. Consulte cada seção abaixo para obter mais detalhes.

<a name="queries"></a>

## <a name="queries"></a>Consultas
Para pacotes de conteúdo de modelo, consultas desenvolvidas no Power BI Desktop são usadas para se conectar à fonte de dados e importar dados. Essas consultas são necessárias para retornar um esquema consistente e têm suporte para atualização de dados agendada (a consulta direta não tem suporte).

Os pacotes de conteúdo do modelo dão suporte apenas a uma fonte de dados por pacote de conteúdo, então defina suas consultas com cuidado. Uma única fonte de dados é definida como uma fonte que requer a mesma autenticação. Você poderá fazer várias chamadas à API em consultas diferentes, se todas as chamadas forem para o mesmo ponto de extremidade de API e usarem a mesma autenticação. Os pacotes de conteúdo do Power BI não dão suporte a várias fontes que exigem autenticações diferentes.

### <a name="connect-to-your-api"></a>Conectar-se à sua API
Para começar, você precisará se conectar à sua API do Power BI Desktop para iniciar a criação de suas consultas.

Você pode usar os Conectores de Dados que estão prontos para uso no Power BI Desktop para conectar-se à sua API. Você pode usar o Conector de Dados da Web (Obter Dados -> Web) para conectar-se ao seu conector da API REST ou do OData (Obter Dados -> Feed OData) para conectar-se ao seu feed OData. Observe que esses conectores prontos para uso só funcionarão se sua API der suporte à autenticação básica.

> [!NOTE]
> Se sua API usa qualquer outro tipo de autenticação, como OAuth 2.0 ou chave de API da Web, você precisará desenvolver seu próprio conector de dados para permitir que o Power BI Desktop e conecte e se autentique em sua API com êxito. Para obter detalhes de como desenvolver ses próprio conector de dados para seu pacote de conteúdo, consulte a documentação de conectores de dados [aqui](https://aka.ms/DataConnectors). 
> 
> 

### <a name="consider-the-source"></a>Considere o código-fonte
As consultas definem os dados que serão incluídos no modelo de dados. Dependendo do tamanho do seu sistema, essas consultas também devem incluir filtros para garantir que seus clientes estejam lidando com um tamanho gerenciável adequado ao seu cenário de negócios.

Pacotes de conteúdo do Power BI podem executar várias consultas em paralelo e para vários usuários simultaneamente.  Planeje antecipadamente sua estratégia de limitação e simultaneidade e nos pergunte como tornar seu pacote de conteúdo tolerante a falhas.

### <a name="schema-enforcement"></a>Imposição do esquema
Verifique se as consultas são resistentes a alterações em seu sistema, alterações no esquema após atualizações podem interromper o modelo. Se a fonte puder retornar resultados de esquema ausente/nulo para algumas consultas, considere retornar uma tabela vazia ou lançar mensagens de erro personalizadas que sejam relevantes para o usuário.

### <a name="parameters"></a>Parâmetros
Os [parâmetros](https://powerbi.microsoft.com/blog/deep-dive-into-query-parameters-and-power-bi-templates/) no Power BI Desktop permitem que os usuários forneçam valores de entrada que personalizam os dados recuperados pelo usuário. Pense antecipadamente nos parâmetros para evitar retrabalho após investir tempo para criar consultas ou relatórios detalhados.

> [!NOTE]
> No momento, os pacotes de conteúdo do modelo somente dão suporte a parâmetros de texto. Outros tipos de parâmetro podem ser usados durante o desenvolvimento, mas durante a fase de [testes](template-content-pack-testing.md#templates) todos os valores fornecidos pelos usuários serão literais.
> 
> 

### <a name="additional-query-tips"></a>Dicas de consulta adicionais
* Certifique-se de que todas as colunas tenham sido digitadas corretamente  
* As colunas têm nomes informativos (consulte a seção sobre P e R)  
* Para a lógica compartilhada, considere o uso de funções ou consultas  
* Níveis de privacidade não têm suporte no serviço atualmente – se você receber um prompt sobre os níveis de privacidade, talvez seja necessário escrever a consulta novamente para usar caminhos relativos  

## <a name="data-model"></a>Modelo de dados
Um modelo de dados bem definido garantirá que os clientes possam interagir de forma fácil e interativa com o pacote de conteúdo. Crie o modelo de dados no Power BI Desktop.

> [!NOTE]
> Grande parte da modelagem básica (digitação, nomes de coluna) deve ser feita nas [consultas](#queries).
> 
> 

### <a name="qa"></a>P e R
A modelagem também afeta a eficiência da seção de P & R ao fornecer resultados para os clientes. Certifique-se de adicionar sinônimos para as colunas mais usadas e de que as colunas sejam nomeadas corretamente nas [consultas](#queries).

### <a name="additional-data-model-tips"></a>Dicas adicionais sobre modelos de dados
* Todas as colunas de valor têm formatação aplicada
    >[!NOTE]
    >Tipos devem ser aplicados na consulta.  
* Todas as medidas têm formatação aplicada  
* O resumo do padrão é definido. Especialmente "Não Resumir", quando aplicável (para valores únicos, por exemplo)  
* A Categoria de Dados foi definida, quando aplicável  
* As Relações estão definidas, conforme necessário  

## <a name="reports"></a>Relatórios
As páginas de relatório oferecem informações adicionais sobre os dados incluídos em seu pacote de conteúdo. Use as páginas do relatório para responder às principais questões de negócios que seu pacote de conteúdo está tentando solucionar. Crie o relatório usando o Power BI Desktop.

> [!NOTE]
> Apenas um único relatório pode ser incluído em um pacote de conteúdo, aproveite as diferentes páginas para ressaltar seções específicas do seu cenário.
> 
> 

### <a name="additional-report-tips"></a>Dicas adicionais sobre relatórios
* Use mais de um visual por página para filtragem cruzada  
* Alinhe os visuais cuidadosamente (sem sobreposição)  
* O layout da página é definido como "4:3" ou "16:9"  
* Todas as agregações apresentadas fazem sentido numérico (médias, valores exclusivos)  
* A divisão gera resultados racionais  
* O logotipo está presente pelo menos no relatório principal  
* Elementos estão no esquema de cores do cliente na medida do possível  

<a name="dashboard"></a>

## <a name="dashboard"></a>Painel
O painel é o principal ponto de interação com o pacote de conteúdo para seus clientes. Ele deve incluir uma visão geral do conteúdo incluído, especialmente as métricas importantes para seu cenário de negócios.

Para criar um painel para seu pacote de conteúdo de modelo, basta carregar seu PBIX por meio de Obter Dados > Arquivos ou publicar diretamente do Power BI Desktop.

> [!NOTE]
> Pacotes de conteúdo de modelo atualmente exigem um único relatório e conjunto de dados por pacote de conteúdo. Não fixe o conteúdo de vários relatórios/conjuntos de dados no painel usado no pacote de conteúdo.
> 
> 

### <a name="additional-dashboard-tips"></a>Dicas adicionais sobre painéis
* Mantenha o mesmo tema ao fixar, de forma que os blocos em seu painel sejam consistentes  
* Fixe um logotipo ao tema para que os consumidores saibam qual é a procedência do pacote  
* O layout sugerido para trabalhar com a maioria das resoluções de tela tem uma largura de 5 a 6 pequenos blocos  
* Todos os blocos de painel devem ter legendas/títulos apropriados  
* Considere a possibilidade de agrupamentos no painel para diferentes cenários, vertical ou horizontalmente  

<a name="restrictions"></a>

## <a name="summary-of-restrictions"></a>Resumo de restrições
Conforme listado nas seções acima, atualmente os pacotes de conteúdo de modelo têm algumas restrições:  

| Com suporte | *Sem suporte* |
| --- | --- |
| Conjuntos de dados criados no Power BI Desktop |*Conjuntos de dados de outros pacotes de conteúdo ou entradas, como arquivos do Excel* |
| Fonte de dados com suporte para a atualização de dados agendada na nuvem |*Não há suporte para a consulta direta nem a conectividade local* |
| As consultas retornam esquemas consistentes ou erros quando apropriado |*Esquemas personalizadas ou dinâmicos* |
| Uma fonte de dados por conjunto de dados |*Várias fontes de dados como mashups ou URLs que são detectadas como fontes de dados múltiplas* |
| Parâmetros do tipo texto |*Outros tipos de parâmetro (como data) ou "lista de valores permitidos"* |
| Um painel, relatório e conjunto de dados |*Vários dashboards, relatórios ou conjuntos de dados* |

## <a name="next-step"></a>Próxima etapa
[Teste e envio de pacote de conteúdo](template-content-pack-testing.md)

