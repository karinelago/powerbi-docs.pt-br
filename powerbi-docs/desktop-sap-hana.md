---
title: Usar o SAP HANA no Power BI Desktop
description: Usar o SAP HANA no Power BI Desktop
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 03/06/2018
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 44dff39d043bb7a71c01b5103cfdf65e7d5e33cb
ms.sourcegitcommit: 80d6b45eb84243e801b60b9038b9bff77c30d5c8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34287591"
---
# <a name="use-sap-hana-in-power-bi-desktop"></a>Usar o SAP HANA no Power BI Desktop
Com o Power BI Desktop, agora você pode acessar bancos de dados do **SAP HANA** . Para usar o **SAP HANA**, o driver ODBC do SAP HANA deve ser instalado no computador cliente local para que a conexão de dados do **SAP HANA** para o Power BI Desktop funcione corretamente. É possível baixar o driver ODBC do SAP HANA no [Centro de Download de Software SAP](https://support.sap.com/swdc). Estando nele, pesquise os computadores com Windows em SAP HANA CLIENT. Como o **Centro de Download de Software SAP** altera sua estrutura com frequência, não estão disponíveis diretrizes mais específicas para navegar nesse site.

Para se conectar a um banco de dados **SAP HANA**, selecione **Obter Dados > Banco de Dados > Banco de Dados SAP HANA**, conforme mostrado na imagem a seguir:

![](media/desktop-sap-hana/sap-hana-1.png)

Ao se conectar a um banco de dados do SAP HANA, especifique o nome do servidor e a porta no formato *servidor:porta* - a imagem a seguir mostra um exemplo com um servidor chamado *ServerXYZ* e a porta *30015*.

![](media/desktop-sap-hana/sap-hana-2.png)

Nesta versão, o **SAP HANA** no modo [DirectQuery](desktop-directquery-sap-hana.md) é compatível com o Power BI Desktop e no serviço do Power BI, e é possível publicar e carregar relatórios que usam o **SAP HANA** no modo DirectQuery no serviço do Power BI. Você também pode publicar e carregar relatórios no Serviço do Power BI quando não estiver usando o **SAP HANA** no modo DirectQuery.

### <a name="supported-features-for-sap-hana"></a>Recursos com suporte para o SAP HANA
Esta versão contém vários recursos para o **SAP HANA**, como mostrado na lista a seguir:

* O conector do Power BI para o **SAP HANA** usa o driver ODBC do SAP, para fornecer a melhor experiência de usuário
* O **SAP HANA** dá suporte às opções de Importação e do DirectQuery
* O Power BI é compatível com modelos de informação do HANA (tais como modos de exibição Analítico e Cálculo) e tem uma navegação otimizada
* Com o **SAP HANA**, você também pode usar o recurso direto do SQL para se conectar às Tabelas de Linhas e Colunas
* Inclui Navegação Otimizada para modelos do HANA
* O Power BI dá suporte a parâmetros de Variáveis e Entrada do **SAP HANA**

### <a name="installing-the-sap-hana-odbc-driver"></a>Instalando o driver ODBC do SAP HANA
### <a name="limitations-of-sap-hana"></a>Limitações do SAP HANA
Também há algumas limitações no uso do **SAP HANA**, conforme mostrado abaixo:

* Cadeias de caracteres NVARCHAR são truncadas para o comprimento máximo de 4.000 caracteres Unicode
* Não há suporte para SMALLDECIMAL
* Não há suporte para VARBINARY
* As Datas Válidas estão entre 30/12/1899 e 31/12/9999


## <a name="next-steps"></a>Próximas etapas
Para obter mais informações sobre o DirectQuery, confira os seguintes recursos:

* [DirectQuery e SAP HANA](desktop-directquery-sap-hana.md)
* [DirectQuery no Power BI](desktop-directquery-about.md)
* [Fontes de dados com suporte do DirectQuery](desktop-directquery-data-sources.md)

