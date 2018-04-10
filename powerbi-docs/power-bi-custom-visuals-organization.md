---
title: Usando os elementos visuais personalizados da organização no Power BI
description: Usar, gerenciar e criar visuais personalizados organizacionais no Power BI
services: powerbi
documentationcenter: ''
author: markingmyname
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
ms.date: 02/06/2018
ms.author: maghan
LocalizationGroup: Visualizations
ms.openlocfilehash: 1f3a3586b3aecb10b07bd171ab7349c4e1089cec
ms.sourcegitcommit: afa10c016433cf72d6d366c024b862187a8692fd
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/04/2018
---
# <a name="using-organization-custom-visuals-in-power-bi"></a>Usando os elementos visuais personalizados da organização no Power BI

Você pode usar visuais personalizados no Power BI para criar um tipo exclusivo de visual que seja adequado para você ou as informações de dados que você está tentando transmitir. Geralmente, esses elementos visuais personalizados são criados por desenvolvedores e criados quando a variedade de visuais que estão incluídos no Power BI não atende a sua necessidade. 

Em algumas organizações, os elementos visuais personalizados são ainda mais importantes. Eles podem ser necessários para transmitir dados específicos ou insights exclusivos para a organização, podem ter requisitos de dados especiais ou dar destaque a métodos particulares de negócios. Essas organizações precisam desenvolver elementos visuais personalizados, compartilhá-los em toda a organização e garantir que eles sejam mantidos corretamente. Os elementos visuais personalizados do Power BI permitem que as organizações façam exatamente isso.

A imagem a seguir mostra o processo pelo qual os elementos visuais personalizados da organização no Power BI flui do administrador, por meio de desenvolvimento e manutenção, todos serão transmitidos para o analista de dados.

![](media/power-bi-custom-visuals-organizational/custom-visual-org-01.jpg)

Os elementos visuais de organização são implantados e gerenciados pelo administrador do Power BI no portal de administração. Uma vez implantado no repositório organizacional, os usuários da organização podem facilmente descobri-los e importar os elementos visuais personalizados da organização em seus relatórios diretamente do Power BI Desktop.

## <a name="using-organizational-custom-visuals"></a>Usando elementos visuais personalizados da organização

Para saber mais sobre como usar elementos visuais personalizados da organização nos relatórios que você criou, confira o seguinte artigo: [Saber mais sobre como importar elementos visuais organizacionais em seus relatórios](power-bi-custom-visuals.md).
 
## <a name="administering-organizational-custom-visuals"></a>Administrando elementos visuais personalizados da organização

Para saber mais sobre como administrar, implantar e gerenciar elementos visuais personalizados organizacionais na sua organização, confira o seguinte artigo: [Saber mais sobre implantação e gerenciamento de elementos visuais personalizados da organização](https://go.microsoft.com/fwlink/?linkid=866790).

> [!WARNING]
> Um elemento visual personalizado pode conter código com riscos de segurança ou privacidade. É importante confiar no autor e na origem de qualquer elemento visual personalizado antes de implantá-lo no repositório da organização. 
> 

## <a name="considerations-and-limitations"></a>Considerações e limitações
 
Há várias considerações e limitações das quais você precisa estar ciente.
 
Administrador:

* Não há suporte para elementos visuais personalizados herdados (como elementos visuais personalizados que não são criados sobre as novas APIs com controle de versão)

* Se um elemento visual personalizado é excluído do repositório, os relatórios existentes que usam o elemento visual excluído param de renderizar. A operação de exclusão do repositório não é reversível. Para desabilitar temporariamente um visual personalizado, use o recurso "Desabilitar".
 
Usuário final:

* Não há suporte para Coleção de Espaços de Trabalho do Power BI para elementos visuais da organização

* Os elementos visuais do Visio, do PowerApps e do GlobeMap do marketplace AppSource não serão renderizados se forem implantados por meio do repositório da organização
