---
title: "Gerenciar sua fonte de dados – Analysis Services"
description: "Como gerenciar o gateway de dados local e as fontes de dados que pertencem ao gateway. Isso é para o Analysis Services em ambos o modo de Tabela e o Multidimensional."
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
ms.date: 01/24/2018
ms.author: davidi
ms.openlocfilehash: 72445988ff4080b7c24f09f797f2038b957631ef
ms.sourcegitcommit: db37f5cef31808e7882bbb1e9157adb973c2cdbc
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/09/2018
---
# <a name="manage-your-data-source---analysis-services"></a>Gerenciar sua fonte de dados – Analysis Services
Depois de instalar o gateway de dados local, será necessário adicionar fontes de dados que podem ser usadas com o gateway. Este artigo abordará como trabalhar com gateways e fontes de dados. Você pode usar a fonte de dados do Analysis Services para a atualização agendada ou para conexões em tempo real.

<iframe width="560" height="315" src="https://www.youtube.com/embed/ownIGbcRAAU" frameborder="0" allowfullscreen></iframe>

## <a name="download-and-install-the-gateway"></a>Baixar e instalar o gateway
É possível baixar o gateway no serviço do Power BI. Selecione **Downloads** > **Gateway de Dados** ou vá para a [página de download do gateway](https://go.microsoft.com/fwlink/?LinkId=698861).

![](media/service-gateway-enterprise-manage-ssas/powerbi-download-data-gateway.png)

## <a name="limitations-of-analysis-services-live-connections"></a>Limitações das conexões dinâmicas do Analysis Services
Você pode usar uma conexão dinâmica em instâncias de tabela ou multidimensionais.

| **Versão do servidor** | **SKU necessário** |
| --- | --- |
| 2012 SP1 CU4 ou posterior |Business Intelligence e SKU Enterprise |
| 2014 |Business Intelligence e SKU Enterprise |
| 2016 |SKU Standard ou superior |

* Não há suporte para a Formatação no Nível de Célula nem para recursos de conversão.
* Ações e Conjuntos Nomeados não são expostos no Power BI, mas você ainda pode se conectar a cubos multidimensionais que também contêm Ações ou Conjuntos Nomeados e criar visuais e relatórios.

## <a name="add-a-gateway"></a>Adicionar um gateway
Para adicionar um gateway, basta [baixar](https://go.microsoft.com/fwlink/?LinkId=698861) e instalar o gateway em um servidor de seu ambiente. Depois de instalar o gateway, ele será mostrado na lista de gateways em **Gerenciar gateways**.

> [!NOTE]
> **Gerenciar gateways** não será mostrado até que você seja o administrador de, pelo menos, um gateway. Isso pode acontecer ao ser adicionado como um administrador ou ao instalar e configurar um gateway.
> 
> 

## <a name="remove-a-gateway"></a>Excluir um gateway
A exclusão de um gateway também excluirá as fontes de dados contidas nele.  Isso também interromperá todos os painéis e relatórios que dependem dessas fontes de dados.

1. Selecione o ícone de engrenagem ![](media/service-gateway-enterprise-manage-ssas/pbi_gearicon.png) no canto superior direito > **Gerenciar gateways**.
2. Gateway > **Remover**
   
   ![](media/service-gateway-enterprise-manage-ssas/datasourcesettings7.png)

## <a name="add-a-data-source"></a>Adicionar uma fonte de dados
É possível adicionar uma fonte de dados selecionando um gateway e clicando em **Adicionar fonte de dados** ou acessando Gateway > **Adicionar fonte de dados**.

![](media/service-gateway-enterprise-manage-ssas/datasourcesettings1.png)

Você pode selecionar o **Tipo de Fonte de Dados** na lista. Se você estiver se conectando a um servidor de Tabela ou Multidimensional, selecione Analysis Services.

![](media/service-gateway-enterprise-manage-ssas/datasourcesettings2-ssas.png)

Em seguida, é necessário preencher as informações sobre a fonte de dados, que incluem o **Servidor** e o **Banco de Dados**.  

O **Nome de usuário** e **Senha** que você inserir serão usados pelo gateway para se conectar à instância do Analysis Services.

> [!NOTE]
> A conta do Windows inserida deve ter permissões de Administrador do Servidor para a instância à qual você está se conectando. Se a senha dessa conta estiver configurada para expirar, os usuários poderão receber um erro de conexão se a senha não estiver atualizada para a fonte de dados. Para obter mais informações, veja o artigo principal sobre o gateway de dados local para saber mais sobre como as [credenciais](service-gateway-onprem.md#credentials) são armazenadas.
> 
> 

![](media/service-gateway-enterprise-manage-ssas/datasourcesettings3-ssas.png)

Você pode clicar em **Adicionar** depois preencher tudo.  Agora você pode usar esta fonte de dados para atualização agendada ou conexões dinâmicas em uma instância local do Analysis Services.  Você verá *Conexão Bem-sucedida* , se tiver êxito.

![](media/service-gateway-enterprise-manage-ssas/datasourcesettings4.png)

### <a name="advanced-settings"></a>Configurações avançadas
Você pode configurar o nível de privacidade para sua fonte de dados. Ele controla como os dados podem ser combinados. É usado somente para a atualização agendada. Não é aplicável às conexões dinâmicas. [Saiba mais](https://support.office.com/article/Privacy-levels-Power-Query-CC3EDE4D-359E-4B28-BC72-9BEE7900B540)

![](media/service-gateway-enterprise-manage-ssas/datasourcesettings9.png)

## <a name="usernames-with-analysis-services"></a>Nomes de usuário com o Analysis Services
Cada vez que um usuário interage com um relatório conectado ao Analysis Services, o nome de usuário efetivo é passado para o gateway e, em seguida, para seu servidor local do Analysis Services. O endereço de email com o qual você entra no Power BI é aquele que informaremos ao Analysis Services como o usuário efetivo. Isso é passado na propriedade de conexão [EffectiveUserName](https://msdn.microsoft.com/library/dn140245.aspx#bkmk_auth). Este endereço de email deve corresponder a um UPN definido dentro do domínio do Active Directory local. O UPN é uma propriedade de uma conta do Active Directory. Essa conta do Windows deverá, então, estar presente em uma função do Analysis Services. Se uma correspondência não for encontrada, o logon no Active Directory não será bem-sucedido. [Saiba mais](https://msdn.microsoft.com/library/ms677605.aspx)

Você também poderá mapear seu nome de entrada do Power BI com um UPN do diretório local. [Saiba mais](service-gateway-enterprise-manage-ssas.md#map-user-names)

<iframe width="560" height="315" src="https://www.youtube.com/embed/Qb5EEjkHoLg" frameborder="0" allowfullscreen></iframe>

### <a name="how-do-i-tell-what-my-upn-is"></a>Como saber qual é a minha UPN?
Talvez você não saiba o que é o UPN e talvez você não seja um administrador de domínio. Você pode usar o comando a seguir em sua estação de trabalho para descobrir o UPN para sua conta.

    whoami /upn

O resultado será semelhante a um endereço de email, mas esse é o UPN que está em sua conta de domínio. Se você estiver usando uma fonte de dados do Analysis Services para conexões dinâmicas e se ela não corresponder ao endereço de email com o qual você entra no Power BI, convém examinar como [Mapear nomes de usuário](#map-user-names).

## <a name="map-user-names"></a>Mapear nomes de usuário
<iframe width="560" height="315" src="https://www.youtube.com/embed/eATPS-c7YRU" frameborder="0" allowfullscreen></iframe>

É possível mapear nomes de usuário para o Analysis Services de duas maneiras diferentes:

1. Remapeamento manual do usuário 
2. Consulta de propriedade do Active Directory local para remapear UPNs AAD para usuários do Active Directory (mapeamento de consulta de AD)

Embora seja possível realizar o mapeamento manual usando a segunda abordagem, fazer isso consumiria tempo e seria difícil de manter; é especialmente difícil quando a correspondência de padrões não é suficiente – como quando os nomes de domínio são diferentes entre o ADD e o AD local ou quando os nomes de conta de usuário são diferentes entre o AAD e o AD. Sendo assim, não é recomendável realizar o mapeamento manual com a segunda abordagem.

Descrevemos essas duas abordagens, em ordem, nas duas seções a seguir

### <a name="manual-user-name-re-mapping"></a>Remapeamento manual de nomes de usuário
Para fontes de dados do Analysis Services, é possível configurar regras personalizadas do nome UPN. Isso ajudará se seus nomes de logon do serviço do Power BI não corresponderem ao UPN do diretório local. Por exemplo, se você entrar no Power BI com john@contoso.com, mas seu UPN do diretório local for john@contoso.local, será possível configurar uma regra de mapeamento para fazer com que john@contoso.local seja passado para o Analysis Services.

Para chegar à tela de Mapeamento de UPN, faça o seguinte:

1. Vá para o **ícone de engrenagem** e selecione **Gerenciar Gateways**.
2. Expanda o gateway que contém a fonte de dados do Analysis Services. Caso contrário, se você ainda não tiver criado a fonte de dados do Analysis Services, poderá fazer isso agora.
3. Selecione a fonte de dados e, em seguida, selecione a guia **Usuários**.
4. Selecione **Mapear nomes de usuário**.
   
    ![](media/service-gateway-enterprise-manage-ssas/gateway-enterprise-map-user-names_02.png)

Em seguida, você verá opções para adicionar regras, bem como para testar determinado usuário.

> [!NOTE]
> Talvez você altere inadvertidamente um usuário que não pretendia alterar. Por exemplo, se **Substituir (valor original)** for *@contoso.com* e seu **Por (Novo nome)**  for *@contoso.local*, todos os usuários com uma entrada que contém *@contoso.com* serão substituídos por *@contoso.local*. Além disso, se **Substituir (Nome Original)** for *dave@contoso.com* e seu **Por (novo nome)** for *dave@contoso.local*, um usuário com a entrada de v-dave@contoso.com deve ser enviado como v-dave*@contoso.local*.
> 
> 

### <a name="ad-lookup-mapping"></a>Mapeamento de consulta do AD
Para realizar a consulta de propriedade do AD local para mapear os UPNs do ADD para usuários do Active Directory, siga as etapas nesta seção. Em primeiro lugar, vamos examinar como isso funciona.

No **serviço do Power BI** ocorre o seguinte:

- Para cada consulta feita por um usuário do AAD do Power BI para um servidor SSAS local, uma cadeia de caracteres UPN é passada, tal como: firstName.lastName@contoso.com

> [!NOTE]
> Quaisquer mapeamentos manuais de usuário UPN definidos na configuração de fonte de dados do Power BI ainda são aplicados *antes* de enviar a cadeia de caracteres de nome de usuário para o gateway de dados local.
> 
> 

No gateway de dados local com o mapeamento de usuário personalizado configurável, faça o seguinte:

1. Localizar o Active Directory para pesquisar (automático ou configurável)
2. Consulte o atributo da Pessoa do AD (como *Email*) com base na cadeia de caracteres UPN (“firstName.lastName@contoso.com”) de entrada no **serviço do Power BI**.
3. Se a Consulta do AD falhar, ela tentará usar o UPN repassado como EffectiveUser para o SSAS.
4. Se a Consulta do AD for bem-sucedida, ela recuperará o *UserPrincipalName* dessa Pessoa do AD. 
5. Ele passa o email *UserPrincipalName* como *EffectiveUser* para o SSAS, tal como:*Alias@corp.on-prem.contoso*

Como configurar seu gateway para executar a Consulta do AD:

1. Baixar e instalar o gateway mais recente
2. No gateway, é necessário alterar o **serviço do gateway de dados local** para ser executado com uma conta de domínio (em vez de uma conta de serviço local, caso contrário, a consulta do AD não funcionará corretamente no tempo de execução). Será necessário reiniciar o serviço do gateway para que a alteração tenha efeito.  Acesse o aplicativo do gateway em seu computador (pesquise “gateway de dados local”). Para fazer isso, vá para **Configurações de Serviço > Alterar a Conta de Serviço**. Certifique-se de ter a chave de recuperação para esse gateway, uma vez que será preciso restaurá-lo no mesmo computador, a menos que você deseje criar um novo gateway em vez disso. 
3. Navegue até a pasta de instalação do gateway, *C:\Arquivos de Programas\Gateway de dados locais* como um administrador para garantir que você tem permissões de gravação e edite o seguinte arquivo:
   
       Microsoft.PowerBI.DataMovement.Pipeline.GatewayCore.dll.config 
4. Editar os dois valores de configuração a seguir de acordo com *suas* configurações de atributo do Active Directory dos seus usuários do AD. Os valores de configuração mostrados abaixo são apenas exemplos – é necessário especificá-los com base em sua configuração do Active Directory. 
   
   ![](media/service-gateway-enterprise-manage-ssas/gateway-enterprise-map-user-names_03.png)
5. Reinicie o serviço do **gateway de dados local** para que a alteração da configuração entre em vigor.

### <a name="working-with-mapping-rules"></a>Trabalhando com regras de mapeamento
Para criar uma regra de mapeamento, insira um valor para **Nome original** e **Novo Nome** e, em seguida, selecione **Adicionar**.

| Campo | Descrição |
| --- | --- |
| Substituir (Nome original) |O endereço de email com o qual você entrou no Power BI. |
| Com (Novo Nome) |O valor pelo qual você deseja substituí-lo. O resultado da substituição é o que será passado para a propriedade *EffectiveUserName* da conexão do Analysis Services. |

![](media/service-gateway-enterprise-manage-ssas/gateway-enterprise-map-user-names-effective-user-names.png)

Ao selecionar um item na lista, você poderá optar por reordenar usando os **ícones de divisa** ou **Excluir** a entrada.

![](media/service-gateway-enterprise-manage-ssas/gateway-enterprise-map-user-names-entry-selected.png)

### <a name="using-wildcard-"></a>Usando curinga (\*)
Você pode usar um caractere curinga para sua cadeia de caracteres **Substituir (Nome Original)**. Ele só pode ser usado sozinho e não com qualquer outra parte da cadeia de caracteres. Isso permitirá que você tire todos os usuários e passe um único valor para a fonte de dados. Isso é útil quando você deseja que todos os usuários em sua organização usem o mesmo usuário no seu ambiente local.

### <a name="test-a-mapping-rule"></a>Testar uma regra de mapeamento
É possível validar o nome que substituirá um nome original inserindo um valor para **Nome original** e selecionando **Testar regra**.

![](media/service-gateway-enterprise-manage-ssas/gateway-enterprise-test-mapping-rule.png)

> [!NOTE]
> As regras que são salvas levarão alguns minutos para o serviço começar a usá-las. No navegador, a regra funcionará imediatamente.
> 
> 

### <a name="limitations-for-mapping-rules"></a>Limitações das regras de mapeamento
* O mapeamento refere-se à fonte de dados específica que está sendo configurada. Não se trata de configurações globais. Caso você tenha várias fontes de dados do Analysis Services, será necessário mapear os usuários para cada fonte de dados.

## <a name="remove-a-data-source"></a>Remover uma fonte de dados
A remoção de uma fonte de dados interromperá todos os painéis ou relatórios que dependem da fonte de dados em questão.  

Para remover uma fonte de dados, acesse Fonte de Dados > **Remover**.

![](media/service-gateway-enterprise-manage-ssas/datasourcesettings6.png)

## <a name="manage-administrators"></a>Gerenciar administradores
Na guia Administradores, para o gateway, você pode adicionar e remover os usuários (ou grupos de segurança) que podem administrar o gateway.

![](media/service-gateway-enterprise-manage-ssas/datasourcesettings8.png)

## <a name="manage-users"></a>Gerenciar usuários
Na guia Usuários da fonte de dados, você pode adicionar e remover os usuários ou os grupos de segurança que podem usar essa fonte de dados.

> [!NOTE]
> A lista de usuários só controla quem tem permissão de publicar relatórios. Os proprietários de relatório podem criar painéis ou pacotes de conteúdo e compartilhá-los com outros usuários.
> 
> 

![](media/service-gateway-enterprise-manage-ssas/datasourcesettings5.png)

## <a name="using-the-data-source"></a>Usando a fonte de dados
Depois de criar a fonte de dados, ela estará disponível para uso com as conexões dinâmicas ou por meio da atualização agendada.

> [!NOTE]
> Os nomes do servidor e do banco de dados devem corresponder entre o Power BI Desktop e a fonte de dados no gateway de dados local!
> 
> 

O vínculo entre o conjunto de dados e a fonte de dados no gateway baseia-se nos nomes do servidor e do banco de dados. Eles devem corresponder. Por exemplo, se você fornecer um Endereço IP para o nome do servidor, no Power BI Desktop, será necessário usar o Endereço IP para a fonte de dados na configuração do gateway. Se você usar *SERVIDOR\INSTÂNCIA*, no Power BI Desktop, precisará usar o mesmo na fonte de dados configurada para o gateway.

Esse é o caso para conexões dinâmicas e a atualização agendada.

### <a name="using-the-data-source-with-live-connections"></a>Usando a fonte de dados com conexões dinâmicas
Você precisará verificar se os nomes do servidor e do banco de dados correspondem entre o Power BI Desktop e a fonte de dados configurada para o gateway. Você também precisará certificar-se de que o usuário está listado na guia **Usuários** da fonte de dados a fim de publicar os conjuntos de dados de conexão dinâmica. A seleção, para conexões dinâmicas, ocorre no Power BI Desktop quando você importa os dados pela primeira vez.

Após a publicação, por meio do Power BI Desktop ou do recurso **Obter Dados**, seus relatórios deverão começar a funcionar. Pode levar vários minutos, após a criação da fonte de dados no gateway, para que a conexão seja utilizável.

### <a name="using-the-data-source-with-scheduled-refresh"></a>Usando a fonte de dados com a atualização agendada
Se você estiver listado na guia **Usuários** da fonte de dados configurada no gateway e houver a correspondência entre os nomes do servidor e do banco de dados, você verá o gateway como uma opção a ser usada com a atualização agendada.

![](media/service-gateway-enterprise-manage-ssas/powerbi-gateway-enterprise-schedule-refresh.png)

## <a name="next-steps"></a>Próximas etapas
[Gateway de dados local](service-gateway-onprem.md)  
[Detalhes sobre o gateway de dados local](service-gateway-onprem-indepth.md)  
[Solução de problemas do gateway de dados local](service-gateway-onprem-tshoot.md)  
Mais perguntas? [Experimente a Comunidade do Power BI](http://community.powerbi.com/)

