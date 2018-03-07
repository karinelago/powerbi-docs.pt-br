---
title: Usando dados de tabela do Analysis Services no Power BI Desktop
description: Dados de tabela do Analysis Services no Power BI Desktop
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
ms.date: 01/24/2018
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: a66272c4fc48c00b8636c7e7f1cd58261cbf5ea6
ms.sourcegitcommit: 88c8ba8dee4384ea7bff5cedcad67fce784d92b0
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/24/2018
---
# <a name="using-analysis-services-tabular-data-in-power-bi-desktop"></a>Usando dados de tabela do Analysis Services no Power BI Desktop
Com o Power BI Desktop, há duas maneiras de se conectar a seus Modelos de tabela dos SQL Server Analysis Services e obter dados deles: Explorar usando uma conexão dinâmica ou Selecionar itens e importá-los para o Power BI Desktop.

Vamos ver isso mais de perto.

**Explorar usando uma conexão dinâmica** – ao usar uma conexão dinâmica, os itens em seu Modelo de tabela ou perspectiva como tabelas, colunas e medidas aparecem na sua lista Campos do Power BI Desktop. Você pode usar as ferramentas avançadas de relatório e visualização do Power BI Desktop para explorar seu Modelo de tabela de maneiras novas e altamente interativas.

Ao se conectar dinamicamente, nenhum dado de Modelo de tabela é importado para o Power BI Desktop. Cada vez que você interage com uma visualização, o Power BI Desktop consulta o Modelo de tabela e calcula os resultados que você vê. Você está sempre vendo os dados mais recentes. Lembre-se, Modelos de tabela são altamente seguros. Itens que aparecem na Área de Trabalho do Power BI dependem de suas permissões para o modelo de Tabela ao qual você está conectado.

Quando você tiver criado relatórios dinâmicos na Área de Trabalho do Power BI, você pode compartilhá-los pela publicação em seu site do Power BI. Ao publicar um arquivo do Power BI Desktop com uma conexão dinâmica em um modelo de Tabela no site do Power BI, um gateway de dados local deverá ser instalado e configurado por um administrador. Para saber mais, veja [Gateway de dados local](service-gateway-onprem.md).

**Selecionar itens e importar para Área de Trabalho do Power BI** – quando você se conecta com essa opção, você pode selecionar itens como tabelas, colunas e medidas em seu Modelo de tabela ou perspectiva e carregá-los em um modelo do Power BI Desktop. Você pode usar o Editor de Consulta avançado do Power BI Desktop para personalizar ainda mais o que você deseja. Você pode usar os recursos de modelagem do Power BI Desktop para modelar ainda mais os dados. Nenhuma conexão dinâmica é mantida entre o Power BI Desktop e o Modelo de tabela. Você pode então explorar offline o modelo de Área de Trabalho do Power BI ou publicar seu site do Power BI.

## <a name="to-connect-to-a-tabular-model"></a>Para conectar-se a um Modelo de tabela
1. No Power BI Desktop, na guia **Home** , clique em **Obter Dados**.
   
   ![](media/desktop-analysis-services-tabular-data/pbid_sqlas_getdata.png)
2. Clique em **Banco de dados do SQL Server Analysis Services**, depois clique em **Conectar**.
   
   ![](media/desktop-analysis-services-tabular-data/pbid_sqlas_getdata_as.png)
3. Digite o Nome do servidor e selecione um modo de conexão. 
   
   ![](media/desktop-analysis-services-tabular-data/pbid_sqlas_getdata_as_server.png)
4. Essa etapa depende do modo de conexão selecionado:

* Se você estiver se conectando dinamicamente, no Navegador, selecione um Modelo de tabela ou uma perspectiva.
  
  ![](media/desktop-analysis-services-tabular-data/pbid_sqlas_getdata_as_live.png)
* Se você escolher Selecionar itens e obter dados, no Navegador, selecione um Modelo de tabela ou uma perspectiva. Além disso, você pode selecionar apenas determinadas tabelas ou colunas para carregar. Para formatar seus dados antes de carregar, clique em Editar para abrir o Editor de Consulta. Quando estiver pronto, clique em Carregar para importar os dados para o Power BI Desktop.

![](media/desktop-analysis-services-tabular-data/pbid_sqlas_getdata_as_select.png)

## <a name="frequently-asked-questions"></a>Perguntas frequentes
**Pergunta:** preciso de um gateway de dados local?

**Resposta:** depende. Se você usar o Power BI Desktop para se conectar dinamicamente a um modelo de Tabela, mas não tem intenção de publicar no site do Power BI, não será necessário ter um gateway. Por outro lado, se pretende publicar em seu site do Power BI, é necessário ter um gateway de dados para garantir a comunicação segura entre o serviço do Power BI e o servidor local do Analysis Services. Certifique-se de falar com o administrador do servidor do Analysis Services antes de instalar um gateway de dados.

Se escolher selecionar itens e obter dados, você importará dados do modelo de Tabela diretamente para seu arquivo do Power BI Desktop; portanto, não será necessário ter um gateway.

**Pergunta:** qual é a diferença entre a conexão dinâmica com um Modelo de tabela do serviço do Power BI e a conexão dinâmica no Power BI Desktop?

**Resposta:** durante a conexão dinâmica com um modelo de Tabela de seu site no serviço do Power BI para um banco de dados local do Analysis Services em sua organização, é necessário ter um gateway de dados local para proteger a comunicação entre eles. Durante a conexão dinâmica com um modelo de Tabela do Power BI Desktop, não é necessário ter um gateway, pois tanto o Power BI Desktop quanto o servidor do Analysis Services ao qual você está se conectando estão sendo executados localmente em sua organização. No entanto, se o arquivo do Power BI Desktop for publicado no seu site do Power BI, será necessário um gateway.

**Pergunta:** se eu criei uma conexão dinâmica, posso me conectar a uma outra fonte de dados no mesmo arquivo do Power BI Desktop?

**Resposta:** não. Você não pode explorar dados dinâmicos e conectar-se a outro tipo de fonte de dados no mesmo arquivo. Se você já importou dados ou conectou-se a uma fonte de dados diferente em um arquivo do Power BI Desktop, você precisará criar um novo arquivo para explorar dinamicamente.

**Pergunta:** se eu criei uma conexão dinâmica, posso editar o modelo ou a consulta no Power BI Desktop?

**Resposta:** é possível criar medidas de nível de relatório no Power BI Desktop, mas todos os outros recursos de consulta e de modelagem ficam desabilitados ao explorar dados dinâmicos.

**Pergunta:** se eu criei uma conexão dinâmica, ela é segura?

**Resposta:** Sim. Suas credenciais atuais do Windows são usadas para se conectar ao servidor do Analysis Services. Não é possível usar credenciais Básicas ou armazenadas no serviço do Power BI ou Power BI Desktop ao explorar dinamicamente.

**Pergunta:** no Navegador, vejo um modelo e uma perspectiva. Qual é a diferença?

**Resposta:** uma perspectiva é uma exibição específica de um Modelo de tabela. Ela pode incluir somente determinadas tabelas, colunas ou medidas dependendo de uma necessidade de análise de dados exclusiva. Um Modelo de tabela sempre contém pelo menos uma perspectiva, que pode incluir tudo no modelo. Se você não tiver certeza de qual(is) você deve selecionar, verifique com seu administrador.

## <a name="to-change-the-server-name-after-initial-connection"></a>Para alterar o nome do servidor após a conexão inicial
Depois de criar um arquivo do Power BI Desktop com uma conexão dinâmica de exploração, pode haver alguns casos em que você deseja alternar a conexão para um servidor diferente. Por exemplo, se você criou o arquivo do Power BI Desktop ao se conectar a um servidor de desenvolvimento e, antes da publicação para o serviço do Power BI, você deseja alternar a conexão para o servidor de produção.

1. Selecione **Editar Consultas** na Faixa de Opções.
   
   ![](media/desktop-analysis-services-tabular-data/pbid_sqlas_chname_editquery.png)
2. Digite o nome do novo servidor.
   
   ![](media/desktop-analysis-services-tabular-data/pbid_sqlas_chname_dialog.png)

