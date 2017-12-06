---
title: Gateway do Power BI - Pessoal
description: Gateway do Power BI - Pessoal
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
ms.date: 12/06/2017
ms.author: davidi
ms.openlocfilehash: fc062387282bf01fd06a9e3d2420ac748c0bc592
ms.sourcegitcommit: d91436de68a0e833ecff18d976de9d9431bc4121
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/06/2017
---
# <a name="power-bi-gateway---personal"></a>Gateway do Power BI - Pessoal
> [!NOTE]
> Há uma nova versão do gateway pessoal para o Power BI denominada **gateway de dados local (modo pessoal)**. O artigo a seguir descreve a versão anterior do gateway pessoal, chamada **Power BI Gateway – Personal**, que será desativada e deixará de funcionar após 31 de julho de 2017. Para obter informações sobre a nova versão do gateway pessoal, incluindo como instalá-la, consulte o artigo [**Gateway de dados local (modo pessoal)**](service-gateway-personal-mode.md).
> 
> 

O **Power BI Gateway – Personal** atua como uma ponte, fornecendo transferência de dados rápida e segura entre o serviço do Power BI e as fontes de dados locais que dão suporte à [atualização](refresh-data.md). Este artigo destina-se a fornecer uma compreensão aprofundada de como o gateway funciona e se ele é necessário para você. Também fizemos um [vídeo bastante útil](https://www.youtube.com/watch?v=de58vROLqZI) sobre o gateway pessoal. 

Ele é instalado e executado como um serviço em seu computador. Como serviço, ele é executado com uma conta do Windows especificada durante a configuração. Em alguns casos, o Gateway é executado como um aplicativo. Veremos mais detalhes posteriormente.

Quando o Power BI atualiza os dados de uma fonte de dados local, o gateway garante que a sua conta do Power BI tem as permissões certas para se conectar e consultar os dados da fonte.

A transferência de dados entre o Power BI e o gateway é protegida pelo [Barramento de Serviço do Azure](http://azure.microsoft.com/documentation/services/service-bus/). O Barramento de Serviço cria um canal seguro entre o serviço do Power BI e seu computador. Como o gateway fornece essa conexão segura, geralmente, não é necessário abrir uma porta no firewall.

Antes de entrarmos em detalhes sobre o gateway, vamos dar uma olhada em alguns termos usados no Power BI:

Um *conjunto de dados* são dados carregados no serviço do Power BI de uma fonte de dados online ou local. Crie um conjunto de dados quando usar o recurso Obter Dados para se conectar e carregar dados. Os conjuntos de dados aparecem no painel Meu Espaço de Trabalho do Espaço de Trabalho do Power BI em seu navegador. Quando você cria relatórios e fixa blocos aos seus painéis, você examina os dados de seus conjuntos de dados.

Na verdade, uma *fonte de dados* é o local do qual os dados carregados em um conjunto de dados são recebidos. Pode ser qualquer coisa: um banco de dados, uma planilha do Excel, um serviço Web, etc. Com as pastas de trabalho do Excel, você pode criar uma planilha simples com linhas de dados, e isso é considerado uma fonte de dados. Você também pode usar o Power Query ou o Power Pivot no Excel para se conectar e consultar dados de fontes de dados online e locais, tudo na mesma pasta de trabalho. Com o Power BI Desktop, você pode usar o recurso Obter Dados para se conectar e consultar dados de fontes de dados online e locais.

O gateway pessoal é instalado por meio do gateway de dados local. Você pode baixá-lo na [página Power BI Gateway](https://powerbi.microsoft.com/gateway/).

## <a name="do-i-need-a-gateway"></a>Preciso de um gateway?
Antes de instalar um gateway, é importante saber se você realmente precisa de um. Isso realmente depende de suas fontes de dados:

### <a name="on-premises-data-sources"></a>Fontes de dados locais
Um gateway pessoal *é necessário* para atualizar os conjuntos de dados que obtêm dados de uma fonte de dados local com suporte em sua organização.

Com um gateway, agora há suporte para ATUALIZAR AGORA e AGENDAR ATUALIZAÇÃO para conjuntos de dados carregados de:

* Pastas de trabalho do Microsoft Excel 2013 (ou posterior) em que o Power Query ou o Power Pivot é usado para se conectar e consultar dados de uma fonte de dados online ou local com suporte. Todas as fontes de dados locais mostradas em Obter Dados Externos no Power Query ou Power Pivot dão suporte à atualização, exceto o arquivo do Hadoop (HDFS) e o Microsoft Exchange.
* Arquivos do Microsoft Power BI Desktop, nos quais o recurso Obter Dados é usado para se conectar e consultar dados de uma fonte de dados local com suporte. Todas as fontes de dados locais mostradas em Obter Dados dão suporte à atualização, exceto o arquivo do Hadoop (HDFS) e o Microsoft Exchange.

### <a name="online-data-sources"></a>Fontes de dados online
Um gateway *somente será necessário* se você estiver usando a função [**Web.Page**](https://msdn.microsoft.com/library/mt260924.aspx). Nos outros casos, um gateway *não* é necessário para a atualização dos conjuntos de dados que obtêm dados somente de uma fonte de dados online.

> [!NOTE]
> Se estiver usando a função [**Web.Page**](https://msdn.microsoft.com/library/mt260924.aspx), você só precisará de um gateway se tiver publicado novamente o conjunto de dados ou o relatório após 18 de novembro de 2016.
> 
> 

Agora há suporte para ATUALIZAR AGORA e AGENDAR ATUALIZAÇÃO sem um gateway para conjuntos de dados carregados de:

* Pacotes de conteúdo de fontes de dados online (pacotes de conteúdo\\serviços). Por padrão, conjuntos de dados de pacotes de conteúdo são atualizados automaticamente uma vez por dia, mas você também pode atualizar manualmente ou configurar um agendamento de atualização.
* Pastas de trabalho do Microsoft Excel 2013 (ou posterior) em que o Power Query ou o Power Pivot é usado para se conectar e consultar dados de uma fonte de dados online.
* Arquivos do Microsoft Power BI Desktop, nos quais o recurso Obter Dados é usado para se conectar e consultar dados de uma fonte de dados online.

**Pergunta:** E se a minha pasta de trabalho do Excel ou arquivo do Power BI Desktop obtiver dados de fontes de dados online e locais?

**Resposta:** Um gateway *é* necessário. Você precisará instalar e configurar um gateway para atualizar os dados das fontes de dados locais.

**Pergunta:** E se a minha pasta de trabalho do Excel contiver apenas linhas de dados digitados?**

**Resposta:** Um gateway *não é* necessário. Você só precisará instalar e configurar um gateway se sua pasta de trabalho usar o Power Query ou o Power Pivot para consultar e carregar dados no modelo de dados por meio de uma fonte de dados local com suporte

## <a name="setting-up-a-gateway-for-the-first-time"></a>Configurando um gateway pela primeira vez
Configurar um gateway pela primeira vez consiste em um processo de três etapas:

1. Baixar e instalar um gateway
2. Configurar o gateway
3. Entrar nas fontes de dados do Power BI

Vamos examinar mais detalhadamente cada etapa.

### <a name="download-and-install-a-gateway"></a>Baixar e instalar um gateway
> [!NOTE]
> Há uma nova versão do gateway pessoal para o Power BI denominada **gateway de dados local (modo pessoal)**. Este artigo descreve a versão anterior do gateway pessoal, chamada **Power BI Gateway – Personal**, que será desativada e deixará de funcionar após 31 de julho de 2017. Para obter informações sobre a nova versão do gateway pessoal, incluindo como instalá-la, consulte o artigo [**Gateway de dados local (modo pessoal)**](service-gateway-personal-mode.md).
> 
> 

Será solicitado que você instale um gateway quando clicar pela primeira vez em ATUALIZAR AGORA ou AGENDAR ATUALIZAÇÃO para um conjunto de dados com suporte. Se preferir, para baixar o gateway, selecione **Gateway de Dados** no menu Downloads. Baixe o [gateway de dados local](http://go.microsoft.com/fwlink/?LinkID=820925).

Você deverá selecionar **Gateway Pessoal** em vez de **Gateway de dados local** para ter um gateway que é por conta própria.

Na verdade, não é muito difícil instalar um gateway. Você selecionará um local para instalá-lo e lerá e aceitará o contrato de licença, assim como qualquer outro aplicativo. No entanto, há algumas coisas importantes que você precisa saber. Em particular, o tipo de computador no qual o gateway é instalado e o tipo de conta ao qual você está conectado ao Windows nesse computador.

> [!NOTE]
> O gateway precisa ter acesso à fonte de dados. Se não for possível conectar seu computador pessoal à fonte de dados, considere a instalação de um [gateway de dados local](service-gateway-onprem.md) em um computador que tenha acesso à fonte de dados. Um exemplo disso seria o SQL Server instalado em uma VM (máquina virtual) hospedada no Azure. Seu computador pessoal pode não ter acesso à VM. Em vez disso, você pode instalar o gateway de dados local na VM e configurar uma fonte de dados no serviço do Power BI.
> 
> 

### <a name="computer-type"></a>Tipo de computador
O tipo de computador em que você instalar o gateway é importante.

> [!NOTE]
> Há suporte para o gateway pessoal apenas em sistemas operacionais Windows de 64 bits.
> 
> 

Em um laptop – Para que uma atualização agendada ocorra, o gateway precisa estar em execução. Laptops estão geralmente desligados ou no estado de suspensão por um período mais longo do que estão sendo executados. Se você instalar o gateway em um laptop, lembre-se de definir os horários da atualização agendada nos quais o laptop será executado. Caso contrário, não haverá uma nova tentativa de atualização até a próxima hora da atualização agendada.

Em um computador desktop – Não há muitos problemas aqui. Assegure-se de que o computador e o gateway estão em execução nos horários da atualização agendada. Muitos computadores desktop entram no modo de suspensão, e a atualização agendada não poderá ocorrer se eles estiverem suspensos.

Assim que instalar um gateway, você não precisará instalar outro. Um gateway funcionará para qualquer número de conjuntos de dados com suporte. Você também não precisa instalar o gateway no mesmo computador usado para carregar a pasta de trabalho e os arquivos do Power BI Desktop. Veja um exemplo: digamos que você tenha uma pasta de trabalho do Excel que se conecta a uma fonte de dados do SQL Server em sua organização. Você usou o recurso Obter Dados no Power BI para carregar a pasta de trabalho do laptop. Você também tem um computador desktop que mantém em execução o tempo todo, e instalou e configurou um gateway nesse computador. No Power BI, você entrou em suas fontes de dados e configurou um agendamento de atualização para o conjunto de dados.  Quando chega o horário da atualização agendada, o Power BI estabelece uma conexão segura com o gateway instalado no computador desktop. Ele então se conecta com segurança às fontes de dados para obter atualizações. Para a atualização, não há nenhuma comunicação com a pasta de trabalho original carregada do laptop.

> [!NOTE]
> É possível instalar os gateways pessoais e corporativos no mesmo computador.
> 
> 

### <a name="windows-account"></a>Conta do Windows
Ao instalar o gateway, você será conectado ao computador por meio de sua conta do Windows. O tipo de permissões que sua conta do Windows tem terá um efeito sobre como o gateway é instalado e como ele é executado no Windows.

Quando estiver conectado ao Windows:

|  | Com permissões de administrador | Sem permissões de administrador |
| --- | --- | --- |
| **O Power BI Gateway – Personal é executado como um(a)** |Serviço |Aplicativo |
| **Atualização agendada** |Enquanto o computador e o serviço de gateway estiverem em execução, você não precisa estar conectado no momento agendado para atualização. |Você deve estar conectado ao computador no momento agendado para atualização. |
| **Alterar senha da conta do Windows** |Você deve alterar sua Senha no serviço do gateway. Se a senha da conta usada pelo gateway não for mais válida, a atualização falhará. |O gateway sempre será executado usando a conta e a senha às quais você está conectado. Se não estiver conectado ao Windows, o gateway não será executado e ocorrerá uma falha na atualização. |

### <a name="configure-the-gateway"></a>Configurar o gateway
Depois de concluir o Assistente de Instalação, você será solicitado a iniciar o Assistente de Configuração. Na verdade, não é muito difícil configurar um gateway. Você precisará entrar no Power BI do Assistente. Isso é necessário para que o Assistente estabeleça uma conexão com sua conta do Power BI no serviço do Power BI.

Se você estiver conectado ao Windows com uma conta com permissões de Administrador, você será solicitado a inserir suas credenciais de conta do Windows. É possível especificar uma conta diferente do Windows, mas lembre-se de que as permissões determinam como o gateway é executado. O serviço do gateway será executado por meio dessa conta.

### <a name="sign-in-to-data-sources"></a>Entre nas fontes de dados
Depois de concluir o Assistente de Configuração e o gateway estiver em execução, você precisará especificar um tipo de Autenticação e entrar em cada uma das fontes de dados do conjunto de dados. Você concluirá esta etapa no Power BI.

![](media/personal-gateway/pg_dataset_settings_signin.png)

Você só precisa especificar um tipo de autenticação e entrar em uma fonte de dados uma única vez. Entre por meio da seção **Gerenciar Fontes de Dados** na tela Configurações de um conjunto de dados. Se você tiver várias fontes de dados, você precisará entrar em cada uma delas. O gateway determina um tipo de Autenticação padrão dependendo da fonte de dados. Na maioria dos casos, é a autenticação do Windows; no entanto, em alguns casos, sua fonte de dados pode exigir um tipo de autenticação diferente. Se não tiver certeza, verifique com seu administrador da fonte de dados.

## <a name="up-and-running"></a>Em execução!
Quando o Gateway estiver em execução, será possível clicar em AGENDAR ATUALIZAÇÃO para um conjunto de dados, em que você verá a página Configurações do conjunto de dados.

![](media/personal-gateway/pg_awintsales_settings.png)

Esta página mostra:

1. Atualizar status - Mostra o êxito da atualização e a hora da próxima atualização agendada.
2. **Gateway** – Mostra se um gateway está instalado e se ele está online. Se um gateway estiver instalado, mas não estiver online, as configurações Gerenciar Fontes de Dados e Agendar Atualização serão desabilitadas.
3. **Gerenciar Fontes de Dados** - Mostra as fontes de dados às quais o conjunto de dados se conecta. Você pode Entrar ou alterar o tipo de autenticação. Você só precisará Entrar em cada fonte de dados uma só vez.
4. **Agendar Atualização** – Você pode definir as configurações de um agendamento de atualização aqui. Se o gateway não estiver online, essas configurações serão desabilitadas.
5. Notificações de falha de atualização – Essa opção, marcada por padrão, enviará um email para você em caso de falha em uma atualização agendada.

## <a name="updating-your-windows-account-password"></a>Atualizando sua senha da conta do Windows
Se você estivesse conectado ao computador com uma conta do Windows com privilégios de administrador durante a instalação do gateway, ele seria executado como um serviço usando a conta do Windows especificada no Assistente de Configuração. Normalmente, essa será a mesma conta do Windows que você usa para fazer logon em seu computador. Quando você altera a senha de sua conta do Windows, também será necessário alterá-la no gateway; caso contrário, o serviço poderá não ser executado e ocorrerá uma falha na atualização. Para alterar sua senha da conta do Windows para o gateway, clique no ícone do gateway pessoal na Barra de Tarefas da Área de Trabalho do Windows ou em Aplicativos.

![](media/personal-gateway/pg_programicon.png)

Aqui, é possível atualizar sua senha e verificar o status da conexão do gateway.

![](media/personal-gateway/pg_credentials.png)

## <a name="ports"></a>Portas
O gateway se comunica com as portas de saída TCP 443 (padrão), 5671, 5672, 9350 a 9354.  O gateway não requer portas de entrada.

| Nomes de domínio | Portas de saída | Descrição |
| --- | --- | --- |
| *.powerbi.com |443 |HTTPS |
| *.analysis.windows.net |443 |HTTPS |
| *.login.windows.net |443 |HTTPS |
| *.servicebus.windows.net |5671-5672 |Advanced Message Queuing Protocol (AMQP) |
| *.servicebus.windows.net |443, 9350-9354 |Ouvintes na Retransmissão do Barramento de Serviço por TCP (requer 443 para aquisição de token de Controle de Acesso) |
| *.frontend.clouddatahub.net |443 |HTTPS |
| *.core.windows.net |443 |HTTPS |
| login.microsoftonline.com |443 |HTTPS |
| login.windows.net |443 |HTTPS |

Se precisar colocar endereços IP em vez de domínios na lista branca, você poderá baixar e usar a lista de intervalos de IP do Datacenter do Microsoft Azure. [Download](https://www.microsoft.com/download/details.aspx?id=41653)

## <a name="next-steps"></a>Próximas etapas
[Gateway de dados local (modo pessoal) – a nova versão do gateway pessoal](service-gateway-personal-mode.md)
[Definindo as configurações de proxy dos gateways do Power BI](service-gateway-proxy.md)  
[Power BI Premium](service-premium.md)

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](http://community.powerbi.com/)

