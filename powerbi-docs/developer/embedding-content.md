---
title: Como inserir seus dashboards, relatórios e blocos do Power BI
description: Saiba mais sobre as etapas necessárias para inserir o conteúdo do Power BI em seu aplicativo.
services: powerbi
documentationcenter: ''
author: markingmyname
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
ms.date: 03/12/2018
ms.author: maghan
ms.openlocfilehash: 2caf5adc442a5794a23e3ed5af478f5467068b14
ms.sourcegitcommit: 3f2f254f6e8d18137bae879ddea0784e56b66895
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="embed-your-power-bi-dashboards-reports-and-tiles"></a>Inserir os dashboards, relatórios e blocos do Power BI

Saiba mais sobre as etapas necessárias para inserir o conteúdo do Power BI em seu aplicativo.

A Microsoft [anunciou o Power BI Premium](https://powerbi.microsoft.com/blog/microsoft-accelerates-modern-bi-adoption-with-power-bi-premium/), um novo modelo de licenciamento com base em capacidade que aumenta a flexibilidade de como os usuários acessam, compartilham e distribuem conteúdo. A oferta também oferece desempenho e escalabilidade adicional para o serviço do Power BI. Também foi anunciado o Power BI Embedded, que permite a criação de capacidade dentro do Microsoft Azure. O Power BI Embedded é focado no aplicativo e nos clientes. 

Este artigo examinará a inserção do conteúdo do Power BI tanto para a organização quanto para os clientes. As etapas são similares entre os dois cenários. Serão exibidos textos explicativos quando uma etapa for específica à inserção para o cliente.

Há algumas etapas que você precisa realizar com seu aplicativo para tornar isso possível. Vamos percorrer as etapas necessárias para permitir que você crie e use o conteúdo inserido em de seu aplicativo.

> [!NOTE]
> As APIs do Power BI ainda se referem aos espaços de trabalho do aplicativo como grupos. As referências a grupos significam que você está trabalhando com espaços de trabalho do aplicativo.

## <a name="step-1-setup-your-embedded-analytics-development-environment"></a>Etapa 1: configurar seu ambiente de desenvolvimento de análise inserido

Antes de começar a inserir dashboards e relatórios em seu aplicativo, é necessário certificar-se de que seu ambiente está configurado para permitir a inserção. Como parte da instalação, será necessário fazer o seguinte.

* [Verifique se você tem um locatário do Azure Active Directory](embedding-content.md#azureadtenant)
* [Criar sua conta do Power BI Pro](embedding-content.md#proaccount)
* [Registrar seu aplicativo e permissões do Azure Active Directory](embedding-content.md#appreg)

> [!NOTE]
> A capacidade do Power BI não é necessária para o desenvolvimento do aplicativo. Os desenvolvedores do aplicativo precisarão ter uma licença Power BI Pro.

### <a name="azureadtenant"></a>Locatário do Azure Active Directory

Será necessário um locatário do Azure Active Directory (Azure AD) para inserir os itens para Power BI. Esse locatário deve ter pelo menos um usuário Power BI Pro. Também será necessário definir um aplicativo do Azure AD dentro do locatário. É possível usar um locatário do Azure AD existente ou criar um novo especificamente para fins de inserção.

Você precisará determinar qual configuração de locatário usar se você estiver inserindo para os clientes.

* Usar seu locatário corporativo existente do Power BI?
* Usar um locatário separado para o seu aplicativo?
* Usar um locatário separado para cada cliente?

Se você não desejar usar um locatário existente, poderá optar por criar um novo locatário para o aplicativo ou um para cada cliente. Consulte [Criar um locatário do Azure Active Directory](create-an-azure-active-directory-tenant.md) ou [Como obter um locatário do Azure Active Directory](https://docs.microsoft.com/azure/active-directory/develop/active-directory-howto-tenant).

### <a name="proaccount"></a>Criar uma conta de usuário do Power BI Pro

Só é necessário ter uma única conta do Power BI Pro para inserir conteúdo. No entanto, convém ter alguns usuários diferentes que têm acesso específico a itens. Veja usuários possíveis a serem considerados em seu locatário.

As contas a seguir precisarão existir dentro do seu locatário e ter uma licença Power BI Pro atribuída a elas. É necessária uma licença do Power BI Pro para trabalhar com espaços de trabalho de aplicativo no Power BI.

#### <a name="an-organizationtenant-admin-user"></a>Um usuário administrador de locatário/organização

É recomendável que o usuário Administrador Global do locatário/organização não seja usado como a conta que seu aplicativo usa ao inserir para os clientes. Isso é para minimizar o acesso que a conta de aplicativo tem dentro do locatário. É recomendável que o usuário administrador seja um administrador de todos os espaços de trabalho de aplicativo criados com a finalidade de inserção.

#### <a name="accounts-for-analysts-that-will-create-content"></a>Contas para analistas que criarão conteúdo

Você pode ter vários usuários que criam conteúdo para o Power BI. Será necessária uma conta do Power BI Pro para cada analista que está criando e implantando conteúdo no Power BI.

#### <a name="an-application-master-user-account-for-embedding-for-your-customers"></a>Uma conta de usuário *mestre* de aplicativo para inserir para os clientes

A conta mestre é a conta usada pelo aplicativo ao inserir conteúdo para os clientes. O cenário normalmente é para os aplicativos ISV. A conta mestre é realmente a única conta necessária em sua organização. Ela também pode ser usada como a conta de administrador e de analista, mas isso não é recomendável. O back-end dos seus aplicativos armazenará as credenciais dessa conta e a usará para adquirir um token de autenticação do Azure AD para usar com as APIs do Power BI. Essa conta será usada para gerar um token de inserção para o aplicativo usar para os clientes.

A conta mestre é apenas um usuário normal com uma licença do Power BI Pro que você usa com o aplicativo. A conta deverá ser administrador do espaço de trabalho do aplicativo que está sendo usado para inserção.

### <a name="appreg"></a> Registro e permissões do aplicativo

Você precisará registrar seu aplicativo no Azure AD para fazer chamadas à API REST. Para obter mais informações, consulte [Registrar um aplicativo do Azure AD para inserir o conteúdo do Power BI](register-app.md).

### <a name="create-app-workspaces"></a>Criar espaços de trabalho do aplicativo

Se você estiver inserindo dashboards e relatórios para os clientes, esses dashboards e relatórios precisarão ser colocados em um espaço de trabalho do aplicativo. A conta *mestre* mencionada acima precisa ser um administrador do espaço de trabalho do aplicativo.

[!INCLUDE [powerbi-service-create-app-workspace](../includes/powerbi-service-create-app-workspace.md)]

> [!NOTE]
> Um usuário não administrador só pode criar até 250 espaços de trabalho do aplicativo. Para criar mais espaços de trabalho do aplicativo, você precisa usar uma conta do administrador de locatário.
>

### <a name="create-and-upload-your-reports"></a>Criar e carregar seus relatórios

É possível criar seus relatórios e conjuntos de dados usando o Power BI Desktop e, em seguida, publicar esses relatórios em um espaço de trabalho do aplicativo. O usuário final que publicar os relatórios precisará ter uma licença Power BI Pro para publicar em um espaço de trabalho do aplicativo.

## <a name="step-2-embed-your-content"></a>Etapa 2: inserir seu conteúdo

Dentro de seu aplicativo, será necessário autenticar com o Power BI. Se você estiver inserindo conteúdo para os clientes, você armazenará as credenciais da conta *mestre* dentro de seu aplicativo. Para obter mais informações, consulte [Autenticar usuários e obter um token de acesso do Azure AD para o aplicativo do Power BI](get-azuread-access-token.md).

Depois de ser autenticar, no aplicativo, use as APIs JavaScript e as APIs REST do Power BI para inserir dashboards e relatórios no aplicativo. 

Para **inserir para a organização**, consulte os seguintes guias passo a passo:

* [Integrar um painel em um aplicativo](integrate-dashboard.md)
* [Integrar um bloco em um aplicativo](integrate-tile.md)
* [Integrar um relatório em um aplicativo](integrate-report.md)

Para **inserir para os clientes**, o que é típico para ISVs, consulte o seguinte:

* [Integrar um dashboard, bloco ou relatório no aplicativo](embed-sample-for-customers.md)

Ao inserir para os clientes, é necessário um token de inserção. Para saber mais, consulte [GenerateToken](https://msdn.microsoft.com/library/mt784614.aspx).

## <a name="step-3-promote-your-solution-to-production"></a>Etapa 3: promover sua solução para produção

Passar para a produção requer algumas etapas adicionais.

### <a name="embedding-for-your-organization"></a>Inserção para a organização

Se você estiver inserindo para a organização, só será necessário explicar para as pessoas como acessar o seu aplicativo. 

Os usuários Gratuitos poderão consumir o conteúdo inserido de um espaço de trabalho de aplicativo (grupo) se esse espaço de trabalho tiver o suporte de uma capacidade. Liste o usuário Gratuito como um membro do grupo (espaço de trabalho de aplicativo); caso contrário, você receberá um erro não autorizado 401. A tabela a seguir lista os SKUs do Power BI Premium disponíveis no Office 365.

| Nó de capacidade | Total de núcleos<br/>*(Back-end + front-end)* | Núcleos de back-end | Núcleos de front-end | Limites de conexão dinâmica/DirectQuery | Máx. de renderizações de página no horário de pico |
| --- | --- | --- | --- | --- | --- |
| EM3 |4 núcleos virtuais |2 núcleos, 10 GB de RAM |2 núcleos | |601-1.200 |
| P1 |8 v-cores |4 núcleos, 25 GB de RAM |4 núcleos |30 por segundo |1.201-2.400 |
| P2 |16 v-cores |8 núcleos, 50 GB de RAM |8 núcleos |60 por segundo |2.401-4.800 |
| P3 |32 v-cores |16 núcleos, 100 GB de RAM |16 núcleos |120 por segundo |4.801-9.600 |

> [!NOTE]
> É necessário ser um Administrador global ou de cobrança, dentro do seu locatário, para adquirir o Power BI Premium. Para obter informações sobre como adquirir o Power BI Premium, consulte [How to purchase Power BI Premium (Como comprar o Power BI Premium)](../service-admin-premium-purchase.md).

### <a name="embedding-for-your-customers"></a>Inserção para os clientes

Se você estiver integrando para os clientes, faça o seguinte.

* Se você estiver usando um locatário separado para desenvolvimento, então será preciso verificar se os espaços de trabalho do aplicativo, juntamente com os dashboards e os relatórios, estão disponíveis no ambiente de produção. Verifique se você criou o aplicativo no Azure AD para seu locatário de produção e atribuiu as permissões de aplicativo adequadas conforme indicado na Etapa 1.
* Adquira uma capacidade que atenda às suas necessidades. É possível usar a tabela abaixo para entender de qual SKU de capacidade do Power BI Embedded você pode precisar. Para obter mais detalhes, consulte [Embedded analytics capacity planning whitepaper (White paper de planejamento de capacidade de análise inserida)](https://aka.ms/pbiewhitepaper). Quando você estiver pronto para a compra, será possível fazê-la dentro do [Portal do Microsoft Azure](https://portal.azure.com). Para obter detalhes sobre como criar a capacidade do Power BI Embedded, consulte [Criar capacidade do Power BI Embedded no Portal do Azure](https://docs.microsoft.com/azure/power-bi-embedded/create-capacity).

> [!IMPORTANT]
> Como os tokens inseridos destinam-se apenas para teste de desenvolvimento, o número de tokens inseridos que uma conta mestre do Power BI pode gerar é limitado. Uma [capacidade deve ser adquirida](https://docs.microsoft.com/power-bi/developer/embedded-faq#technical) para cenários de integração de produção. Não há nenhum limite para a geração de tokens inseridos quando uma capacidade é adquirida. Acesse [Obter recursos disponíveis](https://msdn.microsoft.com/en-us/library/mt846473.aspx) para verificar quantos tokens gratuitos inseridos foram usados.

| Nó de capacidade | Total de núcleos<br/>*(Back-end + front-end)* | Núcleos de back-end | Núcleos de front-end | Limites de conexão dinâmica/DirectQuery | Máx. de renderizações de página no horário de pico |
| --- | --- | --- | --- | --- | --- |
| A1 |1 v-cores |0,5 núcleo, 3 GB de RAM |0,5 núcleo | 5 por segundo |1-300 |
| A2 |2 núcleos virtuais |1 núcleo, 5 GB de RAM |1 núcleo | 10 por segundo |301-600 |
| A3 |4 núcleos virtuais |2 núcleos, 10 GB de RAM |2 núcleos | 15 por segundo |601-1.200 |
| A4 |8 v-cores |4 núcleos, 25 GB de RAM |4 núcleos |30 por segundo |1.201-2.400 |
| A5 |16 v-cores |8 núcleos, 50 GB de RAM |8 núcleos |60 por segundo |2.401-4.800 |
| A6 |32 v-cores |16 núcleos, 100 GB de RAM |16 núcleos |120 por segundo |4.801-9.600 |

* Edite o espaço de trabalho do aplicativo e atribua-o a uma capacidade em avançado.

    ![Atribuir um espaço de trabalho de aplicativo a uma capacidade](media/embedding-content/powerbi-embedded-premium-capacity.png)

* Implante seu aplicativo atualizado para a produção e comece a inserir relatórios e dashboards do Power BI.



## <a name="admin-settings"></a>Configurações de administração

Os Administradores Globais ou administradores do serviço do Power BI, podem ativar ou desativar a capacidade de usar as APIs REST para um locatário. Administradores do Power BI podem definir essa configuração para toda a organização ou para grupos de segurança individuais. Isso é habilitado para toda a organização por padrão. Isso é feito por meio do [portal de administração do Power BI](../service-admin-portal.md).

## <a name="next-steps"></a>Próximas etapas

[Inserindo com o Power BI](embedding.md)  
[Como migrar o conteúdo da coleção do espaço de trabalho do Power BI Embedded para o Power BI](migrate-from-powerbi-embedded.md)  
[Power BI Premium – o que é?](../service-premium.md)  
[Como comprar o Power BI Premium](../service-admin-premium-purchase.md)  
[Repositório Git de API do JavaScript](https://github.com/Microsoft/PowerBI-JavaScript)  
[Repositório Git de C# do Power BI](https://github.com/Microsoft/PowerBI-CSharp)  
[Exemplo inserido do JavaScript](https://microsoft.github.io/PowerBI-JavaScript/demo/)  
[White paper de planejamento de capacidade de análise inserida](https://aka.ms/pbiewhitepaper)  
[White paper do Power BI Premium](https://aka.ms/pbipremiumwhitepaper)  

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](http://community.powerbi.com/)

