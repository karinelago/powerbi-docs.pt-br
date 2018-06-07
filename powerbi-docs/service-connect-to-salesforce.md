---
title: Conectar-se ao Salesforce com o Power BI
description: Salesforce para o Power BI
author: SarinaJoan
manager: kfile
ms.reviewer: maggiesMSFT
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 05/30/2018
ms.author: sarinas
LocalizationGroup: Connect to services
ms.openlocfilehash: e36cff803af74d212f4c1804fe3a955a11c193cf
ms.sourcegitcommit: 80d6b45eb84243e801b60b9038b9bff77c30d5c8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34722441"
---
# <a name="connect-to-salesforce-with-power-bi"></a>Conectar-se ao Salesforce com o Power BI
Com o Power BI, você pode se conectar facilmente à sua conta do Salesforce.com. A criação dessa conexão recupera os dados, além de fornecer automaticamente um painel e relatórios relacionados com base nesses dados.

Conecte-se ao [pacote de conteúdo do Salesforce](https://app.powerbi.com/getdata/services/salesforce) para o Power BI ou leia mais sobre a [integração do Salesforce](https://powerbi.microsoft.com/integrations/salesforce) com o Power BI.

## <a name="how-to-connect"></a>Como se Conectar
1. Selecione **Obter Dados** na parte inferior do painel de navegação esquerdo.
   
   ![](media/service-connect-to-salesforce/pbi_getdata.png) 
2. Na caixa **Serviços** , selecione **Obter**.
   
   ![](media/service-connect-to-salesforce/pbi_getservices.png) 
3. Clique em **Salesforce** e selecione **Obter**.  
   
   ![](media/service-connect-to-salesforce/salesforce.png)
4. Selecione **Entrar** para iniciar o fluxo de logon.
   
    ![](media/service-connect-to-salesforce/dialog.png)
5. Quando solicitado, insira suas credenciais do Salesforce. Clique em **Permitir** para que o Power BI possa acessar suas informações e dados básicos do Salesforce.
   
   ![](media/service-connect-to-salesforce/sf_authorize.png)
6. Configure o que você deseja importar para o Power BI usando a opção de lista suspensa:
   
   * **Dashboard**
     
     Selecione um painel predefinido com base em uma persona (como **Gerente de Vendas**). Esses painéis trazem um conjunto específico de dados padrão do Salesforce e não incluirão nenhum campo personalizado.
     
     ![](media/service-connect-to-salesforce/pbi_salesforcechooserole.png)
   * **Relatórios**
     
     Selecione um ou mais relatórios personalizados da conta do Salesforce. Esses relatórios corresponderão às visualizações no Salesforce, podendo incluir dados de objetos ou campos personalizados.
     
     ![](media/service-connect-to-salesforce/pbi_salesforcereports.png)
     
     Se você não vir quaisquer relatórios, adicione ou crie-os em sua conta do Salesforce e tente conectar-se novamente.
7. Clique em **Conectar** para iniciar o processo de importação. Durante a importação, você verá uma notificação mostrando que a importação está em andamento. Depois de concluída a importação, você verá um painel, relatório e conjunto de dados para os dados do Salesforce listados no painel de navegação esquerdo.
   
   ![](media/service-connect-to-salesforce/pbi_getdatasalesforcedash.png)

Você pode alterar esse painel para exibir os dados de qualquer modo que desejar. É possível fazer perguntas com a P e R ou clicar em um bloco para [abrir o relatório subjacente](service-dashboard-tiles.md) e [alterar os blocos](service-dashboard-edit-tile.md) no dashboard.

**E agora?**

* Tente [fazer uma pergunta na caixa de P e R](power-bi-q-and-a.md) na parte superior do dashboard
* [Alterar os blocos](service-dashboard-edit-tile.md) no dashboard
* [Selecionar um bloco](service-dashboard-tiles.md) para abrir o relatório subjacente
* Enquanto seu conjunto de dados será agendado para ser atualizado diariamente, você pode alterar o agendamento de atualização ou tentar atualizá-lo sob demanda usando **Atualizar Agora**

## <a name="system-requirements-and-considerations"></a>Considerações e requisitos do sistema
- Estar conectado a uma conta do Salesforce que tenha acesso habilitado à API
- Permissão ter sido concedida ao aplicativo Power BI durante o logon
- A conta ter chamadas à API suficientes disponíveis para efetuar pull dos dados e atualizá-los
- Um token de autenticação válido é necessário para a atualização. Certifique-se de ter importado no máximo cinco conjuntos de dados do Salesforce, já que o Salesforce tem um limite de cinco tokens de autenticação por aplicativo
- A API dos Relatórios do Salesforce tem uma restrição que dá suporte a até 2.000 linhas de dados.


## <a name="troubleshooting"></a>Solução de problemas
Se você encontrar algum erro, examine os requisitos acima. Observe também que a capacidade de logon em domínio personalizado de área restrita não é compatível no momento.

### <a name="unable-to-connect-to-the-remote-server-message"></a>Mensagem "Não é possível conectar ao servidor remoto"

Se você receber uma mensagem "Não é possível conectar ao servidor remoto" ao tentar se conectar à sua conta do Salesforce, confira esta solução no Fórum do Outsystems: [Salesforce Connector Log In Error Message: Unable to connect to the remote server](https://www.outsystems.com/forums/Forum_TopicView.aspx?TopicId=17674&TopicName=log-in-error-message-unable-to-connect-to-the-remote-server&) (Mensagem de erro ao fazer logon no Salesforce Connector: Não é possível conectar ao servidor remoto)


## <a name="next-steps"></a>Próximas etapas
[Introdução ao Power BI](service-get-started.md)

[Obter dados](service-get-data.md)

