---
title: "Requisitos de Hardware e de Software para a instalação do Servidor de Relatório do Power BI"
description: "Aqui você encontrará os requisitos mínimos de hardware e de software para instalar e executar o Servidor de Relatório do Power BI."
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
ms.openlocfilehash: 44a1af1553aaa28a5f4abab13bad1fafa040003a
ms.sourcegitcommit: 6e693f9caf98385a2c45890cd0fbf2403f0dbb8a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2018
---
# <a name="hardware-and-software-requirements-for-installing-power-bi-report-server"></a>Requisitos de hardware e de software para a instalação do Servidor de Relatório do Power BI
Aqui você encontrará os requisitos mínimos de hardware e de software para instalar e executar o Servidor de Relatório do Power BI.

## <a name="processor-memory-and-operating-system-requirements"></a>Requisitos de processador, de memória e de sistema operacional
| Componente | Requisito |
| --- | --- |
| .NET Framework |4.6<br><br>É possível instalar manualmente o .NET Framework no [Microsoft .NET Framework 4.6 (instalador da Web) para Windows](http://support.microsoft.com/kb/3045560).<br/><br/> Para obter mais informações, recomendações e diretrizes sobre o .NET Framework 4.6, consulte [Guia de implantação do .NET Framework para desenvolvedores](http://msdn.microsoft.com/library/ee942965\(v=vs.110\).aspx).<br/><br/>O Windows 8.1 e o Windows Server 2012 R2 requerem [KB2919355](http://support.microsoft.com/kb/2919355) antes da instalação do .NET Framework 4.6. |
| Disco rígido |O Servidor de Relatório do Power BI requer 1 GB, no mínimo, de espaço em disco disponível.<br><br>Será necessário ter espaço adicional no servidor de banco de dados que está hospedando o banco de dados do servidor de relatório. |
| Memória |**Mínimo:** 1 GB<br/><br/> **Recomendado:** pelo menos 4 GB |
| Velocidade do processador |**Mínimo:** x64 Processador: 1.4 GHz<br/><br/> **Recomendado:** 2.0 GHz ou mais rápido |
| Tipo de processador |x64 Processador: AMD Opteron, AMD Athlon 64, Intel Xeon com suporte a Intel EM64T, Intel Pentium IV com suporte a EM64T |
| Sistema Operacional |Windows Server 2016 Datacenter<br><br>Windows Server 2016 Standard<br><br>Windows Server 2012 R2 Datacenter<br><br>Windows Server 2012 R2 Standard<br><br>Windows Server 2012 R2 Essentials<br><br>Windows Server 2012 R2 Foundation<br><br>Windows Server 2012 Datacenter<br><br>Windows Server 2012 Standard<br><br>Windows Server 2012 Essentials<br><br>Windows Server 2012 Foundation<br><br>Windows 10 Home<br><br>Windows 10 Professional<br><br>Windows 10 Enterprise<br><br>Windows 8.1<br><br>Windows 8.1 Pro<br><br>Windows 8.1 Enterprise<br><br>Windows 8<br><br>Windows 8 Pro<br><br>Windows 8 Enterprise |

> [!NOTE]
> A instalação do Servidor de Relatórios do Power BI só é compatível com processadores x64.
> 
> 

## <a name="database-server-version-requirements"></a>Requisitos de versão do servidor de banco de dados
O SQL Server é usado para hospedar os bancos de dados do servidor de relatório. A instância do Mecanismo de Banco de Dados do SQL Server pode ser uma instância local ou remota. Estas são as versões com suporte do Mecanismo de Banco de Dados do SQL Server que pode ser usado para hospedar os bancos de dados do servidor de relatório:

* SQL Server 2017
* SQL Server 2016
* SQL Server 2014
* SQL Server 2012
* SQL Server 2008 R2
* SQL Server 2008

A criação do banco de dados do servidor de relatório em um computador remoto requer que você configure a conexão para usar uma conta de usuário de domínio ou uma conta de serviço com acesso à rede. Se você decidir usar uma instância remota do SQL Server, considere cuidadosamente quais credenciais o servidor de relatório deverá usar para se conectar à instância do SQL Server. Para obter mais informações, consulte [Configure a Report Server Database Connection (Configurar uma conexão de banco de dados do servidor de relatório)](https://docs.microsoft.com/sql/reporting-services/install-windows/configure-a-report-server-database-connection-ssrs-configuration-manager).

## <a name="considerations"></a>Considerações
O Servidor de Relatório do Power BI instalará valores padrão para definir as configurações básicas necessárias para tornar operacional um servidor de relatório. Ele tem os seguintes requisitos:

* Um Mecanismo de Banco de Dados do SQL Server deverá estar disponível após a instalação e antes de configurar o banco de dados para o servidor de relatório. A instância do Mecanismo de Banco de Dados hospeda o banco de dados do servidor de relatório que o Gerenciador de Configurações do Reporting Services criará. O Mecanismo de Banco de Dados não é necessário para a experiência de instalação real.
* A conta de usuário usada para executar a Instalação deve ser um membro do grupo local de Administradores.
* A conta de usuário usada para o Gerenciador de Configurações do Reporting Services deve ter permissão para acessar e criar bancos de dados na instância do Mecanismo de Banco de Dados que hospeda os bancos de dados do servidor de relatório.
* A instalação deve poder usar os valores padrão para reservar as URLs que fornecem acesso ao servidor de relatório e o portal da Web. Esses valores são a porta 80, um curinga forte e os nomes de diretório virtual no formato **ReportServer** e **Reports**.

## <a name="read-only-domain-controller-rodc"></a>RODC (Controlador de domínio somente leitura)
 Embora o servidor de relatório possa ser instalado em um ambiente que tenha um RODC (Controlador de domínio somente leitura), o Reporting Services precisa acessar um Controlador de Domínio Leitura-Gravação para funcionar adequadamente. Se o Reporting Services só tiver acesso a um RODC, talvez ocorram erros ao tentar administrar o serviço.

## <a name="power-bi-reports-and-analysis-services-live-connections"></a>Relatórios do Power BI e conexões dinâmicas do Analysis Services
Você pode usar uma conexão dinâmica em instâncias tabulares ou multidimensionais. Seu servidor do Analysis Services deve ter a versão e a edição adequadas para funcionar adequadamente.

| **Versão do servidor** | **SKU necessário** |
| --- | --- |
| 2012 SP1 CU4 ou posterior |Business Intelligence e SKU Enterprise |
| 2014 |Business Intelligence e SKU Enterprise |
| 2016 e posterior |SKU Standard ou superior |

## <a name="next-steps"></a>Próximas etapas
[Manual do usuário](user-handbook-overview.md)  
[Manual do administrador](admin-handbook-overview.md)  
[Início rápido: instalar o Servidor de Relatório do Power BI](quickstart-install-report-server.md)  
[Instalar o Construtor de Relatórios](https://docs.microsoft.com/sql/reporting-services/install-windows/install-report-builder)  
[Baixar o SSDT (SQL Server Data Tools)](http://go.microsoft.com/fwlink/?LinkID=616714)

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)

