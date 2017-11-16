---
title: Como usar o P e R do Power BI
description: Como usar o P e R do Power BI
services: powerbi
documentationcenter: 
author: mihart
manager: kfile
editor: 
tags: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 09/25/2017
ms.author: mihart
ms.openlocfilehash: a6736916a4bb2e94c1f5e1e3c3c3e5339cf990ec
ms.sourcegitcommit: 99cc3b9cb615c2957dde6ca908a51238f129cebb
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/13/2017
---
# <a name="how-to-use-power-bi-qa"></a>Como usar o P e R do Power BI
## <a name="ask-questions-of-your-data-using-natural-language"></a>Faça perguntas de seus dados usando linguagem natural
Iniciar em um dashboard. Na caixa P e R você digitará sua pergunta usando a linguagem natural. P e R reconhece as palavras que você digita e descobre onde (o conjunto de dados) encontrar a resposta. P e R também ajuda a sua pergunta com preenchimento automático, ajuste e outros auxílios textuais e visuais.

![](media/service-how-to-q-and-a/powerbi-qna.png)

A resposta à sua pergunta é exibida como uma visualização interativa e atualizações como modificar a pergunta.

P e R é interativo e até mesmo divertido e, mais frequentemente do que o contrário, uma pergunta levará a muitas outras conforme as visualizações revelam caminhos interessantes para buscar. Veja Amanda demonstrando o uso de P e R para criar visuais, aprofundando-se nesses elementos visuais e fixando-os nos dashboards.

> [!NOTE]
> P e R também está disponível no [aplicativo do Microsoft Power BI para iOS nos dispositivos iPod Touch, iPhones e iPads](mobile-apps-ios-qna.md).
> 
> 

<iframe width="560" height="315" src="https://www.youtube.com/embed/qMf7OLJfCz8?list=PL1N57mwBHtN0JFoKSR0n-tBkUJHeMP2cP" frameborder="0" allowfullscreen></iframe>

## <a name="use-natural-language-to-ask-questions-about-your-data"></a>Usar linguagem natural para fazer perguntas sobre os dados
1. Coloque o cursor na caixa de pergunta. Mesmo antes de começar a digitar, a P e R exibe uma nova tela com sugestões para ajudá-lo a formar sua pergunta.
   
   ![](media/service-how-to-q-and-a/powerbi-qna-cursor.png)  
   
   Esta lista contém:  
   a.  as perguntas usadas para criar [blocos](service-dashboard-tiles.md) que já estão fixados no dashboard e  
   b.  o nome das tabelas no(s) [conjunto(s) de dados subjacente(s)](service-get-data.md).  
   
   Você sempre pode escolher uma dessas perguntas como ponto de partida e continuar a refinar a pergunta para encontrar a resposta específica que você está procurando. Ou use um nome de tabela para ajudá-lo com palavra em uma nova pergunta.
2. Selecione no menu suspenso ou comece a digitar sua própria pergunta.  
   
   ![](media/service-how-to-q-and-a/powerbi-qna-list.png)
3. Ao digitar uma pergunta, a P e R do Power BI escolhe a melhor [visualização](power-bi-visualization-types-for-reports-and-q-and-a.md) para exibir sua resposta; a visualização, por sua vez, muda dinamicamente conforme a pergunta é modificada. P e R também ajuda a formular sua pergunta com preenchimento automático reformulando sua pergunta e com outros recursos textuais e visuais.  
   ![](media/service-how-to-q-and-a/powerbi-qna-viz.png)
4. Quando você digita uma consulta, o Power BI procura uma resposta em qualquer conjunto de dados que tenha um bloco nesse painel.  Se todos os blocos forem do *conjuntodedadosA*, sua resposta será proveniente do *conjuntodedadosA*.  Se houver blocos do *datasetA* e do *datasetB*, a P e R pesquisará a melhor resposta nesses dois conjuntos de dados.
   
   > [!TIP]
   > Por isso, tenha cuidado. Se você tiver apenas um bloco do *datasetA* e removê-lo do dashboard, a P e R deixará de ter acesso ao *datasetA*.
   > 
   > 
5. Quando estiver satisfeito com o resultado, [fixe a visualização em um dashboard](service-dashboard-pin-tile-from-q-and-a.md) selecionando o ícone para fixar no canto superior direito. Se o dashboard tiver sido compartilhado com você ou for parte de um aplicativo, não será possível fixar.
   
   ![](media/service-how-to-q-and-a/pbi_qna_finish-typing-question.jpg)

### <a name="tell-qa-which-visualization-to-use"></a>Informe ao P e R qual visualização deve ser usada.
Com P e R, você pode não apenas solicitar seus dados para falarem por si mesmo, você também pode dizer como você deseja que seja exibido. Basta adicionar "como um <visualization type>" ao final da sua pergunta.  Por exemplo, "mostrar o volume de inventário pela fábrica como um mapa" e "mostrar inventário total como um cartão de crédito".  Experimente.

## <a name="how-does-qa-know-how-to-answer-questions"></a>Como o recurso de P e R sabe como responder a perguntas?
### <a name="which-datasets-does-qa-use"></a>Quais conjuntos de dados P e R usa?
Como o recurso de P e R sabe como responder a perguntas sobre dados específicos? Ele se baseia nos nomes das tabelas, colunas e campos calculados nos conjuntos subjacentes. Portanto, é importante que você (ou o proprietário do conjunto de dados) nomei as coisas! 

Por exemplo, suponha que você tenha uma tabela do Excel como o nome de "Vendas", com colunas intituladas "Produto", "Mês", "Unidades vendidas", "Vendas brutas" e "Lucro". Você pode fazer perguntas sobre qualquer uma dessas entidades.  Você poderia perguntar “mostrar as *vendas* ”, “*lucro* total por *mês* ”, “classificar *produtos* por *unidades vendidas* ” e muito mais.

Q & R pode responder a perguntas com base em como o conjunto de dados é organizado. Como isso funciona para dados de vendas? Quando você se conectar à sua conta do salesforce.com, o Power BI gera automaticamente um painel de controle.  Antes de começar a fazer perguntas com o P e R, dê uma olhada em dados exibidos nas visualizações do painel de controle e também os dados exibidos no menu suspenso de perguntas e respostas.

* Se os valores e os rótulos do eixo de visualizações incluírem “vendas”, “conta”, “mês” e “oportunidades”, será possível fazer perguntas como: “qual *conta* tem a *oportunidade* mais alta?” ou “mostrar *vendas* por mês como um gráfico de barras”.
* Se a lista suspensa inclui "vendedor", "estado" e "ano", você poderá fazer perguntas como: "qual *vendedor* teve as vendas mais *baixas* na *Flórida* em *2013*."

Se você tiver dados de desempenho do site na análise do Google, você pode perguntar ao P e R sobre o tempo gasto em uma página da Web, o número de visitas à página exclusivo e taxas de envolvimento do usuário. Ou, se você estiver consultando dados demográficos, você pode fazer perguntas sobre idade e renda doméstica por local.

### <a name="which-visualization-does-qa-use"></a>Qual visualização que faz perguntas e um uso?
Perguntas e respostas escolhe a melhor visualização com base nos dados que estão sendo exibidos. Às vezes, os dados no conjunto de dados subjacente são definidos como um determinado tipo ou categoria e isso ajuda a P e R saber como exibi-los. Por exemplo, se os dados são definidos como um tipo de data, é mais provável que sejam exibidos como um gráfico de linhas. Dados que são categorizados como uma cidade são mais prováveis de ser exibidos como um mapa.

Você também pode informar ao P e R a visualização que será usada, adicioná-la à sua pergunta. Mas tenha em mente que não será sempre possível exibir os dados no tipo de visualização que você solicitou.

Para obter informações sobre as palavras-chave reconhecidas pela P e R, confira [Dicas para fazer perguntas](service-q-and-a-tips.md).

## <a name="next-steps"></a>Próximas etapas
Voltar a [P e R no Power BI](service-q-and-a.md)  
[Tutorial: Usar perguntas e respostas com o exemplo de Vendas de varejo](power-bi-visualization-introduction-to-q-and-a.md)  
[Dicas para fazer perguntas nas Perguntas e respostas](service-q-and-a-tips.md)  
[Preparar uma pasta de trabalho para Perguntas e respostas](service-prepare-data-for-q-and-a.md)  
[Fixar um bloco ao dashboard de Perguntas e respostas](service-dashboard-pin-tile-from-q-and-a.md)  

