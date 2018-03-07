---
title: "Usando os elementos visuais personalizados da organização no Power BI"
description: Usar, gerenciar e criar visuais personalizados organizacionais no Power BI
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
ms.date: 02/06/2018
ms.author: maghan
LocalizationGroup: Visualizations
ms.openlocfilehash: 6f7827f7804fcd52e7d922ebc8ffad5a8036b33c
ms.sourcegitcommit: 88c8ba8dee4384ea7bff5cedcad67fce784d92b0
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/24/2018
---
# <a name="using-organization-custom-visuals-in-power-bi-preview"></a>Usando os elementos visuais personalizados da organização no Power BI (versão prévia)

Você pode usar visuais personalizados no Power BI para criar um tipo exclusivo de visual que seja adequado para você ou as informações de dados que você está tentando transmitir. Geralmente, esses elementos visuais personalizados são criados por desenvolvedores e criados quando a variedade de visuais que estão incluídos no Power BI não atende a sua necessidade. 

Em algumas organizações, os elementos visuais personalizados são ainda mais importantes. Eles podem ser necessários para transmitir dados específicos ou insights exclusivos para a organização, podem ter requisitos de dados especiais ou dar destaque a métodos particulares de negócios. Essas organizações precisam desenvolver elementos visuais personalizados, compartilhá-los em toda a organização e garantir que eles sejam mantidos corretamente. Os elementos visuais personalizados do Power BI (agora em versão prévia) permitem que as organizações façam exatamente isso. 

A imagem a seguir mostra o processo pelo qual os elementos visuais personalizados da organização (versão prévia) no Power BI flui do administrador, por meio de desenvolvimento e manutenção, todos serão transmitidos para o analista de dados.

![](media/power-bi-custom-visuals-organizational/custom-visual-org-01.jpg)

## <a name="how-to-enable-organizational-custom-visuals-preview"></a>Como habilitar elementos visuais personalizados organizacionais (versão prévia)

Os elementos visuais personalizados da organização estão atualmente em modo de versão prévia, então você deve habilitar o recurso no Power BI Desktop. Para habilitar esse recurso de visualização, na faixa de opções, selecione Arquivo > Opções e Configurações > Opções; em seguida, no painel esquerdo, selecione Visualizar recursos, marque a caixa de seleção ao lado de Elementos visuais personalizados da minha organização, conforme mostrado na imagem a seguir.

![](media/power-bi-custom-visuals-organizational/custom-visual-org-02.jpg)

Os elementos visuais de organização são implantados e gerenciados pelo administrador do Power BI no portal de administração. Uma vez implantado no repositório organizacional, os usuários da organização podem facilmente descobri-los e importar os elementos visuais personalizados da organização em seus relatórios diretamente do Power BI Desktop.

## <a name="using-organizational-custom-visuals"></a>Usando elementos visuais personalizados da organização

Para saber mais sobre como usar elementos visuais personalizados da organização nos relatórios que você criou, confira o seguinte artigo: [Saber mais sobre como importar elementos visuais organizacionais em seus relatórios](power-bi-custom-visuals.md).
 
## <a name="administering-organizational-custom-visuals"></a>Administrando elementos visuais personalizados da organização

Para saber mais sobre como administrar, implantar e gerenciar elementos visuais personalizados organizacionais na sua organização, confira o seguinte artigo: [Saber mais sobre implantação e gerenciamento de elementos visuais personalizados da organização](https://go.microsoft.com/fwlink/?linkid=866790).

> [!WARNING]
> Um elemento visual personalizado pode conter código com riscos de segurança ou privacidade. É importante confiar no autor e na origem de qualquer elemento visual personalizado antes de implantá-lo no repositório da organização. 
> 

## <a name="considerations-and-limitations"></a>Considerações e limitações
 
Como organizacionais visuais personalizados estão em modo de versão prévia, há algumas considerações e limitações que você precisa conhecer e levar em consideração.
 
Administrador:

* Não há suporte para elementos visuais personalizados herdados (como elementos visuais personalizados que não são criados sobre as novas APIs com controle de versão)

* Ainda não há suporte para a atualização in-loco. Para atualizar um visual, você deverá carregar uma nova versão do elemento visual para o repositório da organização (também verifique se ele tem a mesma ID visual no arquivo PBIVIZ). Os autores do relatório, em seguida, poderão importar a nova versão para o seu relatório e fazer uma substituição in-loco de sua versão atual do elemento visual no relatório.

* Se um elemento visual personalizado é excluído do repositório, os relatórios existentes que usam o elemento visual excluído param de renderizar. A operação de exclusão do repositório não é reversível.
 
Usuário final:

* Não há suporte para usar o mesmo elemento visual (a mesma ID Visual) do marketplace público (AppSource) e do repositório da organização. Nessa circunstância, o visual mais recente que foi importado será usado.

* Não há suporte para o compartilhamento externo de elementos visuais organizacionais em painéis e relatórios. Os usuários fora da organização que exibem um painel com um elemento visual personalizado organizacional verão um elemento visual em branco. 

* Não há suporte para Coleção de Espaços de Trabalho do Power BI para elementos visuais da organização

* Os elementos visuais personalizados da organização nos relatórios que são publicados na Web não renderizam

* Os elementos visuais do Visio, do PowerApps e do GlobeMap do marketplace AppSource não serão renderizados se forem implantados por meio do repositório da organização

* Se o administrador excluir um elemento visual personalizado do repositório e esse elemento visual for usado em um relatório, o elemento visual interromperá a renderização e deverá ser removido do relatório a fim de salvar o relatório