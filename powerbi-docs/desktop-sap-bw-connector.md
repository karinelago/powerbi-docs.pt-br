---
title: Usar o Conector SAP BW no Power BI Desktop
description: Usar o Conector SAP BW no Power BI Desktop
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 04/09/2018
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 79fcd556827c0c5c34615021e45e3abfadfd50e2
ms.sourcegitcommit: 80d6b45eb84243e801b60b9038b9bff77c30d5c8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34288143"
---
# <a name="use-the-sap-bw-connector-in-power-bi-desktop"></a>Usar o Conector SAP BW no Power BI Desktop
Com o Power BI Desktop, você pode acessar os dados do **SAP BW (Business Warehouse)**.

Para saber mais sobre como os clientes da SAP podem se beneficiar conectando o Power BI aos sistemas SAP BW (Business Warehouse) existentes deles, veja o [white paper Power BI e SAP BW](https://aka.ms/powerbiandsapbw).

## <a name="installation-of-sap-bw-connector"></a>Instalação do Conector SAP BW
Para usar o **Conector do SAP BW**, siga as etapas de instalação a seguir:

1. Instale a biblioteca do **SAP NetWeaver** em seu computador local. É possível obter a biblioteca do **SAP Netweaver** do administrador do SAP ou diretamente do [Centro de Download de Software SAP](https://support.sap.com/swdc). Como o **Centro de Download de Software SAP** altera sua estrutura com frequência, não estão disponíveis diretrizes mais específicas para navegar nesse site. A biblioteca do **SAP NetWeaver** geralmente é incluída também na instalação do SAP Client Tools.
   
   Talvez seja possível pesquisar *SAP Note #1025361* para obter o local de download da versão mais recente. Verifique se a arquitetura da biblioteca **SAP NetWeaver** (32 bits ou 64 bits) corresponde a sua instalação do **Power BI Desktop** e instale todos os arquivos incluídos no **SDK do SAP NetWeaver RFC** de acordo com a Observação SAP.
2. A caixa de diálogo **Obter Dados** inclui uma entrada para o **Servidor de Aplicativos SAP Business Warehouse** e o **Servidor de Mensagens SAP Business Warehouse** na categoria **Banco de dados**.
   
   ![](media/desktop-sap-bw-connector/sap_bw_2a.png)

## <a name="sap-bw-connector-features"></a>Recursos do Conector SAP BW
Os **conectores do SAP BW** no Power BI Desktop permitem que você importe dados dos cubos do **Servidor SAP Business Warehouse** ou use o DirectQuery. 

Para saber mais sobre o **conector do SAP BW** e como usá-lo com DirectQuery, veja o artigo [DirectQuery e SAP BW (Business Warehouse)](desktop-directquery-sap-bw.md).

Para estabelecer a conexão, você deve especificar um *Servidor*, um *Número do Sistema* e uma *ID do Cliente*.

![](media/desktop-sap-bw-connector/sap_bw_3a.png)

Você também pode especificar duas **Opções avançadas** adicionais: Código de idioma e uma instrução MDX personalizada a ser executada em relação ao servidor especificado.

![](media/desktop-sap-bw-connector/sap_bw_4a.png)

Se nenhuma instrução MDX foi especificada, você vê a janela do **Navegador**, que exibe a lista de cubos disponíveis no servidor com a opção de fazer uma busca detalhada de itens dos cubos disponíveis, incluindo dimensões e medidas. O Power BI expõe consultas e cubos expostos pelos [BAPIs OLAP da Interface de Análise Aberta do BW](https://help.sap.com/saphelp_nw70/helpdata/en/d9/ed8c3c59021315e10000000a114084/content.htm).

Ao selecionar um ou mais itens do servidor, uma visualização da tabela de saída é criada, com base em sua seleção.

![](media/desktop-sap-bw-connector/sap_bw_5.png)

A janela do **Navegador** também fornece algumas **Opções de Exibição** que permitem fazer o seguinte:

* **Exibir *Somente Itens Selecionados* versus *Todos os Itens* (exibição padrão):** essa opção é útil para verificar o conjunto final de itens selecionados. Uma abordagem alternativa para exibir isso é selecionar os *Nomes de Coluna* na área *Visualização*.
* **Habilitar Visualizações de Dados (comportamento padrão):** também é possível controlar se as visualizações de dados devem ser exibidas neste diálogo. A desabilitação das visualizações de dados reduz a quantidade de chamadas do servidor, pois ele não solicita dados para as visualizações.
* **Nomes técnicos:** o SAP BW dá suporte ao conceito de *nomes técnicos* para objetos em um cubo. Os nomes técnicos permitem que um proprietário de cubo exponha nomes *amigáveis* para objetos do cubo, em vez de apenas expor os *nomes físicos* desses objetos no cubo.

![](media/desktop-sap-bw-connector/sap_bw_6.png)

Depois de selecionar todos os objetos necessários no **Navegador**, é possível decidir o que fazer em seguida selecionando um dos seguintes botões na parte inferior da janela do **Navegador**:

* A seleção de **Carga** dispara o carregamento de todo o conjunto de linhas para a tabela de saída no modelo de dados do Power BI Desktop e, em seguida, o leva para a visualização **Relatório**, em que é possível começar a visualizar dados ou fazer modificações adicionais usando as exibições de **Dados** ou **Relações**.
* A seleção de **Editar** mostra o **Editor de Consultas**, em que é possível executar a transformação de dados adicional e as etapas de filtragem antes que todo o conjunto de linhas seja colocado no modelo de dados do Power BI Desktop.

Além de importar dados de cubos do **SAP BW**, lembre-se de que também é possível importar dados de uma ampla variedade de fontes de dados no Power BI Desktop e combiná-los em um único relatório. Isso apresenta todos os tipos de cenários interessantes para relatórios e análises dos dados do **SAP BW**.

## <a name="troubleshooting"></a>Solução de problemas
Esta seção fornece situações de solução de problemas (e as respectivas soluções) para trabalhar com esta versão de preview do conector do **SAP BW**.

1. Dados numéricos do **SAP BW** retorna pontos decimais em vez de vírgulas. Por exemplo, 1,000,000 é retornado como 1.000.000.
   
   O **SAP BW** retorna dados decimais com uma *,* (vírgula) ou um *.* (ponto) como separador decimal. Para especificar quais desses **SAP BW** você deve usar como separador decimal, o driver usado pelo **Power BI Desktop** faz uma chamada para *BAPI_USER_GET_DETAIL*. Essa chamada retorna uma estrutura chamada **PADRÕES**, que tem um campo chamado *DCPFM* que armazena *Notação de Formato Decimal*. Um dos três valores a seguir é usado:
   
       ‘ ‘ (space) = Decimal point is comma: N.NNN,NN
       'X' = Decimal point is period: N,NNN.NN
       'Y' = Decimal point is N NNN NNN,NN
   
   Clientes que relataram esse problema descobriram que a chamada para *BAPI_USER_GET_DETAIL* falha para um usuário específico (o usuário que está mostrando dados incorretos), com uma mensagem de erro semelhante à seguinte:
   
       You are not authorized to display users in group TI:
           <item>
               <TYPE>E</TYPE>
               <ID>01</ID>
               <NUMBER>512</NUMBER>
               <MESSAGE>You are not authorized to display users in group TI</MESSAGE>
               <LOG_NO/>
               <LOG_MSG_NO>000000</LOG_MSG_NO>
               <MESSAGE_V1>TI</MESSAGE_V1>
               <MESSAGE_V2/>
               <MESSAGE_V3/>
               <MESSAGE_V4/>
               <PARAMETER/>
               <ROW>0</ROW>
               <FIELD>BNAME</FIELD>
               <SYSTEM>CLNTPW1400</SYSTEM>
           </item>
   
   Para resolver esse erro, os usuários devem solicitar ao administrador do SAP para conceder ao usuário SAPBW que está sendo usado no Power BI o direito de executar *BAPI_USER_GET_DETAIL*. Também vale a pena verificar se o usuário tem o valor *DCPFM* necessário, conforme descrito anteriormente nesta solução de problemas.
2. **Conectividade para consultas SAP BEx**
   
   É possível executar consultas **BEx** no Power BI Desktop habilitando uma propriedade específica, conforme mostrado na seguinte imagem:
   
   ![](media/desktop-sap-bw-connector/sap_bw_8.png)

## <a name="next-steps"></a>Próximas etapas
Para obter mais informações sobre SAP HANA e DirectQuery, confira os seguintes recursos:

* [DirectQuery e SAP HANA](desktop-directquery-sap-hana.md)
* [DirectQuery no Power BI](desktop-directquery-about.md)
* [Fontes de dados com suporte do DirectQuery](desktop-directquery-data-sources.md)
* [White paper Power BI e SAP BW](https://aka.ms/powerbiandsapbw)
