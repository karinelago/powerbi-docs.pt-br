---
title: Importar pastas de trabalho do Excel para o Power BI Desktop
description: Importar pastas de trabalho do Excel para o Power BI Desktop
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
ms.date: 12/06/2017
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 247b8dca825f3e98de02207ba6d146e1aacd7580
ms.sourcegitcommit: 3f2f254f6e8d18137bae879ddea0784e56b66895
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="import-excel-workbooks-into-power-bi-desktop"></a>Importar pastas de trabalho do Excel para o Power BI Desktop
Com o **Power BI Desktop**, você pode importar facilmente pastas de trabalho do Excel que contêm consultas do Power Query, modelos do Power Pivot e planilhas do Power View para o Power BI Desktop. Relatórios e visualizações são criados automaticamente com base na pasta de trabalho do Excel e, uma vez importados, você pode continuar a melhorar e refinar esses relatórios usando o Power BI Desktop, usando os recursos existentes e novos recursos lançados com cada atualização mensal do Power BI Desktop.

No futuro, a intenção é de oferecer comunicação adicional entre o Excel e o Power BI Desktop (como importação/exportação); essa capacidade atual de importar pastas de trabalho para o Power BI Desktop permite que os usuários atuais do Excel comecem a usar o Power BI Desktop.

## <a name="how-do-i-import-an-excel-workbook"></a>Como importar uma pasta de trabalho do Excel?
Para importar uma pasta de trabalho, do Power BI Desktop, selecione **Arquivo -\> Importar -\> Conteúdo da Pasta de Trabalho do Excel**.

![](media/desktop-import-excel-workbooks/importexceltopbi_1.png)

Uma janela é exibida, permitindo que você selecione a pasta de trabalho a importar. Atualmente, não há nenhuma limitação para o tamanho ou número de objetos na pasta de trabalho, mas o Power BI Desktop leva mais tempo para analisar e importar pastas de trabalho maiores.

> [!NOTE]
> Para carregar ou importar arquivos do Excel de pastas do **OneDrive for Business compartilhado** ou de pastas do **grupo Office 365**, use o URL do arquivo Excel e insira-os na fonte de dados na **Web**, no Power BI Desktop. Existem algumas etapas que você precisa seguir para formatar corretamente a URL do **OneDrive for Business**, então confira [Usar os links do OneDrive for Business no Power BI Desktop](desktop-use-onedrive-business-links.md) para obter mais informações e a série correta de etapas.
> 
> 

Quando uma pasta de trabalho é selecionada, o Power BI Desktop analisa a pasta de trabalho e converte-a em um arquivo do Power BI Desktop (.pbix). Essa ação é um evento único; depois de criar o arquivo do Power BI Desktop com essas etapas, o arquivo não terá nenhuma dependência da pasta de trabalho original do Excel e poderá ser modificado ou alterado (e salvo e compartilhado) sem afetar a pasta de trabalho original.

![](media/desktop-import-excel-workbooks/importexceltopbi_2.png)

Depois que a importação for concluída, é exibida uma página **Resumo** que descreve os itens que foram convertidos e também lista quaisquer itens que não puderam ser importados.

![](media/desktop-import-excel-workbooks/importexceltopbi_3.png)

Quando você seleciona **Fechar**, o relatório é carregado no Power BI Desktop. A imagem a seguir mostra o Power BI Desktop após uma pasta de trabalho do Excel ser importada: o Power BI Desktop carregou automaticamente o relatório com base no conteúdo da pasta de trabalho.

![](media/desktop-import-excel-workbooks/importexceltopbi_4.png)

Agora que a pasta de trabalho foi importada, você pode continuar trabalhando no relatório – criando novas visualizações, adicionando dados, ou criando novas páginas de relatório – usando qualquer um dos recursos e funcionalidades incluídas no Power BI Desktop.

## <a name="which-workbook-elements-are-imported"></a>Quais elementos de pasta de trabalho são importados?
O Power BI Desktop pode importar os elementos a seguir, normalmente conhecidos como *objetos*, no Excel.

| Objeto na Pasta de Trabalho do Excel | Resultado Final no arquivo do Power BI Desktop |
| --- | --- |
| Consultas do Power Query |Todas as consultas do Power Query do Excel são convertidas em consultas no Power BI Desktop. Se havia Grupos de Consulta definidos na Pasta de Trabalho do Excel, a mesma organização será replicada no Power BI Desktop. Todas as consultas são carregadas, a menos que elas tenham sido definidas como "Apenas Criar Conexão" no Excel. O comportamento de Carregamento pode ser personalizado da caixa de diálogo **Propriedades** na guia **Home** do **Editor de Consultas** no Power BI Desktop. |
| Conexões de Dados Externos do Power Pivot |Todas as Conexões de Dados Externos do Power Pivot serão convertidas em consultas no Power BI Desktop. |
| Tabelas Vinculadas ou tabelas de Pasta de Trabalho Atual |Se há uma tabela de planilha no Excel vinculada ao Modelo de Dados ou vinculada a uma consulta (usando *From Table* ou a função *Excel.CurrentWorkbook()* em M), são apresentadas as seguintes opções: 1. Importe a tabela para o arquivo do Power BI Desktop. Essa tabela é um instantâneo único dos dados, após o qual você não poderá editar os dados na tabela no Power BI Desktop. Há um limite de tamanho de 1 milhão de caracteres (no total, combinando todas as células e cabeçalhos de coluna) para tabelas criadas usando essa opção. 2. Mantenha uma conexão com a pasta de trabalho original. Como alternativa, você pode manter uma conexão para a Pasta de Trabalho original do Excel e o Power BI Desktop recupera o conteúdo mais recente nessa tabela com cada atualização, assim como qualquer outra consulta criada para uma pasta de trabalho do Excel no Power BI Desktop. |
| Colunas Calculadas, Medidas, KPIs, Categorias de Dados e Relacionamentos do Modelo de dados |Esses objetos de Modelo de Dados são convertidos em objetos equivalentes no Power BI Desktop. Observe que existem certas categorias de dados que não estão disponíveis no Power BI Desktop, como **Imagem**. Nesses casos, as informações de Categoria de Dados serão redefinidas para as colunas em questão. |
| Planilhas do Power View |Uma nova página de relatório é criada para cada planilha do Power View no Excel. O nome e a ordem dessas páginas de relatório correspondem àqueles da pasta de trabalho original do Excel. |

## <a name="are-there-any-limitations-to-importing-a-workbook"></a>Há alguma limitação para importar uma pasta de trabalho?
Existem algumas limitações para importar uma pasta de trabalho no Power BI Desktop; veja essas limitações na seguinte lista:

* **Conexões Externas para Modelos de Tabela do Analysis Services:** no Excel 2013, é possível criar uma conexão com os Modelos de tabela do SQL Server Analysis Services e criar relatórios do Power View sobre esses modelos, sem a necessidade de importar os dados. Atualmente, não há suporte para esse tipo de conexão como parte da importação de Pastas de Trabalho do Excel para o Power BI Desktop. Como solução, você deve recriar essas conexões externas no Power BI Desktop.
* **Hierarquias:** atualmente, não há suporte para esse tipo de objeto de Modelo de Dados no Power BI Desktop. Desse modo, as hierarquias são ignorados como parte da importação de uma Pasta de Trabalho do Excel para o Power BI Desktop.
* **Colunas de dados binários:** atualmente, não há suporte para esse tipo de coluna de Modelo de Dados no Power BI Desktop. Colunas de Dados Binários são removidas da tabela resultante no Power BI Desktop.
* **Elementos do Power View sem suporte:** há alguns recursos do Power View que não estão disponíveis no Power BI Desktop, como os Temas ou determinados tipos de visualizações (Gráfico de Dispersão com Eixo de Reprodução, comportamentos de Busca Detalhada, etc). Estas visualizações sem suporte resultam em mensagens de *Visualização Sem Suporte* em seus locais correspondentes no relatório do Power BI Desktop, que você pode excluir ou reconfigurar conforme necessário.
* **Intervalos Nomeados usando*****From Table*** **no Power Query, ou usando** ***Excel.CurrentWorkbook*** **em M:** Atualmente não há suporte para a importação desses dados de intervalo nomeado para o Power BI Desktop, mas essa é uma atualização planejada para o Power BI Desktop. Atualmente, esses intervalos nomeados são carregados no Power BI Desktop como uma conexão à pasta de trabalho externa do Excel.
* **PowerPivot SSRS:** atualmente não há suporte para conexões externas do PowerPivot ao SSRS (SQL Server Reporting Services), já que essa fonte de dados não está disponível atualmente no Power BI Desktop.

