---
title: "Como migrar o conteúdo da coleção do espaço de trabalho do Power BI Embedded para o Power BI"
description: "Saiba como migrar do Power BI Embedded para o serviço do Power BI e aproveitar os avanços para inserir em aplicativos."
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
ms.date: 08/24/2018
ms.author: maghan
ms.openlocfilehash: 59d395d11839903108f811ff4a6022ea04cadc8f
ms.sourcegitcommit: 6e693f9caf98385a2c45890cd0fbf2403f0dbb8a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2018
---
# <a name="how-to-migrate-power-bi-embedded-workspace-collection-content-to-power-bi"></a>Como migrar o conteúdo da coleção do espaço de trabalho do Power BI Embedded para o Power BI
Saiba como migrar do Power BI Embedded para o serviço do Power BI e aproveitar os avanços para inserir em aplicativos.

A Microsoft recentemente [anunciou Power BI Premium](https://powerbi.microsoft.com/blog/microsoft-accelerates-modern-bi-adoption-with-power-bi-premium/), um novo modelo de licenciamento com base em capacidade que aumenta a flexibilidade de como os usuários acessam, compartilham e distribuem conteúdo. A oferta também oferece desempenho e escalabilidade adicional para o serviço do Power BI.

Com a introdução do Power BI Premium, o Power BI Embedded e o serviço do Power BI estão convergindo para avançar na maneira como o conteúdo do Power BI é inserido em aplicativos. Isso significa que você terá uma superfície de API, um conjunto consistente de recursos e o acesso aos recursos mais recentes do Power BI, tais como dashboards, gateways e espaços de trabalho de aplicativo, ao inserir seu conteúdo. Mais adiante você poderá iniciar com o Power BI Desktop e mudar para a implantação com o Power BI Premium, que estará disponível no final do segundo trimestre de 2017.

O serviço atual do Power BI Embedded continuará disponível por um período limitado, após a disponibilidade geral da oferta convergida: os clientes com um Enterprise Agreement terão acesso até o final de seus contratos existentes; os clientes que adquiriram o Power BI Embedded por meio de canais Diretos ou CSP aproveitarão o acesso pelo período de um ano após a disponibilidade geral do Power BI Premium.  Este artigo fornecerá algumas diretrizes para a migração do serviço do Azure para o serviço do Power BI e o que esperar em relação às alterações em seu aplicativo.

> [!IMPORTANT]
> Enquanto que a migração receberá uma dependência do serviço do Power BI, não há uma dependência no Power BI para os usuários do seu aplicativo ao usarem um **token de inserção**. Eles não precisa inscrever-se no Power BI para exibir o conteúdo inserido em seu aplicativo. É possível usar essa abordagem de inserção para atender usuários que não são do Power BI.
> 
> 

![](media/migrate-from-powerbi-embedded/powerbi-embed-flow.png)

## <a name="prepare-for-the-migration"></a>Preparar para a migração
Há algumas coisas que você precisa fazer para se preparar para migrar do serviço do Azure do Power BI Embedded para o serviço do Power BI. Você precisará de um locatário disponível, junto com um usuário que tenha uma licença do Power BI Pro.

1. Verifique se que você tem acesso a um locatário do Azure Active Directory (Azure AD).
   
    Será necessário determinar qual configuração de locatário usar.
   
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
> 

1. Um usuário administrador de locatário.
   
    É recomendável que esse usuário seja um membro de todos os Espaços de trabalho de aplicativo criados com a finalidade de inserção.
2. Contas para analistas que criarão conteúdo.
   
    Esses usuários devem ser atribuídos aos Espaços de trabalho de aplicativo, conforme necessário.
3. Uma conta de usuário *mestre* de aplicativo ou conta de serviço.
   
    O back-end de aplicativos armazenará as credenciais dessa conta e a usará para adquirir um token do Azure AD para utilizar com as APIs REST do Power BI. Essa conta será usada para gerar o token de inserção para o aplicativo. Essa conta também precisa ser administrador dos Espaços de trabalho do aplicativo criados para a inserção.
   
   > [!NOTE]
   > Essa é apenas uma conta de usuário regular na sua organização que será usada para fins de inserção.
   > 
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
A migração do conteúdo de suas coleções de espaços de trabalho para o serviço do Power BI poderá ser feita paralelamente à sua solução atual e não requer nenhum tempo de inatividade.

Uma **ferramenta de migração** está disponível para uso a fim de ajudá-lo a copiar o conteúdo do Power BI Embedded para o serviço do Power BI. Principalmente se você tiver muito conteúdo. Para obter mais informações, consulte [Power BI Embedded migration tool (Ferramenta de migração do Power BI Embedded)](migrate-tool.md).

A migração de conteúdo depende principalmente de duas APIs.

1. Baixar PBIX – esta API pode baixar arquivos PBIX que foram carregados no Power BI depois de outubro de 2016.
2. Importar PBIX – esta API carrega qualquer PBIX no Power BI.

Para alguns trechos de código relacionados, consulte [Code snippets for migrating content from Power BI Embedded (Trechos de código para migrar conteúdo do Power BI Embedded)](migrate-code-snippets.md).

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

1. Chame GET https://api.powerbi.com/v1.0/collections/{collection_id}/workspaces/{wid}/datasets/{dataset_id}/Default.GetBoundGatewayDataSources e salve as cadeias de conexão recebidas.
2. Chame Baixar API de PBIX no espaço de trabalho PaaS.
3. Salve o PBIX.
4. Chame Importar PBIX para o espaço de trabalho SaaS.
5. Atualize a cadeia de conexão chamando – POST https://api.powerbi.com/v1.0/myorg/datasets/ {dataset_id}/Default.SetAllConnections
6. Obtenha a ID GW e a ID da fonte de dados chamando – GET https://api.powerbi.com/v1.0/myorg/datasets/{dataset_id}/Default.GetBoundGatewayDataSources
7. Atualize as credenciais do usuário chamando – PATCH https://api.powerbi.com/v1.0/myorg/gateways/{gateway_id}/datasources/{datasource_id}

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

É possível usar algumas soluções alternativas para migrar o relatório de api por push do PaaS para o SaaS fazendo o seguinte.

1. Carregando o PBIX fictício para o espaço de trabalho do PaaS.
2. Clone o relatório de api por push e associe-o ao PBIX fictício da etapa 1.
3. Baixe o relatório de API por push com o PBIX fictício.
4. Carregue o PBIX fictício para seu espaço de trabalho do SaaS.
5. Crie um conjunto de dados por push em seu espaço de trabalho do SaaS.
6. Associe novamente o relatório ao conjunto de dados de api por push.

## <a name="create-and-upload-new-reports"></a>Criar e carregar novos relatórios
Além do conteúdo que você migrou do serviço do Azure do Power BI Embedded, é possível criar seus relatórios e conjuntos de dados usando o Power BI Desktop e depois publicar esses relatórios em um espaço de trabalho do aplicativo. O usuário final que publicar os relatórios precisará ter uma licença Power BI Pro para publicar em um espaço de trabalho do aplicativo.

## <a name="rebuild-your-application"></a>Recriar seu aplicativo
1. Você precisará modificar seu aplicativo para usar as APIs REST do Power BI e o local do relatório em powerbi.com.
2. Recrie sua autenticação AuthN/AuthZ usando a conta *mestre* do seu aplicativo. Você pode tirar proveito do uso de um [token de inserção](https://msdn.microsoft.com/library/mt784614.aspx) para permitir que esse usuário atue em nome de outros usuários.
3. Insira seus relatórios de powerbi.com em seu aplicativo.

## <a name="map-your-users-to-a-power-bi-user"></a>Mapear os usuários para um usuário do Power BI
No aplicativo, você mapeará os usuários que gerencia dentro do aplicativo para uma credencial *mestre* do Power BI para a finalidade do seu aplicativo. As credenciais desta conta *mestre* do Power BI serão armazenadas dentro do seu aplicativo e serão usadas para criar tokens de inserção.

## <a name="what-to-do-when-you-are-ready-for-production"></a>O que fazer quando você estiver pronto para a produção
Quando estiver pronto para passar para a produção, você precisará fazer o seguinte.

* Se você estiver usando um locatário separado para desenvolvimento, então será preciso certificar-se de que seus espaços de trabalho do aplicativo, juntamente com dashboards e relatórios, estão disponíveis em seu ambiente de produção. Também será preciso certificar-se de ter criado o aplicativo no Azure AD para seu locatário de produção e ter atribuído as permissões de aplicativo adequadas conforme indicado na Etapa 1.
* Adquira uma capacidade que atenda às suas necessidades. Para entender melhor a quantidade e o tipo de capacidade necessários, confira o [White paper de planejamento de capacidade de análise inserida](https://aka.ms/pbiewhitepaper). Você pode [adquirir capacidade](https://portal.azure.com/#create/Microsoft.PowerBIDedicated) no Azure.
* Edite o espaço de trabalho do aplicativo e atribua-o a uma capacidade Premium em avançado.
 
    ![](media/migrate-from-powerbi-embedded/powerbi-embedded-premium-capacity.png)
    
* Implante seu aplicativo atualizado para a produção e comece a inserir relatórios do serviço do Power BI.

## <a name="after-migration"></a>Após a migração
Você deve fazer uma limpeza no Azure.

* Remova todos os espaços de trabalho da solução implantada dentro do serviço do Azure do Power BI Embedded.
* Exclua todas as Coleções de Espaço de trabalho que existam no Azure.

## <a name="next-steps"></a>Próximas etapas
[Inserindo com o Power BI](embedding.md)  
[Ferramenta de migração do Power BI Embedded](migrate-tool.md)  
[Trechos de código para migrar conteúdo do Power BI Embedded](migrate-code-snippets.md)  
[Como inserir seus dashboards, relatórios e blocos do Power BI](embedding-content.md)  
[Power BI Premium – o que é?](../service-premium.md)  
[Repositório Git de API do JavaScript](https://github.com/Microsoft/PowerBI-JavaScript)  
[Repositório Git de C# do Power BI](https://github.com/Microsoft/PowerBI-CSharp)  
[Exemplo inserido do JavaScript](https://microsoft.github.io/PowerBI-JavaScript/demo/)  
[White paper de planejamento de capacidade de análise inserida](https://aka.ms/pbiewhitepaper)  
[White paper do Power BI Premium](https://aka.ms/pbipremiumwhitepaper)  

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](http://community.powerbi.com/)

