---
title: Obter dados de arquivos de pasta de trabalho do Excel
description: Saiba como obter dados de arquivos de pasta de trabalho do Excel no Power BI
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 05/02/2018
ms.author: davidi
LocalizationGroup: Data from files
ms.openlocfilehash: 2005069d6497fcbaeeda0fe9275f2c88b0e1999d
ms.sourcegitcommit: 998b79c0dd46d0e5439888b83999945ed1809c94
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/17/2018
---
# <a name="get-data-from-excel-workbook-files"></a>Obter dados de arquivos de pasta de trabalho do Excel
![](media/service-excel-workbook-files/excel_icon.png)

O Microsoft Excel é um dos aplicativos de negócios mais amplamente usados no mundo. Ele também fornece uma das maneiras mais comuns de inserir dados no Power BI.

## <a name="what-types-of-workbooks-does-power-bi-support"></a>Para quais tipos de pastas de trabalho há suporte no Power BI?
O Power BI dá suporte à importação ou conexão a pastas de trabalho criadas no Excel 2007 e posterior. As pastas de trabalho devem ser salvas como os tipos de arquivo .xlsx ou .xlsm e ter menos de 1 GB. Alguns recursos descritos neste artigo estão disponíveis apenas em versões posteriores do Excel.

### <a name="workbooks-with-ranges-or-tables-of-data"></a>Pastas de trabalho com intervalos ou tabelas de dados
Caso sua pasta de trabalho tenha planilhas simples com intervalos de dados, certifique-se de formatar esses intervalos como tabelas para aproveitar ao máximo seus dados no Power BI. Assim, ao criar relatórios no Power BI, você verá tabelas e colunas nomeadas no painel Campos, facilitando a visualização dos dados.

### <a name="workbooks-with-data-models"></a>Pastas de trabalho com modelos de dados
As pastas de trabalho podem conter um modelo de dados com uma ou mais tabelas de dados carregadas usando tabelas vinculadas, o Power Query (Obter e Transformar no Excel 2016) ou o Power Pivot. O Power BI dá suporte a todas as propriedades de modelo de dados como relações, medidas, hierarquias e KPIs.

> [!NOTE]
> Pastas de trabalho com modelos de dados não podem ser compartilhadas entre locatários do Power BI. Por exemplo, um usuário que fizer logon no Power BI usando uma conta *contoso.com* não pode compartilhar uma pasta de trabalho do Excel com um usuário que fizer logon usando uma conta de logon do Power BI de *woodgrovebank.com*.
> 
> 

### <a name="workbooks-with-connections-to-external-data-sources"></a>Pastas de trabalho com conexões a fontes de dados externas
Se você usar o Excel para se conectar a uma fonte de dados externa, depois de inserir sua pasta de trabalho no Power BI, será possível criar relatórios e dashboards baseados nos dados por meio dessa fonte de dados conectada. Também é possível configurar a Atualização Agendada para se conectar de forma automática diretamente à fonte de dados e obter atualizações. Não será mais necessário fazer a atualização manual por meio da faixa de opções Dados no Excel. Todas as visualizações nos relatórios e blocos em dashboards baseados nos dados dessa fonte de dados serão atualizados automaticamente. Para saber mais, veja [Atualização de dados no Power BI](refresh-data.md).

### <a name="workbooks-with-power-view-sheets-pivottables-and-charts"></a>Pastas de trabalho com planilhas do Power View, Tabelas Dinâmicas e gráficos
A forma como as planilhas do Power View, as Tabelas Dinâmicas e os gráficos são exibidos ou não no Power BI dependerá do local em que o arquivo de pasta de trabalho é salvo e de como você optar por inseri-los no Power BI. Vamos examinar esse aspecto mais detalhadamente abaixo.

## <a name="data-types"></a>Tipo de dados
O Power BI dá suporte aos seguintes tipos de dados: Número Inteiro, Número Decimal, Moeda, Data, Verdadeiro/Falso e Texto. Marcar os dados no Excel como tipos de dados específicos melhora a experiência do Power BI.

## <a name="prepare-your-workbook-for-power-bi"></a>Preparar sua pasta de trabalho para o Power BI
Assista a este vídeo bastante útil para saber mais sobre como garantir que suas pastas de trabalho do Excel estão prontas para o Power BI.

<iframe width="500" height="281" src="https://www.youtube.com/embed/l2wy4XgQIu0" frameborder="0" allowfullscreen></iframe>

## <a name="where-your-workbook-file-is-saved-makes-a-difference"></a>O local em que o arquivo de pasta de trabalho é salvo faz a diferença
**Local** – Caso o arquivo de pasta de trabalho seja salvo em uma unidade local no computador ou em outro local em sua organização, por meio do Power BI, é possível carregar o arquivo no Power BI. Na verdade, o arquivo permanecerá na unidade local; portanto, o arquivo completo não é, de fato, importado para o Power BI. O que realmente ocorre é que um novo conjunto de dados é criado no Power BI e os dados e o modelo de dados (caso haja) da pasta de trabalho são carregados nesse conjunto de dados. Se a pasta de trabalho tiver planilhas do Power View, elas serão exibidas no site do Power BI em Relatórios. O Excel 2016 também traz o recurso **Publicar** (no menu **Arquivo**). O uso do recurso **Publicar** é praticamente o mesmo que usar o recurso **Obter Dados > Arquivos > Arquivo Local** no Power BI, mas, em geral, será mais fácil atualizar o conjunto de dados no Power BI se estiver fazendo alterações à pasta de trabalho com frequência.

**OneDrive - Business** – Caso você tenha o OneDrive for Business e entre com a mesma conta usada para o logon no Power BI, essa será, sem dúvida, a maneira mais efetiva de manter seu trabalho no Excel em sincronia com seu conjunto de dados, seus relatórios e dashboards no Power BI. Visto que tanto o Power BI quanto o OneDrive ficam na nuvem, o Power BI se *conecta* ao arquivo de pasta de trabalho no OneDrive em intervalos aproximados de sessenta minutos. Caso sejam encontradas alterações, o conjunto de dados, os relatórios e os dashboards serão atualizados automaticamente no Power BI. Da mesma forma que você salvou a pasta de trabalho em uma unidade local, também é possível usar o recurso Publicar para atualizar o conjunto de dados e os relatórios no Power BI imediatamente. Caso contrário, o Power BI será sincronizado de forma automática, geralmente, em menos de uma hora.

**OneDrive - Personal** – Caso os arquivos de pasta de trabalho sejam salvos em sua própria conta do OneDrive, você aproveitará vários dos mesmos benefícios que teria com o OneDrive for Business. A maior diferença é que, na primeira conexão ao arquivo (usando Obter Dados > Arquivos > OneDrive – Personal), será necessário entrar no OneDrive com sua conta da Microsoft, que, normalmente, é diferente daquela usada para fazer logon no Power BI. Ao entrar no OneDrive com sua conta da Microsoft, certifique-se de selecionar a opção Mantenha-me conectado. Dessa forma, o Power BI poderá se conectar ao arquivo de pasta de trabalho em intervalos aproximados de sessenta minutos e garantir que o conjunto de dados e os relatórios no Power BI estão em sincronia.

**SharePoint – Sites de Equipe** – Salvar seus arquivos do Power BI Desktop no SharePoint – Sites de Equipe é muito semelhante a salvá-los no OneDrive for Business. A maior diferença nesse caso é como você se conecta ao arquivo do Power BI. É possível especificar uma URL ou conectar-se à pasta raiz.

## <a name="one-excel-workbook--two-ways-to-use-it"></a>Uma pasta de trabalho do Excel – duas maneiras de usá-la
Caso você salve os arquivos de pasta de trabalho no **OneDrive**, haverá duas maneiras de explorar os dados no Power BI

![](media/service-excel-workbook-files/excel_import_connect.png)

### <a name="import-excel-data-into-power-bi"></a>Importar dados do Excel para o Power BI
Ao escolher **Importar**, todos os dados com suporte em tabelas e/ou em um modelo de dados são importados para um novo conjunto de dados no Power BI. Caso você tenha planilhas do Power View, elas serão recriadas no Power BI como relatórios.

É possível continuar editando a pasta de trabalho. Quando as alterações forem salvas, elas serão sincronizadas com o conjunto de dados no Power BI, geralmente, em menos de uma hora. Caso você precise de mais resultados imediatos, basta clicar em Publicar novamente, e as alterações serão exportadas imediatamente. Todas as visualizações contidas em relatórios e dashboards serão atualizadas também.

Escolha esta opção caso tenha usado o recurso Obter e Transformar dados ou o Power Pivot para carregar dados em um modelo de dados, ou se a pasta de trabalho tiver planilhas do Power View com visualizações que você deseja ver no Power BI.

No Excel 2016, também é possível usar Publicar > Exportar. É quase a mesma coisa. Para saber mais, veja [Publish to Power BI from Excel 2016](service-publish-from-excel.md) (Publicar no Power BI por meio do Excel 2016).

### <a name="connect-manage-and-view-excel-in-power-bi"></a>Conectar, gerenciar e exibir o Excel no Power BI
Ao escolher **Conectar**, sua pasta de trabalho será exibida no Power BI, exatamente como apareceria no Excel Online. Mas, ao contrário do Excel Online, você terá alguns ótimos recursos para ajudá-lo a fixar elementos de suas planilhas diretamente nos dashboards.

Não é possível editar a pasta de trabalho no Power BI. No entanto, se precisar fazer alterações, clique em Editar e escolha a opção para editar a pasta de trabalho no Excel Online ou abri-la no Excel em seu computador. Todas as alterações feitas são salvas na pasta de trabalho no OneDrive.

Ao escolher essa opção, nenhum conjunto de dados será criado no Power BI. A pasta de trabalho será exibida no painel de navegação do espaço de trabalho do Power BI em Relatórios. Pastas de trabalho conectadas têm um ícone especial do Excel.

Escolha esta opção se tiver apenas dados em planilhas ou se desejar fixar intervalos, Tabelas Dinâmicas e gráficos nos dashboards.

No Excel 2016, também é possível usar Publicar > Carregar. É quase a mesma coisa. Para saber mais, veja [Publish to Power BI from Excel 2016](service-publish-from-excel.md) (Publicar no Power BI por meio do Excel 2016).

## <a name="import-or-connect-to-an-excel-workbook-from-power-bi"></a>Importar ou conectar-se a uma pasta de trabalho do Excel por meio do Power BI
1. No Power BI, no painel de navegação, clique em **Obter Dados**.
   
   ![](media/service-excel-workbook-files/excel_get_data_button.png)
2. Em Arquivos, clique em **Obter**.
   
   ![](media/service-excel-workbook-files/excel_files_get.png)
3. Encontre o arquivo.
   
   ![](media/service-excel-workbook-files/excel_find_your_file.png)
4. Se o arquivo de pasta de trabalho estiver no OneDrive ou SharePoint – Sites de Equipe, escolha **Importar** ou **Conectar**.

## <a name="local-excel-workbooks"></a>Pastas de trabalho locais do Excel
Você também pode usar um arquivo local do Excel e carregá-lo no Power BI. Basta selecionar **Arquivo Local** no menu anterior e navegar até o local em que você salvou as pastas de trabalho do Excel.

![](media/service-excel-workbook-files/excel_import_6.png)

Depois de selecioná-las, escolha Carregar seu arquivo no Power BI.

![](media/service-excel-workbook-files/excel_import_7.png)

Após o upload da pasta de trabalho, você obtém uma notificação indicando que a pasta de trabalho está pronta.

![](media/service-excel-workbook-files/excel_import_8.png)

Quando a pasta de trabalho estiver pronta, você poderá encontrá-la na seção **Relatórios** do Power BI.

![](media/service-excel-workbook-files/excel_import_9.png)

## <a name="publish-from-excel-2016-to-your-power-bi-site"></a>Publicar em seu site do Power BI por meio do Excel 2016
O uso do recurso **Publicar no Power BI no Excel 2016** é praticamente o mesmo que usar o recurso **Obter Dados** no Power BI para importar ou conectar-se ao arquivo. Não entraremos em detalhes aqui, mas é possível ver [Publicar no Power BI por meio do Excel 2016](service-publish-from-excel.md) para saber mais.

## <a name="troubleshooting"></a>Solução de problemas
O arquivo de pasta de trabalho é muito grande? Confira [Reduzir o tamanho de uma pasta de trabalho do Excel para exibi-la no Power BI](reduce-the-size-of-an-excel-workbook.md).

Atualmente, ao escolher a opção Importar, o Power BI importa somente os dados que fazem parte de uma tabela ou de um modelo de dados nomeado. Como resultado, se a pasta de trabalho não contiver nenhuma tabela nomeada, planilhas do Power View ou modelos de dados do Excel, você poderá ver esse erro: **“Não foi possível encontrar nenhum dado em sua pasta de trabalho do Excel”**. [Este artigo](service-admin-troubleshoot-excel-workbook-data.md) explica como corrigir a pasta de trabalho e importá-la novamente.

## <a name="next-steps"></a>Próximas etapas
**Explore os dados** – Depois de obter dados e relatórios de seu arquivo no Power BI, é hora de explorá-los. Basta clicar com o botão direito do mouse no novo conjunto de dados e clicar em Explorar. Caso você tenha decidido se conectar a um arquivo de pasta de trabalho no OneDrive na etapa 4, a pasta de trabalho será exibida em Relatórios. Ao clicar nela, ela será aberta no Power BI, da mesma forma como seria aberta se estivesse no Excel Online.

**Agendar atualização** – Se o arquivo de pasta de trabalho do Excel se conectar a fontes de dados externas ou se ele foi importado de uma unidade local, será possível configurar a atualização agendada para garantir que o conjunto de dados ou relatório está sempre atualizado. Na maioria dos casos, é muito fácil configurar a atualização agendada; no entanto, não entraremos em detalhes sobre essa configuração neste artigo, pois isso está fora do escopo. Veja [Atualização de dados no Power BI](refresh-data.md) para saber mais.

[Publicar no Power BI por meio do Excel 2016](service-publish-from-excel.md)

[Editor do Power BI para Excel](publisher-for-excel.md)

[Atualizar dados no Power BI](refresh-data.md)

