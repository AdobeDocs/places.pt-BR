---
title: Obter acesso ao Places Service
description: Esta seção fornece informações sobre como adicionar um usuário ao Serviço de Places e Experience Platform Launch, para que o usuário possa acessar o Serviço de Places.
exl-id: f388945e-cf26-4694-9697-9fe564ae4b69
source-git-commit: c9058e9b70c2ef97151078f43913963471730bd2
workflow-type: tm+mt
source-wordcount: '913'
ht-degree: 1%

---

# Obter acesso ao Places Service {#adding-user-launch-places}

O Places Service agora está disponível na interface da coleção de dados. Você pode acessar a Coleção de dados no menu de acesso rápido em [Página inicial do Adobe Experience Cloud](https://experience.adobe.com).

![menu de acesso rápido](/help/assets/quickaccess.png)

Você também pode acessar a Coleção de dados no menu do Adobe Experience Platform:

![menu Experience Platform](/help/assets/solutionaccessmenu.png)

Se sua ID de usuário tiver acesso, você verá o ícone Serviço do Places no painel esquerdo, em Gerenciamento de dados na coleção de dados, conforme indicado abaixo:

![Painel esquerdo Coleção de dados](/help/assets/places_in_data_collection.png)

Se você não vir o Serviço de Places nesse local, entre em contato com um administrador em sua organização para adicionar sua ID de usuário à Adobe Experience Platform no Admin Console.

## Adicionar um usuário para acessar o Places Service e a Coleção de dados da Experience Adobe Experience Platform

O Places agora está incluído com o Adobe Experience Platform. Para permitir que os usuários acessem o [Serviço de Places](https://experience.adobe.com/#/data-collection/places), eles precisam ser adicionados ao Adobe Experience Platform no Admin Console como usuário. Para permitir que os usuários tenham acesso à Coleção de dados do Experience Platform com as permissões necessárias para configurar propriedades móveis e usar o Places com o SDK da Adobe Experience Platform, eles também precisam ser adicionados à Coleção de dados da Adobe Experience Platform no Admin Console e receber as seguintes permissões para a Coleção de dados da Adobe Experience Platform:

* Todas as permissões sob Direitos de propriedade:
   * Aprovar
   * Desenvolver
   * Editar propriedade
   * Gerenciar ambientes
   * Gerenciar extensões
   * Publicar
* Permissão Gerenciar propriedades em Direitos da empresa

Se esta for a primeira vez que você adiciona um usuário, conclua as etapas a seguir para adicionar usuários à Coleção de dados da Adobe Experience Platform e ao Adobe Experience Platform. Se você tiver adicionado usuários antes, vários perfis podem ser exibidos, portanto, selecione o perfil correto.

>[!IMPORTANT]
>
>Somente administradores de organização podem acessar o Admin Console e adicionar os usuários.

### 1. Verifique se a coleta de dados da Adobe Experience Platform e da Adobe Experience Platform está provisionada

1. Faça logon na organização da Experience Cloud, [Página inicial do Adobe Experience Cloud](https://experience.adobe.com).
1. No canto superior direito, clique no alternador de shell Experience Cloud para exibir um menu suspenso.

   ![alternador de shell](/help/assets/places_shell_switcher1.png)

1. Na parte inferior da lista, clique em **[!UICONTROL Admin Console]**. (Um link para o **[!UICONTROL Admin Console]** também podem ser encontrados na seção Acesso rápido ).

   Se você não vir **[!UICONTROL Admin Console]** na lista, você não é um administrador. Você deve entrar em contato com o Org Admin para concluir este procedimento.

1. No Admin Console, se você tiver acesso a várias organizações, verifique se a organização correta está selecionada na parte superior direita da página.

   Essa é a organização à qual você adicionará usuários. Se a organização correta não tiver sido selecionada, clique na organização e selecione-a na lista suspensa.

   >[!IMPORTANT]
   >
   >Se a organização desejada não estiver na lista suspensa, significa que você não tem acesso de administrador a essa organização.

1. No Admin Console, clique na guia Produtos e verifique se os cartões para **[!UICONTROL Coleta de dados do Adobe Experience Platform]** e **[!UICONTROL Adobe Experience Platform]** são exibidos.

   ![](/help/assets/places_provisioned1.png)

   Esses dois produtos são provisionados automaticamente para todas as organizações, portanto, devem estar presentes.


### 2. Adicionar usuário a esses produtos

#### Adicionar usuário para fornecer acesso à interface do usuário do Places Service

1. Na guia Produtos, clique na guia **[!UICONTROL Adobe Experience Platform]** cartão.
2. Um usuário pode ser adicionado a qualquer perfil no **[!UICONTROL Adobe Experience Platform]** para obter acesso ao Places, nenhuma permissão específica precisa ser definida.
3. Escolha um perfil (se houver mais de um) e clique nele para abri-lo.
4. Clique no azul **Adicionar usuário** , preencha o usuário com sua Adobe ID e nome e clique em Salvar para concluir a adição.

#### Adicionar usuário à Coleção de dados

1. Na guia Produtos, clique na guia **[!UICONTROL Coleta de dados do Adobe Experience Platform]** cartão.
2. Por padrão, um perfil chamado **Acesso a Todos os Dados da Coleção de Dados Padrão** será criado. Adicionar um usuário a este perfil garantirá que ele tenha as permissões apropriadas para trabalhar com o Serviço de Places e a Coleção de dados. Se um perfil diferente for escolhido, verifique se as permissões incluídas são mencionadas acima.
3. Escolha um perfil (se houver mais de um) e clique nele para abri-lo.
4. Clique no azul **Adicionar usuário** , preencha o usuário com sua Adobe ID e nome e clique em Salvar para concluir a adição.

#### Adicione um usuário como desenvolvedor do Places Service.

Para usuários que também precisam de acesso à API REST do Places Service, é necessário adicioná-los como um Desenvolvedor.
1. Na guia Produtos, clique na guia **[!UICONTROL Adobe Experience Platform]** cartão.
2. Se o usuário já tiver sido adicionado a **[!UICONTROL Adobe Experience Platform]** por meio das instruções acima, escolha o mesmo perfil usado anteriormente e clique nele.
3. No perfil, clique no link **Desenvolvedores** guia
4. Clique no azul **Adicionar desenvolvedor** , preencha o usuário com sua Adobe ID e nome e clique em Salvar para concluir a adição.

Após a conclusão das etapas acima, o usuário receberá um email notificando que tem acesso ao **[!UICONTROL Adobe Experience Platform]** e **[!UICONTROL Coleta de dados do Adobe Experience Platform]**. Eles podem fazer logon na [Adobe Experience Cloud](https://experience.adobe.com) para esta organização e acesse o Serviço de Places e a Coleção de dados. Se você também concluir as etapas **[!UICONTROL Adicionar um desenvolvedor]**, o usuário também poderá fazer logon na [Console do Adobe Developer](https://developer.adobe.com/console/home) para criar um Projeto que forneceria acesso à API REST do Places Service.
