---
title: Gerenciar bibliotecas na interface do usuário do Places
description: Gerencie suas bibliotecas usando a interface do usuário do Places.
translation-type: tm+mt
source-git-commit: 5a0705f02c8ecd540506b628371aec45107df7b2

---


# Manage libraries {#manage-libraries-places-ui}

Uma biblioteca é uma coleção de POIs. Você pode ter até 150.000 POIs em uma biblioteca e pode haver até 100 bibliotecas por organização da Experience Cloud.

Existem várias maneiras de organizar seus POIs em bibliotecas, dependendo do que for mais útil para sua organização. Alguns clientes podem preferir criar uma biblioteca separada para cada aplicativo móvel, enquanto outros podem usar bibliotecas para agrupar tipos específicos de POIs, como cafeterias, parques, hotéis e assim por diante. Por exemplo, uma grande empresa de entretenimento pode ter uma biblioteca que inclui seus locais externos em uma biblioteca e suas lojas de varejo em outra biblioteca. A prefeitura pode ter uma biblioteca que compreende todos os prédios da cidade e outra que compõe todos os parques da cidade.

As bibliotecas são definidas pelo seguinte:

| Teclas: | Descrição: |
| :--- | :--- |
| ID | um identificador exclusivo atribuído à biblioteca na criação |
| Nome | um nome amigável dado a uma biblioteca |
| Classificação | Essas classificações podem ser ignoradas se não houver geofences sobrepostas em sua organização. Se houver POIs sobrepostos, recomendamos colocar cada uma das geofences em bibliotecas separadas, para que possam ser calculadas uma em relação à outra. Um usuário pode estar somente em uma geofence de cada vez. <br><br>A classificação mais alta das geofences em que um usuário está determina sua atual associação à geofence. Se houver geofences com a mesma classificação de biblioteca, a menor geofence será a geofence atual do usuário. <br><br>O SDK também tem conhecimento dos *Últimos POIs de entrada* e dos *Últimos POIs de saída*, portanto, você tem controle total sobre como deseja que as regras sejam acionadas com base na interação do usuário com os POIs. |

## Criar uma biblioteca

1. Faça logon em locais com sua Adobe ID.
1. No lado superior direito, clique em **[!UICONTROL ...]**>**[!UICONTROL Manage Libraries]**.
1. Clique em **[!UICONTROL New]**.
1. Digite o nome.
1. Clique em **[!UICONTROL Confirm]**.

## Alterar a classificação de uma biblioteca na interface do usuário do Places

1. Faça logon em Locais com sua Adobe ID.
1. No lado superior direito, clique em **[!UICONTROL ...]**>**[!UICONTROL Manage Libraries]**.
1. Clique no ícone à esquerda do nome da biblioteca e arraste a biblioteca para a nova classificação.

## Renomear uma biblioteca

1. Faça logon em Locais com sua Adobe ID.
1. No lado superior direito, clique em **[!UICONTROL ...]**>**[!UICONTROL Manage Libraries]**.
1. Localize a biblioteca que deseja excluir.
1. Clique **[!UICONTROL ...]**e selecione**[!UICONTROL Rename]**.
1. Atualize o nome e clique em **[!UICONTROL Save]**.

## Excluir uma biblioteca

1. Faça logon em Locais com sua Adobe ID.
1. No lado superior direito, clique em **[!UICONTROL ...]**>**[!UICONTROL Manage Libraries]**.
1. Localize a biblioteca que deseja excluir.
1. Clique **[!UICONTROL ...]**e selecione**[!UICONTROL Delete]**.

