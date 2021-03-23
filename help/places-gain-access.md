---
title: 'Obter acesso ao Places Service '
description: Esta seção fornece informações sobre como adicionar um usuário ao Places Service e ao Experience Platform Launch, para que o usuário possa acessar o Places Service.
translation-type: tm+mt
source-git-commit: ecf50d67d4c08e79d9c3be64480f27d435fd7fcb
workflow-type: tm+mt
source-wordcount: '1160'
ht-degree: 9%

---

# Obter acesso ao Places Service {#adding-user-launch-places}

Você pode acessar o Places Service no menu de acesso rápido em [Adobe Experience Cloud home](https://experience.adobe.com).
Se a ID de usuário tiver acesso, você verá o ícone do Places Service, conforme indicado abaixo:

![menu acesso rápido](/help/assets/quickaccess.png)

Você também pode acessar o Serviço do Places no menu do Adobe Experience Platform:

![Menu Experience Platform](/help/assets/solutionaccessmenu.png)

Se você não vir o Places Service em nenhum desses menus, entre em contato com um administrador em sua organização para adicionar a ID do usuário ao Places Core Service no Admin Console.

## Adicionar um usuário ao Places Service e ao Experience Platform Launch

Para permitir que os usuários acessem a [interface do usuário do Experience Platform Launch](https://launch.adobe.com), eles precisam ser adicionados ao Places Core Service no Admin Console como um usuário. Para permitir que os usuários tenham acesso ao Experience Platform Launch, configure as propriedades móveis e use o Places com o SDK do Adobe Experience Platform, eles precisam ser adicionados ao Experience Platform Launch no Admin Console e receber as seguintes permissões para o Experience Platform Launch:

* Todos os direitos de propriedade:
   * Desenvolver
   * Aprovar
   * Publicar
   * Gerenciar extensões
   * Gerenciar ambientes
* Permissão Gerenciar propriedades em Direitos da empresa

Se esta for a primeira vez que você está adicionando um usuário, conclua as etapas a seguir para adicionar usuários ao Experience Platform Launch e ao Places Service. Se você tiver adicionado usuários antes, vários perfis podem ser exibidos, para garantir que você selecione o perfil correto.

>[!IMPORTANT]
>
>Somente administradores de organização podem acessar o Admin Console e adicionar os usuários.

### 1. Verifique se o Places Service e o Experience Platform Launch estão provisionados

1. Faça logon na organização do Experience Cloud.
1. No canto superior direito, clique no seletor de Experience Cloud shell.

   ![alternador de shell](/help/assets/places_shell_switcher1.png)

1. Em **[!UICONTROL Plataforma]**, clique em **[!UICONTROL Administração]**.

   Se você não vir **[!UICONTROL Administration]** na lista, você não é um administrador. Você deve entrar em contato com o Org Admin para concluir este procedimento.

1. Na página Administração do Experience Cloud, no cartão **[!UICONTROL Admin Console]**, clique em **[!UICONTROL Leve-me lá]**.

1. Na Admin Console, se você tiver acesso a várias organizações, verifique se a organização correta está selecionada no lado superior direito da página.

   Essa é a organização à qual você adicionará seus usuários. Se a organização correta não tiver sido selecionada, clique na organização e selecione a organização na lista suspensa.

   >[!IMPORTANT]
   >
   >Se você não tiver acesso a uma organização, significa que não tem acesso de administrador a essa organização.

1. Verifique se os cartões do **[!UICONTROL Adobe Experience Platform Launch]** e do **[!UICONTROL Places Core Services]** são exibidos.

   ![](/help/assets/places_provisioned1.png)

   Se forem exibidos, o Places Service e o Experience Platform Launch foram provisionados para a organização. Se não forem exibidos, eles precisarão ser provisionados para sua organização.


### 2. Configure o perfil e adicione as permissões

1. Configure um perfil do Experience Platform Launch, que permite que os usuários adicionados ao perfil usem o Experience Platform Launch e suas propriedades móveis com o SDK do Experience Platform.

   a. Na barra de menu, clique em **[!UICONTROL Produto]**.

   b. No painel esquerdo, na lista de produtos, clique em **[!UICONTROL Adobe Experience Platform Launch]**.

   * Os perfis de Experience Platform Launch são exibidos à direita.
   * O Experience Platform Launch tem um perfil padrão chamado *Launch - (nome da organização)* .

      Se você adicionou usuários anteriormente ao Experience Platform Launch, é possível ver vários perfis listados.

1. Selecione o perfil correto:

   a. Clique no nome do perfil padrão.

   b. Clique na guia **[!UICONTROL Permissões]**.

   c. Clique em **[!UICONTROL Editar]** ao lado de **[!UICONTROL Direitos de propriedade]**.

   d. No painel esquerdo, clique em **[!UICONTROL + Adicionar tudo]**.

   Esta etapa move todas as permissões disponíveis para a lista de permissões incluída.

   e. Clique em **[!UICONTROL Direitos da empresa]**.

   f. No painel esquerdo, clique em **[!UICONTROL + Gerenciar propriedades]**.

   g. Clique em **[!UICONTROL Salvar]**.

>[!IMPORTANT]
>
>No Places Service, há um perfil padrão, mas não é necessário adicionar permissões.

Você adicionou com êxito permissões ao perfil criado.

### 3. Adicione um usuário ou desenvolvedor aos perfis do Places Service e do Experience Platform Launch

Você pode adicionar um usuário e/ou desenvolvedor aos perfis do Places Service e do Experience Platform Launch.

### Adicionar um usuário

Para adicionar um usuário aos perfis do Places Service e do Experience Platform Launch:

1. Adicione um usuário ao perfil do Experience Platform Launch.

   a. Na barra de menus, clique em **[!UICONTROL Visão geral]**.

   b. No cartão **[!UICONTROL Adobe Experience Platform Launch]**, verifique o seguinte:

   * Dois pontos são exibidos na parte inferior do cartão.
   * O ponto à esquerda é preto.

      Se o ponto no lado direito estiver preto, você só poderá adicionar desenvolvedores. Para adicionar um usuário, clique no ponto à esquerda.
   c. Clique em **[!UICONTROL + Adicionar usuários]**.

   d. Insira a Adobe ID do usuário.

   e. Conclua uma das seguintes etapas:

   * Se estiver adicionando um novo usuário, clique em **[!UICONTROL Novo usuário]** e insira o nome e sobrenome do usuário.
   * Se você estiver adicionando um usuário existente, clique no nome do usuário que é exibido.

   f. Na lista suspensa **[!UICONTROL Selecione um perfil para este produto]**, selecione o perfil que você editou anteriormente.

   g. Clique em **[!UICONTROL Salvar]**.

1. Adicione um usuário a **[!UICONTROL Serviços principais do Places]**.

   >[!TIP]
   >
   >Atualmente, todos os usuários do Places Service têm as mesmas permissões, portanto, não é necessário editar as permissões.

   a. No cartão **[!UICONTROL Serviços principais do Places]**, verifique o seguinte:

   * Dois pontos são exibidos na parte inferior do cartão.
   * O ponto à esquerda é preto.

   b. Clique em **[!UICONTROL + Atribuir usuários]**.

   c. Insira a Adobe ID do usuário.

   d. Conclua uma das seguintes etapas:

   * Se estiver adicionando um novo usuário, clique em **[!UICONTROL Novo usuário]** e insira o nome e sobrenome do usuário.
   * Se você estiver adicionando um usuário existente, clique no nome do usuário que é exibido.

   e. Na lista suspensa **[!UICONTROL Selecione um perfil para este produto]**, selecione o perfil Places .

   f. Clique em **[!UICONTROL Salvar]**.

### Adicionar um desenvolvedor

Para usuários que também precisam acessar a API do serviço da Web, é necessário adicioná-los como Desenvolvedor.

Para adicionar um desenvolvedor:

1. No cartão do **[!UICONTROL Serviços principais do Places]**, verifique o seguinte:

   * Dois pontos são exibidos na parte inferior do cartão.
   * Clique no ponto à direita para que **[!UICONTROL Atribuir desenvolvedores]** apareça na parte inferior do cartão.

1. Clique em **[!UICONTROL + Atribuir desenvolvedores]**.

1. Insira a Adobe ID do usuário.

1. Conclua uma das seguintes etapas:

   * Se estiver adicionando um novo usuário, clique em **[!UICONTROL Novo usuário]** e insira o nome e sobrenome do usuário.
   * Se você estiver adicionando um usuário existente, clique no nome do usuário que é exibido.

1. Na lista suspensa **[!UICONTROL Selecione um perfil para este produto]**, selecione o perfil do Places Service.

1. Clique em **[!UICONTROL Salvar]**.

Os usuários recebem um email que notifica sobre o acesso ao Experience Platform Launch. Eles podem fazer logon nas interfaces do usuário do [Experience Platform Launch](https://launch.adobe.com) ou do [Places Service](https://places.adobe.com) dessa organização. Se você concluir a etapa 4 no procedimento **[!UICONTROL Adicionar um desenvolvedor]**, o usuário também poderá fazer logon no [console de E/S da Adobe](https://console.adobe.io) para criar uma integração do Places e usar a API REST do Place.
