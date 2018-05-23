---
title: Publicar no Power BI por meio do Excel 2016
description: Saiba como publicar uma pasta de trabalho do Excel em seu site do Power BI.
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 05/02/2018
ms.author: davidi
LocalizationGroup: Data from files
ms.openlocfilehash: aa2bfed2858f93d91ff806b934f16c06555668d6
ms.sourcegitcommit: 998b79c0dd46d0e5439888b83999945ed1809c94
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/17/2018
---
# <a name="publish-to-power-bi-from-excel-2016"></a>Publicar no Power BI por meio do Excel 2016
Com o Excel 2016, é possível publicar suas pastas de trabalho do Excel diretamente para o site do [Power BI](https://powerbi.microsoft.com), em que é possível criar relatórios e dashboards altamente interativos com base nos dados da pasta de trabalho. Em seguida, você pode compartilhar suas ideias com outras pessoas em sua organização.

Antes de continuarmos, há algumas considerações a serem feitas:

* Antes de publicar no Power BI, a pasta de trabalho deve ser salva no OneDrive for Business.
* A conta usada para entrar no Office, OneDrive for Business e Power BI deve ser a mesma.
* Não é possível publicar uma pasta de trabalho vazia nem uma pasta de trabalho que não tem um conteúdo para o qual há suporte do Power BI.
* Não é possível publicar pastas de trabalho criptografadas ou protegidas por senha nem pastas de trabalho com o Gerenciamento de Proteção de Informações.
* A publicação no Power BI exige a habilitação de uma autenticação moderna (padrão). Se estiver desabilitada, a opção Publicar não estará disponível no menu Arquivo.

## <a name="to-publish-your-excel-workbook"></a>Para publicar sua pasta de trabalho do Excel
No Excel, selecione **Arquivo** > **Publicar**.

### <a name="local-file-publishing"></a>Publicação de arquivo local
A partir da atualização de Fevereiro de 2017, o Excel 2016 dá suporte à publicação de arquivos locais do Excel. Eles não precisam ser salvos no OneDrive for Business ou no SharePoint Online.

> [!IMPORTANT]
> Apenas o Excel 2016 com uma assinatura do Office 365 oferecerá a experiência de publicar arquivos locais. A instalação autônoma do Excel 2016 ainda terá o comportamento de apenas "Publicar", que exige que a pasta de trabalho do Excel seja salva no OneDrive for Business ou no SharePoint Online.
> 
> 

Ao selecionar **Publicar**, você poderá selecionar o espaço de trabalho em que deseja publicar. Poderá ser o espaço de trabalho pessoal ou de grupo ao qual você tem acesso.

![](media/service-publish-from-excel/pbi_choose_workspace.png)

Você terá duas opções para colocar a pasta de trabalho no Power BI.

![](media/service-publish-from-excel/pbi_uploadexport3.png)

Após a publicação, ela será mantida como uma cópia no Power BI, separada do arquivo local. Se desejar atualizar o arquivo no Power BI, será necessário publicar a versão atualizada novamente. Você pode atualizar os dados e definir a atualização agendada na pasta de trabalho ou no conjunto de dados no Power BI.

### <a name="publishing-from-excel-standalone"></a>Publicando do Excel Autônomo
Se a pasta de trabalho ainda não estiver salva no OneDrive, você precisará salvá-la lá primeiro. Selecione Salvar na Nuvem e escolha um local no OneDrive for Business.

![](media/service-publish-from-excel/pbi_savetoonedrive2.png)

Depois que a pasta de trabalho for salva no OneDrive, ao selecionar **Publicar**, você terá duas opções para colocar a pasta de trabalho no Power BI.

![](media/service-publish-from-excel/pbi_uploadexport2.png)

#### <a name="upload-your-workbook-to-power-bi"></a>Carregar sua pasta de trabalho no Power BI
Ao escolher essa opção, sua pasta de trabalho será exibida no Power BI, exatamente como apareceria no Excel Online. Mas, ao contrário do Excel Online, você terá alguns ótimos recursos para ajudá-lo a fixar elementos de suas planilhas nos dashboards.

Você não pode editar a pasta de trabalho aberta no Power BI, mas se precisar fazer algumas alterações, você poderá selecionar **Editar** e, em seguida, escolher editar a pasta de trabalho no Excel Online ou abri-la no Excel do computador. Todas as alterações feitas são salvas na pasta de trabalho no OneDrive.

Assim que carregar, nenhum conjunto de dados será criado no Power BI. A pasta de trabalho será exibida em Relatórios, no painel de navegação do espaço de trabalho do Power BI. As pastas de trabalho carregadas no Power BI têm um ícone especial do Excel, que as identifica como pastas de trabalho do Excel carregadas.

Escolha esta opção se tiver apenas dados em planilhas ou se desejar ver Tabelas Dinâmicas e Gráficos no Power BI.
No Excel, usar Carregar do recurso Publicar no Power BI é praticamente o mesmo que usar Obter Dados > Arquivo > OneDrive for Business > Conectar, Gerenciar e Exibir o Excel no Power BI, do Power BI no navegador.

#### <a name="export-workbook-data-to-power-bi"></a>Exportar dados da pasta de trabalho para o Power BI
Ao escolher essa opção, todos os dados com suporte em tabelas e/ou em um modelo de dados são exportados para um novo conjunto de dados no Power BI. Caso você tenha planilhas do Power View, elas serão recriadas no Power BI como relatórios.

É possível continuar editando a pasta de trabalho. Quando as alterações forem salvas, elas serão sincronizadas com o conjunto de dados no Power BI, geralmente, em menos de uma hora. Se você precisa de resultados mais imediatos, basta selecionar Publicar novamente e as alterações serão exportadas imediatamente. Todas as visualizações contidas em relatórios e dashboards serão atualizadas também.

Escolha esta opção caso tenha usado o recurso Obter e Transformar dados ou o Power Pivot para carregar dados em um modelo de dados, ou se a pasta de trabalho tiver planilhas do Power View com visualizações que você deseja ver no Power BI.

No Excel, usar Exportar do recurso Publicar no Power BI é praticamente o mesmo que usar Obter Dados > Arquivo > OneDrive for Business > Exportar dados do Excel para o Power BI, do Power BI no navegador.

## <a name="publishing"></a>Publicando
Ao escolher uma dessas opções, o Excel entrará no Power BI com sua conta atual e publicará sua pasta de trabalho no site do Power BI. Fique de olho na barra de status do Excel. Ela mostra o progresso da atividade.

![](media/service-publish-from-excel/pbi_publishingstatus.png)

Ao concluir, é possível ir para o Power BI diretamente do Excel.

![](media/service-publish-from-excel/pbi_gotopbi.png)

## <a name="next-steps"></a>Próximas etapas
[Dados do Excel no Power BI](service-excel-workbook-files.md)  
Mais perguntas? [Experimente a Comunidade do Power BI](http://community.powerbi.com/)

