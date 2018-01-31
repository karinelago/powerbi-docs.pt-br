---
title: "Experiências de pacote de conteúdo de modelo no Power BI"
description: "Experiência de pacote de conteúdo de modelo"
services: powerbi
documentationcenter: 
author: markingmyname
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
ms.date: 10/09/2017
ms.author: maghan
ms.openlocfilehash: fb1aaded94ce5411cf26257a1e561125cec9a347
ms.sourcegitcommit: 6e693f9caf98385a2c45890cd0fbf2403f0dbb8a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2018
---
# <a name="template-content-pack-experiences-in-power-bi"></a>Experiências de pacote de conteúdo de modelo no Power BI
Esta seção destaca uma experiência típica de um usuário se conectando a um [pacote de conteúdo](../service-connect-to-services.md) de ISV. 

Tenha a experiência de conexão você mesmo conectando-se a um pacote de conteúdo lançado em https://app.powerbi.com/getdata/services (como o [pacote de conteúdo do GitHub](https://app.powerbi.com/getdata/services/github) descrito abaixo).

## <a name="connect"></a>Conectar-se
Para começar, o usuário navega pela galeria de pacotes de conteúdo e seleciona um pacote de conteúdo para se conectar. A entrada do pacote de conteúdo fornece um nome, um ícone e um texto descritivo que fornece mais informações para o usuário.

![conectar-se](media/template-content-pack-experience/github_data.png)

![conectar-se](media/template-content-pack-experience/github_connect.png)

## <a name="parameters"></a>Parâmetros
Após selecionar, o usuário será solicitado a fornecer parâmetros (se necessários). A caixa de diálogo de parâmetros é fornecida declarativamente pelo autor durante a criação do pacote de conteúdo.

Atualmente, a interface do usuário dos parâmetros é bem básica – não é possível enumerar as listas suspensas e a validação de entrada de dados é restrita a regex.

![parâmetros](media/template-content-pack-experience/github_params.png)

## <a name="credentials"></a>Credenciais
Depois dos parâmetros, o usuário deverá fazer logon.  Se a fonte der suporte a vários tipos de autenticação, o usuário escolherá a opção apropriada. Se a fonte exigir OAuth, a UI de logon do serviço será exibida quando o usuário pressionar Entrar.  Caso contrário, o usuário pode inserir suas credenciais na caixa de diálogo fornecida.

![Credenciais](media/template-content-pack-experience/github_login.png)

![conectar-se](media/template-content-pack-experience/github_creds2.png)

## <a name="instantiation"></a>Instanciação
Quando o logon for bem-sucedido, os artefatos incluídos no pacote de conteúdo - modelo, relatórios e painel - aparecerão na barra de navegação.  Esses artefatos são adicionados à conta de cada usuário.  Os dados são carregados de forma assíncrona para preencher o conjunto de dados (modelo).  O usuário, então, é capaz de consumir o painel, os relatórios e o modelo.

Por padrão, uma agenda de atualização diária é configurada para o usuário, o que avaliará novamente as consultas no modelo.  As credenciais fornecidas ao usuário devem permitir que eles atualizem os dados sem estarem presentes.

![Instanciação](media/template-content-pack-experience/github_dashboard.png)

## <a name="exploration-and-monitoring"></a>Exploração e monitoramento
Após o pacote de conteúdo ser serializado na conta do usuário, ele pode explorar e monitorar as informações/dados.

Normalmente, isso inclui:

* Exibir e personalizar o painel.
* Exibir e personalizar o relatório.
* Usar linguagem natural para fazer perguntas aos dados
* Usar a tela de exploração para explorar os dados no modelo de dados

É necessário levar em consideração o fornecimento de modelagem de linguagem natural (sinônimos) e um esquema de modelo compreensível para permitir melhores experiências de exploração.

