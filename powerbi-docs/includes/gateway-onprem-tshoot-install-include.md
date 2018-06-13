## <a name="update-to-the-latest-version"></a>Atualize para a versão mais recente
Muitos problemas podem surgir quando a versão de gateway estiver desatualizada.  É uma boa prática geral ter certeza que você está na última versão.  Se não tiver atualizado o gateway por um mês ou mais, considere a possibilidade de instalar a última versão do gateway e tentar reproduzir o problema.

## <a name="common-issues"></a>Problemas comuns
Aqui estão algumas resoluções e problemas comuns que ajudaram um número de clientes em ambientes com acesso restrito à Internet.

### <a name="authentication-to-proxy-server"></a>Autenticação com o servidor proxy
Seu proxy pode exigir autenticação de uma conta de usuário do domínio. Por padrão, o gateway usa um SID de Serviço para o log de serviço Windows no usuário. Alterar o usuário de logon para um usuário de domínio pode ajudar com isso. Para obter mais informações, veja [Alterando a conta de serviço do gateway para um usuário de domínio](../service-gateway-proxy.md#changing-the-gateway-service-account-to-a-domain-user).

### <a name="your-proxy-only-allows-ports-80-and-443-traffic"></a>Seu proxy permite apenas tráfego pelas portas 80 e 443
Alguns proxies restringem o tráfego exclusivamente para as portas 80 e 443. Por padrão, a comunicação com o Barramento de Serviço do Azure ocorrerá em outras portas que não a 443.

Você pode forçar o gateway para se comunicar com o Barramento de Serviço do Azure usando HTTPS em vez de TCP direto. Você precisará modificar o arquivo *Microsoft.PowerBI.DataMovement.Pipeline.GatewayCore.dll.config*. Altere o valor de `AutoDetect` para `Https`. Este arquivo está localizado, por padrão, em *C:\Arquivos de Programas\Gateway de dados local*.

```
<setting name="ServiceBusSystemConnectivityModeString" serializeAs="String">
    <value>Https</value>
</setting>
```

## <a name="installation"></a>Instalação
### <a name="error-failed-to-add-user-to-group---2147463168---pbiegwservice---performance-log-users---"></a>Erro: falha ao adicionar usuário ao grupo.  (-2147463168   PBIEgwService   Usuários de Log de Desempenho)
Você poderá receber esse erro se estiver tentando instalar o gateway em um controlador de domínio. Não há suporte para a implantação em um controlador de domínio. Você precisará implantar o gateway em um computador que não seja um controlador de domínio.

### <a name="installation-fails"></a>Falha na instalação
Você poderá encontrar falhas na instalação se o software antivírus do computador de instalação estiver desatualizado. Você pode atualizar a instalação do antivírus ou desabilitá-lo apenas até a instalação do gateway ser concluída e habilitá-lo novamente.

