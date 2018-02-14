---
title: "Desabilitar as configurações de privacidade"
description: "Como habilitar a Combinação Rápida no Gateway Pessoal para desabilitar as configurações de privacidade para a atualização."
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
ms.tgt_pltfrm: na
ms.workload: powerbi
ms.date: 02/06/2018
ms.author: davidi
ms.openlocfilehash: 5d754dbdd5d52e7a5b123755015e656d9fb2cea2
ms.sourcegitcommit: db37f5cef31808e7882bbb1e9157adb973c2cdbc
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/09/2018
---
# <a name="disable-privacy-setting-in-power-bi-gateway---personal"></a>Desabilitar a configuração de privacidade no Gateway do Power BI - Pessoal
> [!NOTE]
> Há uma nova versão do gateway pessoal para o Power BI denominada **gateway de dados local (modo pessoal)**. O artigo a seguir descreve a versão anterior do gateway pessoal, chamada **Power BI Gateway – Personal**, que será desativada e deixará de funcionar após 31 de julho de 2017. Para obter informações sobre a nova versão do gateway pessoal, incluindo como instalá-la, consulte o artigo [**Gateway de dados local (modo pessoal)**](service-gateway-personal-mode.md). A combinação rápida também está disponível na nova versão do gateway pessoal e também é descrita no artigo.
> 
> 

Você poderá receber o erro a seguir com base nas configurações de privacidade de suas fontes de dados quando usadas com o gateway pessoal.

> *Ocorreu um erro durante o processamento dos dados no conjunto de dados.*
> 
> *[não é possível combinar dados] &lt;A parte da consulta&gt;/&lt;…&gt;/&lt;…&gt; está acessando fontes de dados com níveis de privacidade que não podem ser usados em conjunto. Recompile esta combinação de dados.*
> 
> 

Para solucionar esse erro, você pode ativar a **Combinação Rápida**. A **Combinação Rápida** ignorará as configurações de privacidade, permitindo que diferentes fontes de dados sejam combinadas.

> [!NOTE]
> Os níveis de privacidade não são considerados ao combinar dados. Isso poderia expor dados confidenciais para outra fonte de dados ao combinar os dados.
> 
> 

## <a name="what-is-fast-combine"></a>O que é a Combinação Rápida?
Para saber mais sobre níveis de privacidade e a Combinação Rápida, confira [Níveis de privacidade](https://support.office.com/article/Privacy-levels-Power-Query-CC3EDE4D-359E-4B28-BC72-9BEE7900B540). Por padrão, o nível de privacidade será definido para privado, o que poderá resultar no erro mencionado acima. Isso ocorre porque uma configuração privada isolará a fonte de dados de outras fontes. Um exemplo de onde isso seria um problema seria uma consulta parametrizada obter entradas de outra fonte de dados.

A ativação da Combinação Rápida ignorará a configuração privada e permitirá que a execução ocorra.

## <a name="turn-on-fast-combine"></a>Ativar Combinação Rápida
Você pode usar as etapas a seguir para habilitar a Combinação Rápida para o seu gateway pessoal. O gateway de dados local não tem essa configuração.

1. Abra **ConnectorConfig.xml**.  Isso pode estar em um dos dois locais em seu computador.  Se você for um administrador no computador, ele será o seguinte.
   
    <pre><code>C:\Program Files\Power BI Personal Gateway\1.0\Configurator\Connector</code></pre>
   
    Se você não for um administrador, o local será o seguinte.
   
    <pre><code>C:\Users\[username]\AppData\Local\Power BI Personal Gateway\1.0\Configurator\Connector</code></pre>
    
2. Adicione o elemento **&lt;EnableFastCombine&gt;** com um valor de true ao arquivo de configuração. A adição deste elemento ativará a **Combinação Rápida** .
   
   <pre><code>&lt;EnableFastCombine&gt;true&lt;/EnableFastCombine&gt;</code></pre>
   
   ![](media/refresh-enable-fast-combine/configfile.png)
3. Saia e inicie novamente a tela de configuração de gateway.
4. Você verá uma status informando que a Combinação Rápida está habilitada.
   
   ![](media/refresh-enable-fast-combine/fastcombineenabled.png)

## <a name="turn-off-fast-combine"></a>Desativar Combinação Rápida
1. Abra **ConnectorConfig.xml**.  Isso pode estar em um dos dois locais em seu computador.  Se você for um administrador no computador, ele será o seguinte.
   
    <pre><code>C:\Program Files\Power BI Personal Gateway\1.0\Configurator\Connector</code></pre>
   
    Se você não for um administrador, o local será o seguinte.
   
    <pre><code>C:\Users\[username]\AppData\Local\Power BI Personal Gateway\1.0\Configurator\Connector</code></pre>

2. Remova o elemento **&lt;EnableFastCombine&gt;** do arquivo de configuração. A remoção deste elemento desativará a **Combinação Rápida** .
3. Saia e inicie novamente a tela de configuração de gateway.
4. Você não verá mais o status informando se você sabe que a **Combinação Rápida** está habilitada.

## <a name="next-steps"></a>Próximas etapas
[Gateway de dados local (modo pessoal) – a nova versão do gateway pessoal](service-gateway-personal-mode.md)
[Níveis de privacidade](https://support.office.com/article/Privacy-levels-Power-Query-CC3EDE4D-359E-4B28-BC72-9BEE7900B540)  
[Tarefas comuns de consulta no Power BI Desktop](desktop-common-query-tasks.md)  
Mais perguntas? [Experimente a Comunidade do Power BI](http://community.powerbi.com/)

