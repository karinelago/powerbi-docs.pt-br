---
title: "Serviço terceirizados: conector do Facebook para o Power BI Desktop"
description: "Serviço terceirizados: conector do Facebook para o Power BI Desktop"
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
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 12/06/2017
ms.author: davidi
ms.openlocfilehash: 4e8600aac79683a53b7c2075b3d81e91b3354901
ms.sourcegitcommit: d91436de68a0e833ecff18d976de9d9431bc4121
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/06/2017
---
# <a name="facebook-connector-for-power-bi-desktop"></a>Conector do Facebook para Power BI Desktop
O conector do Facebook no **Power BI Desktop** depende da API do Graph do Facebook. Como tal, recursos e disponibilidade podem variar ao longo do tempo.

Você pode ver um [tutorial sobre o Conector do Facebook para o Power BI Desktop](desktop-tutorial-facebook-analytics.md).

Em 30 de abril<sup>de</sup> 2015, o Facebook expirou a v1.0 de sua Graph API. O Power BI usa a Graph API nos bastidores para o conector do Facebook, permitindo que você se conecte aos seus dados e os analise.

Consultas que foram criadas antes de 30 de maio<sup> </sup>de 2015 podem não funcionar ou retornar menos dados. Após 30 de abril<sup> </sup>de 2015, o Power BI usa a v 2.2 em todas as chamadas para o API do Facebook. Se a consulta foi criada antes de 30 de abril de 2015 e você não a usou, provavelmente precisará autenticar novamente para aprovar o novo conjunto de permissões que solicitaremos.

Podemos tentar lançar atualizações de acordo com as alterações, o API pode ser alterado de forma que afeta os resultados das consultas que gerarmos. Em alguns casos, determinadas consultas podem não ter mais suporte. Devido a essa dependência não podemos garantir os resultados de suas consultas ao usar esse conector.

Mais detalhes sobre a alteração na API do Facebook estão disponíveis [aqui](https://developers.facebook.com/docs/apps/changelog#v2_0).

