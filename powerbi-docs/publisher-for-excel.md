---
title: Editor do Power BI para Excel
description: Aprender a usar o editor do Power BI para Excel
services: powerbi
documentationcenter: 
author: davidiseminger
manager: kfile
backup: 
editor: 
tags: 
qualityfocus: complete
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 12/06/2017
ms.author: davidi
LocalizationGroup: Dashboards
ms.openlocfilehash: efd01bc6afec23d614a9f57b1150681983227350
ms.sourcegitcommit: 88c8ba8dee4384ea7bff5cedcad67fce784d92b0
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/24/2018
---
# <a name="power-bi-publisher-for-excel"></a>Editor do Power BI para Excel
Com o Microsoft **Power BI Publisher para Excel**, você pode tirar instantâneos de suas ideias mais importantes no Excel, como Tabelas Dinâmicas, gráficos e intervalos e fixá-los nos dashboards do Power BI.

![](media/publisher-for-excel/pbi_excel_publisher_pinobj_dashboard.png)

O que você pode fixar? Quase tudo em uma planilha do Excel. Você pode selecionar um intervalo de células de um texto ou tabela simples, uma Tabela Dinâmica ou Gráfico Dinâmico, ilustrações, imagens e texto.

O que você não pode fixar: mapas 3D nem visualizações em planilhas do Power View. Também há alguns elementos que você pode fixar, mas não faz muito sentido, como um filtro de Segmentação ou Linha do Tempo.

Quando você fixa um elemento do Excel, um novo bloco é adicionado a um painel de novo ou existente no Power BI. O novo bloco é um instantâneo e, portanto, não é dinâmico, mas ainda assim pode ser atualizado. Por exemplo, se você fizer uma alteração em uma Tabela Dinâmica ou em um gráfico já fixo, o bloco do dashboard no Power BI não será atualizado automaticamente, mas você ainda poderá atualizar os elementos fixos usando o **Gerenciador de Fixação**. Você aprenderá mais sobre o **Gerenciador de Fixação** nas seções a seguir.

## <a name="download-and-install"></a>Baixar e instalar
O Power BI Publisher para Excel é um suplemento que você pode baixar e instalar em versões de área de trabalho do Microsoft Excel 2007 e posteriores.

[Baixar o Power BI Publisher para Excel](http://go.microsoft.com/fwlink/?LinkId=715729)

Depois de instalar o publicador, você verá uma nova faixa de opções do **Power BI** no Excel, na qual é possível entrar (ou sair) do Power BI, fixar elementos nos dashboards e gerenciar os elementos fixos.

![](media/publisher-for-excel/pbi_excel_publisher_ribbon.png)

O suplemento **Power BI Publisher para Excel** está habilitado por padrão, mas se por alguma razão você não vir a guia de faixa de opções Power BI no Excel, será necessário habilitá-lo. Clique em **Arquivo** > **Opções** > **Suplementos** > **Suplementos COM**. Selecione **Microsoft Power BI Publisher para Excel**.

## <a name="pin-a-range-to-a-dashboard"></a>Fixar um intervalo em um painel
Você pode selecionar qualquer intervalo de células da planilha e fixar um instantâneo desse intervalo em um dashboard novo ou existente do Power BI. Você pode fixar o mesmo instantâneo em vários dashboards também.

Para começar, você precisa verificar se está conectado ao Power BI.

1. Selecione **Perfil** na guia de faixa de opções **Power BI** no Excel. Se você já entrou no Power BI, verá uma caixa de diálogo que mostra a conta à qual você está conectado no momento. Se esta for a conta que você deseja usar, ótimo! Vá para o próximo conjunto de etapas para fixar o intervalo. Selecione *Sair* se quiser usar uma conta diferente do Power BI. Se você não tiver se conectado, vá para a próxima etapa (Etapa 2).
   
   ![](media/publisher-for-excel/pbi_excel_publish_connect-to-data_0.png)
2. Se você não estiver conectado, selecione o link **Entrar** que aparece ao selecionar **Perfil** na guia de faixa de opções **Power BI** no Excel, na caixa de diálogo **Conectar-se ao Power BI**, digite o endereço de email da conta do Power BI que você deseja usar e selecione **Entrar**.
   
   ![](media/publisher-for-excel/pbi_excel_publish_connect-to-data_1a.png)

Depois de se conectar, siga estas etapas para fixar um intervalo em um dashboard:

1. No Excel, selecione a guia de faixa de opções **Power BI** para ver o botão da faixa de opções **Fixar**.
2. Selecione um intervalo em sua pasta de trabalho do Excel.
3. Clique no botão **Fixar** da faixa de opções do **Power BI** para mostrar a **caixa de diálogo Fixar no dashboard**. Se você ainda não tiver entrado no Power BI, será solicitado a fazer isso. Selecione um espaço de trabalho na lista suspensa **Espaço de trabalho**. Se você desejar fixá-lo em seu próprio dashboard, verifique se a opção **Meu Espaço de Trabalho** está marcada. Se você deseja fixar um painel em um espaço de trabalho de grupo, selecione o grupo na lista suspensa.
4. Escolha se deseja fixar em um *dashboard existente* ou criar um *novo dashboard*.
5. Clique em **OK** para fixar a seleção no dashboard.
6. Em **Fixar no dashboard**, selecione um dashboard existente no espaço de trabalho ou crie um novo e clique no botão **OK**.
   
   ![](media/publisher-for-excel/xl-publish.gif)

## <a name="pin-a-chart-to-a-dashboard"></a>Fixar um Gráfico em um painel
Basta clicar no gráfico e, em seguida, clicar em Fixar ![](media/publisher-for-excel/pbi_excel_publisher_pin.png).

![](media/publisher-for-excel/pbi_excel_publisher_chart.png)

## <a name="manage-pinned-elements"></a>Gerenciar elementos fixados
Com o **Gerenciador de Fixação**, é possível atualizar um bloco associado do elemento fixo no Power BI. Você também pode remover a marcação entre um elemento fixados em painéis no Power BI.

![](media/publisher-for-excel/pbi_excel_publisher_pin_manager2.png)

Para atualizar os blocos no dashboard, em **Gerenciador de Fixação**, selecione um ou mais elementos e selecione **Atualizar**.

Para remover o mapeamento entre um elemento fixo no Excel e o bloco associado em um dashboard, remova **Remover**. Quando você seleciona **Remover**, você *não* remove o elemento de sua planilha no Excel nem exclui o bloco associado no dashboard. Você está removendo o marcador ou o *mapeamento* entre eles. O elemento removido não aparecerá mais no **Gerenciador de Fixação**. Se você fixar o elemento novamente, ele será exibido como um novo bloco.

Para remover um elemento fixado (um bloco) de um painel, você precisará fazer isso no Power BI. No bloco que você deseja excluir, clique no ícone **Abrir menu** ![](media/publisher-for-excel/pbi_excel_publisher_tile_openmenu.png) e selecione **Excluir bloco**   ![](media/publisher-for-excel/pbi_excel_publisher_tile_trashcan.png).

## <a name="connect-to-data-in-power-bi"></a>Conectar-se a dados no Power BI
A partir da versão de julho de 2016 do **Power BI Publisher para Excel** (incluindo a versão atual, no link acima), você poderá se conectar diretamente aos dados no serviço do Power BI e analisá-los no Excel usando Tabelas Dinâmicas e Gráficos Dinâmicos. Esse recurso facilita o uso de dados do Power BI e do Excel em conjunto, para analisar os dados que são mais importantes para você.

Entre as melhorias estão as seguintes:

* Todos os drivers necessários para se conectar aos dados no Power BI são atualizados automaticamente a cada versão – sem a necessidade de instalar nem gerenciar os drivers por conta própria.
* Você não precisa mais baixar arquivos .odc para criar as conexões – O **Power BI Publisher para Excel** cria as conexões automaticamente quando você seleciona o relatório ou o conjunto de dados que deseja usar.
* Agora, você pode criar várias conexões e Tabelas Dinâmicas na mesma pasta de trabalho
* Os erros são corrigidos e específicos ao **Power BI Publisher para Excel**, em vez do uso de mensagens padrão do Excel

### <a name="how-to-connect-to-power-bi-data-in-excel"></a>Como se conectar a dados do Power BI no Excel
Para se conectar aos dados do Power BI usando o **Power BI Publisher para Excel**, siga estas etapas simples:

1. Verifique se você está conectado ao Power BI. As etapas que descrevem como entrar (ou como entrar com uma conta diferente) são fornecidas acima neste artigo.
2. Quando você estiver conectado ao Power BI com a conta que você deseja usar, selecione **Conectar-se a Dados** na guia de faixa de opções **Power BI** no Excel.
   
   ![](media/publisher-for-excel/pbi_excel_publish_connect-to-data_1.png)
3. O Excel se conecta ao Power BI usando uma conexão HTTPS e apresenta a caixa de diálogo **Conectar-se a dados no Power BI**, na qual você pode selecionar o *espaço de trabalho* em que você deseja selecionar seus dados (1, na imagem abaixo), a qual *tipo de dados* deseja se conectar, seja ou um **relatório** ou um **conjunto de dados** (2), e uma lista suspensa (3) que permite selecionar os *relatórios ou conjuntos de dados disponíveis* ao qual você pode se conectar.
   
   ![](media/publisher-for-excel/pbi_excel_publish_connect-to-data_2.png)
4. Quando você faz suas escolhas e seleciona **Conectar** na caixa de diálogo **Conectar-se a dados no Power BI**, o Excel prepara uma Tabela Dinâmica e exibe o painel **Campos da Tabela Dinâmica**, no qual você pode selecionar campos de seus dados do Power BI conectados e criar tabelas ou gráficos que o ajudam a analisar os dados.
   
   ![](media/publisher-for-excel/pbi_excel_publish_connect-to-data_3.png)

Se você não tiver dados no Power BI, o Excel detectará isso e oferecerá a criação de dados de exemplo para que você se conecte e tente exibir esses dados.

![](media/publisher-for-excel/pbi_excel_publish_connect-to-data_4.png)

Há são alguns pontos a serem considerados nesta versão do **Power BI Publisher para Excel**:

* **Dados compartilhados** – os dados que foram compartilhados com você, mas que não estão diretamente visíveis no Power BI, não estão disponíveis em **Conectar-se a Dados**.
* **SSAS local** – se o conjunto de dados que você selecionar for proveniente de um SSAS (SQL Server Analysis Services) local e o conjunto de dados no Power BI usar o DirectQuery para acessar os dados, o **Power BI Publisher para Excel** se conectará aos dados por meio da conexão de rede local e *não* passará pelo Power BI para se conectar aos dados. Assim, qualquer usuário que tentar se conectar a esses conjuntos de dados deverá estar conectados à rede local e serão autenticados para acessar esses dados usando o método de autenticação empregado pela instância do Analysis Services na qual os dados são armazenados.
* **Drivers necessários** - **O Power BI Publisher para Excel** instala todos os drivers necessários para o funcionamento deste recurso e faz isso automaticamente. Entre esses drivers instalados automaticamente está o driver do Banco de Dados OLE do Excel para o Analysis Services; se esse driver for removido pelo usuário (ou por qualquer outro motivo), a conexão com os dados do Power BI não funcionará.
* **O conjunto de dados deve incluir medidas** – O conjunto de dados deve incluir medidas de modelo definidas para que o Excel as considere como valores em PivotTables e analise os dados corretamente. Saiba mais sobre [Medidas](desktop-measures.md).
* **Suporte para Grupos** - Não há suporte para os conjuntos de dados compartilhados com pessoas de fora do grupo especificado; portanto, não é possível se conectar a eles.
* **Assinaturas gratuitas versus Pro** - Não há suporte para atividades associadas a grupos para usuários gratuitos do Power BI; consequentemente, eles não verão conjuntos de dados ou relatórios compartilhados com um grupo em seu próprio espaço de trabalho.
* **Relatórios ou conjuntos de dados compartilhados** - Não é possível se conectar aos relatórios ou conjuntos de dados que foram compartilhados com você.
* **Usando tabelas em vez de modelos de dados** - No momento, não há suporte para conjuntos de dados e tabelas que são criados mediante a importação somente de tabelas do Excel (sem modelo de dados); portanto, não é possível se conectar a eles.

Depois de criar gráficos interessantes ou outros visuais, como um intervalo de dados, você poderá fixá-los com facilidade em um dashboard do Power BI, conforme descrito anteriormente neste artigo.

## <a name="related-articles"></a>Artigos relacionados
Há várias maneiras de usar o Excel e o Power BI juntos e obter o melhor de ambos. Leia os artigos a seguir para obter mais informações.

* [Analisar no Excel](service-analyze-in-excel.md)
* [Analisar na solução de problemas do Excel](desktop-troubleshooting-analyze-in-excel.md)

