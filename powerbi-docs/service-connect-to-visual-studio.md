---
title: Conectar-se ao Visual Studio Team Services com o Power BI
description: Visual Studio Team Services para o Power BI
services: powerbi
documentationcenter: 
author: joeshoukry
manager: kfile
backup: maggiesMSFT
editor: 
tags: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 10/16/2017
ms.author: yshoukry
ms.openlocfilehash: 20ea9117cf1eee3d7b05be21e5964226349a58c1
ms.sourcegitcommit: 284b09d579d601e754a05fba2a4025723724f8eb
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/15/2017
---
# <a name="connect-to-visual-studio-team-services-with-power-bi"></a>Conectar-se ao Visual Studio Team Services com o Power BI
Use o pacote de conteúdo do Visual Studio Team Services para o Power BI para obter informações sobre seus projetos de equipe TFVC e Git. Depois de estabelecer uma conexão, seus dados são enviados a você automaticamente em um painel e em relatórios. 

Conecte-se ao [pacote de conteúdo do Visual Studio Team Services](https://app.powerbi.com/getdata/services/visual-studio-online) ou leia mais sobre a [integração do Visual Studio Team Services](https://powerbi.microsoft.com/integrations/visual_studio_online) com o Power BI.

>[!NOTE]
>Esse pacote de conteúdo exige acesso a uma conta que tenha o OAuth habilitado. Mais detalhes sobre os requisitos abaixo.

## <a name="how-to-connect"></a>Como se conectar
1. Selecione **Obter Dados** na parte inferior do painel de navegação esquerdo.  
   ![](media/service-connect-to-visual-studio/pbi_getdata.png) 
2. Na caixa **Serviços** , selecione **Obter**.  
   ![](media/service-connect-to-visual-studio/pbi_getservices.png) 
3. Selecione o pacote de conteúdo do **Visual Studio Team Services** e clique em **Obter**.     
   ![](media/service-connect-to-visual-studio/vsts.png)
4. Insira informações sobre sua conta do Visual Studio Team Services. Veja detalhes sobre [como encontrar esses parâmetros](#FindingParams) abaixo.
   
   ![](media/service-connect-to-visual-studio/pbi_vsosignin.png)
   
   O nome da conta é a parte inicial da URL do visualstudio.com:    
   ![](media/service-connect-to-visual-studio/urlimage.png)
   
   O nome do projeto é o nome exibido na parte superior de cada página no Visual Studio Team Services:  
   ![](media/service-connect-to-visual-studio/projectimage.png)
5. Faça a autenticação com o Visual Studio Team Services usando oAuth2. Como resultado, você poderá ver uma caixa de diálogo de logon VSTS. 
   
   > [!IMPORTANT]
   > Algumas implantações do Visual Studio Team Services não são compatíveis com o oAuth2.  Se ocorrer falha ao entrar, siga as diretrizes na seção de Solução de Problemas.
   > 
   > 
   
   ![](media/service-connect-to-visual-studio/pbi_vsosignin2.png)
6. Siga as telas de autenticação do Visual Studio Team Services para conceder ao pacote de conteúdo do Visual Studio para o Power BI a permissão de acesso aos dados do seu projeto de equipe.   
   ![](media/service-connect-to-visual-studio/vsoauthorizeapp450.png)
7. Depois de se conectar ao seu projeto do Visual Studio Team Services, você verá um novo painel, relatório e conjunto de dados no painel de navegação esquerdo. Novos itens são marcados com um asterisco amarelo \*.  
   ![](media/service-connect-to-visual-studio/visualstudioonline800px.png) 

**E agora?**

* Tente [fazer uma pergunta na caixa de P e R](service-q-and-a.md) na parte superior do dashboard
* [Altere os blocos](service-dashboard-edit-tile.md) no dashboard.
* [Selecione um bloco](service-dashboard-tiles.md) para abrir o relatório subjacente.
* Enquanto seu conjunto de dados será agendado para ser atualizado diariamente, você pode alterar o agendamento de atualização ou tentar atualizá-lo sob demanda usando **Atualizar Agora**

## <a name="whats-included"></a>O que está incluído
O Visual Studio Team Services no Power BI fornece uma variedade de tabelas e campos para o seu relatório. A lista completa do que está no pacote de conteúdo pode ser encontrada aqui:  <https://www.visualstudio.com/get-started/report/vso-pbi-whats-available-vs>

## <a name="system-requirements"></a>Requisitos de sistema
* Acesso à conta do Visual Studio Team Services com permissão para coletar os dados usando a API REST.  
* Permissão concedida ao aplicativo “Power BI” durante a conexão inicial. Para desconectar o Power BI e remover sua autorização para acessar sua conta do Visual Studio Team Services, você pode revogar o acesso no Visual Studio Team Services. Consulte <https://www.visualstudio.com/get-started/setup/change-application-access-policies-vs>.  

Mais detalhes estão disponíveis em <https://www.visualstudio.com/en-us/get-started/report/connect-vso-pbi-vs>.

<a name="FindingParams"></a>

## <a name="finding-parameters"></a>Localizando parâmetros
O nome da conta é a parte inicial da URL do visualstudio.com:    
    ![](media/service-connect-to-visual-studio/urlimage.png)

O nome do projeto é o nome que você vê na parte superior de cada página no VSTS:  
    ![](media/service-connect-to-visual-studio/projectimage.png)

Você também pode usar curingas para selecionar vários projetos. Por exemplo, é possível selecionar todos os projetos inserindo apenas “\*” ou todos os projetos que começam com “Azure” inserindo “Azure\*”.

## <a name="troubleshooting"></a>Solução de problemas
Quando você tenta fazer logon para o Visual Studio Team Services, você pode receber uma mensagem de Falha no logon.

Há duas razões comuns pelas quais você pode não conseguir fazer a autenticação com êxito:

1) Você está conectado com uma conta pessoal, em vez de sua conta corporativa ou de estudante  

2) Não há suporte para oAuth em sua implantação do Visual Studio Team Services 

**Entrada com sua conta de trabalho ou escolar**  
Se você encontrar esse problema, pode significar que você já está autenticado com o Visual Studio Team Services em uma conta diferente daquela por meio da qual você está tentando carregar dados - por exemplo, se você conectou-se ao Visual Studio Team Services com uma conta pessoal da Microsoft e conectou-se ao PowerBI com uma conta de trabalho ou escolar.

Para resolver esse problema:  

* Cancele a caixa de diálogo de configuração  
* Saia do Visual Studio Team Services com sua conta pessoal  
* Entre no Visual Studio Online usando sua conta corporativa ou de estudante  
* Reinicie o processo “Obter dados” acima 

Conectando com sua conta de trabalho ou escolar (Azure Active Directory/AAD):  
    ![](media/service-connect-to-visual-studio/vsologinscreen.png)

Se você vir este diálogo e desejar se conectar com sua conta corporativa ou de estudante (Azure Active Directory), lembre-se de clicar no link à esquerda para entrar com essa conta – não forneça suas credenciais do AAD no lado direito, já que ali é esperado que você insira uma conta da Microsoft (sua conta pessoal).

**Implantações do Visual Studio Team Services nas quais não há suporte para oAuth2**  
Seu administrador do VSTS pode ter desabilitado oAuth para sua implantação do Visual Studio Team Services.  Quando isso acontece, você fica momentaneamente impossibilitado de usar o pacote de conteúdo do Visual Studio para o Power BI. 

![](media/service-connect-to-visual-studio/oauth.png)

## <a name="next-steps"></a>Próximas etapas
* [Introdução ao Power BI](service-get-started.md)
* [Obter dados](service-get-data.md)

