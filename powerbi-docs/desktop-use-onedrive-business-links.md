---
title: Usar os links do OneDrive for Business no Power BI Desktop
description: Usar os links do OneDrive for Business no Power BI Desktop
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 05/02/2018
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: ec5b46dcfebf614e70a0b8ebf858af7b34906eae
ms.sourcegitcommit: 638de55f996d177063561b36d95c8c71ea7af3ed
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/17/2018
---
# <a name="use-onedrive-for-business-links-in-power-bi-desktop"></a>Usar os links do OneDrive for Business no Power BI Desktop
Muitas pessoas têm livros de trabalho do Excel armazenados em sua unidade do OneDrive for Business que seriam ótimos para uso com o Power BI Desktop. Com o **Power BI Desktop**, você pode usar links online para arquivos do **Excel** armazenados no **OneDrive for Business** para criar relatórios e visuais. Você pode usar uma conta de grupo do **OneDrive for Business** ou sua conta individual do **OneDrive for Business**.

Obter um link online do **OneDrive for Business** requer algumas etapas específicas. As seções a seguir explicam essas etapas, que permitem que você compartilhe o link do arquivo entre grupos, diferentes computadores e com seus colegas de trabalho.

## <a name="get-a-link-from-excel-starting-in-the-browser"></a>Obter um link do Excel, a partir do navegador
1. Navegue até o local do seu OneDrive for Business usando um navegador. Clique no arquivo que você deseja usar e selecione **Abrir no Excel**.
   
   > [!NOTE]
> A interface do navegador pode não ser exatamente igual à imagem a seguir. Há várias maneiras de selecionar **Abrir no Excel** para arquivos em sua interface de navegador do **OneDrive for Business**. Você pode usar qualquer opção que permite abrir o arquivo no Excel.
   > 
   > 
   
   ![](media/desktop-use-onedrive-business-links/odb-links_02.png)
2. No **Excel**, selecione **Arquivo > Informações** e selecione o link acima do botão **Proteger Pasta de Trabalho**. Selecione **Copiar link para a área de transferência** (pode ser que sua versão diga **Copiar caminho para a área de transferência**).
   
   ![](media/desktop-use-onedrive-business-links/odb-links_03.png)

## <a name="use-the-link-in-power-bi-desktop"></a>Usar o link Power BI Desktop
No Power BI Desktop, você pode usar o link que acabou de copiar para a área de transferência. Realize as seguintes etapas:

1. No Power BI Desktop, selecione **Obter Dados > Web**.
   
   ![](media/desktop-use-onedrive-business-links/odb-links_04.png)
2. Cole o link na caixa de diálogo **Da Web** (**não** selecione OK ainda).
   
    ![](media/desktop-use-onedrive-business-links/odb-links_05.png)
3. Observe a cadeia de caracteres *?web=1* no final do link – você deve *remover essa parte da cadeia de caracteres da URL da Web* **antes**de selecionar**OK**para que o**Power BI Desktop**navegue corretamente até o arquivo.
4. Se o **Power BI Desktop** solicitar suas credenciais, escolha **Windows** (para sites locais do SharePoint) ou **Conta Organizacional** (para sites do Office 365 ou OneDrive for Business).
   
   ![](media/desktop-use-onedrive-business-links/odb-links_06.png)

Uma janela do **Navegador** é exibida, permitindo que você selecione na lista de tabelas, planilhas e intervalos encontrados na pasta de trabalho do Excel. A partir daí, você pode usar o arquivo do OneDrive for Business como qualquer outro arquivo do Excel e criar relatórios e usá-los em conjuntos de dados como faria com qualquer outra fonte de dados.

> [!NOTE]
> Para usar um arquivo **OneDrive for Business** como fonte de dados no serviço do Power BI, com **Atualização de serviço** habilitada para esse arquivo, selecione **OAuth2** como o **método de autenticação** ao configurar as definições de atualização. Caso contrário, você pode encontrar um erro (como *Falha ao atualizar as credenciais de fonte de dados*) ao tentar se conectar ou atualizar. Selecionar **OAuth2** como método de autenticação resolve esse erro de credenciais.
> 
> 

