---
title: Solucionando problemas do aplicativo inserido
description: "Este artigo aborda alguns problemas comuns que podem ser encontrados ao inserir conteúdo do Power BI."
services: powerbi
documentationcenter: 
author: markingmyname
manager: kfile
backup: 
editor: 
tags: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 1/17/2018
ms.author: maghan
ms.openlocfilehash: 2936fa40700895d9953bb227cc30e68d64ae9205
ms.sourcegitcommit: 6e693f9caf98385a2c45890cd0fbf2403f0dbb8a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2018
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


Para obter respostas para perguntas frequentes, veja as [Perguntas frequentes sobre o Power BI Embedded](embedded-faq.md).

Mais perguntas? [Experimente a Comunidade do Power BI](http://community.powerbi.com/)
