---
title: 'Tutorial: Explorar o Servidor de Relatórios do Power BI em uma VM'
description: Neste tutorial, você cria uma máquina virtual com o Servidor de Relatórios do Power BI já instalado e explora o portal da Web.
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-report-server
ms.topic: tutorial
ms.date: 05/18/2018
ms.author: maggies
ms.openlocfilehash: 38985014407a4d64998e25f6944f57aedcc67309
ms.sourcegitcommit: aa8045e42b979206c600bce4a8d17de1f0620462
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/22/2018
ms.locfileid: "34444993"
---
# <a name="tutorial-explore-the-power-bi-report-server-web-portal-in-a-vm"></a>Tutorial: Explorar o portal da Web do Servidor de Relatórios do Power BI em uma VM
Neste tutorial, você cria uma máquina virtual do Azure com o Servidor de Relatórios do Power BI já instalado, para que possa experimentar a exibição, a edição e o gerenciamento de relatórios paginados e de exemplo do Power BI, bem como de KPIs.

![Portal da Web do Servidor de Relatórios](media/tutorial-explore-report-server-web-portal/power-bi-report-server-browser-in-vm-no-numbers.png)

Estas são as tarefas que você executará neste tutorial:

> [!div class="checklist"]
> * Criar e conectar-se a uma VM
> * Iniciar e explorar o portal da Web do Servidor de Relatórios do Power BI
> * Marcar um item favorito
> * Exibir e editar um relatório do Power BI
> * Exibir, gerenciar e editar um relatório paginado
> * Exibir uma pasta de trabalho do Excel no Excel Online

Para este tutorial, você precisará de uma assinatura do Azure. Se não tiver uma, crie uma [conta gratuita](https://azure.microsoft.com/free/?WT.mc_id=A261C142F) antes de começar.

## <a name="create-a-power-bi-report-server-vm"></a>Criar uma VM do Servidor de Relatórios do Power BI

Felizmente, a equipe do Power BI criou uma VM que vem com o Servidor de Relatórios do Power BI já instalado.

1. No Azure Marketplace, abra o [Servidor de Relatórios do Power BI](https://azuremarketplace.microsoft.com/marketplace/apps/reportingservices.technical-preview?tab=Overview).  

2. Selecione **Obter agora**.
3. Para aceitar os termos de uso e a política de privacidade do provedor, selecione **Continuar**.

    ![Criar VM do Servidor de Relatórios do Power BI](media/tutorial-explore-report-server-web-portal/power-bi-report-server-virtual-machine-create.png)

4. **Etapa 1, Básico**, para **Nome da VM**, insira **reportservervm**.

5. Crie um nome de usuário e senha.

6. Para **Grupo de recursos**, mantenha **Criar novo** e chame-o de **reportserverresourcegroup**.

    Se você usar o tutorial mais de uma vez, será necessário dar um nome diferente ao grupo de recursos. Você não pode repetir o nome do grupo de recursos em uma assinatura. 

7. Mantenha os outros valores padrão > **OK**.

    ![Nomeie a VM e o grupo de recursos](media/tutorial-explore-report-server-web-portal/power-bi-report-server-create-resource-group.png)

8. **Etapa 2, Configurações**, mantenha os valores padrão > **OK**.

9. **Etapa 3, Resumo** > **OK**.

10. **Etapa 4**, examinar os Termos do usuário e a política de privacidade > **Criar**.

    O processo **Enviando implantação para Servidor de Relatórios do Power BI** leva alguns minutos.

## <a name="connect-to-your-virtual-machine"></a>Conectar-se à sua máquina virtual

1. No painel de navegação esquerdo do Azure, selecione **Máquinas virtuais**. 

2. Na caixa **Filtrar por nome**, digite "report". 

3. Selecione a VM chamada **REPORTSERVERVM**.

    ![Exibir a máquina virtual](media/tutorial-explore-report-server-web-portal/power-bi-report-server-view-virtual-machine.png)

4. Na máquina virtual REPORTSERVERVM, selecione **Conectar**.

    ![Conectar-se à máquina virtual](media/tutorial-explore-report-server-web-portal/power-bi-report-server-connect-to-virtual-machine.png)

5. Na caixa de diálogo Conexão de Área de Trabalho Remota, selecione **Conectar**.

6. Insira o nome e a senha que você criou para a VM > **OK**.

7. A caixa de diálogo seguinte diz que a identidade do computador remoto não pode ser identificada. Selecione **Sim**.

   Pronto! Sua nova VM é aberta.

## <a name="power-bi-report-server-on-the-vm"></a>Servidor de Relatórios do Power BI na VM

Quando sua VM abrir, estes são os itens que você verá na área de trabalho.

![Máquina virtual do Servidor de Relatórios do Power BI é iniciada](media/tutorial-explore-report-server-web-portal/power-bi-report-server-start-vm-numbered.png)

|Number  |O que é  |
|---------|---------|
|![Número 1](media/tutorial-explore-report-server-web-portal/number-1.png) | Inicia o SQL Server Data Tools para criar relatórios paginados (.RDL) |
|![Número 2](media/tutorial-explore-report-server-web-portal/number-2.png) | Relatórios de exemplo do Power BI (.PBIX)  |
|![Número 3](media/tutorial-explore-report-server-web-portal/number-3.png) | Links para documentação do Servidor de Relatórios do Power BI   |
|![Número 4](media/tutorial-explore-report-server-web-portal/number-4.png) | Iniciar o Power BI Desktop otimizado para o Servidor de Relatórios do Power BI (março de 2018)  |
|![Número 5](media/tutorial-explore-report-server-web-portal/number-5.png) | Abre o portal da Web do Servidor de Relatórios do Power BI no navegador   |

Clique duas vezes no ícone **Portal da Web do Servidor de Relatórios**. O navegador abre http://localhost/reports/browse. No portal da Web, você verá vários arquivos agrupados por tipo. 

![Portal da Web do Servidor de Relatório do Power BI](media/tutorial-explore-report-server-web-portal/power-bi-report-server-browser-in-vm.png)

|Number  |O que é  |
|---------|---------|
|![Número 1](media/tutorial-explore-report-server-web-portal/number-1.png) | KPIs criados no portal da Web |
|![Número 2](media/tutorial-explore-report-server-web-portal/number-2.png) |  Relatórios do Power BI (.PBIX)  |
|![Número 3](media/tutorial-explore-report-server-web-portal/number-3.png) | Relatórios móveis criados no Publicador de Relatórios Móveis do SQL Server  |
|![Número 4](media/tutorial-explore-report-server-web-portal/number-4.png) |  Relatórios paginados criados no Construtor de Relatórios ou no SQL Server Data Tools  |
|![Número 5](media/tutorial-explore-report-server-web-portal/number-5.png) | Pastas de trabalho do Excel   | 
|![Número 6](media/tutorial-explore-report-server-web-portal/number-6.png) | Fontes de dados para relatórios paginados | 


## <a name="tag-your-favorites"></a>Marcar seus favoritos
É possível marcar os relatórios e os KPIs que você deseja que sejam favoritos. Eles são mais fáceis de localizar porque são reunidos em uma única pasta de favoritos, no portal da Web e nos aplicativos móveis do Power BI. 

1. Selecione as reticências (**...**) no canto superior direito de **Margem de Lucro** KPI > **Adicionar aos Favoritos**.
   
    ![Adicionar aos Favoritos](media/tutorial-explore-report-server-web-portal/power-bi-report-server-add-to-favorites.png)
2. Selecione **Favoritos** na faixa de opções do portal da web para vê-lo junto com os outros favoritos na página Favoritos no portal da web.
   
    ![Exibir Favoritos](media/tutorial-explore-report-server-web-portal/power-bi-report-server-favorites.png)

3. Selecione **Procurar** para voltar ao portal da Web.
   
## <a name="view-items-in-list-view"></a>Exibir itens na exibição de Lista
Por padrão, o portal da Web exibe seu conteúdo em exibição de bloco.

É possível mudar para a exibição de lista, em que é fácil mover ou excluir vários itens ao mesmo tempo. 

1. Selecione **Blocos** > **Lista**.
   
    ![Alternar modos de exibição](media/tutorial-explore-report-server-web-portal/report-server-web-portal-list-view.png)

2. Volte para a exibição de Blocos: selecione **Lista** > **Blocos**.

## <a name="power-bi-reports"></a>Relatórios do Power BI

Você pode exibir e interagir com relatórios do Power BI no portal da Web e iniciar o Power BI Desktop no portal da Web.

### <a name="view-power-bi-reports"></a>Exibir relatórios do Power BI

1. No portal da Web, em **Relatórios do Power BI**, selecione **Relatório de Exemplo de Visão Geral do Cliente**. O relatório é aberto no navegador.

1. Selecione o bloco dos Estados Unidos no mapa de árvore para ver como os valores relacionados são destacados em outros visuais.

    ![Relatório do Power BI destacado](media/tutorial-explore-report-server-web-portal/power-bi-report-server-power-bi.png)

### <a name="edit-in-power-bi-desktop"></a>Editar no Power BI Desktop

1. Selecione **Editar no Power BI Desktop**.

1. Selecione **Permitir** para permitir que este site abra um programa em seu computador. 

     O relatório é aberto no Power BI Desktop. Observe o nome na barra superior, "Power BI Desktop (março de 2018)". Trata-se da versão otimizada para o Servidor de Relatórios do Power BI.

    ![Power BI Desktop](media/tutorial-explore-report-server-web-portal/power-bi-report-server-power-bi-desktop.png)

     Use a versão do Power BI Desktop instalada na VM. Você não pode entrar em vários domínios para carregar um relatório.

3. No painel Campos, expanda a tabela Clientes e arraste o campo Ocupação para os filtros de nível de Relatório.

    ![Arraste um campo para o painel de Filtros](media/tutorial-explore-report-server-web-portal/power-bi-report-server-desktop-filter.png)

1. Salve o relatório.

1. Volte para o relatório no navegador e selecione o ícone de **Atualizar** o navegador.

    ![Ícone de Atualizar o navegador](media/tutorial-explore-report-server-web-portal/power-bi-report-server-browser-refresh.png)

8. Expanda o painel **Filtros** à direita para ver o filtro **Ocupação** que você adicionou. Selecione **Profissional**.

    ![Relatório do Power BI filtrado](media/tutorial-explore-report-server-web-portal/power-bi-report-server-power-bi-filtered.png)

3. Selecione **Procurar** para voltar ao portal da Web.

## <a name="paginated-rdl-reports"></a>Relatórios paginados (.RDL)

Você pode exibir e gerenciar relatórios paginados e iniciar o Construtor de Relatórios do portal da Web.

### <a name="manage-a-paginated-report"></a>Gerenciar um relatório paginado

1. No portal da Web, em **Relatórios Paginados**, selecione as reticências (...) ao lado de **Pedido de Vendas** > **Gerenciar**.

1. Selecione **Parâmetros**, altere o valor padrão de **SalesOrderNumber** para **SO50689** > **Aplicar**.

   ![Definir parâmetros de relatório](media/tutorial-explore-report-server-web-portal/power-bi-report-server-set-parameters.png)

3. Selecione **Procurar** para voltar ao portal da Web.

### <a name="view-a-paginated-report"></a>Exibir um relatório paginado

1. Selecione **Pedido de Vendas** no portal da Web.
 
3.  Você verá que o parâmetro **Pedido** definido por você, **SO50689**, será aberto. 

    ![Parâmetro de relatório paginado](media/tutorial-explore-report-server-web-portal/power-bi-report-server-paginated.png)

    Você pode alterar esse parâmetro aqui, junto com os outros parâmetros, sem alterar os padrões.

1. Selecione **Pedido** **SO48339** > **Exibir Relatório**.

4. Você verá que se trata da página 1 de 2. Selecione a seta para a direita para ver a segunda página. A tabela continua nessa página.

    ![Página 2 de 2 do relatório paginado](media/tutorial-explore-report-server-web-portal/power-bi-report-server-paginated-2-of-2.png)

5. Selecione **Procurar** para voltar ao portal da Web.

### <a name="edit-a-paginated-report"></a>Editar um relatório paginado

Você pode editar relatórios paginados no Construtor de Relatórios e pode iniciar o Construtor de Relatórios diretamente no navegador.

1. No portal da Web, selecione as reticências (...) ao lado de **Pedido de Vendas** > **Editar no Construtor de Relatórios**.

1. Selecione **Permitir** para permitir que este site abra um programa em seu computador.

1. O relatório de Pedido de Vendas é aberto no modo de exibição de Design no Construtor de Relatórios.

    ![Modo de exibição de Design, relatório paginado](media/tutorial-explore-report-server-web-portal/power-bi-report-server-paginated-design-view.png)

1. Selecione **Executar** para visualizar o relatório.

    ![Visualizar um relatório paginado](media/tutorial-explore-report-server-web-portal/power-bi-report-server-paginated-preview.png)

5. Feche o Construtor de Relatórios e volte para o navegador.

## <a name="view-excel-workbooks"></a>Exibir pastas de trabalho do Excel

Você pode exibir e interagir com pastas de trabalho do Excel no Excel Online no Servidor de Relatórios do Power BI. 

1. Selecione a pasta de trabalho do Excel **Office Liquidation Sale.xlsx**. Ele pode solicitar credenciais. Selecione **Cancelar**. 
    Ela é aberta no portal da Web.
1. Selecione **Dispositivo** na segmentação.

    ![Excel Online no portal da Web](media/tutorial-explore-report-server-web-portal/power-bi-report-server-excel-online.png)

1. Selecione **Procurar** para voltar ao portal da Web.

## <a name="clean-up-resources"></a>Limpar recursos

Agora que você concluiu o tutorial, exclua o grupo de recursos, a máquina virtual e todos os recursos relacionados. 

- Para fazer isso, selecione o grupo de recursos para a VM e selecione **Excluir**.

## <a name="next-steps"></a>Próximas etapas

Neste tutorial, você criou uma VM com o Servidor de Relatórios do Power BI. Você testou algumas das funcionalidades do portal da Web e abriu um relatório do Power BI e um relatório paginado em seus respectivos editores. Essa VM tem fontes de dados do SQL Server Analysis Services instaladas. Portanto, você pode tentar criar seus próprios relatórios paginados e do Power BI com as mesmas fontes de dados. 

Para saber mais sobre a criação de relatórios para o Servidor de Relatórios do Power BI, siga adiante.

> [!div class="nextstepaction"]
> [Criar um relatório do Power BI para o Servidor de Relatórios do Power BI](./quickstart-create-powerbi-report.md)



