## <a name="using-the-username-or-userprincipalname-dax-function"></a>Usando a função DAX username() ou userprincipalname()
Você pode tirar proveito das funções DAX *username()* ou *userprincipalname()* dentro de seu conjunto de dados. Você pode usá-las dentro de expressões no Power BI Desktop. Quando você publicar seu modelo, ele será usado no serviço do Power BI.

No Power BI Desktop, *username()* retorna um usuário no formato *DOMÍNIO\Usuário* e *userprincipalname()* retorna um usuário no formato *user@contoso.com*.

No serviço do Power BI, *username()* e *userprincipalname()* retornam o nome UPN do usuário. Isso se parece com um endereço de email.

