---
title: Usar ferramentas de desenvolvedor para criar visuais personalizados
description: "Os visuais personalizados permitem atender às necessidades dos usuários e corresponder ao design do aplicativo. Aprenda como criar um visual personalizado para o Power BI usando as ferramentas de desenvolvedor."
services: powerbi
documentationcenter: 
author: guyinacube
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
ms.author: asaxton
ms.openlocfilehash: e84c5045906cb91f028f0c33b5af8164871d8882
ms.sourcegitcommit: 12236d08c27c7ee3fabb7ef9d767e9dee693f8aa
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="use-developer-tools-to-create-custom-visuals"></a>Usar ferramentas de desenvolvedor para criar visuais personalizados
Os visuais personalizados permitem atender às necessidades dos usuários e corresponder ao design do aplicativo. Aprenda como criar um visual personalizado para o Power BI usando as ferramentas de desenvolvedor.

> [!NOTE]
> Você pode usar este documento para começar a trabalhar. Para obter informações mais detalhadas, veja as informações de referência dentro do [repositório git de visuais do Power BI](https://github.com/Microsoft/PowerBI-visuals).
> 
> 

## <a name="requirements"></a>Requisitos
* NodeJS 4.0 ou posterior obrigatório (5.0 ou posterior recomendado) [Baixar o NodeJS](https://nodejs.org)

## <a name="install-nodejs-and-the-power-bi-tools"></a>Instalar o NodeJS e as ferramentas do Power BI
Para criar um visual personalizado, você precisará instalar o NodeJS. O NodeJS é necessário para executar as ferramentas de linha de comando.

1. Baixe e instale o [NodeJS](https://nodejs.org). A versão 4.0 ou posterior é obrigatória, mas é recomendado ter a 5.0 ou posterior.
2. Instale as ferramentas de linha de comando. Execute o seguinte comando em um prompt de comando.
   
        npm install -g powerbi-visuals-tools
3. Você pode confirmar se as ferramentas estão instaladas executando o seguinte comando sem parâmetros.
   
        pbiviz
   
    Você verá a saída da ajuda.
   
    <pre><code>
         +syyso+/
    oms/+osyhdhyso/
    ym/       /+oshddhys+/
    ym/              /+oyhddhyo+/
    ym/                     /osyhdho
    ym/                           sm+
    ym/               yddy        om+
    ym/         shho /mmmm/       om+
     /    oys/ +mmmm /mmmm/       om+
    oso  ommmh +mmmm /mmmm/       om+
   ymmmy smmmh +mmmm /mmmm/       om+
   ymmmy smmmh +mmmm /mmmm/       om+
   ymmmy smmmh +mmmm /mmmm/       om+
   +dmd+ smmmh +mmmm /mmmm/       om+
         /hmdo +mmmm /mmmm/ /so+//ym/
               /dmmh /mmmm/ /osyhhy/
                 //   dmmd
                       ++
   
       PowerBI Custom Visual Tool
   
    Usage: pbiviz [options] [command]
   
    Commands:
   
    new [name]        Create a new visual
    info              Display info about the current visual
    start             Start the current visual
    package           Package the current visual into a pbiviz file
    update [version]  Updates the api definitions and schemas in the current visual. Changes the version if specified
    help [cmd]        display help for [cmd]
   
    Options:
   
    -h, --help      output usage information
    -V, --version   output the version number
    --install-cert  Install localhost certificate
    </code></pre>

<a name"ssl-setup"></a>

### <a name="server-certificate-setup"></a>Instalação de certificado do servidor
Para habilitar uma visualização dinâmica do visual, é necessário um servidor https confiável. Antes de começar, você precisará instalar um certificado SSL para permitir que os ativos visuais sejam carregados no navegador da Web. 

> [!NOTE]
> Esta é uma instalação única para a estação de trabalho do desenvolvedor.
> 
> 

Para *adicionar* um certificado, execute o seguinte comando.

    pbiviz --install-cert

**Sistema operacional Windows**

1. Selecione **Instalar Certificado...**.
   
    ![](media/service-custom-visuals-getting-started-with-developer-tools/install-ssl-certificate-windows.png)
2. Selecione **Usuário Atual** e, em seguida, **Avançar**.
   
    ![](media/service-custom-visuals-getting-started-with-developer-tools/install-ssl-certificate-windows2.png)
3. Selecione **Colocar todos os certificados no repositório a seguir** e selecione **Procurar...**.
4. Selecione **Autoridades de Certificação Confiáveis** e, em seguida, **OK**. Selecione **Avançar**.
   
    ![](media/service-custom-visuals-getting-started-with-developer-tools/install-ssl-certificate-windows3.png)
5. Selecione **Concluir**.
   
    ![](media/service-custom-visuals-getting-started-with-developer-tools/install-ssl-certificate-windows4.png)
6. Selecione **Sim** na caixa de diálogo de aviso de segurança.
   
    ![](media/service-custom-visuals-getting-started-with-developer-tools/install-ssl-certificate-windows5.png)
7. Feche todos os navegadores que estiverem abertos.

> [!NOTE]
> Se o certificado não for reconhecido, poderá ser necessário reiniciar o computador.
> 
> 

**OSX**

1. Se o bloqueio na parte superior esquerda estiver bloqueado, selecione-o para desbloquear. Pesquise *localhost* e clique duas vezes no certificado.
   
    ![](media/service-custom-visuals-getting-started-with-developer-tools/install-ssl-certificate-osx.png)
2. Selecione **Sempre Confiar** e feche a janela.
   
    ![](media/service-custom-visuals-getting-started-with-developer-tools/install-ssl-certificate-osx2.png)
3. Insira seu nome de usuário e sua senha. Selecione **Atualizar Configurações**.
   
    ![](media/service-custom-visuals-getting-started-with-developer-tools/install-ssl-certificate-osx3.png)
4. Feche todos os navegadores que estiverem abertos.

> [!NOTE]
> Se o certificado não for reconhecido, poderá ser necessário reiniciar o computador.
> 
> 

## <a name="enable-live-preview-of-developer-visual"></a>Habilitar visualização dinâmica do visual do desenvolvedor
Para habilitar uma visualização dinâmica de seu visual personalizado, siga estas etapas. Assim, o visual poderá ser usado dentro do serviço do Power BI durante a edição de relatórios.

1. Procure [app.powerbi.com](https://app.powerbi.com) e entre.
2. Selecione o **ícone de engrenagem** e, em seguida, **Configurações**.
   
    ![](media/service-custom-visuals-getting-started-with-developer-tools/powerbi-settings.png)
3. Selecione **Desenvolvedor** e, em seguida, **Habilitar visual do desenvolvedor para teste**.
   
    ![](media/service-custom-visuals-getting-started-with-developer-tools/powerbi-settings-enable-developer-live-preview.png)
4. Selecione o **Visual do Desenvolvedor** no painel **Visualização**.
   
    ![](media/service-custom-visuals-getting-started-with-developer-tools/powerbi-developer-visual-selection.png)
   
   > [!NOTE]
   > Para isso, é necessário ter executado `pbiviz start` na pasta do visual no computador de desenvolvimento. Para saber mais sobre como criar seu visual, consulte [Criar um novo visual](#create-a-new-visual) neste artigo.
   > 
   > 
5. Selecione o visual na tela do relatório. Você pode associar dados da mesma maneira que faria com outros visuais.

Agora você pode começar a desenvolver seu visual.

## <a name="create-a-new-visual"></a>Criar um novo visual
Você pode criar um novo projeto de visual, executando o comando a seguir.

```
pbiviz new My Visual name
```

Você pode substituir *Nome do Meu Visual* pelo nome que deseja dar ao visual. Isso poderá ser alterado posteriormente, modificando os campos `name` e `displayName` no arquivo `pbiviz.json` gerado.

Esse comando criará uma nova pasta no direto no qual o comando foi executado. Será gerado um modelo básico inicial para seu visual. Quando o comando for concluído, você poderá abrir o diretório e usar seu editor favorito para começar a trabalhar no novo visual.

## <a name="testing-your-visual-in-power-bi"></a>Testando seu visual no Power BI
Você pode testar seu visual no serviço do Power BI em relatórios e dashboards.

<a name="running-your-visual"></a>

### <a name="running-your-visual"></a>Executando seu visual
Você pode executar o visual, fazendo o seguinte.

1. Abra um prompt.
2. Altere o diretório para a pasta do visual. Esta é a pasta que contém o arquivo `pbiviz.json`.
3. Execute o seguinte comando.
   
    ```
    pbiviz start
    ```
   
    ![](media/service-custom-visuals-getting-started-with-developer-tools/powerbi-start-visual.png)

Se você estiver no local errado, será exibido um erro semelhante ao seguinte.

```
    error  LOAD ERROR Error: pbiviz.json not found. You must be in the root of a visual project to run this command.
        at e (C:\Users\[user]\AppData\Roaming\npm\node_modules\powerbi-visuals-tools\lib\VisualPackage.js:67:35)
        at Function.loadVisualPackage (C:\Users\[user]\AppData\Roaming\npm\node_modules\powerbi-visuals-tools\lib\VisualPackage.js:62:16)
        at Object.<anonymous> (C:\Users\[user]\AppData\Roaming\npm\node_modules\powerbi-visuals-tools\bin\pbiviz-start.js:43:15)
        at Module._compile (module.js:556:32)
        at Object.Module._extensions..js (module.js:565:10)
        at Module.load (module.js:473:32)
        at tryModuleLoad (module.js:432:12)
        at Function.Module._load (module.js:424:3)
        at Module.runMain (module.js:590:10)
        at run (bootstrap_node.js:394:7)
```

### <a name="viewing-your-visual-in-power-bi"></a>Visualizando seu visual no Power BI
Para exibir seu visual em um relatório, acesse o relatório e selecione o visual dentro do painel **Visualizações**.

> [!NOTE]
> Você deve executar o comando `pbiviz start` antes de fazer isso, conforme a descrição na seção [Executando seu visual](#running-your-visual).
> 
> 

![](media/service-custom-visuals-getting-started-with-developer-tools/powerbi-developer-visual-selection.png)

Você verá o modelo inicial do visual.

![](media/service-custom-visuals-getting-started-with-developer-tools/powerbi-visual.png)

| Item da barra de ferramentas | Descrição |
| --- | --- |
| Atualizar o visual |Atualize o visual manualmente se o recarregamento automático estiver desabilitado. |
| Ativar/desativar recarregamento automático |Quando ativado, o visual será atualizado automaticamente sempre que você salvar seu arquivo de visual. |
| Mostrar exibição de dados |Mostra a exibição de dados subjacente do visual para depuração |
| Obter ajuda |Documentação no GitHub |
| Enviar comentários |Queremos saber se existe alguma forma de melhorarmos a experiência! (Requer uma conta do GitHub) |

## <a name="package-your-visual-for-use-in-power-bi-desktop-and-distribution"></a>Empacotar o visual para usar no Power BI Desktop e em distribuições
Antes de carregar seu visual no [Power BI Desktop](https://powerbi.microsoft.com/desktop/) ou compartilhá-lo com a comunidade na [Galeria de Visuais do Power BI](https://visuals.powerbi.com), você deverá gerar um arquivo `pbiviz`.

Você pode empacotar o visual, fazendo o seguinte.

1. Abra um prompt.
2. Altere o diretório para a pasta do visual. Esta é a pasta que contém o arquivo `pbiviz.json`.
3. Execute o seguinte comando.
   
    ```
    pbiviz package
    ```

Esse comando criará um `pbiviz` no diretório `dist/` do projeto de visual. Se já houver um arquivo `pbiviz` presente, ele será substituído.

## <a name="updating-the-visuals-api-version"></a>Atualizando a versão da API de visuais
Quando você cria um visual usando `pbiviz new`, uma cópia das definições de tipo e dos esquemas json apropriados da API é enviada para o diretório do seu visual. Você pode usar o comando `pbiviz update` para atualizar esses arquivos, se necessário. Isso poderá ser útil se lançarmos uma correção para uma versão anterior da API ou se você desejar atualizar para a última versão da API.

### <a name="updating-your-existing-api-version"></a>Atualizando a versão da API existente
Se lançarmos uma atualização para uma API existente, você poderá obter a versão mais recente fazendo o seguinte.

```
#Update your version of pbiviz
npm install -g powerbi-visuals-tools

#Run update from the root of your visual project, where pbiviz.json is located
pbiviz update
```

Esse comando baixará as ferramentas mais recentes do npm, incluindo as definições de tipo e os esquemas atualizados. O uso de `pbiviz update` substituirá a propriedade `apiVersion` no campo *pbiviz.json* pela versão mais recente.

### <a name="upgrading-to-a-different-api-version"></a>Atualizando para uma versão diferente da API
Você pode atualizar para uma versão diferente da API usando as mesmas etapas mencionadas acima. Você pode especificar explicitamente a versão da API que deseja usar.

```
#Update your version of pbiviz
npm install -g powerbi-visuals-tools

#Run update from the root of your visual project, where pbiviz.json is located
pbiviz update 1.2.0
```

Esse comando atualizaria seu visual para API versão 1.2.0. Você pode substituir `1.2.0` por qualquer versão que deseje usar.

> [!WARNING]
> A versão padrão da API usada pelas ferramentas sempre será a versão estável. Todas as versões posteriores à versão padrão da API serão instáveis e estarão sujeitas a alteração. Elas podem ter comportamentos inesperados e se comportam de forma diferente entre o serviço do Power BI e o Power BI Desktop. Para saber qual é a versão estável atual da API, veja o [log de alterações](https://github.com/Microsoft/PowerBI-visuals/blob/master/ChangeLog.md). Para obter mais informações sobre as versões de pré-lançamento, veja o [roteiro](https://github.com/Microsoft/PowerBI-visuals/blob/master/Roadmap/README.md).
> 
> 

## <a name="inside-the-visual-project"></a>Dentro do projeto de visual
Seu projeto de visual é a pasta criada ao executar o comando `pbiviz new`. 

### <a name="file-structure"></a>Estrutura do arquivo
| Item | Descrição |
| --- | --- |
| assets/ |Usado para armazenar ativos visuais (ícone, capturas de tela, etc). |
| dist/ |Quando você executar `pbiviz package`, o arquivo pbiviz será gerado aqui. |
| src/ |Código TypeScript do visual. |
| style/ |Estilos Less para seu visual. |
| .gitignore |Informa o git para ignorar os arquivos que não devem ser controlados no repositório. |
| capabilities.json |Usado para definir as [funcionalidades](https://github.com/Microsoft/PowerBI-visuals/blob/master/Capabilities/Capabilities.md) do seu visual. |
| package.json |Usado pelo [npm](https://www.npmjs.com/) para gerenciar módulos. |
| pbiviz.json |Arquivo de configuração principal. |
| tsconfig.json |Configurações do compilador de TypeScript. Saiba mais sobre [tsconfig.json](https://www.typescriptlang.org/docs/handbook/tsconfig-json.html). |

### <a name="pbivizjson"></a>pbiviz.json
Este é o arquivo de configuração principal do seu visual. Ele contém metadados e informações sobre os arquivos necessários para compilar seu visual.

```
{
    "visual": {
        "name": "myVisual", // internal visual name (should not contain spaces)
        "displayName": "My Visual!", // visual name displayed to user (used in gallery)
        "guid": "PBI_CV_xxxxxxx", // a unique id for this visual MUST BE UNIQUE
        "visualClassName": "Visual" // the entry class for your visual
        "version": "1.0.0", // visual version. Should be semantic version (increment if you update the visual)
        "description": "", // description used in gallery
        "supportUrl": "", // url to where users can get support for this visual
        "gitHubUrl": "" // url to the source in github (if applicable)
    },
    "apiVersion": "1.0.0", //API version this visual was created with
    "author": {
        "name": "", // your name
        "email": "" // your e-mail
    },
    "assets": {
        "icon": "assets/icon.png" // relative path to your icon file (20x20 png)
    },
    "style": "style/visual.less", // relative path to your less file
    "capabilities": "capabilities.json" // relative path to your capabilities definition 
}
```

### <a name="visual-source-typescript"></a>Fonte do visual (TypeScript)
O código do visual deve ser gravado em TypeScript, que é um superconjunto do JavaScript com suporte a recursos mais avançados e acesso antecipado às funcionalidades do ES6/ES7.

Todos os arquivos TypeScript devem ser armazenados no diretório `src/` e adicionados à matriz `files` em `tsconfig.json`. Isso permite que o compilador TypeScript os carregue em uma determinada ordem.

Quando o visual for criado, todos os TypeScripts serão compilados em um único arquivo JavaScript. Isso permite que você faça referência a elementos exportados de outros arquivos sem precisar executar `require` neles manualmente, desde que ambos os arquivos estejam listados no tsconfig.

Você pode criar quantos arquivos e classes precisar para criar seu visual.

Saiba mais sobre [TypeScript](http://www.typescriptlang.org/).

### <a name="visual-style-less"></a>Estilo do visual (Less)
A definição de estilo do visual é realizada usando CSS (folhas de estilos em cascata). Para facilitar, usamos o pré-compilador de Less que dá suporte a alguns recursos avançados como aninhamento, variáveis, mesclagens, condições, loops, etc. Se não quiser usar esses recursos, escreva apenas o CSS simples no arquivo Less.

Todos os arquivos Less devem ser armazenados no diretório `style/`. O arquivo especificado no campo `style` dentro do arquivo `pbiviz.json` será carregado. Arquivos adicionais devem ser carregados usando `@import`.

Saiba mais sobre [Less](http://lesscss.org/).

## <a name="debugging"></a>Depuração
Para obter dicas de como depurar seu visual personalizado, veja o [guia depuração](https://github.com/Microsoft/PowerBI-visuals/blob/master/tools/debugging.md).

## <a name="submit-your-visual-to-the-office-store"></a>Envie seu visual para a Office Store
Você pode ser incluído na Office Store. Para obter mais informações sobre este processo, consulte [Publicar visuais personalizados na Office Store](developer/office-store.md).

## <a name="troubleshooting"></a>Solução de problemas
**Comando Pbiviz não encontrado (ou erros semelhantes)**

Se você executar `pbiviz` no seu terminal ou na linha de comando, será exibida a tela de ajuda. Caso contrário, ele não estará instalado corretamente. Verifique se no mínimo a versão 4.0 do NodeJS está instalada.

Para obter mais informações, veja [Instalar o NodeJS e as ferramentas do Power BI](#install-nodejs-and-the-power-bi-tools)...

**Não é possível localizar o elemento visual de depuração na guia Visualizações**

O visual de depuração é semelhante a um ícone de aviso dentro da guia **Visualizações**.

![](media/service-custom-visuals-getting-started-with-developer-tools/powerbi-developer-visual-selection.png)

Se ele não estiver visível, verifique se você o habilitou nas configurações do Power BI. 

> [!NOTE]
> No momento, o visual de depuração somente está disponível no serviço do Power BI, mas não no Power BI Desktop nem no aplicativo móvel. O visual empacotado ainda funcionará em todos os lugares.
> 
> 

Para obter mais informações, veja [Habilitar visualização dinâmica do visual do desenvolvedor](#enable-live-preview-of-developer-visual)...

**Não é possível contatar o servidor de elemento visual**

Execute o servidor de visual com o comando `pbiviz start` no terminal ou na linha de comando da raiz do projeto de visual. Se o servidor estiver em execução, provavelmente os certificados SSL não foram instalados corretamente.

Para obter mais informações, veja [Executando seu visual](#running-your-visual) ou [Instalação de certificado de servidor](#ssl-setup).

## <a name="next-steps"></a>Próximas etapas
[Visualizações no Power BI](power-bi-report-visualizations.md)  
[Visualizações personalizadas no Power BI](power-bi-custom-visuals.md)  
[Publicar visuais personalizados na Office Store](developer/office-store.md)  
[TypeScript](http://www.typescriptlang.org/)  
[CSS Less](http://lesscss.org/)  

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](http://community.powerbi.com/)

