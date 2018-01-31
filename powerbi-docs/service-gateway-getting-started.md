---
title: "Introdução aos gateways do Power BI"
description: "Aprenda as noções básicas sobre gateways de dados para o Power BI."
services: powerbi
documentationcenter: 
author: davidiseminger
manager: kfile
backup: 
editor: 
tags: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: powerbi
ms.date: 01/24/2018
ms.author: davidi
ms.openlocfilehash: 14c96dbc88784cd76099c25508409bcc24064e35
ms.sourcegitcommit: 7249ff35c73adc2d25f2e12bc0147afa1f31c232
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/25/2018
---
# <a name="getting-started-with-power-bi-gateways"></a>Introdução aos gateways do Power BI
Bem-vindo ao guia de **Introdução aos gateways do Power BI**. Este breve passo a passo serve para familiarizá-lo com o que um gateway faz, como ele funciona e como ter seu próprio gateway instalado, configurado e em execução.  

![](media/service-gateway-getting-started/gw_gettingstarted_0a.png)

Os gateways podem ser um assunto técnico e como cada rede e empresa são diferentes, a complexidade dos gateways pode ser significativa. Para manter essa complexidade afastada, vamos começar com os fundamentos básicos.

## <a name="how-power-bi-gateways-work"></a>Como funcionam os gateways do Power BI
Um **gateway** é um software que facilita o acesso a dados que residem em uma rede privada e local, para uso subsequente em um serviço de nuvem como o Power BI. Ele é como um gatekeeper que escuta as solicitações de conexão e as concede somente quando as solicitações dos usuários atendem a certos critérios (como se eles tivessem permissão para usar o gateway). Isso permite que as organizações deixem que bancos de dados e warehouses em suas redes locais, ainda que de maneira segura, usem subconjuntos desses dados para criar relatórios e painéis interessantes no Power BI.

Um gateway também protege o acesso e os dados criptografando e compactando todos os dados que passam por ele, bem como todas as senhas usadas para se conectar às fontes de dados. Tenho certeza que tudo isso parece simples, mas há muitos detalhes a considerar.

Às vezes você deseja um gateway só para você. Talvez você tenha uma grande pasta de trabalho do Excel e mais três bancos de dados SQL com anos de execução de dados de vendas e marketing e você deseja criar um dashboard do Power BI que mostre essas vendas de todos os ângulos. Você é a única pessoa que cria relatórios, é a sua pasta de trabalho do Excel e você usa esses bancos de dados somente para criar relatórios do Power BI. Você só precisa de um gateway para uso pessoal e não para compartilhar essas fontes de dados com todas as outras pessoas.

Em outras situações, você pode estar em uma organização com todos os tipos de bancos de dados de diferentes fornecedores, incluindo Analysis Services, SAP, Oracle, IBM e várias outras fontes de dados, e você precisa que muitas pessoas os acessem, para que possam criar uma grande quantidade de relatórios. Nesse caso, você precisa de um gateway que permita que você configure o acesso a todas essas fontes e, em seguida, você precisa compartilhá-lo com muitas pessoas na sua organização. Esse é um tipo completamente diferente de gateway.

Felizmente, o Power BI oferece dois gateways, ajustando-se bem a cada um desses cenários. Essas duas ofertas de gateway do Power BI são as seguintes:

* **Gateway de dados local (modo pessoal)** – permite que um usuário se conecte às fontes e não pode ser compartilhado com outras pessoas. Só pode ser usado com o Power BI.
* **Gateway de dados local** – permite que vários usuários se conectem a várias fontes de dados locais e pode ser usado pelo Power BI, pelo PowerApps, pelo Flow e pelo Aplicativo Lógico do Azure, tudo isso com uma única instalação de gateway.

Os dois gateways realizam uma função semelhante: eles facilitam o acesso aos dados que residem em uma rede privada local, para que os dados possam ser usados em serviços baseados em nuvem, como o Power BI. O gateway pessoal pode ser usado por uma pessoa e apenas pelo Power BI, o **gateway de dados local** pode ser usado por vários usuários e serviços.

Há três partes ou estágios, para colocar um gateway para trabalhar:

* Instalar o gateway
* Adicionar usuários ao gateway (permitir que eles usem o gateway)
* Conectar-se a fontes de dados

Além disso, o uso de um gateway permite que você faça algo mais que pode ser importante:

* Atualizar dados locais, para que os relatórios do Power BI possam ter dados atualizados

A atualização de dados significa que seus dashboards e relatórios do Power BI terão a aparência de novos e mostrarão os dados mais recentes. Assim, quando alguém exibe um relatório criado com os dados locais, esse relatório poderá mostrar as informações mais recentes, mesmo que você o tenha criado há algum tempo.

A primeira parte, instalar um gateway, é fácil. Permitir que usuários acessem o gateway também é fácil: basta adicioná-los em uma caixa de diálogo no Power BI e está pronto. A conexão às fontes de dados pode se tornar complexa, porque há muitas fontes de dados e cada uma tem seus próprios requisitos de conexão e nuances. Nós vamos lidar com a atualização em outro guia, para manter as coisas neste artigo concentradas no gateway.

Então, vamos fazer a coisa fácil primeiro e percorrer o passo a passo da instalação de um gateway.

## <a name="install-the-gateway"></a>Instalar o gateway
Para instalar um gateway, abra o serviço do Power BI (você pode usar este link para iniciar o serviço do Power BI em seu navegador e fazer logon) e faça logon com sua conta do Power BI. No serviço do Power BI, selecione o **ícone de download** na parte superior do canto direito, conforme mostrado na imagem a seguir e selecione **Gateway de Dados**.

![](media/service-gateway-getting-started/gw_gettingstarted_01.png)

Isso o levará a uma página de download, em que você clica no botão **Baixar gateway** para iniciar o download.

![](media/service-gateway-getting-started/gw_gettingstarted_02.png)

Esta tela lhe dá a explicação ultra condensada do que um gateway faz. Ela também oferece alguns **avisos** importantes. Quando você instala um gateway, na verdade ele é executado no computador em que você realiza a instalação. E se esse computador for desligado, o gateway também será (de modo que ele não funcionará quando não estiver em execução). Além disso, a instalação em um computador usando uma rede sem fio não é recomendada, portanto você deve usar um computador conectado a uma rede com fio.

Quando estiver pronto, selecione **Avançar** para continuar com a instalação.

![](media/service-gateway-getting-started/gw_gettingstarted_03.png)

Este é o local em que você decide qual gateway instalará: gateway local ou um gateway pessoal. Neste guia, instalaremos o **Gateway de dados local**.

Há algumas coisas a serem observadas nesse ponto de decisão:

* Ambos os gateways exigem sistemas operacionais Windows de 64 bits.
* Gateways não podem ser instalados em um controlador de domínio.
* Instale até dois gateways de dados locais no mesmo computador, cada um executando um dos modos (pessoal e padrão). 
* Não é possível ter mais de um gateway em execução no mesmo modo no mesmo computador.
* Instale vários gateways de dados locais em computadores diferentes e gerencie-os usando a mesma interface de gerenciamento de gateway do Power BI (exceto o modo pessoal, consulte o marcador a seguir).
* Só pode haver um gateway de modo pessoal em execução para cada usuário do Power BI. Se você instalar outro gateway de modo pessoal para o mesmo usuário, mesmo que em um computador diferente, a instalação mais recente substituirá a instalação anterior existente.

Ao selecionarmos **Avançar**, a instalação do gateway é iniciada. Você precisa especificar o local em que ele será instalado e o local padrão é geralmente o melhor.

![](media/service-gateway-getting-started/gw_gettingstarted_06.png)

O processo de instalação avança rapidamente e você terá uma barra de status.

![](media/service-gateway-getting-started/gw_gettingstarted_06a.png)

Quando estiver quase concluída, você precisará identificar a conta a ser usada com o gateway. Essa deve ser a conta (nome de usuário e senha) que você usa para fazer logon no Power BI. O gateway está associado à sua conta do Power BI e você configura os gateways no serviço do Power BI.

![](media/service-gateway-getting-started/gw_gettingstarted_07.png)

Você será conectado, conforme mostrado na imagem a seguir.

![](media/service-gateway-getting-started/gw_gettingstarted_08.png)

Quando estiver conectado, você precisará criar uma **Chave de recuperação**. Discutiremos sobre isso mais detalhadamente em outro artigo, mas por enquanto, saiba que você precisará dela para recuperar ou mover seu gateway.

![](media/service-gateway-getting-started/gw_gettingstarted_09.png)

Quando tudo corre bem, você vê uma janela informando que seu gateway está pronto.

![](media/service-gateway-getting-started/gw_gettingstarted_10.png)

Isso é tudo para a instalação de um gateway local. Como prometido, esse era um processo bastante fácil. Então, a próxima etapa é para **adicionar usuários** ou para **adicionar fontes de dados**. Você pode fazer qualquer uma delas em primeiro lugar e adicionar qualquer uma delas após sua configuração inicial.

A próxima seção descreve a adição de usuários ao gateway e, depois disso, discutiremos o que fazer em seguida para adicionar fontes de dados ao gateway.

## <a name="add-users-to-a-gateway"></a>Adicionar usuários a um gateway
Agora que temos um gateway instalado, podemos gerenciar o gateway no **serviço do Power BI**. Para chegar à tela de gerenciamento de gateways, no serviço do Power BI, selecione o ícone de Engrenagem no canto superior direito e selecione **Gerenciar gateways**.

![](media/service-gateway-getting-started/gw_gettingstarted_15.png)

Aparece uma página dentro da tela de serviço do Power BI, na qual você pode gerenciar seus gateways. A página **Configurações do Gateway** é semelhante ao seguinte.

![](media/service-gateway-getting-started/gw_gettingstarted_12.png)

Se tocar ou clicar em **Administradores**, você verá a seguinte página de gerenciamento dos administradores. Observe que isso é apenas quais usuários podem *administrar* o gateway e os usuários do gateway que são adicionados (ou removidos) de cada fonte de dados individuais, usando uma página diferente, que examinaremos nos próximos parágrafos.

![](media/service-gateway-getting-started/gw_gettingstarted_13.png)

Depois de instalar e validar (conectar-se com êxito) uma fonte de dados, ela aparece em seu gateway associado no lado esquerdo dessa tela **Gerenciar gateways**, conforme mostrado na imagem a seguir. Observe que, no painel direito, há duas seções entre as quais você pode alternar: **Configurações de fonte de dados** e **Usuários**. A tela diretamente a seguir é a seção **Configurações de fonte de dados**.

![](media/service-gateway-getting-started/gw_gettingstarted_16.png)

Quando você seleciona **Usuários**, obtém uma caixa de texto na qual pode digitar usuários da organização a quem você quer conceder acesso à fonte de dados selecionada. Na tela seguinte, você pode ver que adicionei Maggie e Adam.

Quando você começa a digitar um endereço de email na caixa de texto, o Power BI mostra uma lista de usuários cujos emails correspondem ao que você está digitando, permitindo que você clique no nome e adicione-os à lista.

Você também pode adicionar grupos de email (alias) para permitir que grupos de pessoas acessem, bem como os indivíduos.

![](media/service-gateway-getting-started/gw_gettingstarted_17.png)

Depois de selecionar **Adicionar**, o membros adicionados aparecerão na caixa e você pode adicionar mais se desejar. A remoção de usuários também é fácil. Basta marcar a caixa de seleção ao lado do nome deles e, em seguida, selecionar o botão **Remover** abaixo da caixa.

![](media/service-gateway-getting-started/gw_gettingstarted_18.png)

E isso é tudo o que é necessário. Lembre-se de que você precisa adicionar usuários a cada fonte de dados às quais você deseja conceder acesso. Cada fonte de dados tem uma lista separada de usuários e você deve adicionar usuários para cada fonte de dados separadamente.

## <a name="adding-data-sources"></a>Adicionando fontes de dados
É claro que, para tornar o seu gateway útil, você desejará adicionar fontes de dados. É aqui que um pouco da complexidade dos gateways do Power BI é introduzida: há várias fontes de dados disponíveis e cada uma tem seus próprios requisitos (e com frequência, seu próprio driver necessário).

Mas antes de enviar você para outro artigo, aqui vai uma visão geral de como você pode adicionar uma fonte de dados. Enquanto estiver na página **Gerenciar gateways** do **serviço do Power BI**, selecione o gateway para o qual você deseja adicionar uma fonte de dados e selecione **Adicionar fonte de dados** no canto superior esquerdo da página, logo acima da lista dos seus gateways.

Quando você fizer isso, o painel **Configurações de fonte de dados** será exibido no painel à direita, conforme mostrado na imagem a seguir. Nesse local, você pode nomear sua fonte de dados (inserindo na caixa de texto **Nome da Fonte de Dados**) e selecionar o tipo na lista suspensa **Tipo de fonte de dados**.

![](media/service-gateway-getting-started/gw_gettingstarted_14.png)

Muito bem, agora você tem um gateway instalado e está pronto para adicionar fontes de dados. Ótimo! Consulte os recursos na seção a seguir para obter informações sobre fontes de dados, para obter mais detalhes sobre como usar os gateways e outras informações úteis.

## <a name="next-steps"></a>Próximas etapas
[Usando o gateway de dados local](service-gateway-onprem.md)  
[Detalhes sobre o gateway de dados local](service-gateway-onprem-indepth.md)  
[Gateway de dados local (modo pessoal)](service-gateway-personal-mode.md)
[Solução de problemas do gateway de dados local](service-gateway-onprem-tshoot.md)  

Mais perguntas? [Experimente a Comunidade do Power BI](http://community.powerbi.com/)

