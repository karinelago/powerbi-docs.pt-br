## <a name="limitations"></a>Limitações
Veja a seguir uma lista com as limitações atuais da Segurança em Nível de Linha nos modelos de nuvem.

* Se você já tiver funções e regras definidas no serviço do Power BI, será necessário recriá-las no Power BI Desktop.
* É possível definir a RLS somente nos conjuntos de dados criados usando o cliente do Power BI Desktop. Se desejar habilitar a RLS para conjuntos de dados criados com o Excel, será necessário converter os arquivos em arquivos PBIX primeiro. [Saiba mais](../desktop-import-excel-workbooks.md)
* Somente há suporte para conexões ETL e DirectQuery. Conexões dinâmicas do Analysis Services são tratadas no modelo local.
* No momento, não há suporte para a P e R nem para a Cortana na RLS. Você não verá a caixa de entrada da P e R para os dashboards se todos os modelos tiverem a RLS configurada. Isso está em nossos planos, mas ainda não há um cronograma disponível.
* Atualmente, não há suporte para o compartilhamento externo com conjuntos de dados que usam RLS.
* Para qualquer modelo fornecido, o número máximo de entidade de segurança do Azure AD (ou seja, usuários individuais ou grupos de segurança) que podem ser atribuídos a funções de segurança é 1.000. Para atribuir grandes números de usuários a funções, certifique-se de atribuir grupos de segurança em vez de usuários individuais.

## <a name="known-issues"></a>Problemas conhecidos
Há um problema conhecido que gera uma mensagem de erro quando você tenta publicar usando o Power BI Desktop nos casos em que a publicação já ocorreu. O cenário é descrito a seguir.

1. Sara tem um conjunto de dados que foi publicado no serviço do Power BI e ela configurou a RLS.
2. Sara atualiza o relatório no Power BI Desktop e o publica novamente.
3. Sara recebe um erro.

**Solução alternativa:** publique novamente o arquivo do Power BI Desktop no serviço do Power BI até que esse problema seja resolvido. Você pode fazer isso selecionando **Obter Dados** > **Arquivos**. 

