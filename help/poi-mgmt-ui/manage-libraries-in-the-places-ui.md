---
title: Gerenciar bibliotecas na interface do usuário do Places Service
description: Gerencie suas bibliotecas usando a interface do usuário do Places Service.
exl-id: 2fb999b4-854a-430f-bb89-4c786d1a89cc
source-git-commit: 4ab15ded930b31e4e06920af31f37fdfe45df8eb
workflow-type: tm+mt
source-wordcount: '432'
ht-degree: 22%

---

# Gerenciar bibliotecas {#manage-libraries-places-ui}

Uma biblioteca é uma coleção de POIs. Você pode ter até 150.000 POIs em uma biblioteca e pode haver até 100 bibliotecas por organização Experience Cloud.

Há várias maneiras de organizar seus POIs em bibliotecas, dependendo do que é mais útil para sua organização. Alguns clientes podem preferir criar uma biblioteca separada para cada aplicativo móvel, enquanto outros podem usar bibliotecas para agrupar tipos específicos de POIs, como cafeterias, parques, hotéis e assim por diante. Por exemplo, uma grande empresa de entretenimento pode ter uma biblioteca que compreende seus locais ao ar livre em uma biblioteca e suas lojas de varejo em outra biblioteca. Uma prefeitura pode ter uma biblioteca que compreende todos os edifícios na cidade e outra biblioteca que compreende todos os parques na cidade.

As bibliotecas são definidas do seguinte modo:

| Chaves: | Descrição: |
| :--- | :--- |
| ID | um identificador exclusivo atribuído à biblioteca na criação |
| Nome | um nome amigável dado a uma biblioteca |
| Classificação | Essas classificações podem ser ignoradas se não houver geofences sobrepostas na organização. Se houver POIs sobrepostos, recomendamos colocar cada uma das geofences em bibliotecas separadas, para que possam ser calculadas uma em relação à outra. Um usuário pode estar somente em uma geofence de cada vez. <br><br>A classificação mais alta das geofences em que um usuário está determina sua atual associação à geofence. Se houver geofences com a mesma classificação de biblioteca, a menor geofence será a geofence atual do usuário. <br><br>O SDK também tem conhecimento dos *Últimos POIs de entrada* e dos *Últimos POIs de saída*, portanto, você tem controle total sobre como deseja que as regras sejam acionadas com base na interação do usuário com os POIs. |

## Criar uma biblioteca

1. Faça logon no Places com a Adobe ID.
1. No lado superior direito, clique em **[!UICONTROL ..]**  > **[!UICONTROL Gerenciar bibliotecas]**.
1. Clique em **[!UICONTROL Novo]**.
1. Digite o nome.
1. Clique em **[!UICONTROL Confirmar]**.

## Alterar a classificação de uma biblioteca na interface do usuário do Places

1. Faça logon no Places com a sua Adobe ID.
1. No lado superior direito, clique em **[!UICONTROL ..]**  > **[!UICONTROL Gerenciar bibliotecas]**.
1. Clique no ícone à esquerda do nome da biblioteca e arraste a biblioteca para a nova classificação.

## Renomear uma biblioteca

1. Faça logon no Places com a sua Adobe ID.
1. No lado superior direito, clique em **[!UICONTROL ..]** > **[!UICONTROL Gerenciar bibliotecas]**.
1. Localize a biblioteca que deseja excluir.
1. Clique em **[!UICONTROL ..]** e selecione **[!UICONTROL Renomear]**.
1. Atualize o nome e clique em **[!UICONTROL Salvar]**.

## Excluir uma biblioteca

1. Faça logon no Places com a sua Adobe ID.
1. No lado superior direito, clique em **[!UICONTROL ..]** > **[!UICONTROL Gerenciar bibliotecas]**.
1. Localize a biblioteca que deseja excluir.
1. Clique em **[!UICONTROL ..]** e selecione **[!UICONTROL Excluir]**.
