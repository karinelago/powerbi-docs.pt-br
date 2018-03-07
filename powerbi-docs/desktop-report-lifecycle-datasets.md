---
title: "Conectar-se a conjuntos de dados no serviço do Power BI no Power BI Desktop"
description: "Use um conjunto comum de dados para vários relatórios do Power BI Desktop e gerencie o ciclo de vida dos seus relatórios"
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
ms.date: 01/24/2018
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: fff56b220579a19505337f2ac9697cd3e61e83cb
ms.sourcegitcommit: 88c8ba8dee4384ea7bff5cedcad67fce784d92b0
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/24/2018
---
# <a name="connect-to-datasets-in-the-power-bi-service-from-power-bi-desktop"></a>Conectar-se a conjuntos de dados no serviço do Power BI no Power BI Desktop
Você pode estabelecer uma conexão dinâmica a um conjunto de dados compartilhado no serviço do Power BI e criar vários relatórios diferentes com base no mesmo conjunto de dados. Isso significa que você pode criar seu modelo de dados perfeito no Power BI Desktop, publicá-lo no serviço do Power BI e, junto com outros usuários, criar vários relatórios diferentes (em arquivos .pbix distintos) utilizando o mesmo common data service. Esse recurso é chamado de **conexão dinâmica ao serviço do Power BI**.

![](media/desktop-report-lifecycle-datasets/report-lifecycle_01.png)

São inúmeras as vantagens encontradas nesse recurso, incluindo práticas recomendadas, que discutiremos ao longo deste artigo. Há também algumas considerações e limitações, portanto, certifique-se de ler todo o conteúdo relacionado, que está disponível no fim deste artigo.

## <a name="using-a-power-bi-service-live-connection-for-report-lifecycle-management"></a>Uso da conexão dinâmica ao serviço do Power BI para gerenciamento do ciclo de vida do relatório
Um desafio causado pela popularidade do Power BI é a proliferação de relatórios, dashboards e modelos de dados subjacentes. Eis o porquê: é fácil criar relatórios atraentes no **Power BI Desktop** e depois compartilhar ([publicar](desktop-upload-desktop-files.md)) esses relatórios no **serviço do Power BI**, bem como criar excelentes dashboards a partir dos conjuntos de dados. Visto que muitas pessoas estavam agindo dessa forma, usando com frequência os mesmos (ou quase os mesmos) conjuntos de dados, saber qual relatório se baseou em qual conjunto de dados (e o quão atual cada conjunto de dados é) tornou-se um desafio. A **conexão dinâmica ao serviço do Power BI** lida com esse desafio e torna mais fácil e consistente criar, compartilhar e expandir a partir de relatórios e dashboards de conjuntos de dados comuns.

### <a name="create-a-dataset-everyone-can-use-then-share-it"></a>Crie um conjunto de dados que todos possam usar e compartilhe-o
Digamos que Anna (uma analista de negócios) pertence à sua equipe e é ótima na criação de modelos de dados muito bem feitos (geralmente chamados de conjuntos de dados). Com sua competência, Anna pode criar conjuntos de dados e relatórios e compartilhar os relatórios no **serviço do Power BI**.

![](media/desktop-report-lifecycle-datasets/report-lifecycle_02a.png)

Todos adoram seus relatórios e conjuntos de dados, e é aí que o problema começa: cada membro do grupo tentará criar *sua própria versão* do conjunto de dados e depois compartilhar seus próprios relatórios com a equipe. De repente, surge uma infinidade de relatórios (de diferentes conjuntos de dados) no espaço de trabalho da equipe no **serviço do Power BI**. Qual deles é o mais recente? Os conjuntos de dados eram os mesmos ou quase os mesmos? Quais eram as diferenças? Com o recurso de **conexão dinâmica ao serviço do Power BI**, tudo isso pode mudar para melhor. Na próxima seção, veremos como os demais membros da equipe podem usar o conjunto de dados publicado de Anna em seus próprios relatórios e usar o mesmo conjunto de dados consistente, verificado e publicado para criar seus próprios relatórios exclusivos.

### <a name="connect-to-a-power-bi-service-dataset-using-a-live-connection"></a>Conectar-se a um conjunto de dados do serviço do Power BI usando uma conexão dinâmica
Depois de criar o relatório (e o conjunto de dados no qual se baseou), Anna o publica no **serviço do Power BI**, que será exibido no espaço de trabalho da sua equipe no serviço do Power BI. Agora o relatório está disponível para consulta e uso por qualquer pessoa no espaço de trabalho.

Outros membros do espaço de trabalho podem agora estabelecer uma conexão dinâmica com o modelo de dados compartilhado de Anna (usando o recurso de **conexão dinâmica ao serviço do Power BI**) e criar seus próprios relatórios exclusivos a partir do *conjunto de dados original*.

Na imagem a seguir, veja como Anna cria relatórios no **Power BI Desktop** e os publica (inclui o modelo de dados correspondente) no **serviço do Power BI**. A partir daí, os demais membros do espaço de trabalho poderão se conectar com o seu modelo de dados usando a **conexão dinâmica ao serviço do Power BI** e criar seus próprios relatórios exclusivos com base no conjunto de dados de Anna.

![](media/desktop-report-lifecycle-datasets/report-lifecycle_03.png)

> [!NOTE]
> Conjuntos de dados são compartilhados apenas em um espaço de trabalho. Para estabelecer uma conexão dinâmica ao serviço do Power BI, o conjunto de dados ao qual você se conecta deve estar em um espaço de trabalho compartilhado em que você é membro.
> 
> 

## <a name="step-by-step-for-using-the-power-bi-service-live-connection"></a>Passo a passo sobre como usar a conexão dinâmica ao serviço do Power BI
Agora que sabemos o quanto a **conexão dinâmica ao serviço do Power BI** é útil e como você pode usá-la como abordagem para práticas recomendadas de gerenciamento do ciclo de vida do relatório, vejamos as etapas necessárias para transformar os magníficos relatórios de Anna (e o conjunto de dados) em um conjunto de dados compartilhado que os seus colegas de espaço de trabalho do Power BI poderão usar.

### <a name="publish-a-power-bi-report-and-dataset"></a>Publicar um relatório do Power BI e o conjunto de dados
A primeira etapa do gerenciamento do ciclo de vida de relatórios usando uma **conexão dinâmica ao serviço do Power BI** é ter um relatório (e um conjunto de dados) que os colegas de equipe queiram usar. Sendo assim, Anna deve primeiro **publicar** seu relatório do **Power BI Destkop**. Para fazer isso, ela deve selecionar **Publicar** na faixa de opções **Início** no Power BI Desktop.

![](media/desktop-report-lifecycle-datasets/report-lifecycle_02a.png)

Se Anna não estiver conectada à sua conta de serviço do Power BI, ela será solicitada a fazê-lo.

![](media/desktop-report-lifecycle-datasets/report-lifecycle_04.png)

Após conectar-se, ela poderá escolher o destino no espaço de trabalho no qual o relatório e o conjunto de dados serão publicados. Lembre-se que somente membros com acesso ao espaço de trabalho no qual há relatórios publicados podem acessar seu conjunto de dados usando uma **conexão dinâmica ao serviço do Power BI**.

![](media/desktop-report-lifecycle-datasets/report-lifecycle_05.png)

O processo de publicação é iniciado, e o **Power BI Desktop** mostra o andamento.

![](media/desktop-report-lifecycle-datasets/report-lifecycle_06.png)

Concluído o processo, o **Power BI Desktop** mostrará o sucesso da publicação e fornecerá alguns links de acesso ao relatório propriamente dito no **serviço do Power BI**, bem como um link para acessar **Insights rápidos** no relatório.

![](media/desktop-report-lifecycle-datasets/report-lifecycle_07.png)

Em seguida, vejamos como os outros colegas de equipe com acesso ao espaço de trabalho onde o relatório (e o conjunto de dados) foi publicado podem se conectar ao conjunto de dados e criar seus próprios relatórios.

### <a name="establish-a-power-bi-service-live-connection-to-the-published-dataset"></a>Estabelecer uma conexão dinâmica ao serviço do Power BI com o conjunto de dados publicado
Para estabelecer uma conexão com o relatório publicado e criar seu próprio relatório com base no conjunto de dados publicado, selecione **Obter dados** na faixa de opções **Início** no **Power BI Desktop** e selecione **Serviço do Power BI**. É possível também selecioná-lo em **Obter dados > Serviços online > Serviço do Power BI**.

![](media/desktop-report-lifecycle-datasets/report-lifecycle_08.png)

Caso não tenha acessado ainda o Power BI, você será solicitado a fazê-lo. Após fazer logon, uma janela mostrará os espaços de trabalho dos quais você é membro, permitindo selecionar o espaço de trabalho que contém o conjunto de dados com o qual você deseja estabelecer uma **conexão dinâmica ao serviço do Power BI**.

O número entre colchetes ao lado do espaço de trabalho mostra quantos conjuntos de dados compartilhados estão disponíveis nesse grupo de trabalho; a seleção do triângulo à esquerda expande o espaço de trabalho, permitindo selecionar o conjunto de dados compartilhado.

![](media/desktop-report-lifecycle-datasets/report-lifecycle_09a.png)

Alguns itens existentes na janela anterior da conexão dinâmica ao **serviço do Power BI** merecem atenção:

* É possível pesquisar um conjunto de dados compartilhado, mas os resultados da pesquisa serão limitados aos itens expandidos e não incluirão nenhum espaço de trabalho ainda não expandido.
* Você pode expandir mais de um espaço de trabalho para expandir sua pesquisa.

Ao selecionar **Carregar** na janela, é estabelecida uma conexão dinâmica ao conjunto de dados selecionado, isto é, os dados visualizados (os campos e seus valores) são carregados no **Power BI Desktop** em tempo real.

![](media/desktop-report-lifecycle-datasets/report-lifecycle_10.png)

Agora, você (e os demais) podem criar relatórios personalizados e compartilhar todos eles a partir do mesmo conjunto de dados. Essa é uma excelente maneira de poder contar com uma pessoa experiente para criar um conjunto de dados bem estruturado (assim como Anna faz) e permitir que vários colegas de equipe utilizem o conjunto de dados compartilhado para criar seus próprios relatórios.

> [!NOTE]
> Quando você cria relatórios com base no conjunto de dados usando uma conexão dinâmica com o **serviço do Power BI**, só pode publicar o relatório no mesmo espaço de trabalho de serviço do Power BI que contém o conjunto de dados que está sendo usado.
> 
> 

## <a name="limitations-and-considerations"></a>Limitações e considerações
Ao usar a **conexão dinâmica ao serviço do Power BI**, há algumas limitações e considerações a serem observadas.

* Os membros somente leitura de um espaço de trabalho não podem se conectar a conjuntos de dados no **Power BI Desktop**.
* Somente os usuários pertencentes ao mesmo espaço de trabalho do **serviço do Power BI** podem se conectar ao conjunto de dados publicado usando a **conexão dinâmica ao serviço do Power BI**. Os usuários podem pertencer (e geralmente pertencem) a mais de um espaço de trabalho.
* Como essa é uma conexão dinâmica, a navegação à esquerda e a modelagem são desabilitadas; esse comportamento é semelhante a quando conectado ao **SQL Server Analysis Services**.
* Por se tratar de uma conexão dinâmica, a RLS (segurança em nível de linha e de função), o OneDrive for Business e outros comportamentos de conexão semelhantes são executados da mesma forma como quando conectado ao **SQL Server Analysis Services**.
* Ao selecionar a qual conjunto de dados se conectar no **serviço do Power BI**, a caixa de pesquisa é aplicável apenas a espaços de trabalho que foram expandidos.
* Se você modificar o arquivo .pbix original compartilhado, o conjunto de dados e o relatório compartilhado no **serviço do Power BI** serão substituídos.
* Você não pode substituir o relatório originalmente compartilhado. Tentar fazer isso resulta em um aviso solicitando que você renomeie o arquivo e o publique.
* Se você excluir o conjunto de dados compartilhado no **serviço do Power BI**, outros arquivos .pbix do **Power BI Desktop** não funcionarão corretamente nem exibirão seus elementos visuais.
* Para Pacotes de conteúdo, é necessário primeiro criar uma cópia do pacote de conteúdo antes de usá-lo como base para o compartilhamento de relatórios e conjuntos de dados .pbix no **serviço do Power BI**.
* Para pacotes de conteúdo da *Minha Organização*, uma vez copiados, não é possível substituir o relatório criado no serviço e/ou um relatório criado como parte da cópia de um pacote de conteúdo com uma conexão dinâmica. Tentar fazer isso resulta em um aviso solicitando que você renomeie o arquivo e o publique. Nessa situação, você pode substituir apenas relatórios conectados publicados dinamicamente.
* Quando você cria um relatório com base no conjunto de dados usando uma conexão dinâmica com o **serviço do Power BI**, só pode publicar o relatório no mesmo espaço de trabalho de serviço do Power BI que contém o conjunto de dados que está sendo usado.
* A exclusão de um conjunto de dados compartilhado no **serviço do Power BI** significa que você não pode mais acessar o conjunto de dados do **Power BI Desktop**.

