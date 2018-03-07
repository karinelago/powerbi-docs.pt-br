---
title: Obter o Power BI Desktop
description: Baixar e instalar o Power BI Desktop
services: powerbi
documentationcenter: 
author: davidiseminger
manager: kfile
backup: 
editor: 
tags: 
qualityfocus: monitoring
qualitydate: 08/15/2017
ms.service: powerbi
ms.devlang: NA
ms.topic: get-started-article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 01/24/2018
ms.author: davidi
LocalizationGroup: Get started
ms.openlocfilehash: 0a0ffc46feadc5868b8e7a4bd273b7d8acc8bfb5
ms.sourcegitcommit: 88c8ba8dee4384ea7bff5cedcad67fce784d92b0
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/24/2018
---
# <a name="get-power-bi-desktop"></a>Obter o Power BI Desktop
O **Power BI Desktop** permite a criação de consultas, modelos e relatórios avançados que visualizam dados. Com o **Power BI Desktop**, você pode criar modelos de dados, criar relatórios e compartilhar seu trabalho publicando-o no serviço do Power BI.  **Power BI Desktop** é um download gratuito.

É possível obter o **Power BI Desktop** de duas maneiras e cada uma delas é descrita nas seções a seguir:

* **Download** direto (um pacote MSI baixado e instalado no seu computador)
* Instalação como aplicativo da **Windows Store**

Qualquer uma dessas abordagens instalarão a versão mais recente do **Power BI Desktop** no seu computador, mas há algumas diferenças dignas de nota, que serão descritas nas seções a seguir.

## <a name="download-power-bi-desktop"></a>Baixe o Power BI Desktop
Para baixar a versão mais recente do **Power BI Desktop**, você pode selecionar o ícone de download no canto superior direito do serviço do Power BI e selecionar **Power BI Desktop**.

![](media/desktop-get-the-desktop/getpbid_downloads.png)

Você também pode baixar a versão mais recente do Power BI Desktop da seguinte página de download:

* [**Download do Power BI Desktop** (ambas as versões de 32 e 64 bits)](https://powerbi.microsoft.com/desktop).
  
  [![](media/service-admin-power-bi-security/PBI_Security_01.png)](https://powerbi.microsoft.com/desktop)

Independentemente de qual modo você optar por baixar, quando o **Power BI Desktop** for baixado, você será solicitado a executar o arquivo de instalação:

![](media/desktop-get-the-desktop/getpbid_3.png)

O **Power BI Desktop** é instalado como um aplicativo e executado na sua área de trabalho.

![](media/desktop-get-the-desktop/designer_gsg_install.png)

> [!NOTE]
> A instalação da versão baixada (MSI) e a versão do **Windows Store** do **Power BI Desktop** no mesmo computador (às vezes conhecida como instalação *lado a lado*) não é compatível.
> 
> 

## <a name="install-as-an-app-from-the-windows-store"></a>Instalação como aplicativo da Windows Store
Também é possível obter o **Power BI Desktop** na Windows Store, por meio do link a seguir:

* [Instalar o **Power BI Desktop** da **Windows Store**](http://aka.ms/pbidesktopstore)

![](media/desktop-get-the-desktop/getpbid_04.png)

Há algumas vantagens em obter o **Power BI Desktop** na Windows Store:

* **Atualizações automáticas**: assim que disponível, o Windows baixa a versão mais recente automaticamente em segundo plano, de modo que a sua versão permaneça sempre atualizada.
* **Downloads menores**: a **Windows Store** garante que apenas os componentes alterados em cada atualização sejam baixados em seu computador, o que resulta em downloads menores para cada atualização.
* **Não é necessário ter privilégio de administrador**: ao baixar o MSI diretamente e instalá-lo, é necessário ser administrador para que a instalação seja concluída com êxito. Ao obter o **Power BI Desktop** na Windows Store, o privilégio de administrador *não* é necessário.
* **Disponibilização de TI habilitada**: a versão da **Windows Store** pode ser implantada, ou *disponibilizada*, mais facilmente para todos os membros da sua organização e pode disponibilizar o **Power BI Desktop** por meio da **Microsoft Store para Empresas**.
* **Detecção de idioma**: a versão da **Windows Store** inclui todos os idiomas com suporte e verifica quais deles estão sendo usados no computador toda vez que ele é iniciado. Isso também afeta a localização de modelos criados no **Power BI Desktop**. Por exemplo, hierarquias de datas internas corresponderão ao idioma que o **Power BI Desktop** estava usando quando o arquivo .pbix foi criado.

Há algumas considerações e limitações para instalar o **Power BI Desktop** da Windows Store, como:

* Se o conector SAP for utilizado, poderá ser necessário mover os arquivos do driver do SAP para a pasta *Windows\System32*.

> [!NOTE]
> A instalação da versão baixada (MSI) e a versão do **Windows Store** do **Power BI Desktop** no mesmo computador (às vezes conhecida como instalação *lado a lado*) não é compatível.
> 
> [!NOTE]
> A versão do Servidor de Relatórios do Power BI do **Power BI Desktop** é uma instalação separada e diferente das versões discutidas neste artigo. Para obter informações sobre a versão do Servidor de Relatórios do **Power BI Desktop**, consulte o artigo [Início rápido: criar um relatório do Power BI para o Servidor de Relatórios do Power BI](report-server/quickstart-create-powerbi-report.md).
> 
> 

## <a name="using-power-bi-desktop"></a>Usando o Power BI Desktop
Ao inicializar o **Power BI Desktop**, uma tela de *Boas-vindas* será exibida.

![](media/desktop-get-the-desktop/getpbid_05.png)

Se essa for sua primeira vez usando o **Power BI Desktop** (se a instalação não for uma atualização), será solicitado que você preencha um formulário e responda a algumas perguntas ou então que entre no **serviço do Power BI** antes que seja possível continuar.

Daí, você pode começar a criar relatórios ou modelos de dados e compartilhá-los com outros usuários no serviço do Power BI. Confira os links **Obter mais informações** no final deste artigo para links em guias que podem ajudá-lo a começar a usar **Power BI Desktop**.

## <a name="minimum-requirements"></a>Requisitos mínimos
A lista a seguir fornece os requisitos mínimos para executar o **Power BI Desktop**:

* Windows 7 / Windows Server 2008 R2 ou posterior
* .NET 4.5
* Internet Explorer 9 ou posterior
* **Memória (RAM):** ao menos 1 GB disponível, 1,5 GB ou mais, recomendado.
* **Tela:** ao menos 1440 x 900 ou 1600 x 900 (16:9) recomendado. Resoluções mais baixas, como 1024 x 768 ou 1280 x 800 não são recomendadas, pois determinados controles (como fechar a tela de inicialização) são exibidos além destas resoluções.
* **Configurações de vídeo do Windows:** se as configurações de vídeo forem definidas para alterar o tamanho do texto, dos aplicativos e de outros itens para mais de 100%, talvez você não consiga ver algumas caixas de diálogo que devem ser fechadas ou respondidas para continuar usando o **Power BI Desktop**. Caso tenha esse problema, verifique as **Configurações de vídeo** acessando **Configurações > Sistema > Vídeo** no Windows e use o controle deslizante para retornar as configurações de vídeo para 100%.
* **CPU:** processador de 1 gigahertz (GHz) ou mais rápido x86 - ou x64 bits recomendado.

## <a name="next-steps"></a>Próximas etapas
Depois que você instalar o **Power BI Desktop**, o conteúdo a seguir poderá ajudá-lo a colocar ele em funcionamento rapidamente:

* [Introdução ao Power BI Desktop](desktop-getting-started.md)
* [Visão geral de Consulta com o Power BI Desktop](desktop-query-overview.md)
* [Fontes de dados no Power BI Desktop](desktop-data-sources.md)
* [Conectar-se a dados no Power BI Desktop](desktop-connect-to-data.md)
* [Formatar e combinar dados com o Power BI Desktop](desktop-shape-and-combine-data.md)
* [Tarefas comuns de consulta no Power BI Desktop](desktop-common-query-tasks.md)   

