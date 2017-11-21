---
title: Conectar-se ao IntelliBoard com o Power BI
description: IntelliBoard para o Power BI
services: powerbi
documentationcenter: 
author: joeshoukry
manager: kfile
backup: maggiesMSFT
editor: 
tags: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 10/16/2017
ms.author: yshoukry
ms.openlocfilehash: f668a1c9bfefb1b0b0c7c15f9d68c82312d38105
ms.sourcegitcommit: 284b09d579d601e754a05fba2a4025723724f8eb
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/15/2017
---
# <a name="connect-to-intelliboard-with-power-bi"></a>Conectar-se ao IntelliBoard com o Power BI
O IntelliBoard oferece acesso simplificado aos dados do sistema de gerenciamento de aprendizado Moodle por meio do Reporting Services. O pacote de conteúdo do IntelliBoard para o Power BI oferece análises adicionais, incluindo métricas sobre cursos, usuários registrados, desempenho geral e atividade de LMS.

Conecte-se ao [pacote de conteúdo do IntelliBoard](https://app.powerbi.com/getdata/services/intelliboard) para o Power BI.

## <a name="how-to-connect"></a>Como se conectar
1. Selecione **Obter Dados** na parte inferior do painel de navegação esquerdo.  
   
    ![](media/service-connect-to-intelliboard/getdata.png)
2. Na caixa **Serviços** , selecione **Obter**.  
   
    ![](media/service-connect-to-intelliboard/services.png)
3. Selecione **IntelliBoard** e, em seguida, **Obter**.  
   
    ![](media/service-connect-to-intelliboard/intelliboard.png)
4. Selecione **OAuth 2** e **Entrar**. Quando solicitado, forneça suas credenciais do IntelliBoard.
   
    ![](media/service-connect-to-intelliboard/creds.png)
   
    ![](media/service-connect-to-intelliboard/creds2.png)
5. Depois que você estiver conectado, um dashboard, relatório e conjunto de dados serão carregados automaticamente. Após a conclusão, os blocos serão atualizados com dados de sua conta do IntelliBoard.
   
    ![](media/service-connect-to-intelliboard/dashboard.png)

**E agora?**

* Tente [fazer uma pergunta na caixa de P e R](service-q-and-a.md) na parte superior do dashboard
* [Altere os blocos](service-dashboard-edit-tile.md) no dashboard.
* [Selecione um bloco](service-dashboard-tiles.md) para abrir o relatório subjacente.
* Enquanto seu conjunto de dados será agendado para ser atualizado diariamente, você pode alterar o agendamento de atualização ou tentar atualizá-lo sob demanda usando **Atualizar Agora**

## <a name="whats-included"></a>O que está incluído
O pacote de conteúdo inclui dados das seguintes tabelas:  

    - Atividade  
    - Agentes  
    - Autenticação  
    - Países  
    - CoursesProgress  
    - Registros
    - Idioma  
    - Plataforma  
    - Totais  
    - UsersProgress    

## <a name="system-requirements"></a>Requisitos de sistema
É necessário ter uma conta do IntelliBoard com permissões de acesso às tabelas acima para criar uma instância deste pacote de conteúdo.

## <a name="next-steps"></a>Próximas etapas
[Introdução ao Power BI](service-get-started.md)

[Power BI – conceitos básicos](service-basic-concepts.md)

