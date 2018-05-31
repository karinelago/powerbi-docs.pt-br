---
title: Criar mapa do ArcGIS pelo ESRI no Power BI
description: 'Criar um mapa do ArcGIS pelo ESRI no Power BI '
services: powerbi
documentationcenter: ''
author: mihart
manager: kfile
backup: lukaszp
editor: ''
tags: ''
featuredvideoid: EKVvOZmxg9s
qualityfocus: no
qualitydate: ''
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 02/28/2018
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: a71073c6e4f5962e8cdd6ddfb92d41628d8799c1
ms.sourcegitcommit: 493f160d04ed411ff4741c599adc63ba1f65230f
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33813336"
---
# <a name="arcgis-maps-in-power-bi-service-and-power-bi-desktop-by-esri"></a>Mapas do ArcGIS no serviço do Power BI e no Power BI Desktop pelo ESRI
Este tutorial foi escrito do ponto de vista de uma pessoa que está criando um mapa do ArcGIS. Depois que um criador compartilha um mapa do ArcGIS com um colega, esse colega pode exibir e interagir com o mapa, mas não salvar as alterações. Para saber mais sobre como exibir um mapa do ArcGIS, consulte [Interagindo com mapas do ArcGIS](power-bi-visualizations-arcgis.md).

A combinação de mapas do ArcGIS e do Power BI leva o mapeamento para além da apresentação de pontos em um mapa, para um nível totalmente novo. Escolha entre mapas de base, tipos de local, temas, estilos de símbolo e camadas de referência para criar visualizações de mapas informativas e bonitas. A combinação das camadas de dados competentes em um mapa com análise espacial transmite uma compreensão mais ampla dos dados na sua visualização.

 Embora não seja possível criar mapas do ArcGIS em um dispositivo móvel, é possível exibir e interagir com ele. Consulte [Interagindo com mapas do ArcGIS](power-bi-visualizations-arcgis.md).

> [!TIP]
> GIS significa Geographic Information Science (Ciência de Informações Geográficas).


O exemplo a seguir usa uma tela cinza escura para mostrar as vendas regionais como um mapa de dados em uma camada demográfica do rendimento médio disponível de 2016. Como você verá durante a leitura, o uso do ArcGIS Maps oferece capacidade de mapeamento aprimorada quase ilimitada, dados demográficos e visualizações de mapa ainda mais atraentes para que você possa fazer a melhor apresentação possível.

![](media/power-bi-visualization-arcgis/power-bi-intro-arcgis.png)

> [!TIP]
> Visite a [página do ESRI no Power BI](https://www.esri.com/powerbi) para ver vários exemplos e ler depoimentos. E, em seguida, consulte a [Página de Introdução do ArcGIS Maps para o Power BI](https://doc.arcgis.com/en/maps-for-powerbi/get-started/about-maps-for-power-bi.htm) no ESRI.

## <a name="user-consent"></a>Consentimento do usuário
O ArcGIS Maps for Power BI é fornecido pela Esri (www.esri.com). O uso do ArcGIS Maps para Power BI está sujeito aos termos e à política de privacidade da Esri. Os usuários do Power BI que queiram usar o ArcGIS Maps para o Power BI deverão aceitar a caixa de diálogo de consentimento.

**Recursos**

[Termos](https://go.microsoft.com/fwlink/?LinkID=826322)

[Política de privacidade](https://go.microsoft.com/fwlink/?LinkID=826323)

[Página do produto ArcGIS Maps para Power BI](https://www.esri.com/powerbi)

<br/>

## <a name="enable-arcgis-map"></a>Habilitar mapa do ArcGIS
O ArcGIS Maps está disponível no serviço do Power BI, no Power BI Desktop e no Power BI para Celulares. Este artigo fornece instruções para as versões Desktop e de serviço.

### <a name="enable-the-arcgis-map-in-power-bi-service-apppowerbicom"></a>Habilitar o mapa do ArcGIS ***no serviço do Power BI (app.powerbi.com)***
Este tutorial usa o exemplo de [Análise de Varejo](sample-retail-analysis.md). Para habilitar o **ArcGIS Maps para o Power BI**:

1. Na seção superior direita da barra de menu, selecione o ícone de engrenagem e abra as **Configurações**
   
    ![](media/power-bi-visualization-arcgis/power-bi-settings.png)
2. Marque a caixa de seleção **ArcGIS Maps para Power BI**. Você precisará reiniciar o Power BI depois de fazer a seleção.
   
    ![](media/power-bi-visualization-arcgis/power-bi-use-arcgis-new.png)
3. Abra um relatório no [Modo de Exibição de Edição](service-reading-view-and-editing-view.md) e selecione o ícone do ArcGIS Maps para o Power BI no painel Visualizações.
   
    ![](media/power-bi-visualization-arcgis/power-bi-viz-pane2.png)
4. O Power BI adiciona um modelo de mapa do ArcGIS vazio na tela do relatório.
   
   ![](media/power-bi-visualization-arcgis/power-bi-esri-placeholder2new.png)

<br/>

## <a name="create-an-arcgis-map-visual"></a>Criar um visual de mapa do ArcGIS
Assista ao Will criando algumas visualizações diferentes dos mapas do ArcGIS. Em seguida, use as etapas abaixo para tentar o mesmo por conta própria usando o [exemplo de Análise de Varejo](sample-datasets.md).

<iframe width="560" height="315" src="https://www.youtube.com/embed/EKVvOZmxg9s" frameborder="0" allowfullscreen></iframe>

1. No painel **Campos**, arraste um campo de dados para os buckets **Localização**, **Latitude** e/ou **Longitude**. Neste exemplo, estamos usando **Repositório > Cidade**.
   
   > [!NOTE]
   > O ArcGIS Maps para o Power BI detectará automaticamente se é melhor exibir os campos selecionados como uma forma ou um ponto em um mapa. Você pode ajustar o padrão nas configurações (veja abaixo).
   > 
   > 
   
    ![](media/power-bi-visualization-arcgis/power-bi-fields-pane3new.png)
2. Converta a visualização em um ArcGIS Map selecionando o modelo no painel Visualizações ![](media/power-bi-visualization-arcgis/power-bi-arcgis-template.png).
3. No painel **Campos**, arraste uma medida para o bucket **Tamanho** para ajustar como os dados são mostrados. Neste exemplo, estamos usando **Vendas > Vendas do último ano**.
   
    ![](media/power-bi-visualization-arcgis/power-bi-esri-point-map-size2new.png)

## <a name="settings-and-formatting-for-arcgis-maps"></a>Configurações e formatação de mapas do ArcGIS
Para acessar os recursos de formatação do **ArcGIS Maps para Power BI**:

1. Acesse recursos adicionais, selecionando as elipses no canto superior direito da visualização e escolhendo **Editar**.
   
   ![](media/power-bi-visualization-arcgis/power-bi-edit2.png)
   
   Os recursos disponíveis são exibidos na parte superior da visualização. Cada recurso, quando selecionado, abre um painel de tarefas que fornece opções detalhadas.<br/>
   
   ![](media/power-bi-visualization-arcgis/power-bi-esri-features-new.png)
   
   > [!NOTE]
   > Para obter mais informações sobre as configurações e os recursos, veja **Documentação detalhada** abaixo.
   > 
   > 
2. Para retornar ao relatório, selecione **Voltar ao Relatório** no canto superior esquerdo da tela do relatório.

<br/>

## <a name="detailed-documentation"></a>Documentação detalhada
A **Esri** oferece uma [documentação abrangente](https://go.microsoft.com/fwlink/?LinkID=828772) sobre o conjunto de recursos do **ArcGIS Maps para Power BI**.

## <a name="features-overview"></a>Visão geral dos recursos
### <a name="base-maps"></a>Mapas base
Quatro mapas base são fornecidos: Telas Cinza Escuro, Telas Cinza Claro, OpenStreetMap e Ruas.  Ruas é o mapa base padrão do ArcGIS.

Para aplicar um mapa base selecione-o no painel de tarefas.

![](media/power-bi-visualization-arcgis/power-bi-esri-base-maps-new.png)

### <a name="location-type"></a>Tipo de Localização
O ArgGIS Maps para Power BI detecta automaticamente a melhor maneira de mostrar os dados no mapa. Ele escolhe entre Pontos ou Limites. As opções de Tipo de Localização permitem ajustar essas seleções.

![](media/power-bi-visualization-arcgis/power-bi-esri-location-types-new.png)

**Limites** apenas funcionará se os dados contiverem valores geográficos padrão. O Esri detecta automaticamente a forma para mostrar no mapa. Os valores geográficos padrão incluem países, províncias, CEP, etc. Mas, da mesma forma que com o geocódigo, o Power BI pode não detectar que o campo deve ser um limite por padrão ou ele pode não ter um limite para seus dados.  

### <a name="map-theme"></a>Tema do Mapa
Quatro temas de mapa são fornecidos. Os temas Somente Localização e Tamanho são escolhidos automaticamente com base nos campos que você associou ao local e adicionou ao bucket **Tamanho** no painel Campos do Power BI. No momento, estamos usando **Tamanho**, então vamos alterar para **Mapa de calor**.  

![](media/power-bi-visualization-arcgis/power-bi-esri-map-theme-new.png)

<table>
<tr><th>Tema</th><th>Descrição</th>
<tr>
<td>Somente localização</td>
<td>Plota pontos de dados ou limites preenchidos no mapa com base nas configurações em Tipo de Localização.</td>
</tr>
<tr>
<td>Mapa de calor</td>
<td>Plota um gráfico de intensidade de dados no mapa.</td>
</tr>
<tr>
<td>Tamanho</td>
<td>Plota pontos de dados no mapa dimensionados com base no valor do bucket de tamanho no painel Campos.</td>
</tr>
<tr>
<td>Clustering</td>
<td>Plota a contagem de pontos de dados em regiões do mapa. </td>
</tr>
</table>


### <a name="symbol-style"></a>Estilo de Símbolo
Os estilos de símbolo permitem ajustar como os dados são apresentados no mapa. Os estilos de símbolo são contextuais com base no Tipo de Localização e no Tema do Mapa selecionados. O exemplo abaixo mostra o tipo Localização definido como **Tamanho** e vários ajustes na transparência, no estilo e no tamanho.

![](media/power-bi-visualization-arcgis/power-bi-esri-symbol-style-new.png)

### <a name="pins"></a>Marcadores
Chame a atenção para pontos em seu mapa ao adicionar marcadores.  

1. Selecione a guia **Marcadores**.
2. Digite palavras-chave (como endereços, locais e pontos de interesse) na caixa de pesquisa e selecione uma opção na lista suspensa. Um símbolo é exibido no mapa e o mapa é ampliado na localização. Os resultados da pesquisa são salvos como cartões de localização no painel Marcadores. Você pode salvar até 10 cartões de localização.
   
   ![](media/power-bi-visualization-arcgis/power-bi-pin-arcgis-newer.png)
3. O Power BI adiciona um marcador a esse local e você pode alterar a cor do marcador.
   
   ![](media/power-bi-visualization-arcgis/power-bi-pin-color-new.png)
4. Adicionar e excluir marcadores.
   
   ![](media/power-bi-visualization-arcgis/power-bi-pin3.png)

### <a name="drive-time"></a>Tempo de viagem
O painel Tempo de viagem permite selecionar uma localização e, em seguida, determinar quais outros recursos do mapa estão dentro de um raio ou tempo de viagem especificado.  
    ![](media/power-bi-visualization-arcgis/power-bi-esri-drive-time.png)

1. Selecione a guia **Tempo de viagem** e escolha a ferramenta de seleção única ou múltipla. Faça uma seleção única do marcador de Washington D.C.
    ![](media/power-bi-visualization-arcgis/power-bi-esri-single-select.png)
   
   > [!TIP]
   > Será mais fácil selecionar um local se você ampliar o mapa (usando o ícone +).
   > 
   > 
2. Digamos que você esteja viajando para Washington D.C. daqui a alguns dias e deseja descobrir quais lojas estão dentro de uma distância de viagem razoável. Altere a área de Pesquisa para **Raio** e Distância para **50** milhas e selecione OK.    
   
    ![](media/power-bi-visualization-arcgis/power-bi-esri-drive-time-radius.png)
3. O raio é mostrado em roxo. Selecione uma localização para exibir seus detalhes. Opcionalmente, formate o raio alterando a cor e o contorno.
   
    ![](media/power-bi-visualization-arcgis/power-bi-esri-drive-time.png)

### <a name="reference-layer"></a>Camada de Referência
#### <a name="reference-layer---demographics"></a>Camada de Referência – dados demográficos
O ArcGIS Maps para Power BI oferece uma seleção de camadas demográficas que ajudam a contextualizar os dados do Power BI.

1. Selecione a guia **Camada de Referência** e escolha **Dados demográficos**.
2. Cada camada listada tem uma caixa de seleção. Adicione uma marca de seleção para adicionar essa camada ao mapa.  Neste exemplo, adicionamos a receita média da casa.<br/>
   
    ![](media/power-bi-visualization-arcgis/power-bi-esri-reference-layer-demographic.png)
3. Cada camada também é interativa. Assim como é possível focalizar uma bolha para ver os detalhes, você pode clicar em uma área sombreada no mapa para ver os detalhes.<br/>
   
    ![](media/power-bi-visualization-arcgis/power-bi-esri-reference-layer-details.png)

#### <a name="reference-layer---arcgis"></a>Camada de Referência – ArcGIS
O ArcGIS Online oferece às organizações a capacidade de publicar mapas públicos da Web. Além disso, a Esri fornece um conjunto estruturado de mapas da Web por meio do Living Atlas. Na guia ArcGIS, você pode pesquisar todos os mapas públicos da Web ou os mapas do Living Atlas e adicioná-los no mapa como camadas de referência.

1. Selecione a guia **Camada de Referência** e escolha **ArcGIS**.
2. Insira os termos de pesquisa e selecione uma camada do mapa. Neste exemplo, escolhemos Distritos congressionais dos Estados Unidos.
   
    ![](media/power-bi-visualization-arcgis/power-bi-esri-demographics-esri2-new.png)
3. Para ver os detalhes, selecione uma área sombreada para abrir *Selecionar na camada de referência*: e use a ferramenta de seleção de camada de referência para selecionar limites ou objetos na camada de referência.

<br/>

## <a name="selecting-data-points"></a>Selecionando pontos de dados
O ArcGIS Maps para Power BI permite três modos de seleção.

Altere o modo de seleção usando as opções:

![](media/power-bi-visualization-arcgis/power-bi-esri-selection-tools2.png)

![](media/power-bi-visualization-arcgis/power-bi-esri-selection-single2.png) Selecionar pontos de dados individuais.

![](media/power-bi-visualization-arcgis/power-bi-esri-selection-marquee2.png) Desenha um retângulo no mapa e seleciona os pontos de dados contidos.

![](media/power-bi-visualization-arcgis/power-bi-esri-selection-reference-layer2.png) Permite que os limites ou polígonos nas camadas de referência sejam usados para selecionar os pontos de dados contidos.

> [!NOTE]
> No máximo, 250 pontos de dados podem ser selecionados por vez.
> 
> 

<br/>

## <a name="getting-help"></a>Obtendo ajuda
A **Esri** oferece uma [documentação abrangente](https://go.microsoft.com/fwlink/?LinkID=828772) sobre o conjunto de recursos do **ArcGIS Maps para Power BI**.

Você pode fazer perguntas, encontrar as informações mais recentes, reportar problemas e encontrar respostas no [thread da comunidade do Power BI relacionado ao **ArcGIS Maps para o Power BI**](https://go.microsoft.com/fwlink/?LinkID=828771).

Se você tiver alguma sugestão de melhoria, envie-a para a [Lista de ideias do Power BI](https://ideas.powerbi.com).

<br/>

## <a name="managing-use-of-arcgis-maps-for-power-bi-within-your-organization"></a>Gerenciando o uso do ArcGIS Maps para Power BI em sua organização
O Power BI oferece aos usuários, administradores de locatários e administradores de TI a capacidade de decidir se desejam usar o ArcGIS Maps para Power BI.

**Opções do Usuário** No Power BI Desktop, os usuários podem parar de usar o ArcGIS Maps para o Power BI ao desabilitá-lo na guia de segurança em **Opções**. Quando desabilitado, o ArcGIS Maps não será carregado por padrão.

![](media/power-bi-visualization-arcgis/power-bi-desktop-security-dialog2.png)

No serviço do Power BI, os usuários podem parar de usar os Mapas do ArcGIS para o Power BI desabilitando-os na guia Mapas do ArcGIS para o Power BI em Configurações do usuário. Quando desabilitado, o ArcGIS Maps não será carregado por padrão.

![](media/power-bi-visualization-arcgis/power-bi-use-arcgis-new.png)

**Opções do administrador de locatários** No PowerBI.com, os administradores de locatários podem impedir que todos os usuários locatários usem o ArcGIS Maps para Power BI desabilitando-o. Quando isso acontece, o Power BI deixa de exibir o ícone do ArcGIS Maps para Power BI no painel de visualizações.

![](media/power-bi-visualization-arcgis/power-bi-arcgis-admin-portal2.png)

**Opções do administrador de TI** O Power BI Desktop dá suporte ao uso de **Política de Grupo** para desabilitar o ArcGIS Maps para Power BI entre os computadores implantados em toda a organização.

<table>
<tr><th>Atributo</th><th>Valor</th>
</tr>
<tr>
<td>chave</td>
<td>Software\Políticas\Microsoft\Power BI Desktop\</td>
</tr>
<tr>
<td>valueName</td>
<td>EnableArcGISMaps</td>
</tr>
</table>

O valor 1 (decimal) habilita o ArcGIS Maps para Power BI.

O valor 0 (decimal) desabilita o ArcGIS Maps para Power BI.

## <a name="considerations-and-limitations"></a>Considerações e limitações
Os Mapas do ArcGIS para o Power BI estão disponíveis nos seguintes serviços e aplicativos:

<table>
<tr><th>Serviço/Aplicativo</th><th>Disponibilidade</th></tr>
<tr>
<td>Power BI Desktop</td>
<td>Sim</td>
</tr>
<tr>
<td>Serviço do Power BI (PowerBI.com)</td>
<td>Sim</td>
</tr>
<tr>
<td>Aplicativos móveis do Power BI</td>
<td>Sim</td>
</tr>
<tr>
<td>Publicar na Web do Power BI</td>
<td>Não</td>
</tr>
<tr>
<td>Power BI Embedded</td>
<td>Não</td>
</tr>
<tr>
<td>Incorporação do serviço do Power BI (PowerBI.com)</td>
<td>Não</td>
</tr>
</table>

Em serviços ou aplicativos em que os Mapas do ArcGIS para o Power BI não estiverem disponíveis, a visualização será mostrada como um visual vazio com o logotipo do Power BI.

Ao codificar endereços geograficamente, somente os primeiros 1500 endereços serão codificados. Codificações geográficas de nomes de locais ou países não estarão sujeitas ao limite de 1500 endereços.

<br/>

**Como os ArcGIS Maps for Power BI funcionam juntos?**
O ArcGIS Maps for Power BI é fornecido pela Esri (www.esri.com). O uso do ArcGIS Maps for Power BI está sujeito aos [termos](https://go.microsoft.com/fwlink/?LinkID=8263222) e à [política de privacidade](https://go.microsoft.com/fwlink/?LinkID=826323) da Esri. Os usuários do Power BI que queiram usar os visuais do ArcGIS Maps for Power BI precisam aceitar a caixa de diálogo de consentimento (consulte Consentimento do usuário para obter detalhes).  Usar o ArcGIS Maps for Power BI da Esri está sujeito aos Termos e à Política de Privacidade da Esri que também estão vinculados à caixa de diálogo de consentimento. Cada usuário deve consentir antes de usar o ArcGIS Maps for Power BI pela primeira vez. Depois que o usuário aceitar o consentimento, os dados vinculados ao visual são enviados aos serviços da Esri pelo menos para geocodificação, que significa transformar informações de localização em informações de latitude e longitude que podem ser representadas em um mapa. Você deve considerar que os dados associados à visualização de dados podem ser enviados aos serviços da Esri. A Esri fornece serviços como mapas de base, análise espacial, geocodificação, etc. O visual do ArcGIS Maps for Power BI interage com esses serviços usando uma conexão SSL protegida por um certificado fornecido e mantido pela Esri. Informações adicionais sobre o ArcGIS Maps for Power BI podem ser obtidas da [página do produto ArcGIS Maps for Power BI](https://www.esri.com/powerbi).

Quando um usuário se inscreve para uma assinatura Plus oferecida pela Esfri por meio do ArcGIS Maps for Power BI, ele está entrando em uma relação direta com a Esri. O Power BI não envia informações pessoais sobre o usuário à Esri. O usuário entra e confia em um aplicativo AAD fornecido pela Esri usando sua própria identidade do AAD. Ao fazer isso, o usuário compartilhará suas informações pessoais diretamente com a Esri. Depois que o usuário adicionar o conteúdo Plus a um visual do ArcGIS Maps for Power BI, outros usuários do Power BI também precisarão de uma assinatura Plus da Esri para exibir ou editar esse conteúdo. 

Para obter perguntas técnicas detalhadas sobre como o ArcGIS Maps for Power BI da Esri funciona, contate a Esri por meio do site de suporte.


**O uso do ArcGIS Maps para Power BI é cobrado?**

O Mapa do ArcGIS para o Power BI está disponível para todos os usuários do Power BI sem custo adicional. Ele é um componente fornecido pela **Esri** e seu uso está sujeito aos termos e à política de privacidade fornecidos pela **Esri**, conforme mencionado anteriormente neste artigo.

**Estou recebendo uma mensagem de erro no Power BI Desktop informando que meu cache está cheio**

Esse é um bug que está sendo resolvido.  Enquanto isso, para limpar o cache, tente excluir os arquivos neste local: C:\Users\\AppData\Local\Microsoft\Power BI Desktop\CEF e, depois, reinicie o Power BI.

**O ArcGIS Maps para Power BI dá suporte aos shapefiles da Esri?**

O ArcGIS Maps para Power BI detecta automaticamente os limites padrão como países/regiões, estados/províncias e CEP. Se você precisar fornecer suas próprias formas, faça isso usando o [Shape Maps para Power BI Desktop (Preview)](desktop-shape-map.md).

**Posso exibir meus mapas do ArcGIS offline?**

Não, o Power BI precisa de conectividade de rede para exibir os mapas.

**Posso me conectar à minha conta do ArcGIS Online pelo Power BI?**

Ainda não. [Vote para essa ideia](https://ideas.powerbi.com/forums/265200-power-bi-ideas/suggestions/9154765-arcgis-geodatabases) e nós lhe enviaremos um email quando iniciar o trabalho com esse recurso.  

## <a name="next-steps"></a>Próximas etapas
[Interagindo com um mapa do ArcGIS que foi compartilhado com você](power-bi-visualizations-arcgis.md)

[Postagem do blog anunciando a disponibilidade do ArcGIS Maps para o Power BI](https://powerbi.microsoft.com/blog/announcing-arcgis-maps-for-power-bi-by-esri-preview/)

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](http://community.powerbi.com/)

