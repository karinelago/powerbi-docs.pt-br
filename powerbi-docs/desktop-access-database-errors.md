---
title: "Resolver problemas de importação do Access e .XLS no Power BI Desktop"
description: "Solucionar problemas de importação de bancos de dados do Access e planilhas .XLS no Power BI Desktop e Power Query"
services: powerbi
documentationcenter: 
author: davidiseminger
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
ms.date: 10/12/2017
ms.author: davidi
ms.openlocfilehash: 719bc102efe27261d69da80917655c6043058d92
ms.sourcegitcommit: 284b09d579d601e754a05fba2a4025723724f8eb
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/15/2017
---
# <a name="resolve-issues-importing-access-and-xls-files-in-power-bi-desktop"></a>Resolver problemas de importação de arquivos do Access e .XLS no Power BI Desktop
No **Power BI Desktop**, os **bancos de dados do Access** e as versões anteriores de **pastas de trabalho do Excel** (arquivos XLS do tipo Excel 2007-2003) usam o *mecanismo de banco de dados do Access*. Há três situações comuns que podem impedir que o Mecanismo de Banco de Dados do Access funcione corretamente:

### <a name="situation-1-no-access-database-engine-installed"></a>Situação 1: nenhum Mecanismo de Banco de Dados do Access instalado
Quando a mensagem de erro do Power BI Desktop indica que o Mecanismo de Banco de Dados do Access não está instalado, você deve instalar a versão de 32 ou 64 bits do Mecanismo de Banco de Dados do Access que corresponde à sua versão do Power BI Desktop. Você pode instalar o Mecanismo de Banco de Dados do Access [neste local](http://www.microsoft.com/en-us/download/details.aspx?id=13255).

>[!NOTE]
>Se a versão de bits instalada do Mecanismo de Banco de Dados do Access for diferente da versão de bits de instalação do Microsoft Office, os aplicativos do Office não poderão usar o Mecanismo de Banco de Dados do Access.

### <a name="situation-2-the-access-database-engine-bit-version-32-bit-or-64-bit-is-different-from-your-power-bi-desktop-bit-version"></a>Situação 2: a versão de bits do Mecanismo de Banco de Dados do Access (32 ou 64 bits) é diferente da versão de bits do Power BI Desktop
Essa situação geralmente ocorre quando a versão instalada do Microsoft Office é de 32 bits e a versão do Power BI Desktop instalada é de 64 bits. O contrário também pode ocorrer, com ocorrência de incompatibilidade de versão de bits em ambos os casos (se você estiver usando uma assinatura do Office 365, consulte **Situação 3** para problemas diferentes e soluções). Qualquer uma das seguintes soluções pode corrigir esse erro de incompatibilidade de versão de bits:

1. Altere a versão do Power BI Desktop para corresponder à versão de bits de instalação do Microsoft Office. Para alterar a versão de bits do Power BI Desktop, desinstale o Power BI Desktop e, em seguida, instale a versão do Power BI Desktop que corresponde à sua instalação do Office. Para selecionar uma versão do Power BI Desktop, na página de download para a área de trabalho, selecione **Opções de download avançadas**.
   
   ![](media/desktop-access-database-errors/desktop-access-errors-1.png)
   
   Na página de download que é exibida, escolha o idioma e selecione o botão **Baixar** . Na tela que é exibida, marque a caixa de seleção ao lado de PBIDesktop.msi para a versão de 32 bits ou PBIDesktop_x64.msi para a versão de 64 bits. Na tela a seguir, a versão de 64 bits é selecionada.
   
   ![](media/desktop-access-database-errors/desktop-access-errors-2.png)
   
   >[!NOTE]
   >Ao usar a versão de 32 bits do Power BI Desktop, ao criar modelos de dados muito grandes, você poderá ter problemas de memória insuficiente.
2. Altere a versão do Microsoft Office para corresponder à versão de bits da instalação do Power BI Desktop. Para alterar a versão de bits do Microsoft Office, desinstale o Office e, em seguida, instale a versão do Office que corresponde à sua instalação do Power BI Desktop.
3. Se o erro ocorreu ao tentar abrir um arquivo .XLS (uma pasta de trabalho do Excel 2007-2003), você pode evitar o uso do Mecanismo de Banco de Dados do Access abrindo o arquivo .XLS no Excel e salvando-o como um arquivo XLSX.
4. Se as três soluções anteriores não forem viáveis, é possível instalar as duas versões do Mecanismo de Banco de Dados do Access, mas essa *não* é uma solução alternativa recomendada. Instalar ambas as versões resolverá esse problema para o Power Query para Excel e o Power BI Desktop, mas apresentará erros e problemas de qualquer aplicativo que usa automaticamente (por padrão) a versão de bits do Mecanismo de Banco de Dados do Access que foi instalado pela primeira vez. Para instalar as duas versões de bits do Mecanismo de Banco de Dados do Access, [baixe](http://www.microsoft.com/en-us/download/details.aspx?id=13255) ambas as versões e execute cada uma delas usando a opção */passive*. Por exemplo:
   
       c:\users\joe\downloads\AccessDatabaseEngine.exe /passive
   
       c:\users\joe\downloads\AccessDatabaseEngine_x64.exe /passive

### <a name="situation-3-trouble-using-access-or-xls-files-with-an-office-365-subscription"></a>Situação 3: Problemas para utilizar o Access ou arquivos XLS com uma assinatura do Office 365
Se você estiver usando uma assinatura do Office 365, seja o **Office 2013** ou o **Office 2016**, o provedor do mecanismo de banco de dados do Access é registrado em uma localização do Registro virtual que poderá ser acessada *somente* pelos processos do Office. Como resultado, o mecanismo Mashup (que é responsável por executar o Excel fora do Office 365 e o Power BI Desktop), que não é um processo do Office, não pode usar o provedor do mecanismo de banco de dados do Access.

Para corrigir essa situação, você pode baixar e instalar o mecanismo de banco de dados do Access redistribuível que corresponde à versão de bits da instalação do seu Power BI Desktop (consulte as seções anteriores para obter mais informações sobre as versões de bits).

Link de download: [download do mecanismo de banco de dados do Access](http://www.microsoft.com/en-us/download/details.aspx?id=13255).

### <a name="other-situations-that-cause-import-issues"></a>Outras situações que causam problemas de importação
Nos esforçamos para abordar o máximo possível de problemas que ocorrem com o Access ou com arquivos XLS. Se você encontrar um problema que não foi abordado neste artigo, envie uma pergunta sobre o problema para o [suporte do Power BI](https://powerbi.microsoft.com/support/). Examinamos regularmente os problemas que podem estar afetando muitos clientes, posteriormente incluindo-os em nossos artigos.

