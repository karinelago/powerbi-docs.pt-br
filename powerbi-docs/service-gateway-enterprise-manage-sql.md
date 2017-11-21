---
title: "Gerenciar sua fonte de dados –SQL"
description: Como gerenciar o gateway de dados local e as fontes de dados que pertencem ao gateway.
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
ms.date: 11/02/2017
ms.author: davidi
ms.openlocfilehash: 644078dc61a69cf27cb93b29409546d61e1706f2
ms.sourcegitcommit: 284b09d579d601e754a05fba2a4025723724f8eb
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/15/2017
---
# <a name="manage-your-data-source---sql-server"></a>Gerenciar sua fonte de dados – SQL Server
Depois de instalar o Gateway de dados local, é necessário adicionar fontes de dados que possam ser usadas com o gateway. Este artigo abordará como trabalhar com gateways e fontes de dados. Você pode usar a fonte de dados do SQL Server para a atualização agendada ou para o DirectQuery.

## <a name="download-and-install-the-gateway"></a>Baixar e instalar o gateway
É possível baixar o gateway no serviço do Power BI. Selecione **Downloads** > **Gateway de Dados** ou vá para a [página de download do gateway](https://go.microsoft.com/fwlink/?LinkId=698861).

![](media/service-gateway-enterprise-manage-sql/powerbi-download-data-gateway.png)

## <a name="add-a-gateway"></a>Adicionar um gateway
Para adicionar um Gateway, basta [baixar](https://go.microsoft.com/fwlink/?LinkId=698861) e instalar o gateway em um servidor de seu ambiente. Depois de instalar o gateway, ele será mostrado na lista de gateways em **Gerenciar gateways**.

> [!NOTE]
> **Gerenciar gateways** não será mostrado até que você seja o administrador de, pelo menos, um gateway. Isso ocorre quando você é adicionado como administrador a um gateway ou a instalação e configuração de um gateway é feita por você mesmo.
> 
> 

## <a name="remove-a-gateway"></a>Excluir um gateway
A exclusão de um gateway também excluirá as fontes de dados contidas nele.  Isso também interromperá todos os painéis e relatórios que dependem dessas fontes de dados.

1. Selecione o ícone de engrenagem ![](media/service-gateway-enterprise-manage-sql/pbi_gearicon.png) no canto superior direito > **Gerenciar gateways**.
2. Gateway > **Remover**
   
   ![](media/service-gateway-enterprise-manage-sql/datasourcesettings7.png)

## <a name="add-a-data-source"></a>Adicionar uma fonte de dados
É possível adicionar uma fonte de dados selecionando um gateway e clicando em **Adicionar fonte de dados** ou acessando Gateway > **Adicionar fonte de dados**.

![](media/service-gateway-enterprise-manage-sql/datasourcesettings1.png)

Você pode selecionar o **Tipo de Fonte de Dados** na lista.

![](media/service-gateway-enterprise-manage-sql/datasourcesettings2.png)

> [!NOTE]
> Ao usar o DirectQuery, o gateway só é compatível com o **SQL Server 2012 SP1** e versões subsequentes.
> 
> 

Em seguida, é necessário preencher as informações sobre a fonte de dados, que incluem o **Servidor** e o **Banco de Dados**.  

Também é necessário escolher um **Método de Autenticação**.  Ele pode ser **Windows** ou **Básico**.  Convém escolher **Básico** se você pretende usar a Autenticação do SQL em vez da Autenticação do Windows. Em seguida, insira as credenciais que serão usadas para esta fonte de dados.

> [!NOTE]
> Todas as consultas à fonte de dados serão executadas com essas credenciais, a menos que o SSO (logon único) do Kerberos esteja configurado e habilitado para a fonte de dados. Com SSO, conjuntos de dados de importação usam as credenciais armazenadas, mas conjuntos de dados de DirectQuery usam o usuário atual do Power BI para executar consultas usando o SSO. Para obter mais informações, consulte o artigo de gateway de dados local principal para saber mais sobre como as [credenciais](service-gateway-onprem.md#credentials) são armazenadas, ou o artigo sobre como [usar o Kerberos para SSO (logon único) do Power BI para fontes de dados locais](service-gateway-kerberos-for-sso-pbi-to-on-premises-data.md).
> 
> 

![](media/service-gateway-enterprise-manage-sql/datasourcesettings3.png)

Você pode clicar em **Adicionar** depois preencher tudo.  Agora você pode usar esta fonte de dados para atualização agendada, ou para o DirectQuery, em um SQL Server local. Você verá *Conexão Bem-sucedida* se tiver êxito.

![](media/service-gateway-enterprise-manage-sql/datasourcesettings4.png)

### <a name="advanced-settings"></a>Configurações avançadas
Você pode configurar o nível de privacidade para sua fonte de dados. Ele controla como os dados podem ser combinados. É usado somente para a atualização agendada. Não se aplica ao DirectQuery. [Saiba mais](https://support.office.com/article/Privacy-levels-Power-Query-CC3EDE4D-359E-4B28-BC72-9BEE7900B540)

![](media/service-gateway-enterprise-manage-sql/datasourcesettings9.png)

## <a name="remove-a-data-source"></a>Remover uma fonte de dados
A remoção de uma fonte de dados interromperá todos os painéis ou relatórios que dependem da fonte de dados em questão.  

Para remover uma Fonte de Dados, vá para a Fonte de Dados > **Remover**.

![](media/service-gateway-enterprise-manage-sql/datasourcesettings6.png)

## <a name="manage-administrators"></a>Gerenciar administradores
Na guia Administradores, para o gateway, você pode adicionar e remover os usuários (ou grupos de segurança) que podem administrar o gateway.

![](media/service-gateway-enterprise-manage-sql/datasourcesettings8.png)

## <a name="manage-users"></a>Gerenciar usuários
Na guia Usuários, da fonte de dados, você pode adicionar e remover os usuários ou grupos de segurança que podem usar essa fonte de dados.

> [!NOTE]
> A lista de usuários só controla quem tem permissão de publicar relatórios. Os proprietários de relatório podem criar painéis ou pacotes de conteúdo e compartilhá-los com outros usuários.
> 
> 

![](media/service-gateway-enterprise-manage-sql/datasourcesettings5.png)

## <a name="using-the-data-source"></a>Usando a fonte de dados
Depois de criar a fonte de dados, ela estará disponível para uso com as conexões do DirectQuery ou por meio da atualização agendada.

> [!NOTE]
> O nome do servidor e do banco de dados deve corresponder entre o Power BI Desktop e a fonte de dados no gateway de dados local!
> 
> 

O vínculo entre o conjunto de dados e a fonte de dados no gateway baseia-se nos nomes do servidor e do banco de dados. Eles devem corresponder. Por exemplo, se você fornecer um Endereço IP como nome do servidor no **Power BI Desktop** terá de usar o Endereço IP como fonte de dados na configuração do gateway. Se você usar *SERVIDOR\INSTÂNCIA*, no Power BI Desktop, precisará usar o mesmo na fonte de dados configurada para o gateway.

Isso acontece para o DirectQuery e a atualização agendada.

### <a name="using-the-data-source-with-directquery-connections"></a>Usando a fonte de dados com conexões do DirectQuery
Verifique se os nomes do servidor e do banco de dados correspondem entre o **Power BI Desktop** e a fonte de dados configurada para o gateway. Você também precisará certificar-se de que o usuário está listado na guia **Usuários** da fonte de dados para publicar os conjuntos de dados do DirectQuery. A seleção, para o DirectQuery, ocorre no Power BI Desktop quando você importa dados pela primeira vez. [Saiba mais](desktop-use-directquery.md)

Após a publicação, por meio do Power BI Desktop ou do recurso **Obter Dados**, seus relatórios deverão começar a funcionar. Pode levar vários minutos, após a criação da fonte de dados no gateway, para que a conexão seja utilizável.

### <a name="using-the-data-source-with-scheduled-refresh"></a>Usando a fonte de dados com a atualização agendada
Se você estiver listado na guia **Usuários** da fonte de dados configurada no gateway e houver a correspondência entre os nomes do servidor e do banco de dados, você verá o gateway como uma opção a ser usada com a atualização agendada.

![](media/service-gateway-enterprise-manage-sql/powerbi-gateway-enterprise-schedule-refresh.png)

## <a name="next-steps"></a>Próximas etapas
* [Gateway de dados local](service-gateway-onprem.md)  
* [Detalhes sobre o Gateway de dados local](service-gateway-onprem-indepth.md)  
* [Solução de problemas do Gateway de dados local](service-gateway-onprem-tshoot.md)
* [Use o Kerberos para SSO (logon único) do Power BI para fontes de dados locais](service-gateway-kerberos-for-sso-pbi-to-on-premises-data.md). 
* Mais perguntas? [Experimente a Comunidade do Power BI](http://community.powerbi.com/)

