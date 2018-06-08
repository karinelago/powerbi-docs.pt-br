---
title: Assinar relatórios e painéis no serviço do Power BI
description: Saiba como obter uma assinatura para você e outras pessoas de um instantâneo de um relatório e um dashboard do Power BI.
author: mihart
manager: kfile
ms.reviewer: ''
featuredvideoid: ''
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 06/04/2018
ms.author: mihart
LocalizationGroup: Common tasks
ms.openlocfilehash: 9d166dec82aa56fec1512e3d859e60142afcccd6
ms.sourcegitcommit: b3b32b9b3935706d7caa091833bd32259d7ff6ee
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34755267"
---
# <a name="subscribe-to-a-report-or-dashboard-in-power-bi-service-apppowerbicom"></a>Assinar um relatório ou painel no serviço do Power BI (app.powerbi.com)
Nunca foi tão fácil manter-se atualizado sobre seus dashboards e relatórios mais importantes. Assine as páginas de relatórios e os dashboards mais importantes para você e seus colegas e o Power BI enviará um instantâneo por email para sua caixa de entrada. Informe ao Power BI a frequência com que deseja receber os emails: de uma vez por dia a uma vez por semana. 

O instantâneo e o email usarão o idioma definido nas configurações do Power BI (confira [Idiomas e países/regiões com suporte para o Power BI](supported-languages-countries-regions.md)). Se nenhum idioma for definido, o Power BI usará o idioma de acordo com a configuração de localidade no navegador atual. Para obter ou definir sua preferência de idioma, selecione o ícone de engrenagem ![ícone de engrenagem](media/service-report-subscribe/power-bi-settings-icon.png) > **Configurações > Geral > Idioma**. 

![Lista suspensa Idioma](media/service-report-subscribe/power-bi-language.png)

As assinaturas podem ser criadas somente no serviço do Power BI. Quando você receber o email, ele incluirá um link para "Acessar o relatório ou o dashboard". Em dispositivos móveis com aplicativos do Power BI instalados, a seleção desse link iniciará o aplicativo (ao contrário da ação padrão de abrir o relatório ou o dashboard no site do Power BI).


## <a name="requirements"></a>Requisitos
- A **criação** de uma assinatura é um recurso do Power BI Pro e você precisa ter permissões de edição para o conteúdo (dashboard ou relatório) para criar essa assinatura. 
- Como os emails da assinatura são enviados somente quando um conjunto de dados é alterado ou atualizado, as assinaturas não funcionam em conjuntos de dados que não se alteram nem se atualizam.

## <a name="subscribe-to-a-dashboard-or-a-report-page"></a>Assine um dashboard ou uma página de relatório
Se você estiver assinando um dashboard ou um relatório, o processo será muito semelhante. O mesmo botão permite que você assine (e assine para outras pessoas) os dashboards e relatórios do serviço do Power BI.
 
![selecione o ícone Assinar](media/service-report-subscribe/power-bi-subscribe-orientation.png).

1. Abra o dashboard ou o relatório.
2. Na barra de menus superior, selecione **Assinar** ou selecione o ícone de envelope ![ícone de assinatura](media/service-report-subscribe/power-bi-icon-envelope.png).
   
   ![Ícone Assinar](media/service-report-subscribe/power-bi-subscribe-icon.png)

3. Use o controle deslizante amarelo para ativar e desativar a assinatura.  Definir o controle deslizante como Desativado não excluirá a assinatura. Para excluir a assinatura, selecione o ícone de cesto de lixo.

4. Preencha os detalhes da mensagem de email. Seu email já estará preenchido, mas você também poderá adicionar outras pessoas à assinatura. Somente os endereços de email no mesmo domínio podem ser adicionados (confira **Considerações e solução de problemas** abaixo para obter mais detalhes). Se o relatório ou o dashboard estiver hospedado na [capacidade Premium](service-premium.md), você poderá fazer isso usando endereços de email individuais e aliases de grupo. Se o relatório ou o dashboard não estiver hospedado na capacidade Premium, você ainda poderá incluir outras pessoas usando os endereços de email individuais delas, mas elas também precisarão ter uma licença do Power BI Pro.

    Nas capturas de tela abaixo, observe que quando você assina um relatório, na verdade, você está assinando uma *página* de relatório.  Para assinar mais de uma página em um relatório, selecione **Adicionar outra assinatura** e selecione uma página diferente. 
      
   ![Janela Assinar](media/service-report-subscribe/power-bi-subscribe2.png)

5. Selecione **Salvar e fechar** para salvar a assinatura. Os assinantes receberão um email e um instantâneo do dashboard ou da página de relatório sempre que um dos conjuntos de dados subjacentes for alterado. Se o dashboard ou o relatório for atualizado mais de uma vez por dia, o email será enviado apenas após a primeira atualização.  
   
   ![instantâneo de email de dashboard](media/service-report-subscribe/power-bi-dashboard-email.jpg)
   
   > [!TIP]
   > Deseja ver o email agora mesmo? Dispare um email ao atualizar um dos conjuntos de dados associados ao dashboard ou o conjunto de dados associado ao relatório. (Se não tiver permissões de edição para o conjunto de dados, peça para alguém que as tenha fazer isso para você.) Para descobrir quais conjuntos de dados estão sendo usados, selecione o ícone **Exibir relacionados** ![ícone de Exibir relacionados](media/service-report-subscribe/power-bi-view-related.png) para abrir o **Conteúdo relacionado** e, em seguida, selecione o ícone de atualização ![ícone de atualização](media/service-report-subscribe/power-bi-refresh.png). 
   > 
   > 
   
   ![Conjuntos de dados relacionados](media/service-report-subscribe/power-bi-view-related-screen.png)

## <a name="how-the-email-schedule-is-determined"></a>Como o cronograma de email é determinado
A tabela a seguir descreve com que frequência você receberá um email. Tudo depende do método de conexão do conjunto de dados no qual se baseia o dashboard ou o relatório (DirectQuery, Conexão dinâmica, importado para o Power BI ou arquivo do Excel no OneDrive ou no SharePoint Online) e das opções de assinatura disponíveis e selecionadas (diária, semanal ou nenhuma).

|  | **DirectQuery** | **Live Connect** | **Atualização agendada (importar)** | **Arquivo do Excel no OneDrive /SharePoint Online** |
| --- | --- | --- | --- | --- |
| **Com que frequência o relatório/dashboard é atualizado?** |A cada 15 min |O Power BI verifica a cada 15 minutos e, se o conjunto de dados tiver mudado, o relatório será atualizado. |O usuário seleciona nenhuma, diária ou semanal. Diária pode ser até oito vezes ao dia. Semanal é, na verdade, um cronograma semanal que o usuário cria e define a atualização para apenas uma vez por semana ou para até uma vez por dia. |Uma vez a cada hora |
| **Quanto controle o usuário tem sobre o cronograma do email de assinatura?** |As opções são: diária ou semanal |Não há opções: os usuários receberão um email se o relatório for atualizado, mas não mais do que uma vez por dia. |Se o agendamento de atualização for diário, as opções serão diária e semanal.  Se o agendamento de atualização for semanal, a única opção será semanal. |Não há opções: usuário recebe um email sempre que o conjunto de dados for atualizado, mas não mais do que uma vez por dia. |

## <a name="manage-your-subscriptions"></a>Gerenciar suas assinaturas
Somente a pessoa que criou a assinatura possa gerenciá-la.  Há dois caminhos que levam à tela para gerenciar suas assinaturas.  O primeiro é selecionando **Gerenciar todas as assinaturas** na caixa de diálogo **Assinar emails** (confira as capturas de tela abaixo da etapa 4 acima). O segundo é selecionar o ícone de engrenagem ![ícone de engrenagem](media/service-report-subscribe/power-bi-settings-icon.png) do Power BI na barra de menus superior e escolher **Configurações**.

![selecionar Configurações](media/service-report-subscribe/power-bi-subscribe-settings.png)

As assinaturas específicas exibidas dependerão de qual espaço de trabalho está ativo no momento.  Para ver todas as suas assinaturas de todos os espaços de trabalho ao mesmo tempo, verifique se **Meu Espaço de Trabalho** está ativo. Para obter ajuda para entender os espaços de trabalho, consulte [Espaços de trabalho no Power BI](service-create-distribute-apps.md).

![veja todas as assinaturas no Meu espaço de trabalho](media/service-report-subscribe/power-bi-subscriptions.png)

Uma assinatura será encerrada se a licença Pro expirar, se o dashboard ou o relatório for excluído pelo proprietário ou se a conta de usuário usada para criar a assinatura for excluída.

## <a name="considerations-and-troubleshooting"></a>Considerações e solução de problemas
* As assinaturas da página de relatório são vinculadas ao nome da página de relatório. Se você assinar uma página de relatório e renomeá-la, precisará recriar sua assinatura
* Para assinaturas de email em conjuntos de dados de conexão dinâmica, você só receberá emails quando os dados mudarem. Assim, se ocorrer uma atualização, mas os dados não mudarem, o Power BI não enviará um email.
* Assinaturas de email não dão suporte à maioria dos [visuais personalizados](power-bi-custom-visuals.md).  A única exceção é para os elementos visuais personalizados que foram [certificados](power-bi-custom-visuals-certified.md).  
* Se algum bloco tiver a RLS (Segurança em Nível de Linha) aplicada, esse bloco não será exibido.
* Assinaturas de email são enviadas com estados de segmentação e filtro padrão do relatório. As alterações feitas nos padrões após a assinatura não serão exibidas no email.    
* Ainda não há suporte para as assinaturas de email nas páginas de relatórios criadas pela conexão dinâmica do Power BI Desktop com o recurso de serviço.    
* Especificamente para assinaturas de dashboards, ainda não há suporte para alguns tipos de blocos.  Eles incluem: blocos de streaming, blocos de vídeo, blocos de conteúdo da Web personalizado.     
* Se você compartilhar um dashboard com um colega fora de seu locatário, não será possível criar uma assinatura para esse colega também. Portanto, se você for aaron@xyz.com, poderá compartilhar com anyone@ABC.com, mas ainda não poderá incluir anyone@ABC.com, e ele não poderá assinar o conteúdo compartilhado.      
* As assinaturas poderão falhar em dashboards ou relatórios com imagens extremamente grandes devido aos limites de tamanho de email.    
* O Power BI pausa a atualização automaticamente em conjuntos de dados associados a dashboards e relatórios que não foram visitados há mais de 2 meses.  No entanto, se você adicionar uma assinatura a um dashboard ou relatório, ele não ficará em pausa mesmo que não seja visitado.    
* Se você não estiver recebendo emails de assinatura, verifique se o nome UPN pode receber emails. [A equipe do Power BI está trabalhando para atenuar esse requisito](https://community.powerbi.com/t5/Issues/No-Mail-from-Cloud-Service/idc-p/205918#M10163), portanto, fique ligado. 
* Se o dashboard ou o relatório estiver na capacidade Premium, você poderá usar o alias de email de grupo para assinaturas, em vez de inserir um endereço de email de colega de cada vez na assinatura. Os aliases são baseados no Active Directory atual. 

## <a name="next-steps"></a>Próximas etapas
* Mais perguntas? [Experimente perguntar à Comunidade do Power BI](http://community.powerbi.com/)    
* [Ler a postagem no blog](https://powerbi.microsoft.com/blog/introducing-dashboard-email-subscriptions-a-360-degree-view-of-your-business-in-your-inbox-every-day/)

