---
title: Criar e gerenciar relações no Power BI Desktop
description: Criar e gerenciar relações no Power BI Desktop
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 06/05/2018
ms.author: davidi
LocalizationGroup: Model your data
ms.openlocfilehash: f84e43a96243841b247530b5639f5f0c6ae1bb4f
ms.sourcegitcommit: 8ee0ebd4d47a41108387d13a3bc3e7e2770cbeb8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2018
ms.locfileid: "34813654"
---
# <a name="create-and-manage-relationships-in-power-bi-desktop"></a>Criar e gerenciar relações no Power BI Desktop
Quando você importa várias tabelas, é provável que você realize algumas análises usando dados de todas essas tabelas. Relações entre essas tabelas são necessárias para calcular os resultados com precisão e exibir as informações corretas em seus relatórios. O Power BI Desktop torna fácil a criação dessas relações. Na verdade, na maioria dos casos, você não precisará fazer nada - o recurso de Detecção Automática pode fazer isso por você. No entanto, em alguns casos, talvez você precise criar relações por conta própria, ou talvez seja necessário fazer algumas alterações em uma relação. De qualquer modo, é importante compreender as relações no Power BI Desktop e compreender como criá-las e editá-las.

## <a name="autodetect-during-load"></a>Detectar automaticamente durante o carregamento
Se você consultar duas ou mais tabelas ao mesmo tempo, quando os dados forem carregados, o Power BI Desktop tentará localizar e criar relações para você. A cardinalidade, a direção do filtro cruzado e as propriedades de relação ativa são definidas automaticamente. O Power BI Desktop procura nomes de colunas nas tabelas que você está consultando para determinar se há quaisquer relações em potencial. Se houver, essas relações serão criadas automaticamente. Se o Power BI Desktop não pode determinar com um alto nível de confiança que há uma correspondência, ele não criará automaticamente a relação. Você ainda pode usar a caixa de diálogo Gerenciar Relações para criar ou editar relações.

## <a name="create-a-relationship-by-using-autodetect"></a>Criar uma relação usando a Detecção Automática
Na guia **Página Inicial**, clique em **Gerenciar Relações** \> **Detectar Automaticamente**.

![](media/desktop-create-and-manage-relationships/automaticrelationship.gif)

## <a name="create-a-relationship-manually"></a>Criar uma relação manualmente
1. Na guia **Página Inicial**, clique em **Gerenciar Relações** \> **Nova**.
2. Na caixa de diálogo **Criar Relação**, na primeira lista suspensa de tabelas, selecione uma tabela e, em seguida, selecione a coluna que você deseja usar na relação.
3. Na segunda lista suspensa de tabelas, selecione a outra tabela que você deseja na relação, em seguida a outra coluna que você deseja usar, então clique em **OK**.

![](media/desktop-create-and-manage-relationships/manualrelationship2.gif)

Por padrão, o Power BI Desktop configurará automaticamente a Cardinalidade (direção), Direção do filtro cruzado e Propriedades ativas para sua nova relação; no entanto, você pode alterá-las se necessário. Para obter mais informações, consulte a seção Noções básicas sobre opções adicionais posteriormente neste artigo.

Observe que aparecerá um erro informando que *Uma das colunas precisa ter valores exclusivos* se nenhuma das tabelas selecionadas para a relação tiver valores exclusivos. Pelo menos uma tabela em uma relação *precisa* ter uma lista distinta e exclusiva de valores de chave, que é um requisito comum para todas as tecnologias de banco de dados relacional. 

Se você encontrar esse erro, haverá duas maneiras de corrigir o problema:

* Use "Remover Linhas Duplicadas" para criar uma coluna com valores exclusivos. A desvantagem dessa abordagem é que você perderá informações quando as linhas duplicadas forem removidas e, geralmente, há um bom motivo para que uma chave (linha) esteja duplicada.
* Adicione uma tabela intermediária composta pela lista de valores de chave distintos no modelo, que, em seguida, será vinculado às duas colunas originais na relação.

Para obter mais informações, confira a [postagem no blog](https://blogs.technet.microsoft.com/cansql/2016/12/19/relationships-in-power-bi-fixing-one-of-the-columns-must-have-unique-values-error-message/) que aborda isso detalhadamente.


## <a name="edit-a-relationship"></a>Editar uma relação
1. Na guia **Página Inicial** , clique em **Gerenciar Relações**.
2. Na caixa de diálogo **Gerenciar Relações** , selecione a relação e clique em **Editar**.

## <a name="configure-additional-options"></a>Configurar opções adicionais
Quando você cria ou edita uma relação, pode configurar opções adicionais.  Por padrão, as opções adicionais são configuradas automaticamente com base na melhor estimativa. Isso pode ser diferente para cada relação, com base nos dados contidos nas colunas.

## <a name="cardinality"></a>Cardinalidade
**Muitos para um (\*:1)** – Esse é o tipo padrão mais comum. Isso significa que a coluna em uma tabela pode ter mais de uma instância de um valor, enquanto a outra tabela relacionada, geralmente conhecida como a Tabela de pesquisa, tem apenas uma instância de cada valor.

**Um para um (1:1)** - isso significa que a coluna em uma tabela tem apenas uma instância de um determinado valor e que isso também ocorre na outra tabela relacionada.

Consulte a seção Noções básicas sobre opções adicionais, mais adiante neste artigo, para obter mais detalhes sobre quando alterar a cardinalidade.

## <a name="cross-filter-direction"></a>Direção do filtro cruzado
**Ambas** - essa é a direção padrão, mais comum. Isso significa que, para fins de filtragem, ambas as tabelas são tratadas como se fossem uma única tabela.  Isso funciona bem com uma única tabela que tem uma série de tabelas de pesquisa em torno dela.  Um exemplo é uma tabela de dados reais de Vendas com uma tabela de pesquisa por departamento.  Isso é frequentemente chamado de Configuração de esquema em estrela (uma tabela central com várias Tabelas de pesquisa).  No entanto, se você tiver duas ou mais tabelas que também têm tabelas de pesquisa (com algumas em comum), não seria vantajoso para você usar a configuração “Ambas”.  Para continuar o exemplo anterior, nesse caso, você também tem uma tabela de vendas de orçamento que registra o orçamento de destino para cada departamento.  E a tabela de departamento é conectada tanto à tabela de vendas quanto à de alocação.  Evite a configuração “Ambas” para esse tipo de configuração.

**Única** - isso significa que as opções de filtragem em tabelas conectadas funcionam na tabela na qual os valores estão sendo agregados. Se você importar uma tabela do Power Pivot no Excel 2013 ou um modelo de dados anterior, todas as relações terão uma única direção. 

Consulte a seção de opções adicionais Noções básicas, mais adiante neste artigo, para obter mais detalhes sobre quando alterar a direção do filtro cruzado.

## <a name="make-this-relationship-active"></a>Ativar este relacionamento
Quando marcada, isso significa que a relação serve como a relação ativa, padrão.  Em casos nos quais há mais de uma relação entre duas tabelas, a relação ativa fornece uma maneira para o Power BI Desktop criar automaticamente visualizações que incluem ambas as tabelas.

Veja a seção Noções básicas sobre opções adicionais mais adiante neste artigo para obter mais detalhes sobre quando tornar ativa uma relação específica.

## <a name="understanding-relationships"></a>Noções básicas sobre relações
Depois que você tiver conectado duas tabelas unindo-as com uma relação, você pode trabalhar com os dados em ambas as tabelas como se fossem uma única, não precisando mais se preocupar com detalhes da relação nem mesclar essas tabelas em uma única tabela antes de importá-las.  Em muitas situações, o Power BI Desktop pode criar relações automaticamente para você, ou seja, talvez nem seja necessário criar essas relações por conta própria. No entanto, se a área de trabalho do Power BI Desktop não puder determinar com alto grau de certeza que deve existir uma relação entre duas tabelas, ele não criará automaticamente a relação. Nesse caso, você precisará criar a relação.   

Vamos fazer um pequeno tutorial, para mostrar melhor como funcionam as relações no Power BI Desktop.

>[!TIP]
>Você pode concluir esta lição por conta própria. Copie a tabela ProjectHours abaixo em uma planilha do Excel, selecione todas as células, clique em **INSERIR** \> **Tabela**. Na caixa de diálogo **Criar Tabela** , clique em **OK**. Em seguida, em **Nome da Tabela**, digite **ProjectHours**. Faça o mesmo para a tabela CompanyProject. Em seguida, você pode importar os dados por meio de **Obter Dados** no Power BI Desktop. Selecione sua pasta de trabalho e tabelas como uma fonte de dados.

Esta primeira tabela, ProjectHours, é um registro de tíquetes de trabalho que gravam o número de horas que uma pessoa já trabalhou em um projeto específico.  

**ProjectHours**

| **Ticket** | **SubmittedBy** | **Hours** | **Project** | **DateSubmit** |
| ---:|:--- | ---:|:--- | ---:|
| 1001 |Alan Brewer |22 |Azul |1/1/2013 |
| 1002 |Alan Brewer |26 |Vermelho |2/1/2013 |
| 1003 |Shu Ito |34 |Amarelo |1242012 |
| 1004 |Alan Brewer |13 |Laranja |1/2/2012 |
| 1005 |Eli Bowen |29 |Roxo |1012013 |
| 1006 |Nuno Bento |35 |Verde |2/1/2013 |
| 1007 |David Hamilton |10 |Amarelo |1012013 |
| 1008 |Mu Han |28 |Laranja |1/2/2012 |
| 1009 |Shu Ito |22 |Roxo |2/1/2013 |
| 1010 |Eli Bowen |28 |Verde |1012013 |
| 1011 |Eli Bowen |9 |Azul |10/15/2013 |

Essa segunda tabela, CompanyProject, é uma lista de projetos aos quais é atribuída uma prioridade, A, B ou C. 

**CompanyProject**

| **ProjName** | **Priority** |
| --- | --- |
| Azul |A |
| Vermelho |B |
| Verde |C |
| Amarelo |C |
| Roxo |B |
| Laranja |C |

Observe que cada tabela tem uma coluna de projeto. Cada uma é nomeada de modo ligeiramente diferente, mas os valores parecem ser os mesmos. Isso é importante e retornaremos a esse assunto em breve.

Agora que temos nossas duas tabelas importadas para um modelo, vamos criar um relatório. A primeira coisa que queremos ter é o número de horas enviadas por prioridade do projeto, então vamos selecionar **Priority** e **Hours** em Campos.

 ![](media/desktop-create-and-manage-relationships/candmrel_reportfiltersnorel.png)

Se observarmos nossa tabela na tela Relatório, você verá que o número de horas é **256,00** para cada projeto e é também o total. Obviamente isso não é correto. Por que? É porque não podemos calcular uma soma total dos valores de uma tabela (Hours na tabela Project), dividida por valores em outra tabela (Priority na tabela CompanyProject) sem que exista uma relação entre essas duas tabelas.

Portanto, vamos criar uma relação entre essas duas tabelas.

Lembre-se das colunas que vimos em ambas as tabelas com um nome de projeto, mas com valores parecidos? Vamos usar essas duas colunas para criar uma relação entre nossas tabelas.

Por que essas colunas? Bem, se observarmos a coluna Projeto na tabela ProjectHours, vemos valores como Azul, Vermelho, Amarelo, Laranja e assim por diante. Na verdade, podemos ver várias linhas que têm o mesmo valor. Assim, temos muitos valores de cor para Project.

Se observarmos a coluna ProjName na tabela CompanyProject, vemos que há somente um de cada um dos valores de cor para Project. Cada valor de cor nesta tabela é exclusivo e isso é importante, porque podemos criar uma relação entre essas duas tabelas. Nesse caso, uma relação de tipo muitos para um. Em uma relação muitos para um, pelo menos uma coluna em uma das tabelas deve conter valores exclusivos. Há algumas opções adicionais para determinadas relações, e vamos analisá-las posteriormente, mas por enquanto, vamos criar uma relação entre as colunas Project em cada uma de nossas duas tabelas.

### <a name="to-create-the-new-relationship"></a>Para criar a nova relação
1. Clique em **Gerenciar Relacionamentos**.
2. Em **Gerenciar Relações**, clique em **Novo**. Isso abre a caixa de diálogo **Criar Relação**, na qual podemos selecionar tabelas, colunas e quaisquer configurações adicionais desejadas para nossa relação.
3. Na primeira tabela, selecione **ProjectHours**; em seguida, selecione a coluna **Project** . Este é o lado muitos de nossa relação.
4. Na segunda tabela, selecione **CompanyProject**, depois selecione a coluna **Project** . Este é o lado um de nossa relação.  
5. Vá em frente e clique em **OK** em ambas as caixas de diálogo **Criar Relação** e **Gerenciar Relações** .

![](media/desktop-create-and-manage-relationships/candmrel_create_compproj.png)

Buscando uma divulgação completa, acabamos na verdade criando essa relação da maneira mais difícil. Você poderia ter simplesmente clicado no botão Detecção Automática na caixa de diálogo Gerenciar Relações. Na verdade, a Detecção Automática já teria feito isso ao carregar os dados se ambas as colunas tivessem o mesmo nome. Mas qual é o desafio nisso?

Agora, vamos examinar novamente a tabela em nossa tela Relatório.

 ![](media/desktop-create-and-manage-relationships/candmrel_reportfilterswithrel.png)

Agora a aparência está muito melhor, não é?

Quando somamos as horas por prioridade, o Power BI Desktop procura cada instância dos valores de cor exclusivos na tabela de pesquisa CompanyProject, então procura cada instância de cada um desses valores na tabela CompanyProject; por fim, calcula uma soma total para cada valor exclusivo.

Foi bastante fácil; na verdade, com a Detecção Automática, talvez você nem precise chegar a fazer tudo isso.

## <a name="understanding-additional-options"></a>Noções básicas sobre opções adicionais
Quando uma relação é criada, seja com Detecção Automática ou manualmente por você, o Power BI Desktop configurará opções adicionais automaticamente com base nos dados de suas tabelas. Você pode configurar essas propriedades de relação adicionais localizadas na parte inferior da caixa de diálogo Criar/Editar relação.

 ![](media/desktop-create-and-manage-relationships/candmrel_advancedoptions2.png)

Como dissemos, elas geralmente são definidas automaticamente, e você não precisará lidar com elas; no entanto, há várias situações em que você talvez queira configurar essas opções por conta própria.

## <a name="future-updates-to-the-data-require-a-different-cardinality"></a>Atualizações futuras dos dados exigem uma cardinalidade diferente
Normalmente, o Power BI Desktop pode determinar automaticamente a melhor cardinalidade para a relação.  Se precisar substituir a configuração automática por saber que os dados serão alterados no futuro, você poderá selecioná-la no controle Cardinalidade. Vejamos um exemplo em que precisamos selecionar uma cardinalidade diferente.

A tabela CompanyProjectPriority abaixo é uma lista de todos os projetos da empresa, incluindo a prioridade de cada um. A tabela ProjectBudget é o conjunto de projetos para os quais o orçamento foi aprovado.

**ProjectBudget**

| **Approved Projects** | **BudgetAllocation** | **AllocationDate** |
|:--- | ---:| ---:|
| Azul |40.000 |1212012 |
| Vermelho |100.000 |1212012 |
| Verde |50.000 |1212012 |

**CompanyProjectPriority**

| **Project** | **Priority** |
| --- | --- |
| Azul |A |
| Vermelho |B |
| Verde |C |
| Amarelo |C |
| Roxo |B |
| Laranja |C |

Se criarmos uma relação entre a coluna Project na tabela CompanyProjectPriority e a coluna ApprovedProjects na tabela ProjectBudget, desse modo:

 ![](media/desktop-create-and-manage-relationships/candmrel_create_compproj_appproj2.png)

A cardinalidade é definida automaticamente como Um Para Um (1:1) e a direção da filtragem cruzada como “Ambas” (conforme mostrado).  Isso ocorre porque, para o Designer, a melhor combinação das duas tabelas agora tem essa aparência:

| **Project** | **Priority** | **BudgetAllocation** | **AllocationDate** |
|:--- | --- | ---:| ---:|
| Azul |A |40.000 |1212012 |
| Vermelho |B |100.000 |1212012 |
| Verde |C |50.000 |1212012 |
| Amarelo |C |<br /> |<br /> |
| Roxo |B |<br /> |<br /> |
| Laranja |C |<br /> |<br /> |

Há uma relação um para um entre nossas duas tabelas porque não há repetição de valores na coluna Project da tabela combinada. A coluna Project é exclusiva, porque cada valor ocorre apenas uma vez; portanto, as linhas das duas tabelas podem ser combinadas diretamente sem nenhuma duplicação.

Mas digamos que você saiba que os dados mudarão na próxima vez que você atualizá-los. Uma versão atualizada da tabela ProjectBudget agora tem linhas adicionais para Azul e Vermelho:

**ProjectBudget**

| **Approved Projects** | **BudgetAllocation** | **AllocationDate** |
| --- | ---:| ---:|
| Azul |40.000 |1212012 |
| Vermelho |100.000 |1212012 |
| Verde |50.000 |1212012 |
| Azul |80,000 |6/1/2013 |
| Vermelho |90,000 |6/1/2013 |

 Isso significa que a melhor combinação das duas tabelas agora tem essa aparência: 

| **Project** | **Priority** | **BudgetAllocation** | **AllocationDate** |
| --- | --- | ---:| ---:|
| Azul |A |40.000 |1212012 |
| Vermelho |B |100.000 |1212012 |
| Verde |C |50.000 |1212012 |
| Amarelo |C |<br /> |<br /> |
| Roxo |B |<br /> |<br /> |
| Laranja |C |<br /> |<br /> |
| Azul |A |80000 |6/1/2013 |
| Vermelho |B |90000 |6/1/2013 |

Nessa nova tabela combinada, há repetição de valores na coluna Project.  As duas tabelas originais não terão uma relação de tipo um para um depois que a tabela for atualizada. Nesse caso, por sabermos que as atualizações futuras farão com que a coluna de projeto tenha duplicatas, queremos definir a Cardinalidade como Muitos Para Um (\*:1), com Muitos no lado de ProjectBudget e Um no lado de CompanyProjectPriority.

## <a name="adjusting-cross-filter-direction-for-a-complex-set-of-tables-and-relationships"></a>Ajuste da direção de filtro cruzado para um conjunto complexo de tabelas e relações
Para a maioria das relações, a direção da filtragem cruzada é definida como ‘Ambas’.  No entanto, há algumas circunstâncias mais incomuns em que você talvez precise definir isso de modo diferente do padrão, como se você estivesse importando um modelo de uma versão anterior do PowerPivot, na qual cada relação é configurada para uma única direção. 

A configuração “Ambas” habilita o Power BI Desktop a tratar todos os aspectos das tabelas conectadas como se elas fossem uma única tabela.  Há algumas situações, porém, em que o Power BI Desktop não pode definir a direção de filtro cruzado da relação como ‘Ambas’ e, ao mesmo tempo, manter um conjunto inequívoco de padrões disponíveis para fins de relatório. Se a direção de filtro cruzado de uma relação não é definida como “Ambas”, isso geralmente ocorre porque tal configuração geraria ambiguidade.  Se a configuração padrão de filtro cruzado não está funcionando para você, você pode defini-la em direção a uma tabela específica ou “Ambas”.

A filtragem cruzada em uma única direção funciona em muitas situações.  Na verdade, se você importar um modelo do PowerPivot no Excel 2013 ou anterior, todas as relações estarão definidas para uma única direção.  O uso de uma única direção significa que as opções de filtragem, em tabelas conectadas, funcionam na tabela na qual está ocorrendo trabalho de agregação de valores.  Às vezes compreender a filtragem cruzada pode ser um pouco difícil, portanto, vamos examinar um exemplo.

 ![](media/desktop-create-and-manage-relationships/candmrel_singledircrossfiltering.png)

Com filtragem cruzada de direção única, se você criar um relatório que resume as horas de projeto, você poderá, em seguida, escolher resumir (ou filtrar) por CompanyProject, Priority ou CompanyEmployee, City.   Se, no entanto, você quiser contar o número de funcionários por projeto (uma pergunta menos comum), isso não funcionará. Você obterá uma coluna de valores todos iguais.  No exemplo a seguir, a direção da filtragem cruzada de ambas as relações está definida como uma única direção - em direção à tabela ProjectHours:

 ![](media/desktop-create-and-manage-relationships/candmrel_repcrossfiltersingle.png)

A especificação de filtro fluirá de CompanyProject para CompanyEmployee (conforme mostrado na imagem abaixo), porém, o fluxo não chegará até CompanyEmployee.  No entanto, se você definir a direção de filtragem cruzada como “Ambas”, ela funcionará.  A configuração “Ambas” permite que a especificação de filtro flua até Employee.

 ![](media/desktop-create-and-manage-relationships/candmrel_bidircrossfiltering.png)

Com a direção da filtragem cruzada definida como “Ambas”, nosso relatório agora parece correto:

 ![](media/desktop-create-and-manage-relationships/candmrel_repcrossfilterbi.png)

A filtragem cruzada em ambos os trajetos funciona bem para um padrão de relações de tabela que se parecem com o padrão acima. Isso é mais comumente chamado de um esquema em estrela, como esse:

 ![](media/desktop-create-and-manage-relationships/candmrel_crossfilterstarschema.png)

A direção de filtragem cruzada não funciona bem com um padrão mais geral encontrado com frequência em bancos de dados, como nesse diagrama:

 ![](media/desktop-create-and-manage-relationships/candmrel_crossfilterwithloops.png)

Se você tiver um padrão de tabela como este, com loops, então a filtragem cruzada pode criar um conjunto ambíguo de relações. Por exemplo, se você realiza a soma de um campo da Tabela X e, em seguida, opta por filtrar por um campo na Tabela Y, não fica claro o percurso que o filtro deve fazer: pela tabela superior ou pela inferior. Um exemplo comum para esse tipo de padrão é que a Tabela X seja uma tabela Sales com os dados efetivos e que Tabela Y seja de dados de orçamento. Em seguida, as tabelas no meio são tabelas de pesquisa utilizadas por ambas as tabelas, como Divisão ou Região. 

Assim como ocorre com relações ativas/inativas, o Power BI Desktop não permitirá que uma relação seja definida como “Ambas” se isso gerar ambiguidade em relatórios. Há várias maneiras diferentes de tratar disso. Estas são as duas mais comuns:

* Excluir ou marcar relações como inativas para reduzir a ambiguidade. Em seguida, talvez você possa definir a filtragem cruzada de uma relação como “Ambas”.
* Inclua uma tabela duas vezes (com um nome diferente na segunda vez) para eliminar os loops.  Isso torna o padrão de relações similar a um esquema em estrela.  Com um esquema em estrela, todas as relações podem ser definidas como Ambas.

## <a name="wrong-active-relationship"></a>Relação ativa errada
Quando o Power BI Desktop cria relações automaticamente, ele às vezes encontra mais de uma relação entre duas tabelas.  Quando isso acontece, apenas uma das relações é definida como ativa.  A relação ativa serve como a relação padrão para que, quando você escolher campos de duas tabelas diferentes, o Power BI Desktop possa criar automaticamente uma visualização para você.  No entanto, em alguns casos, a relação selecionada automaticamente pode estar errada.  Você pode usar a caixa de diálogo Gerenciar Relações para definir uma relação como ativa ou inativa, ou então definir a relação ativa na caixa de diálogo Editar relação. 

Para garantir que exista uma relação padrão, o Power BI Desktop permite apenas uma relação ativa entre duas tabelas em um determinado momento.  Portanto, você deve primeiro definir a relação atual como inativa e, em seguida, definir como ativa a relação desejada.

Vejamos um exemplo. Esta primeira tabela é ProjectTickets, a tabela a seguir é EmployeeRole.

**ProjectTickets**

| **Ticket** | **OpenedBy** | **SubmittedBy** | **Hours** | **Project** | **DateSubmit** |
| ---:|:--- |:--- | ---:|:--- | ---:|
| 1001 |Tom Perham |Alan Brewer |22 |Azul |1/1/2013 |
| 1002 |Daniel Romano |Alan Brewer |26 |Vermelho |2/1/2013 |
| 1003 |Daniel Roth |Shu Ito |34 |Amarelo |1242012 |
| 1004 |Tom Perham |Alan Brewer |13 |Laranja |1/2/2012 |
| 1005 |Daniel Romano |Eli Bowen |29 |Roxo |1012013 |
| 1006 |Daniel Roth |Nuno Bento |35 |Verde |2/1/2013 |
| 1007 |Daniel Roth |David Hamilton |10 |Amarelo |1012013 |
| 1008 |Tom Perham |Mu Han |28 |Laranja |1/2/2012 |
| 1009 |Daniel Romano |Shu Ito |22 |Roxo |2/1/2013 |
| 1010 |Daniel Roth |Eli Bowen |28 |Verde |1012013 |
| 1011 |Tom Perham |Eli Bowen |9 |Azul |10/15/2013 |

**EmployeeRole**

| **Employee** | **Função** |
| --- | --- |
| Nuno Bento |Gerente de projeto |
| Eli Bowen |Líder de projeto |
| Alan Brewer |Gerente de projeto |
| David Hamilton |Líder de projeto |
| Mu Han |Líder de projeto |
| Shu Ito |Líder de projeto |
| Tom Perham |Patrocinador de projeto |
| Daniel Romano |Patrocinador de projeto |
| Daniel Roth |Patrocinador de projeto |

Na verdade, existem duas relações aqui. Uma é entre SubmittedBy na tabela ProjectTickets e Employee na tabela EmployeeRole, enquanto a outra é entre OpenedBy na tabela ProjectTickets e Employee na tabela EmployeeRole.

 ![](media/desktop-create-and-manage-relationships/candmrel_activerelview.png)

Se adicionarmos ambas as relações no modelo (OpenedBy primeiro), a caixa de diálogo Gerenciar Relações mostrará em seguida que OpenedBy está ativa:

 ![](media/desktop-create-and-manage-relationships/candmrel_managerelactive.png)

Agora, se criarmos um relatório que usa os campos Role e Employee de EmployeeRole, e o campo Hours de ProjectTickets em uma visualização de tabela na tela Relatório, veremos apenas patrocinadores de projeto, porque eles são os únicos que têm um tíquete de projeto aberto.

 ![](media/desktop-create-and-manage-relationships/candmrel_repcrossfilteractive.png)

Podemos alterar a relação ativa e obter SubmittedBy em vez de OpenedBy. Em Gerenciar Relações, desmarcamos a relação entre ProjectTickets(OpenedBy) e EmployeeRole(Employee) e, em seguida, marcamos a relação entre Project Tickets(SubmittedBy) e EmployeeRole(Employee).

![](media/desktop-create-and-manage-relationships/candmrel_managerelactivesubmittedby.png)

## <a name="see-all-of-your-relationships-in-relationship-view"></a>Ver todas as relações na Exibição de Relação
Às vezes, seu modelo tem várias tabelas e relações complexas entre elas. A Exibição de Relação no Power BI Desktop mostra todas as relações em seu modelo, sua direção e cardinalidade em um diagrama fácil de entender e personalizável. Para saber mais, consulte [Exibição de Relações no Power BI Desktop](desktop-relationship-view.md).

