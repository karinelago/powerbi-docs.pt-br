---
title: "Solucionar problemas de atualização agendada no Servidor de Relatórios do Power BI"
description: "Este artigo aborda os recursos disponíveis para solucionar problemas com a atualização agendada no Servidor de Relatórios do Power BI."
services: powerbi
documentationcenter: 
author: markingmyname
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
ms.date: 11/01/2017
ms.author: maghan
ms.openlocfilehash: 466505ae2c4050629e8bbcc4ff90cde520d31375
ms.sourcegitcommit: 6e693f9caf98385a2c45890cd0fbf2403f0dbb8a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2018
---
# <a name="troubleshoot-scheduled-refresh-in-power-bi-report-server"></a>Solucionar problemas de atualização agendada no Servidor de Relatórios do Power BI
Este artigo aborda os recursos disponíveis para solucionar problemas com a atualização agendada no Servidor de Relatórios do Power BI.

Conforme os problemas surgirem, este artigo será atualizado com informações para ajudar você a resolvê-los.

## <a name="common-issues"></a>Problemas comuns
Veja a seguir os problemas mais comuns encontrados ao tentar agendar a atualização de um relatório. 

### <a name="driver-related-problems"></a>Problemas relacionados ao driver
A conexão a fontes de dados diferentes pode exigir drivers de terceiros que precisam ser instalados para uma conexão bem-sucedida. Você não só precisará instalá-los no computador usando o Power BI Desktop, mas também precisará verificar se o driver está instalado no servidor de relatório.

Além disso, o driver pode ser de 32 e de 64 bits. Instale o driver de 64 bits, uma vez que Servidor de Relatórios do Power BI é de 64 bits.

Consulte o fabricante para obter detalhes sobre como instalar e configurar os drivers de terceiros.

### <a name="memory-pressure"></a>Demanda de memória
A demanda de memória pode ocorrer quando os relatórios exigem mais memória para o processamento e para a renderização. O agendamento de atualização de relatórios pode exigir que o computador tenha uma quantidade significativa de memória. Especialmente para relatórios maiores. A demanda de memória pode provocar falhas nos relatórios, bem como possíveis panes no próprio servidor de relatório.

Caso esteja sofrendo com problemas de demanda de memória de forma consistente, pode ser válido buscar uma implantação expandida do servidor de relatório para distribuir a carga de recursos. Você também pode definir que um servidor de relatório específico seja usado para a atualização de dados com a configuração de `IsDataModelRefreshService` em rsreportserver.config. Com essa configuração, você pode definir um ou mais servidores para ser o servidor front-end para lidar com os relatórios sob demanda e outro conjunto de servidores para ser usado apenas para a atualização agendada.

Para obter informações sobre como monitorar uma instância do Analysis Services, consulte [Monitorar uma instância do Analysis Services](https://docs.microsoft.com/sql/analysis-services/instances/monitor-an-analysis-services-instance).

Para obter informações sobre as configurações de memória no Analysis Services, consulte [Propriedades de memória](https://docs.microsoft.com/sql/analysis-services/server-properties/memory-properties).

### <a name="kerberos-configuration"></a>Configuração do Kerberos
Conectar-se a uma fonte de dados com credenciais do Windows pode exigir a configuração da delegação restrita de Kerberos para que a conexão seja bem-sucedida. Para obter mais informações sobre como configurar a delegação restrita de Kerberos, consulte [Configurar o Kerberos para usar relatórios do Power BI](configure-kerberos-powerbi-reports.md).

## <a name="known-issues"></a>Problemas conhecidos
As informações sobre os problemas conhecidos serão listadas aqui quando disponíveis.

## <a name="configuration-settings"></a>Definições de configuração
As configurações a seguir podem ser usadas para impactar a atualização agendada. As configurações definidas no SSMS (SQL Server Management Studio) aplicam-se a todos os servidores de relatórios em uma implantação escalável. As configurações definidas em rsreportserver.config são para o servidor específico nas quais elas são definidas.

**Configurações no SSMS:**

| Configuração | Descrição |
| --- | --- |
| EnablePowerBIReportEmbeddedModels |Habilita ou desabilita a capacidade de usar dados importados nos relatórios. Os valores válidos são True ou False. |
| MaxFileSizeMb |Tamanho máximo dos arquivos dos relatórios carregados. O padrão é 1.000 MB (1 GB). O valor máximo é 2.000 MB (2 GB). |
| ModelCleanupCycleMinutes |Define a frequência em que o modelo é verificado para removê-lo da memória. O padrão é 15 minutos. |
| ModelExpirationMinutes |Define o tempo para a expiração do modelo com base no último uso e para sua remoção. O padrão é 60 minutos. |
| ScheduleRefreshTimeoutMinutes |Define quanto tempo a atualização de dados pode demorar para um modo. O padrão é 120 minutos. Não há limite máximo. |

**Configurações em rsreportserver.config:**

```
<Configuration>
    <Service>
        <PollingInterval>10</PollingInterval>
        <IsDataModelRefreshService>false</IsDataModelRefreshService>
        <MaxQueueThreads>0</MaxQueueThreads>
    </Service>
</Configuration>
```

## <a name="tools-for-troubleshooting"></a>Ferramentas para solução de problemas
### <a name="logs-relevant-for-scheduled-refresh-of-power-bi-reports"></a>Logs relevantes para a atualização agendada dos relatórios do Power BI
Os arquivos de log com informações sobre a atualização agendada são os logs de RSPowerBI_. Eles estão localizados na pasta LogFiles do local da instalação do servidor de relatório. 

```
C:\Program Files\Microsoft Power BI Report Server\PBIRS\LogFiles\RSPowerBI_*.log
```

**Condição de erro**

```
2017-10-20 02:00:09.5188|ERROR|744|Error Processing Data Model Refresh: SessionId: e960c25e-ddd4-4763-aa78-0e5dceb53472, Status: Error Model can not be refreshed because not all the data sources are embedded, Exception Microsoft.PowerBI.ReportServer.AsServer.InvalidDataSourceException: Model can not be refreshed because not all the data sources are embedde
   at Microsoft.PowerBI.ReportServer.WebHost.EventHandler.AnalysisServicesDataRefresh.CanModelRefresh(IEnumerable`1 dataSources)
   at Microsoft.PowerBI.ReportServer.WebHost.EventHandler.DataRefreshScope.<>c__DisplayClass7.<ExecuteActionWithLogging>b__5()
   at Microsoft.PowerBI.ReportServer.WebHost.EventHandler.DataRefreshScope.<ExecuteFuncWithLogging>d__1`1.MoveNext()
```

***Atualização bem-sucedida***

```
2017-10-25 15:23:41.9370|INFO|6|Handling event with data: TimeEntered: 10/25/2017 8:23:41 PM, Type: Event, SessionId: 46d398db-0b1f-49d8-b7bd-c5461c07ec7a, EventType: DataModelRefresh
2017-10-25 15:23:41.9370|INFO|6|Processing Data Model Refresh: SessionId: 46d398db-0b1f-49d8-b7bd-c5461c07ec7a, Status: Starting Data Refresh.
2017-10-25 15:23:41.9370|INFO|6|Processing Data Model Refresh: SessionId: 46d398db-0b1f-49d8-b7bd-c5461c07ec7a, Status: Starting Retrieving PBIX AsDatabaseInfo.
2017-10-25 15:23:42.7134|INFO|6|Processing Data Model Refresh: SessionId: 46d398db-0b1f-49d8-b7bd-c5461c07ec7a, Status: Starting Verifying all the data sources are embedded.
2017-10-25 15:23:42.7134|INFO|6|Processing Data Model Refresh: SessionId: 46d398db-0b1f-49d8-b7bd-c5461c07ec7a, Status: Starting Verifying connection strings are valid.
2017-10-25 15:23:42.7134|INFO|6|Processing Data Model Refresh: SessionId: 46d398db-0b1f-49d8-b7bd-c5461c07ec7a, Status: Starting Streaming model to Analysis Server.
2017-10-25 15:23:42.7603|INFO|6|Processing Data Model Refresh: SessionId: 46d398db-0b1f-49d8-b7bd-c5461c07ec7a, Status: Starting Refreshing the model.
2017-10-25 15:23:51.5258|INFO|6|Processing Data Model Refresh: SessionId: 46d398db-0b1f-49d8-b7bd-c5461c07ec7a, Status: Starting Removing credentials from the model.
2017-10-25 15:23:51.6508|INFO|6|Processing Data Model Refresh: SessionId: 46d398db-0b1f-49d8-b7bd-c5461c07ec7a, Status: Starting Saving model to the catalog.
```

**Credenciais incorretas**

```
2017-10-20 08:22:01.5595|INFO|302|Processing Data Model Refresh: SessionId: 22cd9ec3-b21a-4eb1-81ae-15fac8d379ea, Status: Starting Refreshing the model.
2017-10-20 08:22:02.3758|ERROR|302|Error Processing Data Model Refresh: SessionId: 22cd9ec3-b21a-4eb1-81ae-15fac8d379ea, Status: Error Failed to refresh the model, Exception Microsoft.AnalysisServices.OperationException: Failed to save modifications to the server. Error returned: 'The credentials provided for the SQL source are invalid. (Source at rosecatalog;reportserver.). The exception was raised by the IDbCommand interface.
'.
   at Microsoft.AnalysisServices.Tabular.Model.SaveChanges(SaveOptions saveOptions)
   at Microsoft.PowerBI.ReportServer.AsServer.TOMWrapper.RefreshModel(Database database)
   at Microsoft.PowerBI.ReportServer.AsServer.AnalysisServicesServer.RefreshDatabase(String databaseName, IEnumerable`1 dataSources)
   at Microsoft.PowerBI.ReportServer.WebHost.EventHandler.AnalysisServicesDataRefresh.RefreshDatabase(AsDatabaseInfo asDatabaseInfo)
   at Microsoft.PowerBI.ReportServer.WebHost.EventHandler.DataRefreshScope.<>c__DisplayClass7.<ExecuteActionWithLogging>b__5()
   at Microsoft.PowerBI.ReportServer.WebHost.EventHandler.DataRefreshScope.<ExecuteFuncWithLogging>d__1`1.MoveNext()
2017-10-20 08:22:02.4588|ERROR|302|Error Processing Data Model Refresh: SessionId: 22cd9ec3-b21a-4eb1-81ae-15fac8d379ea, Status: Error Failed Data Refresh, Exception Microsoft.AnalysisServices.OperationException: Failed to save modifications to the server. Error returned: 'The credentials provided for the SQL source are invalid. (Source at rosecatalog;reportserver.). The exception was raised by the IDbCommand interface.
'.
   at Microsoft.PowerBI.ReportServer.WebHost.EventHandler.DataRefreshScope.ExecuteActionWithLogging(Action methodToExecute, String description, String localizedDescription, String messageInFailure, RefreshInfo refreshInfo, DataAccessors dataAccessors, ReportEventType operation, Int64 size, Boolean isDataRetrieval, Boolean showInExecutionLog)
   at Microsoft.PowerBI.ReportServer.WebHost.EventHandler.AnalysisServicesDataRefresh.RefreshData(RefreshInfo refreshInfo)
   at Microsoft.PowerBI.ReportServer.WebHost.EventHandler.DataRefreshScope.<>c__DisplayClass7.<ExecuteActionWithLogging>b__5()
   at Microsoft.PowerBI.ReportServer.WebHost.EventHandler.DataRefreshScope.<ExecuteFuncWithLogging>d__1`1.MoveNext()
```

#### <a name="enabling-verbose-logging"></a>Habilitando o registro em log detalhado
O procedimento para habilitar o registro em log detalhado no Servidor de Relatórios do Power BI é o mesmo do SQL Server Reporting Services.

1. Abra `<install directory>\PBIRS\ReportServer\bin\ReportingServicesService.exe.config`.
2. Em `<system.diagnostics>`, altere **DefaultTraceSwitch** para **4**.
3. Em `<RStrace>`, altere **Componentes** para **todos: 4**. 

### <a name="executionlog"></a>ExecutionLog
Sempre que um relatório do Power BI é renderizado ou um plano de agendamento de atualização é executado, novas entradas são adicionadas ao Log de Execução no banco de dados. Essas entradas estão disponíveis na exibição **ExecutionLog3** no banco de dados de catálogo do servidor de relatório.

As entradas do log de execução dos relatórios do Power BI são diferentes das entradas de outros tipos de relatório.

* As colunas de TimeRendering são sempre 0. A renderização dos relatórios do Power BI ocorre no navegador, e não no servidor.
* Há dois tipos de solicitações e ações subsequentes de itens:
  * **Interativa**: sempre que um relatório é exibido.
    * **ASModelStream**: quando o modelo de dados é transmitido ao Analysis Services do catálogo.
    * **ConceptualSchema**: quando o usuário clica na exibição do relatório.
    * **QueryData**: sempre que os dados são solicitados no cliente.
  * **Atualizar Cache**: sempre que um plano de agendamento de atualização é executado.
    * **ASModelStream**: sempre que o modelo de dados é transmitido ao Analysis Services do catálogo.
    * **DataRefresh**: sempre que os dados são atualizados de uma ou mais fontes de dados.
    * **SaveToCatalog**: sempre que o modelo de dados é salvo para o catálogo.

## <a name="analysis-services"></a>Analysis Services
Pode haver momentos que você deseja modificar o Analysis Services para diagnosticar problemas ou para ajustar os limites de memória.

> [!IMPORTANT]
> Estas configurações serão redefinidas sempre que você atualizar o servidor de relatório. Mantenha sempre uma cópia das alterações e reaplique-as se necessário.
> 
> 

### <a name="install-location"></a>Local da instalação
O local padrão do Servidor de Relatórios do Power BI e do Analysis Services é o seguinte.

`C:\Program Files\Microsoft Power BI Report Server\PBIRS\ASEngine`

### <a name="configuring-analysis-services-settings-msmdsrvini"></a>Definindo as configurações do Analysis Services (msmdsrv.ini)
No diretório `<install directory>\PBIRS\ASEngine`, você encontrará o arquivo *msmdsrv.ini*, que poderá ser usado para controlar as diferentes configurações do Analysis Services. Ao abrir esse arquivo, você perceberá imediatamente que ele não tem todas as configurações esperadas no arquivo msmdsrv.ini. 

Isso ocorre porque o processo real do Analysis Services executado pelo Servidor de Relatórios do Power BI é iniciado em `<install directory>\PBIRS\ASEngine\workspaces`. Nessa pasta, será possível encontrar o arquivo *msmdsrv.ini* completo ao qual você está acostumado. É importante não modificar o arquivo na pasta workspaces, já que ele é regravado sempre que o processo do Analysis Services é iniciado. Se desejar controlar uma configuração, modifique o msmdsrv.ini no diretório `<install directory>\PBIRS\ASEngine`.

As configurações a seguir são redefinidas sempre que o processo do Analysis Services é iniciado. As alterações realizadas a elas serão ignoradas.

* ConfigurationSettings\PrivateProcess
* ConfigurationSettings\DataDir
* ConfigurationSettings\LogDir
* ConfigurationSettings\TempDir
* ConfigurationSettings\BackupDir
* ConfigurationSettings\AllowedBrowsingFolders
* ConfigurationSettings\CrashReportsFolder
* ConfigurationSettings\ExtensionDir
* ConfigurationSettings\Port
* ConfigurationSettings\DeploymentMode
* ConfigurationSettings\ServerLocation
* ConfigurationSettings\TMCompatabilitySKU
* ConfigurationSettings\FlightRecorder\TraceDefinitionFile

### <a name="profiling-the-local-analysis-services-process"></a>Criação de perfil do processo do Analysis Services local
É possível executar um rastreamento do SQL Profiler no processo do Analysis Services local para fins de diagnóstico. Para conectar-se à instância do Analysis Services local, faça o seguinte.

O Rastreamento do SQL Server Profiler está incluído com o [download do SSMS (SQL Server Management Studio)](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms).

1. Inicie o **SQL Server Profiler** como administrador.
2. Selecione o botão **Novo Rastreamento**.
3. Na caixa de diálogo **Conectar-se ao servidor**, selecione **Analysis Services** e digite **localhost:5132** para o nome do servidor.
4. Na caixa de diálogo **Propriedades do Rastreamento**, selecione os eventos que você deseja capturar e **Executar**.

## <a name="lock-pages-in-memory-windows-privilege"></a>Privilégio Bloquear páginas na memória do Windows
Se perceber que não é possível renderizar um relatório do Power BI, atribuir o privilégio **Bloquear páginas na memória** à conta de serviço que executa o Servidor de Relatórios do Power BI poderá ajudar. Para obter mais informações sobre como configurar o privilégio **Bloquear páginas na memória**, consulte [Privilégios do Windows atribuídos à conta de serviço do Analysis Services](https://docs.microsoft.com/sql/analysis-services/instances/configure-service-accounts-analysis-services#bkmk_winpriv).

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)

