---
title: Práticas recomendadas de design para relatórios e visuais (white paper)
description: 'White paper: práticas recomendadas para a criação de relatórios no Power BI'
services: powerbi
documentationcenter: ''
author: mihart
manager: kfile
backup: ''
editor: ''
tags: ''
qualityfocus: ''
qualitydate: ''
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 04/11/2018
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: c1b0d87d432dc337a1dab5d13bba10cc8c99dd14
ms.sourcegitcommit: df94efc51f261113fa90ebdf3fe68dd149cc4936
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2018
---
# <a name="best-design-practices-for-reports-and-visuals"></a>Práticas recomendadas de design para relatórios e visuais
<!-- Shared newnav Include -->
[!INCLUDE [newnavbydefault](./includes/newnavbydefault.md)]

## <a name="introduction"></a>Introdução
Este documento fornece as práticas recomendadas para a criação de relatórios no Power BI. Começando com o planejamento, ele aborda os princípios de design que podem ser aplicados aos relatórios e às páginas, bem como os visuais individuais que compõem esse relatório.  Muitas dessas práticas recomendadas também se aplicam ao design de dashboard.

Esperamos que este artigo seja um ponto de partida para você e que você aplique o que aprendeu em seus próprios relatórios e visualizações, continuando essa conversa em community.powerbi.com. O uso de design e visualização de relatórios de BI é o assunto do momento e existem vários líderes em inovação, bloggers e sites que examinam cuidadosamente esse tópico (ao final deste artigo, apresentaremos alguns exemplos).   

> [!NOTE]
> As recomendações dadas neste white paper são diretrizes que você deverá aplicar quando for conveniente. Para cada princípio que descrevemos abaixo, geralmente, há motivos válidos para “quebrar a regra”.
> 
> 

*Estamos sobrecarregados com informações, não por conta do excesso, mas porque não sabemos como controlá-las.*
– Stephen Few

## <a name="a-look-at-the-landscape-and-terminology"></a>Análise do cenário e da terminologia
No Power BI, um relatório pode ter uma ou mais páginas de relatório e todas as páginas juntas são denominadas o relatório. Os elementos básicos do relatório são visuais (também conhecidos como visualizações), imagens independentes e caixas de texto. Dos pontos de dados individuais e elementos do relatório à página de relatório em si, há diversas opções de formatação.

Vamos começar no estágio de planejamento do relatório, seguir para os princípios básicos de design de relatório e, em seguida, abordar os princípios de design de visuais, concluindo com uma discussão sobre as práticas recomendadas para os tipos de visual individuais.

Diretrizes e instruções detalhadas sobre como criar e usar relatórios do Power BI estão disponíveis em **powerbi.com > Saiba mais**.

## <a name="before-you-build-your-first-visualizationfocus-on-requirements"></a>Antes de criar sua primeira visualização, concentre-se nos requisitos
A criação de um relatório começa antes da criação do primeiro visual, pois um bom relatório precisa de planejamento.  Conheça os dados com os quais você precisa trabalhar e anote os requisitos do relatório. Faça a seguinte pergunta: “Qual é a necessidade de negócios, como esses dados serão usados e por quem eles serão usados?” Uma pergunta fundamental é: “Quais decisões o leitor deseja conseguir tomar com base nesse relatório?”

A resposta para essas perguntas orientará o design. Cada relatório conta uma história. Verifique se essa história corresponde à necessidade de negócios. Pode ser uma tentação adicionar visuais que mostram análises impactantes, mas, se elas não corresponderem à necessidade de negócios, o relatório não será útil – e, de fato, os usuários poderão ficar distraídos com esses visuais. Além disso, você poderá descobrir que as informações necessárias para tomar a decisão não podem ser coletadas com base nesses dados. Esse relatório pode ser usado para avaliar o que é necessário?

Os relatórios podem ser usados para monitorar, descobrir, acompanhar, prever, avaliar, gerenciar, testar e muito mais. Se, por exemplo, a necessidade de negócios for um relatório de vendas que avalia o desempenho, você poderá criar um relatório que examina as vendas atuais, compara-as às vendas anteriores e aos concorrentes e que inclui alguns KPIs que disparam alertas.  Talvez os leitores possam fazer uma busca detalhada nos números de vendas para ver os fechamentos de lojas ou problemas na cadeia de fornecedores que podem estar afetando as vendas.  Outra busca detalhada pode ser a capacidade de examinar as vendas por loja, região, produto, temporada e muito mais.

Conheça os clientes do relatório e crie um relatório que usa uma terminologia conhecida e oferece dados em um nível de detalhe e complexidade equivalente ao nível de conhecimento dos clientes. Tem mais de um tipo de cliente? Uma solução nem sempre agrada a todos: crie páginas de relatório separadas com base nas competências e lembre-se de rotular cada página com clareza para que os clientes possam se identificar com elas. Outra opção é usar segmentações, para que os clientes possam adaptar a página de acordo com suas necessidades. Envolva o cliente no estágio de planejamento e evite o erro de criar o que você acha que eles precisam.  Esteja preparado para recomeçar e iterar.

Depois de identificar a necessidade de negócios, os clientes e as métricas que você deseja incluir, a próxima etapa é escolher os visuais certos para contar a história e apresentá-los da maneira mais eficaz possível. Isso já abrange grande parte do trabalho. Agora vamos começar com alguns princípios básicos de design de relatórios.

## <a name="principles-of-report-design"></a>Princípios de design de relatórios
Uma página de relatório tem espaço limitado e uma das coisas mais difíceis é ajustar todos os elementos desejados nesse espaço – e ainda fazer com essas informações sejam compreendidas facilmente. Além disso, não subestime o valor do que é “visualmente agradável”. O segredo é encontrar o equilíbrio entre o útil e o visualmente agradável.

Vamos dar uma olhada no layout, na clareza e na estética.

### <a name="layout---the-report-canvas"></a>Layout: a tela de relatório
A tela de relatório tem uma quantidade finita de espaço.  Se você não puder ajustar todos os elementos em uma única página de relatório, divida o relatório em várias páginas.  Uma página de relatório pode ser adaptada a um público específico (por exemplo, RH, TI, Vendas, SLT), ou a uma pergunta de negócios específica (por exemplo: Como os defeitos estão afetando nosso tempo de inatividade? Qual é o impacto de nossa campanha de Marketing sobre o Sentimento?) ou como uma história progressiva (por exemplo, a primeira página como visão geral ou como um “gancho” para chamar a atenção, a segunda página continuando a história de dados, a terceira página aprofundando a história, etc.).  Se o relatório inteiro se ajustar a uma única página, ótimo. Caso contrário, crie páginas de relatório separadas que dividem o conteúdo de forma lógica.  E não se esqueça de dar às páginas nomes significativos e úteis.

Considere a possibilidade de ocupar todos os espaços de uma galeria de arte. Você não colocaria 50 obras da arte em uma sala pequena, ocupando-a com cadeiras e pintando cada parede com uma cor diferente. Como o curador, você escolheria apenas as obras que tivessem um tema comum e as arrumaria pela sala com amplo espaço para que os visitantes circulem e reflitam sobre as obras e colocaria cartões informativos que descrevessem o que eles estão observando. E há uma razão pela qual as galerias mais modernas têm paredes simples!
Neste artigo, vamos começar com um exemplo de relatório que precisa de muito trabalho.  Conforme aplicamos nossas práticas recomendadas e os princípios de design, nosso relatório será aprimorado.

![](media/power-bi-visualization-best-practices/power-bi-example1newa.png)

**Figura 1: esta página de relatório desagradável precisa de muito trabalho**

O exemplo acima apresenta vários problemas de design (layout) relacionados ao espaço que abordaremos abaixo:

* alinhamento, ordem e uso de proximidade
* uso inadequado de espaço e classificação
* desordem

### <a name="alignment-order-and-proximity"></a>alinhamento, ordem e proximidade
O layout dos elementos do relatório afeta a compreensão e orienta o leitor pela página de relatório. A forma como os elementos são colocados e posicionados conta uma história.  O texto pode ser “comece aqui e, depois, veja aqui” ou “esses três elementos estão relacionados entre si”.

* Na maioria das culturas, as pessoas olham um texto da esquerda para a direita e de cima para baixo. Posicione o elemento mais importante no canto superior esquerdo do relatório. Organize também o restante dos visuais de uma maneira que leva à navegação lógica e à compreensão das informações.
* Posicione os elementos que exigem que o leitor faça uma escolha à esquerda das visualizações na qual a opção causará impacto: segmentações, por exemplo.
* Posicione os elementos relacionados próximos entre si: a proximidade indica que os elementos estão relacionados.
* Outra maneira de transmitir as relações é adicionar uma borda ou uma cor da tela de fundo em torno dos elementos relacionados. Por outro lado, adicione um divisor para distinguir entre diferentes seções de um relatório.
* Use o espaço em branco para dividir visualmente as seções da página de relatório.
* Preencha a página de relatório. Se você achar que há muito espaço em branco extra, aumente o tamanho das visualizações ou diminua o tamanho da tela.
* Reflita cuidadosamente sobre o dimensionamento dos elementos do relatório. Não deixe que a disponibilidade de espaço determine o tamanho de uma visualização.
* Faça com que o tamanho dos elementos importantes fique maior em relação aos outros ou adicione um elemento visual como uma seta para chamar a atenção.
* Alinhe os elementos na página de relatório, de forma simétrica ou assimétrica intencionalmente.

Vamos examinar o alinhamento em mais detalhes.

#### <a name="alignment"></a>Alinhamento
O alinhamento não significa que os diferentes componentes precisam ser do mesmo tamanho ou que é necessário ter o mesmo número de componentes em cada linha do relatório. Isso apenas significa que há uma estrutura para a página que ajuda na navegação e legibilidade.

Podemos ver em nosso relatório atualizado abaixo que os componentes do relatório agora estão alinhados nas bordas esquerda e direita e também que cada linha do relatório é alinhada horizontal e verticalmente. Nossas segmentações estão à esquerda dos visuais que elas afetam.

![](media/power-bi-visualization-best-practices/power-bi-example2new.png)

**Figura 2: nosso exemplo de relatório desagradável aprimorado com as edições de layout**

O Power BI inclui ferramentas para ajudá-lo a alinhar os visuais. No Power BI Desktop, com vários visuais selecionados, use as opções **Alinhar e Distribuir** na guia de faixa de opções **Visuais** para fazer a correspondência da posição dos visuais.

![](media/power-bi-visualization-best-practices/power-bi-visualization.png)

**Figura 3: alinhar visuais no Power BI Desktop**

No Power BI online e no Power BI Desktop, você também tem um controle preciso sobre o tamanho e a posição dos visuais por meio da guia **Geral** no painel de formatação de todos os visuais:

![](media/power-bi-visualization-best-practices/power-bi-align-vizs.png)

**Figura 4: definir a posição exata do visual**

Em nossa página de relatório de exemplo (Figura 2), os dois cartões e a borda grande estão alinhados na **Posição X** em 200.

#### <a name="fit-to-the-space"></a>Ajustar ao espaço
Faça o melhor uso do espaço que você tem.  Se você sabe como o relatório será exibido, crie-o com isso em mente. Reduza os espaços vazios para preencher a tela.  Faça tudo o que puder para eliminar a necessidade de barras de rolagem em visuais individuais.  Preencha o espaço sem fazer com que os visuais pareçam “espremidos”.

##### <a name="adjust-the-page-size"></a>Ajustar o tamanho da página
Ao reduzir o tamanho da página, os elementos individuais ficam maiores em relação à página geral. Faça isso desmarcando os visuais na página e usando a guia **Tamanho da Página** no painel de formatação.  

Esta é uma página de relatório usando um tamanho de página 4:3 e, em seguida, 16:9. Observe como o layout combina muito melhor com o tamanho 16:9. Há ainda espaço suficiente para remover a barra de rolagem do segundo visual.

![](media/power-bi-visualization-best-practices/power-bi-page-view-before.png)

**Figura 5a: O relatório no tamanho de página 4:3**

![](media/power-bi-visualization-best-practices/power-bi-page-view-after.png)

**Figura 5b: O relatório na proporção de tamanho de página 16:9**

O relatório será exibido na proporção 4:3, 16:9 ou em outra? Em telas pequenas ou enormes? Ou em todos os tamanhos e proporções de tela possíveis?  Crie o relatório com isso em mente.

Nossa página de relatório de exemplo parece um pouco “espremida”. Sem nenhum visual selecionado, abra o painel de formatação selecionando o ícone de rolo de pintura. Expanda **Tamanho da Página** e altere a **Altura** para 900.

![](media/power-bi-visualization-best-practices/power-bi-page-size.png)

**Figura 6: aumentar a altura da página**

#### <a name="reduce-clutter"></a>Reduzir a desordem
Uma página de relatório cheia será difícil de ser compreendida em uma visão rápida e poderá ser tão complicada que os leitores nem mesmo vão tentar entendê-la.  Elimine todos os elementos do relatório desnecessários. Não adicione elementos extra que não ajudam na compreensão ou na navegação. A página de relatório precisa transmitir as informações da forma mais clara, rápida e coesa possíveis.

Em seu livro *The Visual Display of Quantitative Information* (A exibição visual de informações quantitativas), Edward Tufte chama isso de “proporção de dados para tinta”.  Basicamente, remova qualquer coisa que não seja essencial.

A desordem que você remover aumentará o espaço em branco na página de relatório e lhe dará mais espaço para aplicar as práticas recomendadas que aprendemos acima na seção “Alinhamento, ordem e proximidade”.

Aqui, nosso exemplo já está com uma aparência bem melhor. Removemos muitos elementos que o deixavam cheio e adicionamos formas para agrupar os elementos.  A imagem de tela de fundo não existe mais, removemos a forma de seta e a caixa de texto desnecessárias, movemos um visual para outra página do relatório, entre outras coisas. Também aumentamos o tamanho da página para aumentar o espaço em branco (amarelo?).

![](media/power-bi-visualization-best-practices/power-bi-example3newer.png)

**Figura 7: nosso exemplo de relatório desagradável sem a desordem inicial**

### <a name="tell-a-story-at-a-glance"></a>Contar uma história em uma visão rápida
O teste geral deverá ser uma pessoa sem nenhum conhecimento prévio conseguir entender rapidamente o relatório sem a explicação de ninguém. Em uma visão rápida, os leitores devem conseguir ver rapidamente do que trata a página e cada gráfico e tabela.   

Quando os leitores examinam o relatório, seus olhos devem ser atraídos para o elemento que você deseja que eles examinem primeiro e, em seguida, eles continuarão a leitura da esquerda para a direita e da parte superior para a inferior.  Mude esse comportamento adicionando indicações visuais como rótulos de caixa de texto, formas, bordas, tamanho e cor.  

#### <a name="text-boxes"></a>Caixas de texto
Às vezes, os títulos das visualizações não são suficientes para contar a história.  Adicione caixas de texto para se comunicar com as pessoas que estão vendo seus relatórios.  As caixas de texto podem descrever a página de relatório, um agrupamento de visuais ou um visual individual. Elas podem explicar os resultados ou definir melhor um visual, os componentes do visual ou as relações entre os visuais. As caixas de texto podem ser usadas para chamar a atenção com base em critérios diferentes destacados na caixa de texto.

No serviço do Power BI, na barra de menus superior, selecione **Caixa de Texto**. (No Power BI Desktop, selecione **Caixa de Texto** na área **Inserir** da faixa de opções.)

![](media/power-bi-visualization-best-practices/power-bi-text-boxes.png)

**Figura 8: adicionar uma caixa de texto**

Digite na caixa vazia e, em seguida, use os controles na parte inferior para definir a face da fonte, o tamanho, o alinhamento e muito mais. Use as alças para redimensionar a caixa.

![](media/power-bi-visualization-best-practices/power-bi-text-box-edit.png)

**Figura 9: formatar a caixa de texto**

Mas não exagere! O excesso de texto em um relatório causa distração e desvia a atenção dos visuais. Se você achar que sua página de relatório precisa de “uma tonelada” de texto para torná-la mais compreensível, comece novamente.  É possível escolher um visual diferente que conta uma história melhor por conta própria? É possível ajustar os títulos nativos do visual para torná-los mais inteligíveis?   

#### <a name="text"></a>Text
Crie um guia de estilo de texto e aplique-o a todas as páginas do relatório. Escolha um número limitado de cores, faces de fonte e tamanhos de texto.  Aplique esse guia de estilo não apenas a elementos textuais, mas às opções de fonte que você escolher nas visualizações (consulte Títulos e rótulos que fazem parte das visualizações, abaixo). Defina as regras para quando você usará negrito, itálico, um tamanho da fonte maior, determinadas cores, etc.  Tente evitar usar todas as letras maiúsculas ou sublinhadas.

#### <a name="shapes"></a>Formas
As formas também podem ajudar na navegação e na compreensão. Use formas para agrupar informações relacionadas e realçar dados importantes, e use as setas para direcionar os olhos. As formas ajudam os leitores a entender onde começar e como interpretar o relatório. Em termos de design, isso costuma ser conhecido como *contraste*.

![](media/power-bi-visualization-best-practices/shapes.png)

**Figura 10a: formas no serviço do Power BI**

![](media/power-bi-visualization-best-practices/power-bi-desktop-shapes2new.png)

**Figura 10b: formas no Power BI Desktop**

Qual é a aparência de nossa página de exemplo agora?  A Figura 11 mostra uma página mais limpa e menos cheia com um uso consistente de faces de texto, fontes e cores.  O título da página no canto superior esquerdo nos informa do que trata a página.

![](media/power-bi-visualization-best-practices/power-bi-example4new.png)

**Figura 11: Nosso exemplo de relatório com a aplicação das diretrizes de texto e adição do título**

Em nosso exemplo, o título de uma página de relatório foi adicionado no canto superior esquerdo: no primeiro lugar que os leitores olham. O tamanho da fonte é 28 e a fonte é Segoe Bold para ajudar a destacá-lo do restante da página.  Nosso guia de estilo de texto recomenda que não seja colocada nenhuma tela de fundo, que os títulos sejam pretos, além de legendas e rótulos. Tudo isso foi aplicado a todos os visuais da página, sempre que possível (os rótulos e os eixos do gráfico de Combinação não são editáveis).  Além disso:

* Cartões: **Rótulo de categoria** definido como Desativado, **Título** Ativado e definido como 12 pt preto centralizado.
* Títulos dos visuais: se estiverem Ativados, definidos como 12 pt e alinhados à esquerda.
* Segmentações: **Cabeçalho** definido como Desativado e **Título** Ativado. Mantenha os **Itens** > **Texto** cinza e com 10 pt.
* Gráficos de dispersão e de coluna: fonte preta para os eixos X e Y e os títulos, se forem usados.

#### <a name="color"></a>Cores
Use cores para manter a consistência.  Falaremos mais sobre as cores em Princípios de design de visuais, abaixo. Mas aqui estamos nos referindo a planejar a seleção de cores para que ela não reduza a capacidade de os leitores entenderem rapidamente o relatório.  O excesso de cores vivas sobrecarrega os sentidos. O tema desta seção é mais voltado para o que não fazer com as cores.

#### <a name="backgrounds"></a>Telas de fundo
Ao definir telas de fundo para páginas de relatório, escolha cores que não obscurecem o relatório, que combinam com as outras cores na página ou que, geralmente, não prejudicam a vista. Lembre-se de que algumas cores têm um significado inerente.  Por exemplo, nos EUA, normalmente, a cor vermelha em um relatório é interpretada como algo ruim.

![](media/power-bi-visualization-best-practices/power-bi-page-background.png)

**Figura 12: Definir a tela de fundo do relatório**

Você não está criando uma obra de arte, mas um relatório funcional. Escolha uma cor que melhore a legibilidade e a projeção dos elementos do relatório.  

Um estudo sobre o uso de cores e visualizações em páginas da Web apontou que um contraste mais alto entre as cores aumenta a velocidade de compreensão (The effect of text and background colour on visual search of Web pages [O efeito da cor do texto e da tela de fundo na pesquisa visual de páginas da Web] e **Determining Users’ Perception of Web Page Visual Complexity and Aesthetic Characteristics** [Determinando a percepção dos usuários de características estéticas e da complexidade visual de páginas da Web]).

Aplicamos algumas práticas recomendadas de cores em nosso relatório de exemplo (Figuras 20 e 21) abaixo. O mais admirável foi que alteramos a cor da tela de fundo para preto.  O amarelo era muito claro e forçava a vista.  Além disso, no gráfico “Contagem de nomes de atletas por ano e classe”, a parte amarela das barras desapareceu na tela de fundo amarela.  O uso de uma tela de fundo preta (ou branca) nos dá o contraste máximo e torna os visuais o foco de nossa atenção.

Estas são as etapas adicionais que realizamos para melhorar o relatório de exemplo:

**Título da página**

Quando alteramos a tela de fundo para preto, nosso título desapareceu porque o campo da caixa de texto só permite a fonte preta.   Para corrigir isso, adicione um título da caixa de texto.  Com a caixa de texto selecionada, apague o texto e, na guia visualizações, selecione **Título** e ative-o. Selecione a seta para expandir as opções de **Título**, digite **Jogos Olímpicos de Verão** no campo **Texto do Título** e selecione branco como a **Cor da fonte**.

![](media/power-bi-visualization-best-practices/power-bi-text-box-title.png)

**Figura 13: Adicionar um título de página**

**Cartões**

Para os visuais do cartão, abra o painel de formatação (ícone de rolo de pintura) e ative a **Tela de fundo**. Selecione branco com transparência de 0%. Ative **Título**, selecione branco como a **Cor da fonte** e preto como a **Cor da tela de fundo**.

**Segmentações**

Até este ponto as duas segmentações tinham uma formatação diferente, o que não faz sentido em termos de design. Para ambas as segmentações, altere a cor da tela de fundo para azul-piscina.  Azul-piscina é uma boa opção porque faz parte da paleta de cores da página – você pode vê-la no mapa coroplético, no mapa de árvore e no gráfico de colunas.

![](media/power-bi-visualization-best-practices/power-bi-slicer-background.png)

**Figura 14: Alterar a cor da tela de fundo da segmentação**

Adicione uma borda branca fina.

![](media/power-bi-visualization-best-practices/power-bi-slicer-outline.png)

**Figura 15: Adicionar uma borda à segmentação**

A fonte cinza é difícil de ser vista em cima do azul-piscina; portanto, altere a cor de **Itens** para branco.

![](media/power-bi-visualization-best-practices/power-bi-slicer-items.png)

**Figura 16: Alterar a cor da fonte da segmentação**

E, finalmente, em **Título**, altere a **Cor da fonte** para branco e adicione preto como a **Cor da tela de fundo**.

![](media/power-bi-visualization-best-practices/power-bi-card-formatting.png)

**Figura 17: Formatar o título da segmentação**

**Forma de retângulo**

O retângulo também desapareceu na tela de fundo preta.  Para corrigir isso, selecione a forma e, no painel **Formatar forma**, ative a **Tela de fundo**.

![](media/power-bi-visualization-best-practices/power-bi-shape-format.png)

**Figura 18: Formatar a forma**

**Gráficos de colunas, gráfico de bolhas, mapa coroplético e mapa de árvore**

Adicione uma tela de fundo branca aos visuais restantes na página de relatório. No painel de formatação, expanda a opção **Linha** e defina a **Cor da Linha** como branca e o **Peso** como 3.

![](media/power-bi-visualization-best-practices/power-bi-background.png)

**Figura 19: Adicionar uma tela de fundo branca às visualizações restantes**

![](media/power-bi-visualization-best-practices/power-bi-example5a.png)

**Figura 20: Exemplo de relatório com a aplicação das práticas recomendadas de cores (tela de fundo preta)**

![](media/power-bi-visualization-best-practices/power-bi-example5b.png)

**Figura 21: Exemplo de relatório com a aplicação das práticas recomendadas de cores (tela de fundo branca)**
 

### <a name="aesthetics"></a>Estética
Grande parte do que consideraríamos estética já foi abordado acima: itens como alinhamento, cor, opções de fonte, desordem.  Mas existem algumas outras práticas recomendadas de design de relatórios que vale a pena abordar, que tratam da aparência geral do relatório.  

Lembre-se de que a função do relatório é atender a uma necessidade de negócios, não ser visualmente agradável.  Mas algum senso estético é necessário, especialmente quando se trata das primeiras impressões. O consultor Tony Bodoh, de Nashville, EUA, explica que “a emoção dispara um meio segundo antes de a lógica entrar em cena”.  Primeiro, os leitores reagirão no plano emocional à sua página de relatório, antes de terem mais tempo para se aprofundarem. Se a página parecer desorganizada, confusa, não profissional etc., talvez o leitor nunca descubra a história impactante que ela conta.

Wayne Eckerson, blogger no TDI e analista do setor na TechTarget, faz uma ótima analogia.  Criar um relatório é semelhante a decorar uma sala.  Com o tempo, você compra um vaso, um sofá, uma mesa de canto, um quadro.  Separadamente, você gosta de todos esses elementos. Mas embora cada seleção individual seja lógica, em conjunto, os objetos combinam ou disputam a atenção.

Concentre-se em:

* Criar um tema ou aparência comum para o relatório e aplique-o a todas as páginas do relatório
* Usar imagens independentes e outros elementos gráficos para apoiar e não se desviar da história real
* Aplique também todas as práticas recomendadas que abordamos até o momento neste artigo.

## <a name="principles-of-visual-design"></a>Princípios de design de visuais
Examinamos os princípios do design de relatórios: como organizar os elementos do relatório para que eles facilitem a compreensão rápida do relatório.  Agora vamos examinar os princípios de design de visuais propriamente ditos.  E, na próxima seção, vamos nos aprofundar nos visuais individuais e abordar as práticas recomendadas para alguns dos tipos mais usados.

Nesta seção, por enquanto, vamos deixar de lado nossa página de relatório de exemplo e examinar outros exemplos.  Depois de concluirmos os princípios de design de visuais, vamos voltar à nossa página de relatório de exemplo e aplicar o que aprendemos (com instruções passo a passo).  

### <a name="planning--choose-the-right-visual"></a>Planejamento – escolher o visual certo
Assim como é importante planejar seu relatório antes de começar a criá-lo, cada visual também necessita de planejamento.  Faça a seguinte pergunta: “Qual história estou tentando contar com este visual?” Em seguida, descubra qual tipo de visual contará melhor a história. Você poderia mostrar o progresso ao longo de um ciclo de vendas como um gráfico de barras, mas um gráfico de cascata ou de funil não seria melhor? Para obter ajuda sobre como fazer isso, leia a última seção deste artigo “Tipos de visual e práticas recomendadas”, que descreve as práticas recomendadas para alguns dos tipos mais comuns.  Não se surpreenda se o primeiro tipo de visual escolhido acabe não sendo a melhor opção.  Experimente mais de um tipo de visual para ver qual deles alcança melhor o objetivo.

Compreenda a diferença entre dados categóricos e quantitativos e saiba quais tipos de visual funcionam melhor com tipos de dados específicos. Dados quantitativos costumam ser conhecidos como medidas e, em geral, são numéricos. Dados categóricos costumam ser conhecidos como dimensões e podem ser classificados. Isso é abordado mais detalhadamente em “Escolher a medida certa”, abaixo.

Evite a tentação de usar tipos de visual sofisticados ou mais complexos para fazer com que o relatório pareça mais impressionante. O que você deseja é a opção mais simples para transmitir sua história. Gráficos de barras horizontais e gráficos de linhas simples podem transmitir informações rapidamente.  Eles são conhecidos e convenientes e a maioria dos leitores pode interpretá-los facilmente.  Outra vantagem é que a maioria das pessoas lê da esquerda para a direita e de cima para baixo e, portanto, esses dois tipos de gráfico podem ser examinados e compreendidos rapidamente.

O visual precisa de rolagem para contar a história? Evite a rolagem, se possível.  Tente aplicar filtros e fazer uso de hierarquias e da busca detalhada e, se isso não eliminar a barra de rolagem, considere a possibilidade de escolher um tipo diferente de visual. Se você não conseguir evitar o uso de rolagem, a rolagem horizontal será mais bem aceita do que a rolagem vertical.

Mesmo quando você escolher definitivamente o melhor visual para a história, talvez você ainda precise de ajuda para contar a história.  É nesse momento que os rótulos, títulos, menus, cores e tamanho entram em cena. Abordaremos esses elementos de design mais adiante na seção intitulada “Elementos de design”.

### <a name="choose-the-right-measure"></a>Escolher a medida certa
A história que o visual conta é interessante? Ela tem alguma importância?  Não crie visuais só porque você gosta de criar visuais. Talvez você achou que os dados contariam uma história interessante, mas não foi o caso. Não tenha medo de recomeçar e procurar uma história mais interessante. Ou talvez a história já exista, mas precise ser avaliada de uma maneira diferente.

Por exemplo, digamos que você deseje avaliar o sucesso de seus gerentes de vendas. Qual medida você usaria para fazer isso?  Você avaliaria isso da melhor forma examinando o total de vendas ou o lucro total, o crescimento ao longo do ano anterior ou o desempenho em relação a uma meta? A vendedora Sara pode ter o maior lucro e, se você mostrar o lucro total por vendedor em um gráfico de barras, ela parecerá uma celebridade em comparação com os outros vendedores.  Mas, se Sara tiver um alto custo de vendas (despesas de viagem, custos de envio, custos de fabricação etc.), a simples análise das vendas não contará a melhor história.

#### <a name="reflect-realitydont-distort-reality"></a>Refletir, sem distorcer, a realidade
É possível criar um visual que distorce a verdade. Existe um site em que os fãs de dados compartilham os visuais “ruins”. E o tema comum nos comentários é a decepção com a empresa que criou e distribuiu determinado visual.  Isso deixa claro que eles não podem ser confiáveis.

Portanto, crie visuais que intencionalmente não distorcem a realidade e que não são manipulados para contar a história que você quer que eles contem.  Este é um exemplo disso:

![](media/power-bi-visualization-best-practices/corp-success-distorted.png)

**Figura 22: Gráfico de realidade distorcida**

Neste exemplo, parece que há uma grande diferença entre as quatro empresas, e que CorpB é muito mais bem-sucedida do que as outras três.  Mas observe que o eixo X não começa no zero e que as diferenças entre as empresas, provavelmente, estão dentro da margem de erro.  Aqui estão os mesmos dados com um eixo X que começa no zero.

![](media/power-bi-visualization-best-practices/corp-success.png)

**Figura 23: Gráfico realista**

Os leitores esperam e costumam pressupor que o eixo X começa no zero. Se você decidir não começar no zero, faça isso de uma maneira que não distorça os resultados e considere a adição de uma indicação visual ou caixa de texto para apontar o desvio da regra.  

### <a name="design-elements"></a>Elementos de design
Depois de selecionar um tipo e uma medida e criar o visual, é hora de ajustar a exibição para eficácia máxima.  Esta seção aborda:

* Layout, espaço e tamanho
* Elementos de texto: rótulos, anotações, menus, títulos
* Classificação
* Interação entre visuais
* Cores

#### <a name="tweaking-visuals-for-best-use-of-space"></a>Ajustar os visuais para o melhor uso de espaço
Se você estiver tentando ajustar vários gráficos em um relatório, maximizar a proporção de dados para tinta ajudará a destacar a história nos dados. Como mencionamos acima, Edward Tufte inventou o termo “proporção de dados para tinta”: o objetivo é remover o máximo de marcas possíveis de um gráfico sem comprometer a capacidade do leitor de interpretar os dados.

No primeiro conjunto de gráficos abaixo, há títulos e rótulos de eixo redundantes (janeiro de 2014, abril de 2014, etc.) e títulos (“por Data”). Os títulos dos gráficos também precisam de um espaço horizontal dedicado em cada um deles. Ao removermos os títulos de gráfico e ativarmos rótulos de eixo individuais, removemos também um pouco de tinta e temos um melhor uso do espaço total. Podemos remover os rótulos de eixo dos dois gráficos principais para reduzir um pouco mais o uso de tinta e usar mais espaço para os dados.

Se, em algum momento específico, você desejar destacar algo, poderá desenhar linhas ou retângulos atrás de todos os gráficos para ajudar a chamar a atenção para cima e para baixo, como ajuda para as comparações.

![](media/power-bi-visualization-best-practices/power-bi-multiples-before.png)

**Figura 24: Antes**

![](media/power-bi-visualization-best-practices/power-bi-multiples-after.png)

**Figura 25: Depois**

**Para ativar e desativar os títulos dos eixos**

Selecione visual para torná-lo ativo e abra o painel Formatação. Expanda as opções do **eixo X** ou **eixo Y** e arraste o controle deslizante de **Título** para ativá-lo ou desativá-lo.

![](media/power-bi-visualization-best-practices/power-bi-axis-titles.png)

**Figura 26: Ativar e desativar os títulos dos eixos**

**Para ativar e desativar os rótulos de eixo**

Selecione visual para torná-lo ativo e abra o painel Formatação. Ao lado do **Eixo x** e **Eixo y** estão os controles deslizantes.  Arraste o controle deslizante para ativar ou desativar os rótulos de eixo.

![](media/power-bi-visualization-best-practices/power-bi-axis-labels.png)

**Figura 27: Ativar e desativar os rótulos de eixo**

> [!TIP]
> Um dos cenários em que você poderia desativar os rótulos do eixo Y seria se você tivesse ativado os **Rótulos de dados**.
> 
> 

**Para remover os títulos de visuais**

Selecione visual para torná-lo ativo e abra o painel Formatação. Defina o controle deslizante de **Título** como Desativado.

![](media/power-bi-visualization-best-practices/power-bi-title-off.png)

**Figura 28: Remover os títulos de visuais**

Considere como os leitores exibirão o relatório e verifique se os visuais e o texto são grandes e escuros o suficiente para serem lidos. Se você tiver um visual proporcionalmente maior na página, os leitores poderão pressupor que ele é o mais importante. Coloque espaço suficiente entre os visuais para que o relatório não pareça cheio e confuso.  Alinhe os visuais para ajudar a direcionar os olhos dos leitores.

**Para redimensionar um visual**

Selecione o visual para torná-lo ativo. Capte e arraste uma das alças para ajustar o tamanho.

![](media/power-bi-visualization-best-practices/power-bi-drag-handles.png)

**Figura 29: Redimensionar o visual**

**Para mover um visual**

Selecione o visual para torná-lo ativo. Selecione e mantenha a barra de garra na parte central superior do visual e arraste o visual para o novo local.

![](media/power-bi-visualization-best-practices/power-bi-move.png)

**Figura 30: Mover um visual**

#### <a name="titles-and-labels-that-are-part-of-the-visualizations"></a>Títulos e rótulos que fazem parte das visualizações
Verifique se os títulos e rótulos são legíveis e autoexplicativos. O texto dos títulos e rótulos deve estar em um tamanho ideal com cores que se destacam (como preto, em vez do cinza padrão). Lembra-se de nosso guia de estilo (consulte “Texto” acima)? Limite o número de cores e tamanhos – o excesso de tamanhos de fonte e cores diferentes faz com que a aparência da página fique carregada e confusa.  Considere o uso da mesma cor de fonte e tamanho para o título de todos os visuais de uma página de relatório e escolha o mesmo alinhamento para todos os títulos de uma página de relatório.  

**O painel de formatação**

Para cada um dos ajustes de formatação listados abaixo, selecione o ícone de rolo de pintura para abrir o painel Formatação.

![](media/power-bi-visualization-best-practices/power-bi-paintbrush.png)

**Figura 31: Abrir o painel Formatação**

Em seguida, selecione o elemento visual a ser ajustado e verifique se ele está definido como Ativado. Exemplos de elementos visuais são: **Eixo x**, **Eixo y**, **Título**, **Rótulos de dados** e **Legenda**. O exemplo abaixo mostra o elemento **Título**.

![](media/power-bi-visualization-best-practices/power-bi-title-formatting.png)

**Figura 32: Formatar um título de visual**

**Definir o tamanho do texto**

O tamanho do texto pode ser ajustado em títulos e rótulos de dados, mas não em eixos X ou Y ou legendas.  Especificamente, para rótulos de dados, experimente com as **Unidades de exibição** e o número de **Casas Decimais** até encontrar o nível de detalhe ideal para exibição do relatório.   

**Definir o alinhamento de texto**

As opções de alinhamento de título são à esquerda, à direita e centralizar.  Escolha uma opção e aplique essa mesma configuração a todos os visuais da página.  

**Definir a posição do texto**

A posição do texto pode ser ajustada em alguns eixos Y e na legenda.   Seja qual for a opção escolhida, faça o mesmo para os outros eixos Y e as outras legendas da página.

**Definir o título e o tamanho de rótulo**

Ajuste o tamanho de títulos, títulos de eixo, rótulos de dados e legendas. Se você optar por exibir um desses elementos, ajustar o tamanho (juntamente com o tamanho do texto) garante que nada ficará truncado. Em **Título** e **Legenda**, a configuração é **Texto do Título** e é aqui que você digita o título real que será exibido no visual. Em **Eixo x** e **Eixo y**, a configuração é **Estilo** e você seleciona uma opção em uma lista suspensa. Em **Rótulos de dados**, as configurações são **Exibição** e **Decimal**. Use a lista suspensa **Exibição** para selecionar as unidades de medida: milhões, milhares, nenhum, automático, etc. Use o campo **Decimal** para informar ao Power BI quantas casas decimais serão exibidas.

**Definir a cor do texto**

A cor do texto pode ser ajustada em títulos, eixos e rótulos de dados.  

#### <a name="titles-and-labels-that-are-not-part-of-the-visualizations"></a>Títulos e rótulos que não fazem parte das visualizações
Anteriormente neste documento, abordamos a adição de caixas de texto a páginas de relatório. Às vezes, os títulos das visualizações não são suficientes para contar a história.  Adicione caixas de texto para transmitir informações adicionais para os leitores de seus relatórios.  
Para evitar que a página de relatório fique muito confusa ou carregada, seja consistente no uso de alinhamento, tamanhos, cores e fontes de caixa de texto. Para fazer um ajuste ao texto em uma caixa de texto, selecione a caixa de texto para revelar o menu de formatação.

![](media/power-bi-visualization-best-practices/power-bi-text-box-edit.png)

**Figura 33: Formatar a fonte usada em uma caixa de texto**

#### <a name="sorting"></a>Classificação
Uma oportunidade realmente simples para fornecer análises mais rápidas é definir a classificação dos visuais. Por exemplo, classificar os gráficos de barras em ordem crescente ou decrescente com base no valor das barras permite que você mostre informações incrementais significativas rapidamente sem usar mais espaço.

Para classificar um gráfico, selecione as elipses (...) na parte superior direita do gráfico, selecione **Classificar** e escolha o campo pelo qual você deseja classificar, bem como a direção. Para obter mais informações, consulte [Change how a visual is sorted](power-bi-report-change-sort.md) (Alterar a classificação de um visual).

#### <a name="chart-interaction-and-interplay"></a>Interação entre gráficos
Um dos recursos mais interessantes do Power BI é a capacidade de editar o modo como os gráficos interagem entre si.  Por padrão, os gráficos têm realce cruzado: quando você seleciona um ponto de dados, os dados relacionados de outros gráficos ficam iluminados e os dados não relacionados, esmaecidos. Você pode substituir esse comportamento para usar um gráfico como um filtro verdadeiro que economiza espaço na página. Para fazer isso, selecione **Interações entre visuais** na barra de menus.

![](media/power-bi-visualization-best-practices/power-bi-visual-interactions.png)

**Figura 34: Interações entre visuais**

Em seguida, para cada visual da página, decida se deseja que o visual selecionado seja filtrado, realçado ou não tenha nenhuma ação. Nem todos os visuais podem ser realçados e, para eles, o controle de realce não estará disponível. Para obter mais informações, consulte [Interações entre visuais no Power BI](service-reports-visual-interactions.md).

> [!TIP]
> Para os leitores que estão conhecendo o Power BI agora, essa capacidade de clicar e interagir com relatórios pode não ser imediatamente óbvia. Adicione caixas de texto para ajudá-los a entender no que eles podem clicar para descobrir mais informações.
> 
> 

#### <a name="the-use-of-color-in-visuals"></a>O uso de cores em visuais
Anteriormente neste documento, falamos sobre a importância de ter um plano de como você pretende usar as cores em um relatório. Esta seção trará alguma repetição, mas, basicamente, se aplica a como você usa as cores em visuais individuais. E os mesmos princípios se aplicam: usar as cores para tornar o relatório coeso, adicionar ênfase aos dados importantes e melhorar a compreensão do leitor sobre o visual. O excesso de cores diferentes causa distração e dificulta para o leitor encontrar o foco. Não comprometa a compreensão para fins estéticos. Apenas adicione cores se elas melhorarem a compreensão.

> [!TIP]
> Conheça seu público e as regras de cores inerentes.  Por exemplo, nos Estados Unidos, verde geralmente significa “bom” e vermelho normalmente significa “ruim”.
> 
> 

Este tópico é dividido para abranger:

1. Cores de dados
2. Cores do rótulo de dados
3. Cores de valores categóricos
4. Cores de valores numéricos

**Usar as cores para realçar dados interessantes**

A maneira mais simples de usar as cores é alterar uma ou mais cores do ponto de dados para chamar a atenção para ele. Neste exemplo, a cor muda quando os Jogos Olímpicos passaram de um ciclo de 4 anos para um ciclo de 2 anos de jogos alternados de Inverno e Verão.

![](media/power-bi-visualization-best-practices/power-bi-data-color.png)

**Figura 35: Usar as cores para contar uma história**

Você pode alterar as cores de ponto de dados na guia **Cores de dados** do painel de formatação. Para personalizar cada ponto de dados individualmente, verifique se a opção **Mostrar tudo** está definida como Ativada.

![](media/power-bi-visualization-best-practices/power-bi-colors.png)

**Figura 36: Definir as cores de ponto de dados**

> [!NOTE]
> O Power BI aplica um tema padrão aos visuais de relatório.  As cores de tema foram escolhidas para fornecer variedade e contraste. Para desviar da paleta de temas padrão, selecione **Cor personalizada**.
> 
> 

![](media/power-bi-visualization-best-practices/power-bi-custom-color.png)

**Figura 37: Escolher uma cor personalizada**

No Power BI Desktop, você pode até mesmo realçar exceções ou uma seção de uma linha usando uma segunda série:

![](media/power-bi-visualization-best-practices/power-bi-outliers.png)

**Figura 38: Usando o Desktop para plotar exceções**

Aqui, os valores da série “Exceções” só existem nos casos em que a temperatura média de agosto cai abaixo de 60. Isso foi feito com a criação de uma coluna calculada DAX usando esta fórmula:

Exceções = if(Editions[Temp]<60, Editions[Temp], BLANK())

Em nosso exemplo, havia três exceções: 1952, 1956 e 2000.

**Cores de títulos e rótulos**

Ao explorar todas as opções de formatação disponíveis, você encontrará vários lugares diferentes para adicionar cores a títulos e legendas. Por exemplo, é possível alterar a cor de rótulos de dados e títulos de eixo. Faça isso com cuidado.  Em geral, você deseja usar uma única cor para todos os títulos de visual.  Assim como ocorre com todas as diretrizes deste artigo, há sempre situações e motivos para “quebrar as regras”, mas, se você decidir quebrá-las, faça isso por um bom motivo.

**Cores de valores categóricos**

Normalmente, gráficos com uma série têm um valor categórico na legenda. Por exemplo, cada cor na legenda abaixo representa uma categoria diferente de País/Região.

![](media/power-bi-visualization-best-practices/power-bi-bubble-color.png)

**Figura 39: Cores padrão aplicadas**

Por padrão, as cores que o Power BI usa foram escolhidas para fornecer uma boa separação de cores entre os valores categóricos, para que eles sejam fáceis de serem distinguidos. Às vezes, as pessoas alteram essas cores de acordo com seu esquema corporativo, etc., mas isso pode causar problemas.

![](media/power-bi-visualization-best-practices/power-bi-bubble-color2.png)

**Figura 40: Cores aplicadas como matizes de uma única cor**

Ao manter um único matiz e variar a intensidade da cor, este visual introduziu uma falsa sensação de ordenação entre as categorias. Isso implica que as bolhas mais escuras ficam mais altas ou mais baixas em alguma escala do que os matizes mais claros. Com exceção da ordem alfabética, normalmente, não existe uma ordem inerente a essa classificação de valor categórico.
Para alterar as cores padrão, abra o painel Formatação e selecione **Cores de dados**.

**Cores de valores numéricos**

Para campos que têm alguma ordem inerente e valores numéricos, você também pode colorir os pontos de dados pelo valor. Isso pode ser útil para mostrar o espalhamento de valores pelos dados e também para permitir que duas variáveis sejam mostradas em um único gráfico. Por exemplo, este gráfico deixa claro que, embora a China tenha a maior contagem de medalhas, o Japão e a Tailândia participaram em mais Jogos Olímpicos.

![](media/power-bi-visualization-best-practices/power-bi-saturation.png)

**Figura 41: Colorir pontos de dados pelo valor**

Para criar este gráfico, adicione um valor ao campo Saturação da cor e, em seguida, ajuste as cores no painel Formatação.

![](media/power-bi-visualization-best-practices/power-bi-saturation2.png)

**Figura 42: Adicionar um campo de saturação da cor**

![](media/power-bi-visualization-best-practices/power-bi-color-controls.png)

**Figura 43: Ajustar as cores usadas para saturação**

As cores também podem ser usadas para enfatizar a variação em torno de um valor central. Por exemplo, colorir valores positivos com verde e valores negativos com vermelho. Fique atento às diferenças culturais ao atribuir cores a valores positivos ou negativos; nem todas as culturas usam vermelho para coisas ruins e verde para boas!

![](media/power-bi-visualization-best-practices/power-bi-color.png)

**Figura 44: Cores para enfatizar a variação em torno de um valor central**
 

### <a name="principles-of-visual-design--applied-to-example-report-page"></a>Princípios de design de visuais – aplicados à página de relatório de exemplo
Agora vamos usar os princípios de visuais abordados acima e aplicá-los ao nosso relatório de exemplo.

Antes

![](media/power-bi-visualization-best-practices/power-bi-example5a.png)

**Figura 45: Nosso relatório de exemplo (antes)**

Depois

![](media/power-bi-visualization-best-practices/power-bi-example6anew.png)

**Figura 46: Nosso relatório de exemplo (depois)**

#### <a name="what-did-we-do"></a>O que fizemos?
1. Segmentação: removemos os espaços em branco das segmentações adicionando um filtro de nível de página e selecionando somente ouro, prata ou bronze. Alteramos **Controles de Seleção** para Desativado em **Seleção Única** e **Selecionar Tudo**.
2. Bolhas: há tantos itens na legenda que eles só são exibidos após rolar uma barra de rolagem na tela.  Removemos a legenda e ativamos **Rótulos de categoria**. Os clientes podem focalizar as bolhas para ver os detalhes. Abreviamos o título e removemos “por país/região”, já que isso parece óbvio. Ativamos os rótulos de eixos em ambos para facilitar a compreensão do gráfico.
3. Mapa coroplético: alteramos as **Cores de dados** para destacá-las mais. Ativamos **Divergente** e definimos o **Mínimo** como rosa e o **Máximo** como vermelho.
4. Mapa de árvore: removemos o filtro que foi definido como somente EUA. Definimos os **Rótulos de dados** como uma casa decimal. O visual usava o campo Classe que não é muito útil porque ele quase sempre será 33% (Prata/Ouro/Bronze).  Selecionamos um campo diferente e mais interessante, sexo. Para design, alteramos Aquático para azul e Atlético para cinza.
5. Gráfico de barras superior: abreviamos o título, removemos rótulos de dados e desativamos o título da legenda. Alteramos a ordem das palavras do título para que fosse correspondente ao gráfico abaixo.
6. Gráfico de barras inferior: classificamos por ano em ordem crescente para que fosse correspondente ao gráfico acima. Alteramos as cores para que fossem correspondentes à classe. Alteramos o título. Desativamos a legenda para obter mais espaço para os dados. Ativamos os rótulos de dados que não serão exibidos no relatório (porque o visual é muito pequeno para que os rótulos sejam legíveis), mas que serão exibidos quando o visual for aberto no modo Foco. [Saiba mais sobre o modo Foco](service-focus-mode.md). Adicionamos a Contagem de Eventos (Distinta) a **Dicas de Ferramenta** para que, agora ao focalizar uma coluna empilhada, as dicas de ferramenta também informem quantos eventos foram realizados nesse ano.
7. Interações entre visuais: desativamos as interações em ambos os cartões, pois desejo que eles sempre mostrem o total de jogos e esportes.

## <a name="visual-types-and-best-practices"></a>Tipos de visual e práticas recomendadas
O Power BI fornece vários tipos de visual nativamente.  Além deles, adicione os visuais personalizados disponíveis da Microsoft e da comunidade do Power BI e o total de opções de visual será enorme para documentar aqui. Mas vamos examinar alguns dos tipos de visual nativos mais utilizados.  

### <a name="line-charts"></a>Gráficos de linhas
![](media/power-bi-visualization-best-practices/power-bi-line-chartb.png)

Gráficos de linhas são uma maneira eficiente de examinar dados ao longo do tempo.  Analisar dados em tabelas não aproveita, de fato, a velocidade na qual nossos picos identificam picos, vales, ciclos e padrões.  
O exemplo abaixo mostra as tendências no número de medalhas entregues e de atletas que ganharam essas medalhas.  

![](media/power-bi-visualization-best-practices/power-bi-line-chart.png)

**Figura 47: Gráficos de linhas**

#### <a name="best-practices"></a>Práticas recomendadas
* Quando as pessoas olham os gráficos de linhas, a primeira coisa que veem é a forma da curva.  Isso significa que você precisa ter um eixo X que torna a curva significativa nesse momento ou ter categorias de distribuição.  Se você colocar campos categóricos como produto ou geografia no eixo X, o gráfico de linhas não será interessante, pois a forma da curva não fornecerá nenhuma informação significativa.
* Se você optar por colocar vários gráficos acima e abaixo um do outro dessa forma, a fim de facilitar a comparação entre as séries, alinhe o eixo X. Use filtros para garantir que o mesmo intervalo de valores é mostrado.  Por exemplo, se você estiver examinando intervalos de datas, verifique se eles são os mesmos intervalos de datas.  Por exemplo, 1896 a 2012 em ambos os gráficos.
* Faça uso total do espaço.  Se isto fizer sentido para seus dados, defina os pontos inicial e final do eixo Y para eliminar o espaço vazio na parte superior e inferior do gráfico e se concentrar nos pontos de dados reais. Para fazer isso, selecione o ícone de rolo de pintura para abrir o painel Formatação. Expanda a área do **Eixo y** e defina os pontos **Inicial** e **Final**.
  
  ![](media/power-bi-visualization-best-practices/power-bi-start-end.png)
  
  **Figura 48: Definir os pontos inicial e final**
* Outro motivo para definir explicitamente os pontos Inicial e Final é se você está comparando dois ou mais gráficos na mesma página usando o mesmo campo do eixo Y.  Por exemplo, se você estiver examinando as contagens totais de eventos e o Reino Unido tiver contagens que variam de 1 a 70 e a Austrália tiver contagens que variam de 1 a 12, os dois gráficos de linhas exibirão eixos Y muito diferentes (Figura x). Isso dificulta a comparação em uma visão rápida. Em vez disso, defina os gráficos para que eles usem o mesmo intervalo de eixo Y (Figura x).
  
  ![](media/power-bi-visualization-best-practices/power-bi-line-chart2.png)
  
  **Figura 49: Gráficos de linhas com eixos Y diferentes**
  
  ![](media/power-bi-visualization-best-practices/power-bi-line-chart3.png)
  
  **Figura 50: Gráficos de linhas com eixos Y correspondentes**

Para obter mais informações, veja:

* [Personalizar os eixos X e Y](power-bi-visualization-customize-x-axis-and-y-axis.md)
* [Gráficos de linhas e intervalos irregulares](http://www.perceptualedge.com/articles/visual_business_intelligence/line_graphs_and_irregular_intervals.pdf)
* [Introdução aos gráficos de linhas](http://www.columnfivemedia.com/data-visualization-101-line-charts)

### <a name="barcolumn-charts"></a>Gráficos de barras/colunas
![](media/power-bi-visualization-best-practices/power-bi-bar-chart.png)

Se os gráficos de linhas são o padrão para examinar dados ao longo do tempo, gráficos de barras são o padrão para examinar um valor específico em categorias diferentes.  Se você classificar as barras de acordo com o número, verá instantaneamente os principais valores e a distribuição.  Gráficos de barras horizontais funcionam bem com rótulos muito longos.  

![](media/power-bi-visualization-best-practices/power-bi-horizontal-scroll.png)

**Figura 51: Gráfico de barras horizontais**

#### <a name="best-practices"></a>Práticas recomendadas
* Exiba os rótulos de dados para obter os valores.  Isso facilita a identificação de valores específicos. Para fazer isso, abra o painel Formatação e defina **Rótulos de dados** como Ativado.
  
  ![](media/power-bi-visualization-best-practices/power-bi-data-labels.png)
  
  **Figura 52: Ativar rótulos de dados**
* O gráfico de barras acima é realmente útil para comparar uma medida com várias outras **em um único ponto no tempo**.  Embora o gráfico de linhas acima tenha nos mostrado a tendência ao longo do tempo, o gráfico de barras nos mostra a tendência de uma única categoria em um ponto específico no tempo.  Em uma visão rápida, nosso gráfico de barras mostra que a Espanha tem uma das piores taxas de desemprego do mundo, 25%.
* Quando um gráfico de Barras/Colunas inteiro não se ajusta ao espaço alocado, o Power BI adiciona barras de rolagem. Quando possível, e se fizer sentido, estruture o visual e o relatório para mostrar o gráfico inteiro, para que o leitor obtenha uma visão geral de toda a distribuição.  Infelizmente, isso não é possível em nosso exemplo, dado o número significativo de países em todo o mundo.
  
  Uma maneira de limitar os valores incluídos é usar um filtro. Por exemplo, adicione um filtro de nível de visual que mostra o país somente se a taxa de desemprego está acima de 20%.
* Nos gráficos de Barras/Colunas, é possível fazer uma busca detalhada (e exibi-los novamente em sua forma original).  Essa é uma ótima maneira de empacotar mais informações em um visual sem ocupar mais espaço.  O exemplo abaixo tem uma hierarquia para Regiões > Países.  Clicar duas vezes na barra de uma região faz uma busca detalhada nos países que compõem a região.  Para obter mais informações sobre a busca detalhada, consulte [Fazer uma busca detalhada em uma visualização](power-bi-visualization-drill-down.md).
  
  ![](media/power-bi-visualization-best-practices/power-bi-drill.png)
  
  **Figura 53: Fazer uma busca detalhada**

Para obter mais detalhes sobre gráficos de Barras e Colunas:

* [Introdução aos gráficos de barras](http://blog.newscred.com/article/data-visualization-101-bar-charts)
* [Catálogo de visualização de dados: gráfico de barras](http://www.datavizcatalogue.com/methods/bar_chart.html#.VYV-hY3bLJw)
* [Catálogo de visualização de dados: Gráfico de barras de conjunto múltiplo](http://www.datavizcatalogue.com/methods/multiset_barchart.html#.VYV_gI3bLJw)

### <a name="stacked-barcolumn-charts"></a>Gráficos de barras/colunas empilhadas
![](media/power-bi-visualization-best-practices/power-bi-stacked.png)

Adicione outra dimensão aos gráficos de barras/colunas empilhando categorias diferentes na barra ou na coluna.  Agora o gráfico transmite informações sobre uma tendência geral (com base na altura e no tamanho), mas também mostra a influência das categorias sobre essa tendência. O gráfico abaixo mostra o crescimento geral da receita mais alta de equipes de futebol acima de 6 bilhões em 2014.

![](media/power-bi-visualization-best-practices/power-bi-deloite.png)

**Figura 54: Gráfico de colunas empilhadas**

Este gráfico de colunas empilhadas mostra que a receita total está crescendo ao longo do tempo e que as categorias Comercial e Difusão estão crescendo de forma contínua ao longo do tempo – contribuindo para o aumento da receita geral.  Mas esse gráfico não facilita a comparação do impacto que cada uma das três categorias causa sobre as outras. Por exemplo, como o crescimento da categoria Comercial é comparado ao crescimento da categoria Difusão ou Dia de jogo?  Uma opção melhor para esses dados, ou um visual complementar para esses dados, seria um gráfico de linhas.  

![](media/power-bi-visualization-best-practices/power-bi-deloite2.png)

**Figura 55: Converter em um gráfico de linhas**

Neste gráfico de linhas, é mais fácil ver como a receita comercial foi a que mais cresceu, seguido por difusão e dia de jogo.

#### <a name="best-practices"></a>Práticas recomendadas
* Assim como ocorre com colunas e barras, você tem a opção de exibição horizontal ou vertical.   Horizontal será uma opção melhor se você tiver rótulos longos e vertical se tiver dados de série temporal.  
* Evite gráficos de Barras/Colunas empilhadas se você desejar mostrar tendências e outros padrões de mudança ao longo do tempo.  Outros gráficos, como gráficos de Linhas, fazem um trabalho muito melhor.
* Você também pode ter a distribuição de acordo com o volume total ou como um percentual do total.  
* Como Few observou, *é difícil comparar os segmentos de uma barra empilhada. Se os segmentos fossem organizados lado a lado e todos eles crescessem da mesma linha de base, seria fácil comparar suas alturas, mas quando eles empilhados em cima um do outro, essa tarefa torna-se difícil. Além disso, embora seja razoavelmente fácil ver como (a receita) mudou conforme o mês, é bem difícil ver como (a receita) nas outras (categorias) mudou*.  
* Gráficos 100% empilhados são uma boa opção ao usar percentuais que somam 100.  No exemplo abaixo, vemos a distribuição de categoria por equipe.  Os percentuais são relativos e nos permite observar padrões rapidamente. Por exemplo, a receita do Everton é obtida principalmente de Difusão (mais de 70%), enquanto o PSG obtém apenas 20% de sua receita de Difusão.  A escolha de uma exibição horizontal facilita o ajuste dos rótulos de equipe e a visualização do impacto do tipo de receita.
  
  ![](media/power-bi-visualization-best-practices/power-bi-deloite3.png)
  
  **Figura 56: Gráfico empilhado horizontal**

Para obter mais informações sobre gráficos empilhados:

* [Catálogo de visualização de dados: Gráficos de barras empilhadas](http://www.datavizcatalogue.com/methods/stacked_bar_graph.html#top)
* [Quando os gráficos de barras 100% empilhadas são úteis?](http://www.perceptualedge.com/blog/?p=2239)

### <a name="combo-barcolumn-charts"></a>Gráficos de combinação de barras/colunas
![](media/power-bi-visualization-best-practices/power-bi-combo.png)

No Power BI, é possível combinar gráficos de colunas e linhas em um gráfico de combinação. As opções são: gráfico de Linhas e Colunas Empilhadas e gráfico de Linhas e Colunas Clusterizadas. Economize espaço valioso na tela combinando dois visuais separados em um.

As duas capturas de tela abaixo mostram um cenário antes-e-depois.  A primeira página tem dois visuais separados: um gráfico de Colunas que mostra a população ao longo do tempo e um gráfico de Linhas que mostra o PIB ao longo do tempo. Esses gráficos são um bom candidato para um gráfico de Combinação porque têm o mesmo Eixo X (ano) e valores (2002 a 2012).  Por que não os combinar para comparar essas duas tendências em um único visual?  Combinar esses dois gráficos permite que você faça uma comparação mais rápida dos dados.

A nova página de relatório tem um único visual: um gráfico de linhas e um gráfico de colunas empilhadas. Poderíamos facilmente ter criado um gráfico de linhas e um gráfico de colunas clusterizadas.  Agora é mais fácil procurar uma relação entre as duas tendências.   Podemos ver que, até 2008, a população e o PIB seguiam uma tendência semelhante. Mas a partir de 2009, com o nivelamento do crescimento da população, o PIB ficou mais volátil.  

![](media/power-bi-visualization-best-practices/power-bi-spain-line.png)

 **Figura 57: Como dois gráficos separados**

![](media/power-bi-visualization-best-practices/power-bi-spain-combo.png)

 **Figura 58: Como um único gráfico de combinação**

#### <a name="best-practices"></a>Práticas recomendadas
Os gráficos de combinação funcionam melhor quando ambos os visuais têm, pelo menos, um eixo em comum.

Fique de olho nos eixos! O gráfico de Combinação é fácil de ser lido e interpretado?  Ou ele usa valores e intervalos diferentes? Por exemplo, se a escala do Eixo Y do gráfico de colunas for bem menor do que a escala do Eixo Y do gráfico de linhas, o gráfico de combinação não será significativo.  Por exemplo, observe a terceira linha (na cor azul-piscina) lá em baixo, na parte inferior.

   ![](media/power-bi-visualization-best-practices/power-bi-dual-line.png)

   **Figura 59: Um gráfico de linhas que não deu certo**

Portanto, o gráfico de combinação também não será significativo se o gráfico de colunas e o gráfico de linhas usarem duas medidas diferentes e você não criar eixos duplos.  Por exemplo, dólares versus por cento. Lembre-se de incluir os dois eixos para ajudar o leitor a compreender o gráfico e considere também a adição de rótulos de eixo.

Para fazer isso, abra o painel Formatação, expanda **Eixo Y** e defina **Mostrar Secundário** como Ativado (se ainda não estiver Ativado). Às vezes, essa configuração é difícil de ser encontrada. Expanda **Eixo Y (Coluna)** e role para baixo até ver **Mostrar secundário**. Além disso, defina o **Título** do Eixo Y (Coluna) e o **Título** do Eixo Y (Linha) como Ativado.

![](media/power-bi-visualization-best-practices/power-bi-show-secondary-new.png)

**Figura 60: Mostrar o eixo secundário**

![](media/power-bi-visualization-best-practices/power-bi-combo-chart.png)

**Figura 61: Preferencialmente, criar um gráfico de combinação**

* Aproveite os eixos duplos. É uma ótima maneira de comparar várias medidas com intervalos de valores diferentes. E é uma excelente maneira de ilustrar a correlação entre duas medidas em um visual.

Para obter mais informações, consulte:

* [Tutorial: Gráfico de combinação no Power BI](power-bi-visualization-combo-chart.md)
* [O perigo de eixos com escala dupla em visuais](http://www.perceptualedge.com/articles/visual_business_intelligence/dual-scaled_axes.pdf)

### <a name="scatter-chart"></a>Gráfico de dispersão
![](media/power-bi-visualization-best-practices/power-bi-scatter.png)

Às vezes, temos tantas variáveis que desejamos vê-las juntas, e um gráfico de dispersão pode ser uma maneira muito útil para obter uma visão geral.  Os gráficos de dispersão exibem as relações entre duas (Dispersão) ou três (Bolhas) medidas quantitativas.  Um gráfico de dispersão sempre tem dois eixos de valor para mostrar um conjunto de dados numéricos em um eixo horizontal e outro conjunto de valores numéricos em um eixo vertical. O gráfico exibe pontos na interseção de um valor numérico de x e y, combinando esses valores em pontos de dados individuais. Esses pontos de dados podem ser distribuídos de maneira uniforme ou não pelo eixo horizontal, dependendo dos dados.

Um gráfico de bolhas substitui os pontos de dados por bolhas, com o tamanho de bolha representando uma dimensão adicional dos dados.

O gráfico de bolhas abaixo examina a América do Sul e compara o PIB per capita (Eixo Y), soma do PIB (Eixo X) e população por país da América do Sul.  O tamanho das bolhas representa a população total de um país específico. O Brasil tem a maior população (tamanho de bolha) e a maior participação no PIB da América do Sul (é o mais longo do Eixo X).  Mas observe que o PIB per capita do Uruguai, do Chile e da Argentina é maior que o do Brasil (mais longo do Eixo Y).

![](media/power-bi-visualization-best-practices/power-bi-bubble.png)

**Figura 62: PIB e população da América do Sul como um gráfico de bolhas**

Se você adicionar um eixo de reprodução, poderá fingir que é Hans Rosling e contar a história ao longo do tempo (https://www.youtube.com/watch?v=PbaDBJWCeD4). Para adicionar um eixo de reprodução, arraste um campo de datetime para a seção **Eixo de reprodução**.

#### <a name="best-practices"></a>Práticas recomendadas
* Gráficos de dispersão e de bolhas são excelentes contadores de histórias. Mas eles não são tão úteis ao tentar explorar os dados.  Isso é o que Stephen Few indica no parágrafo abaixo *A vantagem dessa abordagem é quando ela é usada para contar uma história. Quando Rosling narra o que acontece no gráfico conforme as bolhas se movem e seu valor é alterado, apontando para o que ele deseja que nós vemos, as informações ganham vida. No entanto, os gráficos de bolhas animados, são muito menos eficazes para explorar e entender os dados por conta própria. Duvido que Rosling usa esse método para descobrir as histórias, mas apenas para contá-las depois que elas são conhecidas. Não podemos acompanhar mais de uma bolha ao mesmo tempo, pois elas ficam se movendo. Portanto, somos forçados a executar a animação repetidamente para tentar entender o que está acontecendo. Podemos adicionar trilhas às bolhas selecionadas, o que possibilita examinar o caminho completo percorrido por essas bolhas, mas, se as trilhas forem usadas para mais de algumas bolhas, o gráfico rapidamente ficará muito cheio. Basicamente, o que estou enfatizando é que essa não é a melhor maneira de exibir essas informações para análise e exploração.*
* Adicione os rótulos dos eixos X e Y para ajudar a contar a história.  Especialmente com gráficos de bolhas, há muitos componentes em jogo e os rótulos ajudam os leitores a entenderem o visual.
* Adicione rótulos de dados para facilitar a interpretação do visual.  Especialmente com gráficos de bolhas, quando você tiver vários itens na Legenda, poderá ser difícil distinguir cores semelhantes.  No visual acima, as cores de legenda para Suriname Columbia e Equador são muito semelhantes.
* Você criou um gráfico de dispersão e está vendo apenas um ponto de dados que agrega todos os valores nos eixos X e Y? Ou o gráfico agrega todos os valores ao longo de uma única linha horizontal ou vertical?  Para corrigir isso, adicione um campo à área **Detalhes** para informar ao Power BI como agrupar os valores. O campo deve ser exclusivo para cada ponto que você deseja plotar. Para obter ajuda, consulte o [Tutorial de gráficos de dispersão e de bolhas do Power BI](power-bi-visualization-scatter.md).

### <a name="tree-map-charts"></a>Gráficos de mapa de árvore
![](media/power-bi-visualization-best-practices/power-bi-treemap.png)

Os mapas de árvore podem ser muito úteis para dar uma boa visão geral do tamanho relativo dos diferentes componentes que compõem um todo – especialmente quando você pode agrupá-los por categorias.  Sempre que estou tentando entender um novo assunto, ter um mapa de árvore dos principais componentes pode ser muito útil para conhecer a distribuição geral.

No primeiro gráfico abaixo, você pode ver imediatamente que o Brasil compõe aproximadamente metade do PIB da América do Sul e que a Venezuela e Argentina têm aproximadamente o mesmo tamanho.

Se desejar ter um contexto mais amplo e ainda ter uma ideia do impacto dos principais países contribuintes, você poderá criar hierarquias de visual com os membros de categoria (países) aninhados em regiões. O segundo mapa de árvore nos dá uma ideia, em primeiro lugar, do tamanho relativo das regiões e, em cada região, podemos ver quais países individuais contribuem mais. Vemos que existem três regiões substanciais (Europa, Ásia e América do Norte) e nelas podemos ver facilmente os principais países e regiões.

A principal limitação de um mapa de árvore é a capacidade limitada para comparar diferentes retângulos além dos que estão na parte superior.  É um bom gráfico para uma visão geral, mas os gráficos de barras e de colunas provavelmente são uma opção melhor para ter uma ideia mais precisa do tamanho relativo dos diferentes componentes.
  Por exemplo, o primeiro mapa de árvore fornece uma indicação ampla da ordem de tamanho do PIB, mas é difícil identificar diferenças específicas entre países, especialmente, as caixas sem rótulo menores. Para esses dados, em que um único agrupamento é comparado, um gráfico de barras ou colunas pode ser uma opção melhor.

![](media/power-bi-visualization-best-practices/power-bi-treemap3.png)

**Figura 63: Comparação do PIB da América do Sul como um mapa de árvore**

Aqui, adicionamos outro nível de dados, região e podemos ver a contribuição geral para o PIB por regiões, bem como o impacto relativo nas regiões. Lembre-se de que fazer isso com medidas não aditivas (como médias) poderá fazer com que a soma dos detalhes não represente o valor real no nível de agregação.

![](media/power-bi-visualization-best-practices/power-bi-treemap2.png)

**Figura 64: PIB por região e país como um mapa de árvore**

Para obter mais informações sobre os mapas de árvore, não hesite em clicar nos links abaixo.

* [Visão geral dos mapas de árvore](http://www.perceptualedge.com/articles/b-eye/treemaps.pdf)
* [Catálogo de visualização de dados: mapas de árvore](http://www.datavizcatalogue.com/methods/treemap.html#.VYhylI3bL7Y)

### <a name="other-charts"></a>Outros gráficos
#### <a name="pie-or-donut-charts"></a>Gráfico de pizza ou de rosca
![](media/power-bi-visualization-best-practices/power-bi-donut.png)

Em geral, os gráficos de barras/colunas/linhas atenderão a maioria das finalidades. É amplamente reconhecido que os gráficos de pizza e de rosca são difíceis para os humanos interpretarem corretamente e, na verdade, muitas vezes podem distorcer os dados. Evite usá-los sempre que possível. Stephen Few tem um artigo excelente sobre sua história e os perigos em [Save the Pies for Dessert] ([www.percetualedge.com/articles/08-21-07.pdf](http://www.perceptualedge.com/articles/08-21-07.pdf) (Guarde as pizzas para o fim de semana).

Ele explica a única ocasião em que os gráficos de pizza podem ser úteis: ao comparar relações de parte para o todo. Mas raramente isso é significativamente melhor do que, digamos, um gráfico de barras 100% empilhadas.

Outro artigo (e animação) interessante sobre gráficos de pizza pode ser encontrado no [site da Darkhorse Analytics](http://www.darkhorseanalytics.com/blog/salvaging-the-pie).

Se preferir, leia o ponto de vista contrário, [Why Tufte is flat-out wrong about pie charts](http://speakingppt.com/2013/03/18/why-tufte-is-flat-out-wrong-about-pie-charts/) (Por que Tufte está completamente errado sobre gráficos de pizza)

#### <a name="radial-gauges--kpis"></a>Medidores radiais e KPIs
![](media/power-bi-visualization-best-practices/power-bi-gauge.png)

Os medidores radiais parecem ser um bom visual para indicar o desempenho em relação a uma meta e são muito populares em dashboards executivos. No entanto, eles apresentam duas desvantagens principais. Assim como ocorre com os gráficos de pizza, é difícil de interpretar o ângulo da área sombreada em comparação com a linha completa de destino ou arco de 180°. Ele também usa muito espaço para mostrar uma única métrica.

Uma boa alternativa é um visual de KPI simples

![](media/power-bi-visualization-best-practices/power-bi-kpi.png)

Os KPIs mostram o valor, o status, a meta, a variação da meta e a tendência na mesma quantidade de espaço. A coloração verde ficará vermelha se a meta não estiver sendo atingida e poderá ficar amarela se alguma meta intermediária for atingida. É muito mais simples de ser lido e interpretado que o medidor.

Para obter mais informações, veja:

* [Tutorial: Gráficos de medidor radial no Power BI](power-bi-visualization-radial-gauge-charts.md)
* [Tutorial: KPIs no Power BI](power-bi-visualization-kpi.md)

## <a name="conclusion"></a>Conclusão
Agora é hora de colocar essas práticas recomendadas em ação.  Mantenha contato e compartilhe suas próprias práticas recomendadas. Não concorda com nossas recomendações ou descobriu um bom motivo para “quebrar as regras”?  Também gostaríamos muito de saber sua opinião.  

### <a name="book-recommendations"></a>Recomendações de literatura
Há muitos livros excelentes disponíveis hoje para ajudar as equipes a estudarem muito sobre as técnicas de design de visuais. O livro *Information Dashboard Design* (Design de dashboards de informações), de Stephen Few, é uma leitura obrigatória. Ele se aprofunda em mais detalhes em dois outros livros, *Show Me the Numbers* (Mostre-me os números) e *Now You See It* (Agora você pode ver). Few e outros autores se inspiraram de Edward R. Tufte, cujo livro *The Visual Display of Quantitative Information* (A exibição visual de informações quantitativas) é considerado um clássico na área. Tufte também escreveu *Visual Explanations* (Explicações visuais), *Envisioning Information* (Vislumbrando informações) e *Beautiful Evidence* (Linda evidência). O novo livro de Andy Kirk *Data Visualization: A Handbook for Data Driven Design* (Visualização de dados: um manual para o design controlado por dados) é outra excelente opção. Alguns outros autores recomendados são: Lachlan James, William McKnight e Boris Evelson (Forrester) da Darkhorse Analytics.

Mais perguntas? [Experimente a Comunidade do Power BI](http://community.powerbi.com/)

