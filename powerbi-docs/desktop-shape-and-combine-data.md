---
title: Formatar e combinar dados de várias fontes
description: Neste tutorial, você aprenderá a formatar e combinar dados no Power BI Desktop
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: tutorial
ms.date: 05/03/2018
ms.author: davidi
LocalizationGroup: Transform and shape data
ms.openlocfilehash: 27479add7839e1078e76bbb6523b287f10194566
ms.sourcegitcommit: 80d6b45eb84243e801b60b9038b9bff77c30d5c8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34288741"
---
# <a name="tutorial-shape-and-combine-data-in-power-bi-desktop"></a>Tutorial: Formatar e combinar dados no Power BI Desktop

Com o **Power BI Desktop**, você pode se conectar a vários tipos diferentes de fontes de dados e formatar esses dados para atender às suas necessidades, possibilitando que você crie relatórios visuais para compartilhar com outras pessoas. *Formatar* dados significa transformá-los – como renomear colunas ou tabelas, converter o texto em números, remover linhas, definir a primeira linha como títulos e assim por diante. *Combinar* dados significa conectar-se a duas ou mais fontes de dados, formatá-las conforme o necessário e consolidá-las em uma consulta útil.

Neste tutorial, você aprenderá a:

* Formatar dados usando o **Editor de Consultas**
* Conectar-se a uma fonte de dados
* Conectar-se a outra fonte de dados
* Combinar essas fontes de dados e criar um modelo de dados a ser usado em relatórios

Este tutorial demonstra como formatar uma consulta usando o Power BI Desktop, destacando algumas das tarefas mais comuns. A consulta usada aqui é descrita mais detalhadamente, incluindo como criar a consulta do zero, em [Introdução ao Power BI Desktop](desktop-getting-started.md).

É útil saber que o **Editor de Consultas** no Power BI Desktop faz uso abundante tanto de menus de atalho quanto da faixa de opções. A maioria das opções que você pode selecionar na faixa de opções **Transformar** também está disponível com um clique do botão direito do mouse em um item (como uma coluna) e a seleção no menu que é exibido.

## <a name="shape-data"></a>Formatar dados
Ao formatar dados no Editor de Consultas, você fornece instruções passo a passo (que o Editor de Consultas executa para você) para ajustar os dados conforme são carregados e apresentados pelo Editor de Consultas. A fonte de dados original não é afetada; apenas esta exibição específica dos dados é ajustada, ou *formatada*.

As etapas especificadas (como renomear uma tabela, transformar um tipo de dados ou excluir colunas) são registradas pelo Editor de Consultas. Sempre que essa consulta se conectar à fonte de dados, essas etapas serão executadas para que os dados sejam sempre formatados da maneira especificada. Esse processo ocorre sempre que você usa o recurso Editor de Consultas no Power BI Desktop, ou para qualquer pessoa que usa sua consulta compartilhada, como no serviço do **Power BI** Essas etapas são capturadas sequencialmente no painel **Configurações de Consulta**, em **Etapas Aplicadas**.

A imagem a seguir mostra o painel **Configurações de Consulta** para uma consulta que foi formatada – abordaremos cada uma dessas etapas nos próximos parágrafos.

![](media/desktop-shape-and-combine-data/shapecombine_querysettingsfinished2.png)

Com os dados de aposentadoria da [Introdução ao Power BI Desktop](desktop-getting-started.md), que encontramos ao nos conectarmos a uma fonte de dados da Web, vamos formatá-los para que eles adaptem às nossas necessidades.

Para começar, vamos adicionar uma coluna personalizada para calcular a classificação com base em todos os dados sendo fatores iguais, e vamos comparar isso com a coluna existente _Classificação_.  Esta é a faixa de opções de **Adicionar Coluna**, com uma seta apontando para o botão **Coluna Personalizada**, que permite a adição de uma coluna personalizada.

![](media/desktop-shape-and-combine-data/shapecombine_customcolumn.png)

Na caixa de diálogo **Coluna Personalizada**, em **Nome da nova coluna**, insira _Nova Classificação_ e, em **Fórmula de coluna personalizada**, digite o seguinte:

    ([Cost of living] + [Weather] + [Health care quality] + [Crime] + [Tax] + [Culture] + [Senior] + [#"Well-being"]) / 8

Verifique se a mensagem de status indica _"Nenhum erro de sintaxe foi detectado."_ e clique em **OK**.

![](media/desktop-shape-and-combine-data/shapecombine_customcolumndialog.png)

Para manter os dados da coluna consistentes, permita a transformação dos valores da nova coluna em números inteiros. Basta clicar com o botão direito do mouse no título da coluna e selecionar **Alterar Tipo \> Número Inteiro** para alterá-los. 

Se você precisar escolher mais de uma coluna, primeiro selecionamos uma coluna, mantemos pressionada a tecla **SHIFT**, selecionamos colunas adjacentes adicionais e clicamos com o botão direito do mouse em um título de coluna para alterar todas as colunas selecionadas. Você também pode usar a tecla **CTRL** para escolher colunas não adjacentes.

![](media/desktop-shape-and-combine-data/shapecombine_changetype2.png)

Você também pode *transformar* os tipos de dados de coluna na faixa de opções de **Transformar**. Esta é a faixa de opções **Transformar** , com uma seta apontando para o botão **Tipo de Dados** , que permite transformar o tipo de dados atual em outro.

![](media/desktop-shape-and-combine-data/queryoverview_transformribbonarrow.png)

Observe que em **Configurações de Consulta**, as **Etapas Aplicadas** refletem todas as etapas de formatação aplicadas aos dados. Se eu desejar remover qualquer etapa do processo de formatação, basta eu selecionar o **X** à esquerda da etapa. Na imagem a seguir, **Etapas Aplicadas** reflete as etapas realizadas até agora: conectar-se ao site (**Fonte**), selecionar a tabela (**Navegação**) e, ao carregar a tabela, o Editor de Consulta alterou automaticamente as colunas com números em formato de texto, de *Texto* para *Número Inteiro* (**Tipo Alterado**). As duas últimas etapas mostram nossas ações anteriores com **Personalização Adicionada** e **Tipo Alterado1**. 

![](media/desktop-shape-and-combine-data/shapecombine_appliedstepsearly2.png)

Antes que possamos trabalhar com essa consulta, precisamos fazer algumas alterações para colocar os dados nela contidos aonde desejamos:

* *Ajustar as classificações removendo uma coluna* – decidimos que **Custo de vida** é um não fator em nossos resultados. Depois de remover essa coluna, percebemos o problema de que os dados permanecem inalterados, apesar de ser fácil de corrigir usando o Power BI Desktop, e demonstre um recurso interessante das **Etapas Aplicadas** na Consulta.
* *Corrigir alguns erros* – já que removemos uma coluna, precisamos reajustar nossos cálculos na coluna **Nova Classificação**. Isso envolve a alteração de uma fórmula.
* *Classificar os dados* – com base nas colunas **Nova Classificação** e **Classificação**. 
* *Substituir dados* – vamos destacar como substituir um valor específico, e a necessidade de inserir uma **Etapa Aplicada**.
* *Alterar o nome da tabela* – **Tabela 0** não é um descritor útil, mas é simples modificá-lo.

Para remover a coluna **Custo de vida**, basta selecionar a coluna e escolher a guia **Página Inicial** na faixa de opções, depois **Remover Colunas**, como mostra a figura a seguir.

![](media/desktop-shape-and-combine-data/shapecombine_removecolumnscostofliving.png)

Observe que os valores de _Nova Classificação_ não foram alterados; isso ocorre devido à ordem das etapas. Já que o Editor de Consultas registra as etapas sequencialmente, porém de modo independente uma da outra, você pode mover cada **Etapa Aplicada** na sequência, para cima ou para baixo. Basta clicar com o botão direito do mouse em qualquer etapa para que o Editor de Consultas exiba um menu que permite que você faça o seguinte: **Renomear**, **Excluir**, **Excluir** **Até o Final** (remover a etapa atual e todas as etapas subsequentes também) **Mover para Cima**ou **Mover para Baixo**. Vá em frente e mova a última etapa, _Colunas Removidas_ para cima da etapa _Personalização Adicionada_.

![](media/desktop-shape-and-combine-data/shapecombine_movestep.png)

Em seguida, selecione a etapa _Personalização Adicionada_. Observe que agora os dados mostram _Erro_, o qual precisamos resolver. 

![](media/desktop-shape-and-combine-data/shapecombine_error2.png)

Existem algumas maneiras de obter mais informações sobre cada erro. É possível selecionar a célula (sem clicar na palavra **Erro**) ou clicar diretamente na palavra **Erro** . Se você selecionar a célula *sem* clicar diretamente na palavra **Erro**, o Editor de Consultas exibirá as informações de erro na parte inferior da janela.

![](media/desktop-shape-and-combine-data/shapecombine_errorinfo2.png)

Se você clicar na palavra *Erro* diretamente, a Consulta criará uma **Etapa Aplicada** no painel **Configurações de Consulta** e exibirá informações sobre o erro. Não queremos seguir esse caminho, portanto selecione **Cancelar**.

Para corrigir os erros, selecione a coluna _Nova Classificação_, depois exiba a fórmula de dados da coluna abrindo a faixa de opções **Exibição** e marcando a caixa de seleção **Barra de fórmulas**. 

![](media/desktop-shape-and-combine-data/shapecombine_formulabar.png)

Agora você pode remover o parâmetro _Custo de vida_ e diminuir o divisor, alterando a fórmula a seguir: 

    Table.AddColumn(#"Removed Columns", "New Rank", each ([Weather] + [Health care quality] + [Crime] + [Tax] + [Culture] + [Senior] + [#"Well-being"]) / 7)

Selecione a marca de seleção verde à esquerda da caixa fórmula ou pressione **Enter**, e os dados deverão ser substituídos por valores revisados e, agora, a etapa **Personalização Adicionada** deve ser concluída *sem erros* .

> [!NOTE]
> Você também pode **Remover Erros** (usando a faixa de opções ou o menu de clique com o botão direito do mouse), que remove linhas com erros. Nesse caso, ele teria removido todas as linhas de nossos dados, e esse não era nosso objetivo, gostamos de todos os nossos dados e queremos mantê-los na tabela.

Agora temos que classificar os dados com base na coluna **Nova Classificação**. Primeiro, selecione a última etapa aplicada, **Tipo1 Alterado** para obter os dados mais recentes. Em seguida, selecione a lista suspensa ao lado do cabeçalho de coluna **Nova Classificação** e selecione **Classificar em Ordem Crescente**.

![](media/desktop-shape-and-combine-data/shapecombine_sort.png)

Observe que agora os dados estão classificados de acordo com a **Nova Classificação**.  No entanto, se você examinar a coluna **Classificação**, perceberá que os dados não estão classificados corretamente em casos nos quais o valor de **Nova Classificação** é um horário. Para corrigir isso, selecione a coluna **Nova Classificação** e altere a fórmula na **Barra de Fórmulas** para o seguinte:

    = Table.Sort(#"Changed Type1",{{"New Rank", Order.Ascending},{"Rank", Order.Ascending}})

Selecione a marca de seleção verde à esquerda da caixa fórmula ou pressione **Enter**, e as linhas agora devem ser ordenadas de acordo com _Nova Classificação_ e _Classificação_.

Além disso, é possível selecionar uma **Etapa Aplicada** em qualquer lugar na lista e continuar formatando os dados nesse ponto na sequência. O Editor de Consultas inserirá automaticamente uma nova etapa diretamente após a **Etapa Aplicada**selecionada no momento. Vamos experimentar.

Primeiro, selecione a **Etapa Aplicada** anterior à adição da coluna personalizada; seria a etapa _Colunas Removidas_. Aqui, substituiremos o valor da classificação _Clima_ no Arizona. Clique com o botão direito na célula apropriada que contém a classificação _Clima_ e selecione *Substituir Valores...* no menu exibido. Observe qual **Etapa Aplicada** está selecionada no momento (a etapa anterior à etapa _Personalização Adicionada_).

![](media/desktop-shape-and-combine-data/shapecombine_replacevalues2.png)

Já que estamos inserindo uma etapa, o Editor de Consultas nos avisa sobre o perigo de fazer isso: etapas subsequentes poderiam causar uma fragmentação da consulta. Precisamos ser cuidadosos e ponderados! Como este é um tutorial e nós estamos enfatizando um recurso realmente interessante do Editor de Consultas para demonstrar como você pode criar, excluir, inserir e reorganizar as etapas, vamos continuar em frente e selecionar **Inserir**.

![](media/desktop-shape-and-combine-data/shapecombine_insertstep.png)

Altere o valor para _51_ e os dados para Arizona são substituídos. Quando você cria uma nova Etapa Aplicada, o Editor de Consultas a nomeia com base na ação - nesse caso, **Valor Substituído**. Quando você tem mais de uma etapa com o mesmo nome em sua consulta, o Editor de Consultas adiciona um número (em sequência) a cada **Etapa Aplicada** subsequente, para diferenciá-las.

Agora, selecione a última **Etapa Aplicada**, _Linhas Classificadas_ e observe que os dados mudaram com relação à nova classificação do Arizona.  Isso ocorre porque inserimos a etapa _Valor Substituído_ no local correto, antes da etapa _Personalização Adicionada_.

Tudo bem que foi um pouco complexo, mas ainda assim foi um bom exemplo de quão poderoso e versátil o Editor de Consultas pode ser.

Por fim, desejamos alterar o nome dessa tabela para algo descritivo. Ao criar relatórios, é especialmente útil ter nomes de tabela descritivos, principalmente quando nos conectamos a várias fontes de dados e eles estão listados no painel **Campos** da exibição **Relatório** .

É fácil alterar o nome da tabela: no painel **Configurações de Consulta** , em **Propriedades**, basta digitar o novo nome da tabela, como mostrado na imagem a seguir, e pressionar **Enter**. Vamos chamar essa tabela de *RetirementStats*.

![](media/desktop-shape-and-combine-data/shapecombine_renametable2.png)

Muito bem, a formatação desses dados foi realizada na medida necessária. Em seguida, vamos nos conectar a outra fonte de dados e combinar dados.

## <a name="combine-data"></a>Combinar dados
Esses dados sobre vários estados são interessantes e serão úteis para a criação de consultas e esforços de análise adicionais. Mas há um problema: a maioria dos dados usam uma abreviação de duas letras para códigos de estado, em vez de utilizar o nome completo do estado. Precisamos de alguma maneira de associar os nomes de estado às suas abreviações.

Estamos com sorte: há outra fonte de dados pública que faz exatamente isso, mas ela também precisa de um tanto considerável de formatação antes que possamos conectá-la à nossa tabela de aposentadoria. Eis o recurso da Web para abreviações de estado:

<http://en.wikipedia.org/wiki/List_of_U.S._state_abbreviations>

Na faixa de opções **Página Inicial** no Editor de Consultas, selecionamos **Nova Fonte \> Web** e digitamos o endereço, selecionamos **Conectar** para o Navegador mostrar o que ele encontrou nessa página da Web.

 ![](media/desktop-shape-and-combine-data/designer_gsg_usstateabbreviationsnavigator2.png)

Selecionamos **Códigos e abreviações...** porque isso inclui os dados que queremos, mas será necessária bastante formatação para que os dados da tabela sejam equivalentes ao que desejamos.

> [!TIP]
> Há uma maneira mais rápida ou mais fácil de realizar as etapas abaixo? Sim, podemos criar uma *relação* entre as duas tabelas e formatar os dados com base nessa relação. As etapas a seguir ainda são válidas para aprender a trabalhar com tabelas, mas saiba que as relações podem ajudá-lo rapidamente a usar os dados de várias tabelas.
> 
> 

Para formatar esses dados, realizamos as seguintes etapas:

* Remover a primeira linha – ela é resultado do modo como a tabela da página Web foi criada, e não precisamos dela. Na faixa de opções **Página Inicial**, selecione **Reduzir Linhas\> Remover Linhas \> Remover Primeiras Linhas**.

![](media/desktop-shape-and-combine-data/shapecombine_removetoprows.png)

A janela **Remover Primeiras Linhas** é exibida, permitindo que você especifique o número de linhas que deseja remover.

>[!NOTE]
>Se, acidentalmente, o Power BI importar os cabeçalhos de tabela como uma linha em sua tabela de dados, você pode selecionar **Usar Primeira Linha como Cabeçalho** da guia **Página Inicial**, ou na guia **Transformar** na faixa de opções, para corrigir a tabela.

* Remova as últimas 26 linhas – são todas referentes a territórios, que não precisamos incluir. Na faixa de opções **Página Inicial**, selecione **Reduzir Linhas \> Remover Linhas \> Remover Últimas Linhas**.

![](media/desktop-shape-and-combine-data/shapecombine_removebottomrows.png)

* Como a tabela RetirementStats não tem informações de Washington D.C., precisamos filtrá-la de nossa lista. Selecione a seta suspensa ao lado da coluna Status de Região e desmarque a caixa de seleção ao lado de **Distrito federal**.

![](media/desktop-shape-and-combine-data/shapecombine_filterdc.png)

* Remova algumas colunas desnecessárias – precisamos apenas do mapeamento do estado para sua abreviação oficial de duas letras, para que possamos remover as seguintes colunas: **Column1**, **Column3**, **Column4** e **Column6** até **Column11**. Primeiro, selecione **Column1**, mantenha pressionada a tecla **CTRL** e selecione as outras colunas a serem removidas (isso permite que você selecione várias colunas não contíguas). Na guia Página Inicial da faixa de opções, selecione **Remover Colunas \> Remover Colunas**.

![](media/desktop-shape-and-combine-data/shapecombine_removecolumns.png)

>[!NOTE]
>Esse é um bom momento para destacar que a *sequência* de etapas aplicadas no Editor de Consultas é importante e pode afetar o modo de formatação dos dados. Também é importante considerar como uma etapa pode afetar outra etapa subsequente; se você remover uma etapa das Etapas Aplicadas, as etapas subsequentes podem não se comportar como pretendido originalmente, devido ao impacto da sequência de etapas da consulta.

>[!NOTE]
>Ao redimensionar a janela do Editor de Consultas para diminuir a largura, alguns itens de faixa de opções são condensados para fazer o melhor uso do espaço visível. Ao aumentar a largura da janela do Editor de Consultas, os itens da faixa de opções são expandidos para fazer o melhor uso da área aumentada da faixa de opções.

* Renomear as colunas e a própria tabela – como de costume, há duas maneiras de renomear uma coluna: primeiro selecione a coluna e depois selecione **Renomear** na guia **Transformar** da faixa de opções ou clique com o botão direito do mouse e selecione **Renomear...** no menu exibido. A imagem a seguir tem setas apontando para ambas as opções; você precisa escolher apenas uma.

![](media/desktop-shape-and-combine-data/shapecombine_rename.png)

Vamos renomeá-las para *Nome do Estado* e *Código do Estado*. Para renomear a tabela, basta digitar o nome na caixa **Nome** do painel **Configurações de Consulta** . Vamos chamar essa tabela de *StateCodes*.

Agora que nós já formatamos a tabela StateCodes como desejamos, vamos combinar essas duas tabelas, ou consultas, em uma; como as tabelas que temos agora são o resultado das consultas que aplicamos aos dados, elas geralmente são designadas como *consultas*.

Há duas maneiras principais de combinar consultas – *mesclando* e *acrescentando*.

Quando você tem uma ou mais colunas que deseja adicionar a outra consulta, você **mescla** as consultas. Quando você tem linhas adicionais de dados que deseja adicionar a uma consulta existente, você **acrescenta** a consulta.

Nesse caso, desejamos mesclar consultas. Para começar, no painel esquerdo do Editor de Consultas, selecione a consulta *na qual* queremos que a outra consulta seja mesclada, que nesse caso é *RetirementStats*. Em seguida, selecione **Combinar \> Mesclar Consultas** na guia **Página Inicial** da faixa de opções.

![](media/desktop-shape-and-combine-data/shapecombine_mergequeries.png)

Você poderá ser solicitado a definir os níveis de privacidade, para garantir que os dados sejam combinados sem a inclusão ou transferência de dados que você não quer que sejam transferidos.

Em seguida, a janela **Mesclar** é exibida, solicitando que selecionemos qual tabela gostaríamos de mesclar à tabela selecionada e as colunas correspondentes a serem usadas para a mesclagem. Selecione State na tabela *RetirementStats* (consulta) e selecione a consulta *StateCodes* (fácil nesse caso, já que há somente mais uma consulta – quando você se conectar a várias fontes de dados, existirão muitas consultas entre as quais escolher). Quando selecionamos as colunas correspondentes corretas – **State** de *RetirementStats*, e **State Name** de *StateCodes* – a janela **Mesclar** tem a aparência semelhante à mostrada a seguir e o botão **OK** é habilitado.

![](media/desktop-shape-and-combine-data/shapecombine_merge2.png)

Uma **NewColumn** é criada no final da consulta, que consiste no conteúdo da tabela (consulta) que foi mesclada com a consulta existente. Todas as colunas da consulta mesclada são condensadas na **NewColumn**, mas você pode optar por **Expandir** a tabela e incluir quaisquer colunas que desejar.

![](media/desktop-shape-and-combine-data/shapecombine_mergenewcolumn.png)

Para expandir a tabela mesclada e selecionar quais colunas deseja incluir, selecione o ícone de expansão (![Expandir](media/desktop-shape-and-combine-data/icon.png)). A janela **Expandir** é exibida.

![](media/desktop-shape-and-combine-data/shapecombine_mergeexpand.png)

Nesse caso, como só queremos a coluna **State Code** , selecionamos apenas essa coluna e, em seguida, selecionamos **OK**. Desmarcamos a caixa de seleção Usar nome da coluna original como prefixo, porque não precisamos nem desejamos essa opção; se deixarmos essa opção selecionada, a coluna mesclada será nomeada **NewColumn.State Code** (o nome da coluna original ou **NewColumn**, seguido de um ponto e do nome da coluna que está sendo introduzida na consulta).

>[!NOTE]
>Quer experimentar como inserir a tabela **NewColumn**? Você pode experimentar um pouco e, se não gostar dos resultados, basta excluir essa etapa da lista **Etapas Aplicadas** no painel **Configurações de Consulta** ; sua consulta retornará ao estado anterior à aplicação dessa etapa **Expandir** . Você pode refazer essas ações livremente, quantas vezes desejar, até que o processo de expansão tenha a aparência desejada.

Agora temos uma única consulta (tabela) que combinou duas fontes de dados, cada uma das quais foi desenvolvida para atender às nossas necessidades. Essa consulta pode servir como base para muitas conexões de dados adicionais interessantes – como estatísticas de custo de moradia, dados demográficos ou oportunidades de trabalho em qualquer estado.

Para aplicar as alterações e fechar o Editor de Consultas, selecione **Fechar e Aplicar** na guia de faixa de opções **Página Inicial**. O conjunto de dados transformado aparece no Power BI Desktop, pronto para ser usado para a criação de relatórios.

![](media/desktop-shape-and-combine-data/shapecombine_closeandapply.png)

## <a name="next-steps"></a>Próximas etapas
Há inúmeras coisas que você pode fazer com o Power BI Desktop. Para obter mais informações sobre seus recursos, consulte as seguintes fontes:

* [Introdução ao Power BI Desktop](desktop-getting-started.md)
* [Visão geral de Consulta com o Power BI Desktop](desktop-query-overview.md)
* [Fontes de dados no Power BI Desktop](desktop-data-sources.md)
* [Conectar-se a dados no Power BI Desktop](desktop-connect-to-data.md)
* [Tarefas comuns de consulta no Power BI Desktop](desktop-common-query-tasks.md)   

