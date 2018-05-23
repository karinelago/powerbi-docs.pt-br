---
title: Hospedar pastas de trabalho do Excel usando o OOS (Servidor do Office Online) - Servidor de Relatórios do Power BI
description: Além de exibir os relatórios do Power BI no portal da Web, o Servidor de Relatórios do Power BI pode hospedar pastas de trabalho do Excel usando o OOS (Servidor do Office Online).
author: markingmyname
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-report-server
ms.topic: conceptual
ms.date: 04/23/2018
ms.author: maghan
ms.openlocfilehash: 8a002105fcb9f5dc07197aac5722a57c7bba14b6
ms.sourcegitcommit: 638de55f996d177063561b36d95c8c71ea7af3ed
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/17/2018
---
# <a name="configure-your-report-server-to-host-excel-workbooks-using-office-online-server-oos"></a>Configure seu servidor de relatório para hospedar pastas de trabalho do Excel usando o OOS (Servidor do Office Online)
Além de exibir os relatórios do Power BI no portal da Web, o Servidor de Relatórios do Power BI pode hospedar pastas de trabalho do Excel usando o [OOS (Servidor do Office Online)](https://docs.microsoft.com/officeonlineserver/office-online-server-overview). O servidor de relatório se torna um único local para publicar e exibir o conteúdo do Microsoft BI de autoatendimento.

![Relatórios do Excel visualizados do portal da Web do servidor de relatórios.](media/excel-oos/excel-in-pbirs.png)

## <a name="prepare-server-to-run-office-online-server"></a>Preparar o servidor para executar o Servidor do Office Online
Realize esses procedimentos no servidor que executará o Servidor do Office Online. Esse servidor deve ser o Windows Server 2012 R2 ou o Windows Server 2016. O Windows Server 2016 requer o Servidor do Office Online de abril de 2017 ou posterior.

### <a name="install-prerequisite-software-for-office-online-server"></a>Instalação do software de pré-requisito no Servidor do Office Online
1. Abra o prompt do Windows PowerShell como administrador e execute este comando para instalar os serviços e as funções necessárias.
   
    **Windows Server 2012 R2:**
   
    ```
    Add-WindowsFeature Web-Server,Web-Mgmt-Tools,Web-Mgmt-Console,Web-WebServer,Web-Common-Http,Web-Default-Doc,Web-Static-Content,Web-Performance,Web-Stat-Compression,Web-Dyn-Compression,Web-Security,Web-Filtering,Web-Windows-Auth,Web-App-Dev,Web-Net-Ext45,Web-Asp-Net45,Web-ISAPI-Ext,Web-ISAPI-Filter,Web-Includes,InkandHandwritingServices,NET-Framework-Features,NET-Framework-Core,NET-HTTP-Activation,NET-Non-HTTP-Activ,NET-WCF-HTTP-Activation45,Windows-Identity-Foundation,Server-Media-Foundation
    ```
   
    **Windows Server 2016:**
   
    ```
    Add-WindowsFeature Web-Server,Web-Mgmt-Tools,Web-Mgmt-Console,Web-WebServer,Web-Common-Http,Web-Default-Doc,Web-Static-Content,Web-Performance,Web-Stat-Compression,Web-Dyn-Compression,Web-Security,Web-Filtering,Web-Windows-Auth,Web-App-Dev,Web-Net-Ext45,Web-Asp-Net45,Web-ISAPI-Ext,Web-ISAPI-Filter,Web-Includes,NET-Framework-Features,NET-Framework-45-Features,NET-Framework-Core,NET-Framework-45-Core,NET-HTTP-Activation,NET-Non-HTTP-Activ,NET-WCF-HTTP-Activation45,Windows-Identity-Foundation,Server-Media-Foundation
    ```
   
    Se solicitado, reinicie o servidor.
2. Instale o software a seguir:
   
   * [.NET Framework 4.5.2](https://go.microsoft.com/fwlink/p/?LinkId=510096)
   * [Pacotes Redistribuíveis do Visual C++ para o Visual Studio 2013](https://www.microsoft.com/download/details.aspx?id=40784)
   * [Pacotes Redistribuíveis do Visual C++ para Visual Studio 2015](https://go.microsoft.com/fwlink/p/?LinkId=620071)
   * [Microsoft.IdentityModel.Extention.dll](https://go.microsoft.com/fwlink/p/?LinkId=620072)

### <a name="install-office-online-server"></a>Instalar o Servidor do Office Online
Se você planeja usar os recursos do Excel Online que utilizam acesso a dados externos (como o Power Pivot), observe que o Servidor do Office Online deve residir na mesma floresta do Active Directory que seus usuários, bem como qualquer fonte de dados externa que você planeje acessar usando a autenticação baseada no Windows.

1. Baixar o Servidor do Office Online do [VLSC (Centro de Atendimento de Licenciamento por Volume)](http://go.microsoft.com/fwlink/p/?LinkId=256561). O download está localizado nesses produtos do Office no portal do VLSC. Para fins de desenvolvimento, você pode baixar o OOS dos downloads do assinante do MSDN.
2. Execute o Setup.exe.
3. Na página **Leia os termos de licença para Software Microsoft**, selecione **Aceito os termos deste contrato** e **Continuar**.
4. Na página **Escolher um local do arquivo**, selecione a pasta na qual você deseja que os arquivos do Servidor do Office Online sejam instalados (por exemplo, *C:\Arquivos de Programas\Microsoft Office Web Apps*) e selecione **Instalar Agora**. Se a pasta especificada não existir, o assistente de instalação a criará para você.
   
    É recomendável que você instale o Servidor do Office Online na unidade do sistema.
5. Quando a instalação do Servidor do Office Online for concluída, selecione **Fechar**.

### <a name="install-language-packs-for-office-web-apps-server-optional"></a>Instalar pacotes de idiomas no Servidor do Office Online (opcional)
Os pacotes de idioma do Servidor do Office Online permitem que os usuários exibam arquivos do Office com base na Web em vários idiomas.

Para instalar os pacotes de idiomas, siga estas etapas.

1. Baixe os pacotes de idiomas do Servidor do Office Online do [Centro de Download da Microsoft](http://go.microsoft.com/fwlink/p/?LinkId=798136).
2. Execute **wacserverlanguagepack.exe**.
3. No assistente do pacote de idiomas do Servidor do Office Online, na página **Leia os termos de licença para Software Microsoft**, selecione **Aceito os termos deste contrato** e **Continuar**.
4. Quando a instalação do Servidor do Office Online for concluída, selecione **Fechar**.

## <a name="deploy-office-online-server"></a>Implantar o Servidor do Office Online
### <a name="create-the-office-online-server-farm-https"></a>Criar o farm do Servidor do Office Online (HTTPS)
Use o comando New-OfficeWebAppsFarm para criar um novo farm do Servidor do Office Online que consiste em um único servidor, conforme mostrado no exemplo a seguir.

```
New-OfficeWebAppsFarm -InternalUrl "https://server.contoso.com" -ExternalUrl "https://wacweb01.contoso.com" -CertificateName "OfficeWebApps Certificate"
```

**Parâmetros**

* ** – InternalURL** é o FQDN (nome de domínio totalmente qualificado) do servidor que executa o servidor do Office Online, como http://servername.contoso.com.
* **– ExternalURL** é o FQDN que pode ser acessado na Internet.
* **– CertificateName** é o nome amigável do certificado.

### <a name="create-the-office-online-server-farm-http"></a>Criar o farm do Servidor do Office Online (HTTP)
Use o comando New-OfficeWebAppsFarm para criar um novo farm do Servidor do Office Online que consiste em um único servidor, conforme mostrado no exemplo a seguir.

```
New-OfficeWebAppsFarm -InternalURL "http://servername" -AllowHttp
```

**Parâmetros**

* ** – InternalURL** é o nome do servidor que executa o Servidor do Office Online, como http://servername.
* **– AllowHttp** configura o farm para usar o HTTP.

### <a name="verify-that-the-office-online-server-farm-was-created-successfully"></a>Verifique se o farm do Servidor do Office Online foi criado com êxito
Após a criação do farm, os detalhes sobre ele serão exibidos no prompt do Windows PowerShell. Para verificar se o Servidor do Office Online está instalado e configurado corretamente, use um navegador da Web para acessar a URL de descoberta do Servidor do Office Online, conforme mostrado no exemplo a seguir. A URL de descoberta é o parâmetro *InternalUrl* que você especificou quando configurou o farm do Servidor do Office Online, seguido por */hosting/discovery*, por exemplo:

```
<InternalUrl>/hosting/discovery
```

Se o Servidor do Office Online funcionar conforme o esperado, você deverá ver um arquivo XML de descoberta do WOPI (Interface de Plataforma Aberta de aplicativo Web) em seu navegador da Web. As primeiras linhas do arquivo devem se parecer com o exemplo a seguir:

```
<?xml version="1.0" encoding="utf-8" ?> 
- <wopi-discovery>
- <net-zone name="internal-http">
- <app name="Excel" favIconUrl="<InternalUrl>/x/_layouts/images/FavIcon_Excel.ico" checkLicense="true">
<action name="view" ext="ods" default="true" urlsrc="<InternalUrl>/x/_layouts/xlviewerinternal.aspx?<ui=UI_LLCC&><rs=DC_LLCC&>" /> 
<action name="view" ext="xls" default="true" urlsrc="<InternalUrl>/x/_layouts/xlviewerinternal.aspx?<ui=UI_LLCC&><rs=DC_LLCC&>" /> 
<action name="view" ext="xlsb" default="true" urlsrc="<InternalUrl>/x/_layouts/xlviewerinternal.aspx?<ui=UI_LLCC&><rs=DC_LLCC&>" /> 
<action name="view" ext="xlsm" default="true" urlsrc="<InternalUrl>/x/_layouts/xlviewerinternal.aspx?<ui=UI_LLCC&><rs=DC_LLCC&>" /> 
```

### <a name="configure-excel-workbook-maximum-size"></a>Configurar o tamanho máximo da pasta de trabalho do Excel
O tamanho do arquivo máximo para todos os arquivos no Servidor de Relatórios do Power BI é 100 MB. Para que você se mantenha atualizado, essa informação deve ser configurada manualmente no OOS.

```
Set-OfficeWebAppsFarm -ExcelWorkbookSizeMax 100
```

## <a name="using-effectiveusername-with-analysis-services"></a>Uso do EffectiveUserName com o Analysis Services
Para permitir conexões dinâmicas com o Analysis Services e conexões em uma pasta de trabalho do Excel que usa EffectiveUserName. Para que o OOS faça uso do EffectiveUserName, você precisará adicionar a conta do computador do servidor do OOS como um administrador da instância do Analysis Services. O Management Studio para SQL Server 2016 ou posterior é necessário para executar esta ação.

No momento, há suporte apenas para as conexões incorporadas do Analysis Services em uma pasta de trabalho do Excel. A conta de usuário precisará ter permissão para se conectar ao Analysis Services, uma vez que a capacidade de proxy do usuário não está disponível.

Execute os seguintes comandos do PowerShell no servidor do OOS.

```
Set-OfficeWebAppsFarm -ExcelUseEffectiveUserName:$true
Set-OfficeWebAppsFarm -ExcelAllowExternalData:$true
Set-OfficeWebAppsFarm -ExcelWarnOnDataRefresh:$false
```

## <a name="configure-a-power-pivot-instance-for-data-models"></a>Configurar uma instância do PowerPivot para modelos de dados
A instalação de uma instância do modo PowerPivot do Analysis Services permite que você trabalhe com as pastas de trabalho do Excel que estão usando o Power Pivot. Confirme se o nome da instância é *POWERPIVOT*. Adicione a conta do computador do servidor do OOS como administrador na instância do modo PowerPivot do Analysis Services. O Management Studio para SQL Server 2016 ou posterior é necessário para executar esta ação.

Para o OOS usar a instância do modo Power Pivot, execute o seguinte comando.

```
New-OfficeWebAppsExcelBIServer -ServerId <server_name>\POWERPIVOT
```

Se você ainda não permitiu os dados externos, da etapa do Analysis Services anterior, execute o seguinte comando.

```
Set-OfficeWebAppsFarm -ExcelAllowExternalData:$true
```

### <a name="firewall-considerations"></a>Considerações sobre o firewall
Para evitar problemas de firewall, talvez seja necessário abrir as portas 2382 e 2383. Você também pode adicionar o *msmdsrv.exe* para a instância do PowerPivot, como uma política de firewall do aplicativo.

## <a name="configure-power-bi-report-server-to-use-the-oos-server"></a>Configurar o Servidor de Relatórios do Power BI para usar o Servidor de OOS
Na página **Geral** das **Configurações do site**, insira a URL de descoberta do OOS. A URL de descoberta do OOS é a *InternalUrl* usada ao implantar o servidor do OOS, seguida por */hosting/discovery*. Por exemplo, `http://servername/hosting/discovery`, para HTTP. E, `https://server.contoso.com/hosting/discovery` para HTTPS.

Para obter as **Configurações do site**, selecione o **ícone de engrenagem** no canto superior direito e selecione **Configurações do site**.

Somente um usuário com função de **Administrador do Sistema** verá a configuração da URL de descoberta do Servidor do Office Online.

![Configurações do site para o Servidor de Relatórios do Power BI.](media/excel-oos/reportserver-site-settings.png)

Depois de inserir a URL de descoberta e selecionar **Aplicar**, a seleção de uma pasta de trabalho do Excel no portal da Web deverá exibir a pasta de trabalho no portal da Web.

## <a name="limitations-and-considerations"></a>Limitações e considerações
* A capacidade de exibir as pastas de trabalho do Excel no Servidor de Relatórios do Power BI está na versão prévia no momento.
* Você terá a funcionalidade somente leitura das pastas de trabalho.

## <a name="next-steps"></a>Próximas etapas
[Manual do administrador](admin-handbook-overview.md)  
[Instalar o Servidor de Relatório do Power BI](install-report-server.md)  
[Instalar o Construtor de Relatórios](https://docs.microsoft.com/sql/reporting-services/install-windows/install-report-builder)  
[Baixar o SSDT (SQL Server Data Tools)](http://go.microsoft.com/fwlink/?LinkID=616714)

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)

