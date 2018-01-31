---
title: "Notas de versão do Servidor de Relatório do Power BI"
description: "Este tópico descreve as limitações e os problemas com o Servidor de Relatório do Power BI."
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
ms.openlocfilehash: 7f59e3788b24344b5f86b146fb41e440eb0a2098
ms.sourcegitcommit: 6e693f9caf98385a2c45890cd0fbf2403f0dbb8a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2018
---
# <a name="power-bi-report-server-release-notes"></a>Notas de versão do Servidor de Relatório do Power BI
Este tópico descreve as limitações e os problemas com o Servidor de Relatório do Power BI.

Para baixar o Servidor de Relatório do Power BI e o Power BI Desktop otimizado para o Servidor de Relatório do Power BI, acesse [Relatórios locais com o Servidor de Relatório do Power BI](https://powerbi.microsoft.com/report-server/).

## <a name="october-2017"></a>Outubro de 2017
* Suporte para os dados importados nos relatórios do Power BI
* Capacidade de exibir as pastas de trabalho do Excel no portal da Web. Isso é feito ao configurar o Servidor do Office Online.
* Suporte para a nova tabela do Power BI e para a matriz de elementos visuais.
* Suporte para API REST

## <a name="june-2017"></a>Junho de 2017
* Não há itens novos para junho de 2017.

## <a name="may-2017"></a>Maio de 2017
* Os relatórios do Power BI devem ser criados com o Power BI Desktop otimizado para o Servidor de Relatório do Power BI para trabalhar com o Servidor de Relatório do Power BI. É possível baixar o Power BI Desktop no link de download na parte superior desta página.
* Os Relatórios do Power BI só dão suporte a conexões em tempo real com o Analysis Services (tabulares ou multidimensionais).
* Não há suporte para visuais de R.

**Problema e impacto sobre o cliente:** se você tiver o SQL Server Reporting Services e o Servidor de Relatório do Power BI no mesmo computador e desinstalar um deles, não será mais possível se conectar ao servidor de relatório restante com o Gerenciador de Configurações do Servidor de Relatório.

**Solução alternativa** Para contornar esse problema, é necessário realizar as seguintes operações depois de desinstalar um dos servidores.

1. Inicie um prompt de comando no modo de administrador.
2. Vá para o diretório em que o servidor de relatório restante está instalado.
   
    *Local padrão para o Servidor de Relatório do Power BI: C:\Arquivos de Programas\Servidor de Relatório do Microsoft Power BI*
   
    *Local padrão do SQL Server Reporting Services: C:\Arquivos de Programas\Microsoft SQL Server Reporting Services*
3. Em seguida, vá para a próxima pasta. Ela será *SSRS* ou *PBIRS* dependendo do que sobrou.
4. Vá para a pasta WMI.
5. Execute o seguinte comando:
   
    ```
    regsvr32 /i ReportingServicesWMIProvider.dll
    ```
   
    Será possível ignorar o erro a seguir, se você o vir.
   
    ```
    The module "ReportingServicesWMIProvider.dll" was loaded but the entry-point DLLInstall was not found. Make sure that "ReportingServicesWMIProvider.dll" is a valid DLL or OCX file and then try again.
    ```

## <a name="next-steps"></a>Próximas etapas
[Novidades no Servidor de Relatório do Power BI](whats-new.md)  
[Manual do usuário](user-handbook-overview.md)  
[Manual do administrador](admin-handbook-overview.md)  
[Início rápido: instalar o Servidor de Relatório do Power BI](quickstart-install-report-server.md)  
[Instalar o Construtor de Relatórios](https://docs.microsoft.com/sql/reporting-services/install-windows/install-report-builder)  
[Baixar o SSDT (SQL Server Data Tools)](http://go.microsoft.com/fwlink/?LinkID=616714)

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)

