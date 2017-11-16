---
title: "Power BI - conceitos básicos"
description: "Power BI - conceitos básicos"
services: powerbi
documentationcenter: 
author: mihart
manager: kfile
backup: 
editor: 
tags: 
featuredvideoid: B2vd4MQrz4M
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: get-started-article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 05/31/2017
ms.author: mihart
ms.openlocfilehash: f20ea18fb46928bf7533caacf55a0cdb3d761571
ms.sourcegitcommit: 99cc3b9cb615c2957dde6ca908a51238f129cebb
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/13/2017
---
# <a name="power-bi---basic-concepts-for-power-bi-service"></a>Power BI – conceitos básicos do serviço do Power BI
<!-- Shared newnav Include -->
[!INCLUDE [newnavbydefault](./includes/newnavbydefault.md)]

Este artigo pressupõe que você já tenha [se inscrito no Power BI](service-self-service-signup-for-power-bi.md) e [adicionado alguns dados](service-get-data.md).

Ao abrir o serviço do Power BI, você verá um ***dashboard***. Dashboards são uma coisa que diferencia o serviço do Power BI de Power BI Desktop.

![](media/service-basic-concepts/completenewer.png)

Os principais recursos da sua interface do usuário de serviço do Power BI são os seguintes:

1. barra de navegação
2. painel com blocos
3. caixa de perguntas de P e R
4. botões de ajuda e comentários
5. título do painel
6. Iniciador do aplicativo do Office 365
7. Botões da página inicial do Power BI
8. Ações adicionais do painel

Nos aprofundaremos nesses itens mais tarde, mas primeiro vamos examinar alguns conceitos do Power BI.

Ou, talvez você queira assistir a este vídeo primeiro antes de ler o restante deste artigo.  Nesse vídeo, Will examina os conceitos básicos e oferece um tour pelo serviço do Power BI.

<iframe width="560" height="315" src="https://www.youtube.com/embed/B2vd4MQrz4M" frameborder="0" allowfullscreen></iframe>


## <a name="power-bi-concepts"></a>Conceitos do Power BI
Os três principais componentes do Power BI são: ***painéis***, ***relatórios*** e ***conjuntos de dados***. Você não pode ter painéis ou relatórios sem dados (bem, você até pode ter painéis vazios e relatórios vazios, mas eles não são muito úteis até que tenham dados), então vamos começar com os **conjuntos de dados**.

## <a name="datasets"></a>Conjuntos de dados
Um *conjunto de dados* é uma coleção de dados que você *importa* ou a que *se conecta*. O Power BI permite que você se conecte a todos os tipos de conjuntos de dados, os importe e os reúna em um único lugar.  

Na barra de navegação, os conjuntos de dados aos quais você se conectou ou importou estão listados no título **Conjuntos de dados**. Cada conjunto de dados listado representa uma fonte de dados única, por exemplo, uma planilha do Excel no OneDrive, um conjunto de dados de tabela SSAS local ou um conjunto de dados do Salesforce. Há várias diferentes fontes de dados com suporte, e sempre estamos adicionando novas. [Veja a lista de tipos de conjunto de dados que podem ser usados com o Power BI](service-get-data.md).

**UM** conjunto de dados...

* pode ser usado repetidas vezes, indefinidamente.
* pode ser usado em vários relatórios diferentes.
* Visualizações desse único conjunto de dados podem ser exibidas em vários painéis diferentes.
  
  ![](media/service-basic-concepts/drawing2.png)

Para [se conectar a um conjunto de dados ou importá-lo](service-get-data.md), selecione **Obter Dados** (na parte inferior da barra de navegação) ou selecione o ícone de mais ao lado do título **Conjuntos de dados**. Siga as instruções para se conectar à fonte específica ou para importá-la e adicione o conjunto de dados ao seu espaço de trabalho. Novos conjuntos de dados estão listados na barra de navegação esquerda e marcados com um asterisco amarelo. O trabalho que você realiza no Power BI não altera o conjunto de dados subjacente.

Se você fizer [parte de um ***espaço de trabalho do aplicativo***](service-collaborate-power-bi-workspace.md), os conjuntos de dados adicionados por um membro do espaço de trabalho estarão disponíveis para os outros membros do espaço de trabalho.

Os conjuntos de dados podem ser atualizados, renomeados, explorados, usados para criar relatórios e removidos. Para explorar um conjunto de dados, selecione-o. O que você está fazendo é abrir o conjunto de dados no editor de relatórios, onde pode de fato começar a se aprofundar nos dados e criar visualizações. Então, vamos passar para o próximo tópico – relatórios.

### <a name="dig-deeper"></a>Aprofunde-se:
* [Power BI Premium – o que é?](service-premium.md)
* [Obter dados para o Power BI](service-get-data.md)
* [Conjuntos de dados de exemplo e pacotes de conteúdo para o Power BI](sample-datasets.md)

## <a name="reports"></a>Relatórios
Um relatório do Power BI é uma ou mais páginas de visualizações (quadros e gráficos como gráficos de linhas, gráficos de pizza, mapas de árvore e muito outros). As visualizações também são chamadas de ***visuais***. Todas as visualizações em um relatório vêm de um único conjunto de dados. Os relatórios podem ser criados do zero com o Power BI, podem ser importados com dashboards que seus colegas compartilham com você ou podem ser criados quando você se conecta a conjuntos de dados do Excel, Power BI Desktop, bancos de dados, aplicativos SaaS e [pacotes de conteúdo](service-organizational-content-pack-introduction.md).  Por exemplo, quando você se conecta a uma pasta de trabalho do Excel que contém planilhas do Power View, o Power BI cria um relatório baseado nessas planilhas. E quando você se conecta a um aplicativo SaaS, o Power BI importa um relatório pré-criado.

Há dois modos de exibir relatórios e interagir com eles: [Modo de Exibição de Leitura](service-report-open-in-reading-view.md) e [Modo de Exibição de Edição](service-interact-with-a-report-in-editing-view.md).  Somente a pessoa que criou o relatório, co-proprietários e pessoas com permissão têm acesso a todos a todos os recursos de exploração, criação e compartilhamento de recursos do ***Modo de Exibição de Edição*** para esse relatório. E as pessoas com quem eles compartilharem o relatório podem explorar e interagir com o relatório usando o ***Modo de Exibição de Leitura***.   

No painel de navegação, seus relatórios estão listados no título **Relatórios**. Cada relatório listado representa uma ou mais páginas de visualizações, com base em um dos conjuntos de dados subjacentes. Para abrir um relatório, basta selecioná-lo. Por padrão, o relatório é aberto primeiro na Exibição de Leitura.  Selecione apenas **Editar relatório** para abri-lo no Modo de Exibição de Edição (se você tiver as permissões necessárias).  Se um painel compartilhado tiver relatórios, você NÃO verá o relatório listado na barra de navegação. Em vez disso, abra relatórios compartilhados diretamente a partir do painel compartilhado selecionando um bloco do painel (mais informações sobre os blocos serão fornecidas posteriormente).

**UM** relatório...

* pode ser associado a vários painéis (blocos anexados por meio desse relatório podem aparecer em vários painéis).
* pode ser criado usando os dados de um conjunto de dados. (a pequena exceção é que o Power BI Desktop pode combinar mais de um conjunto de dados em um único relatório que pode, por sua vez, ser importado para o Power BI)
  
  ![](media/service-basic-concepts/drawing3new.png)

## <a name="dashboards"></a>Painéis
Um *painel* é algo que você cria ou algo que um colega cria e compartilha com você. Trata-se de uma única tela, que contém nenhum ou mais blocos e widgets. Cada bloco exibe uma única [visualização](power-bi-report-visualizations.md), que foi criada a partir de um conjunto de dados e fixada ao painel. Há várias maneiras de adicionar blocos ao seu painel; muitas maneiras para serem abordadas neste tópico de visão geral. Para saber mais, veja [Blocos do painel no Power BI](service-dashboard-tiles.md). 

Na barra de navegação, "seus" painéis são listados no título **Painéis** . "Seu" significa que você tem acesso a eles, não necessariamente que você os criou. Cada painel representa uma exibição personalizada de algum subconjunto dos conjuntos de dados subjacentes.  Se possuir o painel, você também terá acesso aos conjuntos de dados subjacentes e eles aparecerão na barra de navegação em **Conjuntos de dados**.  Se o painel foi compartilhado com você, ele tem um ícone de compartilhamento ![](media/service-basic-concepts/sharing-icon.png) ao seu lado e, dependendo de como foi compartilhado, você pode ou não ver os conjuntos de dados subjacentes listados na sua barra de navegação.

> [!NOTE]
> A fixação e os blocos são abordados com mais detalhes abaixo, sob o título "Dashboard com blocos".
> 
> 

**UM** painel...

* pode exibir visualizações de vários conjuntos de dados diferentes
* pode exibir visualizações de vários relatórios diferentes
* pode exibir visualizações fixadas de outras ferramentas (por exemplo, Excel)
  
  ![](media/service-basic-concepts/drawing1.png)

### <a name="dig-deeper"></a>Aprofunde-se:
**Um painel pode ser [criado do zero](service-dashboard-create.md)** - crie um novo painel em branco e obtenha alguns dados. 

**Você ou um colega pode criar um painel e [compartilhá-lo](service-share-dashboards.md)** - quando você aceita o convite, o painel compartilhado (e qualquer relatório e o conjunto de dados associados) é adicionado à sua barra de navegação. O Power BI Pro é necessário para compartilhar dashboards e para exibir dashboards compartilhados.

**Às vezes, os painéis são importados com o conjunto de dados ou são criados quando você se conecta ao conjunto de dados**. Por exemplo, o assistente **Obter Dados** para o Salesforce pergunta se você deseja que um painel e/ou relatório seja criado por meio do conjunto de dados. 

**Por que as pessoas criam dashboards?**  Aqui estão apenas alguns dos motivos:

* para ver rapidamente todas as informações necessárias para tomar decisões
* para monitorar as informações mais importantes sobre seus negócios
* para garantir que todos os colegas estejam na mesma página, visualizando e usando as mesmas informações
* para monitorar a integridade uma empresa, produto, unidade de negócios, campanha de marketing, etc.
* para criar uma exibição personalizada de um painel maior – todas as métricas que são importantes para mim

## <a name="my-workspace"></a>Meu espaço de trabalho
Nós já voltamos ao seu painel e espaço de trabalho do Power BI. Vamos examinar com mais detalhes as partes que compõem a página de aterrissagem do serviço do Power BI.

![](media/service-basic-concepts/completenewer.png)

### <a name="1-navigation-bar-navbar"></a>1. **Barra de navegação** (navbar)
Use a barra de navegação para mover-se entre os blocos de construção do Power BI: painéis, relatórios e conjuntos de dados.  

  ![](media/service-basic-concepts/navpane-new.png)

* Selecione **Obter Dados** para [adicionar conjuntos de dados, relatórios e dashboards ao Power BI](service-get-data.md).
* Expanda e recolha a barra de navegação com este ícone ![](media/service-basic-concepts/expand-icon.png).
* Use **Pesquisar** para localizar itens específicos na barra de navegação.
* Selecione um ícone de adição ![](media/service-basic-concepts/pbi_nancy_plus.png) para criar um novo painel ou obter um novo conjunto de dados.
* Os **Painéis, Relatórios** e **Conjuntos de dados** listados estão disponíveis para uso.  Os painéis compartilhados são somente leitura e exibem o ícone de compartilhado ![](media/service-basic-concepts/sharing-icon.png).
* Os nomes do painel, relatório e conjunto de dados geralmente correspondem ao nome do arquivo do conjunto de dados subjacente, mas você pode [renomeá-los](service-rename.md).
* Clique com o botão direito do mouse em um painel, relatório ou conjunto de dados para exibir o menu contextual. 
  
  ![](media/service-basic-concepts/menu.png)

Clique uma vez em

* um título para recolhê-lo ou expandi-lo
* um painel para exibi-lo
* um relatório para abri-lo na Exibição de Leitura
* um conjunto de dados para explorá-lo

### <a name="2-dashboard-with-tiles"></a>2. **Painel com blocos**
Os painéis são compostos por [blocos](service-dashboard-tiles.md).  Os blocos são criados no Modo de Exibição de Edição de relatório, P e R, outros dashboards e podem ser fixados no Excel, no SSRS e muito mais. Um tipo especial de bloco chamado de [widget](service-dashboard-add-widget.md) é adicionado diretamente ao painel. Os blocos que aparecem em um painel foram especificamente inseridos ali pelo criador/proprietário de um relatório.  O ato de adicionar um bloco em um painel é chamado *fixação*.

![](media/service-basic-concepts/canvas.png)

Para obter mais informações, consulte **Dashboards** (acima).

### <a name="3-qa-question-box"></a>3. **Caixa de perguntas de P e R**
Uma maneira de explorar seus dados é fazer uma pergunta e deixar que o P e R do Power BI lhe forneça uma resposta, na forma de uma visualização. O P e R não pode ser usado para adicionar conteúdo a um relatório – apenas para adicionar conteúdo a painéis, na forma de blocos.

O P e R procura uma resposta no conjunto(s) de dados conectado ao painel.  Um conjunto de dados conectado é aquele que tem pelo menos um bloco anexado a esse painel.

![](media/service-basic-concepts/qna.png)

Assim que você começa a digitar sua pergunta, o P e R leva você até a página de P e R. Conforme você digita, o P e R ajuda você a fazer a pergunta certa e encontrar a melhor resposta com reformulações, preenchimento automático, sugestões e muito mais. Quando você encontrar uma visualização (resposta) de que gosta, fixe-a em seu painel. Para obter mais informações, veja [P e R no Power BI](service-q-and-a.md).

### <a name="4-full-screen-notifications-settings-downloads-help-and-feedback"></a>4. **Tela inteira, Notificações, Configurações, Downloads, Ajuda e Comentários**
Os ícones no canto superior direito são seus recursos para configurações, notificações, downloads, obter ajuda e fornecer comentários à equipe do Power BI. Selecione a seta dupla para abrir o dashboard no modo **Tela inteira**.  

![](media/service-basic-concepts/help-new.png)

### <a name="5-dashboard-title-aka-what-dashboard-is-active"></a>5. **Título do painel** (também conhecido como “Que painel está ativo?”)
Nem sempre é fácil descobrir qual painel está ativo.  O título do painel é exibido na página de exibição do painel, na página de P e R, no Modo de Exibição de Edição de relatório, no Modo de Exibição de Leitura de relatório e também quando você abre um conjunto de dados.   

![](media/service-basic-concepts/dash-title-new.png)

### <a name="6-office-365-app-launcher"></a>6. **Iniciador do aplicativo do Office 365**
O iniciador do aplicativo foi projetado para ajudá-lo em seus aplicativos do Office 365.

![](media/service-basic-concepts/basicconcepts2-newer.png)

### <a name="7-power-bi-home"></a>7. **Página inicial do Power BI**
Selecionar esta opção leva você de volta ao painel exibido mais recentemente.

   ![](media/service-basic-concepts/version-new.png)

### <a name="8-options"></a>8. **Opções**
Esta área do espaço de trabalho contém ícones para interagir com o painel.  Além de **Adicionar bloco**, **Favorito** e **Compartilhar**, selecionar as reticências revela opções para duplicar, imprimir e atualizar o dashboard e muito mais.

   ![](media/service-basic-concepts/options.png)

## <a name="next-steps"></a>Próximas etapas
[Introdução ao Power BI](service-get-started.md)  
[Vídeos do Power BI](videos.md)  
[Power BI Premium – o que é?](service-premium.md)

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](http://community.powerbi.com/)

