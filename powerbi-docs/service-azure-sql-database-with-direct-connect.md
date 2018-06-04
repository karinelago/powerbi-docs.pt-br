---
title: Banco de Dados SQL do Azure com DirectQuery
description: Banco de Dados SQL do Azure com DirectQuery
author: markingmyname
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 12/18/2017
ms.author: maghan
LocalizationGroup: Data from databases
ms.openlocfilehash: 27b2eb90a07d3112b771fd3ee23cc86353a46991
ms.sourcegitcommit: 80d6b45eb84243e801b60b9038b9bff77c30d5c8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34242239"
---
# <a name="azure-sql-database-with-directquery"></a>Banco de Dados SQL do Azure com DirectQuery
Saiba como você pode se conectar diretamente ao banco de dados SQL e criar relatórios que usam dados dinâmicos. Você pode manter os dados na fonte e não no Power BI.

Com o DirectQuery, as consultas serão enviadas de volta para o Banco de Dados SQL do Azure conforme você explora os dados na exibição de relatório. Essa experiência é sugerida para usuários que estão familiarizados com os bancos de dados e as entidades aos quais eles se conectam.

**Observações:**

* Especifique o nome totalmente qualificado do servidor ao estabelecer a conexão (consulte abaixo para obter mais detalhes)
* Garanta que as regras de firewall para o banco de dados estejam configuradas para "[Permitir acesso aos serviços do Azure](https://msdn.microsoft.com/library/azure/ee621782.aspx)"
* Toda ação, como selecionar uma coluna ou adicionar um filtro, enviará uma consulta de volta ao banco de dados
* Os blocos são atualizados a cada hora (a atualização não precisa ser agendada). Isso pode ser ajustado nas Configurações avançadas quando você se conectar.
* P e R não estão disponíveis para conjuntos de dados do DirectQuery
* Alterações de esquema não são aplicadas automaticamente

Essas restrições e observações podem mudar conforme continuamos a aprimorar as experiências. As etapas para conectar são detalhadas abaixo. 

## <a name="power-bi-desktop-and-directquery"></a>Power BI Desktop e DirectQuery
Para se conectar ao Banco de Dados SQL do Azure usando DirectQuery, você precisará usar o Power BI Desktop. Essa abordagem fornece mais flexibilidade e funcionalidades adicionais. Os relatórios criados com o Power BI Desktop podem ser publicados no serviço do Power BI. Você pode aprender mais sobre como se conectar ao [Banco de Dados SQL do Azure usando DirectQuery](desktop-use-directquery.md) dentro do Power BI Desktop. 

## <a name="single-sign-on"></a>Logon único

Depois de publicar um conjunto de dados DirectQuery do SQL do Azure para o serviço, você pode habilitar o logon único (SSO) por meio do OAuth2 do Azure Active Directory (Azure AD) para os usuários finais. 

Para habilitar o SSO, acesse as configurações para o conjunto de dados, abra a guia **Fontes de dados** e marque a caixa SSO.

![Configure as caixa de diálogo DQ do SQL do Azure](media/service-azure-sql-database-with-direct-connect/sso-dialog.png)

Quando a opção de SSO está habilitada e os usuários acessam relatórios construídos sobre a fonte de dados, o Power BI envia suas credenciais autenticadas do Azure AD às consultas no banco de dados do SQL do Azure. Isso permite que o Power BI respeite as configurações de segurança que são configuradas no nível da fonte de dados.

A opção de SSO entra em vigor em todos os conjuntos de dados que usam essa fonte de dados. Isso não afeta o método de autenticação usado para cenários de importação.

## <a name="finding-parameter-values"></a>Localizando Valores de Parâmetro
Seu nome do servidor totalmente qualificado e o nome do banco de dados podem ser encontrados no Portal do Azure.

![](media/service-azure-sql-database-with-direct-connect/azureportnew_update.png)

![](media/service-azure-sql-database-with-direct-connect/azureportal_update.png)

## <a name="next-steps"></a>Próximas etapas
[Usar o DirectQuery no Power BI Desktop](desktop-use-directquery.md)  
[Introdução ao Power BI](service-get-started.md)  
[Obter dados para o Power BI](service-get-data.md)  
Mais perguntas? [Experimente a Comunidade do Power BI](http://community.powerbi.com/)
