---
title: Criar um relatório paginado para o Servidor de Relatórios do Power BI
description: Saiba como criar um relatório paginado para o Servidor de Relatório do Power BI em algumas etapas simples.
services: powerbi
documentationcenter: ''
author: maggiesMSFT
manager: kfile
backup: ''
editor: ''
tags: ''
qualityfocus: no
qualitydate: ''
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 10/12/2017
ms.author: maggies
ms.openlocfilehash: 52f4d747738e294d6e73e6311819b6ec91f0b0a2
ms.sourcegitcommit: 493f160d04ed411ff4741c599adc63ba1f65230f
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33813704"
---
# <a name="create-a-paginated-report-for-power-bi-report-server"></a>Criar um relatório paginado para o Servidor de Relatórios do Power BI
Como o nome sugere, relatórios paginados podem ser executados em muitas páginas. Eles são dispostos em um formato fixo e oferecem personalização precisa. Relatórios paginados são arquivos .rdl.

É possível armazenar e gerenciar relatórios paginados no portal da Web do Servidor de Relatório do Power BI, assim como no portal da Web do SSRS (SQL Server Reporting Services). Você cria-os e edita-os no Construtor de Relatórios ou Designer de Relatórios no SSDT (SQL Server Data Tools) e então publica-os em qualquer dos portais da Web. Em seguida, os leitores de relatório em sua organização poderão exibi-los em um navegador ou em um aplicativo móvel do Power BI em seu dispositivo móvel.

![Relatório paginado do Servidor de Relatórios do Power BI](media/quickstart-create-paginated-report/reportserver-paginated-report.png)

Se você já tiver criado relatórios paginados no Construtor de Relatórios ou no Designer de Relatórios, então você estará pronto para criar relatórios paginados para o Servidor de Relatórios do Power BI. Caso contrário, veja algumas etapas rápidas para você começar.

## <a name="step-1-install-and-start-report-builder"></a>Etapa 1: instalar e iniciar o Construtor de Relatórios
Talvez você já tenha instalado o Construtor de Relatórios para criar relatórios para um servidor SSRS. É possível usar a mesma versão ou o Construtor de Relatórios para criar relatórios para o Servidor de Relatório do Power BI. Se você ainda não o tiver instalado, o processo será fácil.

1. No portal da Web do Servidor de Relatórios do Power BI, selecione **Novo** > **Relatório Paginado**.
   
    ![Menu Novo Relatório Paginado](media/quickstart-create-paginated-report/reportserver-new-paginated-report-menu.png)
   
    Se você ainda não tiver instalado o Construtor de Relatórios, ele orientará você pelo processo de instalação agora.
2. Após o Construtor de Relatórios ser instalado, ele é aberto na tela **Novo Relatório ou Conjunto de Dados**.
   
    ![Tela Novo Relatório ou Conjunto de Dados](media/quickstart-create-paginated-report/reportserver-paginated-new-report-screen.png)
3. Selecione o assistente para o tipo de relatório que você deseja criar:
   
   * Tabela ou matriz
   * Gráfico
   * Mapa
   * Em branco
4. Vamos começar com o Assistente de gráfico.
   
    O Assistente de gráfico explica as etapas para criação de um gráfico básico em um relatório. A partir daí, é possível personalizar seu relatório de maneiras praticamente ilimitadas.

## <a name="step-2-go-through-the-chart-wizard"></a>Etapa 2: passar pelo Assistente de gráfico
O Assistente de gráfico explica as etapas básicas para a criação de uma visualização em um relatório.

Os relatórios paginados podem se conectar a uma grande variedade de fontes de dados, do Microsoft SQL Server e do Banco de Dados SQL do Microsoft Azure ao Oracle, Hyperion e muito mais. Leia sobre [fontes de dados com suporte nos relatórios paginados](connect-data-sources.md).

Na primeira página do Assistente de gráfico, **Escolha um conjunto de dados**, é possível criar um conjunto de dados ou escolher um conjunto de dados compartilhado em um servidor. *Conjuntos de dados* retornam dados de relatório de uma consulta em uma fonte de dados externa.

1. Selecione **Procurar** > selecione um conjunto de dados compartilhado em um servidor > **Abrir** > **Avançar**.
   
    ![Assistente de Gráfico: Escolha um conjunto de dados](media/quickstart-create-paginated-report/reportserver-paginated-choose-dataset.png)
   
     Você precisa criar um conjunto de dados? Consulte [Create a shared or embedded dataset (Criar um conjunto de dados compartilhado ou inserido)](https://docs.microsoft.com/sql/reporting-services/report-data/create-a-shared-dataset-or-embedded-dataset-report-builder-and-ssrs).
2. Escolha um tipo de gráfico – nesse caso, um gráfico de barras.
   
    ![Assistente de Gráfico: Tipo de gráfico](media/quickstart-create-paginated-report/reportserver-paginated-choose-chart-type.png)
3. Organize os campos arrastando-os para as caixas **Categorias**, **Série** e **Valores**.
   
    ![Assistente de gráfico: Organizar campos](media/quickstart-create-paginated-report/reportserver-paginated-arrange-fields.png)
4. Selecione **Avançar** > **Concluir**.

## <a name="step-3-design-your-report"></a>Etapa 3: criar seu relatório
Agora você está no modo de exibição de Design de Relatório. Observe que os dados são dados de espaço reservado, não os seus dados.

![Modo de exibição de Design de Relatório](media/quickstart-create-paginated-report/reportserver-paginated-preview-report.png)

* Para exibir seus dados, selecione **Executar**.
  
     ![Executar relatório](media/quickstart-create-paginated-report/reportserver-paginated-run-report.png)
* Para voltar para o modo de exibição de Design, selecione **Design**.

Você pode modificar o gráfico que acabou de criar, alterando o layout, valores, legenda... qualquer coisa mesmo.

E é possível adicionar todos os tipos de outras visualizações: medidores, tabelas, matrizes, mapas e muito mais. É possível adicionar cabeçalhos e rodapés para várias páginas. Consulte os [Tutoriais do Construtor de Relatórios](https://docs.microsoft.com/sql/reporting-services/report-builder-tutorials) testar por conta própria.

![Modo de exibição de Design do Construtor de Relatórios](media/quickstart-create-paginated-report/reportserver-paginated-finished-design-report.png)

## <a name="step-4-save-your-report-to-the-report-server"></a>Etapa 4: salvar seu relatório no servidor de relatório
Quando seu relatório estiver pronto, salve-o no Servidor de Relatórios do Power BI.

1. No menu **Arquivo**, selecione **Salvar como** e salve-o no servidor de relatório. 
2. Agora é possível exibi-lo no navegador.
   
    ![Relatório paginado no navegador](media/quickstart-create-paginated-report/reportserver-paginated-report.png)

## <a name="next-steps"></a>Próximas etapas
Há muitos recursos excelentes para criar relatórios no Construtor de Relatórios e no Report Designer no SQL Server Data Tools. Os tutoriais do Construtor de Relatórios são um bom lugar para começar.

* [Tutoriais do Construtor de Relatórios](https://docs.microsoft.com/sql/reporting-services/report-builder-tutorials)
* [Manual do usuário do Servidor de Relatório do Power BI](user-handbook-overview.md)  

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)

