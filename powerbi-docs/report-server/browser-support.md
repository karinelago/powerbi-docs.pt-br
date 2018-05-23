---
title: Suporte do navegador para o Servidor de Relatório do Power BI
description: Saiba quais versões de navegador têm suporte para gerenciar e exibir o Servidor de Relatório do Power BI e os Controles do Visualizador de Relatórios.
author: markingmyname
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-report-server
ms.topic: conceptual
ms.date: 01/25/2018
ms.author: maghan
ms.openlocfilehash: 23eea014ca4554a2df676cf1fe0be54c2b69d15a
ms.sourcegitcommit: 638de55f996d177063561b36d95c8c71ea7af3ed
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/17/2018
---
# <a name="browser-support-for-power-bi-report-server"></a>Suporte do navegador para o Servidor de Relatório do Power BI
Saiba quais versões de navegador têm suporte para gerenciar e exibir o Servidor de Relatório do Power BI e os Controles do Visualizador de Relatórios.

## <a name="browser-requirements-for-the-web-portal"></a>Requisitos de navegador do portal da Web
Veja a seguir a lista atual de navegadores com suporte no portal da Web.

**Microsoft Windows**  
*Windows 7, 8.1, 10; Windows Server 2008 R2, 2012, 2012 R2*

* Microsoft Edge (+)
* Microsoft Internet Explorer 11
* Google Chrome (+)
* Mozilla Firefox (+)

**Apple OS X**  
*OS X 10.9-10.11*

* Apple Safari (+)
* Google Chrome (+)
* Mozilla Firefox (+)

**Apple iOS**  
*iPhone e iPad com iOS 10*

* Apple Safari (+)

**Google Android**  
*Telefones e tablets com Android 4.4 (KitKat) ou posterior*

* Google Chrome (+)
  
  **(+)** Versão lançada publicamente mais recente

## <a name="browser-requirements-for-the-report-viewer-web-control-2015"></a>Requisitos de navegador para o controle da Web do Visualizador de Relatórios (2015)
Veja a seguir a lista atual de navegadores com suporte no controle da Web do Visualizador de Relatórios. O visualizador de relatórios dá suporte à visualização de relatórios do portal da Web.

**Microsoft Windows**  
*Windows 7, 8.1, 10; Windows Server 2008 R2, 2012, 2012 R2*

* Microsoft Edge (+)
* Microsoft Internet Explorer 11
* Google Chrome (+)
* Mozilla Firefox (+)

**Apple OS X**  
*OS X 10.9-10.11*

* Apple Safari (+)
  
  **(+)** Versão lançada publicamente mais recente

### <a name="authentication-requirements"></a>Requisitos de autenticação
Os navegadores dão suporte a esquemas de autenticação específicos que devem ser tratados pelo servidor de relatório para que a solicitação do cliente seja bem-sucedida. A tabela a seguir identifica os tipos de autenticação padrão com suporte em cada navegador em execução em um sistema operacional Windows.

| **Tipo de navegador** | **Dá suporte a** | **Padrão de navegador** | **Padrão de servidor** |
| --- | --- | --- | --- |
| **Microsoft Edge** (+) |Negotiate, Kerberos, NTLM, Basic |Negotiate |Sim. As configurações de autenticação padrão funcionam com o Edge. |
| **Microsoft Internet Explorer** |Negotiate, Kerberos, NTLM, Basic |Negotiate |Sim. As configurações de autenticação padrão funcionam com o Internet Explorer. |
| **Google Chrome**(+) |Negotiate, NTLM, Basic |Negotiate |Sim. As configurações de autenticação padrão funcionam com o Chrome. |
| **Mozilla Firefox**(+) |NTLM, Basic |NTLM |Sim. As configurações de autenticação padrão funcionam com o Firefox. |
| **Apple Safari**(+) |NTLM, Basic |Básica |Sim. As configurações de autenticação padrão funcionam com o Safari. |

 **(+)** Versão lançada publicamente mais recente

### <a name="script-requirements-for-viewing-reports"></a>Requisitos de script para exibir relatórios
Para usar o visualizador de relatórios, configure seu navegador para executar scripts.

Se o script não estiver habilitado, você verá uma mensagem de erro semelhante à seguinte quando você abrir um relatório:

```
Your browser does not support scripts or has been configured to not allow scripts to run. Click here to view this report without scripts
```

 Se você optar por exibir o relatório sem suporte a script, ele será renderizado em HTML sem os recursos de visualizador de relatórios, como a barra de ferramentas de relatório e o mapa do documento.

> [!NOTE]
> A barra de ferramentas de relatório faz parte do componente Visualizador de HTML. Por padrão, a barra de ferramentas é exibida na parte superior de todo relatório que é renderizado em uma janela do navegador. O visualizador de relatórios fornece recursos que incluem a capacidade de pesquisar informações no relatório, rolar até uma página específica e ajustar o tamanho da página para fins de visualização. Para obter mais informações sobre a barra de ferramentas de relatório ou sobre o Visualizador de HTML, consulte [Visualizador de HTML e a barra de ferramentas de relatório](https://docs.microsoft.com/sql/reporting-services/html-viewer-and-the-report-toolbar).
> 
> 

## <a name="browser-support-for-report-viewer-web-server-controls-in-visual-studio"></a>Suporte do navegador para controles de servidor Web do Visualizador de Relatórios no Visual Studio
O controle de servidor Web do Visualizador de relatórios é usado para inserir a funcionalidade de relatório em um aplicativo Web ASP .NET. Para obter mais informações sobre como obter o Controle do Visualizador de Relatórios, consulte [Integrating Reporting Services Using Report Viewer Controls – Get Started (Integrando Reporting Services usando os Controles do Visualizador de Relatórios – Introdução)](https://docs.microsoft.com/sql/reporting-services/application-integration/integrating-reporting-services-using-reportviewer-controls-get-started).

Use um navegador com suporte a script habilitado. Se o navegador não pode executar scripts, não é possível exibir o relatório.

**Microsoft Windows**  
*Windows 7, 8.1, 10; Windows Server 2008 R2, 2012, 2012 R2*

* Microsoft Edge (+)
* Microsoft Internet Explorer 11
* Google Chrome (+)
* Mozilla Firefox (+)
  
  **(+)** Versão lançada publicamente mais recente

## <a name="next-steps"></a>Próximas etapas
[Manual do administrador](admin-handbook-overview.md)  
[Instalar o Servidor de Relatório do Power BI](install-report-server.md)  
[Instalar o Construtor de Relatórios](https://docs.microsoft.com/sql/reporting-services/install-windows/install-report-builder)  
[Baixar o SSDT (SQL Server Data Tools)](http://go.microsoft.com/fwlink/?LinkID=616714)

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)

