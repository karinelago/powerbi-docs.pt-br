---
title: "Exportar dados de uma visualização do Power BI"
description: "Exporte dados de visualizações de relatórios e de painéis exiba-os no Excel."
services: powerbi
documentationcenter: 
author: mihart
manager: kfile
backup: 
editor: 
tags: 
featuredvideoid: jtlLGRKBvXY
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 11/19/2017
ms.author: mihart
ms.openlocfilehash: 2e5f72b0eb2507f8d2c7df7fc8a57817bb6ce79f
ms.sourcegitcommit: a658b1c936e382f46a19eeb9cc26016cd7b1d756
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/20/2017
---
# <a name="export-data-from-visualizations"></a>Exportar dados de uma visualização
Se desejar ver os dados usados para criar uma visualização, você poderá [exibi-los no Power BI](service-reports-show-data.md) ou exportá-los para o Excel como um arquivo .xlsx ou .csv.   

Assista a Will exportar os dados de uma das visualizações de seu relatório, salvá-los como um arquivo .xlsx e abri-los no Excel. Em seguida, siga as instruções passo a passo abaixo do vídeo para testá-la por conta própria.

<iframe width="560" height="315" src="https://www.youtube.com/embed/KjheMTGjDXw" frameborder="0" allowfullscreen></iframe>

## <a name="from-a-visualization-on-a-power-bi-dashboard"></a>De uma visualização em um painel do Power BI
1. Selecione as elipses no canto superior direito da visualização.
   
    ![](media/power-bi-visualization-export-data/pbi-export-tile3.png)
2. Escolha o ícone  **Exportar dados** .
   
    ![](media/power-bi-visualization-export-data/pbi_export_dash.png)
3. Os dados são exportados para um arquivo .csv. Se o visual for filtrado, os dados baixados também serão filtrados.
4. O navegador solicitará que você salve o arquivo.  Após salvá-lo, abra o arquivo .csv no Excel.
   
    ![](media/power-bi-visualization-export-data/pbi-export-to-excel.png)

## <a name="from-a-visualization-in-a-report"></a>De uma visualização em um relatório
Para continuar, abra o [Relatório de exemplo de análise de aquisições](sample-procurement.md) no [Modo de Exibição de Edição](service-reading-view-and-editing-view.md). [Adicionar uma nova página de relatório em branco](power-bi-report-add-page.md). Em seguida, siga as etapas abaixo para adicionar uma agregação e um filtro de nível de visualização.

1. Criar um novo gráfico de coluna.  No painel Campos, selecione **Localização > Cidade** e **Fatura > Porcentagem de Desconto**.   
   
    ![](media/power-bi-visualization-export-data/power-bi-export-data3.png)
2. Alterar a agregação de **Porcentagem de Desconto** de **Contagem** para **Média**. Na seção Valor, selecione a seta à direita de **Porcentagem de Desconto** (poderá estar como **Contagem de porcentagem de desconto**) e escolha **Média**.
   
    ![](media/power-bi-visualization-export-data/power-bi-export-data6.png)
3. Adicione um filtro para **Cidade** para remover **Atlanta**.
   
   ![](media/power-bi-visualization-export-data/power-bi-export-data4.png)
   
   Agora estamos prontos para experimentar as duas opções de exportação de dados.
4. Selecione as elipses no canto superior direito da visualização. Escolha  **Exportar dados**.
   
   ![](media/power-bi-visualization-export-data/power-bi-export-data2.png)
5. Se a sua visualização tem uma agregação (um exemplo seria se você alterou **Contagem** para *média*, **soma** ou *mínimo*), você terá duas opções: **Dados resumidos** e **Dados subjacentes**. Para entender melhor as agregações, consulte [Agregações no Power BI](service-aggregates.md).
   
    ![](media/power-bi-visualization-export-data/power-bi-export-data5.png)
6. Selecione **Dados resumidos** > **Exportar** e escolha .xlsx ou .csv. O Power BI exporta os dados.  Se você aplicou filtros à visualização, os dados serão exportados da maneira que foram filtrados. Ao selecionar **Exportar**, o navegador solicitará que você salve o arquivo. Após salvá-lo, abra o arquivo no Excel.
   
   **Dados resumidos**: selecione essa opção se você não tiver nenhuma agregação ou se tiver uma agregação, mas não desejar ver a divisão completa. Por exemplo, se você tiver um gráfico de barras mostrando quatro barras, você obterá quatro linhas de dados. Os dados resumidos estão disponíveis como arquivos .xlsx e .csv.
   
   Neste exemplo, a nossa exportação do Excel mostra um total para cada cidade. Como filtramos e retiramos Atlanta, ela não está incluída nos resultados.  A primeira linha da nossa planilha mostra os filtros que foram usados ao extrair os dados do Power BI.
   
   ![](media/power-bi-visualization-export-data/power-bi-export-data7.png)
7. Agora experimente selecionar **Dados subjacentes** > **Exportar** e escolher .xlsx. O Power BI exporta os dados. Se você aplicou filtros à visualização, os dados serão exportados da maneira que foram filtrados. Ao selecionar **Exportar**, o navegador solicitará que você salve o arquivo. Após salvá-lo, abra o arquivo no Excel.
   
   >[!WARNING]
   >A exportação de dados subjacentes permite que os usuários vejam todos os dados detalhados – todas as colunas nos dados. Os administradores de serviço do Power BI podem desativar esse recurso para sua organização. Se for o proprietário de um conjunto de dados, você poderá definir colunas proprietárias como "ocultas" para que elas não apareçam na lista Campos no serviço do Power BI ou na área de trabalho.
   > 
   > 
   
   **Dados subjacentes**: selecione essa opção se a visualização tiver uma agregação e você desejar ver todos os detalhes subjacentes. Basicamente, selecionar *Dados subjacentes* remove a agregação. Ao selecionar **Exportar**, os dados são exportados para um arquivo .xlsx e o navegador solicita que você salve o arquivo. Após salvá-lo, abra o arquivo no Excel.
   
   Neste exemplo, a nossa exportação do Excel mostra uma linha para cada linha única de Cidade do nosso conjunto de dados e a porcentagem de desconto para aquela entrada única. Em outras palavras, os dados são nivelados e não agregados. A primeira linha da nossa planilha mostra os filtros que foram usados ao extrair os dados do Power BI.  
   
   ![](media/power-bi-visualization-export-data/power-bi-export-data8.png)

## <a name="limitations-and-considerations"></a>Limitações e considerações
* O número máximo de linhas que pode ser exportado do **Power BI Desktop** e do **serviço do Power BI** para .csv é 30.000.
* O número máximo de linhas que pode ser exportado para .xlsx durante o **serviço do Power BI** é 150.000 para usuários Pro e 30.000 para usuários gratuitos.
* Ao usar o DirectQuery, a quantidade máxima de dados que podem ser exportados é 16 MB. Isso pode resultar na exportação de um número de linhas menor que o máximo, especialmente se houver muitas colunas, dados que são difíceis de compactar e outros fatores que aumentam o tamanho do arquivo e diminuem o número de linhas exportadas.
* O Power BI dá suporte apenas à exportação em elementos visuais que utilizam agregações básicas. A exportação não está disponível em visuais que utilizam medidas de modelo ou de relatório.
* No momento, não há suporte para visuais personalizados e visuais do R.
* Exportar dados não está disponível para usuários fora da sua organização que estão usando um dashboard que foi compartilhado com eles. 
* Se forem usados caracteres Unicode no arquivo .csv, o texto no Excel poderá não ser exibido corretamente. Apesar disso, abri-lo no Bloco de Notas funcionará bem. Exemplos de caracteres Unicode são símbolos de moeda e palavras estrangeiras. A solução para isso é importar o csv para o Excel em vez de abri-lo diretamente. Para fazer isso:
  
  1. Abrir o Excel
  2. Na guia **Dados**, selecione **Obter dados externos** > **De texto**.
* Administradores do Power BI têm a capacidade de desabilitar a exportação de dados.

## <a name="next-steps"></a>Próximas etapas
[Dashboards no Power BI](service-dashboards.md)  
[Relatórios no Power BI](service-reports.md)  
[Power BI – conceitos básicos](service-basic-concepts.md)

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](http://community.powerbi.com/)

