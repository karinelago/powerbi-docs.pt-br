---
title: Alterar o tamanho de uma página de relatório
description: Alterar as configurações de exibição de uma página em um relatório do Power BI
services: powerbi
documentationcenter: ''
author: mihart
manager: kfile
backup: ''
editor: ''
tags: ''
qualityfocus: modifying
qualitydate: ''
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 01/24/2018
ms.author: mihart
LocalizationGroup: Reports
ms.openlocfilehash: 8381f3100676b6e20f7fb748045c4852b30c45b9
ms.sourcegitcommit: 493f160d04ed411ff4741c599adc63ba1f65230f
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/07/2018
---
# <a name="change-the-size-of-a-report-page"></a>Alterar o tamanho de uma página de relatório
No [artigo e vídeo anterior](power-bi-report-display-settings.md), você aprendeu duas maneiras diferentes de controlar a exibição de página nos relatórios do Power BI: **Exibir** e **Tamanho da Página**. A exibição de Página e o Tamanho da Página estão disponíveis no serviço do Power BI e no Power BI Desktop e têm aparência e funcionamento quase idênticos, mas para este tutorial, estamos usando o serviço do Power BI.

### <a name="prerequisites"></a>Pré-requisitos
- Serviço do Power BI   
- [Relatório de Exemplo de Análise de Varejo](sample-retail-analysis.md)

## <a name="first-lets-change-the-page-view-setting"></a>Primeiro, vamos alterar a configuração do modo de exibição de página

1. Abra o relatório no modo de exibição de Leitura ou no modo de exibição de Edição e selecione a guia de relatório de **Novos Repositórios**. Por padrão, essa página de relatório é exibida usando a configuração **Ajustar à Página**.  Nesse caso, Ajustar à Página exibe a página de relatório sem barras de rolagem, mas alguns dos detalhes e títulos são pequenos demais para leitura.

   ![](media/power-bi-change-report-display-settings/pbi_fit_to_page.png)
2. Certifique-se de que nenhuma visualização seja selecionada na tela. Selecione **Exibição** e revise as opções de exibição.

    * No Modo de Exibição de Leitura, você verá isto.

     ![](media/power-bi-change-report-display-settings/power-bi-page-view-menu-new.png)
    * No Modo de Edição de Exibição, você verá isto.

    ![](media/power-bi-change-report-display-settings/power-bi-view-editing-view.png)

1. Vamos ver como a página aparece usando a configuração **Tamanho real**.

   ![](media/power-bi-change-report-display-settings/power-bi-actal-size2.png)

   Não é boa, pois o dashboard agora tem barras de rolagem duplas.
2. Alterne para **Ajustar à largura**.

   ![](media/power-bi-change-report-display-settings/pbi_fit_to_width.png)

   Ficou melhor. Agora temos barras de rolagem, mas fica mais fácil de ler os detalhes.

## <a name="change-the-default-view-for-a-report-page"></a>Alterar a exibição padrão para uma página de relatório
Se você for um *criador* de relatório, você poderá alterar a exibição padrão das páginas do relatório. Quando você compartilha seu relatório com outras pessoas, as páginas do relatório serão abertas usando o modo de exibição que você definiu. Os *consumidores* do relatório poderão alterar o modo de exibição, mas não poderão salvar as alterações feitas por eles depois de saírem do relatório.

1. Na página **Novos armazenamentos** do relatório, retorne para a exibição **Tamanho real**.

   ![](media/power-bi-change-report-display-settings/power-bi-actual-size.png)

2. Na página de relatório **Vendas Mensais do Distrito**, defina o modo de exibição como **Ajustar à largura**.

3. Na página do relatório **visão geral**, mantenha a configuração de exibição padrão.

4. Agora, salve o relatório selecionando **Arquivo > Salvar**. Na próxima vez que você abrir esse relatório, as páginas serão exibidas usando as novas configurações de exibição. Vamos ver.

   ![](media/power-bi-change-report-display-settings/power-bi-save.png)
3. Selecione o nome do espaço de trabalho atual na barra de navegação superior para retornar a esse espaço de trabalho.  

   ![](media/power-bi-change-report-display-settings/power-bi-my-workspace.png)
4. Selecione a guia **Relatórios** e escolha o mesmo relatório (Exemplo de Análise de Varejo).

    ![](media/power-bi-change-report-display-settings/power-bi-new-report2.png)
5. Abra cada página do relatório para ver as novas configurações.

   ![](media/power-bi-change-report-display-settings/power-bi-page-view.gif)

## <a name="now-lets-explore-the-page-size-setting"></a>Agora, vamos explorar a configuração do modo do *tamanho da página*
As configurações de tamanho de página só estão disponíveis no [modo de exibição de Edição](service-interact-with-a-report-in-editing-view.md), portanto, você deve ter permissões de edição (*criador*) para o relatório para que possa alterar as configurações de tamanho da página. Se você tiver se conectado a qualquer um dos nossos [exemplos](sample-datasets.md), você terá permissões de *criador* para esses relatórios.

1. Abra a página de "Vendas mensais por distrito" do [Exemplo de Análise de Varejo](sample-retail-analysis.md) no Modo de Exibição de Edição.
2. Certifique-se de que nenhuma visualização seja selecionada na tela.  No painel **Visualizações**, selecione o ícone de rolo de pintura ![](media/power-bi-change-report-display-settings/power-bi-paintroller.png).
3. Selecione **Tamanho da Página** &gt; **Tipo** para exibir as opções de tamanho da página.

   ![](media/power-bi-change-report-display-settings/power-bi-page-size-menu-new.png)
4. Selecione **Letra**.  Na tela, somente o conteúdo que se encaixa em 816 x 1056 pixels (tamanho de Carta) permanecerá na posição branca da tela.

   ![](media/power-bi-change-report-display-settings/power-bi-letter-new.png)
5. Selecione a proporção do **Tamanho da Página** **16:9**.

   ![](media/power-bi-change-report-display-settings/power-bi-16-to-9-new.png)

   A página de relatório é exibida com uma razão de 16 de largura por 9 de altura. Para ver o tamanho de pixel real que está sendo usado, dê uma olha nos campos de largura e altura acinzentados (1280x720). Há muito espaço vazio ao redor da tela de relatório. Isso ocorre porque definimos anteriormente **Exibição** como "Ajustar à largura".
7. Continue explorando as opções de **Tamanho da Página**

## <a name="use-page-view-and-page-size-together"></a>Usar o modo de Exibição de página e Tamanho de Página juntos
Use o modo de Exibição de página e Tamanho de Página juntos para criar um relatório que tenha a melhor aparência quando compartilhado com colegas ou inserido em outro aplicativo.

Neste exercício, você criará uma página de relatório que será exibido em um aplicativo com espaço para 500 pixels de largura por 750 pixels de altura.

Lembre-se que, na etapa anterior, vimos que nossa página de relatório é exibida atualmente com 1280 de largura por 720 de altura. Então, sabemos que precisaremos redimensionar e reorganizar muitos itens se quisermos que todos os elementos visuais se ajustem à página.

1. Redimensione e mova os elementos visuais para que caibam em menos da metade da área da tela atual.

    ![](media/power-bi-change-report-display-settings/power-bi-custom-view.gif)
2. Selecione **Tamanho da Página**  &gt;**Personalizado**.
3. Defina a largura para 500 e a altura para 750.

    ![](media/power-bi-change-report-display-settings/power-bi-custom-new.png)
4. Ajuste a página de relatório de modo que ela tenha a melhor aparência. Alterne entre **Exibir > Tamanho real** e **Exibir > Ajustar à página** para fazer ajustes.

    ![](media/power-bi-change-report-display-settings/power-bi-final-new.png)

## <a name="next-steps"></a>Próximas etapas
[Criar relatórios para Cortana](service-cortana-answer-cards.md)

Voltar a [Configurações de exibição de página em um relatório do Power BI](power-bi-report-display-settings.md)

Mais perguntas? [Experimente a Comunidade do Power BI](http://community.powerbi.com/)
