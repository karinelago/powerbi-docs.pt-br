---
title: Executando scripts do R no Power BI Desktop
description: Executando scripts do R no Power BI Desktop
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 05/02/2018
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: acadd84fbd8d0cf7f44b23362474d08608107f24
ms.sourcegitcommit: 638de55f996d177063561b36d95c8c71ea7af3ed
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/17/2018
---
# <a name="run-r-scripts-in-power-bi-desktop"></a>Executar scripts do R no Power BI Desktop
É possível executar scripts do R diretamente no **Power BI Desktop** e importar os conjuntos de dados resultantes para um modelo de dados do Power BI Desktop.

## <a name="install-r"></a>Instalar o R
Para executar scripts do R no Power BI Desktop, você precisa instalar o **R** em seu computador local. É possível baixar e instalar o **R** gratuitamente em vários locais, incluindo a [página de download do Revolution Open](https://mran.revolutionanalytics.com/download/) e o [Repositório CRAN](https://cran.r-project.org/bin/windows/base/). A versão atual do script R no Power BI Desktop dá suporte a caracteres Unicode, bem como espaços (caracteres vazios) no caminho de instalação.

## <a name="run-r-scripts"></a>Executar scripts do R
Com apenas algumas etapas no Power BI Desktop, é possível executar scripts do R e criar um modelo de dados, por meio do qual você pode criar relatórios e compartilhá-los no serviço do Power BI. O script R no Power BI Desktop agora dá suporte a formatos de número que contêm decimais (.) e vírgulas (,).

### <a name="prepare-an-r-script"></a>Preparar um script do R
Para executar um script do R no Power BI Desktop, crie o script em seu ambiente de desenvolvimento local do R e certifique-se de que ele é executado com êxito.

Para executar o script no Power BI Desktop, verifique se o script é executado com êxito em um espaço de trabalho novo e modificado. Isso significa que todos os pacotes e dependências devem ser explicitamente carregados e executados. Você pode usar *source()* para executar scripts dependentes.

Ao preparar e executar um script R no Power BI Desktop, existem algumas limitações:

* Somente os quadros de dados são importados, portanto, tenha certeza de que os dados que você deseja importar para o Power BI são representados em um quadro de dados
* Colunas tipadas como Complexas e Vetoriais não são importadas e são substituídas por valores de erro na tabela criada
* Valores que são N/D são convertidos em valores NULL no Power BI Desktop
* Qualquer script R que é executado por mais de 30 minutos expira
* Chamadas interativas no script R, como aguardar a entrada do usuário, interrompem a execução do script
* Ao definir o diretório de trabalho dentro do script R, é *necessário* definir um caminho completo para o diretório de trabalho, em vez de um caminho relativo

### <a name="run-your-r-script-and-import-data"></a>Executar o script do R e importar dados
1. No Power BI Desktop, o conector de dados de Script do R é encontrado em **Obter Dados**. Para executar o Script R, selecione **Obter Dados &gt; Mais...** e, em seguida, selecione **Outros &gt; Script R**, como mostrado na imagem a seguir:
   
   ![](media/desktop-r-scripts/r-scripts-1.png)
2. Se o R estiver instalado no computador local, a versão mais recente instalada será selecionada como o mecanismo do R. Basta copiar o script na janela de script e selecionar **OK**.
   
   ![](media/desktop-r-scripts/r-scripts-2.png)
3. Se o R não estiver instalado, não for identificado ou se houver várias instalações no computador local, expanda **Configurações de Instalação do R** para exibir as opções de instalação ou para selecionar em qual instalação você deseja executar o script do R.
   
   ![](media/desktop-r-scripts/r-scripts-3.png)
   
   Se o R estiver instalado e não for identificado, será possível fornecer explicitamente seu local na caixa de texto fornecida ao expandir **Configurações de Instalação do R**. Na imagem acima, o caminho *C:\Arquivos de Programas\R\R-3.2.0* é explicitamente fornecido na caixa de texto.
   
   As configurações de instalação do R estão localizadas centralmente na seção Script R do diálogo Opções. Para especificar as configurações de instalação do R, selecione **Arquivo > Opções e configurações** e, em seguida, **Opções > Script R**. Se houver várias instalações do R disponíveis, será exibido um menu suspenso que permite selecionar qual instalação será usada.
   
   ![](media/desktop-r-scripts/r-scripts-4.png)
4. Selecione **OK** para executar o script do R. Quando o script é executado com êxito, você pode escolher os quadros de dados resultantes para adicionar ao modelo do Power BI.

### <a name="refresh"></a>Atualizar
É possível atualizar um script do R no Power BI Desktop. Quando você atualiza um script do R, o Power BI Desktop o executa novamente no ambiente do Power BI Desktop.

## <a name="next-steps"></a>Próximas etapas
Analise as informações adicionais a seguir sobre o R no Power BI.

* [Criar visuais R no Power BI Desktop](desktop-r-visuals.md)
* [Usar um IDE R externo com o Power BI](desktop-r-ide.md)

