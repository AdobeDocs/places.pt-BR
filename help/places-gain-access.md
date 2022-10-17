---
title: Obter acesso ao Places Service
description: Esta seção fornece informações sobre como adicionar um usuário ao Places Service e ao Experience Platform Launch, para que o usuário possa acessar o Places Service.
exl-id: f388945e-cf26-4694-9697-9fe564ae4b69
source-git-commit: c9058e9b70c2ef97151078f43913963471730bd2
workflow-type: tm+mt
source-wordcount: '913'
ht-degree: 1%

---

# Obter acesso ao Places Service {#adding-user-launch-places}

O Places Service agora está disponível na interface do usuário da coleta de dados. Você pode acessar a Coleta de dados no menu de acesso rápido em [Página inicial do Adobe Experience Cloud](https://experience.adobe.com).

![menu acesso rápido](/help/assets/quickaccess.png)

Também é possível acessar a Coleta de dados no menu do Adobe Experience Platform:

![Menu Experience Platform](/help/assets/solutionaccessmenu.png)

Se a ID de usuário tiver acesso, você verá o ícone do Places Service no painel esquerdo, em Gerenciamento de dados na Coleta de dados, conforme indicado abaixo:

![Painel esquerdo Coleta de dados](/help/assets/places_in_data_collection.png)

Se você não vir o Places Service nesse local, entre em contato com um administrador em sua organização para adicionar a ID do usuário ao Adobe Experience Platform no Admin Console.

## Adicionar um usuário para acessar o Places Service e a Coleta de dados da Experience Adobe Experience Platform

O Places agora está incluído no Adobe Experience Platform. Para permitir que os usuários acessem a variável [Serviço Places](https://experience.adobe.com/#/data-collection/places), eles precisam ser adicionados ao Adobe Experience Platform no Admin Console as a user. Para permitir que os usuários tenham acesso à Coleta de dados do Experience Platform com as permissões necessárias para configurar as propriedades móveis e usar o Places com o Adobe Experience Platform SDK, eles também precisam ser adicionados à Coleta de dados do Adobe Experience Platform no Admin Console e receber as seguintes permissões para a Coleta de dados do Adobe Experience Platform:

* Todas as permissões em Direitos de propriedade:
   * Aprovar
   * Desenvolver
   * Editar propriedade
   * Gerenciar ambientes
   * Gerenciar extensões
   * Publicar
* Permissão Gerenciar propriedades em Direitos da empresa

Se esta for a primeira vez que você está adicionando um usuário, conclua as etapas a seguir para adicionar usuários à Coleta de dados do Adobe Experience Platform e ao Adobe Experience Platform. Se você tiver adicionado usuários antes, vários perfis podem ser exibidos, para garantir que você selecione o perfil correto.

>[!IMPORTANT]
>
>Somente administradores de organização podem acessar o Admin Console e adicionar os usuários.

### 1. Verifique se a coleta de dados do Adobe Experience Platform e da Adobe Experience Platform foi provisionada

1. Faça logon na organização do Experience Cloud, [Página inicial do Adobe Experience Cloud](https://experience.adobe.com).
1. No canto superior direito, clique no seletor de Experience Cloud shell para exibir um menu suspenso.

   ![alternador de shell](/help/assets/places_shell_switcher1.png)

1. Na parte inferior da lista, clique em **[!UICONTROL Admin Console]**. (Um link para a variável **[!UICONTROL Admin Console]** também pode ser encontrada na seção Quick access ).

   Se você não vir **[!UICONTROL Admin Console]** na lista, você não é um administrador. Você deve entrar em contato com o Org Admin para concluir este procedimento.

1. Na Admin Console, se você tiver acesso a várias organizações, verifique se a organização correta está selecionada na parte superior direita da página.

   Essa é a organização à qual você adicionará seus usuários. Se a organização correta não tiver sido selecionada, clique na organização e selecione a organização correta na lista suspensa.

   >[!IMPORTANT]
   >
   >Se a organização desejada não estiver na lista suspensa, significa que você não tem acesso de administrador a essa organização.

1. No Admin Console, clique na guia Produtos e verifique se as placas para **[!UICONTROL Coleta de dados do Adobe Experience Platform]** e **[!UICONTROL Adobe Experience Platform]** são exibidas.

   ![](/help/assets/places_provisioned1.png)

   Esses 2 produtos são provisionados automaticamente para todas as organizações, portanto, devem estar presentes.


### 2. Adicionar usuário a esses produtos

#### Adicionar usuário para fornecer acesso à interface do usuário do Places Service

1. Na guia Produtos , clique no botão **[!UICONTROL Adobe Experience Platform]** cartão.
2. Um usuário pode ser adicionado a qualquer perfil dentro de **[!UICONTROL Adobe Experience Platform]** para obter acesso ao Places, nenhuma permissão específica precisa ser definida.
3. Escolha um perfil (se houver mais de um) e clique nele para abri-lo.
4. Clique no azul **Adicionar usuário** , preencha o usuário com a Adobe ID e o nome e clique em Salvar para concluir a adição.

#### Adicionar usuário à coleta de dados

1. Na guia Produtos , clique no botão **[!UICONTROL Coleta de dados do Adobe Experience Platform]** cartão.
2. Por padrão, um perfil chamado **Coleta de dados padrão - Todos os acessos** terão sido criadas. Adicionar um usuário a esse perfil garantirá que ele tenha as permissões apropriadas para trabalhar com o Places Service e a Coleta de dados. Se um perfil diferente for escolhido, verifique se as permissões foram incluídas e são mencionadas acima.
3. Escolha um perfil (se houver mais de um) e clique nele para abri-lo.
4. Clique no azul **Adicionar usuário** , preencha o usuário com a Adobe ID e o nome e clique em Salvar para concluir a adição.

#### Adicione um usuário como desenvolvedor do Places Service.

Para usuários que também precisam acessar a API REST do Places Service, é necessário adicioná-los como Desenvolvedor.
1. Na guia Produtos , clique no botão **[!UICONTROL Adobe Experience Platform]** cartão.
2. Se o usuário já tiver sido adicionado a **[!UICONTROL Adobe Experience Platform]** por meio das instruções acima, escolha o mesmo perfil usado anteriormente e clique nele.
3. No perfil, clique em **Desenvolvedores** guia
4. Clique no azul **Adicionar desenvolvedor** , preencha o usuário com a Adobe ID e o nome e clique em Salvar para concluir a adição.

Após a conclusão das etapas acima, o usuário receberá um email informando que tem acesso a **[!UICONTROL Adobe Experience Platform]** e **[!UICONTROL Coleta de dados do Adobe Experience Platform]**. Eles podem fazer logon no [Adobe Experience Cloud](https://experience.adobe.com) para essa organização e acesse o Places Service e a Coleta de dados. Se você também concluir as etapas **[!UICONTROL Adicionar um desenvolvedor]**, o usuário também pode fazer logon no [Console do Adobe Developer](https://developer.adobe.com/console/home) para criar um Projeto que forneceria acesso à API REST do Places Service.
