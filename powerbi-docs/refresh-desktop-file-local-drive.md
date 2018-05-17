---
title: Atualizar um conjunto de dados criado com base em um arquivo do Power BI Desktop – local
description: Atualizar um conjunto de dados criado com base em um arquivo do Power BI Desktop em uma unidade local
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
LocalizationGroup: Data refresh
ms.openlocfilehash: a1a94e19371a823a3686d44593ab48be62d87c03
ms.sourcegitcommit: f679c05d029ad0765976d530effde744eac23af5
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="refresh-a-dataset-created-from-a-power-bi-desktop-file-on-a-local-drive"></a>Atualizar um conjunto de dados criado com base em um arquivo do Power BI Desktop em uma unidade local
## <a name="whats-supported"></a>O que tem suporte?
No Power BI, há suporte para os recursos Atualizar Agora e Agendar Atualização para os conjuntos de dados criados por meio de arquivos do Power BI Desktop importados de uma unidade local em que Obter Dados ou o Editor de Consultas é usado para se conectar a qualquer uma das seguintes fontes de dados e carregar dados por meio de uma delas:

### <a name="power-bi-gateway---personal"></a>Gateway do Power BI - Pessoal
* Todas as fontes de dados online mostradas no Editor de Consultas e em Obter Dados no Power BI Desktop.
* Todas as fontes de dados locais mostradas no Editor de Consultas e em Obter Dados no Power BI Desktop, exceto o arquivo do Hadoop (HDFS) e o Microsoft Exchange.

<!-- Refresh Data sources-->
[!INCLUDE [refresh-datasources](./includes/refresh-datasources.md)]

> [!NOTE]
> Um gateway deve ser instalado e estar em execução para que o Power BI se conecte a fontes de dados locais e atualize o conjunto de dados.
> 
> 

É possível realizar uma única atualização manual diretamente no Power BI Desktop selecionando Atualizar na faixa de opções Início. Ao selecionar Atualização aqui, os dados no modelo *do arquivo* serão atualizados com dados atualizados da fonte de dados original. Esse tipo de atualização, feita totalmente no próprio aplicativo Power BI Desktop, é diferente da atualização manual ou agendada no Power BI, e é importante compreender a diferença entre elas.

![](media/refresh-desktop-file-local-drive/pbix-refresh.png)

Quando você importa o arquivo do Power BI Desktop de uma unidade local, os dados, juntamente com outras informações sobre o modelo, são carregados em um conjunto de dados no serviço do Power BI. No serviço do Power BI (não o Power BI Desktop), você deseja atualizar os dados no conjunto de dados, visto que são neles que os relatórios contidos no serviço do Power BI se baseiam. Como as fontes de dados são externas, é possível atualizar manualmente o conjunto de dados usando **Atualizar agora** ou configurar um agendamento de atualização usando **Agendar Atualização**.

Quando você atualiza o conjunto de dados, o Power BI não se conecta ao arquivo na unidade local para consultar e verificar se há dados atualizados. Ele usa informações do conjunto de dados para conectar diretamente às fontes de dados para consultar os dados atualizados e os carrega no conjunto de dados.

> [!NOTE]
> Esses dados atualizados no conjunto de dados não são sincronizados de volta com o arquivo na unidade local.
> 
> 

## <a name="how-do-i-schedule-refresh"></a>Como faço para agendar uma atualização?
Quando você configurar um agendamento de atualização, o Power BI se conectará diretamente às fontes de dados usando as informações de conexão e as credenciais no conjunto de dados para consultar os dados atualizados e, em seguida, carregará os dados atualizados no conjunto de dados. Todas as visualizações em relatórios e em dashboards baseadas nesse conjunto de dados no serviço do Power BI também são atualizadas.

Para obter detalhes sobre como configurar a atualização de agendamento, veja [Configurar uma atualização agendada](refresh-scheduled-refresh.md).

## <a name="when-things-go-wrong"></a>Quando algo dá errado
Quando as coisas dão errado, normalmente, isso se deve ao fato de o Power BI não conseguir entrar em fontes de dados. Outra razão é que se o conjunto de dados se conecta a uma fonte de dados local, o gateway fica offline. Verifique se o Power BI pode entrar em fontes de dados. Se uma senha que você usa para entrar em uma fonte de dados for alterada ou o Power BI for desconectado de uma fonte de dados, certifique-se de tentar entrar novamente em suas fontes de dados novamente nas Credenciais da Fonte de Dados.

Lembre-se de deixar a opção **Enviar email de notificação de falha de atualização para mim** marcada. Você desejará saber imediatamente de uma falha em uma atualização agendada.

## <a name="troubleshooting"></a>Solução de problemas
Às vezes, a atualização de dados pode não ocorrer da maneira esperada. Normalmente, isso será um problema relacionado a um gateway. Examine os artigos de solução de problemas do gateway para ver ferramentas e problemas conhecidos.

[Solução de problemas do gateway de dados local](service-gateway-onprem-tshoot.md)

[Solução de problemas do Gateway do Power BI – Pessoal](service-admin-troubleshooting-power-bi-personal-gateway.md)

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](http://community.powerbi.com/)

