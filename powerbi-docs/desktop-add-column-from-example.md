---
title: Adicionar uma coluna de um exemplo no Power BI Desktop
description: Criar rapidamente uma nova coluna no Power BI Desktop usando colunas existentes como exemplos
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
ms.date: 09/06/2017
ms.author: davidi
ms.openlocfilehash: b425e7ea2cffeff31cc8cf49330ca3835d92165c
ms.sourcegitcommit: 284b09d579d601e754a05fba2a4025723724f8eb
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/15/2017
---
# <a name="add-a-column-from-an-example-in-power-bi-desktop"></a>Adicionar uma coluna de um exemplo no Power BI Desktop
A partir da versão de abril de 2017 do **Power BI Desktop**, você poderá adicionar novas colunas de dados ao seu modelo usando o **Editor de Consultas**; para isso, basta fornecer um ou mais valores de exemplo na nova coluna. É possível criar novos exemplos de coluna a partir de uma seleção atual ou da entrada de dados baseados em todas as colunas (ou colunas selecionadas) em determinada tabela.

![](media/desktop-add-column-from-example/add-column-from-example_01.png)

Essa abordagem o ajuda a criar novas colunas de maneira rápida e fácil e é excelente nas seguintes situações:

* Quando o resultado dos dados desejados na nova coluna é conhecido, mas você não tem certeza de qual transformação (ou conjunto de transformações) obterá ali.
* Quando as transformações necessárias já são conhecidas, mas você não tem certeza de onde clicar ou selecionar na interface do usuário para ativá-las.
* Quando já se sabe tudo sobre as transformações necessárias com o uso de uma expressão de *Coluna personalizada* em **M**, mas uma (ou mais) dessas expressões não está disponível para clicar ou adicionar na interface do usuário.

Usar o recurso **Adicionar coluna extraída de exemplo** é fácil e simples. Nas próximas seções, veremos como isso é fácil.

## <a name="use-query-editor-to-add-a-new-column-from-examples"></a>Uso do Editor de Consultas para adicionar uma nova coluna extraída de exemplos
Para criar uma nova coluna extraída de um exemplo, abra o **Editor de Consultas**. Para fazer isso, selecione **Editar consultas** na faixa de opções **Início** no **Power BI Desktop**.

![](media/desktop-add-column-from-example/add-column-from-example_02.png)

Neste artigo, usaremos dados do seguinte artigo da Wikipédia (trata-se de um link, portanto você pode clicar nele para acessar os dados e acompanhar o texto):

* [**Lista de estados e regiões dos Estados Unidos**](https://wikipedia.org/wiki/List_of_states_and_territories_of_the_United_States)

Após abrir o **Editor de Consultas** e carregar alguns dados, você poderá começar adicionando uma coluna extraída de exemplos. Para adicionar uma nova coluna, em **Editor de Consultas**, selecione a guia **Adicionar coluna** na faixa de opções e selecione **Coluna extraída de exemplos**. Se escolher a lista suspensa, você poderá selecionar **De todas as colunas** (que é o padrão, se simplesmente selecionar o botão em vez de a lista suspensa) ou **Da seleção**. Neste artigo, veremos como selecionar **De todas as colunas**.

![](media/desktop-add-column-from-example/add-column-from-example_03.png)

## <a name="the-add-column-from-examples-pane"></a>Painel Adicionar coluna extraída de exemplos
Depois de feita a seleção para adicionar uma nova coluna extraída de exemplos, será exibido um novo painel mostrando as colunas na tabela atual (talvez seja necessário rolar para visualizar todas as colunas). A nova coluna **Column1** também é exibida à direita, que é a coluna a ser criada pelo **Power BI Desktop** com base nos seus exemplos. Abaixo do cabeçalho da nova coluna **Column1**, ficam as células em branco, onde é possível digitar os exemplos utilizados pelo Power BI para criar regras e transformações para corresponder ao seu exemplo.

Observe também que esta é uma **Etapa aplicada** do painel **Configurações de consulta**. Como sempre, o **Editor de Consultas** gravará suas etapas de transformação e as aplicará por ordem à consulta.

![](media/desktop-add-column-from-example/add-column-from-example_04.png)

Este é o painel conhecido como **Adicionar colunas extraídas de exemplos** e consiste em quatro áreas principais:

1. A **barra Comando**, que inclui uma breve descrição do recurso ou da transformação.
2. A opção **Enviar comentários** para ajudar o Power BI aprimorar o recurso.
3. Os botões **OK** e **Cancelar**, com os quais é possível confirmar transformações e adicionar a coluna ou cancelar.
4. A área da nova coluna, onde é possível digitar seus valores de amostra em qualquer uma das linhas (para fornecer o exemplo ao Power BI) relacionados a outras colunas da linha.

![](media/desktop-add-column-from-example/add-column-from-example_05.png)

Ao digitar seu exemplo na nova coluna, o Power BI fornece uma visualização de como a coluna em processo de criação será exibida com base nas transformações detectadas. Por exemplo, digitamos *Alabama* na primeira linha, que corresponde ao valor *Alabama* na primeira coluna da tabela. Basta pressionar *Enter* para o Power BI preencher a coluna com base nesse valor.

Logo depois, no entanto, acessamos a linha que incluía *Massachusetts [E]* e excluímos a última parte *[E]* (porque não queríamos essa parte), e o Power BI detectou a alteração e usou o exemplo para criar uma transformação. Observe a explicação da transformação no painel superior central.

![](media/desktop-add-column-from-example/add-column-from-example_06.png)

À medida que mais exemplos são fornecidos, o **Editor de Consultas** os adiciona às transformações. Quando estiver satisfeito, você poderá selecionar **OK** para confirmar as alterações.

## <a name="see-add-column-from-examples-in-action"></a>Consulte Adicionar coluna extraída de exemplos em ação
Interessado em ver como isso funciona? O vídeo a seguir mostra como colocar esse recurso em prática utilizando a fonte de dados fornecida no exemplo. Dê uma olhada e acompanhe.

<iframe width="560" height="315" src="https://www.youtube.com/embed/-ykbVW9wQfw" frameborder="0" allowfullscreen></iframe>

## <a name="considerations-and-limitations"></a>Considerações e limitações
Há muitas transformações disponíveis quando a opção **Adicionar coluna extraída de exemplos** é usada, mas nem todas as transformações estão incluídas. A lista a seguir fornece todas as transformações *com* suporte.

* **Referência**
  
  * Referência a uma coluna específica (incluindo transformações de corte, de limpeza (a partir de junho de 2017) e de maiúsculas e minúsculas)
* **Transformações de texto**
  
  * Combinar (dá suporte à combinação de cadeias de caracteres literais e a todos os valores da coluna)
  * Substituir
  * Tamanho
  * Extrair
    
    * Primeiros caracteres
    * Últimos caracteres
    * Intervalo
    * Texto antes do delimitador
    * Texto depois do delimitador
    * Texto entre delimitadores
  * As seguintes **transformações de texto** com suporte estão disponíveis com a versão do **Power BI Desktop** de junho de 2017:
    
    * Tamanho

> [!NOTE]
> Todas as transformações de *Texto* levam em consideração a necessidade potencial de cortar, limpar (desde junho de 2017) ou aplicar uma transformação de maiúsculas e minúsculas ao valor da coluna.
> 
> 

* **Transformações de data**
  
  * Dia
  * Dia da semana
  * Nome do dia da semana
  * Dia do ano
  * Mês
  * Nome do mês
  * Trimestre do ano
  * Semana do mês
  * Semana do ano
  * Ano
* As seguintes **transformações de data** com suporte estão disponíveis com a versão do **Power BI Desktop** de junho de 2017:
  
  * Idade
  * Início do ano
  * Fim do ano
  * Início do mês
  * Fim do mês
  * Início do trimestre
  * Dias do mês
  * Fim do trimestre
  * Início da semana
  * Fim da semana
  * Dia do mês
  * Início do dia
  * Fim do dia
* **Transformações de hora**
  
  * Hora
  * Minuto
  * Segundo
* **Transformações de data/hora/fuso horário** – a seguinte transformação com suporte está disponível com a versão do **Power BI Desktop** de junho de 2017:
  
  * Para a hora local

> [!NOTE]
> Todas as transformações de *Data* e *Hora* levam em consideração a necessidade potencial de converter o valor da coluna para *Data* ou *Hora* ou *Data/Hora*.
> 
> 

* **Transformações de número** – as seguintes transformações com suporte estão disponíveis com a versão do **Power BI Desktop** de junho de 2017:
  * Valor absoluto
  * Arco cosseno
  * Arco seno
  * Arco tangente
  * Converter em número
  * Cosseno
  * Cubo
  * Dividir
  * Expoente
  * Fatorial
  * Divisão de inteiro
  * É par
  * É ímpar
  * Ln
  * Logaritmo de base 10
  * Módulo
  * Multiplicar
  * Arredondar para baixo
  * Arredondar para cima
  * Sinal
  * Seno
  * Raiz quadrada
  * Quadrado
  * Subtrair
  * Somar
  * Tangente

