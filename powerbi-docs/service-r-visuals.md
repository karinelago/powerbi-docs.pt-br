---
title: Criar visualizações e análise avançadas usando scripts do R no Power BI
description: Usar scripts do R no Power BI para criar visualizações e análise avançadas
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 05/02/2018
ms.author: davidi
LocalizationGroup: Visualizations
ms.openlocfilehash: fd4198bb6b826f8d4af22e83e313c4c0b8101024
ms.sourcegitcommit: 638de55f996d177063561b36d95c8c71ea7af3ed
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/17/2018
---
# <a name="creating-r-visuals-in-the-power-bi-service"></a>Criar visuais do R no serviço do Power BI
O serviço do Power BI dá suporte à exibição e interação com visuais criados com scripts do R. Os visuais criados com scripts do R, normalmente chamados de *visuais do R*, podem apresentar formatação e análise de dados avançadas, como previsão, usando o poder da análise e da visualização avançadas do R.

> [!NOTE]
> A [linguagem de programação R](https://www.r-project.org/) está entre as linguagens de programação mais amplamente usadas por estatísticos, cientistas de dados e analistas de negócios. A linguagem R tem uma comunidade de software livre que oferece mais de 7.000 pacotes complementares, como bem como os amplamente utilizados [Grupos de Usuários do R](http://msdsug.microsoft.com/). A versão do R implantada no serviço do Power BI é a *Revolution R Open 3.2.2.*
> 
> 

A imagem a seguir mostra um dashboard do Power BI com uma coleção de visuais do R usados para análise avançada.

![](media/service-r-visuals/r-visuals-service_1.png)

Os visuais do R são criados em um [relatório do Power BI Desktop](desktop-get-the-desktop.md), como o relatório mostrado na imagem a seguir.

![](media/service-r-visuals/r-visuals-service_2a.png)

Depois que o relatório for criado no **Power BI Desktop**, será possível publicar o relatório contendo um ou mais visuais do R no serviço do Power BI. Atualmente, os visuais do R só podem ser criados no **Power BI Desktop** e, em seguida, publicados no serviço do Power BI. Para obter mais informações sobre como criar visuais do R, veja [Create Power BI visuals using R (Power BI Desktop)](desktop-r-visuals.md) (Criar visuais do Power BI usando o R [Power BI Desktop]).

Observe que, no serviço, nem todos os pacotes do R têm suporte. Confira os pacotes com suporte ao final deste artigo para obter a lista dos pacotes atualmente com suporte no serviço do Power BI.

Você pode baixar este [arquivo de exemplo do Power BI Desktop](http://download.microsoft.com/download/D/9/A/D9A65269-D1FC-49F8-8EC3-1217E3A4390F/RVisual_correlation_plot_sample SL.pbix) (arquivo .pbix) que contém alguns visuais do R para ver como isso funciona e testá-lo.

Na maioria dos casos, os visuais do R criados no **Power BI Desktop** e publicados no serviço do Power BI, se comportam como qualquer outro visual do serviço do Power BI: é possível interagir, filtrar, segmentá-los e fixá-los em um dashboard ou compartilhá-los com outras pessoas. Para obter mais informações sobre como compartilhar dashboards e visuais, veja [compartilhar um dashboard com seus colegas e com outras pessoas](service-share-dashboards.md). Uma diferença entre os visuais do R e outros visuais é que aqueles não podem mostrar dicas de ferramenta e não podem ser usados para filtrar outros visuais.

Como você pode ver na imagem a seguir, os visuais do R no serviço do Power BI, estejam eles em dashboards ou relatórios, na maioria dos casos, aparecem e se comportam como qualquer outro visual, e os usuários não precisam conhecer o script do R subjacente que criou o visual.

![](media/service-r-visuals/r-visuals-service_3a.png)

## <a name="r-scripts-security"></a>Segurança de scripts do R
Os visuais do R são criados com base nos scripts do R que, potencialmente, podem conter código com riscos de segurança ou privacidade.

Esses riscos existem, principalmente, na fase de criação, quando o autor do script executa o script no próprio computador.

O serviço do Power BI aplica uma tecnologia de *área restrita* para proteger os usuários e o serviço contra riscos de segurança.

Essa abordagem de *área restrita* impõe algumas restrições sobre os scripts do R em execução no serviço do Power BI, como o acesso à Internet ou o acesso a outros recursos que não são necessários para criar o visual do R.

## <a name="r-scripts-error-experience"></a>Experiência de erro com scripts do R
Quando há um erro em um script do R, o visual do R não é plotado e uma mensagem de erro é exibida. Para obter detalhes sobre o erro, selecione **Ver detalhes** no erro do visual do R na tela, conforme mostrado na imagem a seguir.

![](media/service-r-visuals/r-visuals-service_4.png)

Como outro exemplo, a imagem a seguir mostra a mensagem de erro que aparece quando um script do R não é executado corretamente devido à ausência de um pacote do R no Azure.

![](media/service-r-visuals/r-visuals-service_5.png)

## <a name="licensing"></a>Licenças
Os visuais do R exigem uma licença [Power BI Pro](service-self-service-signup-for-power-bi.md) para serem renderizados em relatórios, na atualização, no filtro e no filtro cruzado. Para obter mais informações sobre licenças do Power BI Pro e como elas diferem das licenças gratuitas, veja [Conteúdo do Power BI Pro – o que é isto?](service-premium.md)

Os usuários da versão gratuita do Power BI só poderão consumir blocos compartilhados com eles. Veja [Comprando o Power BI Pro](service-admin-purchasing-power-bi-pro.md) para obter mais informações.

A tabela a seguir descreve as funcionalidades dos visuais do R com base em licenciamento.

![](media/service-r-visuals/r-visuals-service_6a.png)

## <a name="known-limitations"></a>Limitações Conhecidas
Os visuais do R no serviço do Power BI têm algumas limitações:

* O suporte para os visuais do R é limitado aos pacotes identificados na página a seguir <make this a link to the supported packages page per my excel>. Atualmente, não há suporte para pacotes personalizados.
* Limitações de tamanho de dados – os dados usados pelo visual R para plotar são limitados a 150.000 linhas. Se mais de 150.000 linhas forem selecionadas, somente as primeiras 150.000 linhas serão usadas e uma mensagem será exibida na imagem.
* Limite de tempo de cálculo – se um cálculo do visual do R exceder 60 minutos, o script atingirá o tempo limite, resultando em erro.
* Visuais R são atualizados após atualizações de dados, filtragem e realce. No entanto, a própria imagem não é interativa e não dá suporte a dicas de ferramenta.
* Visuais R respondem ao realce de outros elementos visuais, mas você não pode clicar em elementos no visual R para fazer filtragem cruzada de outros elementos.
* Atualmente, não há suporte nos visuais do R para o tipo de dados *Hora*. Em vez disso, use Data/Hora.
* Os visuais do R não são exibidos quando se usa o recurso **Publicar na Web**.
* Atualmente, os visuais do R não são impressos com a impressão de dashboards e relatórios
* Atualmente, não há suporte para os visuais do R no modo DirectQuery do Analysis Services
* As fontes de chinês, japonês e coreano exigem todas as etapas adicionais a seguir para funcionar corretamente no serviço do Power BI:
  
  * Primeiro, instale o pacote de R *showtext* e todas as suas dependências. Você pode fazer isso executando o seguinte script:
    
        *install.packages("showtext")*
  * Em seguida, adicione a seguinte linha no início do script de R:
    
        powerbi_rEnableShowTextForCJKLanguages =  1

## <a name="overview-of-r-packages"></a>Visão geral de pacotes de R
Pacotes de R são coleções de funções de R, dados e código compilado combinados em um formato bem definido. Quando o R é instalado, ele vem com um conjunto padrão de pacotes e outros pacotes estão disponíveis para download e para instalação. Depois de instalados, os pacotes de R devem ser carregados para a sessão a ser usada. A principal origem de pacotes de R gratuitos é o CRAN, a [Rede Completa de Arquivos do R](https://cran.r-project.org/web/packages/available_packages_by_name.html).

O **Power BI Desktop** pode usar qualquer tipo de pacotes de R sem limitação. É possível instalar pacotes de R para uso no **Power BI Desktop** por conta própria (usando o [IDE RStudio](https://www.rstudio.com/), por exemplo).

Os pacotes encontrados na seção **Pacotes com suporte** encontrada **neste artigo** dão suporte aos visuais do R no [serviço do Power BI](service-r-packages-support.md). Se você não encontrar um pacote do seu interesse na lista de pacotes com suporte, será possível solicitar o suporte do pacote. Consulte [Pacotes do R no serviço do Power BI](service-r-packages-support.md) para obter informações sobre como solicitar suporte.

### <a name="requirements-and-limitations-of-r-packages"></a>Requisitos e limitações de pacotes de R
Há alguns requisitos e limitações dos pacotes de R:

* O serviço do Power BI, na sua maioria, dá suporte a pacotes de R com licenças de software gratuitas e de software livre como GPL-2, GPL-3, MIT+ e assim por diante.
* O serviço do Power BI dá suporte a pacotes publicados no CRAN. O serviço não dá suporte a pacotes de R personalizados ou privados. Recomendamos que os usuários disponibilizem seus pacotes privados no CRAN antes de solicitar que o pacote esteja disponível no serviço do Power BI.
* O **Power BI Desktop** tem duas variações para pacotes de R:
  
  * Para visuais do R, é possível instalar qualquer pacote, incluindo pacotes de R personalizados
  * Para visuais personalizados do R, há suporte somente para pacotes CRAN públicos para instalação automática dos pacotes
* Por motivos de privacidade e segurança, atualmente não damos suporte a pacotes de R que forneçam consultas de cliente-servidor por meio da World Wide Web (como RgoogleMaps) no serviço. A rede está bloqueada para essas tentativas. Consulte [Pacotes do R no serviço do Power BI](service-r-packages-support.md) para obter uma lista de pacotes do R com e sem suporte.
* O processo de aprovação para a inclusão de um novo pacote de R tem uma árvore de dependências; algumas delas que precisam ser instaladas no serviço não têm suporte.

### <a name="supported-packages"></a>Pacotes com suporte:
Para obter uma lista longa de pacotes do R com suporte (e a lista curta de pacotes sem suporte), consulte o seguinte artigo:

* [Pacotes do R no serviço do Power BI](service-r-packages-support.md)

