---
title: Perguntas frequentes sobre o gateway de dados local
description: "Estas são as perguntas frequentes sobre o gateway de dados local. Esta é a página em que estão reunidas as perguntas frequentes sobre o gateway."
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
ms.date: 10/05/2017
ms.author: davidi
ms.openlocfilehash: 063fd92829c6b642fc33e578026d109d891b8fd5
ms.sourcegitcommit: 284b09d579d601e754a05fba2a4025723724f8eb
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/15/2017
---
# <a name="on-premises-data-gateway-faq"></a>Perguntas Frequentes do Gateway de Dados Local
<!-- Shared FAQ shared Include -->
[!INCLUDE [gateway-onprem-faq-shared-include](./includes/gateway-onprem-faq-shared-include.md)]

## <a name="analysis-services"></a>Analysis Services
**Pergunta:** Posso usar msdmpump.dll para criar mapeamentos personalizados de nome de usuário efetivo para o Analysis Services?  
**Resposta:** Não. Não há suporte para isso no momento.

**Pergunta:** Posso usar o gateway para me conectar a uma instância multidimensional (OLAP)?  
**Resposta:** Sim! O Gateway de Dados Local oferece suporte a conexões ao vivo tanto com modelos Tabulares quanto modelos Multidimensionais do Analysis Services.

**Pergunta:** e se eu instalar o gateway em um computador em um domínio diferente do meu servidor local que usa a autenticação do Windows?  
**Resposta:** Não há nenhuma garantia nesse caso. Tudo depende a relação de confiança entre os dois domínios. Se os dois domínios diferentes estiverem em um modelo de domínio confiável, o gateway poderá se conectar ao servidor do Analysis Services e o nome de usuário efetivo poderá ser resolvido. Caso contrário, poderá ocorrer uma falha de logon.

**Pergunta:** Como posso descobrir qual nome de usuário efetivo está sendo transmitido para meu servidor local do Analysis Services?  
**Resposta:** Respondemos a essa pergunta no [artigo de solução de problemas](service-gateway-onprem-tshoot.md).

**Pergunta:** Tenho 25 bancos de dados no Analysis Services. Existe uma maneira de habilitar todos eles para o gateway de uma só vez?  
**Resposta:** não. Esse recurso já está em nossos planos, mas não temos previsão de quando será liberado.

## <a name="administration"></a>Administração
**Pergunta:** Posso ter mais de um administrador para um gateway?  
**Resposta:** Sim! Quando você gerencia um gateway, é possível ir para a guia do administrador para adicionar outros administradores.

**Pergunta:** O administrador do gateway precisa ser um administrador no computador em que o gateway está instalado?  
**Resposta:** não. O administrador do gateway é usado para gerenciar o gateway no próprio serviço.

**Pergunta:** Posso impedir que os usuários de minha organização criem um gateway?  
**Resposta:** não. Esse recurso já está em nossos planos, mas não temos previsão de quando será liberado.

**Pergunta:** Posso obter informações de uso e de estatísticas dos gateways de minha organização?  
**Resposta:** não. Esse recurso já está em nossos planos, mas não temos previsão de quando será liberado.

## <a name="power-bi"></a>Power BI
**Pergunta:** Preciso fazer upgrade do gateway pessoal?
**Resposta:** Não, você pode continuar usando o gateway pessoal do Power BI.

**Pergunta:** com que frequência os blocos em um painel no Power BI são atualizados quando conectados por meio do Gateway de Dados Local?  
**Resposta:** Cerca de dez minutos. As conexões do DirectQuery são exatamente assim. Isso não significa que um bloco emite uma consulta ao servidor local e mostra novos dados a cada dez minutos.

**Pergunta:** Posso carregar pastas de trabalho do Excel com modelos de dados do Power Pivot que se conectem a fontes de dados locais? Preciso ter um gateway para este cenário?  
**Resposta:** Sim, você pode carregar a pasta de trabalho. Não, não é necessário ter um gateway. Mas, como os dados residem no modelo de dados do Excel, os relatórios do Power BI baseados na pasta de trabalho do Excel não serão dinâmicos. Você precisaria carregar novamente uma pasta de trabalho atualizada cada vez que desejasse atualizar os relatórios no Power BI. Se preferir, use o gateway com a atualização agendada.

**Pergunta:** Se os usuários compartilharem dashboards que têm uma conexão do DirectQuery, os outros usuários poderão ver os dados mesmo que não tenham as mesmas permissões?  
**Resposta:** Para um painel conectado aos Serviços de Análise, os usuários verão apenas os dados que eles tiverem acesso. Se os usuários não tiverem as mesmas permissões, não poderão ver os dados. Para outras fontes de dados, todos os usuários compartilharão as credenciais inseridas pelo administrador para aquela fonte de dados.

**Pergunta:** por que não consigo me conectar ao servidor do Oracle?  
**Resposta:** talvez seja necessário instalar o cliente Oracle e configurar o arquivo tnsnames.ora com as informações de servidor apropriadas para se conectar ao servidor Oracle. Essa é uma instalação separada fora do Gateway. Para obter mais informações, consulte [Instalando o cliente Oracle](service-gateway-onprem-manage-oracle.md#installing-the-oracle-client).

**Pergunta:** o gateway funcionará com o ExpressRoute?  
**Resposta:** Sim. Para obter mais informações sobre o ExpressRoute e o Power BI, consulte [Power BI e ExpressRoute](service-admin-power-bi-expressroute.md).

## <a name="next-steps"></a>Próximas etapas
[Gateway de dados local](service-gateway-onprem.md)  
[Detalhes sobre o gateway de dados local](service-gateway-onprem-indepth.md)  
[Solução de problemas do Gateway de dados local](service-gateway-onprem-tshoot.md)  
Mais perguntas? [Experimente a Comunidade do Power BI](http://community.powerbi.com/)

