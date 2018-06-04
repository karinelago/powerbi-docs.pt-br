---
title: Parte 2, Adicionar visualizações a um relatório do Power BI
description: Parte 2, Adicionar visualizações a um relatório do Power BI
author: mihart
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 01/23/2018
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: 5c3f98635d188aa1857be9c8d8e36dc296339ad7
ms.sourcegitcommit: 80d6b45eb84243e801b60b9038b9bff77c30d5c8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34292215"
---
# <a name="part-2-add-visualizations-to-a-power-bi-report"></a>Parte 2, Adicionar visualizações a um relatório do Power BI
Na [Parte 1](power-bi-report-add-visualizations-ii.md), você criou uma visualização básica marcando as caixas de seleção ao lado dos nomes de campo.  Na parte 2, você aprenderá como usar o arrastar e soltar e fazer uso integral dos painéis **Campos** e **Visualizações** para criar e modificar as visualizações.

### <a name="prerequisites"></a>Pré-requisitos
- [Parte 1](power-bi-report-add-visualizations-ii.md)
- Serviço do Power BI – visualizações podem ser adicionadas a relatórios usando o serviço Power BI ou Power BI Desktop. Este tutorial usa o serviço Power BI. 
- Exemplo de análise de varejo

## <a name="create-a-new-visualization"></a>Criar uma nova visualização
Neste tutorial, vamos examinar nosso conjunto de dados de Análise de Varejo e criar algumas visualizações chave.

### <a name="open-a-report-and-add-a-new-blank-page"></a>Abra um relatório e adicione uma nova página em branco.
1. Abra o espaço de trabalho no qual você salvou o exemplo Análise de Varejo. Selecione **Exemplo Análise de Varejo** para abrir o relatório no Modo de Exibição de Leitura.
   
   ![](media/power-bi-report-add-visualizations-ii/power-bi-open-report.png)
2. Selecione **Editar relatório** para abrir o relatório no modo de Exibição de Edição.
   
   ![](media/power-bi-report-add-visualizations-ii/editreport1.png)
3. [Adicione uma nova página](power-bi-report-add-page.md) selecionando o ícone de adição amarelo na parte inferior da tela.
   
   ![](media/power-bi-report-add-visualizations-ii/pbi_addreportpage.png)

### <a name="add-a-visualization-that-looks-at-this-years-sales-compared-to-last-year"></a>Adicione uma visualização que examina o débito no último ano de vendas deste ano.
1. Na tabela **Vendas**, selecione **Vendas deste Ano** > **Valor** e **Vendas do Ano Passado**. O Power BI cria um gráfico de colunas.  Isso é interessante e você deseja investigar. O que torna as vendas semelhantes por mês?  
   
   ![](media/power-bi-report-add-visualizations-ii/pbi_part2_4bnew.png)
2. Na tabela Tempo, arraste **Mês** na área **Eixo**.  
   ![](media/power-bi-report-add-visualizations-ii/pbi_part2_5newnew.png)
3. [Mude a visualização](power-bi-report-change-visualization-type.md) para um gráfico Área.  Há muitos tipos de visualização dentre as quais escolher – veja as [descrições de cada uma, dicas de melhores práticas e tutoriais](power-bi-visualization-types-for-reports-and-q-and-a.md) para ajudar a decidir qual tipo usar. No painel de visualizações, selecione o ícone do gráfico Área.
4. Classifique a visualização selecionando as reticências e escolhendo **Classificar por Mês**.
5. [Redimensione a visualização](power-bi-visualization-move-and-resize.md) selecionando a visualização, captando um dos círculos da estrutura de tópicos e arrastando-o. Torne-a grande o suficiente para eliminar a barra de rolagem e pequeno o suficiente para nos dar espaço suficiente para adicionar outra visualização.
   
   ![](media/power-bi-report-add-visualizations-ii/pbi_part2_7b.png)
6. [Salve o relatório](service-report-save.md).

### <a name="add-a-map-visualization-that-looks-at-sales-by-location"></a>Adicionar uma visualização do mapa que analisa as vendas por local
1. Na tabela **Loja**, selecione **Território**. O Power BI reconhece que a Região é um local e cria uma visualização de mapa.  
   ![](media/power-bi-report-add-visualizations-ii/pbi_part2_8newnew.png)
2. Arraste **Pontuação Total** na área Tamanho.  
   ![](media/power-bi-report-add-visualizations-ii/power-bi-add-visual-to-a-reportnew.png)
3. Adicione uma legenda.  Para ver os dados por nome de loja, arraste a **Cadeia** para a área Legenda.  
   ![](media/power-bi-report-add-visualizations-ii/power-bi-add-visual-to-a-report-3new.png)

## <a name="next-steps"></a>Próximas etapas
* Para obter mais informações sobre o painel de Campos, veja [O editor de relatório... faça um tour](service-the-report-editor-take-a-tour.md).   
* Para saber como filtrar e destacar suas visualizações, veja [Filtros e destaque em relatórios do Power BI](power-bi-reports-filters-and-highlighting.md).  
* Mais sobre [Visualizações nos relatórios do Power BI](power-bi-report-visualizations.md).  
* Mais perguntas? [Experimente a Comunidade do Power BI](http://community.powerbi.com/)

