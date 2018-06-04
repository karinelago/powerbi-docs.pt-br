---
title: Uso e otimização de memória da capacidade do Power BI Premium
description: Compreenda a otimização e o gerenciamento de memória da capacidade do Power BI Premium.
ms.date: 04/30/2018
ms.topic: conceptual
ms.service: powerbi
ms.component: powerbi-admin
ms.author: susuresh
ms.reviewer: susuresh
author: suds001
manager: kfile
ms.openlocfilehash: 03c5e56c5f516bb1f09f51463d4c533185fbb63c
ms.sourcegitcommit: 80d6b45eb84243e801b60b9038b9bff77c30d5c8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34298448"
---
# <a name="power-bi-premium-capacity-resource-management-and-optimization"></a>Otimização e gerenciamento de recursos da capacidade do Power BI Premium

Este artigo descreve como o serviço do Power BI Premium gerencia recursos e fornece dicas de como planejar e otimizar sua solução.

## <a name="premium-capacity-memory-management"></a>Gerenciamento de memória da de capacidade Premium

 A memória da capacidade Premium é consumida por:

* Memória usada pelos conjuntos de dados carregados
* Memória usada por atualizações de conjuntos de dados (agendadas e sob demanda)
* Memória usada por consultas de relatório

Quando é emitida uma solicitação para um conjunto de dados publicado em sua capacidade, esse conjunto de dados é carregado na memória do armazenamento persistente (também chamado de carga de imagem). Manter o conjunto de dados carregado na memória ajuda a responder rapidamente a consultas futuras nesse conjunto de dados. Além da memória necessária para manter o conjunto de dados carregado na memória, consultas de relatório e atualizações de conjunto de dados também consomem memória adicional.

### <a name="dataset-memory-estimation"></a>Estimativa de memória de conjunto de dados

Ao tentar carregar um conjunto de dados na memória, o Power BI estima a quantidade de memória de que esse conjunto de dados precisará para concluir o comando solicitado. Conjuntos de dados na memória tendem a ser maiores do que quando estão salvos em disco. Durante a atualização de um conjunto de dados, a capacidade de memória requer pelo menos o dobro da quantidade de memória necessária quando ele está ocioso.

### <a name="overcommitting-capacity-eviction-and-reloading-of-datasets"></a>Superalocação de capacidade, remoção e recarregamento de conjuntos de dados

O Power BI Premium oferece a vantagem de superalocar sua capacidade. Por exemplo, você pode publicar mais conjuntos de dados do que a capacidade de memória pode reter. Se os conjuntos de dados publicados em sua capacidade precisarem de mais memória do que o disponível, alguns dos conjuntos de dados serão armazenados separadamente em um armazenamento persistente. O armazenamento persistente faz parte do armazenamento de 100 TB associado a cada uma de suas capacidades.

Sendo assim, quais conjuntos de dados permanecem na memória e o que acontece com os outros conjuntos de dados? Conforme descrito anteriormente, quando é emitida uma solicitação para um conjunto de dados, ele é carregado na memória (carga de imagem). A solicitação pode ser uma consulta de relatório ou uma operação de atualização.

Como você pode superalocar sua capacidade, ela também pode sofrer demanda de memória. Quando a capacidade sofre demanda de memória (porque um novo conjunto de dados precisa ser carregado ou as consultas em alguns conjuntos de dados carregados aumentam o requisito de memória), o nó *remove um ou mais conjuntos de dados* que ocupam a memória da capacidade. Conjuntos de dados inativos (ou seja, em que não há uma operação de consulta/atualização em execução) são removidos primeiro e a ordem de remoção é o padrão LRU (menos utilizado recentemente). Se novos comandos forem emitidos para o conjunto de dados removido, o serviço tentará recarregá-lo na memória, possivelmente removendo outros conjuntos de dados. Esse comportamento possibilita uma utilização mais eficiente, permitindo que a capacidade atenda muito mais conjuntos de dados do que a memória pode reter.

Carregar um conjunto de dados na memória é uma operação relativamente cara. Dependendo do tamanho do conjunto de dados, ela pode durar de alguns segundos para conjuntos de dados pequenos a dezenas de segundos ou até mesmo minutos para conjuntos de dados grandes, como conjuntos de dados de cerca de 10 GB. A capacidade Premium tenta minimizar o número de vezes que a capacidade precisa ser carregada mantendo os conjuntos de dados menos utilizados recentemente na memória pelo tempo que for possível. Quando memória adicional for necessária, alguns conjuntos de dados precisarão ser removidos e o sistema tentará escolher o que tem o menor impacto sobre a experiência do usuário. Quando memória adicional for necessária, alguns conjuntos de dados precisarão ser removidos e o sistema tentará escolher o que tem o menor impacto sobre a experiência do usuário. Por exemplo, o sistema evitará remover conjuntos de dados que foram usados ativamente nos últimos minutos, porque é provável que eles sejam consultados novamente muito em breve.

O processo de remoção em si é uma operação rápida. Se o conjunto de dados não estiver em uso no momento da remoção, o usuário não poderá determinar o impacto da remoção. No entanto, se muitos conjuntos de dados estiverem em uso ao mesmo tempo e não houver memória suficiente para manter todos, muita remoções poderão ocorrer. Isso pode levar a uma situação de “ultrapaginação ”, em que conjuntos de dados são removidos e recarregados constantemente, e os usuários podem ver uma queda notável no desempenho e um aumento nos tempos de resposta.

### <a name="dataset-refresh-memory-requirement-competing-with-an-active-dataset-memory-requirement"></a>Requisito de memória de atualização de conjunto de dados concorrendo com um requisito de memória de conjunto de dados ativo

Os conjuntos de dados podem ser atualizados segundo uma agenda ou sob demanda pelos usuários. Conforme descrito anteriormente, a memória necessária para realizar atualizações completas tem pelo menos o dobro do tamanho da memória consumida por conjuntos de dados carregados e ociosos. Antes do início da atualização, o requisito de memória de atualização será estimado. Se o requisito de memória total for maior do que a memória disponível na capacidade, alguns conjuntos de dados serão removidos. Os candidatos à remoção são escolhidos na ordem dos conjuntos de dados menos utilizados recentemente, ou seja, o serviço tenta manter na memória o máximo possível de conjuntos de dados usados recentemente.

Se a memória necessária não estiver disponível mesmo com a remoção, a atualização será colocada na fila para ser repetida. O serviço repete a tentativa até ser bem-sucedido ou até que uma nova ação de atualização comece.

Se uma consulta interativa for emitida para qualquer conjunto de dados na capacidade e não houver memória suficiente disponível devido a uma atualização em andamento, a solicitação falhará e deverá ser repetida pelo usuário.

## <a name="cpu-resource-management-in-premium-capacity"></a>Gerenciamento de recursos de CPU na capacidade Premium

Há dois consumidores principais dos recursos da CPU:

- Consultas de relatórios
- Atualização (processamento)

### <a name="queries-from-reports"></a>Consultas de relatórios

As consultas de relatório consomem recursos de CPU da sua capacidade. Se o relatório tiver algumas consultas ineficientes ou se você tiver muitos usuários simultâneos, muitos recursos de CPU poderão ser consumidos e sua capacidade existente poderá não ser suficiente para lidar com a carga.

### <a name="refresh-parallelization-policy"></a>Política de paralelização de atualização

A memória não é o único recurso que pode restringir a atualização de conjuntos de dados. O número de núcleos virtuais em um servidor também pode ser um fator. Como cada operação de atualização requer certo número de núcleos virtuais, há um limite para quantas atualizações podem ser executadas em paralelo. O limite por SKU é detalhado na tabela a seguir. Atualizações adicionais que forem além desses limites serão colocadas na fila.

 | SKU  | Núcleos virtuais de back-end  | Paralelismo de atualização de modelo   |
 | --- | --- | --- |
 | A1  | 0.5  | 1  |
 | A2  | 1  | 2  |
 | A3  | 2  | 3  |
 | A4  | 4  | 6  |
 | A5  | 8  | 12  |
 | A6  | 16  | 24  |
 | EM1  | 0.5  | 1  |
 | EM2  | 1  | 2  |
 | EM3  | 2  | 3  |
 | P1  | 4  | 6  |
 | P2  | 8  | 12  |
 | P3  | 16  | 24  |
 | P4  | 32  | 48  |
 | P5  | 64  | 96  |

 > [!TIP]
> Se as atualizações estiverem sofrendo atrasos, verifique o número de atualizações paralelas com suporte por sua capacidade.

## <a name="example-scenarios"></a>Cenários de exemplo

O exemplo a seguir descreve alguns cenários comuns e as ações executadas pelo serviço:

 **Vinte atualizações agendadas enviadas ao mesmo tempo** – O Power BI tenta iniciar as primeiras *x* atualizações ao mesmo tempo. O valor de *x* é determinado pela política de paralelização de atualização do SKU. Se o Power BI não puder obter memória suficiente removendo conjuntos de dados inativos (conjuntos de dados não usados recentemente), nem todas as *x* atualizações serão iniciadas ao mesmo tempo. Qualquer atualização que não puder ser iniciada será colocada na fila até que possa ser iniciada.

 **Duas atualizações estão em execução ao mesmo tempo e há memória suficiente para a conclusão de apenas uma** – A que pode ser concluída é iniciada. O outra será repetida mais tarde.

 **Grande número de conjuntos de dados sendo consultados enquanto vários conjuntos de dados são atualizados** – Se não houver memória suficiente disponível, o Power BI tentará interromper as atualizações ativas para dar prioridade a consultas interativas. Isso diminuirá o desempenho da atualização.

 **O conjunto de dados requer muita memória para ser atualizado no tamanho da capacidade atual** – A atualização falhará. Não são feitas tentativas de obter mais memória por meio de remoção.

 **Atualização de um único conjunto de dados que tem um grande pico na memória** – Se o pico for maior que a quantidade de memória que pode ser obtida pela remoção de conjuntos de dados inativos, a atualização será repetida mais tarde até que haja memória suficiente para lidar com o pico.

 **É executada uma consulta em um conjunto de dados que não é capaz de obter memória suficiente removendo todos os conjuntos de dados e atualizações inativos** – Essas consultas falharão. Para esses tipos de requisitos de carga de trabalho, uma maior capacidade deve ser adquirida.

## <a name="troubleshooting-and-testing"></a>Solução de problemas e testes

Se os relatórios estiverem lentos ou sem resposta, comece testando apenas um usuário em seu relatório. Depois, comece aumentar a carga de usuários simultâneos para encontrar o limite. Em muitos casos, ajustar seu DAX (consultas de relatório) pode alterar drasticamente o desempenho de seus relatórios (e aumentar o número de usuários simultâneos com suporte da capacidade).

Use a capacidade do Power BI Embedded no Azure para testar diferentes SKUs e determinar o melhor SKU Premium para sua carga de trabalho esperada. O SKU A4 do Power BI Embedded á igual ao P1, o A5 = P2 e o A6 = P3. No Azure, você pode mudar facilmente de SKUs escalando e reduzindo verticalmente no portal do Azure. Quando encontrar o SKU que funciona melhor para sua carga de trabalho e terminar os testes, você poderá excluir o SKU.

Em alguns casos, abrir um arquivo PBIX do modelo em seu computador e verificar o consumo de CPU e memória informa muito sobre o problema. Isso não ajuda para modelos muito grandes, mas para alguns modelos menores, tente abrir, atualizar e consultar o modelo de seu computador. Verifique o tamanho do modelo, a memória e a CPU consumida ao abrir o modelo. Tente atualizar e consultar. Use o Gerenciador de Tarefas para verificar o consumo de CPU e memória para o arquivo PBIX local. Às vezes, essas métricas em seu computador podem informar que capacidades Premium menores, como P1/P2, podem não funcionar para sua solução.
