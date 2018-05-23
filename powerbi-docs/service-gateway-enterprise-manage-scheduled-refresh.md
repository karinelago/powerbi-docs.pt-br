---
title: Gerenciar sua fonte de dados – Importar/Atualização Agendada
description: Como gerenciar o gateway de dados local e as fontes de dados que pertencem ao gateway. Este artigo é específico para fontes de dados que podem ser usadas com a atualização importada/agendada.
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-gateways
ms.topic: conceptual
ms.date: 12/06/2017
ms.author: mblythe
LocalizationGroup: Gateways
ms.openlocfilehash: 17c608b017123b5ae7111ef6d97703cdbc30940d
ms.sourcegitcommit: 638de55f996d177063561b36d95c8c71ea7af3ed
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/17/2018
---
# <a name="manage-your-data-source---importscheduled-refresh"></a>Gerenciar sua fonte de dados – Importar/Atualização Agendada
Depois de instalar o gateway de dados local, será necessário adicionar fontes de dados que podem ser usadas com o gateway. Este artigo examinará como trabalhar com os gateways e fontes de dados que são usadas para a atualização agendada em vez das conexões dinâmicas ou do DirectQuery.

## <a name="download-and-install-the-gateway"></a>Baixar e instalar o gateway
É possível baixar o gateway no serviço do Power BI. Selecione **Downloads** > **Gateway de Dados** ou vá para a [página de download do gateway](https://go.microsoft.com/fwlink/?LinkId=698861).

![](media/service-gateway-enterprise-manage-scheduled-refresh/powerbi-download-data-gateway.png)

## <a name="add-a-gateway"></a>Adicionar um gateway
Para adicionar um gateway, basta [baixar](https://go.microsoft.com/fwlink/?LinkId=698863) e instalar o gateway corporativo em um servidor de seu ambiente. Depois de instalar o gateway, ele será mostrado na lista de gateways em **Gerenciar gateways**.

> [!NOTE]
> **Gerenciar gateways** não será mostrado até que você seja o administrador de, pelo menos, um gateway. Isso pode acontecer ao ser adicionado como um administrador ou ao instalar e configurar um gateway.
> 
> 

## <a name="remove-a-gateway"></a>Excluir um gateway
A exclusão de um gateway também excluirá as fontes de dados contidas nele.  Isso também interromperá todos os painéis e relatórios que dependem dessas fontes de dados.

1. Selecione o ícone de engrenagem ![](media/service-gateway-enterprise-manage-scheduled-refresh/pbi_gearicon.png) no canto superior direito > **Gerenciar gateways**.
2. Gateway > **Remover**
   
   ![](media/service-gateway-enterprise-manage-scheduled-refresh/datasourcesettings7.png)

## <a name="add-a-data-source"></a>Adicionar uma fonte de dados
É possível adicionar uma fonte de dados selecionando um gateway e clicando em **Adicionar fonte de dados** ou acessando Gateway > **Adicionar fonte de dados**.

![](media/service-gateway-enterprise-manage-scheduled-refresh/datasourcesettings1.png)

Você pode selecionar o **Tipo de Fonte de Dados** na lista. Todas as fontes de dados relacionadas podem ser usadas para atualização agendada com o gateway corporativo. O Analysis Services, o SQL Server e o SAP HANA podem ser usados para a atualização agendada ou para o DirectQuery/conexões dinâmicas.

![](media/service-gateway-enterprise-manage-scheduled-refresh/datasourcesettings2.png)

Em seguida, é necessário preencher as informações sobre a fonte de dados, que inclui as informações de origem e as credenciais usadas para acessar a fonte de dados.

> [!NOTE]
> Todas as consultas à fonte de dados serão executadas com essas credenciais. Para obter mais informações, veja o artigo principal sobre o gateway de dados local para saber mais sobre como as [credenciais](service-gateway-onprem.md#credentials) são armazenadas.
> 
> 

![](media/service-gateway-enterprise-manage-scheduled-refresh/datasourcesettings3-oracle.png)

Você pode clicar em **Adicionar** depois preencher tudo.  Agora você pode usar esta fonte de dados para a atualização agendada com seus dados locais. Você verá *Conexão Bem-sucedida* , se tiver êxito.

![](media/service-gateway-enterprise-manage-scheduled-refresh/datasourcesettings4.png)

<!-- Shared Install steps Include -->
[!INCLUDE [gateway-onprem-datasources-include](./includes/gateway-onprem-datasources-include.md)]

### <a name="advanced-settings"></a>Configurações avançadas
Você pode configurar o nível de privacidade para sua fonte de dados. Ele controla como os dados podem ser combinados. É usado somente para a atualização agendada. [Saiba mais](https://support.office.com/article/Privacy-levels-Power-Query-CC3EDE4D-359E-4B28-BC72-9BEE7900B540)

![](media/service-gateway-enterprise-manage-scheduled-refresh/datasourcesettings9.png)

## <a name="remove-a-data-source"></a>Remover uma fonte de dados
A remoção de uma fonte de dados interromperá todos os painéis ou relatórios que dependem da fonte de dados em questão.  

Para remover uma Fonte de Dados, vá para a Fonte de Dados > **Remover**.

![](media/service-gateway-enterprise-manage-scheduled-refresh/datasourcesettings6.png)

## <a name="manage-administrators"></a>Gerenciar administradores
Na guia Administradores, para o gateway, você pode adicionar e remover os usuários que podem administrar o gateway. Você pode adicionar usuários apenas neste momento. Não é possível adicionar grupos de segurança.

![](media/service-gateway-enterprise-manage-scheduled-refresh/datasourcesettings8.png)

## <a name="manage-users"></a>Gerenciar usuários
Na guia Usuários, da fonte de dados, você pode adicionar e remover os usuários ou grupos de segurança que podem usar essa fonte de dados.

> [!NOTE]
> A lista de usuários só controla quem tem permissão de publicar relatórios. Os proprietários de relatório podem criar painéis ou pacotes de conteúdo e compartilhá-los com outros usuários.
> 
> 

![](media/service-gateway-enterprise-manage-scheduled-refresh/datasourcesettings5.png)

## <a name="using-the-data-source-for-scheduled-refresh"></a>Usando a fonte de dados para a atualização agendada
Depois de criar a fonte de dados, ela estará disponível para uso com as conexões do DirectQuery ou por meio da atualização agendada.

> [!NOTE]
> Os nomes do servidor e do banco de dados devem corresponder entre o Power BI Desktop e a fonte de dados no gateway de dados local!
> 
> 

O vínculo entre o conjunto de dados e a fonte de dados no gateway baseia-se nos nomes do servidor e do banco de dados. Eles devem corresponder. Por exemplo, se você fornecer um Endereço IP para o nome do servidor, no Power BI Desktop, será necessário usar o Endereço IP para a fonte de dados na configuração do gateway. Se você usar *SERVIDOR\INSTÂNCIA*, no Power BI Desktop, precisará usar o mesmo na fonte de dados configurada para o gateway.

Se você estiver listado na guia **Usuários** da fonte de dados configurada no gateway e houver a correspondência entre os nomes do servidor e do banco de dados, você verá o gateway como uma opção a ser usada com a atualização agendada.

![](media/service-gateway-enterprise-manage-scheduled-refresh/powerbi-gateway-enterprise-schedule-refresh.png)

> [!WARNING]
> Se seu conjunto de dados contiver várias fontes de dados, cada uma delas deverá ser adicionada dentro do gateway. Se uma ou mais fontes de dados não forem adicionadas ao gateway, você não o verá como disponível para a atualização agendada.
> 
> 

## <a name="limitations"></a>Limitações
* O OAuth não é um esquema de autenticação compatível com o gateway de dados local. Você não pode adicionar fontes de dados que exigem o OAuth. Se seu conjunto de dados tiver uma fonte de dados que exija o OAuth, você não poderá usar o gateway para a atualização agendada.

## <a name="next-steps"></a>Próximas etapas
[Gateway de dados local](service-gateway-onprem.md)  
[Detalhes sobre o gateway de dados local](service-gateway-onprem-indepth.md)  
[Solução de problemas do gateway de dados local](service-gateway-onprem-tshoot.md)  
Mais perguntas? [Experimente a Comunidade do Power BI](http://community.powerbi.com/)

