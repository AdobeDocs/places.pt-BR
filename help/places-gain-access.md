---
source-git-commit: 9b5ed11499da580e48ae27affda238ce6d91f435
translation-type: tm+mt

---
# Acesso ao serviço de localização da plataforma Adobe Experience {#adding-user-launch-places}

Você pode acessar o Serviço de localização da plataforma no menu de acesso rápido na página inicial [da](https://experience.adobe.com)Adobe Experience Cloud.
Se sua ID de usuário tiver acesso, você verá o ícone Serviço de localização conforme indicado abaixo:

![menu de acesso rápido](/help/assets/quick-access.png)

Você também pode acessar o Serviço de localização de plataforma no menu da plataforma Adobe Experience:

![Menu Plataforma de experiência](/help/assets/exp-platform-menu-sm.png)

Se você não vir o Serviço de localização de plataforma em nenhum desses menus, será necessário entrar em contato com um administrador em sua organização para adicionar a ID de usuário ao Serviço de local principal no Admin Console.

## Adicionando um usuário ao Serviço de localização e ao Experience Platform Launch

Para permitir que os usuários acessem a interface do usuário [do](https://places.adobe.com)Serviço de inicialização, eles precisam ser adicionados ao Serviço principal do Places no Admin Console como um usuário. Para permitir que os usuários tenham acesso ao Experience Platform Launch, configurem propriedades móveis e usem o SDK do Adobe Experience Platform, eles precisam ser adicionados ao Experience Platform Launch no Admin Console e receber as seguintes permissões para o Experience Platform Launch:

* Todos os direitos de propriedade:
   * Desenvolver
   * Aprovar
   * Publicar
   * Gerenciar extensões
   * Gerenciar ambientes
* Permissão Gerenciar propriedades sob direitos da empresa

Se esta for a primeira vez que você estiver adicionando um usuário, conclua as etapas a seguir para adicionar usuários ao Serviço de Localização e Inicialização da plataforma Experience. Se você tiver adicionado usuários antes, vários perfis poderão ser exibidos, portanto, certifique-se de selecionar o perfil correto.

>[!IMPORTANT]
>
>Somente administradores de organizações podem acessar o Admin Console e adicionar os usuários.

### 1. Verifique se o Serviço de localização e o Experience Platform Launch foram provisionados

Para verificar se o Serviço de localização e o Experience Platform Launch foram provisionados:

1. Faça logon na organização da Experience Cloud.
1. No lado superior direito, clique no alternador de shell da Experience Cloud.

   ![interruptor de concha](/help/assets/places_shell_switcher1.png)

1. Em **[!UICONTROL Platform]**, clique em **[!UICONTROL Administration]**.

   Se não vir **Administração** na lista, você não é um administrador. Você deve entrar em contato com o administrador da organização para concluir este procedimento.

1. Na página Administração da Experience Cloud, no **[!UICONTROL Admin Console]** cartão, clique em **[!UICONTROL Take me there]**.

1. No Admin Console, se você tiver acesso a várias organizações, verifique se a organização correta está selecionada no lado superior direito da página.

   Esta é a organização à qual você adicionará seus usuários. Se a organização correta não tiver sido selecionada, clique na organização e selecione a organização na lista suspensa.

   >[!IMPORTANT]
   >
   >Se você não tiver acesso a uma organização, isso significa que você não tem acesso administrativo a essa organização.

1. Verify that the cards for **[!UICONTROL Adobe Experience Platform Launch]** and **[!UICONTROL Places Core Services]** are displayed.

   ![](/help/assets/places_provisioned1.png)

   Se forem exibidos, o Serviço de localização e o lançamento da plataforma de experiência foram provisionados para sua organização. Se não forem exibidos, eles precisarão ser provisionados para sua organização.


### 2. Configure o perfil e adicione as permissões

Para configurar o perfil e adicionar as permissões:

1. Configure um perfil do Experience Platform Launch, que permite que os usuários adicionados ao perfil usem o Experience Platform Launch e suas propriedades móveis com o Experience Platform SDK.

   a. Na barra de menus, clique em **[!UICONTROL Product]**.

   b. No painel esquerdo, na lista de produtos, clique em **[!UICONTROL Adobe Experience Platform Launch]**.

   * Os perfis do Experience Platform Launch são exibidos à direita.
   * O Experience Platform Launch tem um perfil padrão chamado *Launch - (nome da organização)* .

      Se você adicionou usuários anteriormente ao Experience Platform Launch, você pode ver vários perfis listados.

1. Selecione o perfil correto:

   a. Clique no nome do perfil padrão.

   b. Clique na **[!UICONTROL Permissions]** guia.

   c. Clique **[!UICONTROL Edit]** ao lado de **[!UICONTROL Property Rights]**.

   d. No painel esquerdo, clique em **[!UICONTROL + Add all]**.

   Esta etapa move todas as permissões disponíveis para a lista de permissões incluída.

   e.Clique em **[!UICONTROL Company Rights]**.

   f. No painel esquerdo, clique em **[!UICONTROL + Manage Properties]**.

   g.Clique em **[!UICONTROL Save]**.

>[!IMPORTANT]
>
>Para o Serviço de localização, há um perfil padrão, mas você não precisa adicionar permissões.

Você adicionou com êxito permissões ao perfil criado.

### 3. Adicione um usuário ou desenvolvedor aos seus perfis Serviço de localização e Inicialização da plataforma Experience

Você pode adicionar um usuário e/ou desenvolvedor aos perfis de Serviço de localização e Inicialização da plataforma de experiência.

### Adicionar um usuário

Para adicionar um usuário aos perfis Local Service e Experience Platform Launch:

1. Adicione um usuário ao perfil do Experience Platform Launch.

   a. Na barra de menus, clique em **[!UICONTROL Overview]**.

   b. Na **[!UICONTROL Adobe Experience Platform Launch]** placa, verifique o seguinte:

   * Dois pontos são exibidos na parte inferior do cartão.
   * O ponto à esquerda é preto.

      Se o ponto no lado direito estiver preto, você só poderá adicionar desenvolvedores. Para adicionar um usuário, clique no ponto à esquerda.
   c.Clique em **[!UICONTROL + Add Users]**.

   d. Insira a Adobe ID do usuário.

   e. Conclua uma das seguintes etapas:

   * Se você estiver adicionando um novo usuário, clique em **[!UICONTROL New user]** e insira o nome e sobrenome do usuário.
   * Se você estiver adicionando um usuário existente, clique no nome do usuário exibido.
   f. Na lista **[!UICONTROL Please select a profile for this product]** suspensa, selecione o perfil editado anteriormente.

   g.Clique em **[!UICONTROL Save]**.

1. Adicionar um usuário a **[!UICONTROL Places Core Services]**.

   >[!TIP]
   >
   >Atualmente, todos os usuários do Serviço de Localização têm as mesmas permissões, portanto, não é necessário editar as permissões.

   a. Na **[!UICONTROL Places Core Services]** placa, verifique o seguinte:

   * Dois pontos são exibidos na parte inferior do cartão.
   * O ponto à esquerda é preto.
   b.Clique em **[!UICONTROL + Assign Users]**.

   c. Insira a Adobe ID do usuário.

   d. Conclua uma das seguintes etapas:

   * Se você estiver adicionando um novo usuário, clique em **[!UICONTROL New user]** e insira o nome e sobrenome do usuário.
   * Se você estiver adicionando um usuário existente, clique no nome do usuário exibido.
   e. Na lista **[!UICONTROL Please select a profile for this product]** suspensa, selecione o perfil Locais.

   f.Clique em **[!UICONTROL Save]**.

### Adicionar um desenvolvedor

Para usuários que também precisam de acesso à API de serviço da Web, é necessário adicioná-los como um Desenvolvedor.

Para adicionar um desenvolvedor:

1. On the **[!UICONTROL Places Core Services]** card, verify the following:

   * Dois pontos são exibidos na parte inferior do cartão.
   * Clique no ponto à direita para **[!UICONTROL Assign Developers]** aparecer na parte inferior do cartão.

1. Clique em **[!UICONTROL + Assign Developers]**.

1. Insira a Adobe ID do usuário.

1. Conclua uma das seguintes etapas:

   * Se você estiver adicionando um novo usuário, clique em **[!UICONTROL New user]** e insira o nome e sobrenome do usuário.
   * Se você estiver adicionando um usuário existente, clique no nome do usuário exibido.

1. Na lista **[!UICONTROL Please select a profile for this product]** suspensa, selecione o perfil Local Service.

1. Clique em **Salvar**.

Os usuários recebem um email que notifica sobre o acesso ao Experience Platform Launch. Eles podem fazer logon no [Experience Platform Launch](https://launch.adobe.com) ou nas interfaces do usuário do [Places](https://places.adobe.com) para essa organização. Se você concluir a etapa 4 no procedimento **Adicionar um desenvolvedor**, o usuário também poderá fazer logon no [console de E/S da Adobe](https://console.adobe.io) para criar uma integração do Places e usar a API REST do Place.
