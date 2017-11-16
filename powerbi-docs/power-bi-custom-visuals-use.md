---
title: "Adicionar um visual personalizado a um relatório (Desktop)"
description: "Adicionar um visual personalizado para um relatório no Desktop"
services: powerbi
documentationcenter: 
author: mihart
manager: kfile
backup: 
editor: 
tags: 
qualityfocus: complete
qualitydate: 03/15/2016
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 09/27/2017
ms.author: mihart
ms.openlocfilehash: b3a3e34fac546ee57cd66924e72a2c93aa647850
ms.sourcegitcommit: 99cc3b9cb615c2957dde6ca908a51238f129cebb
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/13/2017
---
# <a name="add-a-custom-visual-to-a-report-desktop"></a>Adicionar um visual personalizado a um relatório (Desktop)
Você [baixou um modelo de visual personalizado](service-custom-visuals-office-store.md) e o salvou em seu computador ou em outro local.  A próxima etapa é importar o modelo de visual personalizado para um relatório a fim de que ele seja adicionado, como uma opção, ao seu painel de Visualizações.

![](media/power-bi-custom-visuals-use/pbi-custom-viz-icon.png)

Um modelo de visual personalizado é adicionado a um relatório específico quando importado. Se você desejar usar o modelo de visual em outro relatório, também será necessário importá-lo nesse relatório. Quando um relatório com um visual personalizado é salvo com a opção **Salvar como** , uma cópia do modelo do visual personalizado é salva com o novo relatório.

1. Abra o Power BI Desktop e selecione o relatório ao qual deseja adicionar a visualização personalizada.   
2. Há duas opções para importar um visual personalizado: no menu **Arquivo** ou no painel **Visualizações** .
   
    **No menu Arquivo da Área de trabalho**
   
    No menu **Arquivo** do relatório, escolha **Importar** &gt;**Visual Personalizado do Power BI**. Você deve estar no modo de exibição de edição.    
   
      ![](media/power-bi-custom-visuals-use/power-bi-import.png)
   
    **No painel Visualização**
   
    No painel **Visualizações** , escolha **Inserir (…)**.    
   
      ![](media/power-bi-custom-visuals-use/insertpane.png)
   
    Selecione **Importar um visual personalizado**.  
   
      ![](media/power-bi-custom-visuals-use/insertpane.png)
3. **Leia o aviso**.
   
    Um visual personalizado tem acesso aos dados no relatório e, ao compartilhar um relatório que contém visuais personalizados, seus colegas podem acessar esses dados. Lembre-se de examinar o visual personalizado para garantir que ele é proveniente de uma fonte confiável. A Microsoft recomenda que você trabalhe junto ao departamento de TI se não tiver certeza se quer usar um visual personalizado específico obtido na loja online do Office, por email ou de outra fonte.
   
    ![](media/power-bi-custom-visuals-use/caution.png)
4. Navegue até o local em que o arquivo .pbiviz de visual personalizado foi salvo e abra-o.
5. Um ícone (também chamado de um *modelo*) é adicionado ao painel **Visualizações**.
   
    ![](media/power-bi-custom-visuals-use/visualuse.png)
6. Selecione o modelo visual personalizado para adicioná-lo ao seu relatório como faria com qualquer um dos outros modelos no painel Visualizações. Adicione campos e filtros e crie seu visual.
7. Formate o visual personalizado como você faria com qualquer outro visual.  No painel **Visualizações**, selecione o ícone de rolo de tinta. As opções de formatação disponíveis variam por tipo de visual.

## <a name="considerations-and-troubleshooting"></a>Considerações e solução de problemas
* Para permitir que visuais personalizados tenham suporte na [exportação para o PowerPoint](service-publish-to-powerpoint.md) ou que [sejam exibidos em emails recebidos quando um cliente assina páginas do relatório](service-report-subscribe.md), eles precisam ser definidos como *Visuais personalizados certificados* que passaram pelo processo de certificação visual personalizado da Microsoft.  Para ver a lista de *Visuais personalizados certificados* e para saber mais sobre o processo de certificação, consulte [Visuais personalizados certificados](power-bi-custom-visuals-certified.md)

## <a name="next-steps"></a>Próximas etapas
[Baixar e usar visuais personalizados da Office Store](service-custom-visuals-office-store.md)  
[Adicionar um elemento visual personalizado a um relatório no Serviço do Power BI](power-bi-report-add-custom-visual.md)  
[Publicar visuais personalizados na Office Store](developer/office-store.md)  
[Visualizações personalizadas no Power BI](power-bi-custom-visuals.md)  
Mais perguntas? [Experimente a Comunidade do Power BI](http://community.powerbi.com/)

