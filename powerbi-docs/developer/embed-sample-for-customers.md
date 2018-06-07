---
title: Inserir conteúdo do Power BI em um aplicativo para seus clientes
description: Aprenda a integrar ou inserir um dashboard, um bloco ou um relatório em um aplicativo Web usando as APIs do Power BI para seus clientes.
author: markingmyname
ms.author: maghan
ms.date: 05/25/2018
ms.topic: tutorial
ms.service: powerbi
ms.component: powerbi-developer
ms.custom: mvc
manager: kfile
ms.openlocfilehash: ae683dfbeb7b3848575ab766c33b695eb823d497
ms.sourcegitcommit: 80d6b45eb84243e801b60b9038b9bff77c30d5c8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34721031"
---
# <a name="tutorial-embed-a-power-bi-report-dashboard-or-tile-into-an-application-for-your-customers"></a>Tutorial: inserir um relatório, um dashboard ou um bloco do Power BI em um aplicativo para seus clientes
Com o **Power BI Embedded no Azure**, você pode inserir relatórios, painéis ou blocos em um aplicativo usando **app owns data**. **App owns data** representa um aplicativo que usa o Power BI como sua plataforma de análise incorporada. Normalmente, esse é um cenário de **desenvolvedor ISV**. Como **desenvolvedor ISV**, você pode criar conteúdo do Power BI que exibe relatórios, painéis ou blocos em um aplicativo totalmente integrado e interativo, sem precisar que os usuários do aplicativo tenham uma licença do Power BI, ou até mesmo saibam que o Power BI está ativado nos bastidores. Este tutorial demonstra como integrar um relatório em um aplicativo usando o SDK do .NET do **Power BI** com a API JavaScript do **Power BI** ao usar o **Power BI Embedded no Azure** para clientes com **app owns data**.

Neste tutorial, você aprenderá a:
>[!div class="checklist"]
>* Registrar um aplicativo no Azure.
>* Insira um relatório do Power BI em um aplicativo.

## <a name="prerequisites"></a>Pré-requisitos
Para começar, você precisará de uma conta do **Power BI Pro**, que será sua **conta mestre**, e de uma assinatura do **Microsoft Azure**.

* Se não estiver inscrito no **Power BI Pro**, [inscreva-se para uma avaliação gratuita](https://powerbi.microsoft.com/en-us/pricing/) antes de começar.
* Caso você não tenha uma assinatura do Azure, crie uma [conta gratuita](https://azure.microsoft.com/free/?WT.mc_id=A261C142F) antes de começar.
* Você precisa ter seu próprio [locatário do Azure Active Directory](create-an-azure-active-directory-tenant.md) configurado.
* Você precisa do [Visual Studio](https://www.visualstudio.com/) instalado (versão 2013 ou posterior).

## <a name="setup-your-embedded-analytics-development-environment"></a>Configurar seu ambiente de desenvolvimento de análise integrada

Antes de começar a inserir relatórios, painéis ou blocos em seu aplicativo, você precisará verificar se o ambiente está configurado para permitir a inserção. Como parte da instalação, será necessário fazer o seguinte.

Você pode examinar a [Ferramenta de experiência de integração](https://aka.ms/embedsetup/AppOwnsData) para iniciar rapidamente e baixar um aplicativo de exemplo que ajuda a criar um ambiente e a inserir um relatório.

No entanto, se você optar por configurar o ambiente manualmente, você poderá continuar abaixo.
### <a name="register-an-application-in-azure-active-directory-azure-ad"></a>Registrar um aplicativo no Azure AD (Azure Active Directory)

Registre seu aplicativo no Azure Active Directory para permitir que ele tenha acesso às APIs REST do Power BI. Isso permite que você estabeleça uma identidade para seu aplicativo e especifique permissões para recursos REST do Power BI.

1. Aceite os [Termos da API do Microsoft Power BI](https://powerbi.microsoft.com/api-terms).

2. Entre no [Portal do Azure](https://portal.azure.com).
 
    ![Página principal do portal do Azure](media/embed-sample-for-customers/embed-sample-for-customers-002.png)

3. No painel de navegação esquerdo, escolha **Todos os Serviços**, selecione **Registros de Aplicativo** e, em seguida, selecione **Novo registro de aplicativo**.
   
    ![Pesquisa de registro de aplicativo](media/embed-sample-for-customers/embed-sample-for-customers-003.png)</br>
    ![Registro de novo aplicativo](media/embed-sample-for-customers/embed-sample-for-customers-004.png)

4. Siga os prompts e crie um novo aplicativo. Para app owns data, você precisa usar **Nativo** como o tipo de aplicativo. Você também precisará fornecer um **URI de redirecionamento** que o **Azure AD** usa para retornar respostas de token. Insira um valor específico ao seu aplicativo, por exemplo, http://localhost:13526/redirect).

    ![Criar Aplicativo](media/embed-sample-for-customers/embed-sample-for-customers-005.png)

### <a name="apply-permissions-to-your-application-within-azure-active-directory"></a>Aplique permissões ao seu aplicativo no Azure Active Directory

Você precisará habilitar permissões adicionais para seu aplicativo além do que foi fornecido na página de registro do aplicativo. Você precisa estar conectado com a conta *mestre*, usada para inserção, que precisa ser uma conta de administrador global.

### <a name="use-the-azure-active-directory-portal"></a>Use o portal do Azure Active Directory

1. Navegue até [Registros de aplicativo](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ApplicationsListBlade) no Portal do Azure e selecione o aplicativo que você está usando para inserção.
   
    ![Escolhendo o aplicativo](media/embed-sample-for-customers/embed-sample-for-customers-006.png)

2. Selecione **Configurações** e, em **Acesso à API**, selecione **Permissões necessárias**.
   
    ![Permissões necessárias](media/embed-sample-for-customers/embed-sample-for-customers-008.png)

3. Selecione **Microsoft Azure Active Directory** e, em seguida, certifique-se de **Acessar o diretório como o usuário conectado** esteja selecionado. Selecione **Salvar**.
   
    ![Permissões do Microsoft Azure AD](media/embed-sample-for-customers/embed-sample-for-customers-011.png)

4. Selecione **Adicionar**.

    ![Adicionar permissões](media/embed-sample-for-customers/embed-sample-for-customers-012.png)

5. Selecione **Selecionar uma API**.

    ![Adicionar acesso à API](media/embed-sample-for-customers/embed-sample-for-customers-013.png)

6. Selecione **Serviço do Power BI** e, em seguida, selecione **Selecionar**.

    ![Selecione Serviços do PBI](media/embed-sample-for-customers/embed-sample-for-customers-014.png)

7. Selecione todas as permissões em **Permissões Delegadas**. Você precisará selecioná-las uma a uma para salvar as seleções. Selecione **Salvar** quando terminar.
   
    ![Selecione permissões delegadas](media/embed-sample-for-customers/embed-sample-for-customers-015.png)

8. Em **Permissões necessárias**, selecione **Conceder Permissões**.
   
    A ação **Conceder Permissões** é necessária para a *conta mestre*, a fim de evitar prompts de consentimento pelo Azure AD. Se a conta que executar essa ação for um Administrador Global, você concederá permissões para todos os usuários de sua organização a esse aplicativo. Se a conta que executar essa ação for a *conta mestre* e não for um Administrador Global, você concederá permissões apenas para a *conta mestre* a esse aplicativo.
   
    ![Conceder permissões na caixa de diálogo Permissões necessárias](media/embed-sample-for-customers/embed-sample-for-customers-016.png)

## <a name="setup-your-power-bi-environment"></a>Configure seu ambiente do Power BI

### <a name="create-an-app-workspace"></a>Criar um espaço de trabalho de aplicativo

Se estiver inserindo relatórios, dashboards ou blocos para seus clientes, você precisará colocar o conteúdo dentro de um espaço de trabalho do aplicativo. A conta *mestre* precisa ser um administrador do espaço de trabalho do aplicativo.

1. Comece criando o espaço de trabalho. Selecione **espaços de trabalho** > **Criar espaço de trabalho do aplicativo**. Trata-se do local em que será colocado o conteúdo que seu aplicativo precisa acessar.

    ![Criar espaço de trabalho](media/embed-sample-for-customers/embed-sample-for-customers-020.png)

2. Nomeie o espaço de trabalho. Se a **ID do Espaço de Trabalho** correspondente não estiver disponível, edite-a para criar uma ID exclusiva. Esse também será o nome do aplicativo.

    ![Nomeie o espaço de trabalho](media/embed-sample-for-customers/embed-sample-for-customers-021.png)

3. Você tem algumas opções para definir. Se você escolher **Público**, qualquer pessoa na sua organização poderá ver o que está no espaço de trabalho. **Particular**, por outro lado, significará que somente os membros do espaço de trabalho poderão ver o conteúdo.

    ![Particular/Público](media/embed-sample-for-customers/embed-sample-for-customers-022.png)

    Não é possível alterar a configuração Público/Particular depois de criar o grupo.

4. Também é possível escolher se os membros podem **editar** ou se terão acesso **somente exibição**.

    ![Adicionando membros](media/embed-sample-for-customers/embed-sample-for-customers-023.png)

5. Adicione os endereços de email das pessoas que você deseja que tenham acesso ao espaço de trabalho e selecione **Adicionar**. Você não pode adicionar aliases de grupos, apenas indivíduos.

6. Decida se cada pessoa será um membro ou um administrador. Os administradores podem editar o espaço de trabalho, incluindo a adição de outros membros. Os membros podem editar o conteúdo no espaço de trabalho, a menos que tenham acesso somente exibição. Os membros e os administradores podem publicar o aplicativo.

Agora, você pode exibir o novo espaço de trabalho. O Power BI cria o espaço de trabalho e o abre. Ele aparece na lista de espaços de trabalho dos quais você é um membro. Como você é um administrador, você pode selecionar as reticências (...) para voltar e fazer alterações, adicionar novos membros ou alterar as permissões deles.

   ![Novo espaço de trabalho](media/embed-sample-for-customers/embed-sample-for-customers-025.png)

### <a name="create-and-publish-your-reports"></a>Crie e publique seus relatórios

É possível criar seus relatórios e conjuntos de dados usando o Power BI Desktop e, em seguida, publicar esses relatórios em um espaço de trabalho do aplicativo. O usuário final que publicar os relatórios precisará ter uma licença Power BI Pro para publicar em um espaço de trabalho do aplicativo.

1. Baixe o exemplo [Blog Demo](https://github.com/Microsoft/powerbi-desktop-samples) do GitHub.

    ![relatório de exemplo](media/embed-sample-for-customers/embed-sample-for-customers-026-1.png)

2. Abra o relatório de exemplo do PBIX no **Power BI Desktop**

   ![Relatório de área de trabalho do PBI](media/embed-sample-for-customers/embed-sample-for-customers-027.png)

3. Publique no **espaço de trabalho do aplicativo**

   ![Relatório de área de trabalho do PBI](media/embed-sample-for-customers/embed-sample-for-customers-028.png)

    Agora, você pode exibir o relatório no serviço do Power BI online

   ![Relatório de área de trabalho do PBI](media/embed-sample-for-customers/embed-sample-for-customers-029.png)

## <a name="embed-your-content"></a>Insira seu conteúdo

A inserção para seus clientes dentro de seu aplicativo exige que você obtenha um **token de acesso** para sua conta mestre do **Azure AD**. É necessário [obter token de acesso do Azure AD](get-azuread-access-token.md#access-token-for-non-power-bi-users-app-owns-data) para o seu aplicativo do Power BI usando app owns data antes de pode fazer chamadas à API do Power BI.

Execute estas etapas para começar a incorporar o conteúdo usando um aplicativo de exemplo.

1. Baixe o [exemplo App Owns Data](https://github.com/Microsoft/PowerBI-Developer-Samples) do GitHub para começar.

    ![Exemplo de aplicativo App Owns Data](media/embed-sample-for-customers/embed-sample-for-customers-026.png)

2. Abra o arquivo Web.config no aplicativo de exemplo. Há 5 campos que você precisará preencher para executar o aplicativo com êxito. Os campos **clientID**, **groupId**, **reportId**, **pbiUsername** e **pbiPassword**.

      ![Arquivo de configuração da Web](media/embed-sample-for-customers/embed-sample-for-customers-030.png)

    * Preencha as informações de **clientId** com a **ID do Aplicativo** do **Azure**. A **clientId** é usada pelo aplicativo para se identificar aos usuários dos quais você está solicitando permissões. Para obter a **clientId**, siga estas etapas:

    1. Entre no [Portal do Azure](https://portal.azure.com).

        ![Página principal do portal do Azure](media/embed-sample-for-customers/embed-sample-for-customers-002.png)

    2. No painel de navegação esquerdo, escolha **Todos os Serviços** e selecione **Registros de Aplicativo**.

        ![Pesquisa de registro de aplicativo](media/embed-sample-for-customers/embed-sample-for-customers-003.png)
    3. Selecione o aplicativo para o qual você deseja obter **clientId**.

        ![Escolhendo o aplicativo](media/embed-sample-for-customers/embed-sample-for-customers-006.png)

    4. Você deve ver uma **ID do Aplicativo** listada como um GUID. Use esta **ID do Aplicativo** como a **clientId** do aplicativo.

        ![clientId](media/embed-sample-for-customers/embed-sample-for-customers-007.png)     

    * Preencha as informações de **groupId** com o **GUID de espaço de trabalho do aplicativo** do Power BI.

        ![groupId](media/embed-sample-for-customers/embed-sample-for-customers-031.png)

    * Preencha as informações de **reportId** com o **GUID de relatório** do Power BI.

        ![reportId](media/embed-sample-for-customers/embed-sample-for-customers-032.png)    

    * Preencha o **pbiUsername** com o usuário mestre da conta do Power BI.
    * Preencha o **pbiPassword** com a senha do usuário mestre da conta do Power BI.

3. Execute o aplicativo!

    Primeiro, selecione **Executar** no **Visual Studio**.

    ![Execute o aplicativo](media/embed-sample-for-customers/embed-sample-for-customers-033.png)

    Selecione **Inserir Relatório**. Dependendo do conteúdo que você optar por testar – relatórios, painéis ou blocos –, selecione essa opção no aplicativo.

    ![Selecione um conteúdo](media/embed-sample-for-customers/embed-sample-for-customers-034.png)
 
    Agora, você pode exibir o relatório no aplicativo de exemplo.

    ![Exibir o aplicativo](media/embed-sample-for-customers/embed-sample-for-customers-035.png)

## <a name="move-to-production"></a>Mover para a produção

Agora que você terminou o desenvolvimento do seu aplicativo, é hora de conferir uma capacidade dedicada ao espaço de trabalho do seu aplicativo. É necessário ter capacidade dedicada para passar para a produção.

### <a name="create-a-dedicated-capacity"></a>Criar uma capacidade dedicada
Ao criando uma capacidade dedicada, é possível tirar proveito de um recurso dedicado para o seu cliente. Os espaços de trabalho que não receberam uma capacidade dedicada terão uma capacidade compartilhada. Crie uma capacidade dedicada usando a solução [Capacidade dedicada do Power BI Embedded](https://docs.microsoft.com/azure/power-bi-embedded/create-capacity) no Azure.

>[!Note]
>Os tokens inseridos com licença PRO destinam-se para teste de desenvolvimento, portanto, o número de tokens inseridos que uma conta mestre do Power BI pode gerar é limitado. Você deve adquirir uma capacidade dedicada para incorporar em um ambiente de produção. Não há limite para a quantidade de tokens inseridos que você pode gerar com uma capacidade dedicada. Acesse [Obter Recursos Disponíveis](https://msdn.microsoft.com/library/mt846473.aspx) para verificar o valor de uso que indica o uso atual inserido em percentual.
>

### <a name="assign-app-workspace-to-dedicated-capacity"></a>Atribuir um espaço de trabalho de aplicativo a uma capacidade dedicada

Ao criar uma capacidade dedicada, atribua o espaço de trabalho do aplicativo à capacidade dedicada. Para concluir isso, execute estas etapas.

1. Dentro do **serviço do Power BI**, expanda os espaços de trabalho e selecione as reticências do espaço de trabalho ao qual você está inserindo seu conteúdo. Depois, selecione **Editar espaços de trabalho**.

    ![Editar Espaço de Trabalho](media/embed-sample-for-customers/embed-sample-for-customers-036.png)

2. Expanda **Avançado**, habilite **Capacidade dedicada** e selecione a capacidade dedicada criada por você. Depois, selecione **Salvar**.

    ![Atribuir capacidade dedicada](media/embed-sample-for-customers/embed-sample-for-customers-024.png)

Para obter um exemplo completo de como usar a API JavaScript, use a [ferramenta de Playground](https://microsoft.github.io/PowerBI-JavaScript/demo). Trata-se de uma maneira rápida de experimentar diferentes tipos de exemplos do Power BI Embedded. Você também pode obter mais informações sobre a API de JavaScript, visitando a página da [wiki PowerBI-JavaScript](https://github.com/Microsoft/powerbi-javascript/wiki).

Para ver as respostas a perguntas sobre o Power BI Embedded, visite a página de [Perguntas frequentes](embedded-faq.md).  Se estiver tendo problemas com o Power BI Embedded dentro de seu aplicativo, visite a página de [solução de problemas](embedded-troubleshoot.md).

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](http://community.powerbi.com/)