---
title: Usando o OAuth para conectar-se ao Reporting Services
description: Saiba como configurar seu ambiente para dar suporte à autenticação OAuth com o aplicativo móvel do Power BI para conectar-se ao Reporting Services 2016 ou posterior.
author: markingmyname
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-mobile
ms.topic: conceptual
ms.date: 08/10/2017
ms.author: maghan
ms.openlocfilehash: 4c9b2f5233ab984e57bf48978284441850c0c48f
ms.sourcegitcommit: 638de55f996d177063561b36d95c8c71ea7af3ed
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/17/2018
---
# <a name="using-oauth-to-connect-to-reporting-services"></a>Usando o OAuth para conectar-se ao Reporting Services
Saiba como configurar seu ambiente para dar suporte à autenticação OAuth com o aplicativo móvel do Power BI para conectar-se ao Reporting Services 2016 ou posterior.

![](media/mobile-oauth-ssrs/powerbi-mobile-oauth.png)

No passado, o aplicativo móvel do Power BI só dava suporte à autenticação básica, via HTTPS, ao Reporting Services para exibir relatórios móveis ou KPIs. Muitas organizações não permitem esse tipo de configuração devido a questões de segurança. Com uma atualização no aplicativo móvel do Power BI, agora é possível usar o OAuth para conectar-se ao Reporting Services. O Windows Server 2016 fornece algumas melhorias à função de Proxy de aplicativo Web para permitir esse tipo de autenticação.

## <a name="requirements"></a>Requisitos
O Windows Server 2016 é necessário para os servidores WAP (Proxy de aplicativo Web) e Serviços de Federação do Active Directory (AD FS). Não é necessário ter um domínio de nível funcional do Windows 2016.

## <a name="domain-name-services-dns-configuration"></a>Configuração DNS (Serviços de nomes de domínio)
Será necessário determinar qual será a URL pública à qual o aplicativo móvel do Power BI se conectará. Por exemplo, ela deve ser semelhante à seguinte.

```
https://reports.contoso.com
```

Será necessário apontar seu registro DNS de **relatórios** para o endereço IP público do servidor WAP (Proxy de aplicativo Web). Também será necessário configurar um registro DNS público para seu servidor AD FS. Por exemplo, talvez você tenha configurado o servidor AD FS com a seguinte URL.

```
https://fs.contoso.com
```

Será necessário apontar seu registro DNS de **fs** para o endereço IP público do servidor WAP (Proxy de aplicativo Web), uma vez que ele será publicado como parte do aplicativo WAP.

## <a name="certificates"></a>Certificados
Será necessário configurar certificados para o aplicativo WAP e o servidor AD FS. Esses certificados devem fazer parte de uma autoridade de certificado válida que seus dispositivos móveis reconheçam.

## <a name="reporting-services-configuration"></a>Configuração do Reporting Services
Não há muito o que configurar no lado do Reporting Services. Nós só precisamos nos certificar de que temos um SPN (Nome da Entidade de Serviço) válido para habilitar a autenticação Kerberos adequada que deve ocorrer e que o servidor do Reporting Services está habilitado para negociar a autenticação.

### <a name="service-principal-name-spn"></a>SPN (Nome da Entidade de Serviço)
O SPN é um identificador exclusivo para um serviço que usa a autenticação Kerberos. Será necessário certificar-se de que você tem um SPN HTTP apropriado presente para o servidor de relatório.

Para obter informações sobre como configurar o SPN (Nome da Entidade de Serviço) adequado para seu servidor de relatório, consulte [Registrar um SPN (Nome da Entidade de Serviço) para um servidor de relatório](https://msdn.microsoft.com/library/cc281382.aspx).

### <a name="enabling-negotiate-authentication"></a>Habilitando a autenticação do tipo negociar
Para habilitar um servidor de relatório para usar a autenticação Kerberos, será necessário configurar o tipo de autenticação do servidor de relatório para ser RSWindowsNegotiate. Isso é feito no arquivo rsreportserver.config.

```
<AuthenticationTypes>  
    <RSWindowsNegotiate />  
    <RSWindowsKerberos />  
    <RSWindowsNTLM />  
</AuthenticationTypes>
```

Para obter mais informações, consulte [Modify a Reporting Services Configuration File (Modificar um arquivo de configuração de serviços)](https://msdn.microsoft.com/library/bb630448.aspx) e [Configurar a Autenticação do Windows no servidor de relatório](https://msdn.microsoft.com/library/cc281253.aspx).

## <a name="active-directory-federation-services-adfs-configuration"></a>Configuração do Serviços de Federação do Active Directory (AD FS)
Será necessário configurar o AD FS em um servidor do Windows 2016 em seu ambiente. Isso pode ser feito por meio do Gerenciador do Servidor e selecionando Adicionar funções e Recursos em Gerenciar. Para obter mais informações, consulte [Serviços de Federação do Active Directory](https://technet.microsoft.com/windows-server-docs/identity/active-directory-federation-services).

### <a name="create-an-application-group"></a>Criar um grupo de aplicativos
Na tela Gerenciamento do AD FS, crie um grupo de aplicativos para o Reporting Services, que incluirá as informações dos aplicativos Power BI para Celulares.

É possível criar o grupo de aplicativos com as etapas a seguir.

1. Dentro do aplicativo de gerenciamento do AD FS, clique com botão direito do mouse em **Grupos de Aplicativos** e selecione **Adicionar Grupo de Aplicativos...**
   
   ![](media/mobile-oauth-ssrs/adfs-add-application-group.png)
2. No Assistente para Adicionar Grupo de Aplicativos, forneça um **nome** para o grupo de aplicativos e selecione **Aplicativo nativo acessando uma API Web**.
   
   ![](media/mobile-oauth-ssrs/adfs-application-group-wizard1.png)
3. Selecione **Avançar**.
4. Forneça um **nome** para o aplicativo que você está adicionando. 
5. Enquanto a **ID do cliente** estiver sendo automaticamente gerada para o seu, insira *484d54fc-b481-4eee-9505-0258a1913020* para iOS e Android.
6. Adicione as seguintes **URLs de redirecionamento**:
   
   **Entradas para o Power BI para Celulares – iOS:**  
   msauth://code/mspbi-adal://com.microsoft.powerbimobile  
   msauth://code/mspbi-adalms://com.microsoft.powerbimobilems  
   mspbi-adal://com.microsoft.powerbimobile  
   mspbi-adalms://com.microsoft.powerbimobilems
   
   **Os aplicativos Android só precisam do seguinte:**  
   urn:ietf:wg:oauth:2.0:oob
   
   ![](media/mobile-oauth-ssrs/adfs-application-group-wizard2.png)
7. Selecione **Avançar**.
8. Forneça a URL do seu Servidor de Relatório. Esta é a URL externa que atingirá o Proxy de aplicativo Web. Ela deve estar no formato a seguir.
   
   > [!NOTE]
   > Esta URL diferencia maiúsculas de minúsculas!
   > 
   > 
   
   *https://<url to report server>/reports*
   
   ![](media/mobile-oauth-ssrs/adfs-application-group-wizard3.png)
9. Selecione **Avançar**.
10. Escolha a **Política de Controle de Acesso** que atenda às necessidades da sua organização.
    
    ![](media/mobile-oauth-ssrs/adfs-application-group-wizard4.png)
11. Selecione **Avançar**.
12. Selecione **Avançar**.
13. Selecione **Avançar**.
14. Selecione **Fechar**.

Depois de concluir, você deverá ver que as propriedades do seu grupo de aplicativos são semelhantes ao seguinte.

![](media/mobile-oauth-ssrs/adfs-application-group.png)

## <a name="web-application-proxy-wap-configuration"></a>Configuração WAP (Proxy de aplicativo Web)
Habilite a função Proxy de aplicativo Web (função) Windows em um servidor no seu ambiente. Ele deve estar em um servidor Windows 2016. Para obter mais informações, consulte [Proxy de aplicativo Web no Windows Server 2016](https://technet.microsoft.com/windows-server-docs/identity/web-application-proxy/web-application-proxy-windows-server) e [Publicar aplicativos usando pré-autenticação do AD FS](https://technet.microsoft.com/windows-server-docs/identity/web-application-proxy/publishing-applications-using-ad-fs-preauthentication#a-namebkmk14apublish-an-application-that-uses-oauth2-such-as-a-windows-store-app).

### <a name="constrained-delegation-configuration"></a>Configuração de delegação restrita
Para fazer a transição da autenticação OAuth para a autenticação do Windows, é necessário usar a delegação restrita com transição de protocolos. Isso faz parte da configuração do Kerberos. Já definimos o SPN do Reporting Services na configuração do Reporting Services.

É necessário configurar a delegação restrita na conta do computador do servidor WAP dentro do Active Directory. Talvez seja necessário trabalhar com um administrador de domínio se você não tiver direitos no Active Directory.

Para configurar a delegação restrita, faça o seguinte.

1. Em um computador com as ferramentas do Active Directory instaladas, abra **Usuários e Computadores do Active Directory**.
2. Localize a conta do computador do servidor WAP. Por padrão, ela estará no contêiner de computadores.
3. Clique com botão direito do mouse no servidor WAP e acesse **Propriedades**.
4. Selecione a guia **Delegação**.
5. Selecione **Confiar no computador para delegação apenas a serviços especificados** e **Usar qualquer protocolo de autenticação**.
   
   ![](media/mobile-oauth-ssrs/wap-contrained-delegation1.png)
   
   Isso configura a delegação restrita para essa conta do computador do servidor WAP. Em seguida, é necessário especificar os serviços aos quais este computador tem permissão para delegar.
6. Selecione **Adicionar...** na caixa de serviços.
   
   ![](media/mobile-oauth-ssrs/wap-contrained-delegation2.png)
7. Selecione **Usuários ou Computadores...**
8. Insira a conta de serviço que você está usando para o Reporting Services. Esta é a conta que você adicionou o SPN para dentro da configuração do Reporting Services.
9. Selecione o SPN para o Reporting Services e selecione **OK**.
   
   > [!NOTE]
   > Você pode ver apenas o SPN NetBIOS. Na verdade, ele selecionará os SPNs NetBIOS e FQDN se ambos existirem.
   > 
   > 
   
   ![](media/mobile-oauth-ssrs/wap-contrained-delegation3.png)
10. O resultado deverá ser semelhante ao seguinte quando a caixa de seleção **Expandido** estiver marcada.
    
    ![](media/mobile-oauth-ssrs/wap-contrained-delegation4.png)
11. Selecione **OK**.

### <a name="add-wap-application"></a>Adicionar aplicativo WAP
Embora seja possível publicar aplicativos no Console de gerenciamento de acesso a relatórios, nós queremos criar o aplicativo por meio do PowerShell. Este é o comando para adicionar o aplicativo.

```
Add-WebApplicationProxyApplication -Name "Contoso Reports" -ExternalPreauthentication ADFS -ExternalUrl https://reports.contoso.com/reports/ -ExternalCertificateThumbprint "0ff79c75a725e6f67e3e2db55bdb103efc9acb12" -BackendServerUrl http://ContosoSSRS/reports/ -ADFSRelyingPartyName "Reporting Services - Web API" -BackendServerAuthenticationSPN "http/ContosoSSRS.contoso.com" -UseOAuthAuthentication
```

| Parâmetro | Comentários |
| --- | --- |
| **ADFSRelyingPartyName** |Esse é o nome da API Web criada como parte do grupo de aplicativos no AD FS. |
| **ExternalCertificateThumbprint** |Esse é o certificado a ser usado para os usuários externos. É importante que esse certificado seja válido em dispositivos móveis e que venha de uma autoridade de certificação confiável. |
| **BackendServerUrl** |Essa é a URL para o servidor de relatório do servidor WAP. Se o servidor WAP estiver em uma rede de perímetro talvez seja necessário usar um nome de domínio totalmente qualificado. Certificar-se de que você pode acessar essa URL no navegador da Web no servidor WAP. |
| **BackendServerAuthenticationSPN** |Esse é o SPN criado como parte da configuração do Reporting Services. |

### <a name="setting-integrated-authentication-for-the-wap-application"></a>Configurando a autenticação integrada do aplicativo WAP
Depois de adicionar o aplicativo WAP, será necessário definir BackendServerAuthenticationMode para usar IntegratedWindowsAuthentication. Para configurar isso, é necessária a ID do aplicativo WAP.

```
Get-WebApplicationProxyApplication “Contoso Reports” | fl
```

![](media/mobile-oauth-ssrs/wap-application-id.png)

Execute o seguinte comando para definir BackendServerAuthenticationMode usando a ID do aplicativo WAP.

```
Set-WebApplicationProxyApplication -id 30198C7F-DDE4-0D82-E654-D369A47B1EE5 -BackendServerAuthenticationMode IntegratedWindowsAuthentication
```

![](media/mobile-oauth-ssrs/wap-application-backendauth.png)

## <a name="connecting-with-the-power-bi-mobile-app"></a>Conectando-se ao aplicativo Power BI para Celulares
Dentro do aplicativo móvel do Power BI, conecte-se à sua instância do Reporting Services. Para fazer isso, forneça a **URL Externa** para seu aplicativo WAP.

![](media/mobile-oauth-ssrs/powerbi-mobile-app1.png)

Quando você seleciona **Conectar**, você será direcionado para a página de logon do AD FS. Insira credenciais válidas para seu domínio.

![](media/mobile-oauth-ssrs/powerbi-mobile-app2.png)

Depois de selecionar **Entrar**, você verá os elementos do seu servidor do Reporting Services.

![](media/mobile-oauth-ssrs/powerbi-mobile-app2.png)

## <a name="multi-factor-authentication"></a>Autenticação multifator
É possível habilitar a autenticação multifator para habilitar a segurança adicional do seu ambiente. Para saber mais, consulte [Configurar o AD FS 2016 e MFA Azure](https://technet.microsoft.com/windows-server-docs/identity/ad-fs/operations/configure-ad-fs-2016-and-azure-mfa).

## <a name="troubleshooting"></a>Solução de problemas
**Você recebe o erro Falha ao fazer logon no Servidor SSRS. Verifique a configuração do servidor.**

![](media/mobile-oauth-ssrs/powerbi-mobile-error.png)

É possível configurar o [Fiddler](http://www.telerik.com/fiddler) para funcionar como um proxy para seus dispositivos móveis para ver até onde a solicitação chegou. Para habilitar um proxy do Fiddler para seu dispositivo de telefone, será necessário configurar o [CertMaker para iOS e Android](http://www.telerik.com/fiddler/add-ons) no computador que estiver executando o Fiddler. Esse é um suplemento da Telerik para o Fiddler.

Se for possível entrar com êxito usando o Fiddler, talvez você tenha um problema de certificado com o aplicativo WAP ou com o servidor ADFS. É possível usar uma ferramenta como o [Microsoft Message Analyzer](https://www.microsoft.com/download/details.aspx?id=44226) para verificar se os certificados são válidos.

## <a name="next-steps"></a>Próximas etapas
[Registrar um SPN (Nome da Entidade de Serviço) para um servidor de relatório](https://msdn.microsoft.com/library/cc281382.aspx)  
[Como modificar um arquivo de configuração do Reporting Services](https://msdn.microsoft.com/library/bb630448.aspx)  
[Configurar a Autenticação do Windows no servidor de relatório](https://msdn.microsoft.com/library/cc281253.aspx)  
[Serviços de Federação do Active Directory](https://technet.microsoft.com/windows-server-docs/identity/active-directory-federation-services)  
[Proxy de aplicativo Web no Windows Server 2016](https://technet.microsoft.com/windows-server-docs/identity/web-application-proxy/web-application-proxy-windows-server)  
[Publicar aplicativos usando a pré-autenticação do AD FS](https://technet.microsoft.com/windows-server-docs/identity/web-application-proxy/publishing-applications-using-ad-fs-preauthentication#a-namebkmk14apublish-an-application-that-uses-oauth2-such-as-a-windows-store-app)  
[Configurar o AD FS 2016 e MFA Azure](https://technet.microsoft.com/windows-server-docs/identity/ad-fs/operations/configure-ad-fs-2016-and-azure-mfa)  
Mais perguntas? [Experimente a Comunidade do Power BI](http://community.powerbi.com/)

