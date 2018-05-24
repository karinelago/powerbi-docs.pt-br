---
title: 'Exemplo de Análise de compras: faça um tour'
description: 'Exemplo de Análise de Varejo para o Power BI: faça um tour'
author: mihart
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 05/20/2018
ms.author: mihart
LocalizationGroup: Samples
ms.openlocfilehash: 0fee8ea43224f6b2b1d36886c7b8075716f89633
ms.sourcegitcommit: 2b9ef93bbff5c741ba55ea0502f642632683d593
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/24/2018
---
# <a name="procurement-analysis-sample-for-power-bi-take-a-tour"></a>Exemplo de Análise de Varejo para o Power BI: faça um tour

## <a name="overview-of-the-procurement-analysis-sample"></a>Visão geral do exemplo de Análise de Compras
Este painel de exemplo do setor e relatório subjacente analisam as despesas da empresa fabricante com fornecedores por categoria e local. No exemplo, exploraremos essas áreas:

* Quem são os principais fornecedores
* Em quais categorias ocorrem a maioria das despesas
* Quais fornecedores fornecem o desconto mais alto e quando

Este exemplo faz parte de uma série de exemplos que ilustra como o Power BI pode ser usado com dados, relatórios e painéis orientados aos negócios. Os exemplos são dados reais de obviEnce ([www.obvience.com)](http://www.obvience.com/) que foram mantidos anônimos.

![](media/sample-procurement/procurement1.png)

## <a name="prerequisites"></a>Pré-requisitos

 Antes de usar o exemplo, primeiro você deve baixá-lo como um [pacote de conteúdo](https://docs.microsoft.com/en-us/power-bi/sample-procurement#get-the-content-pack-for-this-sample), [arquivo .pbix](http://download.microsoft.com/download/D/5/3/D5390069-F723-413B-8D27-5888500516EB/Procurement-Analysis-Sample-PBIX.pbix) ou [pasta de trabalho do Excel](http://go.microsoft.com/fwlink/?LinkId=529784).

### <a name="get-the-content-pack-for-this-sample"></a>Obter o pacote de conteúdo para este exemplo

1. Abra o serviço do Power BI (app.powerbi.com) e faça logon.
2. No canto inferior esquerdo, selecione **Obter dados**.
   
    ![](media/sample-datasets/power-bi-get-data.png)
3. Na página Obter Dados que aparece, selecione o ícone **Exemplos**.
   
   ![](media/sample-datasets/power-bi-samples-icon.png)
4. Selecione o **exemplo de Análise de Compras** e, em seguida, escolha **Conectar**.  
  
   ![Obter dados](media/sample-procurement/procurement1a.png)
   
5. O Power BI importa o pacote de conteúdo e adiciona um novo dashboard, um relatório e um conjunto de dados ao seu espaço de trabalho atual. O novo conteúdo é marcado com um asterisco amarelo. 
   
   ![Asterisco](media/sample-procurement/procurement1b.png)
  
### <a name="get-the-pbix-file-for-this-sample"></a>Obter o arquivo. pbix para este exemplo

Como alternativa, você pode baixar o exemplo como um arquivo .pbix, que é projetado para uso com o Power BI Desktop. 

 * [Exemplo de Análise de Compras](http://download.microsoft.com/download/D/5/3/D5390069-F723-413B-8D27-5888500516EB/Procurement%20Analysis%20Sample%20PBIX.pbix)

### <a name="get-the-excel-workbook-for-this-sample"></a>Obter a pasta de trabalho do Excel para este exemplo
Também é possível [baixar apenas o conjunto de dados (pasta de trabalho do Excel)](http://go.microsoft.com/fwlink/?LinkId=529784) para este exemplo A pasta de trabalho contém planilhas do Power View que você pode exibir e modificar. Para ver os dados brutos, selecione **Power Pivot > Gerenciar**.


## <a name="spending-trends"></a>Tendências de gastos
Primeiro, vamos analisar as tendências em gastos por categoria e local.  

1. Em seu espaço de trabalho, abra a guia **Dashboards** e selecione o dashboard de Análise de Compras.
2. Selecione o bloco do painel **Total da nota fiscal por país/região**. Abre a página "Visão Geral de Gasto" do relatório "Exemplo de análise de compras".

    ![](media/sample-procurement/procurement2.png)

Observe algumas coisas:

* No gráfico de linhas **Total da fatura por mês e categoria** : a categoria **Direto** apresenta gastos bem consistentes, **Logística** apresenta um pico em dezembro e **Outros** demonstra um pico em fevereiro.
* No mapa **Total da fatura por país/região** : a maioria de nossos gastos está concentrada nos EUA.
* No gráfico de colunas **Total da fatura por subcategoria**: **Hardware** e **Serviços e produtos indiretos** são as categorias que apresentam os maiores gastos.
* No gráfico de barras Total da fatura por camada: a maioria de nossos negócios é feita com nossos fornecedores da Camada 1 (os 10 primeiros). Isso ajuda a gerenciar melhor os relacionamentos com o fornecedor.

## <a name="spending-in-mexico"></a>Gastos no México
Vamos explorar as áreas de gastos no México.

1. No gráfico de pizza, selecione a bolha do **México** no mapa. Observe que, no gráfico de colunas “Total da fatura por subcategoria”, a maior parte dos gastos está concentrada na subcategoria **Serviços e produtos indiretos**.

   ![](media/sample-procurement/pbi_procsample_spendmexico.png)
2. Faça uma busca detalhada na coluna **Serviços e produtos indiretos**:

   * Selecione a seta de busca detalhada ![](media/sample-procurement/pbi_drilldown_icon.png) no canto superior direito do gráfico.
   * Selecione a coluna **Serviços e produtos indiretos**.

      Por uma grande margem de diferença, os maiores gastos nesta categoria geral são os de Vendas e marketing.
   * Selecione **México** no mapa novamente.

      Os maiores gastos nessa categoria no México são os de Manutenção e reparo.

      ![](media/sample-procurement/pbi_procsample_drill_mexico.png)
3. Selecione a seta para cima no canto superior esquerdo do gráfico para fazer drill up.
4. Selecione a seta novamente para desativar os detalhes.  
5. Selecione **Power BI** na barra de navegação superior para retornar ao seu espaço de trabalho.

## <a name="evaluate-different-cities"></a>Avaliar cidades diferentes
Podemos usar o realce para avaliar cidades diferentes.

1. Selecione o bloco do painel **Total da nota fiscal, % de desconto por mês**. O relatório é aberto para a página de "Análise de desconto".
2. Selecione as cidades diferentes no mapa de árvore **Total da fatura por cidade** para ver uma comparação delas. Quase todas as faturas de Miami são provenientes de fornecedores da Camada 1.

   ![](media/sample-procurement/pbi_procsample_miamitreemap2.png)

## <a name="vendor-discounts"></a>Descontos de fornecedor
Também vamos explorar os descontos disponíveis de fornecedores e os períodos de tempo quando chegarmos a maioria dos descontos.

![](media/sample-procurement/procurement4.png)

Especificamente, estas perguntas:

* Os descontos são diferentes ou iguais a cada mês?
* Algumas cidades obtêm mais descontos do que outras?

### <a name="discount-by-month"></a>Desconto por mês
Observando o gráfico de combinação **Total da fatura e % de desconto por mês** , podemos ver que **Fevereiro** é o mês mais movimentado e que **Setembro** , o menos movimentado. Agora examine a porcentagem de desconto durante esses meses.
Observe que quando o volume aumenta, o desconto é reduzido e quando o volume está baixo, o desconto aumenta. Quanto mais precisarmos de desconto, a negociação é pior.

![](media/sample-procurement/procurement5.png)

### <a name="discount-by-city"></a>Desconto por cidade
Outra área para explorar é desconto por cidade. Selecione cada cidade no mapa de árvore e veja como os outros gráficos são alterados.

* St. Louis, MO tinha um grande aumento no total da nota fiscal em fevereiro e uma grande diminuição de economia de desconto em abril.
* Cidade do México no México tem a maior porcentagem de desconto (% 11,05) e Atlanta, GA tem a menor (% 0,08).

![](media/sample-procurement/procurement6.png)

### <a name="edit-the-report"></a>Editar o relatório
Selecione **Editar relatório** no canto superior esquerdo e explore no Modo de Exibição de Edição.

* Veja como as páginas são criadas
* Adicionar páginas e gráficos com base nos mesmos dados
* Alterar o tipo de visualização de um gráfico – por exemplo, alterar o mapa de árvore para um gráfico de rosca
* Fixá-los no dashboard

Este é um ambiente seguro para experimentar. Você pode optar por não salvar as alterações. Se você salvá-las, sempre é possível acessar **Obter Dados** para obter uma nova cópia desse exemplo.

## <a name="next-steps-connect-to-your-data"></a>Próximas etapas: conectar-se aos seus dados
Esperamos que esse tour tenha mostrado como os painéis e relatórios do Power BI podem fornecer informações sobre os dados de compras. Agora é sua vez &#151; conecte-se aos seus próprios dados. Com o Power BI, é possível se conectar a uma grande variedade de fontes de dados. Saiba mais sobre como [começar a usar o Power BI](service-get-started.md)
