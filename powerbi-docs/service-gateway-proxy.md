---
title: "Definindo as configurações de proxy do Gateway de Dados Local"
description: "Informações sobre a definição das configurações de proxy do gateway de dados local."
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
ms.tgt_pltfrm: na
ms.workload: powerbi
ms.date: 09/06/2017
ms.author: davidi
ms.openlocfilehash: 6fb6250f8cd82c7057abe3f9cf9792dc733ea4b6
ms.sourcegitcommit: 284b09d579d601e754a05fba2a4025723724f8eb
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/15/2017
---
# <a name="configuring-proxy-settings-for-the-on-premises-data-gateway"></a>Definindo as configurações de proxy do Gateway de Dados Local
Seu ambiente de trabalho poderá exigir que você passe por um proxy para acessar a Internet. Isso pode impedir que o Gateway de Dados Local se conecte ao serviço.

## <a name="does-your-network-use-a-proxy"></a>Sua rede usa um proxy?
A seguinte postagem no superuser.com discute como você pode tentar determinar se tem um proxy na rede.

[Como saber qual servidor proxy estou usando? (SuperUser.com)](https://superuser.com/questions/346372/how-do-i-know-what-proxy-server-im-using)

## <a name="configuration-file-location-and-default-configuration"></a>Local do arquivo de configuração e configuração padrão
As informações de proxy são configuradas em um arquivo de configuração do .NET. O local e os nomes de arquivo serão diferentes, dependendo do gateway usado.

### <a name="on-premises-data-gateway"></a>Gateway de dados local
Existem dois arquivos de configuração principais que se relacionam ao gateway de dados local.

**Configuração**

O primeiro refere-se às telas de configuração que, na verdade, configuram o gateway. Se estiver tendo problemas para configurar o gateway, este é o arquivo que você desejará examinar.

    C:\Program Files\On-premises data gateway\enterprisegatewayconfigurator.exe.config

**Serviço Windows**

O segundo refere-se ao serviço Windows real que interage com o serviço do Power BI e manipula as solicitações.

    C:\Program Files\On-premises data gateway\Microsoft.PowerBI.EnterpriseGateway.exe.config

### <a name="power-bi-gateway---personal"></a>Gateway do Power BI - Pessoal
> [!NOTE]
> Há uma nova versão de gateway pessoal para o Power BI, denominada **Gateway de dados local (modo pessoal)**. Esta seção deste artigo descreve a versão anterior do gateway pessoal, chamada **Power BI Gateway – Personal**, que será desativada e deixará de funcionar após 31 de julho de 2017. Para obter informações sobre a nova versão do gateway pessoal, incluindo como instalá-la, consulte o artigo [**Gateway de dados local (modo pessoal)**](service-gateway-personal-mode.md).
> 
> 

O gateway pessoal pode ser instalado de uma das duas maneiras. Como um serviço Windows (administrador) ou como um aplicativo de modo de usuário. Isso é determinado durante a instalação. Como resultado, seus arquivos de configuração podem estar em um dos dois locais, dependendo de como o gateway foi instalado. Convém verificar os dois locais.

**Configuração**

O primeiro refere-se às telas de configuração que, na verdade, configuram o gateway. Se estiver tendo problemas para configurar o gateway, este é o arquivo que você desejará examinar.

Para o *serviço Windows*, ele será o seguinte:

    C:\Program Files\Power BI Personal Gateway\1.0\Configurator\GWConfig.exe.config
    C:\Program Files\Power BI Personal Gateway\1.0\Configurator\PowerBIGatewayAgentCmdLine.exe.config

Para o *aplicativo de modo de usuário*, ele será o seguinte:

    C:\Users\<user>\AppData\Local\Power BI Gateway - Personal \1.0\Configurator\GWConfig.exe.config
    C:\Users\<user>\AppData\Local\Power BI Gateway - Personal \1.0\Configurator\PowerBIGatewayAgentCmdLine.exe.config

**Serviço Windows**

O segundo refere-se ao serviço Windows real que interage com o serviço do Power BI e manipula as solicitações.

Para o *serviço Windows*, ele será o seguinte:

    C:\Program Files\Power BI Personal Gateway\1.0\Gateway\diawp.exe.config

Para o *aplicativo de modo de usuário*, ele será o seguinte:

    C:\Users\<user>\AppData\Local\Power BI Gateway - Personal \1.0\Gateway\diawp.exe.config

## <a name="configuring-proxy-settings"></a>Definindo as configurações de proxy
A configuração de proxy padrão é a seguinte:

    <system.net>
        <defaultProxy useDefaultCredentials="true" />
    </system.net>

A configuração padrão funciona com a autenticação do Windows. Se o proxy usar outra forma de autenticação, você precisará alterar as configurações. Se você não tiver certeza, entre em contato com o administrador da rede.

Para saber mais sobre a configuração dos elementos de proxy para os arquivos de configuração do .NET, veja [Elemento defaultProxy (Configurações de Rede)](https://msdn.microsoft.com/library/kd3cf2ex.aspx)

## <a name="changing-the-gateway-service-account-to-a-domain-user"></a>Alterando a conta de serviço do gateway para um usuário de domínio
Ao definir as configurações de proxy para usar credenciais padrão, conforme explicado acima, você pode ter problemas de autenticação com o proxy. Isso ocorre porque a conta de serviço padrão é o SID de Serviço, não um usuário de domínio autenticado. É possível alterar a conta de serviço do gateway para permitir a autenticação adequada com o proxy.

> [!NOTE]
> É recomendável que você use uma conta de serviço gerenciado para evitar a redefinição de senhas. Saiba como criar uma [conta de serviço gerenciado](https://technet.microsoft.com/library/dd548356.aspx) dentro do Active Directory.
> 
> 

### <a name="change-the-on-premises-data-gateway-service-account"></a>Alterar a conta de serviço do Gateway de Dados Local
1. Altere a conta do serviço Windows para o **serviço do Gateway de Dados Local**.
   
    A conta padrão para esse serviço é *NT SERVICE\PBIEgwService*. Altere-a para uma conta de usuário do domínio dentro do seu domínio do Active Directory. Ou utilize uma conta de serviço gerenciado para evitar a necessidade de modificar a senha.
   
    Altere a conta na guia **Fazer Logon** dentro das propriedades do serviço Windows.
2. Reinicie o **serviço do Gateway de Dados Local**.
   
    Em um prompt de comando do administrador, execute os comandos a seguir.
   
        net stop PBIEgwService
   
        net start PBIEgwService
3. Inicie o **configurador do Gateway de Dados Local**. É possível selecionar o botão Iniciar do Windows e procurar o *Gateway de Dados Local*.
4. Entre no Power BI.
5. Restaure o gateway usando sua chave de recuperação.
   
    Isso permitirá que a nova conta de serviço consiga descriptografar as credenciais armazenadas para fontes de dados.

## <a name="next-steps"></a>Próximas etapas
[Gateway de dados local (modo pessoal)](service-gateway-personal-mode.md)
[Informações sobre firewall](service-gateway-onprem-tshoot.md#firewall-or-proxy)  
Mais perguntas? [Experimente a Comunidade do Power BI](http://community.powerbi.com/)

