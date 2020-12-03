---
title: Notificações por push com o Serviço de locais
description: Esta seção fornece informações sobre como usar o Serviço de Locais com notificações por push no Campaign Standard.
translation-type: tm+mt
source-git-commit: fd469358845e14c47a58b40bb18c9144828a8996
workflow-type: tm+mt
source-wordcount: '911'
ht-degree: 2%

---


# Notificações por push com serviços de locais {#push-notifications}

Nesta seção, você aprenderá a usar informações históricas de localização geográfica para público alvo de notificações por push enviadas pelo Adobe Campaign Standard.

## Pré-requisitos

Antes de começar, conclua as seguintes tarefas:

* Tenha um aplicativo móvel configurado com o SDK do Adobe Experience Platform Mobile, incluindo a extensão [do](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-campaign-standard)Adobe Campaign Standard.

* Integre o SDK [do](https://aep-sdks.gitbook.io/docs/getting-started/get-the-sdk) Adobe Experience Platform Mobile ao seu aplicativo.
* Adicione o [Adobe Campaign Standard Extension](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-campaign-standard) à configuração do aplicativo móvel.

* [Crie um POI](/help/poi-mgmt-ui/create-a-poi-ui.md) na interface de gerenciamento de POI do Places Service.

* Ative e instale a extensão [](/help/places-ext-aep-sdks/places-extension/places-extension.md)Locais.


## Criar elementos de dados no Experience Platform Launch

Depois de verificar se a extensão do Places e a extensão do Places Monitor estão funcionando corretamente no aplicativo, é necessário criar elementos de dados no Experience Platform Launch. Os elementos de dados permitem que você leia as informações fornecidas pelas extensões que vêm pelo hub de eventos do SDK móvel e atue como um alias para recuperar dados do aplicativo cliente. Para recuperar dados das extensões do Local e enviar as informações do Serviço Local para a Campanha, é necessário criar alguns elementos de dados.

Para criar um elemento de dados:

1. Na propriedade móvel Experience Platform Launch, clique na **[!UICONTROL Data Elements]** guia e clique em **[!UICONTROL Add Data Element]**.
1. Na lista **[!UICONTROL Extension]** suspensa, selecione **[!UICONTROL Places Service]**.
1. Na lista **[!UICONTROL Data Element Type]** suspensa, selecione **[!UICONTROL Name]**.
1. No painel do lado direito, é possível selecionar qual recupera **[!UICONTROL Current POI]** o nome do POI no qual o usuário está localizado no momento.

   **[!UICONTROL Last Entered]** recupera o nome do POI que o usuário inseriu pela última vez e **[!UICONTROL Last Exited]** fornece o nome do POI que o usuário deixou pela última vez. Neste exemplo, selecionamos **[!UICONTROL Last Entered]** e digitamos um nome para o elemento de dados, como **[!UICONTROL Last Entered POI Name]** e clicamos **[!UICONTROL Save]**.

   ![&quot;Mensagens de push no Campaign Standard&quot;](/help/assets/ACS_Push1.png)

1. Repeat the steps 1-4 above and create data elements for *Last Entered POI Latitude*, *Last Entered POI Longitude*, and *Last Entered POI Radius*.

Além dos elementos de dados do Serviço de locais, certifique-se de criar elementos de dados do Mobile Core para a ID *do* aplicativo e a ID *do* Experience Cloud.

## Criar uma regra para enviar dados de localização para a Adobe Campaign Standard

As regras no Experience Platform Launch permitem que você crie workflows complexos e de várias soluções com base em acionadores de eventos. Com regras, você pode criar novas regras ou modificar as existentes e ter as atualizações implantadas dinamicamente em seus aplicativos móveis. No exemplo a seguir, a regra será acionada quando um usuário inserir um POI delimitado geograficamente. Depois que a regra é acionada, uma atualização é enviada ao Campaign Standard para gravar uma entrada em um POI específico para um usuário específico com base na ID do Experience Cloud.

1. Na propriedade móvel Experience Platform Launch, na **[!UICONTROL Rules]** guia, clique em **[!UICONTROL Add Rule]**.
1. Na **[!UICONTROL Events]** seção, clique **[!UICONTROL +]** e selecione **[!UICONTROL Places Service]** como a extensão.
1. Para o **[!UICONTROL Event Type]**, selecione **[!UICONTROL Enter POI]**.
1. Nomeie a regra, por exemplo, POI inserido pelo **usuário**.
1. Clique em **[!UICONTROL Keep Changes]**.
1. Deixe a **[!UICONTROL Conditions]** seção em branco.

   Esta seção permite que você filtre ou coloque restrições sobre quando esta regra deve ser acionada.

1. Under the **[!UICONTROL Actions]** section, click **[!UICONTROL +]**.
1. Na lista **[!UICONTROL Extension]** suspensa, selecione **[!UICONTROL Mobile Core]** e, na lista **[!UICONTROL Action Type]** suspensa, selecione **[!UICONTROL Send Postback]**.
1. Em **[!UICONTROL URL]**, é necessário construir o terminal de localização de Campaign Standard.

   O URL deve ser semelhante ao `https:///rest/head/mobileAppV5//locations/`.
Certifique-se de usar os elementos de dados corretos que você criou anteriormente para o servidor de Campanha e a pKey.

1. Clique na caixa para adicionar um corpo de publicação e enviar o seguinte:

   ```
   {
    "locationData": {
    "distances": "{%%Last Entered POI Radius%%}",
    "poiLabel": "{%%Last Entered POI Name%%}",
    "latitude": "{%%Last Entered POI Lat%%}",
    "longitude": "{%%Last Entered POI Long%%}",
    "appId": "{%%AppID%%}",
    "marketingCloudId": “{%%ecid%%}”
    }
   }
   ```

1. Certifique-se de usar os elementos de dados criados na seção anterior.
1. Em **[!UICONTROL Content Type]**, digite **[!UICONTROL application/json]**.
1. Clique em **[!UICONTROL Keep Changes]**.

>[!IMPORTANT]
>
>* Pode ser útil configurar um gancho da Web de Slack como uma ação adicional para validar se as entradas estão sendo acionadas e se os dados corretos estão sendo coletados.
>* Lembre-se de publicar as alterações recentes no aplicativo para garantir que a regra e todos os seus elementos de dados sejam implantados como parte da configuração. Depois de publicar, inicie o aplicativo móvel novamente para obter as atualizações de configuração mais recentes.


## Usar dados de localização para mensagens de Campanha do público alvo

Agora que temos dados de localização preenchidos na Campanha, podemos usar POIs como uma ferramenta de segmento de audiência.

1. Em sua instância do Adobe Campaign Standard, clique em **[!UICONTROL Create Push Notification]**.
1. Para o tipo de notificação por push, selecione **[!UICONTROL Send push to Campaign profiles]**.
1. Clique **[!UICONTROL Next]** e digite os detalhes gerais.
1. Na tela de Audiência, clique para determinar quantos usuários estimados a notificação por push será enviada. **[!UICONTROL Count]**

   >[!TIP]
   >
   >Nesse exemplo, a contagem será 3, pois há três dispositivos instalados nos quais o aplicativo está sendo testado.

1. No painel esquerdo, expanda a **[!UICONTROL Profile]** guia e arraste o **[!UICONTROL POI location]** filtro até a área principal.
1. Na janela do filtro POI, digite o nome exato do POI que você deseja público alvo.

   >[!TIP]
   >
   >Você pode fazer seleções adicionais para determinar o período de tempo desde a visita anterior do usuário a esse POI.

   ![&quot;Mensagens de push 2 em ACS&quot;](/help/assets/ACS_push2.png)

1. Clique em **[!UICONTROL Confirm]**.
1. Execute a contagem novamente na parte superior para ver a alteração do tamanho da audiência.

   Se você não vir a atualização da sua contagem, talvez tenha inserido um nome POI para o qual nenhum dispositivo disparou uma entrada. Fazer com que o gancho da web Slack se torne valioso nessa situação, porque você pode ver uma lista de entradas de POI de vários dispositivos de teste.

1. Você pode arrastar filtros adicionais de localização de POI para incluir vários POIs em sua mensagem.
1. Click **[!UICONTROL Next]** to finish creating the push notification for delivery.

   ![&quot;Mensagens de push 3 em ACS&quot;](/help/assets/ACS_push3.png)

O uso do Places Service com a Adobe Campaign Standard oferece uma ferramenta poderosa para segmentar e público alvo suas mensagens para os usuários com base em entradas e saídas de fronteira geográfica. Essa integração ajuda a criar casos de uso mais personalizados e contextuais.