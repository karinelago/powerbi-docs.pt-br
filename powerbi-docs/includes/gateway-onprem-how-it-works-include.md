## <a name="how-the-gateway-works"></a>Como funciona o gateway
![on-prem-data-gateway-how-it-works](./media/gateway-onprem-how-it-works-include/on-prem-data-gateway-how-it-works.png)

Primeiro vamos examinar o que acontece quando um usuário interage com um elemento conectado a uma fonte de dados local. 

> [!NOTE]
> Para o Power BI, você precisará configurar uma fonte de dados para o gateway.
> 
> 

1. Uma consulta será criada pelo serviço de nuvem, juntamente com as credenciais criptografadas para a fonte de dados local, e enviada à fila para ser processada pelo gateway.
2. O serviço de nuvem do gateway analisará a consulta e enviará por push a solicitação para o [Barramento de Serviço do Azure](https://azure.microsoft.com/documentation/services/service-bus/).
3. O gateway de dados local pesquisa o [Barramento de Serviço do Azure](https://azure.microsoft.com/documentation/services/service-bus/) em busca de solicitações pendentes.
4. O gateway obtém a consulta, descriptografa as credenciais e conecta-se à(s) fonte(s) de dados com essas credenciais.
5. O gateway envia a consulta à fonte de dados para execução.
6. Os resultados são enviados da fonte de dados, de volta ao gateway e, em seguida, ao serviço de nuvem. Em seguida, o serviço usa os resultados.

