---
title: Dicas e truques para fazer perguntas com a P e R no Power BI
description: Dicas e truques para fazer perguntas com a P e R no Power BI
services: powerbi
documentationcenter: 
author: mihart
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
ms.date: 01/18/2018
ms.author: jastru
ms.openlocfilehash: 5d9b65448fced78bf3eb4ed02c84e1561d2d209a
ms.sourcegitcommit: d803e85bb0569f6b357ba0586f5702c20d27dac4
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/19/2018
---
# <a name="tips-for-asking-questions-in-power-bi-qa"></a>Dicas para fazer perguntas na P e R do Power BI
## <a name="words-and-terminology-that-qa-recognizes"></a>Palavras e terminologia reconhecida pela P e R
Esta lista de palavras-chave não é completa.  A melhor maneira de ver se o Power BI reconhece uma palavra-chave é testá-la digitando-a na caixa de perguntas.  Se a palavra ou o termo estiver esmaecido, o Power BI não o reconhecerá ou não o reconhecerá no contexto atual.

A lista abaixo usa o presente do indicativo, mas, na maioria dos casos, todos os tempos verbais são reconhecidos. Por exemplo, “é” inclui são, foi, foram, será, têm, tem, tinha, terá, fazem, faz e fez.  Além disso, “classifica” inclui classificado e classificação.  Além disso, o Power BI reconhece e inclui as versões singular e plural de uma palavra. Por exemplo, o Power BI reconhece “ano” e “anos”.

> [!NOTE]
> P e R também está disponível no [aplicativo do Microsoft Power BI para iOS nos dispositivos iPod Touch, iPhones e iPads](mobile-apps-ios-qna.md).
> 
> 

Se você for o proprietário de um conjunto de dados, adicione frases e sinônimos para melhorar os resultados de P e R para os seus clientes.

**Agregações**: total, soma, quantidade, número, quantidade, contagem, média, o mais, o menos, menor, maior, o menor, o mais alto, o maior, máximo, máx, o melhor, o menor, o mais baixo, mínimo, mín

**Artigos**: um, uma, uns, umas, a(s), o(s)

**Em branco e Booliano**: em branco, vazio, nulo, prefixado com “não”, cadeia de caracteres vazia, texto vazio, verdadeiro, v, falso, f

**Comparações**: vs, versus, comparado a, em comparação com

**Conjunções**: e, ou, cada um, com, versus, mas, nem, juntamente com, além de

**Contrações**: P e R reconhece quase todas as contrações, é só experimentar.  Aqui estão alguns exemplos: não fiz, ele fez, ele é, ele não é, isso é, ela vai, eles fizeram, não eram, onde vai, quem é, não vai, não iria.

**Datas**: o Power BI reconhece a maioria dos termos de data (dia, semana, mês, ano, trimestre, década, etc.) e datas escritas em vários formatos diferentes (veja abaixo). O Power BI também reconhece as seguintes palavras-chave: MonthName, Dias 1-31, década.

Exemplos: 3 de janeiro de 1995, 3 de janeiro 1995, 3 jan 1995, 03 jan 1995, 3 de janeiro, janeiro de 1995, jan 1995, 01-1995, 01/1995, nomes de meses.

**Datas relativas**: hoje, agora, hora atual, ontem, amanhã, atual, próximo, a seguir, último, anterior, atrás, um momento atrás, antes de, depois, depois de, a partir de, às, a partir de agora, um momento mais tarde, no futuro, passado, anterior, em, ao longo de, N dias atrás, N dias a partir de hoje, no próximo, uma vez, duas vezes.

Exemplo: contagem de pedidos nos últimos 6 dias.

**Igualdade (Intervalo)**: em, igual a, =, depois, é maior que, em, entre, antes

Exemplos: O ano do pedido é anterior a 2012? O preço está entre 10 e 20? A idade de Marcelo é maior que 40? Total de vendas em 200-300?

**Igualdade (Valor)**: é, igual, igual a, em, de, para, dentro de, está em, está no(a)

Exemplos: Quais produtos são verdes? A data do pedido é igual a 2012. A idade de Marcelo é 40? Total de vendas que não é igual a 200? A data do pedido de 1/1/2016. 10 no preço? De cor verde? 10 no preço?

**Nomes**: se uma coluna no conjunto de dados contiver a frase “nome” (por exemplo, EmployeeName), a P e R entenderá que os valores nessa coluna são nomes e você pode fazer perguntas como “Quais funcionários têm o nome Paulo?”.

**Pronomes**: ele, dele, ele mesmo, seu, ela, ela mesma, dela, isso, isso mesmo, sua, eles, deles, eles mesmos, deles, isto, estes, esses

**Comandos de consulta**: classificado, classificar por, direção, grupo, agrupar por, por, mostrar, listar, exibir, forneça para mim, nomear, apenas, somente, organizar, comparar, com, em ordem alfabética, em ordem crescente, em ordem decrescente, ordenar

**Intervalo**: maior, mais, acima, menor, superior, >, menos, menor, abaixo, sob, <, pelo menos, não menor que, >=, no máximo, não mais que <=, em, entre, no intervalo de, posterior a, anterior a, após, em, às, depois, antes de, depois, desde, a partir de, com início em, com término em

**Horas**: am, pm, horas, meio-dia, meia-noite, hora, minuto, segundo, hh:mm:ss

Exemplos: 22h, 22h35, 22h35min15s, 10 da noite, meio-dia, meia-noite, hora, minuto, segundo.

**Os N primeiros** (ordem, classificação): superior, inferior, o maior, o menor, o primeiro, o último, o próximo, o mais recente, o mais antigo, o mais novo

**Tipos de visual**: todos os tipos de visual nativos do Power BI.  Se esta for uma opção no painel Visualizações, você poderá incluí-la em sua pergunta.  A exceção são [visuais personalizados](power-bi-custom-visuals.md) que você adicionou manualmente ao painel Visualização.

Exemplo: mostrar distritos por mês e vendas total como um gráfico de barras

**Perguntas (relação, qualificada)**: quando, onde, qual, quem, quantos, quanto, quantas vezes, com que frequência, qual valor, quantidade, número, quanto tempo, o que

## <a name="qa-helps-you-phrase-the-question"></a>A P e R ajuda a formular a pergunta
A P e R faz todo o possível para garantir que a resposta reflita com precisão a pergunta que está sendo feita. Ela faz isso de várias maneiras. Para todos esses, é possível aceitar a ação completa, a ação parcial ou não aceitá-la. Ao digitar sua pergunta, a P e R:

* preenche automaticamente palavras e perguntas. Ele usa várias estratégias, incluindo palavras reconhecíveis com preenchimento automático, perguntas comuns para as pastas de trabalho subjacentes e perguntas usadas anteriormente que retornaram respostas válidas. Se houver mais de uma opção de preenchimento automático disponível, elas serão apresentadas em uma lista suspensa.
* corrige a ortografia.
* fornece uma visualização da resposta na forma de uma visualização. A visualização é atualizada conforme você digita e edita a pergunta (ela não aguarda até que você pressione Enter).
* sugere automaticamente termos de substituição do(s) conjunto(s) de dados subjacente(s) quando você move o cursor de volta para a caixa de pergunta.
* reformula a pergunta com base nos dados do(s) conjunto(s) de dados subjacente(s). Isso ajuda a garantir que a P e R entendeu sua pergunta, já que ela substitui as palavras usadas por sinônimos do(s) conjunto(s) de dados subjacente(s).
* esmaece as palavras que não são entendidas.

## <a name="combine-results-from-more-than-one-dataset"></a>Combinar os resultados de mais de um conjunto de dados
Um dos recursos mais avançados do Power BI é a capacidade de combinar dados de diferentes conjuntos de dados.  Portanto, não limite suas perguntas a um único conjunto de dados – faça perguntas que recuperam dados de mais de um conjunto de dados. Por exemplo, se meu dashboard tiver blocos de Amostra de Análise de Varejo e um conjunto de dados de população de estado, poderei pedir para *mostrar a contagem de lojas por população de estado como um gráfico de barras em ordem decrescente*.

## <a name="dont-stop-now"></a>Não parar agora
Depois que a P e R exibir os resultados, é só conversar! Use os recursos interativos da visualização e das P e R para descobrir mais informações.

## <a name="next-steps"></a>Próximas etapas
Voltar a [P e R no Power BI](power-bi-q-and-a.md)  

[Power BI – conceitos básicos](service-basic-concepts.md)  

Mais perguntas? [Experimente a Comunidade do Power BI](http://community.powerbi.com/)

