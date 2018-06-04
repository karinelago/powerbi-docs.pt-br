---
title: Testar os pacotes de conteúdo de modelo para o Power BI
description: Teste do pacote de conteúdo do modelo
author: markingmyname
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-developer
ms.topic: conceptual
ms.date: 10/09/2017
ms.author: maghan
ms.openlocfilehash: 3658a569a0bd15822cd50fefb73e706d771b6c80
ms.sourcegitcommit: 80d6b45eb84243e801b60b9038b9bff77c30d5c8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34288580"
---
# <a name="testing-template-content-packs-for-power-bi"></a>Testar os pacotes de conteúdo de modelo para o Power BI
Há várias maneiras de testar seu pacote de conteúdo antes de enviá-lo para publicação.  

> [!NOTE]
> Se o seu pacote de conteúdo usar um [Conector de Dados](https://aka.ms/DataConnectors) personalizado que você desenvolveu, você não poderá testar a atualização de dados ou o pacote de conteúdo do modelo, conforme a descrição abaixo. Se esse for o caso, vá para [enviar](#submission) seu pacote de conteúdo e a equipe do Power BI trabalhará com você para testar seu pacote de conteúdo.
> 
> 

## <a name="testing-scheduled-data-refresh"></a>Testando a atualização agendada de dados
Os pacotes de conteúdo do modelo utilizam o recurso Atualização no PowerBI.com para criar uma instância de um pacote de conteúdo com os dados do cliente durante a conexão. Antes de o pacote de conteúdo estar publicamente disponível, é possível testar esse fluxo com o arquivo do Desktop que você criou.

Depois de carregar o arquivo, selecione “...” ao lado do conjunto de dados e selecione Agendar Atualização. Configure credenciais para a fonte. Confira se o conjunto de dados é atualizado com êxito: tente “Atualizar Agora” e “Atualização Agendada”. Caso a atualização apresente falhas, verifique a mensagem de erro e valide suas consultas e seu sistema final.

### <a name="additional-refresh-tips"></a>Outras dicas de atualização
* Somente uma única fonte de dados deve ser detectada ao tentar agendar a atualização  
* A conexão de teste deverá indicar que o usuário poderá carregar o pacote de conteúdo. Se esse não for o caso, verifique se suas consultas tratam os casos de erro adicionais.  
* A atualização deverá ser concluída em um tempo razoável; o recomendado é cerca de 5 minutos  

![configurações](media/template-content-pack-testing/scheduledrefresh.png)

<a name="templates"></a>

## <a name="testing-templates"></a>Testando modelos
Um pacote de conteúdo do modelo é semelhante às soluções existentes, com a exceção de que ele não inclui os dados reais no conjunto de dados. Em vez disso, quando um usuário consome ou cria uma instância de um modelo, será solicitado que ele insira parâmetros e credenciais para se conectar. Depois de conectado, ele verá seus próprios dados no dashboard, no relatório e nos conjuntos de dados. 

Depois que um usuário comprova o pacote de conteúdo que ele tem acesso nas configurações do conjunto de dados, incluindo atualização agendada, as configurações de RLS no conjunto de dados **não** são publicadas com o pacote de conteúdo.  

> [!NOTE]
> Os pacotes de conteúdo do modelo só podem incluir um dashboard, um relatório e um conjunto de dados. Veja a lista de restrições na página [Criação](template-content-pack-authoring.md#restrictions). 
> 
> 

Para habilitar a criação de modelo para o seu locatário, trabalhe com o administrador do Power BI para habilitar a opção abaixo. 

![featureswitch](media/template-content-pack-testing/featureswitch.png)

Uma vez habilitada, você verá uma caixa de seleção na parte inferior de ["Criar pacote de conteúdo"](https://app.powerbi.com/groups/me/publish-content/), permitindo que você publique um pacote de conteúdo do modelo em sua organização. 

![caixa de seleção](media/template-content-pack-testing/checkbox.png)

### <a name="naming"></a>Nomenclatura
Sugerimos que você nomeie seu dashboard, relatório e conjunto de dados de maneira consistente em todo o pacote de conteúdo. Esses nomes são embutidos em código e serão os mesmos para todos os usuários; portanto, usar seu nome de produto/cenário pode facilitar a localização por parte dos clientes.

### <a name="additional-template-tips"></a>Outras dicas de modelos
* Confira se os parâmetros especificados nas consultas são significativos para os usuários finais
* Considere quanto tempo o usuário final ficará aguardando até a conclusão da atualização agendada

![criar](media/template-content-pack-testing/createtemplate.png)

<a name="submission"></a>

## <a name="submission"></a>Envio
O processo de envio por meio do [Microsoft AppSource](https://appsource.microsoft.com/en-us/partners/list-an-app) permitirá que você publique o pacote de conteúdo do modelo na galeria de pacotes de conteúdo do serviço no PowerBI.com e também liste seu pacote de conteúdo no [Microsoft AppSource](http://appsource.microsoft.com).

### <a name="before-submission"></a>Antes do envio
* Examinar as dicas de criação para cada um dos artefatos no pacote de conteúdo
* Teste e conecte-se com várias condições de contas e dados. (Pule esta etapa se você desenvolveu seu próprio [Conector de Dados](https://aka.ms/DataConnectors) personalizado)
* Examinar todos os visuais, observar atentamente itens com erros de ortografia
* Verifique se o pacote de conteúdo responde bem à P e R; sugerimos que você teste, pelo menos, 30 perguntas variadas em todo o modelo de dados. (Pule esta etapa se você desenvolveu seu próprio [Conector de Dados](https://aka.ms/DataConnectors) personalizado)

### <a name="submission"></a>Envio
Quando estiver pronto para enviar, visite a [Página de envio de aplicativos](https://appsource.microsoft.com/en-us/partners/list-an-app) em AppSource e envie suas informações. Não se esqueça de selecionar o Power BI na lista de produtos disponíveis

Equipe do Power BI examinará seu envio e entrará em contato para garantir que todos os artefatos atendam aos requisitos de envio. Além de ser concluído, também validaremos a qualidade do dashboard e dos relatórios fornecidos, garantindo que eles atendem ao cenário de negócios descrito no aplicativo.

### <a name="updates"></a>Atualizações
Atualizar seu pacote de conteúdo segue um fluxo semelhante ao envio original. 

