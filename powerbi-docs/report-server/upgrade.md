---
title: Atualizar o Servidor de Relatório do Power BI
description: Saiba como atualizar o Servidor de Relatório do Power BI.
author: markingmyname
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-report-server
ms.topic: conceptual
ms.date: 09/05/2017
ms.author: maghan
ms.openlocfilehash: e54ddf59221b472bbac4e8665e036529ba475d9c
ms.sourcegitcommit: 638de55f996d177063561b36d95c8c71ea7af3ed
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/17/2018
---
# <a name="upgrade-power-bi-report-server"></a>Atualizar o Servidor de Relatório do Power BI
Saiba como atualizar o Servidor de Relatório do Power BI.

 **Baixe** ![baixe](media/upgrade/download.png "baixe")

Para baixar o Servidor de Relatório do Power BI e o Power BI Desktop otimizado para o Servidor de Relatório do Power BI, acesse [Relatórios locais com o Servidor de Relatório do Power BI](https://powerbi.microsoft.com/report-server/).

## <a name="before-you-begin"></a>Antes de começar
Antes de atualizar um servidor de relatório, é recomendável que você execute as seguintes etapas para fazer backup de seu servidor de relatório.

### <a name="backing-up-the-encryption-keys"></a>Fazendo backup das chaves de criptografia
Você precisa fazer backup das chaves de criptografia ao configurar uma instalação do servidor de relatório pela primeira vez. Você também precisa fazer backup das chaves sempre que alterar a identidade das contas de serviço ou renomear o computador. Para obter mais informações, consulte [Backup e restauração das chaves de criptografia do Reporting Services](https://docs.microsoft.com/sql/reporting-services/install-windows/ssrs-encryption-keys-back-up-and-restore-encryption-keys).

### <a name="backing-up-the-report-server-databases"></a>Fazendo backup dos bancos de dados do servidor de relatório
Como um servidor de relatório é um servidor sem monitoração de estado, todos os dados do aplicativo são armazenados nos bancos de dados **reportserver** e **reportservertempdb** que são executados em uma instância do Mecanismo de Banco de Dados do SQL Server. Você pode fazer backup dos bancos de dados **reportserver** e **reportservertempdb** usando um dos métodos com suporte para fazer backup de bancos de dados do SQL Server. Recomendações específicas aos bancos de dados do servidor de relatório incluem o seguinte:

* Use o modelo de recuperação completa para fazer backup do banco de dados **reportserver**.
* Use o modelo de recuperação simples para fazer backup do banco de dados **reportservertempdb**.
* Você pode usar diferentes cronogramas de backup para cada banco de dados. A única razão para fazer backup de **reportservertempdb** é evitar ter que recriá-lo se ocorrer uma falha de hardware. No caso de uma falha de hardware, não será necessário recuperar os dados em **reportservertempdb**, mas você precisará da estrutura de tabela. Se você perder **reportservertempdb**, a única maneira de recuperá-lo será recriar o banco de dados do servidor de relatório. Se você recriar o **reportservertempdb**, é importante que ele tenha o mesmo nome que o banco de dados do servidor de relatório primário.

Para obter mais informações sobre backup e recuperação de bancos de dados relacionais do SQL Server, consulte [Backup e restauração de bancos de dados do SQL Server](https://docs.microsoft.com/sql/relational-databases/backup-restore/back-up-and-restore-of-sql-server-databases).

### <a name="backing-up-the-configuration-files"></a>Fazendo backup dos arquivos de configuração
O Servidor de Relatório do Power BI usa arquivos de configuração para armazenar configurações de aplicativo. Faça backup dos arquivos quando configurar o servidor pela primeira vez e depois de implantar qualquer extensão personalizada. Os arquivos para backup incluem:

* config.json
* RSHostingService.exe.config
* Rsreportserver.config
* Rssvrpolicy.config
* Reportingservicesservice.exe.config
* Web.config para os aplicativos ASP.NET do Servidor de Relatório
* Machine.config para ASP.NET

## <a name="upgrade-the-report-server"></a>Atualizar o servidor de relatório
A atualização do Servidor de Relatório do Power BI é simples. Há apenas algumas etapas para instalar os arquivos.

1. Encontrar o local do PowerBIReportServer.exe e inicie o instalador.
2. Selecione **Atualizar o Servidor de Relatório do Power BI**.
   
    ![](media/upgrade/reportserver-upgrade1.png "Atualizar o Servidor de Relatórios do Power BI")
3. Leia e concorde com os termos e condições da licença e, em seguida, selecione **Atualizar**.
   
    ![](media/upgrade/reportserver-upgrade-eula.png "Contrato de licença")
4. Após uma atualização bem-sucedida, você pode selecionar **Configurar o Servidor de Relatório** para iniciar o Gerenciador de Configurações do Reporting Services ou pode selecionar **Fechar** para sair do instalador.
   
    ![](media/upgrade/reportserver-upgrade-configure.png)

## <a name="upgrade-power-bi-desktop"></a>Atualizar o Power BI Desktop
Após o servidor de relatório ser atualizado, certifique-se de que todos os autores de relatórios do Power BI atualizem para a versão do Power BI Desktop otimizado para o Servidor de Relatório do Power BI correspondente ao servidor.

## <a name="next-steps"></a>Próximas etapas
[Manual do administrador](admin-handbook-overview.md)  
[Instalar o Power BI Desktop otimizado para o Servidor de Relatório do Power BI](install-powerbi-desktop.md)  
[Verificar a instalação do Reporting Services](https://docs.microsoft.com/sql/reporting-services/install-windows/verify-a-reporting-services-installation)  
[Configurar a conta de serviço do Servidor de Relatório](https://docs.microsoft.com/sql/reporting-services/install-windows/configure-the-report-server-service-account-ssrs-configuration-manager)  
[Configurar URLs do Servidor de Relatório](https://docs.microsoft.com/sql/reporting-services/install-windows/configure-report-server-urls-ssrs-configuration-manager)  
[Configurar uma conexão de banco de dados do Servidor de Relatório](https://docs.microsoft.com/sql/reporting-services/install-windows/configure-a-report-server-database-connection-ssrs-configuration-manager)  
[Inicializar um Servidor de Relatório](https://docs.microsoft.com/sql/reporting-services/install-windows/ssrs-encryption-keys-initialize-a-report-server)  
[Configurar conexões SSL em um servidor de relatório](https://docs.microsoft.com/sql/reporting-services/security/configure-ssl-connections-on-a-native-mode-report-server)  
[Configurar permissões e contas de serviço Windows](https://docs.microsoft.com/sql/database-engine/configure-windows/configure-windows-service-accounts-and-permissions)  
[Suporte do navegador para o Servidor de Relatório do Power BI](browser-support.md)

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)

