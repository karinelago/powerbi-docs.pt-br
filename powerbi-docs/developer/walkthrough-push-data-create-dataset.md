---
title: Criar um conjunto de dados
description: "Passo a passo – Enviar dados por push a um conjunto de dados – Criar um conjunto de dados no Power BI"
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
ms.topic: get-started-article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 08/10/2017
ms.author: asaxton
ms.openlocfilehash: b45a6f76a710bc158d0d1763ca10f2125164952a
ms.sourcegitcommit: 284b09d579d601e754a05fba2a4025723724f8eb
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/15/2017
---
# <a name="step-3-create-a-dataset-in-power-bi"></a>Etapa 3: Criar um conjunto de dados no Power BI
Este artigo faz parte do passo a passo para [enviar dados por push a um conjunto de dados](walkthrough-push-data.md).

Na **etapa 2**, [Obter um token de acesso de autenticação](walkthrough-push-data-get-token.md), de Enviar dados por push a um conjunto de dados, você obteve um token para autenticar-se no **Azure AD**. Nesta etapa, você usa o token para chamar a operação [Criar Conjunto de Dados](https://msdn.microsoft.com/library/mt203562.aspx)

Para fazer uma chamada para um recurso REST, você usa uma URL que localiza o recurso e envia uma cadeia de caracteres JSON (JavaScript Object Notation), que descreve o conjunto de dados, ao recurso de serviço do Power BI. Um recurso REST identifica a parte do serviço do Power BI com que você deseja trabalhar. Para enviar dados por push ao conjunto de dados, o recurso de destino é um **Conjunto de Dados**. A URL que identifica um conjunto de dados é https://api.PowerBI.com/v1.0/myorg/datasets. Se você estiver enviando dados por push em um grupo, a URL será https://api.PowerBI.com/v1.0/myorg/groups/{id_grupo}/datasets.

Para autenticar uma operação REST do Power BI, você adiciona o token que recebeu em [Obter um token de acesso de autenticação](walkthrough-push-data-get-token.md) a um cabeçalho de solicitação:

Quando você chama a operação [Criar Conjunto de Dados](https://msdn.microsoft.com/library/mt203562.aspx), um novo conjunto de dados é criado. Para obter exemplos de como usar a API REST do Power BI, consulte [API REST do Power BI no APIARY](http://docs.powerbi.apiary.io/).

![](media/walkthrough-push-data-create-dataset/powerbi-developer-create-dataset.png)

Veja como criar um conjunto de dados no Power BI.

## <a name="create-a-dataset-in-power-bi"></a>Criar um conjunto de dados no Power BI
> [!NOTE]
> Antes de começar, lembre-se de seguir as etapas anteriores no passo a passo [enviar dados por push a um conjunto de dados](walkthrough-push-data.md).
> 
> 

1. No projeto de Aplicativo de Console criado na [Etapa 2 – Obter um token de acesso de autenticação](walkthrough-push-data-get-token.md), adicione **using System.Net;** e **using System.IO;** a Program.cs.
2. Em Program.cs, adicione o código a seguir.
3. Execute o Aplicativo de Console e faça logon na sua conta do Power BI. Você deve ver **Conjunto de Dados Criado** na janela do Console. Além disso, você pode fazer logon no Power BI para ver o novo conjunto de dados.

**Exemplo de envio dados por push a um conjunto de dados**

Adicione este código a Program.cs.

* Em static void Main(string[] args):
  
    ```
    static void Main(string[] args)
    {
        //Get an authentication access token
        token = GetToken();
  
        //Create a dataset in Power BI
        CreateDataset();
    }
    ```
* Adicione um método CreateDataset():
  
    ```
    #region Create a dataset in Power BI
    private static void CreateDataset()
    {
        //TODO: Add using System.Net and using System.IO
  
        string powerBIDatasetsApiUrl = "https://api.powerbi.com/v1.0/myorg/datasets";
        //POST web request to create a dataset.
        //To create a Dataset in a group, use the Groups uri: https://api.PowerBI.com/v1.0/myorg/groups/{group_id}/datasets
        HttpWebRequest request = System.Net.WebRequest.Create(powerBIDatasetsApiUrl) as System.Net.HttpWebRequest;
        request.KeepAlive = true;
        request.Method = "POST";
        request.ContentLength = 0;
        request.ContentType = "application/json";
  
        //Add token to the request header
        request.Headers.Add("Authorization", String.Format("Bearer {0}", token));
  
        //Create dataset JSON for POST request
        string datasetJson = "{\"name\": \"SalesMarketing\", \"tables\": " +
            "[{\"name\": \"Product\", \"columns\": " +
            "[{ \"name\": \"ProductID\", \"dataType\": \"Int64\"}, " +
            "{ \"name\": \"Name\", \"dataType\": \"string\"}, " +
            "{ \"name\": \"Category\", \"dataType\": \"string\"}," +
            "{ \"name\": \"IsCompete\", \"dataType\": \"bool\"}," +
            "{ \"name\": \"ManufacturedOn\", \"dataType\": \"DateTime\"}" +
            "]}]}";
  
        //POST web request
        byte[] byteArray = System.Text.Encoding.UTF8.GetBytes(datasetJson);
        request.ContentLength = byteArray.Length;
  
        //Write JSON byte[] into a Stream
        using (Stream writer = request.GetRequestStream())
        {
            writer.Write(byteArray, 0, byteArray.Length);
  
            var response = (HttpWebResponse)request.GetResponse();
  
            Console.WriteLine(string.Format("Dataset {0}", response.StatusCode.ToString()));
  
            Console.ReadLine();
        }
    }
    #endregion
    ```

A próxima etapa mostra como [obter um conjunto de dados para adicionar linhas a uma tabela do Power BI](walkthrough-push-data-get-datasets.md).

Apresentamos abaixo a [listagem de código completa](#code).

<a name="code"/>

## <a name="complete-code-listing"></a>Listagem de código completo
    using System;
    using Microsoft.IdentityModel.Clients.ActiveDirectory;
    using System.Net;
    using System.IO;

    namespace walkthrough_push_data
    {
        class Program
        {
            private static string token = string.Empty;

            static void Main(string[] args)
            {

                //Get an authentication access token
                token = GetToken();

                //Create a dataset in Power BI
                CreateDataset();

            }

            #region Get an authentication access token
            private static string GetToken()
            {
                // TODO: Install-Package Microsoft.IdentityModel.Clients.ActiveDirectory -Version 2.21.301221612
                // and add using Microsoft.IdentityModel.Clients.ActiveDirectory

                //The client id that Azure AD created when you registered your client app.
                string clientID = "{Client_ID}";

                //RedirectUri you used when you register your app.
                //For a client app, a redirect uri gives Azure AD more details on the application that it will authenticate.
                // You can use this redirect uri for your client app
                string redirectUri = "https://login.live.com/oauth20_desktop.srf";

                //Resource Uri for Power BI API
                string resourceUri = "https://analysis.windows.net/powerbi/api";

                //OAuth2 authority Uri
                string authorityUri = "https://login.windows.net/common/oauth2/authorize";

                //Get access token:
                // To call a Power BI REST operation, create an instance of AuthenticationContext and call AcquireToken
                // AuthenticationContext is part of the Active Directory Authentication Library NuGet package
                // To install the Active Directory Authentication Library NuGet package in Visual Studio,
                //  run "Install-Package Microsoft.IdentityModel.Clients.ActiveDirectory" from the nuget Package Manager Console.

                // AcquireToken will acquire an Azure access token
                // Call AcquireToken to get an Azure token from Azure Active Directory token issuance endpoint
                AuthenticationContext authContext = new AuthenticationContext(authorityUri);
                string token = authContext.AcquireToken(resourceUri, clientID, new Uri(redirectUri)).AccessToken;

                Console.WriteLine(token);
                Console.ReadLine();

                return token;
            }

            #endregion


            #region Create a dataset in Power BI
            private static void CreateDataset()
            {
                //TODO: Add using System.Net and using System.IO

                string powerBIDatasetsApiUrl = "https://api.powerbi.com/v1.0/myorg/datasets";
                //POST web request to create a dataset.
                //To create a Dataset in a group, use the Groups uri: https://api.PowerBI.com/v1.0/myorg/groups/{group_id}/datasets
                HttpWebRequest request = System.Net.WebRequest.Create(powerBIDatasetsApiUrl) as System.Net.HttpWebRequest;
                request.KeepAlive = true;
                request.Method = "POST";
                request.ContentLength = 0;
                request.ContentType = "application/json";

                //Add token to the request header
                request.Headers.Add("Authorization", String.Format("Bearer {0}", token));

                //Create dataset JSON for POST request
                string datasetJson = "{\"name\": \"SalesMarketing\", \"tables\": " +
                    "[{\"name\": \"Product\", \"columns\": " +
                    "[{ \"name\": \"ProductID\", \"dataType\": \"Int64\"}, " +
                    "{ \"name\": \"Name\", \"dataType\": \"string\"}, " +
                    "{ \"name\": \"Category\", \"dataType\": \"string\"}," +
                    "{ \"name\": \"IsCompete\", \"dataType\": \"bool\"}," +
                    "{ \"name\": \"ManufacturedOn\", \"dataType\": \"DateTime\"}" +
                    "]}]}";

                //POST web request
                byte[] byteArray = System.Text.Encoding.UTF8.GetBytes(datasetJson);
                request.ContentLength = byteArray.Length;

                //Write JSON byte[] into a Stream
                using (Stream writer = request.GetRequestStream())
                {
                    writer.Write(byteArray, 0, byteArray.Length);

                    var response = (HttpWebResponse)request.GetResponse();

                    Console.WriteLine(string.Format("Dataset {0}", response.StatusCode.ToString()));

                    Console.ReadLine();
                }
            }
            #endregion
        }
    }


[Próxima etapa >](walkthrough-push-data-get-datasets.md)

## <a name="next-steps"></a>Próximas etapas
[Obter um conjunto de dados para adicionar linhas em uma tabela do Power BI](walkthrough-push-data-get-datasets.md)  
[Obter um token de acesso de autenticação](walkthrough-push-data-get-token.md)  
[Criar conjunto de dados](https://msdn.microsoft.com/library/mt203562.aspx)  
[Enviar dados por push a um Dashboard do Power BI](walkthrough-push-data.md)  
[Visão geral da API REST do Power BI](overview-of-power-bi-rest-api.md)  
[Referência da API REST do Power BI](https://msdn.microsoft.com/library/mt147898.aspx)  
[API REST do Power BI no APIARY](http://docs.powerbi.apiary.io/)  

Mais perguntas? [Experimente a Comunidade do Power BI](http://community.powerbi.com/)

