---
title: Usar um IDE R externo com o Power BI
description: Você pode iniciar e usar um IDE externo com o Power BI
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 05/02/2018
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: c51d89979ccf6791e69a7cdd457004b065b9d537
ms.sourcegitcommit: 80d6b45eb84243e801b60b9038b9bff77c30d5c8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34288856"
---
# <a name="use-an-external-r-ide-with-power-bi"></a>Usar um IDE R externo com o Power BI
Com o **Power BI Desktop**, você pode usar um IDE R externo (ambiente de desenvolvimento integrado) para criar e refinar scripts R e então usar esses scripts no Power BI.

![](media/desktop-r-ide/r-ide_1a.png)

## <a name="enable-an-external-r-ide"></a>Habilitando um IDE R externo
Antes, você precisava usar o editor de scripts R no **Power BI Desktop** para criar e executar scripts R. Com esta versão, você pode iniciar o seu IDE R externo do **Power BI Desktop** e fazer com que seus dados sejam automaticamente importados e exibidos no IDE R. Ali, você pode modificar o script nesse IDE R externo e então colá-lo novamente no **Power BI Desktop** para criar elementos visuais do Power BI e relatórios.

A partir da versão de setembro de 2016 do **Power BI Desktop** (versão 2.39.4526.362), você poderá especificar quais IDE R gostaria de usar e iniciá-los automaticamente no **Power BI Desktop**.

### <a name="requirements"></a>Requisitos
Para usar esse recurso, você precisa instalar um **R IDE** no computador local. O **Power BI Desktop** não inclui, não implanta nem instala o mecanismo do R, portanto, você deve instalar o **R** separadamente no computador local. Você pode escolher quais IDE R para usar, com as seguintes opções:

* Você pode instalar R IDE favorito, muitos dos quais estão disponíveis gratuitamente, como a [página de download Revolution Open](https://mran.revolutionanalytics.com/download/) e o [CRAN Repository](https://cran.r-project.org/bin/windows/base/).
* O **Power BI Desktop** também dá suporte a [Studio R](https://www.rstudio.com/) e **Visual Studio 2015** com [*R Tools para editores do Visual Studio*](https://beta.visualstudio.com/vs/rtvs/).
* Você também pode instalar um IDE R diferente e fazer com que o **Power BI Desktop** inicie o **R IDE** seguindo um destes procedimentos:
  
  * Você pode associar arquivos **.R** com o IDE externo que você deseja que o **Power BI Desktop** inicie.
  * Você pode especificar o .exe que **Power BI Desktop** deve iniciar selecionando *Outros* na seção **Opções de Script R** do diálogo **Opções**. Você pode o diálogo **Opções** ao acessar **Arquivo > Opções e configurações > Opções**.
    
    ![](media/desktop-r-ide/r-ide_1b.png)

Se você tiver vários IDEs R instalados, você poderá especificar qual será iniciado ao selecioná-lo no menu suspenso *IDEs R Detectados* no diálogo **Opções**.

Por padrão, o **Power BI Desktop** iniciará o **Studio R** como o IDE R externo se ele estiver instalado no computador local; se o **Studio R** não estiver instalado e você tiver o **Visual Studio 2015** com **R Tools para Visual Studio**, ele será iniciado. Se nenhuma dessas IDEs R estiver instalada, o aplicativo associado a arquivos **.R** será iniciado.

E se nenhuma associação de arquivo **.R** existir, será possível especificar um caminho para um IDE personalizado na seção *Navegar até seu IDE R preferido* do diálogo **Opções**. Você também pode iniciar um IDE R diferente selecionando o ícone de engrenagem **Configurações** ao lado do ícone de seta **Iniciar IDE R** no **Power BI Desktop**.

## <a name="launch-an-r-ide-from-power-bi-desktop"></a>Iniciando um IDE R do Power BI Desktop
Para iniciar um IDE do R no **Power BI Desktop**, execute as etapas a seguir:

1. Carregue os dados no **Power BI Desktop**.
2. Selecione alguns campos do painel **Campos** com o qual você deseja trabalhar. Se você ainda não tiver habilitado elementos visuais de script, será solicitado a fazê-lo.
   
   ![](media/desktop-r-ide/r-ide_3.png)
3. Quando os elementos visuais de script estão habilitados, você pode selecionar um elemento visual de R do painel **Visualizações**, que cria um visual de R em branco que está pronto para exibir os resultados do script. O painel **Editor de script R** também aparece.
   
   ![](media/desktop-r-ide/r-ide_4.png)
4. Agora você pode selecionar os campos que você deseja usar em seu script R. Quando você seleciona um campo, o campo **Editor de script R** cria automaticamente um código de script com base no campo ou campos selecionados por você. Você pode criar (ou colar) o script R diretamente no painel **Editor de script R**, ou pode deixá-lo vazio.
   
   ![](media/desktop-r-ide/r-ide_5.png)
   
   > [!NOTE]
   > O tipo de agregação padrão para visuais R é *não resumir*.
   > 
   > 
5. Agora você pode iniciar o IDE R diretamente do **Power BI Desktop**. Selecione o botão **Iniciar IDE R**, localizado no lado direito da barra de título do **Editor de script R**, conforme mostrado abaixo.
   
   ![](media/desktop-r-ide/r-ide_6.png)
6. O IDE R especificado é iniciado pelo Power BI Desktop, conforme mostrado na imagem a seguir (nesta imagem, **RStudio** é o IDE R padrão).
   
   ![](media/desktop-r-ide/r-ide_7.png)
   
   > [!NOTE]
   > O **Power BI Desktop** adiciona as primeiras três linhas do script para que os dados possam ser importados do **Power BI Desktop** quando você executar o script.
   > 
   > 
7. Os scripts que você criou no **painel Editor de script R** do **Power BI Desktop** aparece começando na linha 4 no seu IDE R. Agora você pode criar seu script R no IDE do R. Uma vez que o script R esteja concluído no seu IDE R, você precisará copiá-lo e colá-lo de volta no painel **Editor de script R** no **Power BI Desktop**, *excluindo* as três primeiras linhas do script que o **Power BI Desktop** tiver gerado automaticamente. Não copie as três primeiras linhas do script de volta no **Power BI Desktop**, essas linhas foram usadas apenas para importar os dados do **Power BI Desktop** para o IDE R.

### <a name="known-limitations"></a>Limitações conhecidas
Iniciar um IDE R diretamente do Power BI Desktop tem algumas limitações:

* Não há suporte para exportar automaticamente o script do IDE R para o **Power BI Desktop**.
* Não há suporte para o editor **Cliente R** (RGui.exe), porque esse editor não oferece suporte à abertura de arquivos.

## <a name="next-steps"></a>Próximas etapas
Analise as informações adicionais a seguir sobre o R no Power BI.

* [Executando scripts do R no Power BI Desktop](desktop-r-scripts.md)
* [Criar elementos visuais do Power BI usando o R](desktop-r-visuals.md)

