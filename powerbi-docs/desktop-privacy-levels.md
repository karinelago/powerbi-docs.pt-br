---
title: Entender os níveis de privacidade do Power BI Desktop
description: Níveis de privacidade do Power BI Desktop
services: powerbi
documentationcenter: ''
author: davidiseminger
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
ms.date: 05/02/2018
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 1d491ef4325374747b00fb1d3a4c8c3a9be7dd18
ms.sourcegitcommit: f679c05d029ad0765976d530effde744eac23af5
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="power-bi-desktop-privacy-levels"></a>Níveis de privacidade do Power BI Desktop
No **Power BI Desktop**, os níveis de privacidade especificam um nível de isolamento que define o grau que uma fonte de dados será isolada de outras fontes de dados. Apesar de o nível de isolamento restrito bloquear a troca de informações entre as fontes de dados, ele poderá reduzir a funcionalidade e causar um impacto no desempenho.

A configuração **Níveis de Privacidade**, encontrada em **Arquivo > Opções e configurações > Opções** e, em seguida, em **Arquivo atual > Privacidade** determina se o Power BI Desktop usa suas configurações de Nível de Privacidade ao combinar dados. Essa caixa de diálogo inclui um link para a documentação do Power BI Desktop sobre Níveis de Privacidade (este artigo).

![](media/desktop-privacy-levels/desktop_privacylevels1.png)

## <a name="configure-a-privacy-level"></a>Configurar um nível de privacidade
Com as configurações de nível de privacidade, você pode especificar um nível de isolamento que define o grau que uma fonte de dados deve ser isolada de outras fontes de dados.

| Configuração | Descrição | Exemplo de fontes de dados |
| --- | --- | --- |
| **Fonte de dados particular** |Uma fonte e dados **Particular** contém informações confidenciais e a visibilidade da fonte de dados pode ser restrita a usuários autorizados. Uma fonte de dados particular é completamente isolada de outras fontes de dados. |Os dados do Facebook, um arquivo de texto com prêmios de ações ou uma pasta de trabalho com informações de avaliação de funcionários. |
| **Fonte de dados Organizacional** |Uma fonte de dados **Organizacional** limita a visibilidade de uma fonte de dados para um grupo de pessoas confiáveis. Uma fonte de dados **Organizacional** é isolada de todas as fontes de dados **Públicas** , mas é visível para outras fontes de dados **Organizacionais** . |Um documento do **Microsoft Word** em um site do SharePoint com permissões habilitadas para um grupo de pessoas confiáveis. |
| **Fonte de dados pública** |Uma fonte de dados **Pública** fornece a todos visibilidade dos dados contidos na fonte de dados. Somente arquivos, fontes de dados da internet ou dados de pasta de trabalho podem ser marcados **Públicos**. |Os dados gratuitos do Microsoft Azure Marketplace, os dados de uma página do Wikipedia ou um arquivo local com os dados copiados de uma página da Web pública. |

## <a name="configure-privacy-level-settings"></a>Definir configurações de nível de privacidade
O diálogo de configurações de **Privacidade** para cada fonte de dados pode ser encontrado em **Arquivo > Opções e configurações > Configurações da fonte de dados**.

Para configurar um nível de privacidade da fonte de dados, selecione a fonte de dados e selecione **Editar**. O diálogo **Configurações de fonte de dados** é exibida e nele você pode selecionar o nível de privacidade adequado no menu suspenso na parte inferior da caixa de diálogo, como mostrado na imagem a seguir.

![](media/desktop-privacy-levels/desktop_privacylevels2.png)

> [!CAUTION]
> Configure uma fonte de dados que contenha dados altamente confidenciais como **Privada**.
> 

## <a name="configure-privacy-levels"></a>Configurar Níveis de Privacidade
**Níveis de Privacidade** é uma configuração definida para **Combinar dados de acordo com as configurações de Nível de privacidade para cada fonte** por padrão, o que significa que **Níveis de Privacidade** não está habilitada.

| Configuração | Descrição |
| --- | --- |
| **Combinar os dados de acordo com as definições de Nível de privacidade de cada origem** (ativada e a configuração padrão) |As configurações de nível de privacidade são usadas para determinar o nível de isolamento entre fontes de dados ao combinar dados. |
| **Ignorar os níveis de Privacidade e melhorar potencialmente o desempenho** (desativada) |No entanto, os níveis de privacidade não são considerados ao combinar dados; podem aumentar o desempenho e a funcionalidade dos dados. |

> **Observação de segurança:** habilitar **Níveis de Privacidade** selecionando **Ignore os Níveis de Privacidade e melhore potencialmente o desempenho** na caixa de diálogo **Níveis de Privacidade** pode expor dados confidenciais para uma pessoa não autorizada. Não habilite os **Níveis de Privacidade** a menos que você tenha certeza de que a fonte de dados não contém dados confidenciais.
> 
> 

> [!CAUTION]
> O **Ignore os Níveis de Privacidade e melhore potencialmente o desempenho** não funciona no serviço do Power BI. Dessa forma, os relatórios do Power BI Desktop com essa configuração habilitada que, em seguida, são publicados no serviço do Power BI, *não* refletem esse comportamento quando usado no serviço.
> 

**Configurar Níveis de Privacidade**

No Power BI Desktop ou no Editor de Consultas, selecione **Arquivo > Opções e configurações > Opções** e **Arquivo atual > Privacidade**.

a. Quando **Combinar dados de acordo com as configurações de Nível de privacidade para cada fonte** estiver selecionado, os dados serão combinados de acordo com a sua configuração dos Níveis de privacidade. Mesclar dados entre zonas de isolamento de Privacidade resultará em buffer de dados.

b. Quando **Ignorar os Níveis de privacidade e potencialmente melhorar o desempenho** estiver selecionado, os dados serão combinados, ignorando os Níveis de Privacidade que poderiam revelar dados confidenciais para um usuário não autorizado. A configuração pode melhorar o desempenho e a funcionalidade

> **Observação de segurança:** selecionar **Ignorar os Níveis de privacidade e potencialmente melhorar o desempenho** pode melhorar o desempenho; no entanto, o Power BI Desktop não pode garantir a privacidade dos dados mesclados para o arquivo do Power BI Desktop.
> 
> 

