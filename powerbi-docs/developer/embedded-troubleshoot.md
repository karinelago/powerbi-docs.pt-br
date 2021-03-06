---
title: Solucionando problemas do aplicativo inserido
description: Este artigo aborda alguns problemas comuns que podem ser encontrados ao inserir conteúdo do Power BI.
author: markingmyname
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-developer
ms.topic: conceptual
ms.date: 04/23/2018
ms.author: maghan
ms.openlocfilehash: fa142a34da003328ef509c319faf24d556023440
ms.sourcegitcommit: 80d6b45eb84243e801b60b9038b9bff77c30d5c8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34720801"
---
# <a name="troubleshooting-your-embedded-application"></a>Solucionando problemas do aplicativo inserido

Este artigo aborda alguns problemas comuns que podem ser encontrados ao inserir conteúdo do Power BI.

## <a name="tools-for-troubleshooting"></a>Ferramentas para solução de problemas

### <a name="fiddler-trace"></a>Rastreamento do Fiddler

[Fiddler](http://www.telerik.com/fiddler) é uma ferramenta gratuita da Telerik que monitora o tráfego HTTP.  Você pode ver tudo com as APIs do Power BI no computador cliente. Isso pode mostrar erros e outras informações relacionadas.

![Rastreamento do Fiddler](../includes/media/gateway-onprem-tshoot-tools-include/fiddler.png)

### <a name="f12-in-browser-for-front-end-debugging"></a>F12 no navegador para depuração de front-end

A tecla F12 iniciará a janela do desenvolvedor no navegador. Nela é possível examinar o tráfego de rede e outras informações.

![Depuração de navegador com F12](media/embedded-troubleshoot/browser-f12.png)

### <a name="extracting-error-details-from-power-bi-response"></a>Extração de detalhes do erro da resposta do Power BI

Este trecho de código mostra como extrair os detalhes do erro da exceção HTTP:

```
public static string GetExceptionText(this HttpOperationException exc)
{
    var errorText = string.Format("Request: {0}\r\nStatus: {1} ({2})\r\nResponse: {3}",
    exc.Request.Content, exc.Response.StatusCode, (int)exc.Response.StatusCode, exc.Response.Content);
    if (exc.Response.Headers.ContainsKey("RequestId"))
    {
        var requestId = exc.Response.Headers["RequestId"].FirstOrDefault();
        errorText += string.Format("\r\nRequestId: {0}", requestId);
    }

    return errorText;
}
```
É recomendável registrar em log as IDs de solicitação (e detalhes do erro para solução de problemas).
Forneça a ID da solicitação ao entrar em contato com o Suporte da Microsoft.

## <a name="app-registration"></a>Registro de aplicativo

**Falha no registro de aplicativo**

As mensagens de erro no Portal do Azure ou na página de registro de aplicativo do Power BI mencionarão privilégios insuficientes. Para registrar um aplicativo, você deve ser administrador no locatário do Azure AD ou os registros do aplicativo devem estar habilitados para usuários não administradores.

**O serviço do Power BI não aparece no Portal do Azure ao registrar um novo aplicativo**

Pelo menos um usuário deve estar inscrito no Power BI. Se você não vir **Serviço do Power BI** na lista de APIs, será uma indicação de que nenhum usuário está inscrito no Power BI.

## <a name="rest-api"></a>API REST

**Chamada à API retornando 401**

Uma captura do fiddler pode ser necessária para uma investigação mais aprofundada. O escopo necessário da permissão pode estar ausente no aplicativo registrado no Azure AD. Verifique se o escopo necessário está presente no registro do aplicativo para o Azure AD no Portal do Azure.

**Chamada à API retornando 403**

Uma captura do fiddler pode ser necessária para uma investigação mais aprofundada. Pode haver vários motivos para um erro 403.

* O usuário excedeu a quantidade de tokens de inserção que pode ser gerada em uma capacidade compartilhada. É necessário comprar capacidades do Azure para gerar tokens de inserção e atribuir o espaço de trabalho a essa capacidade. Consulte [Criar uma capacidade do Power BI Embedded no Portal do Azure](https://docs.microsoft.com/azure/power-bi-embedded/create-capacity).
* O token de autenticação do Azure AD expirou.
* O usuário autenticado não é membro do grupo (espaço de trabalho do aplicativo).
* O usuário autenticado não é administrador do grupo (espaço de trabalho do aplicativo).
* O cabeçalho de autorização talvez não esteja exibido corretamente. Verifique se não há erros de digitação.

O back-end do aplicativo pode precisar atualizar o token de autenticação antes de chamar GenerateToken.

```
    GET https://wabi-us-north-central-redirect.analysis.windows.net/metadata/cluster HTTP/1.1
    Host: wabi-us-north-central-redirect.analysis.windows.net
    ...
    Authorization: Bearer eyJ0eXAiOi...
    ...
 
    HTTP/1.1 403 Forbidden
    ...
     
    {"error":{"code":"TokenExpired","message":"Access token has expired, resubmit with a new access token"}}
```

**Falha na geração do token ao fornecer a identidade em vigor**

Por motivos diferentes, pode haver falha em GenerateToken com a identidade em vigor fornecida.

* O conjunto de dados não é compatível com a identidade em vigor
* O nome de usuário não foi fornecido
* A função não foi fornecida
* A DatasetId não foi fornecida
* O usuário não tem as permissões corretas

Para verificar qual é o problema, tente as opções a seguir.

* Execute a operação [get dataset](https://msdn.microsoft.com/library/mt784653.aspx). A propriedade IsEffectiveIdentityRequired é verdadeira?
* O nome de usuário é obrigatório para qualquer EffectiveIdentity.
* Se a propriedade IsEffectiveIdentityRolesRequired for verdadeira, a Função será necessária.
* A DatasetId é obrigatória para qualquer EffectiveIdentity.
* Para o Analysis Services, o usuário mestre deve ser administrador do gateway.

## <a name="data-sources"></a>Fontes de dados

**O ISV deseja ter credenciais diferentes para a mesma fonte de dados**

Uma fonte de dados pode ter um único conjunto de credenciais para um usuário mestre. Se você precisar usar credenciais diferentes, crie usuários mestres adicionais. Em seguida, atribua as credenciais diferentes em cada contexto de usuários mestres e insira usando o token do Azure AD do usuário.

## <a name="content-rendering"></a>Renderização de conteúdo

**Falha ou tempo limite esgotado da renderização ou do consumo de conteúdo inserido**

Verifique se o token de inserção não expirou. Não se esqueça de verificar a expiração do token de inserção e atualizá-lo. Para obter mais informações, veja [Refresh token using JavaScript SDK](https://github.com/Microsoft/PowerBI-JavaScript/wiki/Refresh-token-using-JavaScript-SDK-example) (Atualizar token usando o SDK do JavaScript).

**O relatório ou o dashboard não carrega**

Se o usuário não puder visualizar o relatório ou o dashboard, verifique se o relatório ou o dashboard foi carregado corretamente no powerbi.com. O relatório ou o dashboard não funcionará no aplicativo se ele não for carregado no powerbi.com.

**A execução do relatório ou do dashboard está lenta**

Abra o arquivo no Power BI Desktop ou no powerbi.com e verifique se o desempenho é aceitável para eliminar problemas com o aplicativo ou as APIs de inserção.

## <a name="onboarding-experience-tool-for-embedding"></a>Ferramenta de experiência de integração para inserção

É possível examinar a [Ferramenta de experiência de integração](https://aka.ms/embedsetup) e baixar um aplicativo de exemplo. Em seguida, você pode comparar o aplicativo com o exemplo.

### <a name="prerequisites"></a>Pré-requisitos

Verifique se você tem todos os pré-requisitos apropriados antes de usar a Ferramenta de experiência de integração. Você precisará de uma conta do **Power BI Pro** e de uma assinatura do **Microsoft Azure**.

* Se não estiver inscrito no **Power BI Pro**, [inscreva-se para uma avaliação gratuita](https://powerbi.microsoft.com/en-us/pricing/) antes de começar.
* Caso você não tenha uma assinatura do Azure, crie uma [conta gratuita](https://azure.microsoft.com/free/?WT.mc_id=A261C142F) antes de começar.
* Você precisa ter seu próprio [locatário do Azure Active Directory](create-an-azure-active-directory-tenant.md) configurado.
* Você precisa do [Visual Studio](https://www.visualstudio.com/) instalado (versão 2013 ou posterior).

### <a name="common-issues"></a>Problemas comuns

Alguns problemas comuns que você pode encontrar durante o teste com a Ferramenta de experiência de integração são:

#### <a name="using-the-embed-for-your-customers-sample-application"></a>Usando o aplicativo de exemplo Inserir para clientes

Se você estiver trabalhando com a experiência **Inserir para clientes**, salve e descompacte o arquivo *PowerBI-Developer-Samples.zip*. Em seguida, abra a pasta *PowerBI-Developer-Samples-master\App Owns Data* e execute o arquivo *PowerBIEmbedded_AppOwnsData.sln*.

Ao selecionar **Conceder permissões** (a etapa "Conceder permissões"), você verá o seguinte erro:

    AADSTS70001: Application with identifier <client ID> was not found in the directory <directory ID>

A solução é fechar a janela pop-up, aguarde alguns segundos e tente novamente. Talvez seja necessário repetir essa ação algumas vezes. Um intervalo de tempo causa o problema de conclusão do processo de registro de aplicativo quando ele está disponível para APIs externas.

A seguinte mensagem de erro será exibida ao executar o aplicativo de exemplo:

    Password is empty. Please fill password of Power BI username in web.config.

Esse erro ocorre porque o único valor que não está sendo inserido no aplicativo de exemplo é a senha do usuário. Abra o arquivo Web.config na solução e preencha o campo pbiPassword com a senha do usuário.

#### <a name="using-the-embed-for-your-organization-sample-application"></a>Usando o aplicativo de exemplo Inserir para a organização

Se você estiver trabalhando com a experiência **Inserir para a organização**, salve e descompacte o arquivo *PowerBI-Developer-Samples.zip*. Abra a pasta *PowerBI-Developer-Samples-master\User Owns Data\integrate-report-web-app* e execute o arquivo *pbi-saas-embed-report.sln*.

Ao executar o aplicativo de exemplo **Inserir para a organização**, você verá o seguinte erro:

    AADSTS50011: The reply URL specified in the request does not match the reply URLs configured for the application: <client ID>

Isso ocorre porque a URL de redirecionamento especificada para o aplicativo de servidor Web é diferente da URL do exemplo. Se você quiser registrar o aplicativo de exemplo, use *http://localhost:13526/* como a URL de redirecionamento.

Se você quiser editar o aplicativo registrado, aprenda a editar o [aplicativo registrado no AAD](https://docs.microsoft.com/azure/active-directory/develop/active-directory-integrating-applications#updating-an-application), assim, o aplicativo poderá fornecer acesso a APIs Web.

Se você quiser editar o perfil do usuário do Power BI ou os dados, aprenda a editar os [dados do Power BI](https://docs.microsoft.com/en-us/power-bi/service-basic-concepts).

Para saber mais, veja [Perguntas frequentes do Power BI Embedded](embedded-faq.md).

Mais perguntas? [Experimente a Comunidade do Power BI](http://community.powerbi.com/)