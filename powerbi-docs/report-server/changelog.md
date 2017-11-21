---
title: "Log de alterações para o Servidor de Relatório do Power BI"
description: "Esse log de alterações é para o Servidor de Relatório do Power BI e lista novos itens juntamente com correções de bug para cada build lançado."
services: powerbi
documentationcenter: 
author: jtarquino
manager: jonhp
backup: asaxton
editor: 
tags: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 09/19/2017
ms.author: jaimeta
ms.openlocfilehash: 9fdc757fca252c5c35d308dcd0b326098683b159
ms.sourcegitcommit: 99cc3b9cb615c2957dde6ca908a51238f129cebb
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/13/2017
---
# <a name="changelog-for-power-bi-report-server"></a>Log de alterações para o Servidor de Relatório do Power BI
Esse log de alterações é para o Servidor de Relatório do Power BI e lista novos itens juntamente com correções de bug para cada build lançado.

Para obter informações detalhadas sobre os novos recursos, consulte [Novidades no Servidor de Relatório do Power BI](whats-new.md).

## <a name="october-2017"></a>Outubro de 2017
* **Servidor de Relatório do Power BI**
  * *Versão 1.1.6514.9163 (Build 14.0.600.434), Lançamento: 1 de novembro de 2017*
    * Correções de bug
      * Corrigir problemas de confiabilidade de upload para relatórios PBIX acima de 500 MB
      * Corrigir problemas de carregamento de problema para relatórios PBIX acima de 1GB
  * *Versão 1.1.6513.3500 (Build 14.0.600.433) Lançamento: 31 de outubro de 2017*
    * Recursos
      * Suporte para modelo de dados inserido
      * Exibição de pasta de trabalho do Excel (com a integração do Servidor do Office Online habilitada)
      * Atualização de dados agendada (PBIX)
      * Suporte para consulta direta
      * Suporte para arquivos grandes (até 2 GB)
      * API REST pública
        * Suporte para conjunto de dados compartilhado no Power BI Desktop (via OData)
      * Suporte para parâmetro de URL para arquivos PBIX
      * Aprimoramentos de acessibilidade
* **Power BI Desktop (otimizado para o Servidor de Relatórios do Power BI)**
  * *Versão: 2.51.4885.1041 (outubro de 2017). Lançamento: 31 de outubro de 2017*
    * Contém as alterações necessárias para a conexão ao Servidor de Relatórios do Power BI (outubro de 2017)

## <a name="june-2017"></a>Junho de 2017
* **Servidor de Relatório do Power BI**
  
  * *Build 14.0.600.305. Lançamento: 19 de setembro de 2017*  
    
    * Correções de bug
      * Atualizar para a versão mais recente do [Controle da Web do Bing Maps](https://msdn.microsoft.com/library/mt712542.aspx)
  * *Build 14.0.600.301. Lançamento: 11 de julho de 2017*
    
    * Correções de bug
      * A marca {{UserId}} resolve para as credenciais armazenadas, em vez do usuário que executa o relatório nos Relatórios do Power BI
      * Algumas imagens apresentam falha ao ser renderizadas em relatórios do Servidor de Relatório do Power BI
      * Não é possível alterar o nome de um Relatório do Power BI no Servidor de Relatório do Power BI
      * Não é possível carregar visuais personalizados no aplicativo móvel Power BI (isso requer a reinstalação do aplicativo móvel para limpar o cache local)
  * *Build 14.0.600.271. Lançamento: 12 de junho de 2017*
    
    * Versão inicial do Servidor de Relatório do Power BI

## <a name="next-steps"></a>Próximas etapas
[Manual do usuário](user-handbook-overview.md)  
[Manual do administrador](admin-handbook-overview.md)  
[Início rápido: instalar o Servidor de Relatório do Power BI](quickstart-install-report-server.md)  
[Instalar o Construtor de Relatórios](https://docs.microsoft.com/sql/reporting-services/install-windows/install-report-builder)  
[Baixar o SSDT (SQL Server Data Tools)](http://go.microsoft.com/fwlink/?LinkID=616714)

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)

