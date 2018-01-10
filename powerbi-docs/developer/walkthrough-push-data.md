---
title: Enviar dados por push a um conjunto de dados
description: Enviar dados por push a um conjunto de dados do Power BI
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
ms.date: 01/05/2017
ms.author: asaxton
ms.openlocfilehash: aba135a0a790025f732379ecb07157f1150d999c
ms.sourcegitcommit: 7517c068db806f12bb0b953e9a1bd4249ca12da5
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/05/2018
---
# <a name="push-data-into-a-power-bi-dataset"></a>Enviar dados por push a um conjunto de dados do Power BI
Com a API do Power BI, você pode enviar dados por push para um conjunto de dados do Power BI. Por exemplo, você deseja estender um fluxo de trabalho de negócios existente para enviar por push dados de chave para seu conjunto de dados. Nesse caso, você deseja enviar por push um conjunto de dados de Marketing de vendas, que tem uma Tabela de produto, para um conjunto de dados.

Antes de começar a enviar dados por push a um conjunto de dados, é necessário ter uma conta do Azure AD (Azure Active Directory) e uma [conta do Power BI](create-an-azure-active-directory-tenant.md).

## <a name="steps-to-push-data-into-a-dataset"></a>Etapas para enviar dados por push a um conjunto de dados
* Etapa 1: [Registrar um aplicativo no Azure AD](walkthrough-push-data-register-app-with-azure-ad.md)
* Etapa 2: [Obter um token de acesso de autenticação](walkthrough-push-data-get-token.md)
* Etapa 3: [Criar um conjunto de dados no Power BI](walkthrough-push-data-create-dataset.md)
* Etapa 4: [Obter um conjunto de dados para adicionar linhas em uma tabela do Power BI](walkthrough-push-data-get-datasets.md)
* Etapa 5: [Adicionar linhas a uma tabela do Power BI](walkthrough-push-data-add-rows.md)

A próxima seção é uma discussão geral sobre as operações da API do Power BI que enviam dados por push.

## <a name="power-bi-api-operations-to-push-data"></a>Operações da API do Power BI para enviar dados por push
Com a API REST do Power BI, você pode enviar por push fontes de dados para o Power BI. Quando um aplicativo adiciona linhas a um conjunto de dados, os blocos no painel são atualizados automaticamente com os dados atualizados. Para enviar dados por push, você usa a operação [Criar Conjunto de Dados](https://msdn.microsoft.com/library/mt203562.aspx) juntamente com a operação [Adicionar Linhas](https://msdn.microsoft.com/library/mt203561.aspx). Para encontrar um conjunto de dados, você usa a operação [Obter Conjuntos de Dados](https://msdn.microsoft.com/library/mt203567.aspx). Para qualquer uma dessas operações, você pode passar uma ID de grupo para trabalhar com um grupo. Use a operação [Obter Grupos](https://msdn.microsoft.com/library/mt243842.aspx) para obter uma lista de IDs de grupo.

Estas são as operações para enviar dados por push a um conjunto de dados:

* [Criar conjunto de dados](https://msdn.microsoft.com/library/mt203562.aspx)
* [Obter conjuntos de dados](https://msdn.microsoft.com/library/mt203567.aspx)
* [Adicionar linhas](https://msdn.microsoft.com/library/mt203561.aspx)
* [Obter grupos](https://msdn.microsoft.com/library/mt243842.aspx)

Você pode criar um conjunto de dados no Power BI passando uma cadeia de caracteres JSON (JavaScript Object Notation) para o serviço do Power BI. Para saber mais sobre o JSON, veja [Apresentando o JSON](http://json.org/).

A cadeia de caracteres JSON para um conjunto de dados tem o seguinte formato:

**Objeto JSON do conjunto de dados do Power BI**

    {"name": "dataset_name", "tables":
        [{"name": "", "columns":
            [{ "name": "column_name1", "dataType": "data_type"},
             { "name": "column_name2", "dataType": "data_type"},
             { ... }
            ]
          }
        ]
    }

Assim, em nosso exemplo de conjunto de dados de Marketing de vendas, você passaria uma cadeia de caracteres JSON como o exemplo a seguir. Neste exemplo, **SalesMarketing** é o nome do conjunto de dados, e **Product** é o nome da tabela. Depois de definir a tabela, você pode definir o esquema da tabela. Para o conjunto de dados **SalesMarketing** , o esquema da tabela tem as seguintes colunas: ProductID, Manufacturer, Category, Segment, Product e IsCompete.

**JSON de objeto de conjunto de dados de exemplo**

    {
        "name": "SalesMarketing",
        "tables": [
            {
                "name": "Product",
                "columns": [
                {
                    "name": "ProductID",
                    "dataType": "int"
                },
                {
                    "name": "Manufacturer",
                    "dataType": "string"
                },
                {
                    "name": "Category",
                    "dataType": "string"
                },
                {
                    "name": "Segment",
                    "dataType": "string"
                },
                {
                    "name": "Product",
                    "dataType": "string"
                },
                {
                    "name": "IsCompete",
                    "dataType": "bool"
                }
                ]
            }
        ]
    }

Para um esquema de tabela do Power BI, você pode usar os seguintes tipos de dados.

## <a name="power-bi-table-data-types"></a>Tipos de dados de tabela do Power BI
| **Tipo de dados** | **Restrições** |
| --- | --- |
| Int64 |Int64.MaxValue e Int64.MinValue não permitidos. |
| Double |Valores de Double.MaxValue e Double.MinValue não permitidos. Não há suporte para NaN. Não há suporte para +Infinity e -Infinity em algumas funções (por exemplo, Min e Max). |
| Boolean |Nenhum |
| Datetime |Durante o carregamento de dados, podemos quantizar valores com frações de dias para múltiplos inteiros de 1/300 de segundo (3,33 ms). |
| Cadeia de caracteres |Atualmente, permite até 128 mil caracteres. |

## <a name="learn-more-about-pushing-data-into-power-bi"></a>Saiba mais sobre como enviar dados por push ao Power BI
Para começar a enviar dados por push a um conjunto de dados, veja [Etapa 1: registrar um aplicativo no Azure AD](walkthrough-push-data-register-app-with-azure-ad.md) no painel de navegação esquerdo.

[Próxima etapa >](walkthrough-push-data-register-app-with-azure-ad.md)

## <a name="next-steps"></a>Próximas etapas
[Inscrever-se no Power BI](create-an-azure-active-directory-tenant.md)  
[Criar conjunto de dados](https://msdn.microsoft.com/library/mt203562.aspx)  
[Obter conjuntos de dados](https://msdn.microsoft.com/library/mt203567.aspx)  
[Adicionar linhas](https://msdn.microsoft.com/library/mt203561.aspx)  
[Obter grupos](https://msdn.microsoft.com/library/mt243842.aspx)  
[Introdução ao JSON](http://json.org/)  
[Visão geral da API REST do Power BI](overview-of-power-bi-rest-api.md)  
Mais perguntas? [Experimente a Comunidade do Power BI](http://community.powerbi.com/)

