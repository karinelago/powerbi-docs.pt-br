## <a name="validating-the-role-within-power-bi-desktop"></a>Validando a função no Power BI Desktop
Depois de criar sua função, você poderá testar os resultados da função no Power BI Desktop. Para fazer isso, selecione **Exibir Como Funções**.

![](./media/rls-desktop-view-as-roles/powerbi-desktop-rls-view-as-roles.png)

A caixa de diálogo **Exibir como funções** permite alterar a exibição do que você está vendo para esse usuário ou essa função específica. Você pode ver as funções que criou.

![](./media/rls-desktop-view-as-roles/powerbi-desktop-rls-view-as-roles-dialog.png)

Selecione a função que criou e, em seguida, selecione **OK** para aplicar essa função ao que está sendo exibido. Os relatórios renderizam somente os dados relevantes para essa função.

Você também pode selecionar **Outro usuário** e fornecer um determinado usuário. É melhor fornecer o nome UPN, pois é ele que o serviço do Power BI usa. Selecione **OK** e os relatórios serão renderizados com base no que esse usuário pode ver. 

![](./media/rls-desktop-view-as-roles/powerbi-desktop-rls-other-user.png)

> [!NOTE]
> No Power BI Desktop, essa opção somente exibirá resultados diferentes se você estiver usando a segurança dinâmica com base em expressões DAX.
> 
> 

