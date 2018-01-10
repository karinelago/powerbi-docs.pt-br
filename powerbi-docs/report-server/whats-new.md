---
title: "Novidades no Servidor de Relatório do Power BI"
description: "Saiba quais são as novidades no Servidor de Relatório do Power BI. Elas abrangem as principais áreas de recurso e são atualizadas conforme novos itens são lançados."
services: powerbi
documentationcenter: 
author: guyinacube
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
ms.date: 10/31/2017
ms.author: maghan
ms.openlocfilehash: 433581f77cfeaa002cffeecd927ba8751fc46617
ms.sourcegitcommit: eec6b47970bf69ed30638d1a20051f961ba792f2
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/06/2018
---
# <a name="whats-new-in-power-bi-report-server"></a>Novidades no Servidor de Relatório do Power BI
Saiba quais são as novidades no Servidor de Relatório do Power BI. Elas abrangem as principais áreas de recurso e são atualizadas conforme novos itens são lançados.

Para baixar o Servidor de Relatório do Power BI e o Power BI Desktop otimizado para o Servidor de Relatório do Power BI, acesse [Relatórios locais com o Servidor de Relatório do Power BI](https://powerbi.microsoft.com/report-server/).

![dica](media/whats-new/fyi-tip.png "dica") Para ver as notas de versão atuais, consulte [Power BI Report Server – Release notes (Servidor de Relatório do Power BI – Notas de versão)](release-notes.md).

Para informações sobre “Novidades” relacionadas, consulte:

* [Novidades no serviço do Power BI](../service-whats-new.md)
* [Novidades no Power BI Desktop](../desktop-latest-update.md)
* [Novidades em aplicativos móveis para o Power BI](../mobile-whats-new-in-the-mobile-apps.md)
* [Blog da equipe do Power BI](https://powerbi.microsoft.com/blog/)

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
[Notas de versão do Servidor de Relatório do Power BI](release-notes.md)  
[Manual do usuário](user-handbook-overview.md)  
[Manual do administrador](admin-handbook-overview.md)  
[Início rápido: instalar o Servidor de Relatório do Power BI](quickstart-install-report-server.md)  
[Instalar o Construtor de Relatórios](https://docs.microsoft.com/sql/reporting-services/install-windows/install-report-builder)  
[Baixar o SSDT (SQL Server Data Tools)](http://go.microsoft.com/fwlink/?LinkID=616714)

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)

