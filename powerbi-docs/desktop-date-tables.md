---
title: Definir e usar tabelas de datas no Power BI Desktop
description: Saiba como definir uma tabela como uma tabela de datas e o que isso significa no Power BI Desktop
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 05/02/2018
ms.author: davidi
LocalizationGroup: Model your data
ms.openlocfilehash: f856b8fd0bc86f880a564e89ae86994fd7f1c602
ms.sourcegitcommit: 998b79c0dd46d0e5439888b83999945ed1809c94
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/17/2018
---
# <a name="set-and-use-date-tables-in-power-bi-desktop"></a>Definir e usar tabelas de datas no Power BI Desktop

O **Power BI Desktop** funciona nos bastidores para identificar automaticamente as tabelas como **tabelas de datas** e, em seguida, cria hierarquias de datas e outros metadados de habilitação para o seu modelo em seu nome. Você pode usar essas hierarquias internas ao criar recursos de relatório como elementos visuais, tabelas, medidas rápidas, segmentações de dados e assim por diante. O Power BI Desktop faz isso criando tabelas ocultas em seu nome, que você pode usar para seus relatórios e expressões DAX.

Muitos analistas de dados preferem criar suas próprias tabelas de datas, e isso é bom. No **Power BI Desktop**, você pode especificar a tabela que deseja que seu modelo use como sua **tabela de datas** e posteriormente criar elementos visuais relacionados a datas, tabelas, medidas rápidas e assim por diante usando dados de data dessa tabela. Quando você especifica sua própria tabela de datas, controla as hierarquias de datas criadas em seu modelo e usa-as em **medidas rápidas** e outras operações que usam a tabela de datas do seu modelo. 

![](media/desktop-date-tables/date-tables_01.png)

## <a name="setting-your-own-date-table"></a>Definindo sua própria tabela de datas

Para definir uma **tabela de datas**, selecione a tabela que você deseja usar como uma tabela de datas no painel **Campos**, em seguida, clique na tabela e selecione **Marcar como tabela de datas > Marcar como tabela de datas** no menu que aparece, conforme mostrado na imagem a seguir.

![](media/desktop-date-tables/date-tables_02.png)

Você também pode selecionar a tabela e, em seguida, selecionar **Marcar como tabela de datas** na faixa de opções **Modelagem** mostrada aqui.

![](media/desktop-date-tables/date-tables_02b.png)

Quando você especifica sua própria **tabela de datas**, o Power BI Desktop executa as validações a seguir dessa coluna e de seus dados, para garantir que os dados:

* contenham valores exclusivos
* não contenham valores nulos
* contenham valores de datas contíguas (do início ao fim)
* se for um tipo de dados **data/hora**, ele terá o mesmo carimbo de data e hora em cada valor

Há dois cenários prováveis para criar sua própria tabela de datas, ambos são abordagens razoáveis:

* O primeiro cenário é quando você usa uma tabela de datas básica ou canônica e hierarquia. Essa é uma tabela em seus dados que atende aos critérios de validação descritos anteriormente para uma tabela de datas. 

* O segundo cenário é onde você usa uma tabela do Analysis Services, por exemplo, com um campo *dim data* que você deseja usar como a tabela de datas. 

Depois que você especificar uma tabela de datas, poderá selecionar qual coluna nessa tabela é a coluna de datas. Você pode especificar qual coluna será usada selecionando a tabela no painel **Campos**, em seguida, clique com o botão direito na tabela e selecione **Marcar como tabela de datas > Configurações da tabela de datas**. A janela a seguir é exibida, onde você pode selecionar a coluna a ser usada como a tabela de datas na caixa da lista suspensa.

![](media/desktop-date-tables/date-tables_03.png)

É importante observar que, quando você especifica sua própria tabela de datas, o **Power BI Desktop** não cria automaticamente as hierarquias que seriam compiladas em seu modelo em seu nome. Se mais tarde você desmarcar sua tabela de datas (e não tiver uma tabela de datas definida manualmente), o Power BI Desktop recriará as tabelas de datas internas criadas automaticamente para você para as colunas de datas na tabela.

Também é importante a observar que, quando você marca uma tabela como uma tabela de datas, a tabela de datas interna (criada automaticamente) que o Power BI Desktop criou é removida e as expressões DAX e os visuais que você criou anteriormente com base nessas tabelas internas deixarão de funcionar corretamente. 

## <a name="marking-your-date-table-as-the-appropriate-data-type"></a>Marcando sua tabela de datas como o tipo de dados apropriado

Quando você especifica sua própria **tabela de datas**, precisa se garantir que o tipo de dados está definido corretamente. Para definir o **Tipo de dados** para **Data/Hora** ou **Data**. Realize as seguintes etapas:

1. Selecione a sua **tabela de datas** do painel **Campos**, expanda se for necessário e, em seguida, selecione a coluna a ser usada como a data.
   
    ![](media/desktop-date-tables/date-tables_04.png) 

2. Na guia **Modelagem**, selecione **Tipo de dados:** e, em seguida, clique na seta suspensa para mostrar os tipos de dados disponíveis.

    ![](media/desktop-date-tables/date-tables_05.png)

3. Especifique o tipo de dados para a coluna. 


## <a name="next-steps"></a>Próximas etapas

Você também pode estar interessado nos artigos a seguir.

* [Tipos de dados no Power BI Desktop](desktop-data-types.md)

 