---
title: "Inserir com Web Part de Relatório no SharePoint Online"
description: "Com a nova Web Part de Relatório do Power BI para o SharePoint Online, você pode facilmente inserir relatórios interativos do Power BI às páginas do SharePoint Online."
services: powerbi
documentationcenter: 
author: guyinacube
manager: kfile
backup: 
editor: 
tags: 
featuredvideoid: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 11/19/2017
ms.author: asaxton
ms.openlocfilehash: a60682f9da2befe5f87b11749c089f72949a8f6f
ms.sourcegitcommit: 6e8fbbbcbe3e1a38207b29a9ca66ea94fb2a51fb
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/19/2017
---
# <a name="embed-with-report-web-part-in-sharepoint-online"></a>Inserir com Web Part de Relatório no SharePoint Online

Com a nova Web Part de Relatório do Power BI para o SharePoint Online, você pode facilmente inserir relatórios interativos do Power BI às páginas do SharePoint Online.

Ao usar a nova opção **Inserir ao SharePoint Online**, os relatórios incorporados são totalmente protegidos para que você possa facilmente criar portais internos seguros.

## <a name="requirements"></a>Requisitos

Há alguns requisitos para que os relatórios da opção **Inserir ao SharePoint Online** funcionem.

* A web part do Power BI para o SharePoint Online requer [Páginas Modernas](https://support.office.com/article/Allow-or-prevent-creation-of-modern-site-pages-by-end-users-c41d9cc8-c5c0-46b4-8b87-ea66abc6e63b).

## <a name="embed-your-report"></a>Insira seu relatório

Para inserir o seu relatório ao SharePoint Online, primeiro você precisa obter a URL do relatório e, em seguida, usar essa URL com a nova web part do Power BI no SharePoint Online.

### <a name="get-a-url-to-your-report"></a>Obter a URL do relatório

1. Exibir o relatório no serviço do Power BI.

2. Selecionar o item de menu **Arquivo**.

3. Selecione **Inserir no SharePoint Online**.
   
    ![](media/service-embed-report-spo/powerbi-file-menu.png)

4. Copiar a URL da caixa de diálogo.

    ![](media/service-embed-report-spo/powerbi-embed-link-sharepoint.png)

   > [!NOTE]
   > Você também pode usar a URL que é exibida na barra de endereços do navegador da Web ao visualizar um relatório. Essa URL conterá a página do relatório que está sendo exibido. Você precisará remover a seção de relatório da URL se quiser usar uma página diferente.

### <a name="add-the-power-bi-report-to-a-sharepoint-online-page"></a>Adicionar o relatório do Power BI a uma página do SharePoint Online

1. Abra a página desejada no SharePoint Online e selecione **Editar**.

    ![](media/service-embed-report-spo/powerbi-sharepoint-edit-page.png)

    Ou crie uma nova página de site selecionando **+ novo** dentro do SharePoint Online.

    ![](media/service-embed-report-spo/powerbi-sharepoint-new-page.png)

2. Selecione **+** e selecione a web part do **Power BI**.

    ![](media/service-embed-report-spo/powerbi-sharepoint-new-web-part.png)

3. Selecione **Adicionar relatório**.

    ![](media/service-embed-report-spo/powerbi-sharepoint-new-report.png)

4. Cole a URL do relatório no painel de propriedade. Esta é a URL que você copiou nas etapas acima. O relatório será carregado automaticamente.

    ![](media/service-embed-report-spo/powerbi-sharepoint-new-web-part-properties.png)

5. Selecione **Publicar** para tornar a alteração visível para os usuários do SharePoint Online.

    ![](media/service-embed-report-spo/powerbi-sharepoint-report-loaded.png)

## <a name="granting-access-to-reports"></a>Conceder acesso aos relatórios

Incorporar um relatório ao SharePoint Online automaticamente não dá aos usuários permissão para exibir o relatório. As permissões para exibir o relatório são definidas dentro do serviço do Power BI.

> [!IMPORTANT]
> Certifique-se de examinar quem pode ver o relatório dentro do serviço do Power BI e de conceder acesso aos que não aparecem na lista.

Há duas maneiras de conceder acesso ao relatório dentro do serviço do Power BI. Se você estiver usando um grupo do Office 365 para criar seu site de equipe do SharePoint Online, liste o usuário como um membro do espaço de trabalho de aplicativo no serviço do Power BI. Isso assegurará que os usuários podem exibir o conteúdo desse grupo. Para obter mais informações, consulte [Criar e distribuir um aplicativo no Power BI](service-create-distribute-apps.md).

Como alternativa, você pode conceder acesso ao seu relatório aos usuários fazendo o seguinte.

1. Adicione um bloco de seu relatório a um painel.

2. Compartilhe o painel com os usuários que precisam acessar o relatório. Para obter mais informações, consulte [Compartilhar um painel com seus colegas e com outras pessoas](service-share-dashboards.md).

## <a name="allowing-free-users-access-to-reports"></a>Permitir que os usuários gratuitos acessem os relatórios

Os usuários gratuitos podem exibir relatórios que são inseridos com a web part do Power BI para o SharePoint Online. Você fornece acesso para os usuários gratuitos da mesma maneira que faria com usuários Pro, conforme descrito em [Conceder acesso a relatórios](#granting-access-to-reports) acima. O espaço de trabalho, no qual o relatório está localizado, também deve ser auxiliado pela capacidade do Power BI Premium. 

Por exemplo, se você tiver um relatório em um espaço de trabalho do aplicativo, você precisará atribuir o espaço de trabalho do aplicativo para uma capacidade do Power BI Premium. Você também precisa adicionar o usuário gratuito à lista de membros desse espaço de trabalho do aplicativo.

## <a name="web-part-settings"></a>Configurações de Web Part

Abaixo, temos uma descrição das configurações que podem ser ajustadas para a web part do Power BI para o SharePoint Online.

![](media/service-embed-report-spo/powerbi-sharepoint-web-part-properties.png)

| Propriedade | Descrição |
| --- | --- |
| Nome da página |Define a página padrão que é exibida pela web part. Selecionar um valor na lista suspensa. Se nenhuma página for exibida, o relatório terá uma página ou a URL que você colou conterá um nome de página. Remover a seção de relatório da URL para selecionar uma página específica. |
| Exibição |Opção para ajustar como o relatório é ajustado dentro da página do SharePoint Online. |
| Exibir o Painel de Navegação |Exibe ou oculta o painel de navegação da página. |
| Exibir Painel de Filtro |Exibe ou oculta o painel de filtro. |

## <a name="multi-factor-authentication"></a>Autenticação multifator

Se seu ambiente do Power BI requer que a sessão seja iniciada usando a autenticação multifator, pode ser que você precise entrar com um dispositivo de segurança para verificar sua identidade. Isso ocorrerá se você não entrou no SharePoint Online usando a autenticação multifator, mas seu ambiente Power BI requer uma conta validada por um dispositivo de segurança.

> [!NOTE]
> O Azure Active Directory 2.0 ainda não dá suporte para autenticação multifator. Os usuários receberão uma mensagem indicando *erro*. Se o usuário entrar novamente no SharePoint Online usando seu dispositivo de segurança, o relatório poderá ser exibido.

## <a name="reports-that-do-not-load"></a>Relatórios que não são carregados

O relatório pode não ser carregado dentro da web part do Power BI e a seguinte mensagem pode ser exibida.

*Este conteúdo não está disponível.*

![](media/service-embed-report-spo/powerbi-sharepoint-report-not-found.png)

Há duas razões comuns para essa mensagem.

1. Você não tem acesso a este relatório.
2. O relatório foi excluído.

Entre em contato com o proprietário da página do SharePoint Online para ajudá-lo a resolver o problema.

## <a name="known-issues-and-limitations"></a>Limitações e problemas conhecidos

* **Erro: "Ocorreu um erro, tente sair, entrar outra vez e visitar esta página novamente. ID de correlação: indefinida, status de resposta http: 400, código de erro do servidor 10001, mensagem: token de atualização inexistente"**
  
  Se você receber esse erro, tente um destes procedimentos.
  
  1. Saia do SharePoint e entre novamente. Certifique-se de fechar todas as janelas do navegador antes de entrar novamente.

  2. Se sua conta de usuário exigir a Autenticação Multifator (MFA), entre no SharePoint usando o dispositivo de Autenticação Multifator (aplicativo de telefone, cartão inteligente, etc.)

* O Power BI não dá suporte aos mesmos idiomas localizados que o SharePoint Online. Como resultado, você não verá a localização correta no relatório inserido.

* Você pode encontrar problemas se usar o Internet Explorer 10. Você pode examinar o [suporte dos navegadores para o Power BI](service-browser-support.md) e para o [Office 365](https://products.office.com/office-system-requirements#Browsers-section).

## <a name="next-steps"></a>Próximas etapas

[Permitir ou impedir a criação de páginas de sites modernas pelos usuários finais](https://support.office.com/article/Allow-or-prevent-creation-of-modern-site-pages-by-end-users-c41d9cc8-c5c0-46b4-8b87-ea66abc6e63b)  
[Criar e distribuir um aplicativo no Power BI](service-create-distribute-apps.md)  
[Compartilhar um painel com seus colegas e com outras pessoas](service-share-dashboards.md)  
[Power BI Premium – o que é?](service-premium.md)  

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](http://community.powerbi.com/)

