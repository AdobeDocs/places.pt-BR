---
title: Notificações por push
seo-title: Notificações por push
description: Esta seção fornece informações sobre como usar Locais com notificações por push no Campaign Standard.
seo-description: 'Esta seção fornece informações sobre como usar Locais com notificações por push no Campaign Standard. '
translation-type: tm+mt
source-git-commit: a76e91775efd92ce56f2dc5cbdcc65786855b5c3

---


# Notificações por push com o Serviço de localização da plataforma de experiência {#push-notifications}

Neste guia, mostraremos como você pode usar informações históricas de localização geográfica para direcionar notificações por push fornecidas pelo Adobe Campaign Standard.

## Pré-requisitos

Antes de começar, conclua as seguintes tarefas:

* Tenha um aplicativo móvel configurado com o SDK do Adobe Experience Platform Mobile, incluindo a extensão [do](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-campaign-standard)Adobe Campaign Standard.

* Integre o SDK [do](https://aep-sdks.gitbook.io/docs/getting-started/get-the-sdk) Adobe Experience Platform Mobile ao seu aplicativo.
* Adicione o [Adobe Campaign Standard Extension](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-campaign-standard) à configuração do aplicativo móvel.

* [Crie um POI](/help/poi-mgmt-ui/create-a-poi-ui.md) na interface de gerenciamento POI do Places.

* Ative e instale a extensão [](/help/places-ext-aep-sdks/places-extension/places-extension.md)Locais.


## Criar elementos de dados no Experience Platform Launch

Depois de verificar se as extensões do Monitor de locais e locais para serviços de localização estão funcionando corretamente no aplicativo, crie elementos de dados no Experience Platform Launch. Os elementos de dados permitem ler as informações fornecidas pelas extensões que vêm pelo hub de eventos do SDK móvel e agem como um alias para recuperar dados do aplicativo cliente. Para recuperar dados das extensões do Local e enviar as informações do Local para o Campaign, é necessário criar alguns elementos de dados.

Para criar um elemento de dados:

1. Na propriedade móvel do Experience Platform Launch, clique na **[!UICONTROL Data Elements]** guia e em **[!UICONTROLAAdicionar elemento]** de dados.
2. Na lista **[!UICONTROL Extension]** suspensa, selecione **[!UICONTROL Places]**.
3. Na lista **[!UICONTROL Data Element Type]** suspensa, selecione **[!UICONTROL Name]**.
4. No painel direito, você pode selecionar qual recupera o nome do POI no qual o usuário está localizado no momento. **[!UICONTROL Current POI]**

   **[!UICONTROL Last Entered]** recupera o nome do POI que o usuário inseriu pela última vez e **[!UICONTROL Last Exited]** fornece o nome do POI que o usuário deixou pela última vez. Neste exemplo, selecionaremos **[!UICONTROL Last Entered]** e digitaremos um nome para o elemento de dados, como **[!UICONTROL Last Entered POI Name]** e clicamos **[!UICONTROL Save]**.

   !["Mensagens de push no Campaign Standard"](/help/assets/ACS_Push1.png)

5. Repita as etapas 1 a 4 acima e crie elementos de dados para Latitude *com POI* inserido pela última vez, Longitude *de POI inserido pela*&#x200B;última vez e Raio ** de POI inserido pela última vez.

Além dos elementos de dados do Serviço de localização, certifique-se de criar elementos de dados do Mobile Core para a ID *do* aplicativo e a *Experience Cloud ID*.

## Criar uma regra para enviar dados de localização para o Adobe Campaign Standard

As regras no Experience Platform Launch permitem criar fluxos de trabalho complexos e de várias soluções com base em acionadores de eventos. Com regras, você pode criar novas regras ou modificar as existentes e ter as atualizações implantadas dinamicamente em seus aplicativos móveis. No exemplo a seguir, a regra será acionada quando um usuário inserir um POI delimitado geograficamente. Depois que a regra é acionada, uma atualização é enviada ao Campaign Standard para gravar uma entrada em um POI específico para um usuário específico com base na Experience Cloud ID.

1. Na propriedade Launch mobile, na **[!UICONTROL Rules]** guia, clique em **[!UICONTROL Add Rule]**.
2. Na **[!UICONTROL Events]** seção, clique **[!UICONTROL +]** e selecione **[!UICONTROL Places]** como a extensão.
3. For the **[!UICONTROL Event Type]**, select **[!UICONTROL Enter POI]**.
4. Nomeie a regra, por exemplo, POI inserido pelo **usuário**.
5. Clique em **[!UICONTROL Keep Changes]**.
6. Deixe a **[!UICONTROL Conditions]** seção em branco.

   Esta seção permite que você filtre ou coloque restrições sobre quando esta regra deve ser acionada.

7. Na **[!UICONTROL Actions]** seção, clique em **[!UICONTROL +]**.
8. Na lista **[!UICONTROL Extension]** suspensa, selecione **[!UICONTROL Mobile Core]** e, na lista **[!UICONTROL Action Type]** suspensa, selecione **[!UICONTROL Send Postback]**.
9. Em **[!UICONTROL URL]**, é necessário construir o terminal de locais do Campaign Standard.

   O URL deve ser semelhante ao `https:///rest/head/mobileAppV5//locations/`.
Certifique-se de usar os elementos de dados corretos que você criou anteriormente para o servidor do Campaign e a pKey.

10. Clique na caixa para adicionar um corpo de publicação e enviar o seguinte:

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

11. Certifique-se de usar os elementos de dados criados na seção anterior.
12. Em **[!UICONTROL Content Type]**, digite **[!UICONTROL application/json]**.
13. Clique em **[!UICONTROL Keep Changes]**.

>[!IMPORTANT]
>
>* Pode ser útil ter uma configuração de gancho da Web em falta como uma ação adicional para validar se as entradas estão sendo acionadas e se os dados corretos estão sendo coletados.


>* Lembre-se de publicar as alterações recentes no aplicativo para garantir que a regra e todos os seus elementos de dados sejam implantados como parte da configuração. Após a publicação, você deve iniciar o aplicativo móvel novamente para obter as atualizações de configuração mais recentes.


## Usar dados de localização para direcionar mensagens da campanha

Agora que temos dados de localização preenchidos no Campaign, podemos usar POIs como uma ferramenta de segmento de público-alvo.

1. Na instância do Adobe Campaign Standard, clique em **[!UICONTROL Create Push Notification]**.
2. Para o tipo de notificação por push, selecione **[!UICONTROL Send push to Campaign profiles]**.
3. Clique **[!UICONTROL Next]** e digite os detalhes gerais.
4. Na tela Público-alvo, clique **[!UICONTROL Count]** para determinar quantos usuários estimados a notificação por push será enviada.

   >[!TIP]
   >
   >Nesse exemplo, a contagem será 3, pois há três dispositivos instalados nos quais o aplicativo está sendo testado.

5. No painel esquerdo, expanda a **[!UICONTROL Profile]** guia e arraste o **[!UICONTROL POI location]** filtro até a área principal.
6. Na janela do filtro POI, digite o nome exato do POI que você deseja direcionar.

   >[!TIP]
   >
   >Você pode fazer seleções adicionais para determinar o período de tempo desde a visita anterior do usuário a esse POI.

   !["Mensagens de push 2 em ACS"](/help/assets/ACS_push2.png)

7. Clique em **[!UICONTROL Confirm]**.
8. Execute a contagem novamente na parte superior para ver o tamanho do seu público-alvo mudar.

   Se você não vir a atualização da contagem, talvez tenha inserido um nome POI para o qual nenhum dispositivo disparou uma entrada. Ter o gancho da Web Slow torna-se valioso nesta situação, porque você pode ver uma lista de entradas de POI de vários dispositivos de teste.
9. Você pode arrastar outros filtros de localização de POI para incluir vários POIs na sua mensagem.
10. Clique **[!UICONTROL Next]** para concluir a criação da notificação por push para entrega.

   !["Mensagens de push 3 em ACS"](/help/assets/ACS_push3.html)

Usar o Serviço de localização com o Adobe Campaign Standard oferece uma ferramenta poderosa para segmentar e direcionar suas mensagens para usuários com base em entradas e saídas de fronteira geográfica. Essa integração ajuda a criar casos de uso mais personalizados e contextuais.