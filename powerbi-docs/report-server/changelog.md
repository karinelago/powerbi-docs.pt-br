---
title: Log de alterações para o Servidor de Relatório do Power BI
description: Esse log de alterações é para o Servidor de Relatório do Power BI e lista novos itens juntamente com correções de bug para cada build lançado.
services: powerbi
documentationcenter: ''
author: jtarquino
manager: kfile
backup: maggies
editor: ''
tags: ''
qualityfocus: no
qualitydate: ''
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 12/11/2017
ms.author: jtarquino
ms.openlocfilehash: bf6fae781863379e56c398f58d86d1bf1e5244af
ms.sourcegitcommit: 493f160d04ed411ff4741c599adc63ba1f65230f
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33813520"
---
# <a name="changelog-for-power-bi-report-server"></a>Log de alterações para o Servidor de Relatório do Power BI

Esse log de alterações é para o Servidor de Relatório do Power BI e lista novos itens juntamente com correções de bug para cada build lançado.

Para obter informações detalhadas sobre os novos recursos, consulte [Novidades no Servidor de Relatório do Power BI](whats-new.md). 

## <a name="march-2018"></a>Março de 2018
- **Servidor de Relatório do Power BI**
    - *Versão 1.2.6690.34729 (build 15.0.2.402), lançada em 27 de abril de 2018*
        - Correções de bug
            - Habilitar a migração de catálogos do SQL Server Reporting Services 2017
            - Para relatórios do Power BI (PBIX)
                - Os relatórios podem ser atualizados quando um servidor está configurado para usar a autenticação personalizada
                - Modificar as propriedades de um relatório não redefine as credenciais da fonte de dados
            - Para relatórios paginados (RDL)
                - O uso de funções `Lookup()` ou derivadas, como `LookupSet()` e `MultiLookup()`, em expressões RDL não resultam mais em `#Error`
                - Os relatórios vinculados respeitam o tamanho da página do relatório de destino ao imprimir
                - É possível criar assinaturas para relatórios vinculados que usam parâmetros em cascata
                - É possível alterar padrões de parâmetro com vários valores ao usar o IE11
                - É possível editar as opções de entrega de assinatura controladas por dados
                - É possível exibir e editar assinaturas enquanto a assinatura está em execução
                - Configurar credenciais de fonte de dados não remove as cadeias de caracteres de conexão baseadas em expressão
            - Para KPIs
                - As linhas de tendência são atualizadas com os dados
            - Melhorias na estabilidade geral

    - *Versão 1.2.6660.39920 (Build 15.0.2.389), lançada em: 28 de março de 2018*
        - Correções de bug
            - Para Relatórios do Power BI (PBIX), correção para Exportar Dados que não está funcionando em Visuais do Power BI
            - Para Relatórios do Power BI (PBIX), correção para filtros de URL não estão funcionando
            - Para Relatórios Paginados (RDL), correção para imagens que não são exibidas corretamente no IE11 após a atualização para a versão de março do Servidor de Relatórios do Power BI

    - *Versão 1.2.6648.38132 (Build 15.0.2.378), lançada em: 19 de março de 2018*
        - Atualizações de Segurança
        - Aprimoramentos de acessibilidade
        - Correções de bug
            - Para Relatórios Paginados (RDL), correção de visibilidade de parâmetros em um relatório vinculado que é revertido após a edição de suas propriedades
            - Correção para o portal da Web com autenticação de formulários personalizados que está ignorando o cookie sliding expiration
            - Correção para exportação para o Word, que cria uma altura de linha desigual se o conteúdo da linha está vazio
            - Para Relatórios Paginados (RDL), correção para cadeia de conexão baseada em expressão que é excluída quando alteramos a credencial da fonte de dados
            - Correção para a capacidade de usar um KPI com valores de texto
            - Para Relatórios Paginados (RDL), correção para a capacidade de atribuir um novo conjunto de dados para um Relatório Paginado (RDL) existente
            - Outras correções de estabilidade e de facilidade de uso

- **Power BI Desktop (otimizado para o Servidor de Relatórios do Power BI)**
    - Versão: 2.56.5023.1043 (março de 2018), lançada em: 19 de março de 2018
        - Contém as alterações necessárias para a conexão ao Servidor de Relatórios do Power BI (março de 2018)

## <a name="october-2017"></a>Outubro de 2017

- **Servidor de Relatório do Power BI**
    - *Versão 1.1.6582.41691 (Build 14.0.600.442), Lançamento: 10 de janeiro de 2018*
        - Atualizações de Segurança
        - Correções de bug
            - Correção para Model.GetParameters retornando 400
            - Correção para configurar o conjunto de dados compartilhado para Relatórios Paginados existentes (RDL)
            - Correção para ExecutionNotFoundException ao exportar o relatório com valores de parâmetros diferentes para PDF

    - *Versão 1.1.6551.5155 (Build 14.0.600.438), Lançamento: 11 de dezembro de 2017*
        - Correções de bug
            - Falha ao salvar dados após a atualização para determinados relatórios do Power BI Desktop.

    - *Versão 1.1.6530.30789 (Build 14.0.600.437), Lançamento: 17 de novembro de 2017*
        - Correções de bug
            - Correção para Cenários de Autenticação Básica 
            - A correção para dias da semana não pode ser selecionada na página de agendamentos para Assinaturas, Planos de Atualização de Cache e Instantâneos de Histórico no Portal
            - Para Relatórios Paginados (RDL), correção para expressões na caixa de texto com a propriedade CanGrow configurada como false resulta em valores que não mostram cores e fontes inadequadas
            - Para Relatórios do Power BI (PBIX), a correção para adicionar Legendas de gráfico de linhas renderiza um visual vazio

    - *Versão 1.1.6514.9163 (Build 14.0.600.434), Lançamento: 1 de novembro de 2017*
        - Correções de bug
            - Corrigir problemas de confiabilidade de upload para relatórios PBIX acima de 500 MB
            - Corrigir problemas de carregamento de problema para relatórios PBIX acima de 1GB

    - *Versão 1.1.6513.3500 (Build 14.0.600.433) Lançamento: 31 de outubro de 2017*
        - Recursos
            - Suporte para modelo de dados inserido
            - Exibição de pasta de trabalho do Excel (com a integração do Servidor do Office Online habilitada)
            - Atualização de dados agendada (PBIX)
            - Suporte para consulta direta
            - Suporte para arquivos grandes (até 2 GB)
            - API REST pública
            - Suporte para conjunto de dados compartilhado no Power BI Desktop (via OData)
            - Suporte para parâmetro de URL para arquivos PBIX
            - Aprimoramentos de acessibilidade

- **Power BI Desktop (otimizado para o Servidor de Relatórios do Power BI)**
    - *Versão: 2.51.4885.3981 (outubro de 2017), Lançamento: 10 de abril de 2018*
        - Atualizações de Segurança

    - *Versão: 2.51.4885.2501 (October 2017), Lançamento: 10 de janeiro de 2018*
        - Atualizações de Segurança

    - *Versão: 2.51.4885.1423 (outubro de 2017). Lançamento: 17 de outubro de 2017*
        - Correções de bug
            - Correção para Power BI Desktop de 32 bits falha na execução em SO x86
            - Para os Relatórios do Power BI (PBIX), correção para mostrar linhas de grade do eixo x
            - Outras correções de bugs secundários

    - *Versão: 2.51.4885.1041 (outubro de 2017). Lançamento: 31 de outubro de 2017*
        - Recursos
            - Contém as alterações necessárias para a conexão ao Servidor de Relatórios do Power BI (outubro de 2017)

## <a name="june-2017"></a>Junho de 2017

- **Servidor de Relatório do Power BI**
    - *Build 14.0.600.309, Lançamento: 10 de janeiro de 2018*
        - Atualizações de Segurança

    - *Build 14.0.600.305. Lançamento: 19 de setembro de 2017*  
        - Correções de bug
            - Atualizar para a versão mais recente do [Controle da Web do Bing Maps](https://msdn.microsoft.com/library/mt712542.aspx)

    - *Build 14.0.600.301. Lançamento: 11 de julho de 2017*
        - Correções de bug
            - A marca `{{UserId}}` resolve para as credenciais armazenadas, em vez do usuário que executa o relatório nos Relatórios do Power BI
            - Algumas imagens apresentam falha ao ser renderizadas em relatórios do Servidor de Relatório do Power BI
            - Não é possível alterar o nome de um Relatório do Power BI no Servidor de Relatório do Power BI
            - Não é possível carregar visuais personalizados no aplicativo móvel Power BI (isso requer a reinstalação do aplicativo móvel para limpar o cache local)

    - *Build 14.0.600.271. Lançamento: 12 de junho de 2017*
        - Versão inicial do Servidor de Relatório do Power BI

- **Power BI Desktop (otimizado para o Servidor de Relatórios do Power BI)**
    - *Versão: 2.47.4766.4901 (Junho de 2017), Lançamento: 10 de janeiro de 2018*
        - Atualizações de Segurança

## <a name="next-steps"></a>Próximas etapas

[Manual do usuário](user-handbook-overview.md)  
[Manual do administrador](admin-handbook-overview.md)  
[Instalar o Servidor de Relatório do Power BI](install-report-server.md)  
[Instalar o Construtor de Relatórios](https://docs.microsoft.com/sql/reporting-services/install-windows/install-report-builder)  
[Baixar o SSDT (SQL Server Data Tools)](http://go.microsoft.com/fwlink/?LinkID=616714)

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)
