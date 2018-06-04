---
title: Inserir um relatório usando um iFrame
description: Inserindo um relatório do Servidor de Relatórios do Power BI em um iFrame no SharePoint Server
author: markingmyname
ms.author: maghan
ms.date: 05/04/2018
ms.topic: quickstart
ms.service: powerbi
ms.component: powerbi-report-server
ms.custom: mvc
manager: kfile
ms.openlocfilehash: 8d7653e6f390959df745fa2b19076ee89b26b1bc
ms.sourcegitcommit: 80d6b45eb84243e801b60b9038b9bff77c30d5c8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34293687"
---
# <a name="quickstart-embed-a-power-bi-report-server-report-using-an-iframe-in-sharepoint-server"></a>Início Rápido: Inserir um relatório do Servidor de Relatórios do Power BI usando um iFrame no SharePoint Server

Neste início rápido, você aprenderá a inserir um relatório do Servidor de Relatórios do Power BI usando um iFrame em uma página do SharePoint. Se você estiver trabalhando com o SharePoint Online, o Servidor de Relatórios do Power BI precisará estar acessível publicamente. No SharePoint Online, o Web Part do Power BI que funciona com o serviço do Power BI não funciona com o Servidor de Relatórios do Power BI. 

![Exemplo do iFrame](media/quickstart-embed/quickstart_embed_01.png)
## <a name="prerequisites"></a>Pré-requisitos
* Você precisará ter o [Servidor de Relatórios do Power BI](https://powerbi.microsoft.com/en-us/report-server/) instalado e configurado.
* Você precisará ter o [Power BI Desktop otimizado para o Servidor de Relatórios do Power BI](install-powerbi-desktop.md) instalado.
* Você precisará ter um ambiente do [SharePoint](https://docs.microsoft.com/en-us/sharepoint/install/install) instalado e configurado.

## <a name="creating-the-power-bi-report-server-report-url"></a>Criando a URL de relatório do Servidor de Relatórios do Power BI

1. Baixe o exemplo do GitHub – [Blog Demo](https://github.com/Microsoft/powerbi-desktop-samples).

    ![Baixar arquivo PBIX de exemplo](media/quickstart-embed/quickstart_embed_14.png)

2. Abra o arquivo PBIX de exemplo do GitHub no **Power BI Desktop otimizado para o Servidor de Relatórios do Power BI**.

    ![Ferramenta do PBI RS Desktop](media/quickstart-embed/quickstart_embed_02.png)

3. Salve o relatório no **Servidor de Relatórios do Power BI**. 

    ![Salvar no PBI RS](media/quickstart-embed/quickstart_embed_03.png)

4. Exiba o relatório no **Portal da Web**.

    ![Portal da Web](media/quickstart-embed/quickstart_embed_04.png)

### <a name="capturing-the-url-parameter"></a>Capturando o parâmetro de URL

Quando tiver sua URL, você poderá criar um iFrame em uma página do SharePoint para hospedar o relatório. Para qualquer URL de relatório do Servidor de Relatórios do Power BI, você pode adicionar um parâmetro querystring de `?rs:embed=true` para inserir o relatório em um iFrame. 

   Por exemplo:
    ``` 
    http://myserver/reports/powerbi/Sales?rs:embed=true
    ```
## <a name="embedding-a-power-bi-report-server-report-in-a-sharepoint-iframe"></a>Inserindo um relatório do Servidor de Relatórios do Power BI em um iFrame no SharePoint

1. Navegue até a página **Conteúdo do Site** no SharePoint.

    ![Página Conteúdo do Site](media/quickstart-embed/quickstart_embed_05.png)

2. Escolha a página em que deseja adicionar seu relatório.

    ![Aplicativo da Página Conteúdo do Site](media/quickstart-embed/quickstart_embed_06.png)

3. Selecione a engrenagem no canto superior direito e selecione **Editar Página**.

    ![Opção Editar Página](media/quickstart-embed/quickstart_embed_07.png)

4. Selecione **Adicionar Web Part**.

    ![Adicionar Web Part](media/quickstart-embed/quickstart_embed_08.png)

5. Em **Categorias**, selecione **Mídia e Conteúdo**, em **Partes**, selecione **Editor de Conteúdo** e, em seguida, selecione **Adicionar**.

    ![Selecionar Web Part do Editor de Conteúdo](media/quickstart-embed/quickstart_embed_09.png) ![Selecione Adicionar](media/quickstart-embed/quickstart_embed_091.png)

6. Selecione **Clique aqui para adicionar novo conteúdo**.

    ![Adicionar novo conteúdo](media/quickstart-embed/quickstart_embed_10.png)

7. Na faixa de opções, selecione a guia **Formatar Texto** e selecione **Editar Fonte**.

     ![Editar Fonte](media/quickstart-embed/quickstart_embed_11.png)

8. Na janela Editar Fonte, cole o código do iFrame e selecione OK.

    ![Código do iFrame](media/quickstart-embed/quickstart_embed_12.png)

     Por exemplo:
     ```
     <iframe width="800" height="600" src="http://myserver/reports/powerbi/Sales?rs:embed=true" frameborder="0" allowFullScreen="true"></iframe>
     ```

9. Na faixa de opções, selecione a guia **Página** e selecione **Parar a Edição**.

    ![Parar a Edição](media/quickstart-embed/quickstart_embed_13.png)

10. Agora, você deve ver o relatório na página.

    ![Exemplo do iFrame](media/quickstart-embed/quickstart_embed_01.png)

## <a name="next-steps"></a>Próximas etapas

[Início rápido: criar um relatório do Power BI para o Servidor de Relatório do Power BI](quickstart-create-powerbi-report.md)  
[Início rápido: criar um relatório paginado para o Servidor de Relatório do Power BI](quickstart-create-paginated-report.md)  

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/) 