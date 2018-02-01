---
title: Streaming em tempo real no Power BI
description: Obtenha o fluxo de dados em tempo real e elementos visuais no Power BI
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
ms.openlocfilehash: faf31ead10ce2d0374f99e8bfa1b27378c0c3ebb
ms.sourcegitcommit: 7249ff35c73adc2d25f2e12bc0147afa1f31c232
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/25/2018
---
# <a name="real-time-streaming-in-power-bi"></a>Streaming em tempo real no Power BI
Com o streaming em tempo real do Power BI, você pode transmitir dados e atualizar painéis em tempo real. Qualquer visual ou painel que possa ser criado no Power BI também pode ser criado para exibir e atualizar dados e visuais em tempo real. Os dispositivos e fontes de fluxo de dados podem ser sensores de fábrica, fontes de mídia social, métricas de uso do serviço e tudo o mais de que dados sensíveis ao tempo possam ser coletados ou transmitidos.

![](media/service-real-time-streaming/real-time-streaming_10.jpg)

Este artigo mostra como configurar um conjunto de dados de streaming em tempo real no Power BI. Mas antes disso, é importante entender os tipos de conjuntos de dados em tempo real que são projetados para exibição em blocos (e dashboards), e como esses conjuntos de dados se diferem.

## <a name="types-of-real-time-datasets"></a>Tipos de conjuntos de dados em tempo real
Há três tipos de conjuntos de dados em tempo real que são projetados para exibição em dashboards em tempo real:

* Conjunto de dados de push
* Conjunto de dados de streaming
* Conjunto de dados de streaming do PubNub

Primeiro vamos entender como esses conjuntos de dados são diferentes uns dos outros (nesta seção) e, em seguida, discutiremos como enviar dados por push a cada um desses conjuntos de dados.

### <a name="push-dataset"></a>Conjunto de dados de push
Com um **conjunto de dados de push**, os dados são enviados por push ao serviço do Power BI. Quando o conjunto de dados é criado, o serviço do Power BI cria automaticamente um novo banco de dados no serviço para armazenar os dados. Como há um banco de dados subjacente que continua a armazenar os dados conforme eles chegam, os relatórios podem ser criados com os dados. Esses relatórios e seus visuais são exatamente como qualquer outro visual de relatório, o que significa que você pode usar todos os recursos de criação de relatórios do Power BI para criar visuais, incluindo visuais personalizados, alertas de dados, blocos de dashboard fixados e muito mais.

Depois que um relatório for criado usando o conjunto de dados de push, qualquer um de seus visuais poderá ser fixado em um dashboard. Nesse dashboard, os visuais serão atualizados em tempo real, sempre que os dados forem atualizados. Dentro do serviço, o dashboard dispara uma atualização de bloco sempre que novos dados são recebidos.

Há duas considerações a serem observadas a respeito de blocos fixados de um conjunto de dados de push:

* A fixação de um relatório inteiro usando a opção *Fixar esta Página em Tempo Real* **não** resultará na atualização automática dos dados.
* Quando um visual é fixado em um dashboard, você pode usar **P e R** para fazer perguntas sobre o conjunto de dados de push em idioma natural. Depois de fazer uma consulta de **P e R**, você pode fixar o visual resultante de volta no dashboard e ele *também* será atualizado em tempo real.

### <a name="streaming-dataset"></a>Conjunto de dados de streaming
Com um **conjunto de dados de streaming**, os dados também são enviados por push ao serviço do Power BI, com uma diferença importante: o Power BI só armazena os dados em um cache temporário, que expira rapidamente. O cache temporário só é usado para exibir visuais que tenham algum sentido de histórico transitório, como um gráfico de linhas que tem uma janela de tempo de uma hora.

Com um **conjunto de dados de streaming**, *não* há banco de dados subjacente, portanto você *não pode* criar visuais de relatório usando os dados que fluem do fluxo. Assim, você não pode fazer uso de funcionalidades de relatório como filtragem, visuais personalizados e outras funções de relatório.

A única maneira de visualizar um conjunto de dados de streaming é adicionar um bloco e usar o conjunto de dados de streaming como uma fonte de dados de **dados streaming personalizados**. Os blocos de streaming personalizados com base em um **conjunto de dados de streaming** são otimizados para exibir rapidamente os dados em tempo real. Há baixíssima latência entre o momento em que os dados são enviados por push ao serviço do Power BI e quando o visual é atualizado, pois não há necessidade dos dados serem inseridos ou lidos em um banco de dados.

Na prática, os conjuntos de dados de streaming e os visuais de streaming que o acompanham são melhor utilizados em situações em que é crítico minimizar a latência entre quando os dados são enviados por push e quando eles são visualizados. Além disso, é recomendável que os dados sejam enviados por push em um formato em que possam ser visualizados no estado em que se encontram, sem nenhuma agregação adicional. Exemplos de dados que estão prontos no estado em que se encontram incluem temperaturas e médias pré-calculadas.

### <a name="pubnub-streaming-dataset"></a>Conjunto de dados de streaming do PubNub
Com um conjunto de dados de streaming do **PubNub**, o cliente Web do Power BI usa o SDK do PubNub para ler um fluxo de dados PubNub existente e nenhum dado é armazenado pelo serviço do Power BI.

Assim como acontece com o **conjunto de dados de streaming**, no **conjunto de dados de streaming do PubNub** não há banco de dados subjacente no Power BI, portanto você não pode criar visuais de relatório com os dados que entram, e não pode aproveitar as funcionalidades de relatório, como visuais personalizados, filtragem e assim por diante. Sendo assim, o **conjunto de dados de streaming do PubNub** só pode ser visualizado adicionando um bloco ao dashboard e configurando um fluxo de dados do PubNub como a origem.

Os blocos com base em um **conjunto de dados de streaming do PubNub** são otimizados para exibir rapidamente os dados em tempo real. Como o Power BI é conectado diretamente ao fluxo de dados do PubNub, há baixíssima latência entre o momento em que os dados são enviados por push ao serviço do Power BI e quando o visual é atualizado.

### <a name="streaming-dataset-matrix"></a>Matriz de conjunto de dados de streaming
A seguinte tabela (ou matriz, se desejar) descreve os três tipos de conjuntos de dados de streaming em tempo real e lista os recursos e limitações de cada uma delas.

![](media/service-real-time-streaming/real-time-streaming_11.png)

> [!NOTE]
> Consulte [esse artigo do MSDN](https://msdn.microsoft.com/library/dn950053.aspx) para obter informações sobre limites de **Push** em relação à quantidade de dados que pode ser enviada por push.
> 
> 

## <a name="pushing-data-to-datasets"></a>Enviar dados por push para conjuntos de dados
A seção anterior descreveu os três principais tipos de conjuntos de dados em tempo real que você pode usar no streaming em tempo real e as diferenças entre eles. Esta seção descreve como criar e enviar dados por push para esses conjuntos de dados.

Há três formas principais de enviar dados por push para um conjunto de dados:

* Usando as APIs REST do Power BI
* Usando a interface do usuário do conjunto de dados de streaming
* Usando o Stream Analytics do Azure

Vamos dar uma olhada em cada uma dessas abordagens.

### <a name="using-power-bi-rest-apis-to-push-data"></a>Usando APIs REST do Power BI para enviar dados por push
As **APIs REST do Power BI** podem ser usadas para criar e enviar dados para conjuntos de dados de **push** e para conjuntos de dados de **streaming**. Ao criar um conjunto de dados usando APIs REST do Power BI, o sinalizador *defaultMode* especifica se o conjunto de dados é de push ou de streaming. Se o sinalizador *defaultMode* não for definido, o conjunto de dados será definido como de **push** por padrão.

Se o valor *defaultMode* for definido como *pushStreaming*, o conjunto de dados será de **push** *e* de **streaming**, oferecendo os benefícios de ambos os tipos de conjunto de dados. O [artigo de API REST para **Criar conjunto de dados**](https://msdn.microsoft.com/library/mt203562.aspx) demonstra a criação de um conjunto de dados de streaming e mostra o sinalizador *defaultMode* em ação.

> [!NOTE]
> Ao usar conjuntos de dados com o sinalizador *defaultMode* definido como *pushStreaming*, se uma solicitação exceder a restrição de tamanho de 15 Kb para um conjunto de dados de **streaming**, mas for menor do que a restrição de tamanho de 16 MB de um conjunto de dados de **push**, a solicitação será bem-sucedida e os dados serão atualizados no conjunto de dados de push. No entanto, os blocos de streaming sofrerão falha temporária.
> 
> 

Depois de criar um conjunto de dados, use as APIs REST para enviar dados por push usando a [API **Adicionar linhas**](https://msdn.microsoft.com/library/mt203561.aspx), como [demonstrados neste artigo](https://msdn.microsoft.com/library/mt203561.aspx).

Todas as solicitações para as APIs REST são protegidas usando o **OAuth do Azure AD**.

### <a name="using-the-streaming-dataset-ui-to-push-data"></a>Usando a interface do usuário do conjunto de dados de streaming para enviar dados por push
No serviço do Power BI, é possível criar um conjunto de dados selecionando a abordagem de **API** conforme mostrado na imagem a seguir.

![](media/service-real-time-streaming/real-time-streaming_0b.png)

Ao criar o novo conjunto de dados de streaming, você pode optar por habilitar a **Análise de dados histórica** conforme mostrado abaixo, o que terá um impacto significativo.

![](media/service-real-time-streaming/real-time-streaming_0c.png)

Quando a **Análise de dados histórica** é desabilitada (ela é desabilitada por padrão), você cria um **conjunto de dados de streaming** conforme descrito anteriormente neste artigo. Quando a **Análise de dados histórica** é *habilitada*, o conjunto de dados criado torna-se um **conjunto de dados de streaming** e um **conjunto de dados de push**. Isso é equivalente a usar as APIs REST do Power BI para criar um conjunto de dados com o *defaultMode* definido como *pushStreaming*, conforme descrito anteriormente neste artigo.

> [!NOTE]
> Para conjuntos de dados de streaming criados usando a interface do usuário do serviço do Power BI, como descrito no parágrafo anterior, a autenticação do Azure AD não é necessária. Nesses conjuntos de dados, o proprietário do conjunto de dados recebe uma URL com uma rowkey, que autoriza o solicitante a enviar dados por push para o conjunto de dados sem usar um token de portador OAuth do Azure AD. Entenda, no entanto, que a abordagem do AAD (Azure AD) ainda funciona para enviar dados por push para o conjunto de dados.
> 
> 

### <a name="using-azure-stream-analytics-to-push-data"></a>Usando o Stream Analytics do Azure para enviar dados por push
Você pode adicionar o Power BI como uma saída no ASA (**Stream Analytics do Azure**) e, em seguida, visualizar esses fluxos de dados no serviço do Power BI em tempo real. Esta seção descreve os detalhes técnicos de como esse processo ocorre.

O Stream Analytics do Azure usa as APIs REST do Power BI para criar o fluxo de dados de saída no Power BI com o *defaultMode* definido como *pushStreaming* (consulte as seções anteriores deste artigo para obter informações sobre o *defaultMode*), o que resulta em um conjunto de dados que pode aproveitar tanto o **push** quanto o **streaming**. Durante a criação do conjunto de dados, o Stream Analytics do Azure também define o sinalizador **retentionPolicy* como *basicFIFO*. Com essa configuração, o banco de dados que dá suporte ao conjunto de dados de push armazena 200.000 linhas e, depois que esse limite é atingido, as linhas são descartadas à maneira PEPS (primeiro a entrar, primeiro a sair).

> [!CAUTION]
> Se a consulta do Azure Stream Analytics resultar em saída muito rápida para o Power BI (por exemplo, uma ou duas vezes por segundo), o Azure Stream Analytics fará envio em lote dessas saídas em uma única solicitação. Isso pode fazer com que o tamanho da solicitação exceda o limite do bloco de streaming. Nesse caso, como mencionado nas seções anteriores, os blocos de streaming falharão ao renderizar. Nesses casos, a prática recomendada é diminuir a taxa de saída de dados para o Power BI. Por exemplo, em vez de um valor máximo a cada segundo, defina a taxa de saída como um valor máximo durante 10 segundos.
> 
> 

## <a name="set-up-your-real-time-streaming-dataset-in-power-bi"></a>Configure seu conjunto de dados de streaming em tempo real no Power BI
Agora que abordamos os três principais tipos de conjuntos de dados para streaming em tempo real e as três maneiras principais que você pode usar para enviar dados por push a um conjunto de dados, vamos colocar seu conjunto de dados de streaming em tempo real para funcionar no Power BI.

Para iniciar a transmissão em tempo real, você precisará escolher uma das duas maneiras em que o fluxo de dados pode ser consumido no Power BI:

* **blocos** com visuais de fluxo de dados
* **conjuntos de dados** criados a partir de fluxos de dados que persistem no Power BI

Com qualquer opção, você precisará configurar **Fluxo de dados** no Power BI. Para fazer isso, no painel (um painel existente ou um novo) selecione **Adicionar um bloco** e, em seguida, selecione **Fluxo de dados personalizado**.

![](media/service-real-time-streaming/real-time-streaming_1.png)

Se você não tiver o fluxo de dados configurado ainda, não se preocupe – você pode selecionar **Gerenciar dados** para começar.

![](media/service-real-time-streaming/real-time-streaming_2.png)

Nessa página, você pode inserir o ponto de extremidade do seu conjunto de dados de streaming se já tiver um criado (na caixa de texto). Se você ainda não tiver um conjunto de dados de streaming, selecione o ícone de adição ( **+** ) no canto superior direito para ver as opções disponíveis para criar um conjunto de dados de streaming.

![](media/service-real-time-streaming/real-time-streaming_3.png)

Ao clicar no ícone **+**, você verá duas opções:

![](media/service-real-time-streaming/real-time-streaming_4a.png)

A próxima seção descreve essas opções e fornece mais informações sobre como criar um **bloco** de streaming ou como criar um **conjunto de dados** a partir da fonte de fluxo de dados, que você pode usar mais tarde para criar relatórios.

## <a name="create-your-streaming-dataset-with-the-option-you-like-best"></a>Crie o conjunto de dados de streaming com a opção que você gostar mais
Há duas maneiras de criar um feed de fluxo de dados em tempo real que pode ser consumido e visualizado pelo Power BI:

* **API REST do Power BI** usando um ponto de extremidade de streaming em tempo real
* **PubNub**

As seções a seguir examinarão cada opção sucessivamente.

### <a name="using-the-power-bi-rest-api"></a>Usando a API REST do Power BI
**API REST do Power BI** - Foram desenvolvidas melhorias recentes no API REST do Power BI para tornar o streaming em tempo real mais fácil para os desenvolvedores. Ao selecionar **API** na janela **Novo conjunto de dados de streaming**, você terá que fornecer entradas que habilitarão o Power BI a conectar e usar o seu ponto de extremidade:

![](media/service-real-time-streaming/real-time-streaming_5.png)

Se quiser que o Power BI armazene os dados enviados por meio desse fluxo de dados, habilite *Análise de dados históricos* e você poderá fazer a emissão de relatórios e análises dos fluxos de dados coletados. Você também pode [Saber mais sobre a API](https://msdn.microsoft.com/library/dn877544.aspx).

Após criar com sucesso o seu fluxo de dados, você receberá um ponto de extremidade de URL da API REST, que o seu aplicativo poderá convocar usando solicitações de *POST* para enviar seus dados ao conjunto de dados do **fluxo de dados** do Power BI que você criou.

Ao fazer solicitações *POST*, você deve garantir que o corpo da solicitação corresponda ao JSON de exemplo fornecido pela interface do usuário do Power BI. Por exemplo, encapsule os objetos JSON em uma matriz.

### <a name="using-pubnub"></a>Usando o PubNub
Com a integração do streaming **PubNub** com o Power BI, você poderá usar seus fluxos de dados de baixa latência **PubNub** (ou criar novos) e usá-los no Power BI. Ao selecionar **PubNub** e, em seguida, **Próximo**, você verá a seguinte janela:

![](media/service-real-time-streaming/real-time-streaming_7.png)

> [!WARNING]
> Canais de PubNub podem ser protegidos usando uma chave de autenticação do PAM (Gerenciador de acesso do PubNub). Essa chave será compartilhada com todos os usuários que têm acesso ao painel. Você pode [obter mais informações sobre o controle de acesso do PubNub](https://www.pubnub.com/docs/web-javascript/pam-security).
> 
> 

Os fluxos de dados **PubNub** costumam estar em grande volume e nem sempre são adequados para armazenamento e análise histórica em sua forma original. Para usar o Power BI para a análise histórica de dados PubNub, você terá que agregar o fluxo PubNub bruto e enviá-lo para o Power BI. Uma maneira de fazer isso é com o [Stream Analytics do Azure](https://azure.microsoft.com/services/stream-analytics/).

## <a name="example-of-using-real-time-streaming-in-power-bi"></a>Exemplo de uso de streaming em tempo real no Power BI
Aqui está um exemplo rápido de como funciona o streaming em tempo real no Power BI. Você pode prosseguir com este exemplo para experimentar o valor do streaming em tempo real.

Neste exemplo, usamos um fluxo disponível publicamente do **PubNub**. Aqui estão as etapas para fazer isso:

1. No **serviço do Power BI**, selecione um painel (ou crie um novo) e selecione **Adicionar bloco** > **Fluxo de Dados Personalizado** e, em seguida, selecione o botão **Próximo**.
   
   ![](media/service-real-time-streaming/real-time-streaming_1.png)
2. Se você ainda não tiver fontes de fluxos de dados, selecione o link **Gerenciar dados** (logo acima do botão **Próximo**), em seguida, selecione **+ Adicionar fluxo de dados** do link no canto superior direito da janela. Selecione **PubNub** e, em seguida, **Próximo**.
3. Crie um nome para o conjunto de dados, em seguida, cole os seguintes valores na janela que aparecerá, depois selecione **Próximo**:
   
   *Chave de assinatura:*
   
       sub-c-5f1b7c8e-fbee-11e3-aa40-02ee2ddab7fe
   *Canal:*
   
       pubnub-sensor-network
   
   ![](media/service-real-time-streaming/real-time-streaming_8.png)
4. Na janela seguinte, apenas selecione os padrões (que são preenchidos automaticamente) e depois selecione **Criar**.
   
   ![](media/service-real-time-streaming/real-time-streaming_9.png)
5. De volta ao seu espaço de trabalho no Power BI, crie um novo painel e, em seguida, adicione um bloco (consulte acima para ver as etapas, se necessário). Dessa vez, quando você criar um bloco e selecionar **Fluxo de Dados Personalizado**, terá um conjunto de fluxos de dados para trabalhar. Vá em frente e brinque com ele. Ao adicionar os campos *número* para os gráficos de linhas e, em seguida, adicionar outros blocos, você poderá obter um painel em tempo real que é semelhante ao seguinte:
   
   ![](media/service-real-time-streaming/real-time-streaming_10.jpg)

Experimente e brinque com o exemplo de conjunto de dados. Depois crie seus próprios conjuntos de dados e transmita dados dinâmicos ao Power BI.

## <a name="questions-and-answers"></a>Perguntas e respostas
Aqui estão algumas perguntas e respostas comuns sobre o streaming em tempo real no Power BI.

#### <a name="can-i-use-filters-on-push-dataset-how-about-streaming-dataset"></a>Posso usar filtros em conjuntos de dados de push? E nos conjuntos de dados de streaming?
Infelizmente, os conjuntos de dados de streaming não dão suporte à filtragem. Para conjuntos de dados de push, você pode criar um relatório, filtrar o relatório e, em seguida, fixar os visuais filtrados em um dashboard. No entanto, não há como alterar o filtro no visual quando ele está no dashboard.

Você pode fixar o bloco de relatório em tempo real no dashboard de forma separada e, nesse caso, você pode alterar os filtros. No entanto, os blocos de relatório em tempo real não serão atualizados em tempo real conforme os dados são enviados. Será necessário atualizar manualmente o visual, usando a opção *Atualizar os blocos de painel* do menu **Mais**.

Ao aplicar filtros para enviar conjuntos de dados por push com campos *DateTime* com precisão de milissegundos, não há suporte para operadores de *equivalência*. No entanto, operadores como maior que (>) ou menor que (<) funcionam corretamente.

#### <a name="how-do-i-see-the-latest-value-on-a-push-dataset-how-about-streaming-dataset"></a>Como faço para ver o valor mais recente em um conjunto de dados de push? E nos conjuntos de dados de streaming?
Os conjuntos de dados de streaming são projetados para exibir os dados mais recentes. Você pode usar o visual de streaming **Cartão** para visualizar facilmente os valores numéricos mais recentes. Infelizmente, o cartão não dá suporte a dados do tipo *DateTime* ou *Text*.
Para conjuntos de dados de push, supondo que você tenha um carimbo de data/hora no esquema, você pode tentar criar um visual de relatório com o último filtro N.

#### <a name="can-i-connect-to-push-or-streaming-datasets-in-power-bi-desktop"></a>Posso conectar conjuntos de dados de push ou de streaming no Power BI Desktop?
Infelizmente, isso não está disponível no momento.

#### <a name="given-the-previous-question-how-can-i-do-any-modeling-on-real-time-datasets"></a>Dada a pergunta anterior, como posso fazer qualquer modelagem em conjuntos de dados em tempo real?
A modelagem não é possível em um conjunto de dados de streaming, pois os dados não são armazenados permanentemente. Para um conjunto de dados de push, você pode usar as APIs REST de atualizar conjunto de dados/tabela para adicionar medidas e relações. Você pode obter mais informações no [artigo Atualizar esquema da tabela](https://msdn.microsoft.com/library/mt203560.aspx) e no [artigo Propriedades do conjunto de dados](https://msdn.microsoft.com/library/mt742155.aspx).

#### <a name="how-can-i-clear-all-the-values-on-a-push-dataset-how-about-streaming-dataset"></a>Como faço para limpar todos os valores em um conjunto de dados de push? E nos conjuntos de dados de streaming?
Em um conjunto de dados de push, você pode usar a chamada à API REST excluir linhas. Você também pode usar essa ferramenta útil separadamente, que é um wrapper em torno das APIs REST. Atualmente não há nenhuma maneira para limpar os dados de um conjunto de dados de streaming, embora os dados vão se auto limpar após uma hora.

#### <a name="i-set-up-an-azure-stream-analytics-output-to-power-bi-but-i-dont-see-it-appearing-in-power-bi--whats-wrong"></a>Eu configurei uma saída do Stream Analytics do Azure para o Power BI, mas não a vejo aparecer no Power BI. O que está errado?
Aqui está uma lista de verificação que você pode usar para solucionar o problema:

1. Reinicie o trabalho do Stream Analytics do Azure (trabalhos criados antes da versão GA do streaming necessitarão reiniciar)
2. Tente autorizar novamente a conexão do Power BI no Stream Analytics do Azure
3. Qual espaço de trabalho você especificou na saída do Stream Analytics do Azure? Você verificando nesse (mesmo) espaço de trabalho no serviço do Power BI?
4. A consulta do Stream Analytics do Azure gera saída explicitamente na saída do Power BI? (usando a palavra-chave INTO)
5. O trabalho do Stream Analytics do Azure tem dados fluindo através dele? O conjunto de dados será criado somente quando houver dados sendo transmitidos.
6. Você pode verificar os logs do Stream Analytics do Azure para ver se há erros ou avisos?

## <a name="next-steps"></a>Próximas etapas
Aqui estão alguns links que podem ser úteis ao trabalhar com o streaming em tempo real no Power BI:

* [Visão geral da API REST do Power BI com os dados em tempo real](https://msdn.microsoft.com/library/dn877544.aspx)
* [Limitações da API REST do Power BI](https://msdn.microsoft.com/library/dn950053.aspx)
* [Artigo da API REST para **Criar conjunto de dados**](https://msdn.microsoft.com/library/mt203562.aspx)
* [API REST **Adicionar linhas** do Power BI](https://msdn.microsoft.com/library/mt203561.aspx)
* [Stream Analytics do Azure](https://azure.microsoft.com/services/stream-analytics/)

