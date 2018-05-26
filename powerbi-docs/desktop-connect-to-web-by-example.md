---
title: Extrair dados de uma página da Web por exemplo no Power BI Desktop (versão prévia)
description: Extraia dados de uma página da Web fornecendo um exemplo dos dados dos quais deseja efetuar pull
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
ms.date: 05/07/2018
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 3d67d9737ff09e3d5959ab24e615473f537654ab
ms.sourcegitcommit: 509be8852ba7595b9441c9479224f9dca298b26d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/09/2018
---
# <a name="get-data-from-a-web-page-by-providing-an-example-preview"></a>Obtenha dados de uma página da Web fornecendo um exemplo (versão prévia)

Obter dados de uma página da Web permite que os usuários extraiam facilmente dados de páginas da Web e importem esses dados para o **Power BI Desktop**. No entanto, normalmente os dados em páginas da Web não estão em tabelas organizadas fáceis de extrair, portanto, obter dados dessas páginas – mesmo que eles sejam estruturados e consistentes – pode ser um desafio. 

Há uma solução. Com o recurso **Obter dados da Web por exemplo**, você pode, essencialmente, mostrar ao **Power BI Desktop** quais dados deseja extrair fornecendo um ou mais exemplos com a caixa de diálogo do conector e ele coletará outros dados na página que correspondem a seus exemplos. Com essa solução, você pode extrair todos os tipos de dados de páginas da Web, incluindo dados encontrados em tabelas *e* outros dados fora delas. 

![Obter dados da Web por exemplo](media/desktop-connect-to-web-by-example/web-by-example_01.png)


## <a name="enabling-the-preview-feature-get-data-from-web-by-example"></a>Habilitando o recurso de visualização Obter Dados da Web por exemplo

O recurso **Obter dados da Web por exemplo** está em versão prévia e precisa ser habilitado no **Power BI Desktop**. Para habilitá-lo, selecione **Arquivo > Opções e Configurações > Opções > Recursos de Visualização** e marque a caixa de seleção **Experiência Novo da Web**. Você precisará reiniciar o Power BI Desktop depois de fazer a seleção.

![Habilitar o recurso de visualização](media/desktop-connect-to-web-by-example/web-by-example_02.png)

Quando o recurso de visualização estiver habilitado, você poderá começar a usá-lo. 

## <a name="using-get-data-from-web-by-example"></a>Usando Obter dados da Web por exemplo

Para usar **Obter dados da Web por exemplo**, selecione **Obter Dados** no menu de faixa de opções **Início**. Na janela que aparece, selecione **Outros** nas categorias no painel esquerdo e, em seguida, selecione **Web**.

![Selecionar Web em Obter Dados](media/desktop-connect-to-web-by-example/web-by-example_03.png)

Aí, insira a URL da página da Web da qual você deseja extrair dados. Neste artigo, usaremos a página da Web da Microsoft Store e mostraremos como esse conector funciona. 

Se quiser acompanhar, você poderá usar a [URL da Microsoft Store](https://www.microsoft.com/en-us/store/top-paid/games/xbox?category=classics) que usamos neste artigo:

    https://www.microsoft.com/en-us/store/top-paid/games/xbox?category=classics

![Caixa de diálogo da Web](media/desktop-connect-to-web-by-example/web-by-example_04.png)

Quando selecionar **OK**, você será levado à caixa de diálogo **Navegador**, em que qualquer tabela detectada automaticamente da página da Web será apresentada. No caso de mostrado na imagem abaixo, nenhuma tabela foi encontrada, mas há um botão na parte inferior da página chamado **Extrair a tabela usando exemplos** que permite fornecer exemplos.


![Janela do Navegador](media/desktop-connect-to-web-by-example/web-by-example_05.png)

Selecionar **Extrair a tabela usando exemplos** apresenta uma janela interativa em que você pode visualizar o conteúdo da página da Web e digitar os valores de exemplo dos dados que deseja extrair. 

Neste exemplo, extrairemos o *Nome* e o *Preço* de cada um dos jogos na página. Podemos pode fazer isso especificando dois exemplos da página para cada coluna, conforme mostrado na imagem a seguir. Conforme esses exemplos são digitados, o **Power Query** (que é a tecnologia subjacente que extrai os dados da página da Web) é capaz de extrair os dados que correspondem ao padrão de entradas de exemplo usando algoritmos de extração de dados inteligente.

![dados por exemplo](media/desktop-connect-to-web-by-example/web-by-example_06.png)

Quando ficamos satisfeitos com os dados extraídos da página da Web, selecionamos **OK** para ir para o **Editor de Consultas**, no qual podemos aplicar mais transformações ou formatar os dados, como combinar esses dados com outros dados ou fontes.

![dados por exemplo](media/desktop-connect-to-web-by-example/web-by-example_07.png)

Aí, você pode criar visuais ou usar os dados da página da Web ao criar seus relatórios do **Power BI Desktop**.


## <a name="next-steps"></a>Próximas etapas
Há muitos tipos de dados aos quais você pode se conectar usando o **Power BI Desktop**. Para obter mais informações sobre fontes de dados, confira os seguintes recursos:

* [Adicionar coluna por exemplo](desktop-add-column-from-example.md)
* [Conectar-se a uma página da Web](desktop-connect-to-web.md)
* [Fontes de dados no Power BI Desktop](desktop-data-sources.md)
* [Formatar e combinar dados com o Power BI Desktop](desktop-shape-and-combine-data.md)
* [Conectar-se a pastas de trabalho do Excel no Power BI Desktop](desktop-connect-excel.md)   
* [Conectar-se a arquivos CSV no Power BI Desktop](desktop-connect-csv.md)   
* [Inserir dados diretamente no Power BI Desktop](desktop-enter-data-directly-into-desktop.md)   

