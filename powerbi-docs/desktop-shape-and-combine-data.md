-- title: Formatar e combinar dados no Power BI Desktop description: Formatar e combinar dados em serviços do Power BI Desktop: powerbi documentationcenter: '' author: davidiseminger manager: kfile backup: '' editor: '' tags: '' qualityfocus: no qualitydate: ''

ms.service: powerbi ms.devlang: NA ms.topic: article ms.tgt_pltfrm: NA ms.workload: powerbi ms.date: 01/30/2018 ms.author: davidi

---
# <a name="shape-and-combine-data-in-power-bi-desktop"></a>Formatar e combinar dados no Power BI Desktop
Com o **Power BI Desktop**, você pode se conectar a vários tipos diferentes de fontes de dados e formatar esses dados para atender às suas necessidades. *Formatar* dados significa transformá-los – como renomear colunas ou tabelas, converter o texto em números, remover linhas, definir a primeira linha como títulos e assim por diante. *Combinar* dados significa conectar-se a duas ou mais fontes de dados, formatá-las conforme o necessário e consolidá-las em uma consulta útil.

Este documento demonstra como formatar uma consulta usando o Power BI Desktop, destacando algumas das tarefas mais comuns. A consulta usada aqui é descrita mais detalhadamente, incluindo como criar a consulta do zero, em [Introdução ao Power BI Desktop](desktop-getting-started.md).

É útil saber que o **Editor de Consultas** no Power BI Desktop faz uso abundante tanto de menus de atalho quanto da faixa de opções. A maioria das opções que você pode selecionar na faixa de opções **Transformar** também está disponível com um clique do botão direito do mouse em um item (como uma coluna) e a seleção no menu que é exibido.

## <a name="shape-data"></a>Formatar dados
Ao formatar dados no Editor de Consultas, você fornece instruções passo a passo (que o Editor de Consultas executa para você) para ajustar os dados conforme são carregados e apresentados pelo Editor de Consultas. A fonte de dados original não é afetada; apenas esta exibição específica dos dados é ajustada, ou *formatada*.

As etapas especificadas (como renomear uma tabela, transformar um tipo de dados ou excluir colunas) são registradas pelo Editor de Consultas. Sempre que essa consulta se conectar à fonte de dados, essas etapas serão executadas para que os dados sejam sempre formatados da maneira especificada. Esse processo ocorre sempre que você usa o recurso Editor de Consultas no Power BI Desktop, ou para qualquer pessoa que usa sua consulta compartilhada, como no serviço do **Power BI** Essas etapas são capturadas sequencialmente no painel **Configurações de Consulta**, em **Etapas Aplicadas**.

A imagem a seguir mostra o painel **Configurações de Consulta** para uma consulta que foi formatada – abordaremos cada uma dessas etapas nos próximos parágrafos.

![](media/desktop-shape-and-combine-data/shapecombine_querysettingsfinished.png)

Com os dados de aposentadoria da [Introdução ao Power BI Desktop](https://powerbi.uservoice.com/knowledgebase/articles/471664), que encontramos ao nos conectarmos a uma fonte de dados da Web, vamos formatá-los para que eles adaptem às nossas necessidades.

Para começar, as pontuações de uma coluna não foram transformadas automaticamente de texto em números quando o Editor de Consultas carregou a tabela, mas precisamos dessas pontuações como números. Sem problemas – basta clicar com o botão direito do mouse no título da coluna e selecionar **Alterar Tipo \> Número Inteiro** para alterá-los. Para escolher mais de uma coluna, primeiro selecionamos uma coluna, mantemos pressionada a tecla **SHIFT**, selecionamos colunas adjacentes adicionais e clicamos com o botão direito do mouse em um título de coluna para alterar todas as colunas selecionadas. Você também pode usar a tecla **CTRL** para escolher colunas não adjacentes.

![](media/desktop-shape-and-combine-data/shapecombine_changetype.png)

Você também pode *transformar* essas colunas de texto em título na faixa de opções **Transformar** . Esta é a faixa de opções **Transformar** , com uma seta apontando para o botão **Tipo de Dados** , que permite transformar o tipo de dados atual em outro.

![](media/desktop-shape-and-combine-data/queryoverview_transformribbonarrow.png)

Observe que em **Configurações de Consulta**, as **Etapas Aplicadas** refletem todas as etapas de formatação aplicadas aos dados. Se eu desejar remover qualquer etapa do processo de formatação, basta eu selecionar o **X** à esquerda da etapa. Na imagem a seguir, **Etapas Aplicadas** reflete as etapas realizadas até agora: conectar-se ao site (**Fonte**), selecionar a tabela (**Navegação**) e, ao carregar a tabela, o Editor de Consulta alterou automaticamente as colunas com números em formato de texto, de *Texto* para *Número Inteiro* (**Tipo Alterado**). Uma coluna de classificações não foi alterada automaticamente para um tipo de número, e descobriremos o porquê nos próximos parágrafos.

![](media/desktop-shape-and-combine-data/shapecombine_appliedstepsearly.png)

Antes que possamos trabalhar com essa consulta, precisamos fazer algumas alterações para colocar os dados nela contidos aonde desejamos:

* *Remover a primeira coluna* – ela não é necessária e inclui apenas linhas redundantes que indicam “Verifique qual a classificação do seu estado em relação à aposentadoria”, o que é um artefato por esta fonte de dados ser uma tabela baseada na Web
* *Corrigir alguns erros* – uma das colunas, **Qualidade de assistência médica**, contém alguns empates nas classificações de Estado, o que foi observado no site pela exibição do texto *(empate)* após seus números. Isso funciona bem no site, mas requer que transformemos manualmente a coluna de texto em dados. É fácil de corrigir esse problema usando o Power BI Desktop, e isso demonstra um recurso interessante de **Etapas Aplicadas** na Consulta
* *Alterar o Nome da Tabela* – **Tabela 0** não é um descritor útil, mas é simples modificá-lo

Para remover a primeira coluna, basta selecionar a coluna e escolher a guia **Página Inicial** na faixa de opções e **Remover Colunas** , como mostrado na figura a seguir.

![](media/desktop-shape-and-combine-data/shapecombine_removecolumnsretirement.png)

Em seguida, precisamos tratar da coluna de texto e transformá-la em números. Inicialmente, isso parece simples, já que podemos apenas alterar o tipo da coluna **Qualidade de assistência médica** de texto para número (como*Número Inteiro* ou *Número Decimal*). Mas quando alteramos o tipo de **Texto** para **Número Inteiro**e examinamos os valores nessa coluna, descobrimos que o Editor de Consultas relata alguns erros.

![](media/desktop-shape-and-combine-data/shapecombine_error.png)

Existem algumas maneiras de obter mais informações sobre cada erro. É possível selecionar a célula (sem clicar na palavra **Erro**) ou clicar diretamente na palavra **Erro** . Se você selecionar a célula *sem* clicar diretamente na palavra **Erro**, o Editor de Consultas exibirá as informações de erro na parte inferior da janela.

![](media/desktop-shape-and-combine-data/shapecombine_errorinfo.png)

Se você clicar na palavra *Erro* diretamente, a Consulta criará uma **Etapa Aplicada** no painel **Configurações de Consulta** e exibirá informações sobre o erro.

![](media/desktop-shape-and-combine-data/shapecombine_errorselect.png)

Para voltar ao Editor de Consultas, é necessário remover essa etapa selecionando o **X** ao lado dela.

Quando selecionamos a **Etapa Aplicada**mais recente, podemos ver o erro que acabamos de descrever, como mostrado na imagem a seguir.

![](media/desktop-shape-and-combine-data/shapecombine_querystep1.png)

Já que o Editor de Consultas registra as etapas sequencialmente, podemos selecionar a etapa em **Etapas Aplicadas**antes da alteração do tipo e ver qual é o valor da célula antes da conversão, como mostrado na imagem a seguir.

![](media/desktop-shape-and-combine-data/shapecombine_querystep2.png)

Tudo bem, agora podemos corrigir esses valores e *então* alterar o tipo. Já que o Editor de Consultas registra as etapas sequencialmente, porém de modo independente uma da outra, você pode mover cada **Etapa Aplicada** na sequência, para cima ou para baixo. Basta clicar com o botão direito do mouse em qualquer etapa para que o Editor de Consultas exiba um menu que permite que você faça o seguinte: **Renomear**, **Excluir**, **Excluir** **Até o Final** (remover a etapa atual e todas as etapas subsequentes também) **Mover para Cima**ou **Mover para Baixo**.

![](media/desktop-shape-and-combine-data/shapecombine_querystepreorder.png)

Além disso, é possível selecionar uma **Etapa Aplicada** em qualquer lugar na lista e continuar formatando os dados nesse ponto na sequência. O Editor de Consultas inserirá automaticamente uma nova etapa diretamente após a **Etapa Aplicada**selecionada no momento. Vamos experimentar.

Primeiro, selecionamos a **Etapa Aplicada** antes de alterar o tipo da coluna **Qualidade de assistência médica** . Em seguida, substituímos os valores com o texto "(empate)" na célula para que somente o número permaneça. Clique com o botão direito do mouse na célula que contém “35 (empate)” e selecione *Substituir Valores...* no menu exibido. Observe qual **Etapa Aplicada** está selecionada no momento (a etapa anterior à alteração do tipo).

![](media/desktop-shape-and-combine-data/shapecombine_replacevalues.png)

Já que estamos inserindo uma etapa, o Editor de Consultas nos avisa sobre o perigo de fazer isso: etapas subsequentes poderiam causar uma fragmentação da consulta. Precisamos ser cuidadosos e ponderados! Como este é um tutorial e nós estamos enfatizando um recurso realmente interessante do Editor de Consultas para demonstrar como você pode criar, excluir, inserir e reorganizar as etapas, vamos continuar em frente e selecionar **Inserir**.

![](media/desktop-shape-and-combine-data/shapecombine_insertstep.png)

Há três empates, portanto, substituímos os valores para cada um. Quando você cria uma nova Etapa Aplicada, o Editor de Consultas a nomeia com base na ação - nesse caso, **Valor Substituído**. Quando você tem mais de uma etapa com o mesmo nome em sua consulta, o Editor de Consultas adiciona um número (em sequência) a cada **Etapa Aplicada** subsequente, para diferenciá-las.

A tela a seguir mostra as três etapas de **Valor Substituído** nas **Configurações de Consulta**, mas ela também mostra algo que é ainda mais interessante: já que removemos todas as instâncias do texto “(empate)” na coluna **Qualidade de assistência médica** , a etapa **Tipo Alterado** agora é concluída *sem erros*.

![](media/desktop-shape-and-combine-data/shapecombine_replacedvaluesok.png)

> [!NOTE]
> Você também pode **Remover Erros** (usando a faixa de opções ou o menu de clique com o botão direito do mouse), que remove linhas com erros. Nesse caso, ele teria removido todos os Estados contendo “ *(empate)* ” de nossos dados, e não queremos fazer isso – apreciamos todos os Estados e desejamos mantê-los na tabela.

Tudo bem que foi um pouco complexo, mas ainda assim foi um bom exemplo de quão poderoso e versátil o Editor de Consultas pode ser.

Por fim, desejamos alterar o nome dessa tabela para algo descritivo. Ao criar relatórios, é especialmente útil ter nomes de tabela descritivos, principalmente quando nos conectamos a várias fontes de dados e eles estão listados no painel **Campos** da exibição **Relatório** .

É fácil alterar o nome da tabela: no painel **Configurações de Consulta** , em **Propriedades**, basta digitar o novo nome da tabela, como mostrado na imagem a seguir, e pressionar **Enter**. Vamos chamar essa tabela de *RetirementStats*.

![](media/desktop-shape-and-combine-data/shapecombine_renametable.png)

Muito bem, a formatação desses dados foi realizada na medida necessária. Em seguida, vamos nos conectar a outra fonte de dados e combinar dados.

## <a name="combine-data"></a>Combinar dados
Esses dados sobre vários estados são interessantes e serão úteis para a criação de consultas e esforços de análise adicionais. Mas há um problema: a maioria dos dados usam uma abreviação de duas letras para códigos de estado, em vez de utilizar o nome completo do estado. Precisamos de alguma maneira de associar os nomes de estado às suas abreviações.

Estamos com sorte: há outra fonte de dados pública que faz exatamente isso, mas ela também precisa de um tanto considerável de formatação antes que possamos conectá-la à nossa tabela de aposentadoria. Eis o recurso da Web para abreviações de estado:

<http://en.wikipedia.org/wiki/List_of_U.S._state_abbreviations>

Na faixa de opções **Página Inicial** no Editor de Consultas, selecionamos **Nova Fonte \> Web** e digitamos o endereço, selecionamos OK para o Navegador mostrar o que ele encontrou nessa página da Web.

 ![](media/desktop-shape-and-combine-data/designer_gsg_usstateabbreviationsnavigator.png)

Selecionamos **Table[edit]** porque isso inclui os dados que queremos, mas será necessária bastante formatação para que os dados da tabela sejam equivalentes ao que desejamos.

> [!TIP]
> Há uma maneira mais rápida ou mais fácil de realizar as etapas abaixo? Sim, podemos criar uma *relação* entre as duas tabelas e formatar os dados com base nessa relação. As etapas a seguir ainda são válidas para aprender a trabalhar com tabelas, mas saiba que as relações podem ajudá-lo rapidamente a usar os dados de várias tabelas.
> 
> 

Para formatar esses dados, realizamos as seguintes etapas:

* Remova as duas primeiras linhas – elas são resultado do modo como tabela da página da Web foi criada e não precisamos delas. Na faixa de opções **Página Inicial**, selecione **Reduzir Linhas\> Remover Linhas \> Remover Primeiras Linhas**.

![](media/desktop-shape-and-combine-data/shapecombine_removetoprows.png)

A janela **Remover Primeiras Linhas** é exibida, permitindo que você especifique o número de linhas que deseja remover.

* Remova as últimas 26 linhas – são todas referentes a territórios, que não precisamos incluir. Na faixa de opções **Página Inicial**, selecione **Reduzir Linhas \> Remover Linhas \> Remover Últimas Linhas**.

![](media/desktop-shape-and-combine-data/shapecombine_removebottomrows.png)

* Como a tabela RetirementStats não tem informações de Washington D.C., precisamos filtrá-la de nossa lista. Selecione a seta suspensa ao lado da coluna Status de Região e desmarque a caixa de seleção ao lado de **Distrito federal**.

![](media/desktop-shape-and-combine-data/shapecombine_filterdc.png)

* Remova algumas colunas desnecessárias – precisamos apenas do mapeamento do estado para sua abreviação oficial de duas letras, para que possamos remover as seguintes colunas: **Column2**, **Column3**e depois **Column5** até **Column10**. Primeiro, selecione Column2, mantenha pressionada a tecla **CTRL** e selecione as outras colunas a serem removidas (isso permite que você selecione várias colunas não contíguas). Na guia Página Inicial da faixa de opções, selecione **Remover Colunas \> Remover Colunas**.

![](media/desktop-shape-and-combine-data/shapecombine_removecolumns.png)

* Use a primeira linha como cabeçalhos – já que removemos as três primeiras linhas, a primeira linha atual é a que desejamos para cabeçalhos. Você pode selecionar **Usar Primeira Linha como Títulos** na guia **Página Inicial** ou na guia **Transformar** da faixa de opções.

![](media/desktop-shape-and-combine-data/shapecombine_usefirstrowasheaders.png)

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

![](media/desktop-shape-and-combine-data/shapecombine_mergequeriesb.png)

Em seguida, a janela **Mesclar** é exibida, solicitando que selecionemos qual tabela gostaríamos de mesclar à tabela selecionada e as colunas correspondentes a serem usadas para a mesclagem. Selecione State na tabela *RetirementStats* (consulta) e selecione a consulta *StateCodes* (fácil nesse caso, já que há somente mais uma consulta – quando você se conectar a várias fontes de dados, existirão muitas consultas entre as quais escolher). Quando selecionamos as colunas correspondentes corretas – **State** de *RetirementStats*, e **State Name** de *StateCodes* – a janela **Mesclar** tem a aparência semelhante à mostrada a seguir e o botão **OK** é habilitado.

![](media/desktop-shape-and-combine-data/shapecombine_merge.png)

Uma **NewColumn** é criada no final da consulta, que consiste no conteúdo da tabela (consulta) que foi mesclada com a consulta existente. Todas as colunas da consulta mesclada são condensadas na **NewColumn**, mas você pode optar por **Expandir** a tabela e incluir quaisquer colunas que desejar.

![](media/desktop-shape-and-combine-data/shapecombine_mergenewcolumn.png)

Para expandir a tabela mesclada e selecionar quais colunas deseja incluir, selecione o ícone de expansão (![Expandir](media/desktop-shape-and-combine-data/icon.png)). A janela **Expandir** é exibida.

![](media/desktop-shape-and-combine-data/shapecombine_mergeexpand.png)

Nesse caso, como só queremos a coluna **State Code** , selecionamos apenas essa coluna e, em seguida, selecionamos **OK**. Desmarcamos a caixa de seleção Usar nome da coluna original como prefixo, porque não precisamos nem desejamos essa opção; se deixarmos essa opção selecionada, a coluna mesclada será nomeada **NewColumn.State Code** (o nome da coluna original ou **NewColumn**, seguido de um ponto e do nome da coluna que está sendo introduzida na consulta).

>[!NOTE]
>Quer experimentar como inserir a tabela **NewColumn**? Você pode experimentar um pouco e, se não gostar dos resultados, basta excluir essa etapa da lista **Etapas Aplicadas** no painel **Configurações de Consulta** ; sua consulta retornará ao estado anterior à aplicação dessa etapa **Expandir** . Você pode refazer essas ações livremente, quantas vezes desejar, até que o processo de expansão tenha a aparência desejada.

Agora temos uma única consulta (tabela) que combinou duas fontes de dados, cada uma das quais foi desenvolvida para atender às nossas necessidades. Essa consulta pode servir como base para muitas conexões de dados adicionais interessantes – como estatísticas de custo de moradia, dados demográficos ou oportunidades de trabalho em qualquer estado.

Para aplicar as alterações e fechar o Editor de Consultas, selecione Fechar e Aplicar na guia de faixa de opções **Página Inicial** O conjunto de dados transformado aparece no Power BI Desktop, pronto para ser usado para a criação de relatórios.

![](media/desktop-shape-and-combine-data/shapecombine_closeandapply.png)

## <a name="next-steps"></a>Próximas etapas
Há inúmeras coisas que você pode fazer com o Power BI Desktop. Para obter mais informações sobre seus recursos, consulte as seguintes fontes:

* [Introdução ao Power BI Desktop](desktop-getting-started.md)
* [Visão geral de Consulta com o Power BI Desktop](desktop-query-overview.md)
* [Fontes de dados no Power BI Desktop](desktop-data-sources.md)
* [Conectar-se a dados no Power BI Desktop](desktop-connect-to-data.md)
* [Tarefas comuns de consulta no Power BI Desktop](desktop-common-query-tasks.md)   

