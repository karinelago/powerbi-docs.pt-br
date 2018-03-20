---
title: "Conectar-se ao Adobe Analytics no Power BI Desktop (versão prévia)"
description: Conecte-se facilmente e use o Adobe Analytics no Power BI Desktop
services: powerbi
documentationcenter: 
author: davidiseminger
manager: kfile
backup: 
editor: 
tags: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 03/09/2018
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: efd6d066e2f98f86248730917c2f4aa0c8a39983
ms.sourcegitcommit: 4217430c3419046c3a90819c34f133ec7905b6e7
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2018
---
# <a name="connect-to-adobe-analytics-in-power-bi-desktop-preview"></a>Conectar-se ao Adobe Analytics no Power BI Desktop (versão prévia)
No **Power BI Desktop**, você pode se conectar ao **Adobe Analytics** e usar os dados subjacentes, assim como em qualquer outra fonte de dados no Power BI Desktop. 

![Obter dados do Adobe Analytics](media/desktop-connect-adobe-analytics/connect-adobe-analytics_01.png)

## <a name="enable-the-adobe-analytics-connector-preview"></a>Habilitar a versão prévia do conector do Adobe Analytics 
Como o conector do **Adobe Analytics** está atualmente em versão prévia, você precisa habilitar o recurso de versão prévia para que o conector fique disponível na janela **Obter Dados**. Para habilitar a versão prévia do conector, selecione **Arquivo > Opções e Configurações > Opções > Recursos de Versão Prévia** no Power BI Desktop e, em seguida, marque a caixa de seleção ao lado de **Indicadores**. 

![Habilitar a versão prévia do conector do Adobe Analytics nas Opções](media/desktop-connect-adobe-analytics/connect-adobe-analytics_02.png)

Você precisará reiniciar o **Power BI Desktop** depois de habilitar a versão prévia do conector do Adobe Analytics.

## <a name="connect-to-adobe-analytics-data"></a>Conectar-se aos dados do Adobe Analytics
Para se conectar aos dados do **Adobe Analytics**, selecione **Obter Dados** na faixa de opções **Início** no Power BI Desktop. Selecione **Serviços Online** nas categorias à esquerda, e você verá o **Conector do Adobe Analytics**.

![Obter dados do Adobe Analytics](media/desktop-connect-adobe-analytics/connect-adobe-analytics_01.png)

Na janela do **Adobe Analytics** que é exibida, selecione o botão **Entrar** e, em seguida, forneça suas credenciais para entrar em sua conta do Adobe Analytics. A janela de entrada do Adobe aparece, conforme mostrado na imagem a seguir.

![Entrar no Adobe Analytics](media/desktop-connect-adobe-analytics/connect-adobe-analytics_03.png)

Quando solicitado, insira o nome de usuário e a senha. Quando a conexão é estabelecida, você pode visualizar e selecionar várias dimensões e medidas na caixa de diálogo **Navegador** do Power BI para criar uma única saída de tabela. Você também pode fornecer os parâmetros de entrada necessários para os itens selecionados. 

![Selecionar dados usando o Navegador](media/desktop-connect-adobe-analytics/connect-adobe-analytics_04.png)

Você pode **Carregar** a tabela selecionada, que leva toda a tabela para o **Power BI Desktop** ou você pode **Editar** a consulta, o que abre **Editor de Consultas** para filtrar e refinar o conjunto de dados que você deseja usar e, em seguida, carregar tal conjunto de dados refinado no **Power BI Desktop**.

![Carregar ou editar dados no Navegador](media/desktop-connect-adobe-analytics/connect-adobe-analytics_05.png)


## <a name="next-steps"></a>Próximas etapas
Há todos os tipos de dados aos quais você pode se conectar usando o Power BI Desktop. Para obter mais informações sobre fontes de dados, confira os seguintes recursos:

* [Introdução ao Power BI Desktop](desktop-getting-started.md)
* [Fontes de dados no Power BI Desktop](desktop-data-sources.md)
* [Formatar e combinar dados com o Power BI Desktop](desktop-shape-and-combine-data.md)
* [Conectar-se a pastas de trabalho do Excel no Power BI Desktop](desktop-connect-excel.md)   
* [Inserir dados diretamente no Power BI Desktop](desktop-enter-data-directly-into-desktop.md)   

