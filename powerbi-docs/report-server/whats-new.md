---
title: Novidades no Servidor de Relatório do Power BI
description: Saiba quais são as novidades no Servidor de Relatório do Power BI. Elas abrangem as principais áreas de recurso e são atualizadas conforme novos itens são lançados.
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-report-server
ms.topic: conceptual
ms.date: 04/19/2018
ms.author: maggies
ms.openlocfilehash: 391edc8a2187f9a4af43b93f0713d40e41f6e943
ms.sourcegitcommit: 638de55f996d177063561b36d95c8c71ea7af3ed
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/17/2018
ms.locfileid: "34295412"
---
# <a name="whats-new-in-power-bi-report-server"></a>Novidades no Servidor de Relatório do Power BI
Saiba quais são as novidades no Servidor de Relatório do Power BI. Elas abrangem as principais áreas de recurso e são atualizadas conforme novos itens são lançados.

Para baixar o Servidor de Relatório do Power BI e o Power BI Desktop otimizado para o Servidor de Relatório do Power BI, acesse [Relatórios locais com o Servidor de Relatório do Power BI](https://powerbi.microsoft.com/report-server/).

Consulte também essas fontes para ficar atualizado sobre os novos recursos no Servidor de Relatórios do Power BI.

* [Blog do Microsoft Power BI](https://powerbi.microsoft.com/blog/)
* [Blog da equipe do SQL Server Reporting Services](https://blogs.msdn.microsoft.com/sqlrsteamblog/)
* O [canal do YouTube Guy in a Cube](https://aka.ms/guyinacube)

Para saber mais sobre as “Novidades” do Power BI, consulte:

* [Novidades no serviço do Power BI](../service-whats-new.md)
* [Novidades no Power BI Desktop](../desktop-latest-update.md)
* [Novidades em aplicativos móveis para o Power BI](../mobile-whats-new-in-the-mobile-apps.md)

## <a name="march-2018-release"></a>Versão de março de 2018

Em março de 2018, houve a adição de muitos recursos novos à versão do Power BI Desktop otimizado para o Servidor de Relatórios do Power BI. Aqui estão elas, divididas por área: 
- [Visuais](#visuals-updates)
- [Relatórios](#reporting)
- [Análise](#analytics)
- [Desempenho](#performance)
- [Servidor de relatórios](#report-server)
- [Outros](#other-improvements)

### <a name="highlights-of-this-release"></a>Destaques desta versão

De toda a longa lista de novos recursos, esses se destacam como especialmente interessantes.

#### <a name="rule-based-conditional-formatting-for-table-and-matrixhttpspowerbimicrosoftcomblogpower-bi-desktop-november-2017-feature-summaryconditionalformatting"></a>[Formatação condicional baseada em regras para visuais de tabela e de matriz](https://powerbi.microsoft.com/blog/power-bi-desktop-november-2017-feature-summary/#conditionalFormatting)
 
Crie regras para colorir condicionalmente a tela de fundo ou a fonte de uma coluna com base na lógica de negócios específica na tabela ou na matriz.

#### <a name="show-and-hide-pageshttpspowerbimicrosoftcomblogpower-bi-desktop-january-2018-feature-summaryhidepages"></a>[Mostrar e ocultar páginas](https://powerbi.microsoft.com/blog/power-bi-desktop-january-2018-feature-summary/#hidePages)

Você deseja que os leitores acessem seu relatório, mas algumas páginas não estão concluídas. Agora você pode ocultá-las até que elas fiquem prontas. Ou você pode ocultar páginas da navegação normal, permitindo que os leitores cheguem à página por indicadores ou por detalhamento.

#### <a name="bookmarkinghttpspowerbimicrosoftcomblogpower-bi-desktop-march-2018-feature-summarybookmarking"></a>[Uso de indicadores](https://powerbi.microsoft.com/blog/power-bi-desktop-march-2018-feature-summary/#bookmarking)

Falando de uso de indicadores, crie-os para contar uma história com os dados em seu relatório.

- [Realce cruzado para indicadores](https://powerbi.microsoft.com/blog/power-bi-desktop-december-feature-summary/#bookmarkCrossHighlighting): indicadores mantêm e exibem o estado com realce cruzado da página do relatório no momento em que são criados.
- [Mais flexibilidade para indicadores](https://powerbi.microsoft.com/blog/power-bi-desktop-december-feature-summary/#bookmarkFlexibility): indicadores refletem as propriedades que você define no relatório e afeta somente os visuais que você escolhe.

#### <a name="multi-select-data-points-across-multiple-chartshttpspowerbimicrosoftcomblogpower-bi-desktop-february-2018-feature-summarycrosshighlight"></a>[Pontos de dados de seleção múltipla em vários gráficos](https://powerbi.microsoft.com/blog/power-bi-desktop-february-2018-feature-summary/#crosshighlight)

Selecione vários pontos de dados em vários gráficos e aplique a filtragem cruzada a toda a página.

#### <a name="sync-slicers-across-multiple-pages-of-your-reporthttpspowerbimicrosoftcomblogpower-bi-desktop-february-2018-feature-summarysyncslicers"></a>[Sincronizar segmentações de dados em várias páginas do relatório](https://powerbi.microsoft.com/blog/power-bi-desktop-february-2018-feature-summary/#syncSlicers)

Uma segmentação de dados pode se aplicar a uma, duas ou mais páginas em um relatório.

#### <a name="quick-measureshttpspowerbimicrosoftcomblogpower-bi-desktop-february-2018-feature-summaryquickmeasures"></a>[Medidas rápidas](https://powerbi.microsoft.com/blog/power-bi-desktop-february-2018-feature-summary/#quickMeasures) 

Crie medidas com base em medidas existentes e nas colunas numéricas em uma tabela.

#### <a name="drilling-down-filters-other-visualshttpspowerbimicrosoftcomblogpower-bi-desktop-december-feature-summarydrillfiltersothervisuals"></a>[Filtros de detalhamento de outros elementos visuais](https://powerbi.microsoft.com/blog/power-bi-desktop-december-feature-summary/#drillFiltersOtherVisuals)

Quando você faz drill down em uma determinada categoria em um visual, você pode filtrar todos os elementos visuais na página por essa mesma categoria.

### <a name="visuals-updates"></a>Atualizações de visuais

- [Alinhamento de células para visuais de tabela e de matriz](https://powerbi.microsoft.com/blog/power-bi-desktop-november-2017-feature-summary/#alignment)
- [Ver unidades e controle de precisão para colunas de tabela e de matriz](https://powerbi.microsoft.com/blog/power-bi-desktop-march-2018-feature-summary/#displayUnits)
- [Rótulos de dados de estouro para elementos visuais de gráfico de barras e colunas](https://powerbi.microsoft.com/blog/power-bi-desktop-february-2018-feature-summary/#overflow)
- [Controlar a cor da tela de fundo do rótulo de dados para Cartesiano e visuais de mapas](https://powerbi.microsoft.com/blog/power-bi-desktop-january-2018-feature-summary/#dataLabelBackground)
- [Controle de preenchimento de barra/coluna](https://powerbi.microsoft.com/blog/power-bi-desktop-january-2018-feature-summary/#padding)
- [Aumentar a área usada para rótulos de eixo em gráficos](https://powerbi.microsoft.com/blog/power-bi-desktop-january-2018-feature-summary/#axisSize)
- [Dispersão visual de agrupamentos do eixo x e y](https://powerbi.microsoft.com/blog/power-bi-desktop-december-feature-summary/#scatterChart)
- [Amostragem de alta densidade para mapas com base em latitude e longitude](https://powerbi.microsoft.com/blog/power-bi-desktop-december-feature-summary/#highDensityMaps)
- [Segmentações responsivas](https://powerbi.microsoft.com/blog/power-bi-desktop-december-feature-summary/#responsive)
- [Adicionar uma data de âncora para segmentação de data relativa](https://powerbi.microsoft.com/blog/power-bi-desktop-january-2018-feature-summary/#anchorDate)

### <a name="reporting"></a>Relatórios

- [Desativar o cabeçalho do visual no modo de leitura em um relatório](https://powerbi.microsoft.com/blog/power-bi-desktop-march-2018-feature-summary/#visualHeader)
- [Opções de relatório para fontes de dados lentas](https://powerbi.microsoft.com/blog/power-bi-desktop-november-2017-feature-summary/#slowDataSource)
- [Posicionamento de visual padrão aprimorado](https://powerbi.microsoft.com/blog/power-bi-desktop-march-2018-feature-summary/#visualPlacement)
- [Controle a ordem visual por meio do painel de seleção](https://powerbi.microsoft.com/blog/power-bi-desktop-november-2017-feature-summary/#selectionPane)
- [Bloqueie objetos no relatório](https://powerbi.microsoft.com/blog/power-bi-desktop-november-2017-feature-summary/#lock)
- [Pesquisar o painel de formatação e análise](https://powerbi.microsoft.com/blog/power-bi-desktop-february-2018-feature-summary/#search)
- [Painel de propriedades de campo e descrições de campo](https://powerbi.microsoft.com/blog/power-bi-desktop-december-feature-summary/#fieldPropertiesPane)

### <a name="analytics"></a>Análise

- [UTCNOW() e UTCTODAY()](https://powerbi.microsoft.com/blog/power-bi-desktop-february-2018-feature-summary/#utcDAX)
- [Marcar tabela de datas personalizada](https://powerbi.microsoft.com/blog/power-bi-desktop-february-2018-feature-summary/#customDateTable)
- [Detalhar filtros de outros visuais](https://powerbi.microsoft.com/blog/power-bi-desktop-december-feature-summary/#drillFiltersOtherVisuals)
- [Formatação de nível de célula para modelos multidimensionais do AS para cartão de múltiplas linhas](https://powerbi.microsoft.com/blog/power-bi-desktop-november-2017-feature-summary/#cellLevelFormatting)
 
### <a name="performance"></a>Desempenho

- [Melhorias de desempenho de filtragem](https://powerbi.microsoft.com/blog/power-bi-desktop-november-2017-feature-summary/#filtering)
- [Melhorias de desempenho DirectQuery](https://powerbi.microsoft.com/blog/power-bi-desktop-february-2018-feature-summary/#dqPerf)
- [Melhorias de desempenho de abrir e salvar](https://powerbi.microsoft.com/blog/power-bi-desktop-february-2018-feature-summary/#savePerf)
- [Melhorias de “Mostrar itens sem dados”](https://powerbi.microsoft.com/blog/power-bi-desktop-february-2018-feature-summary/#showItemsWithNoData)
 
### <a name="report-server"></a>Servidor de relatórios 

#### <a name="export-to-accessible-pdf"></a>Exportar para PDF acessível

Quando você exporta um relatório paginado (RDL) para PDF, você pode obter um arquivo PDF acessível/marcado. Ele é maior em tamanho, mas sua leitura e navegação pelos leitores de tela e outras tecnologias assistenciais é mais fácil. Você habilita o PDF acessível definindo a configuração de informações de dispositivo **AccessiblePDF** para **True**. Consulte [Configuração de Informações de Dispositivo PDF](https://docs.microsoft.com/sql/reporting-services/pdf-device-information-settings) e [Alterar as Configurações de Informações do Dispositivo](https://docs.microsoft.com/sql/reporting-services/customize-rendering-extension-parameters-in-rsreportserver-config#changing-device-information-settings).


### <a name="other-improvements"></a>Outros aprimoramentos

- [Aprimoramentos em Adicionar Coluna de Exemplos](https://powerbi.microsoft.com/blog/power-bi-desktop-november-2017-feature-summary/#addColumnFromExamples)
- [Link rápido para Serviços de Consultoria](https://powerbi.microsoft.com/blog/power-bi-desktop-february-2018-feature-summary/#consultingServices)
- [Relatório de erros aprimorado](https://powerbi.microsoft.com/blog/power-bi-desktop-march-2018-feature-summary/#errors)
- [Ver erros anteriores que você encontrou](https://powerbi.microsoft.com/blog/power-bi-desktop-march-2018-feature-summary/#viewErrors)

 
## <a name="october-2017-release"></a>Versão de outubro de 2017
### <a name="power-bi-report-data-sources"></a>Fontes de dados de relatório do Power BI
Os relatórios do Power BI no Servidor de Relatórios do Power BI podem conectar-se a uma variedade de fontes de dados. É possível importar e agendar a atualização de dados ou consultá-los diretamente usando o DirectQuery ou uma conexão dinâmica ao SQL Server Analysis Services. Veja a lista das fontes de dados compatíveis com a atualização agendada e as compatíveis com o DirectQuery em "Fontes de dados de relatórios do Power BI no Servidor de Relatórios do Power BI".

### <a name="scheduled-data-refresh-for-imported-data"></a>Atualização agendada de dados importados
No Servidor de Relatórios do Power BI, é possível configurar a atualização de dados agendada para manter os dados atualizados nos relatórios do Power BI usando um modelo inserido, em vez de uma conexão dinâmica ou o DirectQuery. Com um modelo inserido, os dados importados estão desconectados da fonte de dados original. Eles precisam ser atualizados para permanecerem em sua versão mais recente e a atualização agendada é a maneira de fazer isso. Leia mais sobre a "atualização agendada dos relatórios do Power BI no Servidor de Relatórios do Power BI".

### <a name="editing-power-bi-reports-from-the-server"></a>Editando relatórios do Power BI no servidor
É possível abrir e editar os arquivos de relatório do Power BI (.pbix) no servidor, mas você retorna o arquivo original carregado.  Isso significa que **se os dados tiverem sido atualizados pelo servidor, eles não estarão atualizados quando você abrir o arquivo pela primeira vez**. Para ver a alteração, você precisará atualizá-los manual e localmente.

### <a name="large-file-uploaddownload"></a>Upload/download de arquivo grande
Você pode carregar arquivos de até 2 GB, embora, por padrão, esse limite é definido como 1 GB nas configurações do Servidor de Relatórios no SSMS (SQL Server Management Studio).  Esses arquivos são armazenados no banco de dados como no SharePoint e nenhuma configuração especial para o catálogo do SQL Server é necessária.  

### <a name="accessing-shared-datasets-as-odata-feeds"></a>Acessando conjuntos de dados compartilhados como feeds OData
Você pode acessar os conjuntos de dados compartilhados do Power BI Desktop com um feed OData. Para obter mais informações, consulte [Acessando conjuntos de dados compartilhados como feeds OData no Servidor de Relatórios do Power BI](access-dataset-odata.md).

### <a name="scale-out"></a>Escalabilidade horizontal
Esta versão é compatível com escalabilidade horizontal. Use um balanceador de carga e defina a afinidade do servidor para uma melhor experiência. Observe que o cenário ainda não está otimizado para a escalabilidade horizontal, portanto você verá os modelos possivelmente replicados em vários nós. O cenário funcionará sem o balanceador de carga de rede e as sessões temporárias. No entanto, você não só verá um uso excessivo de memória nos nós conforme o modelo for carregado N vezes, mas o desempenho também ficará mais lento entre as conexões conforme o modelo for transmitido a um novo nó entre as solicitações.  

### <a name="administrator-settings"></a>Configurações do administrador
Os administradores podem definir as seguintes propriedades nas Propriedades Avançadas do SSMS para o farm de servidores:

* EnableCustomVisuals: True/False
* EnablePowerBIReportEmbeddedModels: True/False
* EnablePowerBIReportExportData: True/False
* MaxFileSizeMb: o padrão agora é 1.000
* ModelCleanupCycleMinutes: a frequência da verificação para remover modelos da memória
* ModelExpirationMinutes: quanto tempo levará até o modelo expirar e ser removido, com base no último uso
* ScheduleRefreshTimeoutMinutes: quanto tempo a atualização de dados de um modelo poderá demorar. Por padrão, duas horas.  Não há nenhum limite máximo.

**Arquivo de configuração rsreportserver.config**

```
<Configuration>
  <Service>
    <PollingInterval>10</PollingInterval>
    <IsDataModelRefreshService>false</IsDataModelRefreshService>
    <MaxQueueThreads>0</MaxQueueThreads>
  </Service>
</Configuration>
```

### <a name="developer-api"></a>API para desenvolvedores
A API para desenvolvedores (API REST) apresentada para o SSRS 2017 foi estendida para o Servidor de Relatórios do Power BI trabalhar com arquivos do Excel e .pbix. Um possível caso de uso é, por meio de programação, baixar arquivos do servidor, atualizá-los e publicá-los novamente. Essa é a única maneira de atualizar as pastas de trabalho do Excel com modelos do PowerPivot, por exemplo.

Observe que há uma nova API separada para arquivos grandes, que será atualizada na versão de Servidor de Relatórios do Power BI do Swagger. 

### <a name="sql-server-analysis-services-ssas-and-the-power-bi-report-server-memory-footprint"></a>O SSAS (SQL Server Analysis Services) e o volume de memória do Servidor de Relatórios do Power BI
O Servidor de Relatórios do Power BI agora hospeda o SSAS (SQL Server Analysis Services) internamente. Isso não é específico para a atualização agendada. Hospedar o SSAS pode expandir consideravelmente o volume de memória do servidor de relatório. O arquivo de configuração AS.ini está disponível nos nós do servidor, portanto, se estiver familiarizado com o SSAS, será possível atualizar as configurações, incluindo o limite máximo de memória, o cache de disco, etc. Consulte [Propriedades de servidor do Analysis Services](https://docs.microsoft.com/sql/analysis-services/server-properties/server-properties-in-analysis-services) para obter detalhes.

### <a name="viewing-and-interacting-with-excel-workbooks"></a>Exibição e interação com as pastas de trabalho do Excel
O Excel e o Power BI contêm um portfólio de ferramentas que é exclusivo no setor. Juntas, elas permitem que os analistas de negócios reúnam, moldem, analisem e explorem visualmente seus dados com mais facilidade. Além de exibirem os relatórios do Power BI no portal da Web, os usuários empresariais agora podem fazer o mesmo com as pastas de trabalho do Excel no Servidor de Relatórios do Power BI, o que proporciona a eles uma única localização para publicar e exibir seu conteúdo de autoatendimento do Microsoft BI.

Publicamos um [passo a passo de como adicionar um OOS (Servidor do Office Online) em seu ambiente de versão prévia do Servidor de Relatórios do Power BI](excel-oos.md). Os clientes que têm uma conta de Licenciamento por Volume podem baixar o OOS do Centro de Manutenção da Licença de Volume sem nenhum custo e terão a funcionalidade somente exibição. Uma vez configuradas, os usuários poderão exibir e interagir com as pastas de trabalho do Excel que:

* Não tiverem nenhuma dependência de fonte de dados externa
* Tiverem uma conexão dinâmica com uma fonte de dados externa do SQL Server Analysis Services
* Tiver um modelo de dados PowerPivot

### <a name="support-for-new-table-and-matrix-visuals"></a>Suporte para os novos elementos visuais de matriz e de tabela
O Servidor de Relatórios do Power BI agora é compatível com os novos elementos visuais de matriz e de tabela do Power BI. Para criar relatórios com esses elementos visuais, você precisará de uma versão atualizada do Power BI Desktop para a versão de outubro de 2017. Ela não pode ser instalada paralelamente à versão do Power BI Desktop (junho de 2017). Para obter a versão mais recente do Power BI Desktop, na [página de download do Servidor de Relatórios do Power BI](https://powerbi.microsoft.com/report-server/), selecione **Opções de download avançadas**.

## <a name="june-2017"></a>Junho de 2017
* Servidor de Relatório do Power BI disponibilizado para o público geral (GA).

## <a name="may-2017"></a>Maio de 2017
* Visualização do Servidor de Relatório do Power BI disponibilizada
* Capacidade de publicar relatórios do Power BI local
  * Suporte para visuais personalizados
  * Suporte para conexões em tempo real do Analysis Services somente com mais fontes de dados em breve.
  * Aplicativo Power BI para Celulares atualizado para exibir relatórios do Power BI hospedados no Servidor de Relatório do Power BI
* Colaboração aprimorada em relatórios com comentários

## <a name="next-steps"></a>Próximas etapas
[Manual do usuário](user-handbook-overview.md)  
[Manual do administrador](admin-handbook-overview.md)  
[Instalar o Servidor de Relatório do Power BI](install-report-server.md)  
[Instalar o Construtor de Relatórios](https://docs.microsoft.com/sql/reporting-services/install-windows/install-report-builder)  
[Baixar o SSDT (SQL Server Data Tools)](http://go.microsoft.com/fwlink/?LinkID=616714)

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)

