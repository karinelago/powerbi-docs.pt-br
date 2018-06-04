---
title: Visualizações personalizadas no Power BI
description: Visualizações personalizadas no Power BI
author: markingmyname
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 02/06/2018
ms.author: maghan
LocalizationGroup: Visualizations
ms.openlocfilehash: d8c3a33a3ae6166d33ea7a613917616613b84696
ms.sourcegitcommit: 80d6b45eb84243e801b60b9038b9bff77c30d5c8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34721445"
---
# <a name="custom-visuals-in-power-bi"></a>Visuais personalizados no Power BI
Ao criar ou editar um relatório do Power BI, há muitos tipos diferentes de visuais disponíveis para uso. Esses visuais são exibidos no painel **Visualizações**. Quando você baixar o Power BI Desktop ou abrir o serviço do Power BI (app.powerbi.com), esse conjunto de visuais é "predefinido".

![](media/power-bi-custom-visuals/power-bi-visualizations.png)

Mas você não está limitado a esse conjunto de visuais, selecionar reticências abre outra origem de visuais do relatório: *visuais personalizados*.

Os elementos visuais personalizados são criados por desenvolvedores usando os SDK personalizados a fim de permitir que os usuários vejam os dados de maneira que melhor se adapte ao seu negócio. Os autores do relatório podem, em seguida, importar os arquivos visuais personalizados para seus relatórios e usá-los como quaisquer outros elementos visuais do Power BI. Os elementos visuais personalizados são cidadãos de 1º de classe no Power BI e podem ser filtrados, realçados, editados, compartilhados etc.

Os elementos visuais personalizados podem estar na forma de 3 canais de implantação:
* Arquivos de elementos visuais personalizados
* Elementos visuais da organização
* Elementos visuais do Marketplace

## <a name="custom-visual-files"></a>Arquivos de elementos visuais personalizados

Os elementos visuais personalizados são pacotes que incluem o código para renderizar os dados que são fornecidos a eles. Qualquer pessoa pode criar um visual personalizado e empacotá-lo como um arquivo .pbiviz único, que pode ser importado em um relatório do Power BI.

> [!WARNING]
> Um visual personalizado pode conter código com riscos de segurança ou privacidade; verifique se você confia no autor e a fonte do visual personalizado antes de importá-lo em seu relatório.
> 
> 

## <a name="organization-visuals"></a>Elementos visuais da organização

Os administradores do Power BI podem implantar visuais personalizados em sua organização, para que os autores do relatório possam descobrir e usar com facilidade os elementos visuais personalizados que o administrador aprovou para usar dentro da organização. Isso dá ao administrador o controle para escolher os elementos visuais personalizados específicos para implantar na organização, bem como uma maneira fácil de gerenciar (ou seja, atualizar versão, ativar/desativar) os elementos visuais. Para o autor do relatório, é uma maneira fácil de descobrir elementos visuais que são exclusivos para a organização, bem como um suporte contínuo para atualizar esses elementos.

Para obter mais informações sobre os elementos visuais personalizados da organização, [Leia mais sobre os elementos visuais organizacionais](power-bi-custom-visuals-organization.md).

## <a name="marketplace-visuals"></a>Elementos visuais do Marketplace

Os membros da comunidade, bem como a Microsoft, contribuíram com seus elementos visuais personalizados para o benefício do público e os publicaram no marketplace [AppSource](https://appsource.microsoft.com/en-us/marketplace/apps?product=power-bi-visuals). Esses visuais podem ser baixados e adicionados aos relatórios do Power BI. Todos esses elementos visuais personalizados foram testados e aprovados pela Microsoft em relação à funcionalidade e à qualidade.

O que é o AppSource? De forma simples, é o lugar para encontrar aplicativos, suplementos e extensões para o seu software da Microsoft. A [AppSource](https://appsource.microsoft.com/en-us/) conecta milhões de usuários de produtos como o Office 365, Azure, Dynamics 365, Cortana e Power BI com soluções que os ajudam a realizar seu trabalho com mais eficiência, perspicácia ou harmonia do que antes.

### <a name="certified-visuals"></a>Elementos visuais certificados

Os visuais certificados para o Power BI são elementos visuais que passaram por rigorosos testes de qualidade adicionais e têm suporte em cenários adicionais, como [assinaturas de email](https://docs.microsoft.com/power-bi/service-report-subscribe) e para serem [exportados para o PowerPoint](https://docs.microsoft.com/power-bi/service-publish-to-powerpoint).
Para ver a lista de visuais personalizados certificados ou para enviar seus próprios, consulte [Certified custom visuals (Visuais personalizados certificados)](https://docs.microsoft.com/power-bi/power-bi-custom-visuals-certified).

Você é um desenvolvedor da Web e está interessado em criar suas próprias visualizações e adicioná-las ao AppSource? Consulte [Introdução às Ferramentas para Desenvolvedores](https://docs.microsoft.com/power-bi/service-custom-visuals-getting-started-with-developer-tools) e saiba como [publicar visuais personalizados na AppSource](https://appsource.microsoft.com/en-us/marketplace/apps?product=power-bi-visuals).

### <a name="import-a-custom-visuals-from-a-file"></a>Importar um visual personalizado de um arquivo

1. Selecione as reticências na parte inferior do painel de Visualizações.

    ![](media/power-bi-custom-visuals/power-bi-visualizations2.png)

2. No menu suspenso, selecione **Importar do arquivo**.

    ![](media/power-bi-custom-visuals/power-bi-custom-visual-import-from-file.png)

3. No menu Abrir arquivo, selecione o arquivo .pbiviz que você deseja importar e, em seguida, selecione Abrir. O ícone do visual personalizado é adicionado à parte inferior do painel de Visualizações e agora está disponível para uso em seu relatório.

    ![](media/power-bi-custom-visuals/power-bi-custom-visual-imported.png)

### <a name="import-organization-visuals"></a>Importar elementos visuais da organização

1. Selecione as reticências na parte inferior do painel de Visualizações.

    ![](media/power-bi-custom-visuals/power-bi-visual-org-01.png)

2. No menu suspenso, selecione Importar do marketplace.

    ![](media/power-bi-custom-visuals/power-bi-visual-org-02.png)

3. Selecione **MINHA ORGANIZAÇÃO** no menu da guia superior.

    ![](media/power-bi-custom-visuals/power-bi-visual-org-03.png)

4. Role a lista para localizar o visual para importar.
    
    ![](media/power-bi-custom-visuals/power-bi-visual-org-04.png)

5. Importe o visual personalizado selecionando **Adicionar**. O ícone do visual personalizado é adicionado à parte inferior do painel de Visualizações e agora está disponível para uso em seu relatório.

    ![](media/power-bi-custom-visuals/power-bi-visual-org-05.png)
 
## <a name="download-or-import-custom-visuals-from-microsoft-appsource"></a>Baixar ou importar visuais personalizados do Microsoft AppSource
Você tem duas opções para baixar e importar os visuais personalizados; de dentro do Power BI e do site do AppSource.

### <a name="import-custom-visuals-from-within-power-bi"></a>Importar visuais personalizados do Power BI

1. Selecione as reticências na parte inferior do painel de Visualizações.

    ![](media/power-bi-custom-visuals/power-bi-visualizations2.png)

2. No menu suspenso, selecione **Importar do marketplace**.

    ![](media/power-bi-custom-visuals/power-bi-visual-org-02.png)

3. Role a lista para localizar o visual para importar.

    ![](media/power-bi-custom-visuals/power-bi-import-visual.png)

4. Para saber mais sobre um dos visuais, realce e selecione-o.

    ![](media/power-bi-custom-visuals/power-bi-select.png)

5. Na página de detalhes, você pode exibir capturas de tela, vídeos, descrições detalhadas e muito mais.

    ![](media/power-bi-custom-visuals/power-bi-synoptic.png)

6. Role para baixo para ver as análises.

    ![](media/power-bi-custom-visuals/power-bi-reviews.png)

7. Importe o visual personalizado selecionando Adicionar. O ícone do visual personalizado é adicionado à parte inferior do painel de Visualizações e agora está disponível para uso em seu relatório.

    ![](media/power-bi-custom-visuals/power-bi-custom-visual-imported.png)

### <a name="download-and-import-custom-visuals-from-microsoft-appsource"></a>Baixar e importar visuais personalizados do Microsoft AppSource

1. Inicie em [Microsoft AppSource](https://appsource.microsoft.com) e selecione a guia para **Aplicativos**. 

    ![](media/power-bi-custom-visuals/power-bi-appsource-apps.png)

2. Isso leva você para a [página de resultados de Aplicativos](https://appsource.microsoft.com/en-us/marketplace/apps) na qual você pode exibir os principais aplicativos em cada categoria, incluindo *Aplicativos do Power BI*. Mas estamos procurando visuais personalizados, portanto, vamos restringir os resultados selecionando **visuais do Power BI** na lista de navegação à esquerda.

    ![](media/power-bi-custom-visuals/power-bi-appsource-visuals.png)

3. O AppSource exibe um bloco para cada visual personalizado.  Cada bloco tem um instantâneo do visual personalizado e fornece uma breve descrição e um link de download. Para ver mais detalhes, selecione o bloco. 

    ![](media/power-bi-custom-visuals/powerbi-custom-select-visual.png)

4. Na página de detalhes, você pode exibir capturas de tela, vídeos, descrições detalhadas e muito mais. Baixe o visual personalizado selecionando **Obtê-lo agora** e, em seguida, concordando com os Termos de uso. 

    ![](media/power-bi-custom-visuals/power-bi-appsource-get.png)

5. Selecione o link para baixar o visual personalizado.

    ![](media/power-bi-custom-visuals/powerbi-custom-download.png)

    A página de download também inclui instruções sobre como importar o visual personalizado para o Power BI Desktop e para o serviço do Power BI.

    Você também pode baixar um relatório de exemplo que inclua o visual personalizado e apresente suas funcionalidades.

    ![](media/power-bi-custom-visuals/powerbi-custom-try-sample.png)

6. Salve o arquivo. pbiviz e, em seguida, abra o Power BI.

7. Importe o arquivo .pbiviz em seu relatório (confira a seção [Importar um visual personalizado de um arquivo](#import-a-custom-visuals-from-a-file) acima)

## <a name="considerations-and-troubleshooting"></a>Considerações e solução de problemas

- Um visual personalizado é adicionado a um relatório específico quando importado. Se você desejar usar o visual em outro relatório, você precisará importá-lo nesse relatório também. Quando um relatório com um visual personalizado é salvo com a opção **Salvar como** , uma cópia do visual personalizado será salva com o novo relatório.

- Se você não ver um painel **Visualizações**, isso significará que não é necessário editar permissões para o relatório.  Você só pode adicionar visuais personalizados para relatórios que você pode editar, não para relatórios que foram compartilhados com você.

Mais perguntas? [Experimente a Comunidade do Power BI](http://community.powerbi.com/)
