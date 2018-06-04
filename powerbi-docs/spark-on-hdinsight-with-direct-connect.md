---
title: Spark no HDInsight com DirectQuery
description: Spark no HDInsight com DirectQuery
author: markingmyname
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 06/28/2017
ms.author: maghan
LocalizationGroup: Data from databases
ms.openlocfilehash: 236a3d1bde84d4259d921d44730057a4e2fd3591
ms.sourcegitcommit: 80d6b45eb84243e801b60b9038b9bff77c30d5c8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34256738"
---
# <a name="spark-on-hdinsight-with-directquery"></a>Spark no HDInsight com DirectQuery
O Spark no Azure HDInsight com DirectQuery permite criar relatórios dinâmicos baseados nos dados e nas métricas que você já tem em seu cluster do Spark. Com o DirectQuery, as consultas são enviadas de volta para o cluster do Spark no HDInsight conforme você explora os dados na exibição do relatório. Essa experiência é sugerida para usuários que estão familiarizados com as entidades aos quais eles se conectam.

> [!WARNING]
> Atualização automática de bloco foi desabilitada para blocos de dashboard criados em conjuntos de dados com base no Spark. Você pode selecionar **Atualizar Blocos do Dashboard** para atualizar manualmente. Os relatórios não são afetados e devem permanecer atualizados. 
> 
> 

Você pode seguir as etapas abaixo para se conectar à sua fonte de dados Spark no Azure HDInsight usando o DirectQuery no serviço do Power BI.

1. Selecione **Obter Dados** na parte inferior do painel de navegação esquerdo.
   
     ![](media/spark-on-hdinsight-with-direct-connect/spark-getdata.png)
2. Selecione **Bancos de Dados e Mais**.
   
     ![](media/spark-on-hdinsight-with-direct-connect/spark-getdata-databases.png)
3. Selecione o conector **Spark no HDInsight** e escolha **Conectar**.
   
     ![](media/spark-on-hdinsight-with-direct-connect/spark-getdata-databases-connect.png)
4. Insira o nome do **servidor** que você deseja se conectar, bem como seu **nome de usuário** e **senha**. O servidor sempre está no formato \<clustername\>.azurehdinsight.net, veja mais detalhes sobre como localizar estes valores a seguir.
   
     ![](media/spark-on-hdinsight-with-direct-connect/spark-server-name.png)
   
     ![](media/spark-on-hdinsight-with-direct-connect/spark-username.png)
5. Uma vez conectado, você verá um novo conjunto de dados com o nome "SparkDataset". Você também pode acessar o conjunto de dados por meio do bloco de espaço reservado que é criado.
   
     ![](media/spark-on-hdinsight-with-direct-connect/spark-dataset.png)
6. Detalhando o conjunto de dados, você pode explorar todas as tabelas e colunas do banco de dados. Selecionar uma coluna resultará no envio de uma consulta de volta para a fonte, criando dinamicamente seu visual. Esses elementos visuais podem ser salvos em um novo relatório e fixados de volta em seu painel.

## <a name="finding-your-spark-on-hdinsight-parameters"></a>Localizando seus parâmetros do Spark no HDInsight
O servidor sempre está no formato \<clustername\>.azurehdinsight.net e pode ser encontrado no Portal do Azure.

![](media/spark-on-hdinsight-with-direct-connect/spark-server-name-parameter.png)

O nome de usuário e a senha também podem ser encontrados no Portal do Azure.

## <a name="limitations"></a>Limitações
Essas restrições e observações podem mudar conforme continuamos a aprimorar as experiências. Documentação adicional pode ser encontrada em [Usar ferramentas de BI com o Apache Spark no Azure HDInsight](https://azure.microsoft.com/documentation/articles/hdinsight-apache-spark-use-bi-tools/)

* O serviço do Power BI só dá suporte a uma configuração do Spark 2.0 e do HDInsight 3.5.
* Cada ação, como selecionar uma coluna ou adicionar um filtro, enviará uma consulta de volta para o banco de dados – antes de selecionar campos muito grandes, considere escolher um tipo adequado de visual.
* P e R não estão disponíveis para conjuntos de dados do DirectQuery.
* As alterações de esquema não são selecionadas automaticamente.
* O Power BI dá suporte para 16.000 colunas **em todas as tabelas** dentro de um conjunto de dados. O Power BI também inclui uma coluna de números de linhas internas por tabela. Isso significa que se você tiver 100 tabelas no conjunto de dados, o número de colunas disponíveis será de 15.900. Dependendo da quantidade de dados com os quais você estiver trabalhando na fonte de dados do Spark, você poderá encontrar essa limitação.

## <a name="troubleshooting"></a>Solução de problemas
Se estiver acessando problemas ao executar consultas em seu cluster, verifique se o aplicativo ainda está em execução e reinicie se necessário.

Você também pode alocar recursos adicionais no Portal do Azure em **Configuração** > **Cluster de Escala**:

![](media/spark-on-hdinsight-with-direct-connect/spark-scale.png)

## <a name="next-steps"></a>Próximas etapas
[Introdução: criar o cluster do Apache Spark no HDInsight Linux e executar consultas interativas usando o Spark SQL](https://azure.microsoft.com/documentation/articles/hdinsight-apache-spark-jupyter-spark-sql)  
[Introdução ao Power BI](service-get-started.md)  
[Obter dados para o Power BI](service-get-data.md)  
Mais perguntas? [Experimente a Comunidade do Power BI](http://community.powerbi.com/)

