---
title: "Análise de Varejo de fornecedor para o Power BI: faça um tour"
description: "Análise de Varejo de fornecedor para o Power BI: faça um tour"
services: powerbi
documentationcenter: 
author: mihart
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
ms.date: 01/19/2018
ms.author: mihart
ms.openlocfilehash: d629788a5b64ec96b18340d8dd9da0ad4890f1aa
ms.sourcegitcommit: 1a5446c3136dc0787f2a1d5b8cad1113704301ba
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2018
---
# <a name="supplier-quality-analysis-sample-for-power-bi-take-a-tour"></a>Análise de Varejo de fornecedor para o Power BI: faça um tour

## <a name="a-brief-overview-of-the-supplier-quality-analysis-sample"></a>Uma breve visão geral do exemplo de Análise da Qualidade do Fornecedor
Este painel de exemplo do setor, e relatório subjacente, enfocam um dos desafios típicos da cadeia de fornecedores – análise de qualidade do fornecedor.
Duas métricas principais estão envolvidas na análise: o número total de defeitos e o tempo de inatividade total que causou esses defeitos. Este exemplo tem dois objetivos principais:

* Entender quem são os melhores e os piores fornecedores, com respeito à qualidade
* Identificar quais fábricas realizam um trabalho melhor em localizar e rejeitar defeitos, a fim de reduzir o tempo de inatividade

![](media/sample-supplier-quality/supplier1.png)

Este exemplo faz parte de uma série de exemplos que ilustra como o Power BI pode ser usado com dados, relatórios e painéis orientados aos negócios.
Os exemplos são dados reais de obviEnce ([www.obvience.com](http://www.obvience.com/)) que foram mantidos anônimos.

## <a name="prerequisites"></a>Pré-requisitos

 Antes de usar o exemplo, primeiro você deve baixá-lo como um pacote de conteúdo, arquivo .pbix ou pasta de trabalho do Excel.

### <a name="get-the-content-pack-for-this-sample"></a>Obter o pacote de conteúdo para este exemplo

1. Abra o serviço do Power BI (app.powerbi.com) e faça logon.
2. No canto inferior esquerdo, selecione **Obter dados**.
   
    ![](media/sample-datasets/power-bi-get-data.png)
3. Na página Obter Dados que aparece, selecione o ícone **Exemplos**.
   
   ![](media/sample-datasets/power-bi-samples-icon.png)
4. Selecione o **exemplo de Análise da Qualidade do Fornecedor** e, em seguida, escolha **Conectar**.  
  
   ![Exemplo de Análise de Qualidade do Fornecedor](media/sample-supplier-quality/supplier16.png)
   
5. O Power BI importa o pacote de conteúdo e adiciona um novo dashboard, um relatório e um conjunto de dados ao seu espaço de trabalho atual. O novo conteúdo é marcado com um asterisco amarelo. 
   
   ![Asterisco](media/sample-supplier-quality/supplier17.png)
  
### <a name="get-the-pbix-file-for-this-sample"></a>Obter o arquivo. pbix para este exemplo

Como alternativa, você pode baixar o exemplo como um arquivo .pbix, que é projetado para uso com o Power BI Desktop. 

 * [Exemplo de Análise de Qualidade do Fornecedor](http://download.microsoft.com/download/8/C/6/8C661638-C102-4C04-992E-9EA56A5D319B/Supplier-Quality-Analysis-Sample-PBIX.pbix)

### <a name="get-the-excel-workbook-for-this-sample"></a>Obter a pasta de trabalho do Excel para este exemplo
Também é possível [baixar apenas o conjunto de dados (pasta de trabalho do Excel)](http://go.microsoft.com/fwlink/?LinkId=529779) para este exemplo A pasta de trabalho contém planilhas do Power View que você pode exibir e modificar. Para ver os dados brutos, selecione **Power Pivot > Gerenciar**.


## <a name="downtime-caused-by-defective-materials"></a>Tempo de inatividade causado por materiais com defeito
Vamos analisar o tempo de inatividade causado por material defeituoso e ver quais fornecedores são responsáveis.  

1. No painel, selecione o título de número da **Quantidade Total de Defeito** ou o número de título **Total de minutos de inatividade** .  

   ![](media/sample-supplier-quality/supplier2.png)  

   O relatório "Exemplo de análise de qualidade do fornecedor" abre a página "Análise de tempo de inatividade". Observe que temos 33M total de peças com defeito, e o tempo de inatividade total causado por essas partes com defeito é 77K minutos. Alguns materiais têm menos peças com defeito, mas podem causar um atraso enorme, resultando em maior tempo de inatividade. Vamos explorá-los na página do relatório.  
2. Observando a linha **Total de minutos de inatividade** no gráfico de combinação **Defeitos e tempo de inatividade (min) por tipo de Material** , podemos ver materiais corrugados que causam a maior tempo de inatividade.  
3. Selecione a **Corrugado** no mesmo gráfico de combinação para ver quais fábrica têm impacto por esse defeito e qual fornecedor é responsável.  

   ![](media/sample-supplier-quality/supplier3.png)  
4. Selecione plantas individuais no mapa para ver quais fornecedores ou material é responsável por tempo de inatividade nessa fábrica.

### <a name="which-are-the-worst-suppliers"></a>Quais são os piores fornecedores?
 Queremos localizar os oito piores fornecedores e determinar qual é o percentual do tempo de inatividade que eles são responsáveis. Podemos fazer isso alterando o gráfico de área **Tempo de inatividade (min) por fornecedor** para um treemap.  

1. Na página 3 do relatório, "Análise de Inatividade", selecione **Editar relatório** no canto superior esquerdo.  
2. Selecione o gráfico de área **Tempo de inatividade (min) por fornecedor** e, no painel de visualizações, selecione Treemap.  

   ![](media/sample-supplier-quality/supplier4.png)  

    O Treemap automaticamente coloca o campo **Fornecedor** como o **grupo**.  

    ![](media/sample-supplier-quality/supplier5.png)  

   Nesse treemap, podemos ver quais são os oito principais fornecedores à esquerda o mapa de árvore. Também é possível observar que se responsabilizam por cerca de 50% de todos os minutos de inatividade.  
3. Selecione **Exemplo de Análise da Qualidade do Fornecedor** na barra de navegação superior para retornar ao dashboard.

### <a name="comparing-plants"></a>Comparando fábricas
Agora vamos explorar quais fábricas fazem um trabalho de melhor gerenciamento de material com defeito, resultando em menor tempo de inatividade.  

1. Selecione o título do mapa **Relatórios de defeito totais por fábrica, tipo de defeito** .  

    O relatório abre a página “Qualidade do Fornecedor”.  

   ![](media/sample-supplier-quality/supplier6.png)  
2. Na legenda do mapa, selecione o círculo **Impacto** .  

    ![](media/sample-supplier-quality/supplier7.png)  

    Observe no gráfico de bolha que a **Logística** é categoria mais problemática – é a maior em termos de quantidade total de defeito, relatórios de defeitos total e minutos de tempo de inatividade total. Vamos explorar mais essa categoria.  
3. Selecione a bolha de Logística no gráfico de bolhas e observa as fábricas em Springfield, IL e Naperville, IL. Naperville parece fazer um trabalho melhor de gerenciamento de fornecimentos com defeitos, uma vez tem um número alto de rejeição e alguns impactos, se comparado ao grande número de impactos de Springfield.  

   ![](media/sample-supplier-quality/supplier8.png)  
4. Selecione **Exemplo de Análise de Qualidade do Fornecedor** na barra de navegação superior para retornar ao espaço de trabalho ativo.

## <a name="which-material-type-is-best-managed"></a>Que tipo de material é melhor gerenciado?
O melhor tipo material gerenciado é aquele com o menor tempo de inatividade ou nenhum impacto, independentemente da quantidade de defeito.

* No painel, examine o bloco **Quantidade de Defeito Total pelo Tipo de Material, Tipo de Defeito**.

  ![](media/sample-supplier-quality/supplier9.png)

Observe que **Matérias-Primas** têm muitos defeitos totais, mas a maioria dos defeitos é rejeitada ou não tem um impacto.

Vamos verificar se as matérias-primas não causam muito tempo de inatividade, apesar da quantidade de defeito alta.

* No painel, examine o bloco **Quantidade de Defeito Total, Total de Minutos de Inatividade por tipo de Material**.

  ![](media/sample-supplier-quality/supplier10.png)

Aparentemente as matérias-primas são bem gerenciado: elas têm mais defeitos, mas menos minutos de inatividade total.

### <a name="compare-defects-to-downtime-by-year"></a>Comparar defeitos em tempo de inatividade por ano
1. Selecione a peça de mapa **Relatórios de defeito totais por fábrica, tipo de defeito** para abrir o relatório na primeira página, Qualidade do Fornecedor.
2. Observe que **Qtd de defeito** é maior em 2014 que em 2013.  

    ![](media/sample-supplier-quality/supplier11.png)  
3. Mais defeitos se traduz em mais tempo de inatividade? Podemos fazer perguntas na caixa de P e R para descobrir.  
4. Selecione **Exemplo de Análise da Qualidade do Fornecedor** na barra de navegação superior para retornar ao dashboard.  
5. Como sabemos que as matérias-primas têm o maior número de defeitos, na caixa pergunta, digite "Mostrar tipos de material, ano e quantidade total de defeito".  

    Havia muitos mais defeitos de matérias-primas em 2014 que em 2013.  

    ![](media/sample-supplier-quality/supplier12.png)  
6. Agora, altere a pergunta para "Mostrar tipos de material, ano e minutos de tempo de inatividade total".  

   ![](media/sample-supplier-quality/supplier13.png)

O tempo de inatividade de matérias-primas era quase o mesmo em 2013 e 2014, mesmo que houvesse muitos mais defeitos de matérias-primas do que em 2014.

Ocorre que mais matérias-primas com defeitos em 2014 não levou a mais tempo de inatividade no mesmo período.

### <a name="compare-defects-to-downtime-month-to-month"></a>Compare defeitos em tempo de inatividade mês a mês
Vejamos outro bloco de painel relacionado à quantidade total de defeito.  

1. Selecione a seta voltar ![](media/sample-supplier-quality/backarrow.png) no canto superior esquerdo acima da caixa de pergunta para retornar ao painel.  

    Olhando mais de perto o bloco **Quantidade Total de Defeitos por Mês, Anos** , mostra que o primeiro semestre de 2014 tinha um número semelhante de defeitos do que em 2013, mas no segundo semestre de 2014, o número de defeitos aumentou significativamente.  

    ![](media/sample-supplier-quality/supplier14.png)  

    Vamos ver se esse aumento na quantidade de defeito levou a um aumento igual em minutos do tempo de inatividade.  
2. Na caixa de pergunta, digite "minutos totais de inatividade por mês e ano como um gráfico de linha”.  

   ![](media/sample-supplier-quality/supplier15.png)

   Vemos um salto em minutos de inatividade durante junho e outubro, mas fora isso, o salto no número de defeitos não resulta em tempo de inatividade significantemente maior. Isso mostra que estamos gerenciando bem os defeitos.  
3. Para fixar este gráfico ao seu painel, selecione o ícone de pino ![](media/sample-supplier-quality/pin.png) à direita da caixa de pergunta.  
4. Para explorar os meses de exceções, verifique os minutos de tempo de inatividade durante outubro por tipo de material, introduzir local, categoria, etc., fazendo perguntas como "minutos de tempo de inatividade total em outubro pela fábrica".    
5. Selecione a seta voltar ![](media/sample-supplier-quality/backarrow.png) no canto superior esquerdo acima da caixa de pergunta para retornar ao painel.

Este é um ambiente seguro para experimentar. Você pode optar por não salvar as alterações. Mas se você salvá-las, sempre é possível acessar **Obter Dados** para ter uma nova cópia deste exemplo.

## <a name="next-steps-connect-to-your-data"></a>Próximas etapas: conectar-se aos seus dados
Esperamos que este tour tenha mostrado como os painéis, P e R e relatórios do Power BI podem fornecer informações sobre os dados de gastos na qualidade do fornecedor. Agora é sua vez - conecte-se aos seus próprios dados. Com o Power BI, é possível se conectar a uma grande variedade de fontes de dados. Saiba mais sobre como [começar a usar o Power BI](service-get-started.md)
