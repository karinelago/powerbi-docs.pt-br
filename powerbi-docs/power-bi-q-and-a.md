---
title: Visão geral de P e R no serviço do Power BI e Power BI Desktop
description: Tópico de visão geral da documentação para consultas de linguagem naturais de P e R do Power BI.
author: mihart
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 01/18/2018
ms.author: mihart
LocalizationGroup: Ask questions of your data
ms.openlocfilehash: a1d39d10982f1d598ffce7e978c1b030e0a442d4
ms.sourcegitcommit: 638de55f996d177063561b36d95c8c71ea7af3ed
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/17/2018
---
# <a name="qa-in-power-bi-service-and-power-bi-desktop"></a>P e R no serviço do Power BI e Power BI Desktop
## <a name="what-is-qa"></a>O que é P e R?
Às vezes, a maneira mais rápida de obter uma resposta de seus dados é fazer uma pergunta usando o idioma natural. Por exemplo, "qual foi o total de vendas no ano passado".  Use P e R para explorar seus dados do Excel usando recursos intuitivos em idioma natural e receba as respostas na forma de quadros e gráficos. P e R é diferente de um mecanismo de pesquisa - P e R fornece apenas resultados sobre os dados no Power BI.

Este artigo é ponto de partida para tudo que envolve P e R. Selecione um link abaixo para saber como a P e R funciona no serviço do Power BI (relatórios e dashboards), Power BI Desktop (relatórios), Power BI Embedded e Power BI Mobile.  

> [!NOTE]
> A **P e R do Power BI** só dá suporte a responder consultas em linguagem natural perguntadas em inglês. Você também pode testar um recurso em versão prévia para perguntas feitas em espanhol. Em **Power BI Desktop**, vá até **Arquivo**, **Opções e configurações**, **Opções** e procure a guia **Recursos em Versão Prévia**. Marque a caixa para **Suporte ao idioma espanhol para P e R**.  
>
>

![](media/power-bi-q-and-a/pbi_qa_boxsalessqft.png)

A pergunta é apenas o começo.  Divirta-se viajando através de seus dados refinando ou expandindo sua pergunta, revelando informações novas de confiança, concentrando-se em detalhes e diminuindo o zoom para uma exibição mais ampla. Você vai se deliciar com as ideias e descobertas feitas.

A experiência é verdadeiramente interativa... e rápida! Equipada com um armazenamento na memória, a resposta é quase instantânea.

##  <a name="qa-for-consumers"></a>P e R para *consumidores*
Quando um colega compartilhar um dashboard com você, você encontrará a caixa de perguntas no dashboard de P e R no serviço do Power BI (app.powerbi.com), na parte inferior do dashboard no Power BI Mobile e acima da visualização no Power BI Embedded. A menos que o proprietário tenha lhe concedido permissões de edição, você poderá usar P e R para explorar dados, mas não poderá salvar nenhuma visualização criada com a P e R.

![](media/power-bi-q-and-a/powerbi-qna.png)

## <a name="qa-for-creators"></a>P e R para *criadores*
Se você for um *criador* de relatórios do Power BI ou tiver permissões de edição para um conjunto de dados, você encontrará a caixa de perguntas de P e R no dashboard no serviço do Power BI e em cada página de relatório, no serviço do Power BI e no Power BI Desktop. Qualquer visualização que você criar usando P e R poderá ser salva em um dashboard e salva em um relatório.

![](media/power-bi-q-and-a/power-bi-desktop.png)

Além de usar p e r para explorar seus dados, criadores e proprietários de conjuntos de dados podem melhorar a experiência de P e R para os consumidores [modificando seus conjuntos de dados](service-prepare-data-for-q-and-a.md), adicionando [perguntas em destaque](service-q-and-a-create-featured-questions.md) e [habilitando e desabilitando P e R](service-q-and-a-direct-query.md) para conjuntos de dados de conexão dinâmica locais. Em [Cenários inseridos](developer/qanda.md), os desenvolvedores podem optar entre 2 modos: **interativo** e **apenas resultado**.

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


## <a name="for-more-details-about-power-bi-qa"></a>Para obter mais detalhes sobre P e R do Power BI
[Visão geral: como usar a P e R em relatórios e dashboards do Power BI](power-bi-tutorial-q-and-a.md): instruções passo a passo para usar a P e R e uma visão geral de como tudo funciona.

[Aplicativo móvel do Microsoft Power BI](mobile-apps-ios-qna.md) para iOS em dispositivos iPod Touch, iPhones e iPads.

[Microsoft Power BI Embedded](developer/qanda.md) Incorporar P e R em um aplicativo.

[Dicas para fazer perguntas no P e R](service-q-and-a-tips.md): saiba como se comunicar com o P e R para obter os melhores resultados possíveis.

[Adicione perguntas em destaque aos conjuntos de dados](service-q-and-a-create-featured-questions.md) e P e R sugerirá essas perguntas para seus colegas.

[Habilitar P e R para seus conjuntos de dados locais](service-q-and-a-direct-query.md) Se você precisar que um gateway se conecte ao conjunto de dados, use as configurações do Power BI para ativar e desativar P e R.

[Tutorial: usar a P e R do Power BI com o exemplo de Vendas de Varejo no serviço do Power BI](power-bi-visualization-introduction-to-q-and-a.md): use a P e R em um tutorial realístico do setor.

[Faça seus dados funcionarem bem com o P e R](service-prepare-data-for-q-and-a.md): você é a pessoa que cria conjuntos de dados e modelos de dados?  Então este tópico é para você.

Mais perguntas? [Experimente a Comunidade do Power BI](http://community.powerbi.com/)
