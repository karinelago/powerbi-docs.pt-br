---
title: Diretrizes de planejamento de capacidade do Servidor de Relatórios do Power BI
description: Este documento oferece diretrizes de planejamento de capacidade do Servidor de Relatórios do Power BI, com o compartilhamento de resultados de execuções de teste de carga de várias cargas de trabalho.
author: parthsha
manager: kfile
ms.reviewer: maghan
ms.service: powerbi
ms.component: powerbi-report-server
ms.topic: conceptual
ms.date: 3/5/2018
ms.author: pashah
ms.openlocfilehash: 3c3295483112ae0b5475e15c2073faba86dfff30
ms.sourcegitcommit: 80d6b45eb84243e801b60b9038b9bff77c30d5c8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34561806"
---
# <a name="capacity-planning-guidance-for-power-bi-report-server"></a>Diretrizes de planejamento de capacidade do Servidor de Relatórios do Power BI
O Servidor de Relatórios do Power BI é uma solução de relatórios corporativos e de BI de autoatendimento que os clientes podem implantar em suas instalações, protegida pelo firewall. Ele combina a funcionalidade de relatório interativo do Power BI Desktop com a plataforma de servidor local do SQL Server Reporting Services. Com o uso intenso e cada vez maior de análises e relatórios nas empresas, a inclusão no orçamento da infraestrutura de hardware e das licenças de software necessárias para dimensionar para uma base de usuários corporativos pode ser um desafio. Este documento tem como objetivo oferecer diretrizes de planejamento de capacidade do Servidor de Relatórios do Power BI, com o compartilhamento de resultados de diversas execuções de teste de carga de várias cargas de trabalho em um servidor de relatório. Embora os relatórios, as consultas e os padrões de uso das organizações variem muito, os resultados apresentados neste documento, juntamente com os testes reais usados e uma descrição detalhada de como eles foram executados, servem como um ponto de referência para qualquer pessoa que está no processo de planejamento do estágio inicial da implantação do Servidor de Relatórios do Power BI.

## <a name="executive-summary"></a>Resumo executivo
Executamos dois tipos diferentes de cargas de trabalho em um Servidor de Relatórios do Power BI; cada carga de trabalho consistia na renderização de diferentes tipos de relatórios, bem como na execução de várias operações do portal da Web. 

* Na carga de trabalho “Intensa de Relatório do Power BI”, a operação executada com mais frequência (ou seja, a operação foi executada 60% do tempo) renderizou relatórios do Power BI.
* Na carga de trabalho “Intensa de Relatório Paginado”, a operação executada com mais frequência renderizou relatórios paginados.

Em uma topologia de quatro servidores do Servidor de Relatórios do Power BI e com a expectativa de que não mais do que 5% dos usuários acessará um servidor de relatório a qualquer momento, a tabela a seguir descreve o número máximo de usuários que pode ser manipulado pelo Servidor de Relatórios do Power BI com, uma confiabilidade de, pelo menos, 99%. 

| Carga de trabalho | 8 núcleos/32 GB de RAM | 16 núcleos/64 GB de RAM |
| --- | --- | --- |
| **Intensa de Relatório do Power BI** (>60%) |1.000 usuários |3.000 usuários |
| **Intensa de Relatório Paginado (RDL)** (>60%) |2.000 usuários |3.200 usuários |

Em cada execução, o recurso mais sobrecarregado foi a CPU. Devido a isso, o aumento do número de núcleos no Servidor de Relatórios do Power BI gerará um ganho maior na confiabilidade do sistema do que o aumento da quantidade de memória ou de espaço em disco rígido. 

## <a name="test-methodology"></a>Metodologia de teste
A topologia de teste usada foi baseada nas Máquinas Virtuais do Microsoft Azure, em vez de no hardware físico específico ao fornecedor. Todos os computadores foram hospedados em regiões dos EUA. Isso reflete a tendência geral da virtualização de hardware local e na nuvem pública. 

### <a name="power-bi-report-server-topology"></a>Topologia do Servidor de Relatórios do Power BI
A implantação do Servidor de Relatórios do Power BI consistiu nas seguintes máquinas virtuais:

* Controlador de Domínio do Active Directory: isso era necessário para o Mecanismo de Banco de Dados do SQL Server, o SQL Server Analysis Services e o Servidor de Relatórios do Power BI para autenticar todas as solicitações com segurança.
* Mecanismo de Banco de Dados do SQL Server e SQL Server Analysis Services: foi neles que armazenamos todos os bancos de dados para consumo dos relatórios quando os renderizamos.
* Servidor de Relatório do Power BI
* Banco de dados do Servidor de Relatórios do Power BI. O banco de dados do servidor de relatório é hospedado em um computador diferente do Servidor de Relatórios do Power BI, de modo que ele não precise competir com o Mecanismo de Banco de Dados do SQL Server por memória, CPU, rede e recursos de disco.

![](media/capacity-planning/report-server-topology.png)

Consulte o Apêndice 1.1 – Topologia do Servidor de Relatórios do Power BI e o Apêndice 1.2 – Configuração de máquina virtual do Servidor de Relatórios do Power BI para obter uma configuração completa de cada máquina virtual usada na topologia.

### <a name="tests"></a>Testes
Os testes usados nas execuções de teste de carga estão disponíveis publicamente em um projeto do GitHub chamado [Reporting Services LoadTest](https://github.com/Microsoft/Reporting-Services-LoadTest). Essa ferramenta permite aos usuários estudar as características de desempenho, confiabilidade, escalabilidade e capacidade de recuperação do SQL Server Reporting Services e do Servidor de Relatórios do Power BI. Este projeto consiste em quatro grupos de casos de teste:

* Testes que simulam a renderização de relatórios do Power BI;
* Testes que simulam a renderização de relatórios móveis;
* Testes que simulam a renderização de relatórios paginados pequenos e grandes; e 
* Testes que simulam a execução de vários tipos de operações do portal da Web. 

Todos os testes foram escritos para executar uma operação de ponta a ponta (como renderização de um relatório, criação de uma nova fonte de dados, etc.). Eles realizam isso fazendo uma ou mais solicitações da Web para o servidor de relatório (por meio de APIs). No mundo real, um usuário pode precisar executar algumas operações intermediárias para concluir uma dessas operações de ponta a ponta. Por exemplo, para renderizar um relatório, um usuário precisará acessar o portal da Web, navegar para a pasta em que o relatório está localizado e, depois, clicar no relatório para renderizá-lo. Embora os testes não executem todas as operações necessárias para realizar uma tarefa de ponta a ponta, eles ainda impõem a maior parte da carga que o Servidor de Relatórios do Power BI experimentará. Saiba mais sobre os diferentes tipos de relatórios usados, bem como a variedade de operações executadas explorando o projeto do GitHub.

### <a name="workloads"></a>Cargas de trabalho
Há dois perfis de carga de trabalho usados no teste: Intensa de Relatório do Power BI e Intensa de Relatório Paginado. A tabela abaixo descreve a distribuição de solicitações executadas no Servidor de Relatórios.

| Atividade | Intensa de Relatório do Power BI, Frequência de ocorrência | Intensa de Relatório Paginado, Frequência de ocorrência |
| --- | --- | --- |
| **Renderização de relatórios do Power BI** |60% |10% |
| **Renderização de relatórios paginados (RDL)** |30% |60% |
| **Renderização de relatórios móveis** |5% |20% |
| **Operações do portal da Web** |5% |10% |

### <a name="user-load"></a>Carga de usuários
Para cada execução de teste, os testes foram executados com base na frequência especificada em uma das duas cargas de trabalho. Os testes foram iniciados com 20 solicitações de usuários simultâneos para o servidor de relatório. Em seguida, a carga de usuários aumentou gradativamente até a confiabilidade cair abaixo da meta de 99%.

## <a name="results"></a>Resultados
### <a name="concurrent-user-capacity"></a>Capacidade de usuários simultâneos
Conforme mencionado anteriormente, os testes foram iniciados com 20 usuários simultâneos fazendo solicitações para o servidor de relatório. Em seguida, o número de usuários simultâneos aumentou gradativamente até 1% de todas as solicitações falhar. Os resultados da tabela a seguir informam o número de solicitações de usuários simultâneos que o servidor poderá manipular sob a carga de pico com uma taxa de falha inferior a 1%.

| Carga de trabalho | 8 núcleos/32 GB | 16 núcleos/64 GB |
| --- | --- | --- |
| **Intensa de Relatório do Power BI** |50 usuários simultâneos |150 usuários simultâneos |
| **Intensa de Relatório Paginado** |100 usuários simultâneos |160 usuários simultâneos |

### <a name="total-user-capacity"></a>Capacidade total de usuários
Na Microsoft, temos uma implantação de produção do Servidor de Relatórios do Power BI que foi usada por várias equipes. Quando analisamos o uso real desse ambiente, observamos que o número de usuários simultâneos em determinado momento (mesmo durante a carga de pico diária) não tende a exceder 5% da base total de usuários. Usando essa proporção de simultaneidade de 5% como um parâmetro de comparação, extrapolamos a base total de usuários que o Servidor de Relatórios do Power BI pode manipular com uma confiabilidade de 99%.

| Carga de trabalho | 8 núcleos/32 GB | 16 núcleos/64 GB |
| --- | --- | --- |
| **Intensa de Relatório do Power BI** |1.000 usuários |3.000 usuários |
| **Intensa de Relatório Paginado** |2.000 usuários |3.200 usuários |

### <a name="view-results"></a>Exibir os resultados
Selecione um relatório para exibir os resultados do teste de carga.

| Carga de trabalho | 8 núcleos/32 GB | 16 núcleos/64 GB |
| --- | --- | --- |
| **Intensa de Relatório do Power BI** |[Exibir – 8 núcleos](https://msit.powerbi.com/view?r=eyJrIjoiMDhhNGY4NGQtNGRhYy00Yzk4LTk2MzAtYzFlNWI5NjBkMGFiIiwidCI6IjcyZjk4OGJmLTg2ZjEtNDFhZi05MWFiLTJkN2NkMDExZGI0NyIsImMiOjV9) |[Exibir – 16 núcleos](https://msit.powerbi.com/view?r=eyJrIjoiNDBiODk1OGUtYTAyOC00MzVhLThmZmYtNzVjNTFjNzMwYzkwIiwidCI6IjcyZjk4OGJmLTg2ZjEtNDFhZi05MWFiLTJkN2NkMDExZGI0NyIsImMiOjV9) |
| **Intensa de Relatório Paginado** |[Exibir – 8 núcleos](https://msit.powerbi.com/view?r=eyJrIjoiNDFiZWYzMTktZGIxNS00MzcwLThjODQtMmJkMGRiZWEzNjhlIiwidCI6IjcyZjk4OGJmLTg2ZjEtNDFhZi05MWFiLTJkN2NkMDExZGI0NyIsImMiOjV9) |[Exibir – 16 núcleos](https://msit.powerbi.com/view?r=eyJrIjoiOTU0YjJkYTgtNDg4Yy00NzlhLWIwMGYtMzg4YWI2MjNmOTZjIiwidCI6IjcyZjk4OGJmLTg2ZjEtNDFhZi05MWFiLTJkN2NkMDExZGI0NyIsImMiOjV9) |

<iframe width="640" height="360" src="https://msit.powerbi.com/view?r=eyJrIjoiMDhhNGY4NGQtNGRhYy00Yzk4LTk2MzAtYzFlNWI5NjBkMGFiIiwidCI6IjcyZjk4OGJmLTg2ZjEtNDFhZi05MWFiLTJkN2NkMDExZGI0NyIsImMiOjV9" frameborder="0" allowFullScreen="true"></iframe>

<iframe width="640" height="360" src="https://msit.powerbi.com/view?r=eyJrIjoiNDBiODk1OGUtYTAyOC00MzVhLThmZmYtNzVjNTFjNzMwYzkwIiwidCI6IjcyZjk4OGJmLTg2ZjEtNDFhZi05MWFiLTJkN2NkMDExZGI0NyIsImMiOjV9" frameborder="0" allowFullScreen="true"></iframe>

<iframe width="640" height="360" src="https://msit.powerbi.com/view?r=eyJrIjoiNDFiZWYzMTktZGIxNS00MzcwLThjODQtMmJkMGRiZWEzNjhlIiwidCI6IjcyZjk4OGJmLTg2ZjEtNDFhZi05MWFiLTJkN2NkMDExZGI0NyIsImMiOjV9" frameborder="0" allowFullScreen="true"></iframe>

<iframe width="640" height="360" src="https://msit.powerbi.com/view?r=eyJrIjoiOTU0YjJkYTgtNDg4Yy00NzlhLWIwMGYtMzg4YWI2MjNmOTZjIiwidCI6IjcyZjk4OGJmLTg2ZjEtNDFhZi05MWFiLTJkN2NkMDExZGI0NyIsImMiOjV9" frameborder="0" allowFullScreen="true"></iframe>

## <a name="summary"></a>Resumo
Para cada execução de teste de carga, a CPU foi o recurso mais sobrecarregado no ponto de carga de pico no computador do Servidor de Relatórios do Power BI. Devido a isso, o primeiro recurso que deve ser aumentado é o número de núcleos. Como alternativa, você pode considerar a possibilidade de expandir com a adição de mais servidores que hospedam o Servidor de Relatórios do Power BI na topologia.

Os resultados apresentados neste documento foram obtidos com a execução de um conjunto específico de relatórios que consumiram um conjunto específico de dados, repetidos de uma maneira específica. É um ponto de referência útil, mas tenha em mente que o uso dependerá dos relatórios, das consultas, dos padrões de uso e da implantação do Servidor de Relatórios do Power BI.

## <a name="appendix"></a>Apêndice
### <a name="1-topology"></a>1 Topologia
**1.1 Topologia do Servidor de Relatórios do Power BI**

Para se concentrar apenas no comportamento do Servidor de Relatórios do Power BI em configurações diferentes, a configuração de VM de cada tipo de computador (com exceção do computador que hospeda o Servidor de Relatórios do Power BI) foi corrigida. Cada computador foi provisionado de acordo com os computadores da Série D de segunda geração (v2) com Discos de Armazenamento Premium. Você pode encontrar informações detalhadas sobre cada tamanho da VM na seção "Propósito geral" em https://azure.microsoft.com/en-us/pricing/details/virtual-machines/windows/.

| Tipo de máquina virtual | Processador | Memória | Tamanho de VM do Azure |
| --- | --- | --- | --- |
| **Controlador de Domínio do Active Directory** |2 núcleos |7 GB |Standard_DS2_v2 |
| **Mecanismo de Banco de Dados do SQL Server e Analysis Services** |16 núcleos |56 GB |Standard_DS5_v2 |
| **Banco de dados do servidor de relatório** |16 núcleos |56 GB |Standard_DS5_v2 |

**1.2 Configuração de máquina virtual do Servidor de Relatórios do Power BI** 

Foram usadas configurações diferentes de processador e memória para a Máquina Virtual que hospeda o Servidor de Relatórios do Power BI. Ao contrário das outras VMs, esse computador foi provisionado de acordo com os Computadores da Série D de terceira geração (v3) máquinas com Discos de Armazenamento Premium. Você pode encontrar informações detalhadas sobre este tamanho da VM na seção "Propósito geral" em https://azure.microsoft.com/en-us/pricing/details/virtual-machines/windows/.

| Máquina virtual | Processador | Memória | Tamanho de VM do Azure |
| --- | --- | --- | --- |
| **Servidor de Relatórios do Power BI (Pequeno)** |8 núcleos |32 GB |Standard_D8S_v3 |
| **Servidor de Relatórios do Power BI (Grande)** |16 núcleos |64 GB |vStandard_D16S_v3 |

### <a name="2-run-the-loadtest-tool"></a>2 Executar a ferramenta LoadTest
Se você deseja executar a ferramenta LoadTest do Reporting Services em uma implantação sua ou uma implantação do Microsoft Azure do Servidor de Relatórios do Power BI, siga estas etapas.

1. Clone o projeto Reporting Services LoadTest do GitHub (https://github.com/Microsoft/Reporting-Services-LoadTest).
2. No diretório do projeto, você encontrará um arquivo de solução chamado RSLoadTests.sln. Abra esse arquivo no Visual Studio 2015 ou posterior.
3. Determine se deseja executar essa ferramenta em sua implantação do Servidor de Relatórios do Power BI ou em uma implantação do Servidor de Relatórios do Power BI no Microsoft Azure. Se você pretende executá-la em sua implantação, vá para a etapa 5.
4. Siga as instruções apresentadas em https://github.com/Microsoft/Reporting-Services-LoadTest#create-a-sql-server-reporting-services-load-environment-in-azure para criar um ambiente de Servidor de Relatórios do Power BI no Azure.
5. Depois de concluir a implantação do ambiente, siga as instruções apresentadas em https://github.com/Microsoft/Reporting-Services-LoadTest#load-test-execution para executar os testes.

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)


