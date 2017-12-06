Nos tópicos anteriores, examinamos como é possível usar o Power BI para se conectar a fontes de dados e como atualizar manualmente os conjuntos de dados no serviço do Power BI. No entanto, você não vai querer atualizar tudo manualmente sempre que os dados forem alterados; assim, é possível usar o Power BI para configurar uma atualização agendada que se conectará às suas fontes de dados e as publicará no serviço do Power BI automaticamente. Isso também fornece uma maneira de se conectar ao serviço com quaisquer fonte de dados locais, incluindo arquivos do Excel, bancos de dados do Access, bancos de dados SQL e muito mais.

O sistema que permite a conexão das fontes de dados locais ao serviço do Power BI é chamado de **gateway de dados**. É um pequeno aplicativo executado no computador que usa um agendamento predefinido para se conectar aos dados, coletar todas as atualizações e enviá-las por push ao serviço do Power BI. O **gateway pessoal** é uma versão do **gateway de dados** que pode ser usada sem nenhuma configuração do administrador.

>[!NOTE]
>O computador executando o Power BI Personal Gateway *deve* estar ligado e conectado à Internet para que o **gateway pessoal** funcione corretamente.
> 

Para configurar o **gateway pessoal**, primeiro faça logon no serviço do Power BI. Selecione o ícone **Baixar** no canto superior direito da tela e, em seguida, selecione **Gateways de Dados** no menu.

![](media/4-6-install-configure-personal-gateway/4-6_1b.png)

Nele, você será direcionado para uma página da Web em que é possível selecionar o **Power BI Gateway – Personal**, conforme mostrado abaixo.

![](media/4-6-install-configure-personal-gateway/4-6_2b.png)

Execute o aplicativo após a conclusão do download e conclua o assistente de instalação.

![](media/4-6-install-configure-personal-gateway/4-6_3a.png)

Em seguida, você será solicitado a iniciar o assistente de configuração para configurar seu gateway.

![](media/4-6-install-configure-personal-gateway/4-6_3b.png)

Primeiro, você deverá fazer logon na conta de serviço do Power BI e, em seguida, fazer logon na conta do Windows do computador, pois o serviço do gateway é executado na sua conta.

![](media/4-6-install-configure-personal-gateway/4-6_3c.png)

Retorne ao serviço do Power BI. Selecione o menu de reticências (três pontos) ao lado do conjunto de dados que você deseja atualizar e, em seguida, selecione **Agendar Atualização**. Isso abrirá a página **Configurações de Atualização**. O Power BI detecta que você instalou um **gateway pessoal** e permite que você saiba seu status.

Selecione **Editar credenciais** ao lado de cada fonte de dados aplicável e configure a autenticação.

![](media/4-6-install-configure-personal-gateway/4-6_6.png)

Por fim, defina as opções em **Agendar Atualização** para ativar as atualizações automáticas e definir quando e com que frequência elas ocorrerão.

![](media/4-6-install-configure-personal-gateway/4-6_7.png)

E isso é tudo. Nos horários agendados, o Power BI acessará essas fontes de dados (usando as credenciais fornecidas e a conexão com o computador que tem o **gateway pessoal** em execução) e atualizará os relatórios e os conjuntos de dados de acordo com o agendamento. Na próxima vez que você acessar o Power BI, esses dashboards, relatórios e conjuntos de dados refletirão os dados da atualização agendada mais recente.

## <a name="next-steps"></a>Próximas etapas
**Parabéns!** Você concluiu esta seção **Explorando dados** do curso **Aprendizagem interativa** sobre o Power BI. O serviço do Power BI está repleto de maneiras interessantes de explorar dados, compartilhar informações e interagir com visuais. Além disso, é acessível de um navegador, de um serviço ao qual você pode se conectar em qualquer lugar onde estiver.

Um parceiro eficiente e conhecido do Power BI é o **Excel**. O Power BI e o Excel foram projetados para funcionar bem juntos; suas pastas de trabalho se sentirão como se estivessem em casa no Power BI, e é fácil inseri-las nele.

![](media/4-6-install-configure-personal-gateway/5-1_1.png)

Como é fácil? Na próxima seção, **Power BI e Excel**, você aprenderá exatamente isso.

Vejo vocês na próxima seção!

