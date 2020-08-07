---
title: 'Obter acesso ao Serviço de Locais '
description: Esta seção fornece informações sobre como adicionar um usuário ao Places Service e ao Experience Platform Launch, para que o usuário possa acessar o Places Service.
translation-type: tm+mt
source-git-commit: 26538602a73e806a4822705c7a3aa44d76351030
workflow-type: tm+mt
source-wordcount: '1079'
ht-degree: 7%

---

# Obter acesso ao Serviço de Locais {#adding-user-launch-places}

Você pode acessar o Serviço de Locais no menu de acesso rápido no [Adobe Experience Cloud home](https://experience.adobe.com).
Se sua ID de usuário tiver acesso, você verá o ícone do Serviço de locais, conforme indicado abaixo:

![menu de acesso rápido](/help/assets/quickaccess.png)

Você também pode acessar o Serviço de Locais no menu Adobe Experience Platform:

![Menu Experience Platform](/help/assets/solutionaccessmenu.png)

Se você não vir o Serviço de Locais em nenhum desses menus, entre em contato com um administrador em sua organização para adicionar sua ID de usuário ao Serviço de Locais Principais no Admin Console.

## Adicionando um usuário ao Places Service e Experience Platform Launch

Para permitir que os usuários acessem a interface do usuário do [Experience Platform Launch](https://launch.adobe.com), eles precisam ser adicionados ao Serviço principal do Places no Admin Console como um usuário. Para permitir que os usuários tenham acesso ao Experience Platform Launch, configurem propriedades móveis e usem o SDK do Adobe Experience Platform, eles precisam ser adicionados ao Experience Platform Launch no Admin Console e receber as seguintes permissões para o Experience Platform Launch:

* Todos os direitos de propriedade:
   * Desenvolver
   * Aprovar
   * Publicar
   * Gerenciar extensões
   * Gerenciar ambientes
* Permissão Gerenciar propriedades em Direitos de Empresa

Se esta for a primeira vez que você estiver adicionando um usuário, conclua as etapas a seguir para adicionar usuários ao Experience Platform Launch e ao Places Service. Se você adicionou usuários antes, vários perfis podem ser exibidos, portanto, certifique-se de selecionar o perfil correto.

>[!IMPORTANT]
>
>Somente administradores de organizações podem acessar o Admin Console e adicionar os usuários.

### 1. Verifique se os serviços e o Experience Platform Launch do local estão provisionados

1. Faça logon na organização do seu Experience Cloud.
1. No lado superior direito, clique no alternador de shell de Experience Cloud.

   ![interruptor de concha](/help/assets/places_shell_switcher1.png)

1. Em **[!UICONTROL Platform]**, clique em **[!UICONTROL Administration]**.

   Se não vir **Administração** na lista, você não é um administrador. Você deve entrar em contato com o administrador da organização para concluir este procedimento.

1. Na página Administração de Experience Cloud, no **[!UICONTROL Admin Console]** cartão, clique em **[!UICONTROL Take me there]**.

1. Na Admin Console, se você tiver acesso a várias organizações, verifique se a organização correta está selecionada no lado superior direito da página.

   Esta é a organização à qual você adicionará seus usuários. Se a organização correta não tiver sido selecionada, clique na organização e selecione a organização na lista suspensa.

   >[!IMPORTANT]
   >
   >Se você não tiver acesso a uma organização, isso significa que você não tem acesso administrativo a essa organização.

1. Verify that the cards for **[!UICONTROL Adobe Experience Platform Launch]** and **[!UICONTROL Places Core Services]** are displayed.

   ![](/help/assets/places_provisioned1.png)

   Se forem exibidos, o Places Service e o Experience Platform Launch foram provisionados para sua organização. Se não forem exibidos, eles precisarão ser provisionados para sua organização.


### 2. Configure o perfil e adicione as permissões

1. Configure um perfil Experience Platform Launch, que permite que os usuários adicionados ao perfil usem Experience Platform Launch e suas propriedades móveis com o SDK Experience Platform.

   a. Na barra de menus, clique em **[!UICONTROL Product]**.

   b. No painel esquerdo, na lista dos produtos, clique em **[!UICONTROL Adobe Experience Platform Launch]**.

   * Os perfis Experience Platform Launch são exibidos à direita.
   * Experience Platform Launch tem um perfil padrão chamado *Launch - (nome da organização)* .

      Se você adicionou usuários ao Experience Platform Launch anteriormente, você pode ver vários perfis listados.

1. Selecione o perfil correto:

   a. Clique no nome do perfil padrão.

   b. Click the **[!UICONTROL Permissions]** tab.

   c. Clique **[!UICONTROL Edit]** ao lado de **[!UICONTROL Property Rights]**.

   d. No painel esquerdo, clique em **[!UICONTROL + Add all]**.

   Esta etapa move todas as permissões disponíveis para a lista de permissões incluída.

   e. Clique em **[!UICONTROL Company Rights]**.

   f. No painel esquerdo, clique em **[!UICONTROL + Manage Properties]**.

   g. Clique em **[!UICONTROL Save]**.

>[!IMPORTANT]
>
>Para o Serviço de Locais, há um perfil padrão, mas você não precisa adicionar permissões.

Você adicionou com êxito permissões ao perfil criado.

### 3. Adicione um usuário ou desenvolvedor ao seu Serviço Places e perfis Experience Platform Launch

Você pode adicionar um usuário e/ou desenvolvedor ao Serviço de Locais e aos perfis de Experience Platform Launch.

### Adicionar um usuário

Para adicionar um usuário ao Serviço de Locais e aos perfis de Experience Platform Launch:

1. Adicione um usuário ao perfil Experience Platform Launch.

   a. Na barra de menus, clique em **[!UICONTROL Overview]**.

   b. Na **[!UICONTROL Adobe Experience Platform Launch]** placa, verifique o seguinte:

   * Dois pontos são exibidos na parte inferior do cartão.
   * O ponto à esquerda é preto.

      Se o ponto no lado direito estiver preto, você só poderá adicionar desenvolvedores. Para adicionar um usuário, clique no ponto à esquerda.
   c. Clique em **[!UICONTROL + Add Users]**.

   d. Insira o Adobe ID do usuário.

   e. Conclua uma das seguintes etapas:

   * Se você estiver adicionando um novo usuário, clique em **[!UICONTROL New user]** e insira o nome e sobrenome do usuário.
   * Se você estiver adicionando um usuário existente, clique no nome do usuário exibido.

   f. Na lista **[!UICONTROL Please select a profile for this product]** suspensa, selecione o perfil editado anteriormente.

   g. Clique em **[!UICONTROL Save]**.

1. Adicionar um usuário a **[!UICONTROL Places Core Services]**.

   >[!TIP]
   >
   >Atualmente, todos os usuários do Serviço Local têm as mesmas permissões, portanto, não é necessário editar as permissões.

   a. Na **[!UICONTROL Places Core Services]** placa, verifique o seguinte:

   * Dois pontos são exibidos na parte inferior do cartão.
   * O ponto à esquerda é preto.

   b. Clique em **[!UICONTROL + Assign Users]**.

   c. Insira o Adobe ID do usuário.

   d. Conclua uma das seguintes etapas:

   * Se você estiver adicionando um novo usuário, clique em **[!UICONTROL New user]** e insira o nome e sobrenome do usuário.
   * Se você estiver adicionando um usuário existente, clique no nome do usuário exibido.

   e. Na lista **[!UICONTROL Please select a profile for this product]** suspensa, selecione o perfil Locais.

   f. Clique em **[!UICONTROL Save]**.

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

1. Na lista **[!UICONTROL Please select a profile for this product]** suspensa, selecione o perfil Places Service.

1. Clique em **Salvar**.

Os usuários recebem um email que notifica sobre o acesso ao Experience Platform Launch. They can can log in to the [Experience Platform Launch](https://launch.adobe.com) or the [Places Service](https://places.adobe.com) UIs for this organization. Se você concluir a etapa 4 no procedimento **Adicionar um desenvolvedor**, o usuário também poderá fazer logon no [console de E/S da Adobe](https://console.adobe.io) para criar uma integração do Places e usar a API REST do Place.
