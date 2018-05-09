---
title: Adicionar uma coluna de um exemplo no Power BI Desktop
description: Criar rapidamente uma nova coluna no Power BI Desktop usando colunas existentes como exemplos
services: powerbi
documentationcenter: ''
author: davidiseminger
manager: kfile
backup: ''
editor: ''
tags: ''
qualityfocus: no
qualitydate: ''
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 04/24/2018
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: 5031e31f83925d17fb87f39e4610a53617b9fca3
ms.sourcegitcommit: bdb1fee3612bcc66153dcad8c4db2e99fb041014
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2018
---
# <a name="add-a-column-from-an-example-in-power-bi-desktop"></a>Adicionar uma coluna de um exemplo no Power BI Desktop
A partir da versão de abril de 2017 do **Power BI Desktop**, você poderá adicionar novas colunas de dados ao seu modelo usando o **Editor de Consultas**; para isso, basta fornecer um ou mais valores de exemplo na nova coluna. Você pode criar um novo exemplo de coluna usando uma seleção atual ou fornecer entrada com base em todas as colunas (ou nas selecionadas) em uma determinada tabela.

![](media/desktop-add-column-from-example/add-column-from-example_01.png)

Essa abordagem o ajuda a criar novas colunas de maneira rápida e fácil e é excelente nas seguintes situações:

* Quando o resultado dos dados desejados na nova coluna é conhecido, mas você não tem certeza de qual transformação (ou conjunto de transformações) obterá ali.
* Quando as transformações necessárias já são conhecidas, mas você não tem certeza de onde clicar ou selecionar na interface do usuário para ativá-las.
* Quando já se sabe tudo sobre as transformações necessárias com o uso de uma expressão de *Coluna personalizada* em **M**, mas uma (ou mais) dessas expressões não está disponível para clicar ou adicionar na interface do usuário.

Usar o recurso **Adicionar coluna extraída de exemplo** é fácil e simples. Nas próximas seções, veremos como isso é fácil.

## <a name="use-query-editor-to-add-a-new-column-from-examples"></a>Uso do Editor de Consultas para adicionar uma nova coluna extraída de exemplos
Para criar uma nova coluna extraída de um exemplo, abra o **Editor de Consultas**. Para fazer isso, selecione **Editar consultas** na faixa de opções **Início** no **Power BI Desktop**.

![](media/desktop-add-column-from-example/add-column-from-example_02.png)

Para obter dados de uma página da Web, acesse a guia **Página Inicial**, clique em **Obter Dados > Web** e, em seguida, cole a URL na caixa de diálogo que aparece. Este artigo usa dados de um artigo da Wikipédia. Você pode clicar no seguinte link para obter os dados sozinho e prosseguir:

* [**Lista de estados e regiões dos Estados Unidos**](https://wikipedia.org/wiki/List_of_states_and_territories_of_the_United_States)

Após abrir o **Editor de Consultas** e carregar alguns dados, você poderá começar adicionando uma coluna extraída de exemplos. Para adicionar uma nova coluna, em **Editor de Consultas**, selecione a guia **Adicionar coluna** na faixa de opções e selecione **Coluna extraída de exemplos**. Se escolher a lista suspensa, você poderá selecionar **De todas as colunas** (que é o padrão, se simplesmente selecionar o botão em vez de a lista suspensa) ou **Da seleção**. Neste artigo, veremos como selecionar **De todas as colunas**.

![](media/desktop-add-column-from-example/add-column-from-example_03.png)

## <a name="the-add-column-from-examples-pane"></a>Painel Adicionar coluna extraída de exemplos
Depois de feita a seleção para adicionar uma nova coluna extraída de exemplos, será exibido um novo painel mostrando as colunas na tabela atual (talvez seja necessário rolar para visualizar todas as colunas). A nova coluna **Column1** também é exibida à direita, que é a coluna a ser criada pelo **Power BI Desktop** com base nos seus exemplos. Abaixo do cabeçalho da nova coluna **Column1**, ficam as células em branco, nas quais é possível digitar os exemplos que o Power BI usa para criar regras e transformações para corresponder ao seu exemplo.

Observe que esta é uma **Etapa Aplicada** do painel **Configurações de Consulta**. Como sempre, o **Editor de Consultas** gravará suas etapas de transformação e as aplicará por ordem à consulta.

![](media/desktop-add-column-from-example/add-column-from-example_04.png)

Este é o painel conhecido como **Adicionar colunas extraídas de exemplos** e consiste em quatro áreas principais:

1. A **barra Comando**, que inclui uma descrição resumida do recurso ou da transformação.
2. A opção **Enviar comentários** para ajudar o Power BI aprimorar o recurso.
3. Os botões **OK** e **Cancelar**, com os quais é possível confirmar transformações e adicionar a coluna ou cancelar.
4. A área da nova coluna, onde é possível digitar seus valores de amostra em qualquer uma das linhas (para fornecer o exemplo ao Power BI) relacionados a outras colunas da linha.

![](media/desktop-add-column-from-example/add-column-from-example_05.png)

Quando você digita o exemplo na nova coluna, o Power BI fornece uma visualização de como ela será exibida com base nas transformações detectadas. Por exemplo, se você digitar *Alabama* na primeira linha, isso corresponderá ao valor *Alabama* na primeira coluna da tabela. Assim que você pressionar *Enter*, o Power BI preencherá a coluna com base nesse valor.

Mas digamos que, em seguida, na linha que inclui *Massachusetts[E]* você exclua essa última parte *[E]* (porque não deseja mais). O Power BI detectará a alteração e usará o exemplo para criar uma transformação. Observe a explicação da transformação no painel superior intermediário.

![](media/desktop-add-column-from-example/add-column-from-example_06.png)

À medida que mais exemplos são fornecidos, o **Editor de Consultas** os adiciona às transformações. Quando estiver satisfeito, você poderá selecionar **OK** para confirmar as alterações.

## <a name="see-add-column-from-examples-in-action"></a>Consulte Adicionar coluna extraída de exemplos em ação
Interessado em ver como isso funciona? O vídeo a seguir mostra como colocar esse recurso em prática utilizando a fonte de dados fornecida no exemplo. Dê uma olhada e prossiga sozinho!

<iframe width="560" height="315" src="https://www.youtube.com/embed/-ykbVW9wQfw" frameborder="0" allowfullscreen></iframe>

## <a name="considerations-and-limitations"></a>Considerações e limitações
Há muitas transformações disponíveis quando a opção **Adicionar coluna extraída de exemplos** é usada, mas nem todas as transformações estão incluídas. A lista a seguir fornece todas as transformações com suporte.

* **Referência**
  
  * Referência a uma coluna específica (incluindo cortar, limpar ou aplicar uma transformação de maiúsculas e minúsculas)

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
    * Tamanho

* As seguintes **transformações de texto** com suporte estão disponíveis com a versão do **Power BI Desktop** de novembro de 2017:
    
  * Remover Caracteres
  * Manter Caracteres

> [!NOTE]
> Todas as transformações de *Texto* levam em consideração a necessidade potencial de cortar, limpar ou aplicar uma transformação de maiúsculas e minúsculas ao valor da coluna.
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
  * Para a hora local

> [!NOTE]
> Todas as transformações de *Data* e *Hora* levam em consideração a necessidade potencial de converter o valor da coluna para *Data* ou *Hora* ou *Data/Hora*.
> 
> 

* **Transformações de número** 

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

* As seguintes **transformações de número** com suporte estão disponíveis a partir da versão do **Power BI Desktop** de novembro de 2017:

  * Particionamento/intervalos

* **Geral**
  
  * Coluna Condicional