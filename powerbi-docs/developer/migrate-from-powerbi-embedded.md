---
title: Como migrar conteúdo da Coleção de Espaços de Trabalho do Power BI para o Power BI
description: Saiba como migrar da Coleção de Espaços de Trabalho do Power BI para o Power BI Embedded e aproveitar os avanços para inserir em aplicativos.
author: markingmyname
manager: kfile
ms.reviewer: ''
ms.Embedded: powerbi
ms.topic: conceptual
ms.date: 05/25/2018
ms.author: maghan
ms.openlocfilehash: 67b52fa94ee3af9da3bfcae17f69a72e1aa46c77
ms.sourcegitcommit: 80d6b45eb84243e801b60b9038b9bff77c30d5c8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34689773"
---
# <a name="how-to-migrate-power-bi-workspace-collection-content-to-power-bi-embedded"></a>Como migrar conteúdo da Coleção de Espaços de Trabalho do Power BI para o Power BI Embedded
Saiba como migrar da Coleção de Espaços de Trabalho do Power BI para o Power BI Embedded e aproveite os avanços para inserir em aplicativos.

A Microsoft recentemente [anunciou o Power BI Embedded](https://powerbi.microsoft.com/en-us/blog/power-bi-embedded-capacity-based-skus-coming-to-azure/), um novo modelo de licenciamento com base em capacidade que aumenta a flexibilidade de como os usuários acessam, compartilham e distribuem conteúdo. A oferta também oferece desempenho e escalabilidade adicionais.

Com o Power BI Embedded, você terá uma superfície de API, um conjunto consistente de recursos e o acesso aos recursos mais recentes do Power BI, tais como dashboards, gateways e espaços de trabalho de aplicativo, ao inserir seu conteúdo. A seguir, você poderá começar a usar o Power BI Desktop e seguir para a implantação com o Power BI Embedded.

A Coleção de Espaços de Trabalho do Power BI atual continuará disponível por um período limitado. Os clientes com um Contrato Enterprise terão acesso por meio da expiração de seus contratos existentes; os clientes que adquiriram a Coleção de Espaços de Trabalho do Power BI por meio de canais Direct ou CSP manterão o acesso por um ano após a versão de disponibilidade geral do Power BI Embedded.  Este artigo fornecerá algumas diretrizes para a migração da Coleção de Espaços de Trabalho do Power BI para a nova experiência do Power BI Embedded e também o preparará a respeito do que esperar em relação às alterações em seu aplicativo.

> [!IMPORTANT]
> Embora a migração receba uma dependência do Power BI Embedded, não há uma dependência no Power BI para os usuários do seu aplicativo ao usarem um **token de inserção**. Eles não precisa inscrever-se no Power BI para exibir o conteúdo inserido em seu aplicativo. É possível usar essa abordagem de inserção para inserir usuários que não são do Power BI.
> 

![](media/migrate-from-powerbi-embedded/powerbi-embed-flow.png)

Antes de começar a migração para o novo Power BI Embedded, é possível seguir rapidamente um passo a passo que ajuda a configurar o novo ambiente do Power BI Embedded usando a [Ferramenta de experiência de integração](https://aka.ms/embedsetup).

Escolha a solução certa para você:
* **Inserir para clientes**: quando você estiver interessado em uma solução [app owns data](https://aka.ms/embedsetup/AppOwnsData). A [inserção para clientes](embedding.md#embedding-for-your-customers) fornece a capacidade de inserir os dashboards e relatórios para usuários que não têm uma conta do Power BI. 
* **Inserir para a organização**: quando você estiver interessado em uma solução [user owns data](https://aka.ms/embedsetup/UserOwnsData). A [inserção para a organização](embedding.md#embedding-for-your-organization) permite que você estenda o serviço do Power BI.

## <a name="prepare-for-the-migration"></a>Preparar para a migração
Há algumas coisas que você precisa fazer para se preparar para migrar da Coleção de Espaços de Trabalho do Power BI para o Power BI Embedded. Você precisará de um locatário disponível, junto com um usuário que tenha uma licença do Power BI Pro.

1. Verifique se que você tem acesso a um locatário do Azure Active Directory (Azure AD).
   
    Você precisa determinar qual configuração de locatário usar.
   
   * Usar seu locatário corporativo existente do Power BI?
   * Usar um locatário separado para o seu aplicativo?
   * Usar um locatário separado para cada cliente?
     
     Se você decidir criar um novo locatário para seu aplicativo ou para cada cliente, consulte [Create an Azure Active Directory tenant (Criar um locatário do Azure Active Directory)](create-an-azure-active-directory-tenant.md) ou [Como obter um locatário do Azure Active Directory](https://docs.microsoft.com/azure/active-directory/develop/active-directory-howto-tenant).
2. Crie um usuário nesse novo locatário que funcionará como sua conta mestre do aplicativo. Essa conta precisa se inscrever no Power BI e ter uma licença Power BI Pro atribuída a ela.

## <a name="accounts-within-azure-ad"></a>Contas no Azure AD
As seguintes contas precisarão existir no seu locatário.

> [!NOTE]
> Essas contas precisarão ter as licenças Power BI Pro para usar os espaços de trabalho do aplicativo.
>

1. Um usuário administrador de locatário.
   
    É recomendável que esse usuário seja um membro de todos os Espaços de trabalho de aplicativo criados com a finalidade de inserção.
2. Contas para analistas que criarão conteúdo.
   
    Esses usuários devem ser atribuídos aos Espaços de trabalho de aplicativo, conforme necessário.
3. Uma conta de usuário *mestre* de aplicativo ou uma conta do Embedded.
   
    O back-end de aplicativos armazenará as credenciais dessa conta e a usará para adquirir um token do Azure AD para utilizar com as APIs REST do Power BI. Essa conta será usada para gerar o token de inserção para o aplicativo. Essa conta também precisa ser administrador dos Espaços de trabalho do aplicativo criados para a inserção.
   
> [!NOTE]
> Essa é apenas uma conta de usuário regular na sua organização que será usada para fins de inserção.
>

## <a name="app-registration-and-permissions"></a>Registro do aplicativo e permissões
Você precisará registrar um aplicativo no Azure AD e conceder permissões específicas.

### <a name="register-an-application"></a>Registrar um aplicativo
Você precisará registrar seu aplicativo no Azure AD para fazer chamadas à API REST. Isso inclui o acesso do portal do Azure para aplicar a configuração adicional, além do acesso da página de registro de aplicativo do Power BI. Para obter mais informações, consulte [Registrar um aplicativo do Azure AD para inserir o conteúdo do Power BI](register-app.md).

Você deve registrar o aplicativo usando a conta **mestre** do aplicativo.

## <a name="create-app-workspaces-required"></a>Criar Espaços de trabalho de aplicativo (necessário)
Você pode aproveitar os Espaços de trabalho de aplicativo para fornecer melhor isolamento, caso seu aplicativo esteja atendendo a vários clientes. Os dashboards e relatórios ficariam isolados entre seus clientes. Você poderia usar uma conta do Power BI por Espaço de trabalho de aplicativo para isolar ainda mais as experiências de aplicativos entre seus clientes.

> [!IMPORTANT]
> Não é possível usar um espaço de trabalho pessoal para tirar proveito da inserção para usuários que não são do Power BI.
> 
> 

Será necessário um usuário que tenha uma licença Pro para criar um Espaço de trabalho do aplicativo no Power BI. O usuário do Power BI que criar o Espaço de trabalho de aplicativo será um administrador desse espaço de trabalho por padrão.

> [!NOTE]
> A conta *mestre* do aplicativo precisa ser um administrador do espaço de trabalho.
> 
> 

## <a name="content-migration"></a>Migração de conteúdo
A migração do conteúdo de suas coleções de espaços de trabalho para o Power BI Embedded pode ser feita paralelamente à sua solução atual e não requer nenhum tempo de inatividade.

Há uma **ferramenta de migração** disponível para ajudá-lo a copiar o conteúdo da Coleção de Espaços de Trabalho do Power BI para o Power BI Embedded. Principalmente se você tiver muito conteúdo. Para obter mais informações, consulte [Power BI Embedded migration tool (Ferramenta de migração do Power BI Embedded)](migrate-tool.md).

A migração de conteúdo depende principalmente de duas APIs.

1. Baixar PBIX – esta API pode baixar arquivos PBIX que foram carregados no Power BI depois de outubro de 2016.
2. Importar PBIX – esta API carrega qualquer PBIX no Power BI.

Para alguns trechos de código relacionados, consulte [Trechos de código para migrar conteúdo da Coleção de Espaços de Trabalho do Power BI](migrate-code-snippets.md).

### <a name="report-types"></a>Tipos de relatório
Há vários tipos de relatórios, cada um requerendo um fluxo de migração um pouco diferente.

#### <a name="cached-dataset--report"></a>Relatório e conjunto de dados armazenados em cache
Conjuntos de dados armazenados em cache referem-se a arquivos PBIX que tinham importado dados em vez de uma conexão dinâmica ou uma conexão do DirectQuery.

**Fluxo**

1. Chame Baixar API de PBIX no espaço de trabalho PaaS.
2. Salve o PBIX.
3. Chame Importar PBIX para o espaço de trabalho SaaS.

#### <a name="directquery-dataset--report"></a>Relatório e conjunto de dados do DirectQuery
**Fluxo**

1. Chame GET https://api.powerbi.com/v1.0/collections/{collection_id}/workspaces/{wid}/datasets/{dataset_id}/Default.GetBoundGatewayDataSources e salve a cadeia de conexão recebida.
2. Chame Baixar API de PBIX no espaço de trabalho PaaS.
3. Salve o PBIX.
4. Chame Importar PBIX para o espaço de trabalho SaaS.
5. Atualizar a cadeia de conexão chamando - POST  https://api.powerbi.com/v1.0/myorg/datasets/{dataset_id}/Default.SetAllConnections
6. Obter id de GW e id de fonte de dados chamando - GET https://api.powerbi.com/v1.0/myorg/datasets/{dataset_id}/Default.GetBoundGatewayDataSources
7. Atualizar credenciais do usuário chamando - PATCH https://api.powerbi.com/v1.0/myorg/gateways/{gateway_id}/datasources/{datasource_id}

#### <a name="old-dataset--reports"></a>Relatórios e conjunto de dados antigos
Esses são os conjuntos de dados/relatórios criados antes de outubro de 2016. Baixar PBIX não dá suporte a PBIXs carregados antes de outubro de 2016

**Fluxo**

1. Obtenha o PBIX do seu ambiente de desenvolvimento (seu controle do código-fonte interno).
2. Chame Importar PBIX para o espaço de trabalho SaaS.

#### <a name="push-dataset--report"></a>Enviar relatório e conjunto de dados por push
Baixar PBIX não dá suporte a conjuntos de dados *API Push*. O conjunto de dados de API por push não podem ser portados do PaaS para o SaaS.

**Fluxo**

1. Chame a API “Criar conjunto de dados” com o Json do conjunto de dados para criar conjunto de dados no espaço de trabalho do SaaS.
2. Recrie o relatório para o conjunto de dados criado *.

Ao usar algumas soluções alternativas, é possível tentar migrar o relatório de API por push de PaaS para SaaS fazendo o seguinte.

1. Carregando o PBIX fictício para o espaço de trabalho do PaaS.
2. Clone o relatório de api por push e associe-o ao PBIX fictício da etapa 1.
3. Baixe o relatório de API por push com o PBIX fictício.
4. Carregue o PBIX fictício para seu espaço de trabalho do SaaS.
5. Crie um conjunto de dados por push em seu espaço de trabalho do SaaS.
6. Associe novamente o relatório ao conjunto de dados de api por push.

## <a name="create-and-upload-new-reports"></a>Criar e carregar novos relatórios
Além do conteúdo que você migrou da Coleção de Espaços de Trabalho do Power BI, é possível criar relatórios e conjuntos de dados usando o Power BI Desktop e, em seguida, publicar esses relatórios em um espaço de trabalho de aplicativo. O usuário final que publicar os relatórios precisará ter uma licença Power BI Pro para publicar em um espaço de trabalho do aplicativo.

## <a name="rebuild-your-application"></a>Recriar seu aplicativo
1. Você precisará modificar seu aplicativo para usar as APIs REST do Power BI e o local do relatório em powerbi.com.
2. Recrie sua autenticação AuthN/AuthZ usando a conta *mestre* do seu aplicativo. Você pode tirar proveito do uso de um [token de inserção](https://msdn.microsoft.com/library/mt784614.aspx) para permitir que esse usuário atue em nome de outros usuários.
3. Insira seus relatórios de powerbi.com em seu aplicativo.

## <a name="map-your-users-to-a-power-bi-user"></a>Mapear os usuários para um usuário do Power BI
No aplicativo, você mapeará os usuários que gerencia dentro do aplicativo para uma credencial *mestre* do Power BI para a finalidade do seu aplicativo. As credenciais desta conta *mestre* do Power BI serão armazenadas dentro do seu aplicativo e serão usadas para criar tokens de inserção.

## <a name="what-to-do-when-you-are-ready-for-production"></a>O que fazer quando você estiver pronto para a produção
Quando estiver pronto para passar para a produção, você precisará fazer o seguinte.

* Se você estiver usando um locatário separado para desenvolvimento, então será preciso certificar-se de que seus espaços de trabalho do aplicativo, juntamente com dashboards e relatórios, estão disponíveis em seu ambiente de produção. Também será preciso certificar-se de ter criado o aplicativo no Azure AD para seu locatário de produção e ter atribuído as permissões de aplicativo adequadas conforme indicado na Etapa 1.
* Adquira uma capacidade que atenda às suas necessidades. Para entender melhor a quantidade e o tipo de capacidade necessários, confira o [White paper de planejamento de capacidade de análise do Power BI Embedded](https://aka.ms/pbiewhitepaper). Você pode [adquirir capacidade](https://portal.azure.com/#create/Microsoft.PowerBIDedicated) no Azure.
* Edite o espaço de trabalho do aplicativo e atribua-o a uma capacidade Premium em avançado.
 
    ![](media/migrate-from-powerbi-embedded/powerbi-embedded-premium-capacity02.png)
    
* Implante seu aplicativo atualizado para a produção e comece a inserir relatórios do Power BI Embedded.

## <a name="after-migration"></a>Após a migração
Você deve fazer uma limpeza no Azure.

* Remova todos os espaços de trabalho da solução implantada no Azure Embedded da Coleção de Espaços de Trabalho do Power BI.
* Exclua todas as Coleções de Espaço de trabalho que existam no Azure.

## <a name="next-steps"></a>Próximas etapas
[Inserindo com o Power BI](embedding.md)  
[Ferramenta de migração da Coleção de Espaços de Trabalho do Power BI](migrate-tool.md)  
[Trechos de código para migrar conteúdo da Coleção de Espaços de Trabalho do Power BI](migrate-code-snippets.md)  
[Como inserir seus dashboards, relatórios e blocos do Power BI](embedding-content.md)  
[Power BI Premium – o que é?](../service-premium.md)  
[Repositório Git de API do JavaScript](https://github.com/Microsoft/PowerBI-JavaScript)  
[Repositório Git de C# do Power BI](https://github.com/Microsoft/PowerBI-CSharp)  
[Exemplo inserido do JavaScript](https://microsoft.github.io/PowerBI-JavaScript/demo/)  
[White paper de planejamento de capacidade de análise da Coleção de Espaços de Trabalho](https://aka.ms/pbiewhitepaper)  
[White paper do Power BI Premium](https://aka.ms/pbipremiumwhitepaper)  

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](http://community.powerbi.com/)