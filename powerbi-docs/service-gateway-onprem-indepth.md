---
title: Detalhes sobre o gateway de dados local
description: "Este artigo examina o gateway local mais detalhadamente. Ele explica como o serviço funciona com o Azure Active Directory e o Active Directory local ao trabalhar com o Analysis Services"
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
ms.date: 12/06/2017
ms.author: davidi
ms.openlocfilehash: fbb1b22b930a00fa9e090b3ebc5ab9fd1ffc88c0
ms.sourcegitcommit: d91436de68a0e833ecff18d976de9d9431bc4121
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/06/2017
---
# <a name="on-premises-data-gateway-in-depth"></a>Detalhes sobre o gateway de dados local
É possível que os usuários na sua organização acessem dados locais (para os quais eles já têm autorização de acesso), mas antes que eles possam se conectar à fonte de dados local, um gateway de dados local precisa ser instalado e configurado. O gateway facilita a comunicação nos bastidores, de maneira rápida e segura, de um usuário na nuvem para a fonte de dados local, retornando à nuvem em seguida.

A instalação e configuração de um gateway geralmente são feitas por um administrador. Esse processo pode necessitar de conhecimento especial sobre seus servidores locais e, em alguns casos, pode exigir permissões do Administrador do Servidor.

Este artigo não fornece orientações passo a passo sobre como instalar e configurar o gateway. Para fazer isso, veja [Gateway de dados local](service-gateway-onprem.md). Este artigo destina-se a fornecer uma compreensão detalhada de como o gateway funciona. Também veremos alguns detalhes sobre nomes de usuário e segurança no Azure Active Directory e no Analysis Services, além de como o serviço de nuvem usa o endereço de email que um usuário usa para entrar no gateway e no Active Directory para se conectar com segurança aos dados locais e consultá-los.

<!-- Shared Requirements Include -->
[!INCLUDE [gateway-onprem-requirements-include](./includes/gateway-onprem-how-it-works-include.md)]

<!-- Shared Install steps Include -->
[!INCLUDE [gateway-onprem-datasources-include](./includes/gateway-onprem-datasources-include.md)]

## <a name="sign-in-account"></a>Conta de entrada
Os usuários entrarão com uma conta corporativa ou de estudante. Essa é a conta de sua organização. Se você se inscreveu para uma oferta do Office 365 e não forneceu seu email de trabalho real, ela poderá ser semelhante a nancy@contoso.onmicrosoft.com. Sua conta, em um serviço de nuvem, é armazenada em um locatário do AAD (Azure Active Directory). Na maioria dos casos, o UPN de sua conta do AAD corresponderá ao endereço de email.

## <a name="authentication-to-on-premises-data-sources"></a>Autenticação em fontes de dados locais
Uma credencial armazenada será usada para se conectar a fontes de dados locais do gateway, exceto o Analysis Services. Independentemente do usuário individual, o gateway usa a credencial armazenada para se conectar.

## <a name="authentication-to-a-live-analysis-services-data-source"></a>Autenticação em uma fonte de dados dinâmica do Analysis Services
Cada vez que um usuário interage com o Analysis Services, o nome de usuário efetivo é passado para o gateway e, em seguida, para o servidor local do Analysis Services. O nome UPN, normalmente, o endereço de email que você usa para entrar na nuvem, é o que passaremos para o Analysis Services como o usuário efetivo. O nome UPN é passado na propriedade de conexão EffectiveUserName. Esse endereço de email deve corresponder a um UPN definido no domínio do Active Directory local. O UPN é uma propriedade de uma conta do Active Directory. Essa conta do Windows precisará estar presente em uma função do Analysis Services para que ela tenha acesso ao servidor. O logon não terá êxito se nenhuma correspondência for encontrada no Active Directory.

O Analysis Services também poderá fornecer a filtragem com base nessa conta. A filtragem pode ocorrer com a segurança baseada em função ou com a segurança em nível de linha.

## <a name="role-based-security"></a>Segurança baseada em função
Modelos fornecem segurança baseada em funções de usuário. Funções são definidas para um projeto de modelo específico durante a criação no SSDT-BI (SQL Server Data Tools – Business Intelligence), ou depois que um modelo é implantado usando o SSMS (SQL Server Management Studio). As funções contêm membros organizados por nome de usuário do Windows ou por grupo do Windows. As funções definem as permissões de que um usuário dispõe para consultar ou executar ações no modelo. A maioria dos usuários pertencerão a uma função com permissões de Leitura. Outras funções são destinadas a administradores com permissões para processar itens e gerenciar funções, tanto de banco de dados quanto de outros tipos.

## <a name="row-level-security"></a>Segurança em nível de linha
A segurança em nível de linha é específica para a segurança em nível de linha do Analysis Services. Os modelos podem fornecem segurança dinâmica no nível de linha. Em vez de ter pelo menos uma função à qual os usuários pertencem, a segurança dinâmica não é requerida para nenhum modelo de tabela. Em um nível elevado, a segurança dinâmica define o acesso de leitura de um usuário aos dados diretamente para uma linha específica em uma tabela específica. De modo similar ao que ocorre nas funções, a segurança dinâmica no nível de linha depende de um nome de usuário do Windows.

A capacidade de um usuário de consultar e ver dados de modelo é determinada, primeiramente, pelas funções das quais sua conta de usuário do Windows é membro e, em segundo lugar, pela segurança dinâmica em nível de linha, se estiver configurada.

A implementação de segurança dinâmica em nível de linha e a segurança baseada em função em modelos está além do escopo deste artigo.  Saiba mais em [Funções (SSAS de tabela)](https://msdn.microsoft.com/library/hh213165.aspx) e [Funções de segurança (Analysis Services – dados multidimensionais)](https://msdn.microsoft.com/library/ms174840.aspx) no MSDN. Além disso, para obter uma compreensão mais profunda sobre a segurança do modelo de tabela, baixe e leia o [white paper Securing the Tabular BI Semantic Model](https://msdn.microsoft.com/library/jj127437.aspx) (Protegendo o modelo semântico de BI de tabela).

## <a name="what-about-azure-active-directory"></a>E quanto ao Azure Active Directory?
Os serviços em nuvem da Microsoft usam o [Azure Active Directory](https://azure.microsoft.com/documentation/articles/active-directory-whatis/) para cuidar da autenticação de usuários. O Azure Active Directory é o locatário que contém nomes de usuário e grupos de segurança. Normalmente, um endereço de email usado para a entrada de um usuário é o mesmo que o UPN da conta.

Qual é a função do meu Active Directory local?

Para que o Analysis Services determine se um usuário que se conecta a ele pertence a uma função com permissões para leitura de dados, o servidor precisa converter o nome de usuário efetivo passado do ADD para o gateway e, em seguida, para o servidor do Analysis Services. O servidor do Analysis Services passa o nome de usuário efetivo para um DC (controlador de domínio) do Active Directory do Windows. Em seguida, o DC Active Directory valida o nome de usuário efetivo como um UPN válido, em uma conta local, e retorna esse nome de usuário do Windows do usuário de volta ao servidor do Analysis Services.

EffectiveUserName não pode ser usado em um servidor do Analysis Services que não foi ingressado em domínio. O servidor do Analysis Services deve ser ingressado em um domínio para evitar erros de logon.

## <a name="how-do-i-tell-what-my-upn-is"></a>Como saber qual é a minha UPN?
Talvez você não saiba o que é o UPN e talvez você não seja um administrador de domínio. Você pode usar o comando a seguir em sua estação de trabalho para descobrir o UPN para sua conta.

    whoami /upn

O resultado será semelhante a um endereço de email, mas esse é o UPN que está em sua conta de domínio local. Se você estiver usando uma fonte de dados do Analysis Services para conexões dinâmicas, ela deverá corresponder ao que foi passado para EffectiveUserName por meio do gateway.

## <a name="mapping-usernames-for-analysis-services-data-sources"></a>Mapeando nomes de usuário para fontes de dados do Analysis Services
O Power BI possibilita o mapeamento de nomes de usuário para fontes de dados do Analysis Services. É possível configurar regras para mapear um nome de usuário conectado com o Power BI para um nome passado para EffectiveUserName na conexão do Analysis Services. O recurso Mapear nomes de usuário é uma ótima maneira de solucionar problemas quando seu nome de usuário no AAD não corresponde a um UPN no Active Directory local. Por exemplo, se seu endereço de email fosse nancy@contoso.onmicrsoft.com, você poderia mapeá-lo para nancy@contoso.com e esse valor seria passado para o gateway. Saiba mais sobre como [mapear nomes de usuário](service-gateway-enterprise-manage-ssas.md#map-user-names).

## <a name="synchronize-an-on-premises-active-directory-with-azure-active-directory"></a>Sincronizar um Active Directory local com o Azure Active Directory
Você desejará que suas contas do Active Directory local correspondam ao Azure Active Directory se você for usar conexões dinâmicas do Analysis Services, já que o UPN deve ser correspondente entre as contas.

Os serviços de nuvem conhecem apenas as contas no Azure Active Directory. Não importa se você adicionou uma conta no Active Directory local, se ela não existir no AAD, não poderá ser usada. Há diferentes maneiras pelas quais você poderá corresponder suas contas do Active Directory local ao Azure Active Directory.

1. É possível adicionar contas manualmente ao Azure Active Directory.
   
   É possível criar uma conta no portal do Azure ou no Portal de Administração do Office 365, e o nome da conta corresponderá ao UPN da conta do Active Directory local.
2. Você pode usar a ferramenta [Azure AD Connect](https://azure.microsoft.com/documentation/articles/active-directory-aadconnect/) para sincronizar contas locais ao seu locatário do Azure Active Directory.
   
   A ferramenta Azure AD Connect fornece opções para a sincronização de diretório e senha. Se você não for um administrador de locatários nem um administrador de domínio local, precisará entrar em contato com seu administrador de TI para obter essa configuração.
3. Você pode configurar o ADFS (Serviços de Federação do Active Directory).
   
   É possível associar seu servidor do ADFS ao locatário do AAD com a ferramenta [Azure AD Connect](https://azure.microsoft.com/documentation/articles/active-directory-aadconnect/). O ADFS faz uso da sincronização de diretórios abordada acima, mas permite uma experiência de SSO (Logon Único). Por exemplo, se você estiver em sua rede corporativa, quando acessar um serviço de nuvem e entrar nele, talvez não seja solicitado que você insira um nome de usuário ou uma senha. Você precisará conversar com seu Administrador de TI caso essa opção esteja disponível para sua organização.

O uso do Azure AD Connect garante que o UPN corresponderá entre o AAD e o Active Directory local.

> [!NOTE]
> A sincronização de contas com a ferramenta Azure AD Connect criará novas contas em seu locatário do AAD.
> 
> 

## <a name="now-this-is-where-the-gateway-comes-in"></a>Agora, é aqui que entra o gateway
O gateway atua como uma ponte entre a nuvem e o servidor local. A transferência de dados entre a nuvem e o gateway é protegida pelo [Barramento de Serviço do Azure](https://azure.microsoft.com/documentation/services/service-bus/). O Barramento de Serviço cria um canal seguro entre a nuvem e o servidor local por meio de uma conexão de saída no gateway.  Não é necessário abrir nenhuma conexão de entrada no firewall local.

Se você tiver uma fonte de dados do Analysis Services, você precisará instalar o gateway em um computador associado ao mesmo domínio/floresta que o servidor do Analysis Services.

Quanto mais próximo o gateway está do servidor, mais rápida será a conexão. Se você pode obter o gateway no mesmo servidor que a fonte de dados, isso é melhor para evitar a latência da rede entre o gateway e o servidor.

## <a name="what-to-do-next"></a>O que fazer em seguida?
Depois que o gateway for instalado, você desejará criar fontes de dados para ele. Você pode adicionar fontes de dados na tela **Gerenciar gateways**. Para obter mais informações, consulte os artigos sobre gerenciar fontes de dados.

[Gerenciar sua fonte de dados – Analysis Services](service-gateway-enterprise-manage-ssas.md)  
[Gerenciar sua fonte de dados – SAP HANA](service-gateway-enterprise-manage-sap.md)  
[Gerenciar sua fonte de dados – SQL Server](service-gateway-enterprise-manage-sql.md)  
[Gerenciar sua fonte de dados – Oracle](service-gateway-onprem-manage-oracle.md)  
[Gerenciar sua fonte de dados – Importar/Atualização agendada](service-gateway-enterprise-manage-scheduled-refresh.md)  

## <a name="where-things-can-go-wrong"></a>O que pode dar errado
Às vezes, a instalação do gateway falha. Ou talvez o gateway pareça ser instalado sem problemas, mas o serviço ainda não poderá trabalhar com ele. Em muitos casos, é algo simples, como a senha para as credenciais que o gateway usa para entrar na fonte de dados.

Em outros casos, pode haver problemas com o tipo de endereço de email com que os usuários se autenticam, ou com ou incapacidade do Analysis Services de resolver um nome de usuário efetivo. Caso você tenha vários domínios com relações de confiança entre eles, e o gateway estiver em um domínio e o Analysis Services em outro, às vezes, isso poderá causar alguns problemas.

Em vez de explorar a solução de problemas do gateway aqui, apresentamos uma série de etapas de solução de problemas em outro artigo: [Solução de problemas do gateway de dados local](service-gateway-onprem-tshoot.md). Esperamos que você não tenha nenhum problema. Mas se acontecer, um entendimento de como tudo isso funciona e o artigo de solução de problemas devem ajudar.

<!-- Account and Port information -->
[!INCLUDE [gateway-onprem-accounts-ports-more](./includes/gateway-onprem-accounts-ports-more.md)]

## <a name="next-steps"></a>Próximas etapas
[Solução de problemas do gateway de dados local](service-gateway-onprem-tshoot.md)  
[Barramento de serviço do Azure](https://azure.microsoft.com/documentation/services/service-bus/)  
[Azure AD Connect](https://azure.microsoft.com/documentation/articles/active-directory-aadconnect/)  
Mais perguntas? [Experimente a Comunidade do Power BI](http://community.powerbi.com/)

