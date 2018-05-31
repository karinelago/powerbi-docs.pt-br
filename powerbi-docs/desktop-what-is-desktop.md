---
title: O que é o Power BI Desktop?
description: Saiba o que é o Power BI Desktop e como começar a usá-lo
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: overview
ms.date: 12/06/2017
ms.author: davidi
LocalizationGroup: Get started
ms.openlocfilehash: be29d5879ef62ab3d7fcef271e61337a0d2fb050
ms.sourcegitcommit: 638de55f996d177063561b36d95c8c71ea7af3ed
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/17/2018
ms.locfileid: "34289178"
---
# <a name="what-is-power-bi-desktop"></a>O que é o Power BI Desktop?

O **Power BI Desktop** é um aplicativo gratuito que você pode instalar no computador local e que permite que você se conecte, transforme e visualize seus dados. Com o **Power BI Desktop**, você pode se conectar a várias fontes de dados diferentes e combiná-las (geralmente chamado de modelagem) em um modelo de dados que possibilita criar elementos gráficos e conjuntos de visuais que podem ser compartilhados como relatórios com outras pessoas dentro da sua organização. A maioria dos usuários que trabalham em projetos de Business Intelligence usam o **Power BI Desktop** para criar relatórios e, em seguida, usam o **serviço do Power BI** para compartilhar seus relatórios com outras pessoas.

![Power BI Desktop](media/desktop-what-is-desktop/what-is-desktop_01.png)

Os usos mais comuns para o **Power BI Desktop** são os seguintes:

* Conectar-se a dados
* Transformar e limpar esses dados para criar um modelo de dados
* Criar visuais, como gráficos, que fornecem representações visuais dos dados
* Criar relatórios que são conjuntos de visuais em uma ou mais páginas do relatório
* Compartilhar relatórios com outras pessoas usando o **serviço do Power BI**

As pessoas responsáveis por essas tarefas geralmente são consideradas *analistas de dados* (às vezes, chamados de *analistas*) ou profissionais de Business Intelligence (conhecidos como *criadores de relatórios*). No entanto, muitas pessoas que não se consideram analistas ou criadores de relatórios usam o **Power BI Desktop** para criar relatórios atraentes ou extrair dados de várias fontes e criar modelos de dados, que podem compartilhar com seus colegas de trabalho e organizações.

Com o **Power BI Desktop**, é possível criar relatórios complexos e visualmente avançados, usando dados de várias fontes, tudo em um relatório que você pode compartilhar com outras pessoas em sua organização. 

## <a name="connect-to-data"></a>Conectar-se a dados
Para começar a usar o **Power BI Desktop**, a primeira etapa é conectar-se aos dados. Há vários tipos diferentes de fontes de dados aos quais você pode se conectar com o **Power BI Desktop**. Para se conectar a dados, basta selecionar **Início**, **Obter Dados > Mais** na faixa de opções. A imagem a seguir mostra a janela **Obter Dados** exibindo as muitas categorias às quais o Power BI Desktop pode se conectar.

![Obter Dados no Power BI Desktop](media/desktop-what-is-desktop/what-is-desktop_02.png)

Quando você seleciona um tipo de dados, o sistema solicita informações, como a URL e as credenciais, necessárias para o Power BI Desktop se conectar à fonte de dados em seu nome.

![Conectar-se a um banco de dados SQL Server no Power BI Desktop](media/desktop-what-is-desktop/what-is-desktop_03.png)

Depois que você se conectar a uma ou mais fontes de dados, convém transformar os dados para que sejam úteis para você.

## <a name="transform-and-clean-data-create-a-model"></a>Transformar e limpar os dados, criar um modelo

No Power BI Desktop, você pode limpar e transformar dados usando o **Editor de Consultas** interno. Com o Editor de Consultas, é possível fazer alterações nos dados, como alterar um tipo de dados, remover colunas ou combinar dados de várias fontes. É como esculpir: você pode começar com um grande bloco de argila (ou dados), depois remover partes ou adicionar outras conforme o necessário, até que a forma dos dados fique como você deseja. 

![Editor de Consultas no Power BI Desktop](media/desktop-getting-started/designer_gsg_editquery.png)

Cada etapa que você realiza na transformação de dados (como renomear uma tabela, transformar um tipo de dados ou excluir colunas) é registrada pelo **Editor de Consultas**. Sempre que essa consulta se conectar à fonte de dados, essas etapas serão executadas para que os dados sejam sempre formatados da maneira especificada.

A imagem a seguir mostra o painel **Config. Consulta** para uma consulta que foi formatada e transformada em um modelo.

 ![](media/desktop-getting-started/shapecombine_querysettingsfinished.png)

Depois que os dados estiverem como você desejar, é possível criar visuais. 

## <a name="create-visuals"></a>Criar visuais 

Quando você tiver um modelo de dados, poderá arrastar *campos* para a tela do relatório para criar *visuais*. Um *visual* é uma representação gráfica dos dados em seu modelo. O visual a seguir mostra um gráfico de colunas simples. 

![Um visual no Power BI Desktop](media/desktop-what-is-desktop/what-is-desktop_04.png)

Há muitos tipos diferentes de visuais para escolher no Power BI Desktop. Para criar ou alterar um visual, basta selecionar o ícone visual do painel **Visualizações**. Se você tiver um visual selecionado na tela do relatório, ele é alterado para o tipo selecionado. Se nenhum visual for selecionado, um novo visual será criado com base na sua seleção.

![O painel Visualizações no Power BI Desktop](media/desktop-what-is-desktop/what-is-desktop_05.png)

## <a name="create-reports"></a>Criar relatórios

Com frequência, você desejará criar uma coleção de visuais que mostram vários aspectos dos dados que você usou para criar o modelo no Power BI Desktop. Um conjunto de visuais em um arquivo do Power BI Desktop é chamado de *relatório*. Um relatório pode ter uma ou mais páginas, assim como um arquivo do Excel pode ter uma ou mais planilhas. Na imagem a seguir, você vê a primeira página de um relatório do Power BI Desktop, chamada de Visão geral (você pode ver a guia na parte inferior da imagem). Neste relatório, há dez páginas.

![Relatório do Power BI Desktop com dez páginas](media/desktop-what-is-desktop/what-is-desktop_01.png)

## <a name="share-reports"></a>Compartilhar relatórios

Quando um relatório estiver pronto para compartilhar com outras pessoas, você pode **Publicar** o relatório para o **serviço do Power BI** e torná-lo disponível para qualquer pessoa em sua organização que tenha uma licença do Power BI. Para publicar um relatório do Power BI Desktop, você seleciona o botão **Publicar** na faixa de opções **Início** no Power BI Desktop.

![Publicar um relatório por meio do Power BI Desktop](media/desktop-what-is-desktop/what-is-desktop_06.png)

Depois de selecionar **Publicar**, o Power BI Desktop conecta-se ao **serviço do Power BI** usando sua conta do Power BI e, em seguida, solicita que você selecione onde no serviço do Power BI você deseja compartilhar o relatório, como seu espaço de trabalho, um espaço de trabalho de equipe ou algum outro local no serviço do Power BI. Você deve ter uma licença do Power BI para compartilhar relatórios para o serviço do Power BI.


## <a name="next-steps"></a>Próximas etapas

Para começar a usar o **Power BI Desktop**, primeiro baixe e instale o aplicativo. Há duas maneiras de obter o **Power BI Desktop**:

* [Baixar o Power BI Desktop pela Web](desktop-get-the-desktop.md)
* [Obter o Power BI Desktop por meio da Windows Store](http://aka.ms/pbidesktopstore)
