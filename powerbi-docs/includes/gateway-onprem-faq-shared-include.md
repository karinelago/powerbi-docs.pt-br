## <a name="general"></a>Geral
**Pergunta:** Qual é o nome do serviço Windows real?  
**Resposta:** o gateway é chamado de serviço do gateway de dados local em Serviços

**Pergunta:** Quais são os requisitos para o gateway?  
**Resposta:** Dê uma olhada na seção Requisitos do [artigo principal sobre gateway](../service-gateway-onprem.md).

**Pergunta:** Quais fontes de dados têm suporte no gateway?  
**Resposta:** Confira a tabela de fontes de dados no [artigo principal sobre gateway](../service-gateway-onprem.md).

**Pergunta:** Preciso de um gateway para fontes de dados de nuvem como o Banco de Dados SQL do Azure?  
**Resposta:** Não. O serviço poderá se conectar à fonte de dados sem um gateway.

**Pergunta:** Existem conexões de entrada para o gateway por meio da nuvem?  
**Resposta:** não. O gateway usa conexões de saída ao Barramento de Serviço do Azure.

**Pergunta:** O que acontecerá se eu bloquear as conexões de saída? O que preciso abrir?  
**Resposta:** Veja a [lista de portas](../service-gateway-onprem.md#ports) e hosts usados pelo gateway.

**Pergunta:** O gateway precisa ser instalado no mesmo computador que a fonte de dados?  
**Resposta:** não. O gateway será conectado à fonte de dados usando as informações de conexão fornecidas. Nesse sentido, considere o gateway como um aplicativo cliente. Ele apenas precisa conseguir se conectar ao nome do servidor que foi fornecido.

**Pergunta:** Qual é a latência para a execução de consultas em uma fonte de dados do gateway? Qual é a melhor arquitetura?  
**Resposta:** É recomendável ter o gateway o mais próximo possível à fonte de dados a fim de evitar a latência de rede. Se você conseguir instalar o gateway na fonte de dados real, isso minimizará a latência introduzida. Considere também os datacenters. Por exemplo, caso seu serviço esteja fazendo uso do datacenter do Oeste dos EUA e você tiver o SQL Server hospedado em uma VM do Azure, é recomendável ter a VM do Azure também no Oeste dos EUA. Isso minimizará a latência e evitará encargos de saída na VM do Azure.

**Pergunta:** Há algum requisito de largura de banda de rede?  
**Resposta:** É recomendável ter uma taxa de transferência suficiente para sua conexão de rede. Cada ambiente é diferente e isso também depende da quantidade de dados enviados. O uso do ExpressRoute pode ajudar a garantir um nível de taxa de transferência entre os datacenters locais e do Azure.

Você pode usar o aplicativo [Azure Speed Test](http://azurespeedtest.azurewebsites.net/) de terceiros para ajudar a medir sua taxa de transferência.

**Pergunta:** O serviço Windows do gateway pode ser executado com uma conta do Azure Active Directory?  
**Resposta:** não. O serviço Windows precisa ter uma conta válida do Windows. Por padrão, ele será executado com o SID do Serviço, *NT SERVICE\PBIEgwService*.

**Pergunta:** Como os resultados são enviados de volta para a nuvem?  
**Resposta:** Isso é feito por meio do Barramento de Serviço do Azure. Para obter mais informações, veja [como isso funciona](../service-gateway-onprem.md#how-the-gateway-works).

**Pergunta:** Em que local minhas credenciais são armazenadas?  
**Resposta:** As credenciais que você inserir para uma fonte de dados são armazenadas criptografadas no serviço de nuvem do gateway. As credenciais são descriptografadas no gateway local.

**Pergunta:** Posso colocar o gateway em uma rede de perímetro (também conhecida como DMZ, zona desmilitarizada e sub-rede filtrada)?  
**Resposta:** O gateway precisa de conectividade com a fonte de dados. Se a fonte de dados não estiver acessível na sua rede de perímetro, o gateway não poderá se conectar a ela. Por exemplo, o SQL Server talvez não esteja na sua rede de perímetro. Além disso, não é possível se conectar ao SQL Server por meio da rede de perímetro. Se você tivesse colocado o gateway na rede de perímetro, ele não seria capaz de acessar o SQL Server.

**Pergunta:** é possível forçar o gateway a usar o tráfego HTTPS com o Barramento de Serviço do Azure em vez do TCP?  
**Resposta:** Sim. No entanto, isso reduzirá o desempenho significativamente. Talvez você queira modificar o arquivo *Microsoft.PowerBI.DataMovement.Pipeline.GatewayCore.dll.config*. Convém alterar o valor de `AutoDetect` para `Https`. Este arquivo está localizado, por padrão, em *C:\Arquivos de Programas\Gateway de dados local*.

**Pergunta:** preciso colocar a lista de IP do Datacenter do Azure na lista branca? Onde posso obter a lista?  
**Resposta:** se você estiver bloqueando o tráfego de saída de IP, talvez seja necessário colocar a lista de IP do Datacenter do Azure na lista branca. Atualmente, o gateway se comunicará com o Barramento de Serviço do Azure usando o endereço IP, além do nome de domínio totalmente qualificado. A lista de IP do Datacenter do Azure é atualizada semanalmente. Você pode baixar a [lista de IP do Data Center do Microsoft Azure](https://www.microsoft.com/download/details.aspx?id=41653).

```
<setting name="ServiceBusSystemConnectivityModeString" serializeAs="String">
    <value>Https</value>
</setting>
```

## <a name="high-availabilitydisaster-recovery"></a>Alta Disponibilidade/Recuperação de Desastre
**Pergunta:** Existem planos para habilitar cenários de alta disponibilidade com o gateway?  
**Resposta:** Sim, essa é uma área de investimento ativo da equipe do Power BI. Fique ligado no [blog do Power BI](https://powerbi.microsoft.com/blog/) para obter mais atualizações sobre esse recurso.

**Pergunta:** Quais são as opções disponíveis para a recuperação de desastre?  
**Resposta:** Você pode usar a chave de recuperação para restaurar ou mover um gateway. Ao instalar o gateway, forneça a chave de recuperação.

**Pergunta:** Qual é a vantagem de usar a chave de recuperação?  
**Resposta:** Ela fornece uma maneira de migrar ou recuperar suas configurações de gateway. Também é usada para a recuperação de desastre.

## <a name="troubleshooting"></a>Solução de problemas
**Pergunta:** Em que local os logs do gateway estão localizados?  
**Resposta:** Confira a seção Ferramentas do [artigo sobre solução de problemas](../service-gateway-onprem-tshoot.md#tools-for-troubleshooting).

**Pergunta:** Como posso ver quais consultas estão sendo enviadas à fonte de dados local?  
**Resposta:** Você pode habilitar o rastreamento de consultas.  Isso incluirá as consultas que estão sendo enviadas. Lembre-se de alterá-lo para o valor original quando concluir a solução de problemas. Habilitar o rastreamento de consultas fará com que os logs sejam maiores.

Você também pode examinar as ferramentas que sua fonte de dados tem para o rastreamento de consultas. Por exemplo, para o SQL Server e o Analysis Services, é possível usar os Eventos Estendidos ou o SQL Profiler.

