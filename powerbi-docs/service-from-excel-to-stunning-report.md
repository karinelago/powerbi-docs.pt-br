---
title: Da pasta de trabalho do Excel para um relatório incrível em um instante
description: Da pasta de trabalho do Excel para um relatório incrível em um instante
services: powerbi
documentationcenter: ''
author: mihart
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
ms.date: 02/28/2018
ms.author: mihart
LocalizationGroup: Data from files
ms.openlocfilehash: 849511476200d401432fdcc2ad88ec2930448bf9
ms.sourcegitcommit: 493f160d04ed411ff4741c599adc63ba1f65230f
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/07/2018
---
# <a name="from-excel-workbook-to-stunning-report-in-no-time"></a>Da pasta de trabalho do Excel para um relatório incrível em um instante
Sua gerente deseja ver um relatório sobre os números de vendas mais recentes combinado com as impressões da última campanha no final do dia. Porém, os dados mais recentes residem em vários sistemas de terceiros e em arquivos em seu laptop. Anteriormente, levava várias horas para criar visuais e formatar um relatório. Você está começando a ficar ansioso.

Não se preocupe. Com o Power BI, é possível criar um relatório impressionante em pouco tempo.

Neste exemplo, vamos carregar um arquivo do Excel de um sistema local, criar um novo relatório e compartilhá-lo com colegas – tudo no Power BI.

## <a name="prepare-your-data"></a>Preparar seus dados
Vamos tomar um arquivo simples do Excel como exemplo. Antes de carregar o arquivo do Excel no Power BI, você deve organizar seus dados em uma tabela simples. Isso significa que cada coluna contém o mesmo tipo de dados – por exemplo, texto, data, número ou moeda. Você deve ter uma linha de cabeçalho, mas não deve haver colunas ou linhas exibindo os totais.

![dados organizados em Excel](media/service-from-excel-to-stunning-report/pbi_excel_file.png)

Em seguida, formate os dados como uma tabela. No Excel, na guia Página Inicial, no grupo Estilos, selecione **Formatar como Tabela**. Selecione um estilo de tabela para aplicar à sua planilha. Sua planilha do Excel agora está pronta para ser carregada no Power BI.

![dados formatados como uma tabela](media/service-from-excel-to-stunning-report/pbi_excel_table.png)

## <a name="upload-your-excel-file-into-power-bi"></a>Carregar seu arquivo do Excel no Power BI
O Power BI se conecta a várias fontes de dados, incluindo arquivos do Excel que residem em seu computador. Para começar, entre no Power BI. Se você ainda não se inscreveu, [poderá fazê-lo gratuitamente](https://powerbi.com).

Você deseja criar um novo painel. Abra **Meu espaço de trabalho** e selecione o ícone **+ Criar**.

![Ícone Criar](media/service-from-excel-to-stunning-report/power-bi-new-dash.png)

Selecione **Dashboard**, insira um nome e selecione **Criar**. O novo dashboard é exibido, sem dados.

![Lista suspensa Criar](media/service-from-excel-to-stunning-report/power-bi-create-dash.png)

Na parte inferior do painel de navegação esquerdo, selecione **Obter Dados**. Na página Obter Dados, em Importar ou Conectar-se a Dados, na caixa Arquivos, selecione **Obter**.

![Obter dados de arquivos](media/service-from-excel-to-stunning-report/pbi_get_files.png)

Na página Arquivos, selecione **Arquivo Local**. Navegue até o arquivo de pasta de trabalho do Excel em seu computador e o selecione para carregar no Power BI. Selecione **Importar**.

> **OBSERVAÇÃO**: para acompanhar o restante deste tutorial, use a [Pasta de trabalho de exemplo financeiro](sample-financial-download.md).
> 
> 

![Janela Obter dados > Arquivos](media/service-from-excel-to-stunning-report/pbi_local_file.png)

## <a name="build-your-report"></a>Criar seu relatório
Depois que o Power BI importar seu arquivo do Excel, comece a criar seu relatório. Quando a mensagem **Seu conjunto de dados está pronto** for exibida, selecione **Exibir conjunto de dados**.  O Power BI abre no Modo de exibição de edição e exibe a tela do relatório. No lado direito estão os painéis Visualizações, Filtros e Campos.

Observe que os dados de tabela da pasta de trabalho do Excel aparecem no painel Campos. Abaixo do nome da tabela, o Power BI lista os cabeçalhos de coluna como campos individuais.

![aparência do Excel no painel Campos](media/service-from-excel-to-stunning-report/pbi_report_fields.png)

Agora você pode começar a criar visualizações. Sua gerente deseja ver o lucro ao longo do tempo. No painel Campos, arraste **Lucro** para a tela de relatório. Por padrão, o Power BI exibe um gráfico de barras. Em seguida, arraste **Data** à tela de relatório. O Power BI atualiza o gráfico de barras para mostrar o lucro por data.

![gráfico de colunas no editor de relatório](media/service-from-excel-to-stunning-report/pbi_report_pin-new.png)

> **Dica**: se o gráfico não tiver a aparência esperada, verifique suas agregações. Por exemplo, em **Valor**, clique com o botão direito do mouse no campo que você acabou de adicionar e verifique se os dados estão sendo agregados da maneira desejada.  Neste exemplo, estamos usando **Soma**.
> 
> 

Sua gerente deseja saber quais países são os mais lucrativos. Impressione-a com uma visualização de mapa. Selecione uma área em branco na tela e, no painel Campos, arraste-a sobre os campos **País** e **Lucro**. O Power BI cria um visual de mapa com bolhas que representam o lucro relativo de cada local.

![visual de mapa no editor de relatório](media/service-from-excel-to-stunning-report/pbi_report_map-new.png)

Que tal exibir um visual mostrando as vendas por produto e segmento de mercado? Isso é fácil. No painel Campos, selecione as caixas de seleção ao lado dos campos Vendas, Produto e Segmento. O Power BI cria um gráfico de barras instantaneamente. Altere o tipo de gráfico escolhendo um dos ícones no menu Visualizações. Por exemplo, altere-o para um gráfico de barras empilhadas.  Para classificar o gráfico, selecione as reticências (...) > **Classificar por**.

![gráfico de colunas empilhadas no editor de relatório](media/service-from-excel-to-stunning-report/pbi_barchart-new.png)

Fixe todos os visuais em seu Painel. Você está pronto para compartilhá-lo com seus colegas.

![painel com três visuais fixados](media/service-from-excel-to-stunning-report/pbi_report.png)

## <a name="share-your-dashboard"></a>Compartilhar seu painel
Você deseja compartilhar seu painel com sua gerente, Paula. Você pode compartilhar seu painel e o relatório subjacente com colegas que têm uma conta do Power BI. Eles podem interagir com seu relatório, mas não podem salvar as alterações.

Para compartilhar seu relatório, na parte superior do painel, selecione **Compartilhar**.

![Ícone Compartilhar](media/service-from-excel-to-stunning-report/power-bi-share.png)

O Power BI exibe a página Compartilhar Painel. Na área superior, digite os endereços de email dos destinatários. Adicione uma mensagem no campo abaixo. Para permitir que os destinatários compartilhem seu painel com outras pessoas, selecione **Permitir que os destinatários compartilhem seu painel**. Selecione **Compartilhar**.

![Janela Compartilhar dashboard](media/service-from-excel-to-stunning-report/power-bi-share-dash-new.png)

Próximas etapas

* [Introdução ao serviço do Power BI](service-get-started.md)
* [Introdução ao Power BI Desktop](desktop-getting-started.md)
* [Power BI – conceitos básicos](service-basic-concepts.md)
* Mais perguntas? [Experimente a Comunidade do Power BI](http://community.powerbi.com/)

