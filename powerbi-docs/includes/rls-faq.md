## <a name="faq"></a>PERGUNTAS FREQUENTES
**Pergunta:** E se eu já tiver criado funções e regras para um conjunto de dados no serviço do Power BI? Elas ainda funcionariam se eu não fizesse nada?  
**Resposta:** não. Os visuais não seriam renderizados corretamente. Você precisará recriar as funções e regras no Power BI Desktop e, em seguida, publicá-las no serviço do Power BI.

**Pergunta:** Posso criar essas funções para fontes de dados do Analysis Services?  
**Resposta:** Sim, é possível se você importou os dados no Power BI Desktop. Se você estiver usando uma conexão dinâmica, não poderá configurar a RLS no serviço do Power BI. Isso é definido no modelo local do Analysis Services.

**Pergunta:** Posso usar a RLS para limitar as colunas ou as medidas acessíveis por meus usuários?  
**Resposta:** não. Se um usuário tiver acesso a uma linha específica de dados, ele poderá ver todas as colunas de dados dessa linha.

**Pergunta:** A RLS permite ocultar dados detalhados, mas conceder acesso aos dados resumidos nos visuais?  
**Resposta:** Não. Você protege linhas individuais de dados, mas os usuários sempre podem ver os detalhes ou os dados resumidos.

