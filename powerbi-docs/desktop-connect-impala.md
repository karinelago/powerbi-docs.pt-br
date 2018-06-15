---
title: Conectar-se a um banco de dados Impala no Power BI Desktop
description: Conectar-se facilmente e usar um banco de dados Impala no Power BI Desktop
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 04/24/2018
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: b4e45d2ce20e42b4289ffcaaf7c487e4ae746ca0
ms.sourcegitcommit: 4b61588e3ab3c8bbb17276402dbf7fa00085a266
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/11/2018
ms.locfileid: "35301747"
---
# <a name="connect-to-an-impala-database-in-power-bi-desktop"></a>Conectar-se a um banco de dados Impala no Power BI Desktop
No Power BI Desktop, você pode se conectar a um banco de dados **Impala** e usar os dados subjacentes, assim como qualquer outra fonte de dados no Power BI Desktop.

## <a name="connect-to-an-impala-database"></a>Conectar-se a um banco de dados Impala
Para se conectar a um banco de dados **Impala**, selecione **Obter Dados** na faixa de opções **Início** no Power BI Desktop. Selecione **Banco de Dados** nas categorias à esquerda e você verá o **Impala**.

![](media/desktop-connect-impala/connect_impala_2.png)

Na janela **Impala** que será exibida, digite ou cole o nome do servidor Impala na caixa e selecione **OK**. Observe que você pode escolher **Importar** dados diretamente no Power BI ou pode usar o **DirectQuery**. Você pode aprender mais à respeito [usando o DirectQuery](desktop-use-directquery.md).

![](media/desktop-connect-impala/connect_impala_3a.png)

Quando solicitado, insira suas credenciais ou conecte-se anonimamente. O conector Impala é compatível com a autenticação Anônima, Básica (nome de usuário + senha) e do Windows.

![](media/desktop-connect-impala/connect_impala_4.png)

> [!NOTE]
> Quando você insere seu nome de usuário e senha para um servidor **Impala** específico, o Power BI Desktop usa as mesmas credenciais em tentativas de conexão subsequentes. Você pode modificar essas credenciais indo para **Arquivo > Opções e configurações > Configurações de fonte de dados**.
> 
> 

Depois que você se conectar com êxito, uma janela **Navegador** será mostrada e exibirá os dados disponíveis no servidor, dentre os quais você pode selecionar um ou vários elementos para importar e usar no **Power BI Desktop**.

![](media/desktop-connect-impala/connect_impala_5.png)

## <a name="considerations-and-limitations"></a>Considerações e limitações
Existem alguns limites e considerações que você deve ter em mente com relação ao conector **Impala**:

* O conector Impala é compatível com o gateway de dados local, usando qualquer um dos três mecanismos de autenticação suportados.

## <a name="next-steps"></a>Próximas etapas
Há todos os tipos de dados aos quais você pode se conectar usando o Power BI Desktop. Para obter mais informações sobre fontes de dados, confira os seguintes recursos:

* [Introdução ao Power BI Desktop](desktop-getting-started.md)
* [Fontes de dados no Power BI Desktop](desktop-data-sources.md)
* [Formatar e combinar dados com o Power BI Desktop](desktop-shape-and-combine-data.md)
* [Conectar-se a pastas de trabalho do Excel no Power BI Desktop](desktop-connect-excel.md)   
* [Inserir dados diretamente no Power BI Desktop](desktop-enter-data-directly-into-desktop.md)   

