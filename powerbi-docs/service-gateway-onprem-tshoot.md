---
title: "Solução de problemas do gateway de dados local"
description: "Este artigo fornece maneiras de solucionar problemas com o gateway de dados local. Apresenta as possíveis soluções alternativas para problemas conhecidos, bem como ferramentas para ajudá-lo."
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
ms.date: 11/21/2017
ms.author: davidi
LocalizationGroup: Gateways
ms.openlocfilehash: 1651f18194cd47582376b52bb6359db10a330c27
ms.sourcegitcommit: 88c8ba8dee4384ea7bff5cedcad67fce784d92b0
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/24/2018
---
# <a name="troubleshooting-the-on-premises-data-gateway"></a>Solução de problemas do gateway de dados local
Este artigo aborda alguns problemas comuns que você poderá encontrar ao usar o **gateway de dados local**.

<!-- Shared Community & support links Include -->
[!INCLUDE [gateway-onprem-tshoot-support-links-include](./includes/gateway-onprem-tshoot-support-links-include.md)]

<!-- Shared Troubleshooting Install Include -->
[!INCLUDE [gateway-onprem-tshoot-install-include](./includes/gateway-onprem-tshoot-install-include.md)]

## <a name="configuration"></a>Configuração
### <a name="how-to-restart-the-gateway"></a>Como reiniciar o gateway
O gateway é executado como um serviço Windows, então você pode iniciá-lo e pará-lo de várias maneiras. Por exemplo, você pode abrir um prompt de comando com permissões elevadas no computador em que o gateway está em execução e, em seguida, executar um destes comandos:

* Para interromper o serviço, execute este comando:
  
    '''   net stop PBIEgwService   '''
* Para iniciar o serviço, execute este comando:
  
    '''   net start PBIEgwService   '''

### <a name="error-failed-to-create-gateway-please-try-again"></a>Erro: falha ao criar gateway. Tente novamente.
Todos os detalhes estão disponíveis, mas a chamada para o serviço do Power BI retornou um erro. O erro e uma ID de atividade serão exibidos. Isso pode acontecer por diferentes motivos. Você pode coletar e examinar os logs da maneira descrita abaixo para obter mais detalhes.

Isso também pode ser devido a problemas de configuração de proxy. A interface do usuário agora permite a configuração de proxy. Saiba mais sobre como fazer [alterações da configuração de proxy](service-gateway-proxy.md)

### <a name="error-failed-to-update-gateway-details--please-try-again"></a>Erro: falha ao atualizar detalhes do gateway.  Tente novamente.
As informações foram recebidas do serviço do Power BI para o gateway. As informações foram transmitidas para o serviço do Windows local, mas houve uma falha ao retornar. Ou então, uma falha de geração de chave simétrica. A exceção interna será exibida em **Mostrar detalhes**. Você pode coletar e examinar os logs da maneira descrita abaixo para obter mais detalhes.

### <a name="error-power-bi-service-reported-local-gateway-as-unreachable-please-restart-the-gateway-and-try-again"></a>Erro: o serviço do Power BI relatou o gateway local como inacessível. Reinicie o gateway e repita a operação.
No final da configuração, o serviço do Power BI será chamado novamente para validar o gateway. O serviço do Power BI não relata o gateway como *dinâmico*. Reiniciar o serviço do Windows pode permitir que a comunicação seja bem-sucedida. Você pode coletar e examinar os logs da maneira descrita abaixo para obter mais detalhes.

### <a name="script-error-during-sign-into-power-bi"></a>Erro de script durante a conexão no Power BI
Você pode receber um erro de script ao entrar no Power BI como parte da configuração de gateway de dados local. Instalar a seguinte atualização de segurança deve resolver o problema. Isso pode ser instalado por meio do Windows Update.

[MS16-051: atualização de segurança do Internet Explorer: 10 de maio de 2016 (KB 3154070)](https://support.microsoft.com/kb/3154070)

### <a name="gateway-configuration-failed-with-a-null-reference-exception"></a>Falha de configuração do gateway com uma exceção de referência nula
Você pode receber um erro semelhante a este:

        Failed to update gateway details.  Please try again.
        Error updating gateway configuration.

Isso incluirá um rastreamento de pilha, que poderá incluir o seguinte:

        Microsoft.PowerBI.DataMovement.Pipeline.Diagnostics.CouldNotUpdateGatewayConfigurationException: Error updating gateway configuration. ----> System.ArgumentNullException: Value cannot be null.
        Parameter name: serviceSection

Se você estiver atualizando um gateway mais antigo, o arquivo de configuração será preservado. Pode haver uma seção ausente. Quando o gateway tentar ler isso, obteremos a exceção de referência nula acima.

Para corrigir esse problema, faça o seguinte:

1. Desinstale o gateway.
2. Exclua a seguinte pasta:
   
        c:\Program Files\on-premises data gateway
3. Reinstale o gateway.
4. Se preferir, aplique a chave de recuperação para restaurar um gateway existente.

### <a name="support-for-tls-1112"></a>Suporte para TLS 1.1/1.2
Com a atualização de agosto de 2017 e as posteriores, o gateway de dados local usa o protocolo TLS 1.1 ou 1.2 para comunicar-se com o **serviço do Power BI** por padrão. As versões anteriores do gateway de dados local usam o TLS 1.0 por padrão. Em 1º de novembro de 2017, o suporte para o TLS 1.0 será encerrado. Por isso, você deverá atualizar as instalações do gateway de dados local para a versão de agosto de 2017 ou mais recente para garantir que os gateways continuem a funcionar.

É importante observar que o TLS 1.0 ainda é compatível com o gateway de dados local antes de 1º de novembro e é usado pelo gateway como um mecanismo de fallback. Para garantir que todo o tráfego de gateway use o TLS 1.1 ou 1.2 (e evite o uso do TLS 1.0 no gateway), você deverá adicionar ou modificar as seguintes chaves do registro no computador que executa o serviço de gateway:

        [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework\v4.0.30319]"SchUseStrongCrypto"=dword:00000001
        [HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\.NETFramework\v4.0.30319]"SchUseStrongCrypto"=dword:00000001

> [!NOTE]
> A adição ou modificação dessas chaves do Registro aplica a alteração a todos os aplicativos .NET. Para obter informações sobre as alterações no registro que afetam o TLS em outros aplicativos, consulte [Transport Layer Security (TLS) registry settings](https://docs.microsoft.com/windows-server/security/tls/tls-registry-settings) (Configurações de registro do protocolo TLS).
> 
> 

## <a name="data-sources"></a>Fontes de dados
### <a name="error-unable-to-connect-details-invalid-connection-credentials"></a>Erro: impossível conectar. Detalhes: "Credenciais de conexão inválidas"
Em **Mostrar detalhes**, deve ser exibida a mensagem de erro recebida da fonte de dados. Para o SQL Server, você verá algo semelhante ao seguinte.

    Login failed for user 'username'.

Verifique se você tem o nome de usuário correto e a senha. Verifique também se essas credenciais podem se conectar à fonte de dados com êxito. Verifique se a conta que está sendo usada corresponde ao **Método de Autenticação**.

### <a name="error-unable-to-connect-details-cannot-connect-to-the-database"></a>Erro: impossível conectar. Detalhes: "Não é possível se conectar ao banco de dados"
Conseguimos nos conectar ao servidor, mas não ao banco de dados fornecido. Verifique o nome do banco de dados e se as credenciais do usuário têm a permissão apropriada para acessar esse banco de dados.

Em **Mostrar detalhes**, deve ser exibida a mensagem de erro recebida da fonte de dados. Para o SQL Server, você verá algo semelhante ao seguinte.

    Cannot open database "AdventureWorks" requested by the login. The login failed. Login failed for user 'username'.

### <a name="error-unable-to-connect-details-unknown-error-in-data-gateway"></a>Erro: impossível conectar. Detalhes: "Erro desconhecido no gateway de dados"
Esse erro pode ocorrer por diferentes motivos. Não se esqueça de validar que você pode se conectar à fonte de dados do computador que hospeda o gateway. Isso pode ocorrer devido ao fato de o servidor não estar acessível.

Em **Mostrar detalhes**, você verá um código de erro **DM_GWPipeline_UnknownError**.

Você também pode examinar os Logs de Eventos > **Logs de Aplicativos e Serviços** > **Serviço do gateway de dados local** para obter mais detalhes.

### <a name="error-we-encountered-an-error-while-trying-to-connect-to-server-details-we-reached-the-data-gateway-but-the-gateway-cant-access-the-on-premises-data-source"></a>Erro: encontramos um erro ao tentar conectar-se com <server>. Detalhes: "Alcançamos o gateway de dados, mas o gateway não consegue acessar a fonte de dados local".
Não é possível se conectar à fonte de dados especificada. Certifique-se de validar as informações fornecidas para essa fonte de dados.

Em **Mostrar detalhes**, você encontrará um código de erro de **DM_GWPipeline_Gateway_DataSourceAccessError**.

Se a mensagem de erro subjacente for semelhante à seguinte, isso significa que a conta que você está usando para a fonte de dados não é um administrador do servidor para essa instância do Analysis Services. [Saiba mais](https://docs.microsoft.com/sql/analysis-services/instances/grant-server-admin-rights-to-an-analysis-services-instance)

    The 'CONTOSO\account' value of the 'EffectiveUserName' XML for Analysis property is not valid.

Caso a mensagem de erro subjacente seja semelhante à seguinte, isso pode indicar que a conta de serviço do Analysis Services pode não ter o atributo de diretório TGGAU ([token-groups-global-and-universal](https://msdn.microsoft.com/library/windows/desktop/ms680300.aspx)).

    The user name or password is incorrect.

Domínios com acesso de compatibilidade de versões anteriores ao Windows 2000 terão o atributo TGGAU habilitado. No entanto, os domínios criados mais recentemente não habilitarão esse atributo por padrão. Leia mais sobre isso [aqui](https://support.microsoft.com/kb/331951).

Confirme isso fazendo o seguinte:

1. Conecte-se ao computador do Analysis Services no SQL Server Management Studio. Nas propriedades de conexão Avançada, inclua EffectiveUserName para o usuário em questão e veja se isso reproduz o erro.
2. Você pode usar a ferramenta dsacls do Active Directory para validar se o atributo está listado. Essa é a ferramenta normalmente encontrada em um controlador de domínio. Você precisará saber qual é o nome diferenciado de domínio da conta e passá-lo para a ferramenta.
   
        dsacls "CN=John Doe,CN=UserAccounts,DC=contoso,DC=com"
   
    Você deseja ver algo semelhante ao mostrado a seguir nos resultados.
   
            Allow BUILTIN\Windows Authorization Access Group
                                          SPECIAL ACCESS for tokenGroupsGlobalAndUniversal
                                          READ PROPERTY

Para corrigir esse problema, você precisará habilitar o TGGAU na conta usada para o serviço Windows do Analysis Services.

**Outra possibilidade de nome de usuário ou senha incorretos**

Esse erro também poderá ser causado se o servidor do Analysis Services estiver em um domínio diferente dos usuários e não houver uma relação de confiança bidirecional estabelecida.

Você precisará trabalhar com seus administradores de domínio para verificar a relação de confiança entre os domínios.

**Não é possível ver as fontes de dados do gateway de dados na experiência "Obter Dados" do Analysis Services por meio do serviço do Power BI**

Confira se sua conta está listada na guia **Usuários** da fonte de dados na configuração do gateway. Se não tiver acesso ao gateway, verifique com o administrador do gateway e solicite a verificação. Somente as contas na lista **Usuários** verão a fonte de dados relacionada na lista do Analysis Services.

## <a name="datasets"></a>Conjuntos de dados
### <a name="error-there-is-not-enough-space-for-this-row"></a>Erro: não há espaço suficiente para esta linha.
Isso ocorrerá se você tiver uma única linha com um tamanho maior que 4 MB. Você precisará determinar qual linha é proveniente da fonte de dados e tentar filtrá-la ou reduzir o tamanho desta linha.

### <a name="error-the-server-name-provided-doesnt-match-the-server-name-on-the-sql-server-ssl-certificate"></a>Erro: O nome fornecido para o servidor não corresponde ao nome do servidor no certificado SSL do SQL Server.
Isso pode ocorrer quando o certificado CN é para o nome de domínio totalmente qualificado (FQDN) do servidor, mas você somente forneceu o nome NetBIOS para o servidor. Isso causará uma incompatibilidade para o certificado. Para resolver esse problema, você precisará criar o nome do servidor e do arquivo PBIX na fonte de dados do gateway, para usar o FQDN do servidor.

### <a name="i-dont-see-the-on-premises-data-gateway-persent-when-configuring-scheduled-refresh"></a>Não consigo ver o gateway de dados local presente ao configurar a atualização agendada.
Isso pode ser devido a alguns cenários diferentes.

1. O nome do servidor e do banco de dados não corresponde entre o que foi inserido no Power BI Desktop e a fonte de dados configurada para o gateway. Eles precisam ter os mesmos valores. Eles não diferenciam maiúsculas de minúsculas.
2. Sua conta não está listada na guia **Usuários** da fonte de dados na configuração do gateway. Você precisará solicitar ao administrador do gateway para ser adicionado à lista.
3. O arquivo do Power BI Desktop contém dados de várias fontes e nem todas as fontes de dados estão configuradas com o gateway. Você precisará ter cada fonte de dados definida com o gateway para que o gateway apareça na Atualização Agendada.

### <a name="error-the-received-uncompressed-data-on-the-gateway-client-has-exceeded-limit"></a>Erro: os dados descompactados recebidos no cliente de gateway excederam o limite.
A limitação exata é de 10 GB de dados descompactados por tabela. Se você estiver tendo esse problema, há boas opções para otimizá-lo e evitá-lo. Especificamente, será útil reduzir o uso de valores de cadeia de caracteres longos e altamente repetitivos e, em vez disso, usar uma chave normalizada ou remover a coluna (se ela não estiver em uso).

## <a name="reports"></a>Relatórios
### <a name="report-could-not-access-the-data-source-because-you-do-not-have-access-to-our-data-source-via-an-on-premises-data-gateway"></a>O relatório não pôde acessar a fonte de dados porque você não tem acesso à nossa fonte de dados por meio de um gateway de dados local.
Isso geralmente é causado por um dos motivos a seguir.

1. As informações da fonte de dados não correspondem as que estão no conjunto de dados subjacente. O servidor e o nome do banco de dados precisam corresponder à fonte de dados definida para o gateway de dados local e às informações fornecidas no Power BI Desktop. Se você usar um Endereço IP no Power BI Desktop, a fonte de dados do gateway de dados local também precisará usar um Endereço IP.
2. Não há uma fonte de dados disponível em nenhum gateway de sua organização. É possível configurar a fonte de dados em um gateway de dados local novo ou existente.

### <a name="error-data-source-access-error-please-contact-the-gateway-administrator"></a>Detalhes: erro de acesso à fonte de dados. Entre em contato com o administrador do gateway.
Se este relatório estiver usando uma conexão dinâmica do Analysis Services, você poderá ter problemas ao passar um valor para EffectiveUserName que não seja válido ou que não tenha permissões no computador do Analysis Services. Normalmente, um problema de autenticação ocorre devido ao fato de que o valor passado para EffectiveUserName não corresponde a um nome UPN local.

Para confirmar isso, faça o seguinte:

1. Encontre o nome de usuário efetivo nos [logs do gateway](#logs).
2. Depois de obter o valor que está sendo passado, valide se ele está correto. Se ele for seu usuário, você poderá usar o comando a seguir em um prompt de comando para ver qual deve ser o UPN. O UPN será parecido com um endereço de email.
   
        whoami /upn

Se preferir, é possível ver o que o Power BI obtém do Azure Active Directory.

1. Navegue até [https://graphexplorer.cloudapp.net](https://graphexplorer.cloudapp.net).
2. Selecione **Entrar** no canto superior direito.
3. Execute a consulta a seguir. Você verá uma resposta JSON bem grande.
   
        https://graph.windows.net/me?api-version=1.5
4. Procure **userPrincipalName**.

Se o UPN do Azure Active Directory não corresponder ao UPN local do Active Directory, você poderá usar o recurso [Mapear nomes de usuário](service-gateway-enterprise-manage-ssas.md#map-user-names) para substituí-lo por um valor válido. Se preferir, você pode trabalhar com seu administrador de locatários, ou com o administrador local do Active Directory, para alterar o UPN.

<!-- Shared Troubleshooting Firewall/Proxy Include -->
[!INCLUDE [gateway-onprem-tshoot-firewall-include](./includes/gateway-onprem-tshoot-firewall-include.md)]

É possível encontrar a região do datacenter em que você está fazendo o seguinte:

1. Selecione **?** na parte superior direita do serviço do Power BI.
2. Selecione **Sobre o Power BI**.
3. Sua região de dados será listada em **Seus dados estão armazenados em**.
   
    ![](media/service-gateway-onprem-tshoot/power-bi-data-region.png)

Se você ainda não conseguiu descobri-la, tente obter um rastreamento de rede usando uma ferramenta como [fiddler](#fiddler) ou netsh, embora esses sejam métodos de coleta avançados e você possa precisar de assistência para analisar os dados coletados. Entre em contato com o [suporte](https://support.microsoft.com) para obter assistência.

## <a name="performance"></a>Desempenho
<iframe width="560" height="315" src="https://www.youtube.com/embed/IJ_DJ30VNk4?showinfo=0" frameborder="0" allowfullscreen></iframe>

### <a name="performance-counters"></a>Contadores de desempenho
Existem inúmeros contadores de desempenho que podem ser usados para medir as atividades do gateway. Eles podem ser úteis para entender quando há uma grande carga de atividade e talvez seja necessário criar um novo gateway. Esses contadores não refletirão a duração de algo.

Eles podem ser acessados por meio da ferramenta Monitor de Desempenho do Windows.

![](media/service-gateway-onprem-tshoot/gateway-perfmon.png)

Há agrupamentos gerais desses contadores.

| Tipo de contador | Descrição |
| --- | --- |
| ADO.NET |É usado para qualquer conexão de DirectQuery. |
| ADOMD |É usado para o Analysis Services 2014 e anterior. |
| OLEDB |É usado por determinadas fontes de dados. Inclui o SAP HANA e o Analysis Service 2016 ou posterior. |
| Mashup |Inclui qualquer fonte de dados importados. Se estiver agendando uma atualização ou fazendo uma atualização sob demanda, esse processo passará pelo mecanismo de mashup. |

Aqui está uma lista de contadores de desempenho disponíveis.

| Contador | Descrição |
| --- | --- |
| Número de conexões abertas do ADO.NET executadas por segundo |Número de ações de conexões abertas do ADO.NET executadas por segundo (com êxito ou falha). |
| Número de conexões abertas do ADO.NET com falha por segundo |Número de ações de conexões abertas do ADO.NET com falha por segundo. |
| Número de consultas do ADO.NET executadas por segundo |Número de consultas do ADO.NET executadas por segundo (com êxito ou falha). |
| Número de consultas do ADO.NET com falha por segundo |Número de consultas do ADO.NET com falha executadas por segundo. |
| Número de conexões abertas do ADOMD executadas por segundo |Número de ações de conexões abertas do ADOMD executadas por segundo (com êxito ou falha). |
| Número de conexões abertas do ADOMD com falha por segundo |Número de ações de conexões abertas do ADOMD com falha por segundo. |
| Número de consultas do ADOMD executadas por segundo |Número de consultas do ADOMD executadas por segundo (com êxito ou falha). |
| Número de consultas do ADOMD com falha por segundo |Número de consultas do ADOMD com falha executadas por segundo. |
| Número de todas as conexões abertas executadas por segundo |Número de ações de conexões abertas executadas por segundo (com êxito ou falha). |
| Número de todas as conexões abertas com falha por segundo |Número de ações de conexões abertas com falha executadas por segundo. |
| Número de todas as consultas executadas por segundo |Número de consultas executadas por segundo (com êxito ou falha). |
| Número de itens no pool de conexões do ADO.NET |Número de itens no pool de conexões do ADO.NET. |
| Número de itens no pool de conexões do OLEDB |Número de itens no pool de conexões do OLEDB. |
| Número de itens no pool de Barramentos de Serviço |Número de itens no pool de Barramentos de Serviço. |
| Número de conexões abertas do Mashup executadas por segundo |Número de ações de conexões abertas do Mashup executadas por segundo (com êxito ou falha). |
| Número de conexões abertas do Mashup com falha por segundo |Número de ações de conexões abertas do Mashup com falha por segundo. |
| Número de consultas do Mashup executadas por segundo |Número de consultas do Mashup executadas por segundo (com êxito ou falha). |
| Número de consultas do Mashup com falha por segundo |Número de consultas do Mashup com falha executadas por segundo |
| Número de consultas do OLEDB de vários conjuntos de resultados com falha por segundo |Número de consultas do OLEDB de vários conjuntos de resultados com falha por segundo. |
| Número de consultas do OLEDB de vários conjuntos de resultados por segundo |Número de consultas do OLEDB de vários conjuntos de resultados executadas por segundo (com êxito ou falha). |
| Número de conexões abertas OLEDB executadas por segundo |Número de ações de conexões abertas do OLEDB executadas por segundo (com êxito ou falha). |
| Número de conexões abertas do OLEDB com falha por segundo |Número de ações de conexões abertas do OLEDB com falha por segundo. |
| Número de consultas do OLEDB executadas por segundo |Número de consultas do OLEDB de vários conjuntos de resultados executadas por segundo (com êxito ou falha). |
| Número de consultas do OLEDB com falha por segundo |Número de consultas do OLEDB de vários conjuntos de resultados com falha executadas por segundo. |
| Número de consultas do OLEDB de conjunto de resultados único por segundo |Número de consultas do OLEDB de conjunto de resultados único executadas por segundo (com êxito ou falha). |
| Número de consultas com falha por segundo |Número de consultas com falha executadas por segundo. |
| Número de consultas do OLEDB de conjunto de resultados único com falha por segundo |Número de consultas do OLEDB de conjunto de resultados único com falha executadas por segundo. |

## <a name="reviewing-slow-performing-queries"></a>Examinando consultas com desempenho lento
Você pode achar que a resposta pelo gateway está lenta. Isso pode ser em consultas DirectQuery ou ao atualizar o conjunto de dados importado. Você pode habilitar um registro em log adicional para emitir as consultas e seus tempos para ajudar a entender o que está com desempenho lento. Ao encontrar alguma consulta de execução longa, poderá ser necessário fazer modificações adicionais na fonte de dados para ajustar o desempenho da consulta. Por exemplo, ajustando os índices para uma consulta do SQL Server.

Você precisará modificar dois arquivos de configuração para determinar a duração de uma consulta.

### <a name="microsoftpowerbidatamovementpipelinegatewaycoredllconfig"></a>Microsoft.PowerBI.DataMovement.Pipeline.GatewayCore.dll.config
No arquivo *Microsoft.PowerBI.DataMovement.Pipeline.GatewayCore.dll.config*, altere o valor de `EmitQueryTraces` de `False` para `True`. Este arquivo está localizado, por padrão, em *C:\Arquivos de Programas\Gateway de dados local*. Ao habilitar `EmitQueryTraces`, começarão ser registradas em log as consultas enviadas do gateway para uma fonte de dados.

> [!IMPORTANT]
> Habilitar EmitQueryTraces pode aumentar o tamanho do log significativamente, dependendo do uso de gateway. Depois de examinar os logs, você desejará definir EmitQueryTraces como False. Não é recomendável deixar esta configuração habilitada a longo prazo.
> 
> 

```
<setting name="EmitQueryTraces" serializeAs="String">
    <value>True</value>
</setting>
```

**Exemplo de entrada de consulta**

```
DM.EnterpriseGateway Information: 0 : 2016-09-15T16:09:27.2664967Z DM.EnterpriseGateway    4af2c279-1f91-4c33-ae5e-b3c863946c41    d1c77e9e-3858-4b21-3e62-1b6eaf28b176    MGEQ    c32f15e3-699c-4360-9e61-2cc03e8c8f4c    FF59BC20 [DM.GatewayCore] Executing query (timeout=224) "<pi>
SELECT
TOP (1000001) [t0].[ProductCategoryName],[t0].[FiscalYear],SUM([t0].[Amount])
 AS [a0]
FROM
(
(select [$Table].[ProductCategoryName] as [ProductCategoryName],
    [$Table].[ProductSubcategory] as [ProductSubcategory],
    [$Table].[Product] as [Product],
    [$Table].[CustomerKey] as [CustomerKey],
    [$Table].[Region] as [Region],
    [$Table].[Age] as [Age],
    [$Table].[IncomeGroup] as [IncomeGroup],
    [$Table].[CalendarYear] as [CalendarYear],
    [$Table].[FiscalYear] as [FiscalYear],
    [$Table].[Month] as [Month],
    [$Table].[OrderNumber] as [OrderNumber],
    [$Table].[LineNumber] as [LineNumber],
    [$Table].[Quantity] as [Quantity],
    [$Table].[Amount] as [Amount]
from [dbo].[V_CustomerOrders] as [$Table])
)
 AS [t0]
GROUP BY [t0].[ProductCategoryName],[t0].[FiscalYear] </pi>"
```

### <a name="microsoftpowerbidatamovementpipelinegatewaycoredllconfig"></a>Microsoft.PowerBI.DataMovement.Pipeline.GatewayCore.dll.config
No arquivo *Microsoft.PowerBI.DataMovement.Pipeline.Diagnostics.dll.config*, altere o valor de `TraceVerbosity` de `4` para `5`. Este arquivo está localizado, por padrão, em *C:\Arquivos de Programas\Gateway de dados local*. A alteração dessa configuração começará a registrar entradas detalhadas no log de gateway. Isso inclui entradas que mostram a duração.

> [!IMPORTANT]
> Habilitar o TraceVerbosity para `5` pode aumentar o tamanho do log significativamente, dependendo do uso do gateway. Depois de examinar os logs, você poderá definir TraceVerbosity como `4`. Não é recomendável deixar esta configuração habilitada a longo prazo.
> 
> 

```
<setting name="TracingVerbosity" serializeAs="String">
    <value>5</value>
</setting>
```

<a name="activities"></a>

### <a name="activity-types"></a>Tipos de atividade
| Tipo de atividade | Descrição |
| --- | --- |
| MGEQ |Consultas executadas no ADO.NET. Estão inclusas outras fontes de dados do DirectQuery. |
| MGEO |Consultas executadas no OLEDB. Inclui o SAP HANA e o Analysis Services 2016. |
| MGEM |Consultas executadas do mecanismo de Mashup. Usadas com conjuntos de dados importados que usam a atualização agendada ou a atualização sob demanda. |

### <a name="determine-the-duration-of-a-query"></a>Determinar a duração de uma consulta
Para determinar o tempo necessário para consultar a fonte de dados, você pode fazer o seguinte.

1. Abra o log de gateway.
2. Pesquise um [Tipo de Atividade](#activities) para localizar a consulta. Um exemplo seria MGEQ.
3. Anote o segundo GUID, que é a ID de solicitação.
4. Continue a pesquisar o MGEQ até encontrar a entrada FireActivityCompletedSuccessfullyEvent com a duração. Você pode verificar se a entrada tem a mesma ID de solicitação. A duração estará em milissegundos.
   
        DM.EnterpriseGateway Verbose: 0 : 2016-09-26T23:08:56.7940067Z DM.EnterpriseGateway    baf40f21-2eb4-4af1-9c59-0950ef11ec4a    5f99f566-106d-c8ac-c864-c0808c41a606    MGEQ    21f96cc4-7496-bfdd-748c-b4915cb4b70c    B8DFCF12 [DM.Pipeline.Common.TracingTelemetryService] Event: FireActivityCompletedSuccessfullyEvent (duration=5004)
   
   > [!NOTE]
   > FireActivityCompletedSuccessfullyEvent é uma entrada detalhada. Essa entrada apenas será registrada se o TraceVerbosity estiver no nível 5.
   > 
   > 

<!-- Shared Troubleshooting tools Include -->
[!INCLUDE [gateway-onprem-tshoot-tools-include](./includes/gateway-onprem-tshoot-tools-include.md)]

### <a name="refresh-history"></a>Histórico de atualização
Ao usar o gateway para atualização agendada, o **Histórico de Atualização** pode ajudá-lo a ver quais erros ocorreram, além de fornecer dados úteis caso precise criar uma solicitação de suporte. Você pode exibir as atualizações programadas ou sob demanda. Aqui está como você pode acessar o **Histórico de atualização**.

1. No painel de navegação do Power BI, em **Conjuntos de Dados**, selecione um conjunto de dados &gt; Abrir Menu &gt; **Agendar Atualização**.
   
    ![](media/service-gateway-onprem-tshoot/scheduled-refresh.png)
2. Em **Configurações de...** &gt; **Agendar Atualização**, selecione **Histórico de Atualização**.
   
    ![](media/service-gateway-onprem-tshoot/scheduled-refresh-2.png)
   
    ![](media/service-gateway-onprem-tshoot/refresh-history.png)

Para obter informações adicionais sobre como solucionar problemas de cenários de atualização, examine o artigo [Solução de problemas de cenários de atualização](refresh-troubleshooting-refresh-scenarios.md).

## <a name="next-steps"></a>Próximas etapas
[Definindo as configurações de proxy dos gateways do Power BI](service-gateway-proxy.md)  
[Gateway de dados local](service-gateway-onprem.md)  
[Detalhes sobre o gateway de dados local](service-gateway-onprem-indepth.md)  
[Gerenciar sua fonte de dados – Analysis Services](service-gateway-enterprise-manage-ssas.md)  
[Gerenciar sua fonte de dados – SAP HANA](service-gateway-enterprise-manage-sap.md)  
[Gerenciar sua fonte de dados – SQL Server](service-gateway-enterprise-manage-sql.md)  
[Gerenciar sua fonte de dados – Importar/Atualização agendada](service-gateway-enterprise-manage-scheduled-refresh.md)  
Mais perguntas? [Experimente a Comunidade do Power BI](http://community.powerbi.com/)

