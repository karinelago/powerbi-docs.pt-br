---
title: "Serviço do Power BI - conceitos básicos"
description: "Espaços de trabalho, painéis, relatórios, conjunto de dados e pastas de trabalho do Power BI."
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
ms.date: 01/20/2018
ms.author: mihart
LocalizationGroup: Get started
ms.openlocfilehash: f0f296f402bf1c2bcb1b12e11bd2998bfeec5bc5
ms.sourcegitcommit: 88c8ba8dee4384ea7bff5cedcad67fce784d92b0
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/24/2018
---
# <a name="power-bi---basic-concepts-for-power-bi-service"></a>Power BI – conceitos básicos do serviço do Power BI

Este artigo presume que você já [se inscreveu no serviço do Power BI](service-self-service-signup-for-power-bi.md) e [adicionou alguns dados](service-get-data.md).

Ao abrir o serviço do Power BI, você verá um ***dashboard***. Dashboards são uma coisa que diferencia o serviço do Power BI de Power BI Desktop.

![](media/service-basic-concepts/completenewest.png)

Os principais recursos da sua interface do usuário de serviço do Power BI são os seguintes:

1. painel de navegação (nav esq)
2. telas (neste caso, painel com blocos)
3. caixa de perguntas de P e R
4. botões de ícone, incluindo ajuda e comentários
5. bloco do painel (caminho de navegação, também trilhas)
6. Iniciador do aplicativo do Office 365
7. Botão Página inicial do Power BI
8. Botões de ícone rotulados

Nos aprofundaremos nesses itens mais tarde, mas primeiro vamos examinar alguns conceitos do Power BI.

Ou, talvez você queira assistir a este vídeo primeiro antes de ler o restante deste artigo.  Nesse vídeo, Will examina os conceitos básicos e oferece um tour pelo serviço do Power BI.

<iframe width="560" height="315" src="https://www.youtube.com/embed/B2vd4MQrz4M" frameborder="0" allowfullscreen></iframe>


## <a name="power-bi-concepts"></a>Conceitos do Power BI
Os quatro maiores blocos de construção do Power BI são: ***painéis***, ***relatórios***, ***pastas de trabalho*** e ***conjuntos de dados***. E eles ficam todos organizados em ***pastas de trabalho***. É importante entender os espaços de trabalho antes de nos aprofundarmos nos quatro blocos de construção, então, vamos começar com essa parte. 

## <a name="workspaces"></a>Espaços de trabalho
Espaços de trabalho são contêineres para painéis, relatórios, pastas de trabalho e conjunto de dados no Power BI. Há dois tipos de espaços de trabalho: **Meu Espaço de Trabalho* e espaços de trabalho do aplicativo. Então, o que é um *aplicativo*? Um *aplicativo* do Power BI é uma coleção de painéis e relatórios para entregar métricas-chave para sua organização. Aplicativos são interativos, mas não podem ser editados 

- *Meu Espaço de Trabalho* é o espaços de trabalho para qualquer cliente do Power BI trabalhar com seu conteúdo. Apenas você tem acesso ao Meu Espaço de Trabalho pertencente a você. Caso queira compartilhar algum dos seus conteúdos, você tem várias opções: criar um espaço de trabalho do aplicativo no qual você agrupa conteúdos em um *aplicativo* e o torne disponível para outros na sua organização ou criar um espaço de trabalho do aplicativo e permitir o acesso de seus colegas a ele para que vocês possam compartilhar e colaborar.     
-  *Espaços de trabalho do aplicativo* são usados para colaborar e compartilhar conteúdo com colegas. Eles também são os locais nos quais você cria, publica e gerencia aplicativos para sua organização. Imagine-os como áreas de preparo e contêineres para o conteúdo que vai formar um aplicativo do Power BI. Você pode adicionar colegas aos seus espaços de trabalho do aplicativo e colaborar em painéis, relatórios, pastas de trabalho e conjunto de dados. Todos os membros do espaço de trabalho do aplicativo precisam ter licenças do Power BI Pro, mas clientes do aplicativo (os colegas que têm acesso aos aplicativos) não necessariamente precisam de licenças Pro.  

Para saber mais, consulte a seção **Compartilhar seu trabalho** do Sumário, começando com [Como eu devo colaborar e compartilhar painéis e relatórios](service-how-to-collaborate-distribute-dashboards-reports.md)


Agora voltemos aos blocos de construção do Power BI. Você não pode ter painéis ou relatórios sem dados (bem, você até pode ter painéis vazios e relatórios vazios, mas eles não são muito úteis até que tenham dados), então vamos começar com os **conjuntos de dados**.

## <a name="datasets"></a>Conjuntos de dados
Um *conjunto de dados* é uma coleção de dados que você *importa* ou a que *se conecta*. O Power BI permite que você se conecte a todos os tipos de conjuntos de dados, os importe e os reúna em um único lugar.  

Conjuntos de dados estão associados aos *espaços de trabalho*, e um conjunto de dados exclusivo pode ser parte de muitos espaços de trabalho. Ao abrir um espaço de trabalho, os conjuntos de dados associados estarão listados na guia **Conjuntos de Dados**. Cada conjunto de dados listado representa uma fonte de dados única, por exemplo, uma planilha do Excel no OneDrive, um conjunto de dados de tabela SSAS local ou um conjunto de dados do Salesforce. Há várias diferentes fontes de dados com suporte, e sempre estamos adicionando novas. [Veja a lista de tipos de conjunto de dados que podem ser usados com o Power BI](service-get-data.md).

No exemplo abaixo, selecionamos o espaço de trabalho do aplicativo “Vendas e marketing” e clicamos na guia para **Conjuntos de dados**.

![](media/service-basic-concepts/power-bi-datasets.png)

**UM** conjunto de dados...

* pode ser usado repetidamente em um ou mais espaços de trabalho.
* pode ser usado em vários relatórios diferentes.
* Visualizações desse único conjunto de dados podem ser exibidas em vários painéis diferentes.
  
  ![](media/service-basic-concepts/drawing2.png)

Para [conectar-se a um conjunto de dados ou importá-lo](service-get-data.md), selecione **Obter Dados** (na parte inferior da navegação esquerda) ou selecione **+ Criar > Conjunto de dados** (no canto superior direito). Siga as instruções para se conectar à fonte específica ou importá-la e depois adicionar o conjunto de dados ao espaço de trabalho ativo. Novos conjuntos de dados ficam marcados com um asterisco amarelo. O trabalho que você realiza no Power BI não altera o conjunto de dados subjacente.

Se você fizer [parte de um ***espaço de trabalho do aplicativo***](service-collaborate-power-bi-workspace.md), os conjuntos de dados adicionados por um membro do espaço de trabalho estarão disponíveis para os outros membros do espaço de trabalho.

Conjuntos de dados podem ser atualizados, renomeados, explorados e removidos. Use um conjunto de dados para criar um relatório do zero ou executando [insights rápidos](service-insights.md).  Para ver quais relatórios e painéis já estão usando um conjunto de dados, selecione **Exibição relacionada**. Para explorar um conjunto de dados, selecione-o. O que você está fazendo é abrir o conjunto de dados no editor de relatórios, onde pode de fato começar a se aprofundar nos dados e criar visualizações. Então, vamos passar para o próximo tópico – relatórios.

### <a name="dig-deeper"></a>Mergulhe mais fundo
* [Power BI Premium – o que é?](service-premium.md)
* [Obter dados para o Power BI](service-get-data.md)
* [Conjuntos de dados de amostra para o Power BI](sample-datasets.md)

## <a name="reports"></a>Relatórios
Um relatório do Power BI é uma ou mais páginas de visualizações (quadros e gráficos como gráficos de linhas, gráficos de pizza, mapas de árvore e muito outros). As visualizações também são chamadas de ***visuais***. Todas as visualizações em um relatório vêm de um único conjunto de dados. Relatórios podem ser criados do zero dentro do Power BI, podem ser importados com painéis que colegas compartilharam com você ou podem ser criados quando você se conectar a conjuntos de dados a partir do Excel, Power BI Desktop, banco de dados, aplicativos SaaS e [aplicativos](service-get-data.md).  Por exemplo, quando você se conecta a uma pasta de trabalho do Excel que contém planilhas do Power View, o Power BI cria um relatório baseado nessas planilhas. E quando você se conecta a um aplicativo SaaS, o Power BI importa um relatório pré-criado.

Há dois modos de exibir relatórios e interagir com eles: [modo de exibição de Leitura e modo de exibição de Edição](service-reading-view-and-editing-view.md).  Somente a pessoa que criou o relatório, co-proprietários e pessoas com permissão têm acesso a todos a todos os recursos de exploração, criação e compartilhamento de recursos do ***Modo de Exibição de Edição*** para esse relatório. E as pessoas com quem eles compartilharem o relatório podem explorar e interagir com o relatório usando o ***Modo de Exibição de Leitura***.   

Ao abrir um espaço de trabalho, os relatórios associados ficam listados na guia **Relatórios**. Cada relatório listado representa uma ou mais páginas de visualizações baseadas em apenas um conjunto de dados subjacente. Para abrir um relatório, basta selecioná-lo. 

Ao abrir um aplicativo, você verá um painel.  Para acessar um relatório subjacente, selecione um bloco do painel (falaremos mais sobre isso depois) que foi fixado em um relatório. Lembre-se de que nem todos os blocos são fixados em relatórios, então, talvez seja preciso clicar em alguns blocos para encontrar um relatório. 

Por padrão, o relatório abre em Modo de Exibição de Leitura.  Basta selecionar **Editar relatório** para abri-lo no Modo de Exibição de Edição (caso tenha as permissões necessárias). 

No exemplo abaixo, selecionamos o aplicativo de espaço de trabalho “Vendas e marketing” e clicamos na guia **Relatórios**.

![](media/service-basic-concepts/power-bi-reports.png)

**UM** relatório...

* está contido em um único espaço de trabalho
* pode ser associado com vários painéis dentro desse espaço de trabalho (blocos fixados a partir desse relatório podem aparecer em diversos painéis).
* pode ser criado usando os dados de um conjunto de dados. (a pequena exceção é que o Power BI Desktop pode combinar mais de um conjunto de dados em um único relatório que pode, por sua vez, ser importado para o Power BI)
  
  ![](media/service-basic-concepts/drawing3new.png)

### <a name="dig-deeper"></a>Mergulhe mais fundo
* [Relatórios no serviço do Power BI e Power BI Desktop](service-reports.md)
* [Relatórios em aplicativos móveis no Power BI](mobile-reports-in-the-mobile-apps.md)

## <a name="dashboards"></a>Painéis
Um *painel* é algo que você cria **no serviço do Power BI** ou algo que um colega cria **no serviço do Power BI** e compartilha com você. Trata-se de uma única tela, que contém nenhum ou mais blocos e widgets. Cada bloco fixado em um relatório ou uma [P e R](power-bi-q-and-a.md) exibe uma única [visualização](power-bi-report-visualizations.md) que foi criada a partir de um conjunto de dados e fixado ao painel. Páginas inteiras do relatório também podem ser fixadas a um painel como um bloco único. Há várias maneiras de adicionar blocos ao seu painel; muitas maneiras para serem abordadas neste tópico de visão geral. Para saber mais, veja [Blocos do painel no Power BI](service-dashboard-tiles.md). 

Por que as pessoas criam painéis?  Aqui estão apenas alguns dos motivos:

* para ver rapidamente todas as informações necessárias para tomar decisões
* para monitorar as informações mais importantes sobre seus negócios
* para garantir que todos os colegas estejam na mesma página, visualizando e usando as mesmas informações
* para monitorar a integridade uma empresa, produto, unidade de negócios, campanha de marketing, etc.
* para criar uma exibição personalizada de um painel maior – todas as métricas que importam para você

Ao abrir um espaço de trabalho, os painéis associados ficam listados na guia **Painéis**. Para abrir um painel, basta selecioná-lo. Ao abrir um aplicativo, você verá um painel.  Cada painel representa uma exibição personalizada de algum subconjunto dos conjuntos de dados subjacentes.  Se você possui seu próprio painel, também será preciso editar o acesso aos conjuntos de dados e relatórios subjacentes.  Caso o painel tenha sido compartilhado com você, será possível interagir com ele e quaisquer relatórios subjacentes, mas não será possível salvar quaisquer alterações.

Há muitas maneiras diferentes para você ou um colega [compartilhar um painel](service-share-dashboards.md). É preciso ter o Power BI Pro para compartilhar um painel e pode ser necessário para exibir um painel compartilhado.


> [!NOTE]
> A fixação e os blocos são abordados com mais detalhes abaixo, sob o título "Dashboard com blocos".
> 

**UM** painel...

* está associado a um único espaço de trabalho
* pode exibir visualizações de vários conjuntos de dados diferentes
* pode exibir visualizações de vários relatórios diferentes
* pode exibir visualizações fixadas de outras ferramentas (por exemplo, Excel)
  
  ![](media/service-basic-concepts/drawing1.png)

### <a name="dig-deeper"></a>Mergulhe mais fundo
* [Criar um novo painel em branco e obter alguns dados](service-dashboard-create.md)
* [Duplicar um painel](service-dashboard-copy.md) 
* [Criar um modo de exibição de telefone de um painel](service-create-dashboard-mobile-phone-view.md)


## <a name="workbooks"></a>Pastas de Trabalho
Pastas de Trabalho são um tipo especial de conjunto de dados. Se você leu a seção **Conjuntos de dados** anterior, já deve saber praticamente tudo de que precisa sobre pastas de trabalho. Mas você deve estar se perguntando porque algumas vezes o Power BI classifica uma pasta de trabalho do Excel como um **Conjunto de dados** e outras vezes como uma **Pasta de trabalho**. 

Ao usar o **Obter dados** com arquivos de Excel, você tem a opção de *Importar* ou *Conectar-se* ao arquivo. Ao escolher Conectar-se, sua pasta de trabalho vai aparecer no Power BI assim como apareceria no Excel Online. Mas, ao contrário do Excel Online, você terá alguns ótimos recursos para ajudá-lo a fixar elementos de suas planilhas diretamente nos dashboards.

Não é possível editar a pasta de trabalho no Power BI. No entanto, se precisar fazer alterações, clique em Editar e escolha a opção para editar a pasta de trabalho no Excel Online ou abri-la no Excel em seu computador. Todas as alterações feitas são salvas na pasta de trabalho no OneDrive.

### <a name="dig-deeper"></a>Mergulhe mais fundo
* [Obter dados de arquivos de pasta de trabalho do Excel](service-excel-workbook-files.md)
* [Publicar no Power BI com o Excel](service-publish-from-excel.md)


## <a name="my-workspace"></a>Meu Espaço de Trabalho
Nós falamos sobre espaços de trabalho e blocos de construção. Vamos ver novamente a interface do Power BI e revisar as peças que formam a página inicial do serviço do Power BI.

![](media/service-basic-concepts/completenewest.png)

### <a name="1-navigation-pane-left-nav"></a>1. **Painel de navegação** (nav esq)
Use o painel de navegação para localizar e se mover entre os espaços de trabalho e os blocos de construção do Power BI: painéis, relatórios, pastas de trabalho e conjuntos de dados.  

  ![](media/service-basic-concepts/power-bi-navigation.png)

* Selecione **Obter Dados** para [adicionar conjuntos de dados, relatórios e dashboards ao Power BI](service-get-data.md).
* Expanda e recolha a barra de navegação com este ícone ![](media/service-basic-concepts/expand-icon.png).
* Abra ou gerencie seu conteúdo favorito selecionando **Favoritos**.
* Exiba e abra o conteúdo visitado mais recentemente selecionando **Recente**.
* Exiba, abra ou exclua um aplicativo selecionando **Aplicativos**.
* Algum colega compartilhou um conteúdo com você? Selecione **Compartilhado comigo** para pesquisar e classificar esse conteúdo para encontrar aquilo de que precisa.
* Exiba e abra suas pastas de trabalho selecionando **Pastas de trabalho**.

Clique uma vez em

* um ícone ou cabeçalho para abrir a exibição de conteúdo
* uma seta à direita (>) para abrir um menu do submenu para Favoritos, Recentes e Espaços de trabalho. 
* um ícone de divisa () para exibir a lista rolável de painéis, relatórios, pastas de trabalho e conjuntos de dados do **Meu Espaço de Trabalho**.
* um conjunto de dados para explorá-lo

### <a name="2-canvas"></a>2. **Telas** 
Como abrimos um painel, a área de telas exibe blocos de visualização. Se, por exemplo, nós tivéssemos aberto o editor de relatório, a área de telas exibiria uma página de relatório. 

Os painéis são compostos por [blocos](service-dashboard-tiles.md).  Blocos são criados no Modo de Exibição de Edição de relatório, P e R e outros painéis e podem ser fixados no Excel, SSRS e outros. Um tipo especial de bloco chamado de [widget](service-dashboard-add-widget.md) é adicionado diretamente ao painel. Os blocos que aparecem em um painel foram especificamente inseridos ali pelo criador/proprietário de um relatório.  O ato de adicionar um bloco em um painel é chamado *fixação*.

![Telas de painel do Power BI](media/service-basic-concepts/canvas.png)

Para obter mais informações, consulte **Dashboards** (acima).

### <a name="3-qa-question-box"></a>3. **Caixa de perguntas de P e R**
Uma maneira de explorar seus dados é fazer uma pergunta e deixar que o P e R do Power BI lhe forneça uma resposta, na forma de uma visualização. O P e R pode ser usado para adicionar conteúdo a um painel ou relatório.

O P e R procura uma resposta no conjunto(s) de dados conectado ao painel.  Um conjunto de dados conectado é aquele que tem pelo menos um bloco anexado a esse painel.

![caixa de perguntas de P e R](media/service-basic-concepts/power-bi-qna.png)

Assim que você começa a digitar sua pergunta, o P e R leva você até a página de P e R. Conforme você digita, o P e R ajuda você a fazer a pergunta certa e encontrar a melhor resposta com reformulações, preenchimento automático, sugestões e muito mais. Quando você encontrar uma visualização (resposta) de que gosta, fixe-a em seu painel. Para obter mais informações, veja [P e R no Power BI](power-bi-q-and-a.md).

### <a name="4-icon-buttons"></a>4. **Botões de ícone** 
Os ícones no canto superior direito são seus recursos para configurações, notificações, downloads, obter ajuda e fornecer comentários à equipe do Power BI. Selecione a seta dupla para abrir o dashboard no modo **Tela inteira**.  

![botões de ícone](media/service-basic-concepts/power-bi-icons.png)

### <a name="5-dashboard-title-navigation-path-aka-breadcrumbs"></a>5. **Bloco do dashboard** (caminho de navegação, também trilhas)
Nem sempre é fácil descobrir quais espaços de trabalho e painéis estão ativos, por isso, o Power BI cria um caminho de navegação para você.  Neste exemplo, vemos o espaço de trabalho (Meu espaço de trabalho) e o bloco do painel (Exemplo de Análise de Varejo).  Se abrimos um relatório, o nome dele seria acrescentado ao final do caminho de navegação.  Cada seção do caminho é um hiperlink ativo.  

Observe o ícone “C” após o bloco do painel. Esse painel tem uma [marca de classificação de dados](service-data-classification.md) do tipo “confidencial”. A marca identifica o nível de confidencialidade e segurança dos dados. Se o Administrador ativou a classificação de dados, todo painel terá uma definição de marca padrão. Os proprietários de painéis devem mudar a marca para corresponder com o nível de segurança adequado do painel.

![](media/service-basic-concepts/power-bi-title.png)

### <a name="6-office-365-app-launcher"></a>6. **Iniciador do aplicativo do Office 365**
Com o iniciador de aplicativos, todos os aplicativos do Office 365 ficam facilmente disponíveis a um clique. A partir daqui, você pode iniciar rapidamente seus emails, documentos, calendários e muito mais. 

![Iniciador de aplicativo do Office](media/service-basic-concepts/power-bi-waffle.png)

### <a name="7-power-bi-home"></a>7. **Página inicial do Power BI**
Ao selecioná-la, um [painel em destaque](service-dashboard-featured.md) (caso tenha definido um) é aberto, caso contrário, é aberto o último painel exibido.

   ![](media/service-basic-concepts/version-new.png)

### <a name="8-labeled-icon-buttons"></a>8. **Botões de ícone rotulados**
Essa área da tela contém opções adicionais para interagir com o conteúdo (neste caso, com o painel).  Além dos ícones rotulados que ficam visíveis, ao selecionar as reticências, são reveladas opções para duplicar, imprimir, atualizar o painel e muito mais.

   ![](media/service-basic-concepts/power-bi-labeled-icons.png)

## <a name="next-steps"></a>Próximas etapas
[Introdução ao Power BI](service-get-started.md)  
[Navegação: como explorar o serviço do Power BI](service-the-new-power-bi-experience.md)
[Vídeos do Power BI](videos.md)  
[Editor de relatório - faça um tour](service-the-report-editor-take-a-tour.md)

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](http://community.powerbi.com/)

