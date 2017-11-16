## <a name="firewall-or-proxy"></a>Firewall ou proxy
Para obter informações sobre como fornecer informações de proxy para o gateway, veja [Configuring proxy settings for the Power BI Gateways](../service-gateway-proxy.md) (Definindo as configurações de proxy dos Power BI Gateways).

É possível testar para ver se seu firewall, ou proxy, pode estar bloqueando as conexões, executando [Test-NetConnection](https://technet.microsoft.com/library/dn372891.aspx) em um prompt do PowerShell. Isso testará a conectividade com o Barramento de Serviço do Azure. Isso apenas testa a conectividade de rede e não tem nenhuma relação com o serviço do servidor de nuvem nem com o gateway. Isso ajuda a determinar se seu computador pode realmente acessar a Internet.

    Test-NetConnection -ComputerName watchdog.servicebus.windows.net -Port 9350

> [!NOTE]
> Test-NetConnection só está disponível no Windows Server 2012 R2 e versões posteriores. Também está disponível no Windows 8.1 e versões posteriores. Em versões anteriores do sistema operacional, é possível usar o Telnet para testar a conectividade da porta.
> 
> 

Os resultados devem ser parecidos ao mostrado a seguir. A diferença será em TcpTestSucceeded. Se **TcpTestSucceeded** não for *true*, isso indica que você poderá estar sendo bloqueado por um firewall.

    ComputerName           : watchdog.servicebus.windows.net
    RemoteAddress          : 70.37.104.240
    RemotePort             : 5672
    InterfaceAlias         : vEthernet (Broadcom NetXtreme Gigabit Ethernet - Virtual Switch)
    SourceAddress          : 10.120.60.105
    PingSucceeded          : False
    PingReplyDetails (RTT) : 0 ms
    TcpTestSucceeded       : True

Se você quiser fazer uma verificação completa, substitua os valores de **ComputerName** e **Port** por aqueles listados para [portas](../service-gateway-onprem.md#ports)

O firewall também pode estar bloqueando as conexões que o Barramento de Serviço do Azure estabelece com os datacenters do Azure. Se este for o caso, será recomendável adicionar à lista branca (desbloquear) todos os endereços IP da sua região para os data centers. Você pode obter uma lista de endereços IP do Azure [aqui](https://www.microsoft.com/download/details.aspx?id=41653).

