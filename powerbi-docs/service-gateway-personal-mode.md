---
title: Gateway de dados local (modo pessoal)
description: Gateway de dados para o Power BI que os usuários podem usar para se conectar a dados locais
services: powerbi
documentationcenter: ''
author: davidiseminger
manager: kfile
backup: ''
editor: ''
tags: ''
qualityfocus: no
qualitydate: ''
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 12/14/2017
ms.author: davidi
LocalizationGroup: Gateways
ms.openlocfilehash: 777e5f27954890fe842096c0f2633f6803ebf319
ms.sourcegitcommit: 65426de556cd7207cbc4f478198664e25c33a769
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/30/2018
---
# <a name="on-premises-data-gateway-personal-mode"></a>Gateway de dados local (modo pessoal)
É possível usar fontes de dados locais e criar relatórios e dashboards do Power BI usando um gateway. Um **gateway** é um software que facilita o acesso a dados armazenados em uma rede privada local e permite que você use esses dados em serviços online, como o **Serviço do Power BI**. O **Gateway de dados local (modo pessoal)** é uma atualização lançada recentemente do Gateway do Power BI, que permite que os usuários instalem um gateway em seu próprio computador e tenham acesso a dados locais.

![](media/service-gateway-personal-mode/gateway-personal-mode_00.png)

> [!NOTE]
> O **Gateway de dados local (modo pessoal)** substitui a versão anterior compatível do gateway pessoal, chamada **Power BI Gateway – Personal**. O gateway pessoal anterior continuará funcionando apenas até 31 de julho de 2017. Consulte as seções abaixo para obter informações sobre como atualizar para a nova versão.
> 
> 

## <a name="features-of-the-on-premises-data-gateway-personal-mode"></a>Recursos do Gateway de dados local (modo pessoal)
Com o lançamento do **Gateway de dados local (modo pessoal)**, um conjunto de recursos e melhorias agora estão disponíveis. Na versão anterior do gateway pessoal (que se chama **Power BI Gateway – Personal**), sua implementação impunha algumas limitações. Assim como ocorreu com muitos produtos do Power BI, ouvimos as necessidades e solicitações dos clientes e como eles usavam o produto. Como resultado, o **Gateway de dados local (modo pessoal)** foi reformulado completamente e agora inclui os seguintes recursos e aprimoramentos:

* **Maior confiabilidade** – a nova versão do gateway pessoal aumentou a confiabilidade com relação à versão anterior, devido a melhorias no software estrutural e no código.
* **Extensibilidade avançada** – como parte das melhorias no software estrutural, recursos adicionais poderão ser adicionados facilmente ao gateway pessoal assim que se tornarem disponíveis.
* **Excluir o gateway pessoal do serviço do Power BI** – com a nova versão, agora você pode excluir seu gateway pessoal de dentro do **serviço do Power BI**.
* **Logs de configuração e serviço** – a nova versão permite que você exporte facilmente logs de configuração e serviço para um arquivo .zip, com um único clique.

## <a name="installing-on-premises-data-gateway-personal-mode"></a>Instalando o Gateway de dados local (modo pessoal)
Para instalar o **Gateway de dados local (modo pessoal)** sem ter a versão anterior do gateway instalada, selecione o ícone de engrenagem no **serviço do Power BI** e selecione **Gateway de Dados**.

![](media/service-gateway-personal-mode/gateway-personal-mode_02.png)

Também é possível baixar o gateway [neste local](https://go.microsoft.com/fwlink/?LinkId=820925&clcid=0x409). Você pode seguir as etapas de instalação e, como o processo de instalação permite que você instale qualquer uma das versões do gateway (o gateway padrão, que pode ser compartilhado com outras pessoas ou o modo pessoal), certifique-se de selecionar **Gateway de dados local (modo pessoal)** quando for perguntado qual versão do gateway você deseja instalar.

### <a name="updating-from-the-previous-personal-gateway"></a>Atualizando do gateway pessoal anterior
Se você já tiver o **Power BI Gateway – Personal** instalado, será solicitado que você instale a nova versão aprimorada do gateway pessoal quando você exibir **Conjuntos de Dados** em **Configurações** no **serviço do Power BI**.

![](media/service-gateway-personal-mode/gateway-personal-mode_03.png)

Quando selecionar um conjunto de dados e, em seguida, selecionar **Conexão de Gateway**, você será notificado de que uma versão nova e aprimorada do gateway pessoal está disponível. Quando isso acontecer, selecione **Instalar agora**.

![](media/service-gateway-personal-mode/gateway-personal-mode_04.png)

> [!NOTE]
> Se você estiver executando a versão anterior do **Power BI Gateway – personal** como um processo com privilégios elevados, certifique-se de iniciar o processo de instalação do novo gateway com privilégios elevados também, para que as credenciais de seu conjunto de dados possam ser atualizadas automaticamente. Caso contrário, você precisará atualizar as credenciais do conjunto de dados manualmente.
> 
> 

Você percorrerá o processo de atualização, após o qual verá que a instalação foi bem-sucedida. Não feche as coisas ainda, há uma última etapa.

![](media/service-gateway-personal-mode/gateway-personal-mode_05.png)

Esta é a última etapa. Depois que o novo gateway pessoal estiver instalado (com a última tela de instalação ainda visível), entre no **serviço do Power BI** e aguarde até ver que o gateway está online, conforme mostrado na imagem a seguir.

![](media/service-gateway-personal-mode/gateway-personal-mode_06.png)

Se você tiver atualizado o gateway pessoal no mesmo computador em que o gateway anterior foi instalado, suas credenciais serão atualizadas automaticamente e todas as atividades de atualização passarão pelo novo gateway. Se o gateway anterior tiver sido instalado em um computador diferente, você precisará atualizar suas credenciais em determinados conjuntos de dados. Na imagem anterior, observe a lista de conjuntos de dados na janela. A lista mostrará conjuntos de dados que podem exigir credenciais atualizadas. Cada conjunto de dados listado é um link direto no qual basta você clicar para atualizar suas credenciais com facilidade.

É isso... quase. Com o novo gateway instalado, você não precisa mais da versão anterior instalada em seu computador, portanto, você deve desinstalá-la. Você pode fazer pesquisando pelo **Power BI Gateway – Personal** em seu computador e desinstalando-o.

### <a name="determining-which-version-of-the-personal-gateway-you-have-installed"></a>Determinando qual versão do gateway pessoal está instalada
Para determinar qual versão do gateway pessoal está instalada, você pode fazer o seguinte:

* A versão anterior do gateway pessoal se chama **Power BI Gateway – Personal** e usa o ícone do Power BI em sua caixa de diálogo de instalação.
* A nova versão do gateway pessoal é chamada **gateway de dados local (modo pessoal)** e usa o ícone de gateway (uma nuvem com uma seta para cima e para baixo na parte inferior).

Você pode ir até **Adicionar/Remover Programas** e ver se **Power BI Gateway – Personal** aparece na lista e, se sim, você tem a versão anterior do gateway pessoal instalada.

## <a name="using-fast-combine-with-the-personal-gateway"></a>Usando a Combinação Rápida com o gateway pessoal
Caso estivesse usando a **Combinação Rápida** com o gateway anterior, você precisará executar as seguintes etapas para habilitar novamente o uso da **Combinação Rápida** com o **Gateway de dados local (modo pessoal)**:

1. Usando o Explorador de Arquivos, abra o arquivo a seguir:
   
   ```
   %localappdata%\Microsoft\On-premises data gateway (personal mode)\Microsoft.PowerBI.DataMovement.Pipeline.GatewayCore.dll.config
   ```
2. Na parte inferior do arquivo, adicione o seguinte texto:
   
       ```
       <setting name="EnableFastCombine" serializeAs="String">```
       <value>true</value>
       </setting>
       ```
3. Uma vez concluída, a configuração entrará em vigor em aproximadamente um minuto. Para verificar se ela está funcionando corretamente, tente fazer uma atualização sob demanda no **serviço do Power BI** para confirmar se a **Combinação Rápida** está funcionando.

## <a name="limitations-and-considerations"></a>Limitações e considerações
Há algumas coisas a levar em consideração ao usar o **Gateway de dados local (modo pessoal)**, conforme descrito na lista a seguir.

* Se estiver usando o **Windows Hello** ou um pin para entrar no Windows, você poderá encontrar o seguinte erro: 
  * *A conta de usuário que você selecionou não corresponde aos requisitos do aplicativo. Use uma conta diferente.*
  * Para corrigir esse erro, selecione *Usar uma conta diferente* e entre novamente. 

No momento, não há suporte para as seguintes fontes de dados no **Gateway de dados local (modo pessoal)**:

* ADO.NET 
* CurrentWorkbook
* FTP
* HDFS
* SAP BusinessObjects         
* Spark

O suporte para Spark está planejado para o segundo semestre do ano civil de 2017.

## <a name="frequently-asked-questions-faq"></a>Perguntas frequentes
* É possível executar o **Gateway de dados local (modo pessoal)** lado a lado com o **Gateway de dados local** (anteriormente conhecido como a versão Enterprise do gateway)?
  
  * **Resposta**: sim, com a nova versão, ambos podem ser executados simultaneamente.
* É possível executar o **Gateway de dados local (modo pessoal)** como um serviço?
  
  * **Resposta:** não. O **Gateway de dados local (modo pessoal)** só pode ser executado como um aplicativo. Se precisar executar o gateway como um serviço e/ou no modo admin, você precisará considerar o [**Gateway de dados local**](service-gateway-onprem.md) (anteriormente conhecido como gateway Enterprise).
* Com que frequência o **Gateway de dados local (modo pessoal)** é atualizado?
  
  * **Resposta**: planejamos atualizar o gateway pessoal mensalmente.
* Por que estou solicitado a atualizar minhas credenciais?
  
  * **Resposta**: muitas situações podem levar a uma solicitação de credenciais. A mais comum é você ter reinstalado o **Gateway de dados local (modo pessoal)** em um computador diferente de seu gateway do **Power BI – pessoal**. Também pode haver um problema na fonte de dados e o Power BI não conseguiu realizar uma conexão de teste ou ocorreu um erro de tempo limite ou do sistema. Você pode atualizar suas credenciais no **serviço do Power BI** indo até o **ícone de engrenagem**, selecionando **Configurações** e, em seguida, **Conjuntos de Dados** e localizando o conjunto de dados em questão e clicando em *atualizar credenciais*.
* Quanto tempo meu gateway pessoal anterior ficará offline durante a atualização?
  
  * **Resposta**: atualizar o gateway pessoal para a nova versão deve levar apenas alguns minutos. 
* O que acontece se eu não migrar para o novo gateway pessoal até 31 de julho de 2017?
  
  * **Resposta**: se você estiver atualizando seus relatórios com o gateway atual, suas atualizações pararão. A única maneira de configurar uma nova agenda de atualização será instalando e configurando o novo gateway.
* Estou usando o script do R. Ele tem suporte?
  
  * **Resposta**: adicionaremos o suporte para scripts do R em breve.
* Por que não estou vendo a mensagem para atualizar meu gateway no **serviço do Power BI**?
  
  * **Resposta**: provavelmente, isso está acontecendo porque você tem um ou mais conjuntos de dados que incluem uma fonte de dados que ainda não tem suporte.

## <a name="next-steps"></a>Próximas etapas
[Definição das configurações de proxy para Gateways do Power BI](service-gateway-proxy.md)  
Mais perguntas? [Experimente a Comunidade do Power BI](http://community.powerbi.com/)

