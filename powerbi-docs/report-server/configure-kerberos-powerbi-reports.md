---
title: Configurar o Kerberos para usar relatórios do Power BI
description: Saiba como configurar seu servidor de relatório para a autenticação Kerberos para fontes de dados usadas em relatórios do Power BI para um ambiente distribuído.
services: powerbi
documentationcenter: ''
author: markingmyname
manager: kfile
backup: ''
editor: ''
tags: ''
qualityfocus: no
qualitydate: ''
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 11/01/2017
ms.author: maghan
ms.openlocfilehash: 8a99f4d07b17ae1a8d260c1655dfbb948f76c317
ms.sourcegitcommit: 493f160d04ed411ff4741c599adc63ba1f65230f
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/07/2018
---
# <a name="configure-kerberos-to-use-power-bi-reports"></a>Configurar o Kerberos para usar relatórios do Power BI
<iframe width="640" height="360" src="https://www.youtube.com/embed/vCH8Fa3OpQ0?showinfo=0" frameborder="0" allowfullscreen></iframe>

Saiba como configurar seu servidor de relatório para a autenticação Kerberos para fontes de dados usadas em relatórios do Power BI para um ambiente distribuído.

O Servidor de Relatório do Power BI inclui a capacidade de hospedar relatórios do Power BI. Várias fontes de dados são compatíveis com o servidor de relatório. Embora este artigo concentre-se especificamente no SQL Server Analysis Services, você pode usar os conceitos e aplicá-los a outras fontes de dados, como o SQL Server.

É possível instalar o Servidor de Relatório do Power BI, SQL Server e o Analysis Services em um único computador e tudo deve funcionar sem configuração adicional. Isso é ótimo para um ambiente de teste. Talvez ocorram erros se esses serviços estiverem instalados em computadores separados, o que é chamado ambiente distribuído. Nesse ambiente, é necessário usar a autenticação Kerberos. Há uma configuração necessária para implementar isso. 

Especificamente, será necessário configurar a delegação restrita. O Kerberos pode estar configurado em seu ambiente, mas ele não pode ser configurado para a delegação restrita.

## <a name="error-running-report"></a>Erro ao executar o relatório
Se seu servidor de relatório não estiver configurado corretamente, você receberá o seguinte erro.

    Something went wrong.

    We couldn’t run the report because we couldn’t connect to its data source. The report or data source might not be configured correctly. 

Nos detalhes técnicos, você verá a seguinte mensagem.

    We couldn’t connect to the Analysis Services server. The server forcibly closed the connection. To connect as the user viewing the report, your organization must have configured Kerberos constrained delegation.

![](media/configure-kerberos-powerbi-reports/powerbi-report-config-error.png)

## <a name="configuring-kerberos-constrained-delegation"></a>Configurando a delegação restrita de Kerberos
Há vários itens que precisam ser configurados para que a delegação restrita de Kerberos funcione. Isso inclui o SPN (Nomes de Entidade de Serviço) e configurações de delegação em contas de serviço.

> [!NOTE]
> Para definir configurar SPNs e definir configurações de delegação, é necessário ser um administrador de domínio.
> 
> 

Será necessário configurar ou validar o seguinte.

1. Tipo de autenticação na configuração do Servidor de Relatório.
2. SPNs para a conta de serviço do servidor de relatório.
3. SPNs para o serviço do Analysis Services.
4. SPNs para o serviço do SQL Browser no computador do Analysis Services. Isso é apenas para instâncias nomeadas.
5. Configurações de delegação na conta de serviço do servidor de relatório.

## <a name="authentication-type-within-report-server-configuration"></a>Tipo de autenticação na configuração do Servidor de Relatório
É necessário configurar o tipo de autenticação para que o servidor de relatório possibilite a delegação restrita de Kerberos. Isso é feito dentro do arquivo **rsreportserver.config**. O local padrão desse arquivo é `C:\Program Files\Microsoft Power BI Report Server\PBIRS\ReportServer`.

No arquivo rsreportserver.config, você encontrará a seção **Authentication/AuthenticationTypes**.

Queremos garantir que o RSWindowsNegotiate esteja listado e seja o primeiro na lista de tipos de autenticação. Ela deve ser semelhante à seguinte.

```
<AuthenticationTypes>
    <RSWindowsNegotiate/>
    <RSWindowsNTLM/>
</AuthenticationTypes>
```

Se fosse necessário alterar o arquivo de configuração, você teria que parar e iniciar o servidor de relatório para garantir que as alterações entrem em vigor.

Para obter mais informações, consulte [Configurar a Autenticação do Windows no servidor de relatório](https://docs.microsoft.com/sql/reporting-services/security/configure-windows-authentication-on-the-report-server).

## <a name="spns-for-the-report-server-service-account"></a>SPNs para a conta de serviço do servidor de relatório
Em seguida, é necessário garantir que o servidor de relatório tenha SPNs válidos disponíveis. Isso se baseia na conta de serviço configurada para o servidor de relatório.

### <a name="virtual-service-account-or-network-service"></a>Conta de serviço virtual ou de Serviço de Rede
Se seu servidor de relatório estiver configurado para a conta Serviço de Rede ou Conta de Serviço Virtual, você não deverá fazer nada. Elas estão no contexto da conta de computador. A conta de computador terá SPNs HOST por padrão. Elas abordarão o serviço HTTP e serão usadas pelo servidor de relatório.

Se você estiver usando um nome do servidor virtual, que não seja o mesmo que a conta de computador, as entradas HOST não abrangerão você e será necessário adicionar manualmente os SPNs para o nome de host do servidor virtual.

### <a name="domain-user-account"></a>Conta de usuário de domínio
Se seu servidor de relatório estiver configurado para usar uma conta de usuário de domínio, será necessário criar manualmente os SPNs HTTP nessa conta. Isso pode ser feito usando a ferramenta setspn que vem com o Windows.

> [!NOTE]
> Será necessário ter direitos de administrador de domínio para criar o SPN.
> 
> 

É recomendável criar dois SPNs. Um com o nome NetBIOS e outro com o FQDN (nome de domínio totalmente qualificado). O SPN deve estar no seguinte formato.

    <Service>/<Host>:<port>

O Servidor de Relatório do Power BI usará um Serviço de HTTP. Para SPNs HTTP, você não listará uma porta. O serviço que estamos interessados aqui é HTTP. O host do SPN será o nome usado em uma URL. Normalmente, esse é o nome do computador. Se você estiver atrás de um balanceador de carga, isso pode ser um nome virtual.

> [!NOTE]
> É possível verificar a URL examinando o que você digitar na barra de endereços do navegador ou é possível procurar no Gerenciador de Configurações do Servidor de Relatório na guia URL do Portal da Web.
> 
> 

Se o nome do computador for ContosoRS, seus SPNs serão o seguinte.

| Tipo de SPN | SPN |
| --- | --- |
| FQDN (nome de domínio totalmente qualificado) |HTTP/ContosoRS.contoso.com |
| NetBIOS |HTTP/ContosoRS |

### <a name="location-of-spn"></a>Local do SPN
Então, onde colocar o SPN? O SPN será colocado no que você estiver usando para sua conta de serviço. Se você estiver usando a Conta de Serviço Virtual ou o Serviço de Rede, isso será a conta do computador. No entanto, mencionamos antes que você só deve fazer isso para uma URL virtual. Se você estiver usando um usuário de domínio para a conta de serviço do servidor de relatório, coloque o SPN nessa conta de usuário de domínio.

Por exemplo, se estivermos usando a conta de Serviço de Rede e o nome do computador for ContosoRS, colocaremos o SPN em ContosoRS.

Se estivermos utilizando uma conta de usuário de domínio de RSService, colocaremos o SPN em RSService.

### <a name="using-setspn-to-add-the-spn"></a>Usando o SetSPN para adicionar o SPN
Podemos usar a ferramenta SetSPN para adicionar o SPN. Vamos seguir o mesmo exemplo que o de cima com a conta do computador e a conta de usuário de domínio.

Colocar o SPN em uma conta de computador para o SPN FQDN e NetBIOS seria semelhante ao seguinte se estivéssemos usando uma URL virtual de contosoreports.

      Setspn -a HTTP/contosoreports.contoso.com ContosoRS
      Setspn -a HTTP/contosoreports ContosoRS

Colocar o SPN em uma conta de usuário de domínio, para o SPN FQDN e NetBIOS, seria semelhante ao seguinte se estivéssemos usando um nome de computador para o host do SPN.

      Setspn -a HTTP/ContosoRS.contoso.com RSService
      Setspn -a HTTP/ContosoRS RSService

## <a name="spns-for-the-analysis-services-service"></a>SPNs para o serviço do Analysis Services
Os SPNs do Analysis Services são semelhantes ao que fizemos com o Servidor de Relatório do Power BI. O formato do SPN será um pouco diferente se você tiver uma instância nomeada.

Para o Analysis Services, podemos usar um serviço de MSOLAPSvc.3. Especificaremos o nome de instância do local da porta no SPN. A parte de host do SPN será o nome do computador ou o nome virtual do Cluster.

Um exemplo de um SPN do Analysis Services teria a seguinte aparência.

| Type | Format |
| --- | --- |
| Instância padrão |MSOLAPSvc.3/ContosoAS.contoso.com<br>MSOLAPSvc.3/ContosoAS |
| Instância nomeada |MSOLAPSvc.3/ContosoAS.contoso.com:INSTANCENAME<br>MSOLAPSvc.3/ContosoAS:INSTANCENAME |

A colocação do SPN também é semelhante ao que foi mencionado com o Servidor de Relatório do Power BI. Ele se baseia na conta de serviço.  Se você estiver usando o Sistema Local ou o Serviço de Rede, você estará no contexto da conta de computador. Se você estiver usando uma conta de usuário de domínio para a instância do Analysis Services, coloque o SPN na conta de usuário de domínio.

### <a name="using-setspn-to-add-the-spn"></a>Usando o SetSPN para adicionar o SPN
Podemos usar a ferramenta SetSPN para adicionar o SPN. Nesse exemplo, o nome do computador será ContosoAS.

Colocar o SPN em uma conta de computador para o SPN FQDN e NetBIOS seria semelhante ao seguinte.

    Setspn -a MSOLAPSvc.3/ContosoAS.contoso.com ContosoAS
    Setspn -a MSOLAPSvc.3/ContosoAS ContosoAS

Colocar o SPN em uma conta de usuário de domínio, para o SPN FQDN e NetBIOS, seria semelhante ao seguinte.

    Setspn -a MSOLAPSvc.3/ContosoAS.contoso.com OLAPService
    Setspn -a MSOLAPSvc.3/ContosoAS OLAPService

## <a name="spns-for-the-sql-browser-service"></a>SPNs para o serviço SQL Browser
Se você tiver uma instância nomeada do Analysis Services, também será necessário certificar-se de que você tem um SPN para o serviço de navegador. Isso é exclusivo do Analysis Services.

Os SPNs do SQL Browser são semelhantes ao que fizemos com o Servidor de Relatório do Power BI.

Para o SQL Browser, usamos um serviço de MSOLAPDisco.3. Especificaremos o nome de instância do local da porta no SPN. A parte de host do SPN será o nome do computador ou o nome virtual do Cluster.
Não é necessário especificar nada para a porta ou o nome da instância.

Um exemplo de um SPN do Analysis Services teria a seguinte aparência.

    MSOLAPDisco.3/ContosoAS.contoso.com
    MSOLAPDisco.3/ContosoAS

A colocação do SPN também é semelhante ao que foi mencionado com o Servidor de Relatório do Power BI. A diferença é que o SQL Browser sempre é executado na conta do Sistema Local. Isso significa que os SPNs sempre vão na conta do computador. 

### <a name="using-setspn-to-add-the-spn"></a>Usando o SetSPN para adicionar o SPN
Podemos usar a ferramenta SetSPN para adicionar o SPN. Nesse exemplo, o nome do computador será ContosoAS.

Colocar o SPN na conta de computador para o SPN FQDN e NetBIOS seria semelhante ao seguinte.

    Setspn -a MSOLAPDisco.3/ContosoAS.contoso.com ContosoAS
    Setspn -a MSOLAPDisco.3/ContosoAS ContosoAS

Para obter mais informações, consulte [Um SPN do serviço SQL Server Browser é necessário](https://support.microsoft.com/kb/950599).

## <a name="delegation-settings-on-the-report-server-service-account"></a>Configurações de delegação na conta de serviço do servidor de relatório
A última parte que precisamos configurar são as configurações de delegação da conta de serviço do servidor de relatório. Há diferentes ferramentas que podem ser usadas para seguir essas etapas. Para os fins deste documento, continuaremos com os Usuários e Computadores do Active Directory.

Será necessário iniciar indo para as propriedades de conta de serviço do servidor de relatório nos Usuários e Computadores do Active Directory. Essa será a conta do computador, se você usou a Conta de Serviço Virtual ou o Serviço de Rede ou será uma conta de usuário de domínio.

Configure a delegação restrita com o trânsito de protocolos. Com a delegação restrita, é necessário ser explícito com relação a quais serviços queremos delegar. Adicionaremos o SPN de serviço do Analysis Services e o SPN do SQL Browser à lista à qual o Servidor de Relatório do Power BI pode delegar.

1. Clique com o botão direito do mouse na conta de serviço do servidor de relatório e selecione **Propriedades**.
2. Selecione a guia **Delegação**.
3. Selecione **Confiar no computador para delegação apenas a serviços especificados**.
4. Selecione **Usar qualquer protocolo de autenticação**.
5. Nos **Serviços aos quais esta conta pode apresentar credenciais delegadas**: selecione **Adicionar**.
6. Na caixa de diálogo, selecione **Usuários ou computadores**.
7. Insira a conta de serviço para o serviço do Analysis Services e selecione **Ok**.
8. Selecione o SPN criado. Ele começará com `MSOLAPSvc.3`. Se você adicionou o FQDN e o SPN NetBIOS, ele selecionará ambos. Você pode ver apenas um.
9. Selecione **OK**.  Agora você verá o SPN na lista.
10. Ou é possível selecionar **Expandido** para mostrar o SPN FQDN e NetBIOS na lista.
11. Selecione **Adicionar** novamente. Agora, adicionaremos o SPN do SQL Browser.
12. Na caixa de diálogo, selecione **Usuários ou computadores**.
13. Insira o nome do computador para o computador no qual o serviço SQL Browser está e selecione **Ok**.
14. Selecione o SPN criado. Ele começará com `MSOLAPDisco.3`. Se você adicionou o FQDN e o SPN NetBIOS, ele selecionará ambos. Você pode ver apenas um.
15. Selecione **OK**. A caixa de diálogo deverá ter aparência semelhante à seguinte, se você tiver marcado **Expandido**.
    
    ![](media/configure-kerberos-powerbi-reports/powerbi-report-config-delegation.png)
16. Selecione **OK**.
17. Reinicializar o Servidor de Relatório do Power BI.

## <a name="running-a-power-bi-report"></a>Executando um Relatório do Power BI
Depois que todas as configurações acima estiverem em vigor, o relatório deverá ser exibido corretamente. 

![](media/configure-kerberos-powerbi-reports/powerbi-report.png)

Embora essa configuração deva funcionar na maioria dos casos, com Kerberos, pode haver configurações diferentes dependendo do seu ambiente. Se o relatório ainda não for carregado, contate o suporte ou o seu administrador de domínio para investigar mais.

## <a name="next-steps"></a>Próximas etapas
[Manual do administrador](admin-handbook-overview.md)  
[Instalar o Servidor de Relatório do Power BI](install-report-server.md)  

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)

