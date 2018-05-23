---
title: Usando páginas de dica de ferramenta de relatório no Power BI
description: As páginas de dica de ferramenta no Power BI Desktop permitem que você crie dicas de ferramenta sofisticadas que são exibidas ao passar o mouse sobre visuais dos seus relatórios
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 03/06/2018
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: 1f53b0efc2195221fbcbe45f03102d2c98e8eef3
ms.sourcegitcommit: 998b79c0dd46d0e5439888b83999945ed1809c94
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/17/2018
---
# <a name="create-tooltips-based-on-report-pages-in-power-bi-desktop-preview"></a>Criar dicas de ferramenta com base nas páginas de relatório no Power BI Desktop (versão prévia)
Você pode criar **dicas de ferramentas de relatório** visualmente sofisticadas que aparecem ao passar o mouse sobre visuais, com base nas páginas de relatório que você cria no **Power BI Desktop**. Ao criar uma página de relatório que sirva como dica de ferramenta, as dicas de ferramenta personalizadas poderão incluir elementos visuais, imagens e qualquer outra coleção de itens que você criar na página de relatório. 

![Dicas de ferramenta de relatório do Power BI Desktop](media/desktop-tooltips/desktop-tooltips_00a.png)

Você pode criar tantas páginas de dica de ferramenta quanto desejar. Cada página de dica de ferramenta pode ser associada a um ou mais campos do seu relatório, para que, ao passar o mouse sobre um visual que inclua o campo selecionado, a dica de ferramenta criada em sua página de dica de ferramenta é exibida, filtrada com base no ponto de dados sobre o qual o mouse está passando. 

Há inúmeras coisas interessantes que você pode fazer com dicas de ferramentas de relatório. Vamos ver como criar dicas de ferramenta e o que você deve fazer para configurá-las.

### <a name="enable-the-tooltips-preview"></a>Habilitar a versão prévia das dicas de ferramenta 
Como as dicas de ferramentas de relatório estão atualmente em versão prévia, antes de criá-las é necessário habilitá-las. Para habilitar o recurso das dicas de ferramentas de relatório, que está em versão prévia, selecione **Arquivo > Opções e Configurações > Opções > Recursos de Visualização** no Power BI Desktop e, em seguida, marque a caixa de seleção ao lado de **Dicas de ferramenta de página de relatório**. 

![Habilitar o recurso em versão prévia das dicas de ferramentas de relatório](media/desktop-tooltips/desktop-tooltips_01.png)

Você precisará reiniciar o **Power BI Desktop** depois de habilitar a versão prévia das dicas de ferramentas de relatório.

## <a name="create-a-report-tooltip-page"></a>Criar uma página de dica de ferramenta de relatório
Para começar, crie uma nova página de relatório clicando no botão **+**, que se encontra na parte inferior da tela do **Power BI Desktop**, na área de guias da página. O botão fica ao lado da última página no relatório. 

![Criar uma nova página de relatório para a dica de ferramenta](media/desktop-tooltips/desktop-tooltips_02.png)

As dicas de ferramenta podem ser de qualquer tamanho, mas tenha em mente elas passam sobre a tela de relatório, portanto convém mantê-las razoavelmente pequenas. Veja no painel **Formato**, no cartão **Tamanho da Página**, um novo modelo de tamanho de página chamado *Dica de ferramenta*. Ele fornece um tamanho de tela de página de relatório pronto para a dica de ferramenta.

![Escolher dica de ferramenta no tamanho da página para uma dica de ferramenta pronta para usar](media/desktop-tooltips/desktop-tooltips_03.png)

Por padrão, o **Power BI Desktop** ajusta a tela de relatório ao espaço disponível na página. Isso é geralmente adequado, mas não no caso das dicas de ferramenta. Para ter uma noção melhor da aparência da dica de ferramenta quando você terminar, altere a **Exibição de Página** para o tamanho real. 

Para fazer isso, selecione a guia **Exibir** na faixa de opções. Depois, selecione **Exibição de Página > Tamanho Real**, conforme mostrado na imagem a seguir.

![Mostrar a página de relatório no tamanho real para facilitar na criação de dica de ferramenta](media/desktop-tooltips/desktop-tooltips_04.png)

Você também pode nomear a página de relatório para que a finalidade fique mais clara. Basta selecionar o cartão **Informações da Página** no painel **Formatar** e, em seguida, digitar o nome no campo **Nome** que você encontrar. Na imagem a seguir o nome do relatório de dica de ferramenta é *Tooltip 1*, mas você pode colocar o nome que achar conveniente.

![Nomear a página de relatório de dica de ferramenta](media/desktop-tooltips/desktop-tooltips_05.png)

Em seguida, você pode criar os visuais que deseja que apareçam na dica de ferramenta. Na imagem a seguir, há dois cartões e um gráfico de barras clusterizado na página de dica de ferramenta, juntamente com uma cor da tela de fundo para a página propriamente dita, além de telas de fundo de cada um dos visuais, para dar a aparência que queremos.

![Dicas de ferramenta de relatório do Power BI Desktop](media/desktop-tooltips/desktop-tooltips_06.png)

Há mais etapas a serem concluídas antes que a página de relatório de dica de ferramenta esteja pronta para funcionar como uma dica de ferramenta. É necessário configurar a página de dica de ferramenta de algumas maneiras, conforme descrito na próxima seção. 

## <a name="configure-your-tooltip-report-page"></a>Configurar a página de relatório de dica de ferramenta

Com a página de relatório de dica de ferramenta criada, agora é necessário configurar a página para que o **Power BI Desktop** a registre como uma dica de ferramenta e para garantir que ela apareça sobre os elementos visuais corretos.

Em primeiro lugar, você precisa mudar o controle deslizante **Dica de ferramenta** para a posição **Ativar**, no cartão **Informações da Página**, para fazer com que a página se torne uma dica de ferramenta. 

![Ativar o controle deslizante de dica de ferramenta para indicar que a página é uma dica de ferramenta](media/desktop-tooltips/desktop-tooltips_07.png)

Depois de ativar esse controle deslizante, você pode especificar os campos para os quais deseja que a dica de ferramenta de relatório seja exibida. Para os visuais do relatório que incluem o campo que você especificar, a dica de ferramenta será exibida. Você especifica quais campos se aplicam arrastando-os para o bucket **Campos de dicas de ferramenta**, que pode ser encontrado na seção **Campos** do painel **Visualizações**. Na imagem a seguir, o campo *SalesAmount* foi arrastado para o bucket **Campos de dicas de ferramenta**.

![Adicionar campos para determinar o local em que a dica de ferramenta aparecerá](media/desktop-tooltips/desktop-tooltips_08.png)
 
Você pode incluir campos categóricos e numéricos no bucket **Campos de dicas de ferramenta**, incluindo medidas.

Depois de concluído, a página de relatório de dica de ferramenta que você criou será usada como dica de ferramenta nos visuais de relatório que usarem os campos colocados no bucket **Campos de dicas de ferramenta**, substituindo a dica de ferramenta padrão do Power BI.

## <a name="manually-setting-a-report-tooltip"></a>Configuração manual de uma dica de ferramenta de relatório

Além de criar uma dica de ferramenta que aparece automaticamente ao passar o mouse sobre um visual que contém o campo especificado, você também pode definir uma dica de ferramenta manualmente. 

Todos os visuais que são compatíveis com dicas de ferramentas de relatório agora têm um cartão **Dica de ferramenta** no painel **Formatação**. 

Para definir uma dica de ferramenta manualmente, selecione o visual para o qual você deseja especificar a dica de ferramenta manual e, em seguida, no painel **Visualizações**, selecione a seção **Formatar** e expanda o cartão **Dica de ferramenta**.

![Cartão de dica de ferramenta para um visual individual](media/desktop-tooltips/desktop-tooltips_09.png)

Em seguida, na lista suspensa **Página**, selecione a página de dica de ferramenta que você deseja usar para o visual selecionado. Observe que apenas as páginas de relatório especificadas como páginas de **Dica de ferramenta** aparecem na caixa de diálogo.

![Selecionar uma página de dica de ferramenta para a dica de ferramenta manual](media/desktop-tooltips/desktop-tooltips_10.png)

A possibilidade de definir manualmente uma dica de ferramenta é muito útil. Você pode definir uma página em branco para uma dica de ferramenta e, assim, substituir a seleção de dica de ferramenta padrão do Power BI. Outro uso é quando você não quer que a dica de ferramenta selecionada automaticamente pelo Power BI seja a dica de ferramenta. Por exemplo, se você tiver um visual que inclui dois campos, e cada um desses campos tiver uma dica de ferramenta associada, o Power BI selecionará apenas uma para mostrar. Caso isso não seja conveniente, você poderá selecionar manualmente qual dica de ferramenta deverá ser exibida.

## <a name="reverting-to-default-tooltips"></a>Revertendo para as dicas de ferramentas padrão

Se você criar uma dica de ferramenta manual para um visual, mas decidir que quer a dica de ferramenta padrão novamente, será sempre possível retornar para a dica de ferramenta padrão oferecida pelo Power BI. Para fazer isso, quando um visual é selecionado e o cartão **Dica de ferramenta** é expandido, basta selecionar *Auto*, na lista suspensa **Página**, para voltar para o padrão.

![Voltar para a dica de ferramenta padrão para um visual](media/desktop-tooltips/desktop-tooltips_11.png)

## <a name="custom-report-tooltips-and-line-charts"></a>Dicas de ferramenta de relatório e gráficos de linhas personalizados

Há algumas considerações para ter em mente quando as dicas de ferramentas de relatório estiverem interagindo com visuais de gráfico de linhas e com visuais ao fazer realce cruzado.

### <a name="report-tooltips-and-line-charts"></a>Dicas de ferramenta de relatório e gráficos de linhas

Ao exibir uma dica de ferramenta de relatório para um gráfico de linhas, só é possível exibir uma dica de ferramenta para todas as linhas do gráfico. Esse comportamento é semelhante ao da dica de ferramenta padrão para gráficos de linhas, que também exibe apenas uma dica de ferramenta. 

Isso ocorre porque o campo da legenda não é passado como um filtro para a dica de ferramenta. Na imagem a seguir, a dica de ferramenta que está sendo exibida está mostrando todas as unidades vendidas naquele dia, entre todas as três classes exibidas na dica de ferramenta de relatório (neste exemplo, Deluxe, Economy e Regular). 

![Gráficos de linhas mostram somente dados agregados de dica de ferramenta](media/desktop-tooltips/desktop-tooltips_12.png)

### <a name="report-tooltips-and-cross-highlighting"></a>Dicas de ferramentas de relatório e realce cruzado

Quando se faz realce cruzado em um visual em um relatório, as dicas de ferramentas de relatório sempre mostram os dados de realce cruzado, mesmo que você esteja passando o mouse sobre a seção esmaecida do ponto de dados. Na imagem a seguir, o mouse está passando sobre a seção esmaecida do gráfico de barras (a seção que não está realçada), mas a dica de ferramenta do relatório ainda mostra os dados da parte realçada daquele ponto de dados (os dados realçados).

![Dicas de ferramentas de relatório mostram dados realçados quando ocorre realce cruzado](media/desktop-tooltips/desktop-tooltips_13.png)



## <a name="limitations-and-considerations"></a>Limitações e considerações
Nesta versão prévia das **dicas de ferramenta** de relatório, há algumas limitações e considerações a serem lembradas.

* Não há suporte para dicas de ferramentas de relatório ao exibir relatórios em aplicativos móveis ou em ambientes inseridos, incluindo Publicar na Web. 
* Dicas de ferramentas de relatório não são compatíveis com visuais personalizados. 
* Atualmente não há suporte para usar clusters como campos que podem ser mostrados nas dicas de ferramentas de relatório. 
* Ao escolher um campo a ser mostrado como dicas de ferramentas de relatório, usando-o em vez de usar uma categoria, os visuais que contém esse campo só mostrarão a dica de ferramenta especificada quando houver correspondência entre os campos selecionados e o resumo. 


## <a name="next-steps"></a>Próximas etapas
Para obter mais informações sobre os recursos que são semelhantes ou interagem com dicas de ferramentas de relatório, consulte os seguintes artigos:

* [Usar o detalhamento no Power BI Desktop](desktop-drillthrough.md)
* [Exibir um bloco do dashboard ou visual do relatório no modo de Foco](service-focus-mode.md)

