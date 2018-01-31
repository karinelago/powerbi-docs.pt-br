---
title: "Examinar a segurança e a privacidade dos visuais personalizados"
description: "Antes de habilitar um elemento visual personalizado, você deve examinar tal elemento visual em relação à segurança e à privacidade, para certificar-se de que ele se ajustará aos padrões da sua organização."
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
ms.date: 09/05/2017
ms.author: maghan
ms.openlocfilehash: 15f8d9090736a62fdaa53aa3f19e7e0fff127337
ms.sourcegitcommit: 6e693f9caf98385a2c45890cd0fbf2403f0dbb8a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2018
---
# <a name="review-custom-visuals-for-security-and-privacy"></a>Examinar a segurança e a privacidade dos visuais personalizados
Antes de habilitar um elemento visual personalizado, você deve examinar tal elemento visual em relação à segurança e à privacidade, para certificar-se de que ele se ajustará aos padrões da sua organização.

## <a name="enable-a-custom-visual"></a>Habilitar um visual personalizado
<a name="enable"></a>Um visual personalizado no relatório será desabilitado até você escolher **Habilitar visuais personalizados**, conforme mostrado abaixo.  

![](media/service-custom-visuals-review-for-security-and-privacy/emptyvisual.png)

## <a name="considerations-before-you-enable-a-custom-visual"></a>Considerações antes de habilitar um visual personalizado
<a name="considerations"></a>

> [!WARNING]
> Um visual personalizado pode conter código com riscos de segurança ou privacidade; portanto, no relatório, ele é desabilitado até que a opção Habilitar visuais personalizados seja escolhida. Aqui estão algumas considerações para decidir se é necessário habilitar um visual personalizado:
> 
> 

1. Certifique-se de que você confia no autor e na fonte dos visuais personalizados usados no relatório
2. Se você não souber o que fazer, entre em contato com sua equipe de TI para decidir se você deve habilitar visuais personalizados para os relatórios exibidos.
3. Se alguém compartilhar um relatório com você que contém um visual personalizado, mesmo se ele for um colega de trabalho próximo, não se sinta obrigado a habilitar o visual personalizado. Não há problema em voltar atrás e considerar se isso é essencial para a tarefa em questão. É sempre bom pedir que alguém forneça um relatório sem visuais personalizados, caso você não tenha confiança no visual personalizado.

## <a name="security-best-practices-for-it-professionals-to-enable-a-custom-visual"></a>Práticas recomendadas de segurança para profissionais de TI para habilitar um visual personalizado
<a name="security"></a>

> [!WARNING]
> Um visual personalizado pode conter código com riscos de segurança ou privacidade; portanto, no relatório, ele é desabilitado até que a opção Habilitar visuais personalizados seja escolhida. Há várias práticas recomendadas que você pode seguir para avaliar a segurança e a privacidade de um visual personalizado.
> 
> 

1. Implemente um processo de habilitação para visuais personalizados na organização. Os visuais personalizados verificados seriam compartilhados com usuários internos por meio de um site interno, como uma biblioteca de documentos do SharePoint ou um documento do OneNote.
2. Fornece orientações para usuários de negócios sobre o uso apropriado dos visuais personalizados e um grupo de email para que os usuários de negócios enviem perguntas sobre privacidade e segurança.
3. Avalie o código JavaScript no arquivo pbiviz do visual personalizado.

**Para avaliar o código JavaScript em um elemento visual personalizado**

Um visual personalizado usa JavaScript e, portanto, pode conter riscos de segurança ou privacidade. Se você receber um visual personalizado ou um arquivo pbix com um visual personalizado de uma fonte desconhecida, convém examinar o JavaScript para ver se ele é seguro.

Para avaliar o código JavaScript em um visual personalizado, extraia o código do visual personalizado. Veja aqui como extrair o código:  

1. Salve o arquivo .pbiviz em uma pasta.
2. Renomeie o arquivo para um arquivo .zip.
3. Extraia o arquivo zip para uma pasta local.

## <a name="custom-visual-file-contents"></a>Conteúdo do arquivo do visual personalizado
Veja abaixo o conteúdo de um arquivo pbiviz:

| **Arquivo** | **Descrição** |
|:--- |:--- |
| ./package.json |Um arquivo de manifesto que indica quais arquivos serão carregados para o visual personalizado. |
| ./resources |Contém o CSS, TypeScript e JavaScript usados pelo visual personalizado. |
| ./resources/&lt;nome&gt; |&lt;nome&gt; é o nome do elemento visual personalizado. |
| ./resources/&lt;nome&gt;.css |O arquivo de recurso css do visual personalizado. |
| ./resources/&lt;nome&gt;.js |O código que é executado quando um usuário clica em Habilitar visuais personalizados ou depois de um usuário Importar um visual personalizado. Código JavaScript de aviso pode conter riscos de segurança ou privacidade. |
| ./resources/&lt;nome&gt;.ts |O código-fonte em JavaScript para o visual no formato TypeScript. Código JavaScript ou TypeScript de aviso pode conter riscos de segurança ou privacidade. |
| ./resources/&lt;nome&gt;.png |O ícone mostrado ao usuário para o visual. |

Depois de extrair o arquivo pbiviz, é possível avaliar o código. Aqui estão algumas práticas recomendadas e as ameaças para procurar.

## <a name="best-practices-to-evaluate-the-javascript-or-typescript-code"></a>Práticas recomendadas para avaliar o código JavaScript ou TypeScript
O código **JavaScript** ou **TypeScript** pode conter riscos de segurança ou de privacidade. Aqui estão algumas práticas recomendadas e as ameaças para procurar.

### <a name="best-practices-to-evaluate-javascript-code"></a>Práticas recomendadas para avaliar o código JavaScript
* Sempre avalie o conteúdo do arquivo .js. Este é o código que é realmente executado. É possível que o conteúdo do arquivo .ts não seja compilado para o arquivo .js incluído no visual personalizado.
* Sempre avalie o conteúdo do arquivo .ts. É possível carregar o arquivo .ts nas **Ferramentas de Desenvolvedor**, exportar o visual e comparar o arquivo .js resultante no arquivo .pbiviz recém-criado com o arquivo .js original contido no visual
* Verifique se o ícone do visual personalizado não se assemelha muito a outros visuais com que o usuário esteja familiarizado.
* Sempre avalie o visual em uma conta de teste que tem privilégios mínimos e que não tem acesso a dados confidenciais. O ideal é que a conta de teste seja uma conta local sem informações de logon para serviços diferentes do Power BI.

### <a name="threats-to-look-for-in-javascript-code"></a>Ameaças que devem ser procuradas em um código JavaScript
* Verifique a atividade de rede quando o visual estiver sendo usado no modo de edição e exibição. Tenha certeza de que está satisfeito com as solicitações que estão sendo feitas. Você não deve ver solicitações aos recursos fora do domínio do Power BI, a menos que o autor do visual tenha comunicado isso antecipadamente.
* Quaisquer dados que você veja deixando o domínio do Power BI devem corresponder às suas expectativas para o que seria um uso “normal”. Por exemplo - se o visual implementa um player de vídeo que usa um iFrame para exibir um vídeo de outro site, algumas informações devem percorrer as solicitações de IFrame para renderizar o vídeo corretamente. No entanto, se você vir todo o conjunto de dados que é enviado pela rede, você poderá investigar mais detalhadamente se isso for necessário e desejado.
* Verifique se dados pessoalmente identificáveis estão sendo enviados ou armazenados pelo visual personalizado.
* Verifique se o visual personalizado está tentando acessar recursos do computador local, como gravar arquivos em disco ou acessar cookies.
* Verifique se o visual personalizado tem o que parecem ser códigos ofuscados ou códigos sem um objetivo claro.
* Salve cópias de cada visual examinado anteriormente.
* Se você estiver examinando uma atualização em um visual que você examinou anteriormente, certifique-se de verificar as alterações. Sempre aplique igual rigor às atualizações, assim como na primeira vez que você recebeu o visual para análise
* Se encontrar algo suspeito ou incorreto, entre em contato conosco; estamos aqui para ajudar.

## <a name="next-steps"></a>Próximas etapas
[Visualizações no Power BI](power-bi-report-visualizations.md)  
[Visualizações personalizadas no Power BI](power-bi-custom-visuals.md)  
[Publicar visuais personalizados na Office Store](developer/office-store.md)  
[Introdução às ferramentas de desenvolvedor de visuais personalizados](service-custom-visuals-getting-started-with-developer-tools.md)  
[Como certificar um visual personalizado](power-bi-custom-visuals-certified.md)    
[Vídeo: criação de visualizações personalizadas para o Power BI com Sachin Patney e Nico Cristache](https://www.youtube.com/watch?v=kULc2VbwjCc)  

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](http://community.powerbi.com/)

