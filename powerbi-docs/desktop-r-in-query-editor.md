---
title: Usando o R no Editor de Consultas do Power BI
description: "Uso do R no Editor de Consultas do Power BI Desktop para análise avançada"
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
ms.date: 10/12/2017
ms.author: davidi
ms.openlocfilehash: c48e7042f16ac43619a7a0a6708a54f0575d795f
ms.sourcegitcommit: f2b38777ca74c28f81b25e2f739e4835a0ffa75d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/17/2017
---
# <a name="using-r-in-query-editor"></a>Uso de R no Editor de Consultas
Você pode usar **R**, uma linguagem de programação amplamente usada por estatísticos, cientistas de dados e analistas de dados, no **Editor de Consultas** do Power BI Desktop. Essa integração de R ao **Editor de Consultas** permite executar a limpeza de dados usando R e executar análise e modelagem de dados avançadas em conjuntos de dados, inclusive completar dados ausentes, fazer previsões e clustering, apenas para citar alguns exemplos. **R** é uma linguagem poderosa e pode ser usada no **Editor de Consultas** para preparar seu modelo de dados e criar relatórios.

## <a name="installing-r"></a>Instalando o R
Para usar **R** no **Editor de Consultas** do Power BI Desktop, você precisa instalar **R** no computador local. É possível baixar e instalar o **R** gratuitamente em vários locais, incluindo a [página de download do Revolution Open](https://mran.revolutionanalytics.com/download/) e o [Repositório CRAN](https://cran.r-project.org/bin/windows/base/).

## <a name="using-r-in-query-editor"></a>Uso de R no Editor de Consultas
Para mostrar como usar **R** no **Editor de consultas**, usaremos um exemplo de um conjunto de dados do mercado de ações, com base em um arquivo .CSV que você pode [baixar aqui](http://download.microsoft.com/download/F/8/A/F8AA9DC9-8545-4AAE-9305-27AD1D01DC03/EuStockMarkets_NA.csv) para acompanhar o exemplo. As etapas deste exemplo são as seguintes:

1. Primeiro, carregue os dados no **Power BI Desktop**. No exemplo, carregaremos o arquivo *EuStockMarkets_NA.csv*. Selecione **Obter Dados > CSV** na faixa de opções **Início** no **Power BI Desktop**.
   
   ![](media/desktop-r-in-query-editor/r-in-query-editor_1.png)
2. Selecione o arquivo e selecione **Abrir**. O CSV será exibido na caixa de diálogo **Arquivo CSV**.
   
   ![](media/desktop-r-in-query-editor/r-in-query-editor_2.png)
3. Depois que os dados forem carregados, você os verá no painel **Campos** no Power BI Desktop.
   
   ![](media/desktop-r-in-query-editor/r-in-query-editor_3.png)
4. Abra o **Editor de Consultas** selecionando **Editar Consultas** na guia **Início** do **Power BI Desktop**.
   
   ![](media/desktop-r-in-query-editor/r-in-query-editor_4.png)
5. Na guia **Transformar**, selecione **Executar Script R**, e o editor **Executar Script R** será exibido (mostrado na próxima etapa). Observe que as linhas 15 e 20 têm dados ausentes, assim como outras linhas que você não pode ver na imagem a seguir. As etapas a seguir mostram como R pode (e vai) completar essas linhas para você.
   
   ![](media/desktop-r-in-query-editor/r-in-query-editor_5d.png)
6. Para este exemplo, vamos inserir o seguinte código de script:
   
       library(mice)
       tempData <- mice(dataset,m=1,maxit=50,meth='pmm',seed=100)
       completedData <- complete(tempData,1)
       output <- dataset
       output$completedValues <- completedData$"SMI missing values"
   
   > [!NOTE]
   > Instale a biblioteca *mice* em seu ambiente R para que o código do script anterior funcione corretamente. Para instalar mice, execute o seguinte em sua instalação de R: |      > install.packages('mice')
   > 
   > 
   
   Quando colocado na caixa de diálogo **Executar Script R**, o código é semelhante ao seguinte:
   
   ![](media/desktop-r-in-query-editor/r-in-query-editor_5b.png)
7. Quando selecionarmos **OK**, o **Editor de Consultas** exibirá um aviso sobre a privacidade dos dados.
   
   ![](media/desktop-r-in-query-editor/r-in-query-editor_6.png)
8. Para que os scripts de R funcionem corretamente no serviço do Power BI, todas as fontes de dados precisam ser definidas como *públicas*. Para obter mais informações sobre as configurações de privacidade e suas implicações, confira [Níveis de privacidade](desktop-privacy-levels.md).
   
   ![](media/desktop-r-in-query-editor/r-in-query-editor_7.png)
   
   Em seguida, vemos uma nova coluna em **Campos**, chamada *completedValues*. Observe que há alguns elementos de dados ausentes, como nas linhas 15 e 18. Veremos como R lida com isso na próxima seção.
   

Com apenas cinco linhas de script R, o **Editor de Consultas** preencheu os valores ausentes com um modelo preditivo.

## <a name="creating-visuals-from-r-script-data"></a>Criar elementos visuais com base em dados de script R
Agora, podemos criar um elemento visual para ver como o código de script R usando a biblioteca *mice* preencheu os valores ausentes, conforme mostrado na imagem a seguir.

![](media/desktop-r-in-query-editor/r-in-query-editor_8a.png)

Quando esse elemento visual for concluído, assim como outros elementos visuais que talvez desejemos criar usando o **Power BI Desktop**, poderemos salvar o arquivo do **Power BI Desktop** (que é salvo como um arquivo .pbix) e, em seguida, usar o modelo de dados, inclusive os scripts R que fazem parte dele, no serviço do Power BI.

> [!NOTE]
> Quer ver um arquivo .pbix concluído com essas etapas concluídas? Você está com sorte: pode baixar o arquivo concluído do **Power BI Desktop** usado nesses exemplos [aqui](http://download.microsoft.com/download/F/8/A/F8AA9DC9-8545-4AAE-9305-27AD1D01DC03/Complete Values with R in PQ.pbix).
> 
> 

Depois que você carregar o arquivo .pbix no serviço do Power BI, algumas etapas serão necessárias para habilitar a atualização de dados (no serviço) e habilitar os elementos visuais para serem atualizados no serviço (os dados precisam acessar R para que os elementos visuais sejam atualizados). As etapas adicionais são as seguintes:

* **Habilitar atualização agendada para o conjunto de dados** - para habilitar a atualização agendada para a pasta de trabalho que contém o conjunto de dados com scripts R, confira [Configurar a atualização agendada](refresh-scheduled-refresh.md), que também inclui informações sobre o **Gateway Pessoal**.
* **Instale o Gateway Pessoal** - você precisa de um **Gateway Pessoal** instalado no computador em que o arquivo está localizado e R está instalado. O serviço do Power BI deve acessar essa pasta de trabalho e renderizar novamente qualquer elemento visual atualizado. Você pode obter mais informações sobre como [Instalar e configurar o Gateway Pessoal](personal-gateway.md).

## <a name="limitations"></a>Limitações
Existem algumas limitações para consultas que incluem scripts R criados no **Editor de Consultas**:

* Todas as configurações de fonte de dados R devem ser definidas como *Públicas*, e todas as outras etapas em uma consulta criada no **Editor de Consultas** também devem ser públicas. Para obter as configurações de fonte de dados, no **Power BI Desktop**, selecione **Arquivo > Opções e configurações > Configurações de fonte de dados**.
  
  ![](media/desktop-r-in-query-editor/r-in-query-editor_9.png)
  
  Na caixa de diálogo **Configurações de Fonte de Dados**, selecione a fontes de dados, selecione **Editar Permissões...** e verifique se o **Nível de Privacidade** está definido como *Público*.
  
  ![](media/desktop-r-in-query-editor/r-in-query-editor_10.png)    
* Para habilitar a atualização agendada do conjunto de dados ou dos elementos visuais R, você precisa habilitar a **Atualização agendada** e ter um **Gateway Pessoal** instalado no computador que hospeda a pasta de trabalho e a instalação de R. Para obter mais informações sobre ambos, confira a seção anterior deste artigo, que fornece links, para saber mais sobre cada um.

Há inúmeras coisas que você pode fazer com R e consultas personalizadas, então, explore e modele seus dados da maneira como deseja que eles sejam mostrados.

