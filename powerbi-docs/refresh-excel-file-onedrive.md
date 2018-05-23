---
title: Atualizar um conjunto de dados criado com base em uma pasta de trabalho do Excel – nuvem
description: Atualizar um conjunto de dados criado com base em uma pasta de trabalho do Excel no OneDrive ou SharePoint Online
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 05/02/2018
ms.author: davidi
LocalizationGroup: Data refresh
ms.openlocfilehash: b7a49a04ed344d6977dba5ac739c0f0d41aca5b9
ms.sourcegitcommit: 998b79c0dd46d0e5439888b83999945ed1809c94
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/17/2018
---
# <a name="refresh-a-dataset-created-from-an-excel-workbook-on-onedrive-or-sharepoint-online"></a>Atualizar um conjunto de dados criado com base em uma pasta de trabalho do Excel no OneDrive ou SharePoint Online
Você pode importar pastas de trabalho do Excel armazenadas no computador local ou no armazenamento em nuvem, como o OneDrive for Business ou o SharePoint Online. Vamos examinar as vantagens de usar o armazenamento em nuvem para os arquivos do Excel. Para obter mais informações sobre como importar arquivos do Excel no Power BI, consulte [Obter dados de arquivos de pasta de trabalho do Excel](service-excel-workbook-files.md).

## <a name="what-are-the-advantages"></a>Quais são as vantagens?
Importar arquivos do OneDrive ou SharePoint Online é uma ótima maneira de garantir que o trabalho que você está fazendo no Excel permaneça em sincronia com o serviço do Power BI. Todos os dados que você carregou no modelo do arquivo são importados no conjunto de dados e todos os relatórios que você criou no arquivo são carregados nos Relatórios do Power BI. Caso você faça alterações no arquivo do OneDrive ou SharePoint Online, como adicionar novas medidas, alterar nomes de coluna ou editar visualizações, depois de salvá-las, essas alterações também serão atualizadas no Power BI, normalmente, em menos de uma hora.

Quando você importa uma pasta de trabalho do Excel do OneDrive pessoal, todos os dados na pasta de trabalho, como tabelas em planilhas e/ou dados que são carregados no modelo de dados do Excel e a estrutura do modelo de dados, são importados para um novo conjunto de dados no Power BI. Quaisquer visualizações do Power View são recriadas em Relatórios. O Power BI conecta-se automaticamente à pasta de trabalho no OneDrive ou SharePoint Online em intervalos aproximados de sessenta minutos para verificar se há atualizações. Se a pasta de trabalho tiver sido alterada, o Power BI atualizará o conjunto de dados e os relatórios no serviço do Power BI.

É possível atualizar o conjunto de dados no serviço do Power BI. Quando você atualiza manualmente ou agenda a atualização no conjunto de dados, o Power BI conecta-se diretamente às fontes de dados externas para consultar os dados atualizados e os carrega no conjunto de dados. A atualização de um conjunto de dados no Power BI não atualiza os dados na pasta de trabalho no OneDrive ou SharePoint Online. 

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

## <a name="onedrive-or-onedrive-for-business-whats-the-difference"></a>OneDrive ou OneDrive for Business. Qual é a diferença?
Se você tiver um OneDrive Pessoal e um OneDrive para Empresas, é recomendável manter todos os arquivos que deseja importar no Power BI no OneDrive para Empresas. Eis o porquê: você provavelmente usa duas contas diferentes para entrar neles.

A conexão ao OneDrive para Empresas no Power BI é normalmente contínua, porque a mesma conta com a qual você usa para entrar no Power BI é geralmente a mesma conta usada para entrar no OneDrive para Empresas. Mas, com o OneDrive pessoal, você provavelmente entrará com outra [conta da Microsoft](http://www.microsoft.com/account/default.aspx).

Quando você entrar com sua conta da Microsoft, certifique-se de selecionar Mantenha-me conectado. O Power BI pode então sincronizar as atualizações feitas no arquivo do Power BI Desktop com conjuntos de dados no Power BI  
    ![](media/refresh-excel-file-onedrive/refresh_signin_keepmesignedin.png)

Se você fizer alterações no arquivo no OneDrive que não podem ser sincronizadas com o conjunto de dados ou os relatórios no Power BI devido à possibilidade de as suas credenciais de conta da Microsoft terem sido alteradas, você precisará se conectar e importar o arquivo novamente do seu OneDrive pessoal.

## <a name="options-for-connecting-to-excel-file"></a>Opções de conexão ao arquivo do Excel
Quando você se conecta a uma pasta de trabalho do Excel no OneDrive for Business ou SharePoint Online, você terá duas opções sobre como inserir o conteúdo de sua pasta de trabalho no Power BI.

[**Importar dados do Excel no Power BI**](service-excel-workbook-files.md#import-or-connect-to-an-excel-workbook-from-power-bi) – Ao importar uma pasta de trabalho do Excel por meio do OneDrive for Business ou SharePoint Online, ela funcionará da mesma forma que a descrita acima.

[**Conectar, gerenciar e exibir o Excel no Power BI**](service-excel-workbook-files.md#one-excel-workbook--two-ways-to-use-it) – Ao usar essa opção, você cria uma conexão do Power BI diretamente com sua pasta de trabalho no OneDrive for Business ou SharePoint Online.

Quando você se conecta a uma pasta de trabalho do Excel dessa forma, um conjunto de dados não é criado no Power BI. No entanto, a pasta de trabalho será exibida no serviço do Power BI em Relatórios com um ícone do Excel ao lado do nome. Ao contrário do Excel Online, quando você se conecta à sua pasta de trabalho do Power BI, se ela tiver conexões a fontes de dados externas que carregam dados no modelo de dados do Excel, será possível configurar um agendamento de atualização.

Quando você configura um agendamento de atualização dessa forma, a única diferença são que os dados atualizados são inseridos no modelo de dados da pasta de trabalho no OneDrive ou SharePoint Online, em vez de um conjunto de dados no Power BI.

## <a name="how-do-i-make-sure-data-is-loaded-to-the-excel-data-model"></a>Como ter certeza de que os dados são carregados no modelo de dados do Excel?
Quando você usa o Power Query (Obter e transformar dados no Excel 2016) para se conectar a uma fonte de dados, você tem várias opções de onde carregar os dados. Para se certificar de que você carrega os dados no modelo de dados, você deve selecionar a opção **Adicionar esses dados ao Modelo de Dados** na caixa de diálogo **Carregar Para** .

> [!NOTE]
> As imagens aqui mostram o Excel 2016.
> 
> 

Em **Navegador**, clique em **Carregar para...**  
    ![](media/refresh-excel-file-onedrive/refresh_loadtodm_1.png)

Ou então, se você clicar em **Editar** no Navegador, você abrirá o Editor de Consultas. Lá, é possível clicar em **Fechar e Carregar para...**  
    ![](media/refresh-excel-file-onedrive/refresh_loadtodm_2.png)

Em seguida, em **Carregar para**, certifique-se de que você selecionou **Adicionar esses dados ao Modelo de Dados**.  
    ![](media/refresh-excel-file-onedrive/refresh_loadtodm_3.png)

### <a name="what-if-i-use-get-external-data-in-power-pivot"></a>E se eu usar o recurso Obter Dados Externos no Power Pivot?
Sem problemas. Sempre que você usar o Power Pivot para se conectar e consultar dados de uma fonte de dados local ou online, os dados serão carregados automaticamente no modelo de dados.

## <a name="how-do-i-schedule-refresh"></a>Como faço para agendar uma atualização?
Quando você configurar um agendamento de atualização, o Power BI se conectará diretamente às fontes de dados usando as informações de conexão e as credenciais no conjunto de dados para consultar os dados atualizados e, em seguida, carregará os dados atualizados no conjunto de dados. Todas as visualizações em relatórios e em dashboards baseadas nesse conjunto de dados no serviço do Power BI também são atualizadas.

Para obter detalhes sobre como configurar a atualização de agendamento, veja [Configurar uma atualização agendada](refresh-scheduled-refresh.md).

## <a name="when-things-go-wrong"></a>Quando algo dá errado
Quando as coisas dão errado, normalmente, isso se deve ao fato de o Power BI não conseguir entrar em fontes de dados. Outra razão é que se o conjunto de dados se conecta a uma fonte de dados local, o gateway fica offline. Verifique se o Power BI pode entrar em fontes de dados. Se uma senha que você usa para entrar em uma fonte de dados for alterada ou o Power BI for desconectado de uma fonte de dados, certifique-se de tentar entrar novamente em suas fontes de dados novamente nas Credenciais da Fonte de Dados.

Lembre-se de deixar a opção **Enviar email de notificação de falha de atualização para mim marcada**. Você desejará saber imediatamente de uma falha em uma atualização agendada.

## <a name="important-notes"></a>Observações importantes
\*Não há suporte para a atualização de feeds OData conectados ao Power Pivot e consultados por meio dele. Ao usar um feed OData como uma fonte de dados, use o Power Query.

## <a name="troubleshooting"></a>Solução de problemas
Às vezes, a atualização de dados pode não ocorrer da maneira esperada. Normalmente, isso será um problema relacionado a um gateway. Examine os artigos de solução de problemas do gateway para ver ferramentas e problemas conhecidos.

[Solução de problemas do gateway de dados local](service-gateway-onprem-tshoot.md)

[Solução de problemas do Gateway do Power BI – Pessoal](service-admin-troubleshooting-power-bi-personal-gateway.md)

Mais perguntas? [Experimente a Comunidade do Power BI](http://community.powerbi.com/)

