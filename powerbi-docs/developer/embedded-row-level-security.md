---
title: "Usar segurança em nível de linha com conteúdo inserido do Power BI"
description: "Saiba mais sobre as etapas necessárias para inserir o conteúdo do Power BI em seu aplicativo."
services: powerbi
documentationcenter: 
author: guyinacube
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
ms.author: asaxton
ms.openlocfilehash: 1ab1590146f8b9714a27735cd556dd0203ecc6bf
ms.sourcegitcommit: b3ee37e1587f1269ee7dd9daf1685a06dea3b50c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2017
---
# <a name="use-row-level-security-with-power-bi-embedded-content"></a>Usar segurança em nível de linha com conteúdo inserido do Power BI
A RLS (segurança em nível de linha) pode ser usada para restringir o acesso do usuário aos dados em um relatório ou conjunto de dados, permitindo que vários usuários diferentes usem o mesmo relatório, enquanto todos veem dados diferentes. A RLS pode ser aproveitada durante a inserção de relatórios do Power BI.

Se você está fazendo uma inserção para usuários que não têm o Power BI (o aplicativo possui dados), o que normalmente é um cenário de ISV, este artigo é ideal para você! Você precisará configurar o token de inserção da conta para o usuário e a função. Continue lendo para saber como fazer isso.

Se você está fazendo uma inserção para usuários do Power BI (o usuário possui dados), em sua organização, a RLS funciona da mesma maneira que no serviço do Power BI diretamente. Não há nada mais a ser feito no aplicativo. Para obter mais informações, consulte [RLS (segurança em nível de linha) com o Power BI](../service-admin-rls.md).

![Itens envolvidos com a Segurança em Nível de Linha.](media/embedded-row-level-security/powerbi-embedded-rls-components.png)

Para aproveitar a RLS, é importante entender os três conceitos principais: Usuários, Funções e Regras. Vamos examinar cada um deles mais detalhadamente:

**Usuários** – esses são os usuários finais reais que exibem relatórios. No Power BI Embedded, os usuários são identificados pela propriedade de nome de usuário em um token de inserção.

**Funções** – os usuários pertencem a funções. Uma função é um contêiner de regras e pode ser nomeada como algo parecido com *Gerente de Vendas* ou *Representante de Vendas*. As funções são criadas no Power BI Desktop. Para obter mais informações, consulte [RLS (segurança em nível de linha) com o Power BI Desktop](../desktop-rls.md).

**Regras** – as funções têm regras e essas regras são os filtros reais que serão aplicados aos dados. Isso pode ser tão simples como “País = EUA” ou algo muito mais dinâmico.
No restante deste artigo, forneceremos um exemplo de como criar a RLS e, em seguida, como consumir isso em um aplicativo inserido. Nosso exemplo usa o arquivo PBIX da [Amostra de Análise de Varejo](http://go.microsoft.com/fwlink/?LinkID=780547).

![Exemplo de relatório](media/embedded-row-level-security/powerbi-embedded-report-example.png)

## <a name="adding-roles-with-power-bi-desktop"></a>Adicionando funções com o Power BI Desktop
Nossa amostra de Análise de Varejo mostra as vendas de todas as lojas de uma cadeia de varejo. Sem a RLS, não importa qual gerente regional se conecta e exibe o relatório: eles verão os mesmos dados. A gerência sênior determinou que cada gerente regional deve ver apenas as vendas das lojas que eles gerenciam e, para fazer isso, podemos usar a RLS.

A RLS é criada no Power BI Desktop. Quando o conjunto de dados e o relatório são abertos, é possível alternar para a exibição de diagrama para ver o esquema:

![Exibição de diagrama no Power BI Desktop](media/embedded-row-level-security/powerbi-embedded-schema.png)

A seguir, veja alguns itens a serem observados com esse esquema:

* Todas as medidas, como **Total de Vendas**, são armazenadas na tabela de fatos **Vendas**.
* Há mais quatro tabelas de dimensões relacionadas: **Item**, **Hora**, **Loja** e **Distrito**.
* As setas nas linhas de relacionamento indicam em que direção os filtros podem fluir de uma tabela para outra. Por exemplo, se um filtro for colocado em **Hora[Data]**, no esquema atual, ele apenas filtrará valores da tabela **Vendas**. Nenhuma outra tabela será afetada por esse filtro, pois todas as setas nas linhas de relacionamento apontam para a tabela de vendas e não para outra.
* A tabela **Distrito** indica quem é o gerente de cada distrito:
  
    ![Linhas na tabela Distrito](media/embedded-row-level-security/powerbi-embedded-district-table.png)

Com base nesse esquema, se aplicarmos um filtro à coluna **Gerente Regional** da tabela **Distrito** e se o filtro corresponder ao usuário que exibe o relatório, esse filtro também filtrará as tabelas **Loja** e **Vendas** para apenas mostrar dados desse gerente regional.

Aqui está como:

1. Na guia **Modelagem**, selecione **Gerenciar Funções**.
   
    ![Guia Modelagem no Power BI Desktop](media/embedded-row-level-security/powerbi-embedded-manage-roles.png)
2. Crie uma nova função chamada **Gerente**.
   
    ![Criar nova função](media/embedded-row-level-security/powerbi-embedded-new-role.png)
3. Na tabela **Distrito**, insira a seguinte expressão DAX: **[Gerente Regional] = USERNAME()**.
   
    ![Instrução DAX para a regra de RLS](media/embedded-row-level-security/powerbi-embedded-new-role-dax.png)
4. Para verificar se as regras estão funcionando, na guia **Modelagem**, selecione **Exibir como Funções** e, depois, selecione a função **Gerente** que você acabou de criar, juntamente com **Outro usuário**. Insira **Alberto Ge** como o usuário.
   
    ![Exibir como uma caixa de diálogo de função](media/embedded-row-level-security/powerbi-embedded-new-role-view.png)
   
    Os relatórios agora mostrarão dados como se você tivesse entrado como **Alberto Ge**.

A aplicação do filtro, da maneira como fizemos aqui, filtrará todos os registros nas tabelas **Distrito**, **Loja** e **Vendas**. No entanto, devido à direção do filtro nos relacionamentos entre **Vendas** e **Hora**, as tabelas **Vendas** e **Item** e **Item** e **Hora** não serão filtradas. Para saber mais sobre a filtragem cruzada bidirecional, baixe o white paper [Filtragem cruzada bidirecional no SQL Server Analysis Services 2016 e no Power BI Desktop](http://download.microsoft.com/download/2/7/8/2782DF95-3E0D-40CD-BFC8-749A2882E109/Bidirectional%20cross-filtering%20in%20Analysis%20Services%202016%20and%20Power%20BI.docx).

## <a name="applying-user-and-role-to-an-embed-token"></a>Aplicando o usuário e a função a um token de inserção
Agora que você tem as funções do Power BI Desktop configuradas, é necessário trabalhar um pouco no aplicativo para aproveitar as funções.

Os usuários são autenticados e autorizados pelo aplicativo e os tokens de inserção são usados para conceder o acesso de usuário a um relatório específico do Power BI Embedded. O Power BI Embedded não tem nenhuma informação específica sobre quem é o usuário. Para que a RLS funcione, você precisará passar algum contexto adicional como parte do token de inserção na forma de identidades. Isso é feito pela API [GenerateToken](https://msdn.microsoft.com/library/mt784614.aspx).

A API [GenerateToken](https://msdn.microsoft.com/library/mt784614.aspx) aceita uma lista de identidades com a indicação dos conjuntos de dados relevantes. No momento, apenas uma identidade pode ser fornecida. O suporte a vários conjuntos de dados será adicionado para a inserção de dashboards no futuro. Para que a RLS funcione, você precisará passar os itens a seguir como parte da identidade.

* **nome de usuário (obrigatório)** – isso é uma cadeia de caracteres que pode ser usada para ajudar a identificar o usuário ao aplicar as regras de RLS. Apenas um usuário pode ser listado.
* **funções (obrigatório)** – uma cadeia de caracteres que contém as funções a serem selecionadas ao aplicar as regras de Segurança em Nível de Linha. Se você estiver passando mais de uma função, elas deverão ser passadas como uma matriz de cadeia de caracteres.
* **conjunto de dados (obrigatório)** – o conjunto de dados aplicável ao relatório que está sendo inserido. Apenas um conjunto de dados pode ser fornecido na lista de conjuntos de dados. O suporte a vários conjuntos de dados será fornecido para a inserção de dashboards no futuro.

Crie o token de inserção usando o método **GenerateTokenInGroup** em **PowerBIClient.Reports**. Atualmente, há suporte apenas para relatórios.

Por exemplo, você poderá alterar a amostra [PowerBIEmbedded_AppOwnsData](https://github.com/Microsoft/PowerBI-Developer-Samples/tree/master/App%20Owns%20Data). *As linhas 76 e 77 de Home\HomeController.cs* podem ser atualizadas de:

```
// Generate Embed Token.
var generateTokenRequestParameters = new GenerateTokenRequest(accessLevel: "view");

var tokenResponse = await client.Reports.GenerateTokenInGroupAsync(GroupId, report.Id, generateTokenRequestParameters);
```

para

```
var generateTokenRequestParameters = new GenerateTokenRequest("View", null, identities: new List<EffectiveIdentity> { new EffectiveIdentity(username: "username", roles: new List<string> { "roleA", "roleB" }, datasets: new List<string> { "datasetId" }) });

var tokenResponse = await client.Reports.GenerateTokenInGroupAsync("groupId", "reportId", generateTokenRequestParameters);
```

Se você estiver chamando a API REST, a API atualizada agora aceitará uma matriz JSON adicional, chamada **identidades**, que contém um nome de usuário, a lista de funções de cadeia de caracteres e a lista de conjuntos de dados de cadeia de caracteres, por exemplo:

```
{
    "accessLevel": "View",
    "identities": [
        {
            "username": "EffectiveIdentity",
            "roles": [ "Role1", "Role2" ],
            "datasets": [ "fe0a1aeb-f6a4-4b27-a2d3-b5df3bb28bdc" ]
        }
    ]
}
```

Agora, com todas as informações juntas, quando alguém fizer logon no aplicativo para exibir este relatório, ele só poderá ver os dados que tem permissão para ver, conforme definido por nossa segurança em nível de linha.

## <a name="working-with-analysis-services-live-connections"></a>Trabalhando com conexões dinâmicas do Analysis Services
A segurança em nível de linha pode ser usada com conexões dinâmicas do Analysis Services para servidores locais. Há alguns conceitos específicos que você deve compreender ao usar esse tipo de conexão.

A identidade efetiva fornecida para a propriedade de nome de usuário deve ser um usuário do Windows com permissões no servidor do Analysis Services.

**Configuração do gateway de dados local**

Um [gateway de dados local](../service-gateway-onprem.md) é usado ao trabalhar com as conexões dinâmicas do Analysis Services. Ao gerar um token de inserção, com uma identidade listada, a conta mestra precisa estar listada como um administrador do gateway. Se a conta mestra não estiver listada, a segurança em nível de linha não aplicará a propriedade aos dados. Um não administrador do gateway pode fornecer funções, mas deve especificar seu próprio nome de usuário para a identidade efetiva.

**Uso de funções**

As funções podem ser fornecidas com a identidade em um token de inserção. Se nenhuma função for fornecida, o nome de usuário fornecido será usado para resolver as funções associadas.

## <a name="considerations-and-limitations"></a>Considerações e limitações
* A atribuição de usuários a funções, no serviço do Power BI, não afeta a RLS ao usar um token de inserção.
* Embora o serviço do Power BI não aplicará a configuração de RLS a administradores ou membros com permissões de edição, ao fornecer uma identidade com um token de inserção, ela será aplicada aos dados.
* Apenas há suporte para o fornecimento das informações de identidade, durante a chamada à GenerateToken, na leitura/gravação de relatório. O suporte para outros recursos será fornecido posteriormente.
* Para servidores locais, há suporte para conexões dinâmicas do Analysis Services.
* Não há suporte para conexões dinâmicas do Azure Analysis Services.
* Se o conjunto de dados subjacente não exigir a RLS, a solicitação de GenerateToken **não** deverá conter uma identidade efetiva.
* Se o conjunto de dados subjacente for um modelo de nuvem (modelo armazenado em cache ou DirectQuery), a identidade efetiva deverá incluir, pelo menos, uma função. Caso contrário, a atribuição de função não ocorrerá.
* Apenas uma identidade pode ser fornecida na lista de identidades. Estamos usando uma lista para permitir tokens de várias identidades para a inserção de dashboard no futuro.

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)

