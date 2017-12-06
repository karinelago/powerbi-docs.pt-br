---
title: Diretrizes para implantar um gateway de dados para o Power BI
description: "Conheça as melhores práticas e considerações para implantar um gateway para Power BI."
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
ms.openlocfilehash: 3caf9f8aef802e8423f6a3940e55aba99331b912
ms.sourcegitcommit: b3ee37e1587f1269ee7dd9daf1685a06dea3b50c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2017
---
# <a name="guidance-for-deploying-a-data-gateway-for-power-bi"></a>Diretrizes para implantar um gateway de dados para o Power BI
Este artigo fornece diretrizes e considerações para implantar um gateway de dados em seu ambiente de rede. Um **gateway** é um software que facilita o acesso a dados que residem em uma rede privada e local, para uso subsequente em um serviço de nuvem como o Power BI. Este artigo explica as etapas da implantação e fornece diretrizes para a instalação do **gateway de dados local**.

![](media/service-gateway-deployment-guidance/powerbi-gateway-deployment-guidance_01.png)

Para obter mais informações sobre o **gateway de dados local**, incluindo um link para instalá-lo, veja a [postagem no blog](https://powerbi.microsoft.com/blog/power-bi-gateways-march-update/).

## <a name="installation-considerations-for-the-on-premises-data-gateway"></a>Considerações de instalação para o gateway de dados local
Antes de se aprofundar na instalação e implantação, há algumas considerações que você deve ter em mente. As seções a seguir descrevem coisas importantes para se ter em mente.

### <a name="number-of-users"></a>Número de usuários
O número de usuários que consomem um relatório que está usando o gateway é uma métrica importante que decide onde instalar o gateway. Veja algumas perguntas a serem consideradas:

* Os usuários estão usando esses relatórios em diferentes momentos do dia?
* Que tipos de conexões eles estão usando (DirectQuery ou Importação)?
* Todos os usuários estão usando o mesmo relatório?

Se todos os usuários estiverem acessando um determinado relatório ao mesmo tempo todos os dias, certifique-se de instalar o gateway em um computador capaz de tratar todas essas solicitações (consulte as seções a seguir para contadores de desempenho e os requisitos mínimos que podem ajudá-lo a determinar isso).

Há uma restrição no **Power BI** que permite apenas *um* gateway por *relatório*. Portanto, mesmo se um relatório basear-se em várias fontes de dados, todas essas fontes de dados devem passar por um único gateway. No entanto, se um dashboard basear-se em *vários* relatórios, será possível usar um gateway dedicado para cada relatório de contribuição e, assim, distribuir o carregamento do gateway entre esses vários relatórios que contribuem para um único dashboard.

### <a name="connection-type"></a>Tipo de conexão
O **Power BI** oferece dois tipos de conexões, **DirectQuery** e **Importação**. Nem todas as fontes de dados dão suporte aos dois tipos de conexão e muitos motivos podem contribuir para escolher um em vez do outro, como requisitos de segurança, desempenho, limites de dados e tamanhos de modelo de dados. Você pode saber mais sobre o tipo de conexão e as fontes de dados com suporte na seção *lista de tipos de fontes de dados disponíveis* do [artigo Gateway de dados local](service-gateway-onprem.md).

Dependendo de qual tipo de conexão for usado, o uso do gateway poderá ser diferente. Por exemplo, você deve tentar experimentar separar as fontes de dados do **DirectQuery** das fontes de dados de **Atualização agendada** sempre que possível (supondo que eles estejam em relatórios diferentes e possam ser separadas). Fazer isso impede que o gateway tenha milhares de solicitações do DirectQuery em fila no mesmo tempo que a atualização agendada da manhã de um modelo de dados de tamanho grande usada para o dashboard principal da empresa. Veja o que considerar para cada uma:

* Para **Atualização agendada**: dependendo do tamanho da sua consulta e do número de atualizações que ocorrem diariamente, é possível escolher ficar entre os requisitos mínimos de hardware recomendados ou atualizar para um computador de melhor desempenho. Se uma determinada consulta não for fechada, ocorrem transformações no computador do gateway e, dessa forma, ele se beneficia de ter mais RAM disponível.
* Para **DirectQuery**: uma consulta deverá ser enviada sempre que um usuário abrir o relatório ou examinar dados. Portanto, se você previr que mais de 1.000 usuários acessarão os dados ao mesmo tempo, certifique-se de que seu computador tenha componentes de hardware robustos e compatíveis. Mais núcleos de CPU resultará em uma melhor taxa de transferência para uma conexão do **DirectQuery**.

Os requisitos de um computador para instalar um **gateway de dados local** são os seguintes:

**Mínimos:**

* .NET 4.5 Framework
* Versão de 64 bits do Windows 7 / Windows Server 2008 R2 (ou posterior)

**Recomendado:**

* CPU de 8 núcleos
* 8 GB de memória
* Versão de 64 bits do Windows 2012 R2 (ou posterior)

### <a name="location"></a>Localização
O local da instalação do gateway pode ter um impacto significativo no desempenho da sua consulta, então tente certificar-se de que seu gateway, os locais de fonte de dados e o locatário do Power BI estejam o mais próximo possível uns dos outros para minimizar a latência de rede. Para determinar o local de locatário do seu Power BI no serviço do Power BI, selecione o ícone **?** no canto superior direito e, em seguida, selecione **Sobre o Power BI**.

![](media/service-gateway-deployment-guidance/powerbi-gateway-deployment-guidance_02.png)

### <a name="monitoring-gateways"></a>Gateways de monitoramento
Há algumas ferramentas que você pode usar para monitorar o uso e o desempenho de seus gateways instalados.

#### <a name="performance-counters"></a>Contadores de desempenho
Há vários contadores de desempenho que podem ser usados para avaliar a atividade que ocorre no gateway. Os contadores podem ajudá-lo a entender se você tem um grande volume de atividades pelo tipo específico, que pode solicitar a você implantar um novo gateway.

> [!NOTE]
> Esses contadores não capturarão o tempo específico de duração da tarefa.
> 
> 

Além dos contadores do seu computador, o *contador do gateway* fornecerá uma ideia de quanto carregamento o seu computador está manipulando e poderá fornecer uma indicação se a capacidade de recurso do servidor estiver se ampliando ou excedendo.

Esses contadores poderão ser acessados no **Monitor de Desempenho do Windows** e consumidos por quaisquer ferramentas de relatório que você usar para esse fim. Para obter uma explicação sobre como usar o monitor de desempenho do gateway com o Power BI, veja a seguinte postagem no blog criado pela comunidade.

* [Monitorar gateway de dados local](https://insightsquest.com/2016/08/08/monitor-on-premises-data-gateways/)

#### <a name="logs"></a>Logs
Os logs de configuração e de serviço fornecem outra dimensão sobre o que está acontecendo com seu gateway. Sempre verifique os logs do seu gateway quando a conexão não estiver funcionando conforme o esperado, pois nem todas as mensagens de erro são apresentadas no serviço do Power BI.

Uma maneira fácil de exibir todos os arquivos de log no computador local será usar o botão *Exportar Logs* no **gateway de dados local** ao reabrir o gateway depois que a instalação inicial for concluída e, em seguida, selecionar **Diagnóstico > Exportar Logs**.

#### <a name="additional-logging"></a>Log adicional
Por padrão, o gateway realiza log básico. Se você estiver investigando problemas de gateway e precisar de mais informações sobre detalhes de conexão de consulta, será possível habilitar temporariamente o *log detalhado* para coletar outras informações de log. Para fazer isso, no gateway instalado, selecione **Diagnóstico > Log adicional**.

Habilitar essa configuração provavelmente aumentará o tamanho do log de maneira significativa, com base no uso do gateway. É recomendável que, quando você terminar a revisão dos logs, você desabilite o **Log adicional**. Não é recomendável deixar esta configuração habilitada durante o uso normal do gateway.

![](media/service-gateway-deployment-guidance/powerbi-gateway-deployment-guidance_03.png)

#### <a name="network-configuration"></a>Configuração de rede
O gateway cria uma conexão de saída com o **Barramento de Serviço do Azure**. O gateway se comunica nas seguintes portas de saída:

* TCP 443 (padrão)
* 5671
* 5672
* 9350 a 9354

O gateway *não* requer portas de entrada. Todas as necessárias portas estão listadas na lista acima.

É recomendável colocar os endereços IP no seu firewall, para sua região de dados, na lista branca. É possível baixar a lista de endereços IP, localizada na [lista de IP do Datacenter do Microsoft Azure](https://www.microsoft.com/download/details.aspx?id=41653). Essa lista é atualizada semanalmente. O gateway se comunicará com o **Barramento de Serviço do Azure** usando o endereço IP especificado, juntamente com o FQDN (nome de domínio totalmente qualificado). Se você estiver forçando o gateway a se comunicar usando o HTTPS, o gateway usará apenas o FQDN de forma exclusiva e nenhuma comunicação ocorrerá usando os endereços IP.

#### <a name="forcing-https-communication-with-azure-service-bus"></a>Forçar a comunicação HTTPS com o Barramento de Serviço do Azure
É possível forçar o gateway para se comunicar com o **Barramento de Serviço do Azure** usando HTTPS em vez de TCP direto. Fazer isso reduzirá ligeiramente o desempenho. Também é possível forçar o gateway para se comunicar com o **Barramento de Serviço do Azure** por meio do HTTPS usando a interface do usuário do gateway (a partir do lançamento do gateway em março de 2017).

Para fazer isso, no gateway, selecione **Rede** e, em seguida, **ative** o **Modo de conectividade do Barramento de Serviço do Azure**.

![](media/service-gateway-deployment-guidance/powerbi-gateway-deployment-guidance_04.png)

### <a name="additional-guidance"></a>Diretrizes adicionais
Esta seção fornece diretrizes adicionais para implantar e gerenciar gateways.

* Evite ter um único ponto de falha. Se possível, distribua suas fontes de dados locais em vários gateways; nesse caso, se um computador ficar não disponível, ainda será possível atualizar partes dos dados e você não perderá essa funcionalidade completamente.
* O gateway não pode ser instalado em um controlador de domínio. Portanto, não planeje nem tente fazer isso.
* Não instale um gateway em um computador que possa ser desligado, entre no modo de suspensão ou não se conecte à Internet (por exemplo, um laptop), pois o gateway não poderá ser executado em nenhuma dessas circunstâncias.
* Evite instalar um gateway em uma rede sem fio, já que o desempenho poderá ser afetado em uma rede sem fio.

#### <a name="gateway-recovery"></a>Recuperação do gateway
É possível recuperar seu gateway existente ou movê-lo para um novo computador usando a **chave de recuperação**. A chave de recuperação será fornecida ao usuário que instalar o gateway e *não poderá* ser alterada posteriormente. A chave de recuperação é usada para a criptografia de dados e para a recuperação do gateway.

Para recuperar seu gateway, certifique-se de ser um administrador no gateway, de saber o nome do gateway, de que ter a chave de recuperação correta e de ter um novo computador disponível com características de desempenho semelhantes.

Depois de entrar, selecione a opção **Migrar um gateway existente**. Em seguida, é necessário escolher o gateway que você gostaria de recuperar ou migrar e, por fim, fornecer que a chave de recuperação e clicar em configurar. Quando essa etapa for concluída, o gateway antigo será substituído pelo novo gateway e o novo gateway herdará seu nome e todas as fontes de dados configuradas anteriormente. Agora todas as fontes de dados passarão pelo novo computador, sem a necessidade de republicar nada. Ainda não há suporte para o failover automático, mas ele é um recurso que a equipe de gateway está considerando ativamente.

#### <a name="administrators"></a>Administradores
É possível encontrar uma lista de administradores de gateway no **serviço do Power BI**. Depois de entrar no serviço do **Power BI**, selecione **Configurações** (o ícone de engrenagem) **> Gerenciar Gateways -> Interface do Usuário do Gateway**.  

![](media/service-gateway-deployment-guidance/powerbi-gateway-deployment-guidance_05.png)

Lá, é possível selecionar um gateway e ver a lista de administradores de gateway. Os administradores listados podem acessar, recuperar e excluir o gateway. Eles também podem adicionar e excluir fontes de dados no gateway. Para se certificar de que todos os administradores na organização tenham acesso a todos os gateways no seu grupo, recomenda-se o seguinte:

* Crie um grupo de segurança do **AAD** e adicione outros usuários a ele. Em seguida, adicione esse grupo de segurança à lista dos respectivos administradores de gateway. Isso garante que mais de uma pessoa tenha acesso ao gateway em caso de falha ou quando for necessário recuperar ou migrar o gateway. Isso também oferece a outros administradores uma visão de quais gateways estão sendo usados em seus grupos e quais fontes de dados existem em cada gateway.

## <a name="next-steps"></a>Próximas etapas
[Definindo as configurações de proxy](service-gateway-proxy.md)  
[Solução de problemas do gateway de dados local](service-gateway-onprem-tshoot.md)  
[Perguntas frequentes do gateway de dados local](service-gateway-onprem-faq.md)  

Mais perguntas? [Experimente a Comunidade do Power BI](http://community.powerbi.com/)

