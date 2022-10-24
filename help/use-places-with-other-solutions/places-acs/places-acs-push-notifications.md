---
title: Notificações por push com o Places Service
description: Esta seção fornece informações sobre como usar o Places Service com notificações por push no Campaign Standard.
exl-id: 4b50f552-deb8-49cd-9221-fbbf33aaa5f9
source-git-commit: 010de286c25c1eeb989fb76e3c2adaa82ac9fd35
workflow-type: tm+mt
source-wordcount: '1005'
ht-degree: 4%

---

# Notificações por push com o Places Service {#push-notifications}

Nesta seção, você aprenderá a usar informações históricas de localização geográfica para segmentar notificações por push enviadas pelo Adobe Campaign Standard.

## Pré-requisitos

Antes de começar, conclua as seguintes tarefas:

* Ter um aplicativo móvel configurado com o SDK do Adobe Experience Platform Mobile, incluindo o [Extensão do Adobe Campaign Standard](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-campaign-standard).

* Integre o [Adobe Experience Platform Mobile SDK](https://aep-sdks.gitbook.io/docs/getting-started/get-the-sdk) no seu aplicativo.
* Adicione o [Extensão do Adobe Campaign Standard](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-campaign-standard) à configuração do aplicativo móvel.

* [Criar um POI](/help/poi-mgmt-ui/create-a-poi-ui.md) na interface de gerenciamento de POI do Places Service.

* Ative e instale o [Extensão do Places](/help/places-ext-aep-sdks/places-extension/places-extension.md).


## Criar elementos de dados no Experience Platform Launch

Depois de verificar se a extensão do Places e uma solução de monitoramento de região ([Documentação do CoreLocation](https://developer.apple.com/documentation/corelocation/monitoring_the_user_s_proximity_to_geographic_regions) para iOS ou [Documentação de localização do Android](https://developer.android.com/training/location/geofencing)) estiverem funcionando corretamente em seu aplicativo, será necessário criar elementos de dados no Experience Platform Launch. Os elementos de dados permitem ler as informações fornecidas pelas extensões que vêm por meio do hub de eventos do SDK móvel e agem como um alias para recuperar dados do aplicativo cliente. Para recuperar dados das extensões do Places e enviar as informações do Places Service para o Campaign, é necessário criar alguns elementos de dados.

Para criar um elemento de dados:

1. Na propriedade móvel do Experience Platform Launch, clique no botão **[!UICONTROL Elementos de dados]** e clique em **[!UICONTROL Adicionar elemento de dados]**.
1. No **[!UICONTROL Extensão]** , selecione **[!UICONTROL Serviço Places]**.
1. No **[!UICONTROL Tipo de elemento de dados]** , selecione **[!UICONTROL Nome]**.
1. No painel do lado direito, você pode selecionar **[!UICONTROL POI atual]** que recupera o nome do POI no qual o usuário está localizado no momento.

   **[!UICONTROL Última entrada]** recupera o nome do POI digitado pela última vez pelo usuário e **[!UICONTROL Última Saída]** fornece o nome do POI que o usuário deixou pela última vez. Neste exemplo, selecionamos **[!UICONTROL Última entrada]** e digitou um nome para o elemento de dados, como **[!UICONTROL Nome do último POI inserido]** e clicado **[!UICONTROL Salvar]**.

   ![&quot;Mensagens por push no Campaign Standard&quot;](/help/assets/ACS_Push1.png)

1. Repita as etapas 1 a 4 acima e crie elementos de dados para *Latitude do último POI de entrada*, *Longitude do último POI de entrada* e *Raio do último POI inserido*.

Além dos elementos de dados do Places Service, certifique-se de criar elementos de dados do Mobile Core para o *ID do aplicativo* e *Experience Cloud ID*.

## Criar uma regra para enviar dados de localização para o Adobe Campaign Standard

As regras no Experience Platform Launch permitem criar fluxos de trabalho complexos e de várias soluções com base em acionadores de eventos. Com regras, você pode criar novas regras ou modificar as existentes e implantar as atualizações dinamicamente em seus aplicativos móveis. No exemplo a seguir, a regra será acionada quando um usuário digitar um POI cercado geograficamente. Depois que a regra é acionada, uma atualização é enviada ao Campaign Standard para registrar uma entrada em um POI específico para um usuário específico com base na ID do Experience Cloud.

1. Na propriedade móvel do Experience Platform Launch, no **[!UICONTROL Regras]** clique em **[!UICONTROL Adicionar regra]**.
1. Em **[!UICONTROL Eventos]** seção , clique em **[!UICONTROL +]** e selecione **[!UICONTROL Serviço Places]** como a extensão.
1. Para o **[!UICONTROL Tipo de evento]**, selecione **[!UICONTROL Inserir POI]**.
1. Nomeie a regra, por exemplo, **POI inserido pelo usuário**.
1. Clique em **[!UICONTROL Manter alterações]**.
1. Deixe o **[!UICONTROL Condições]** em branco.

   Esta seção permite que você filtre ou coloque restrições sobre quando essa regra deve ser acionada.

1. Em **[!UICONTROL Ações]** seção , clique em **[!UICONTROL +]**.
1. No **[!UICONTROL Extensão]** , selecione **[!UICONTROL Mobile Core]** e na **[!UICONTROL Tipo de ação]** , selecione **[!UICONTROL Enviar postback]**.
1. Em **[!UICONTROL URL]**, é necessário construir o terminal de localizações de Campaign Standard.

   O URL deve ser semelhante a `https:///rest/head/mobileAppV5//locations/`.
Certifique-se de usar os elementos de dados corretos criados anteriormente para o servidor do Campaign e a pKey.

1. Clique na caixa para adicionar um corpo da publicação e envie o seguinte:

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

1. Certifique-se de usar elementos de dados criados na seção anterior.
1. Em **[!UICONTROL Tipo de conteúdo]**, digite **[!UICONTROL aplicativo/json]**.
1. Clique em **[!UICONTROL Manter alterações]**.

>[!IMPORTANT]
>
>* Pode ser útil ter um gancho da Web do Slack configurado como uma ação adicional para validar se as entradas estão sendo acionadas e se os dados corretos estão sendo coletados.
>* Lembre-se de publicar as alterações recentes no aplicativo para garantir que a regra e todos os seus elementos de dados sejam implantados como parte da configuração. Depois de publicar, inicie o aplicativo móvel novamente para obter as atualizações de configuração mais recentes.


## Use os dados de localização para direcionar mensagens da campanha

Agora que temos dados de localização preenchidos no Campaign, podemos usar POIs como uma ferramenta de segmento de público-alvo.

1. Na instância do Adobe Campaign Standard, clique em **[!UICONTROL Criar notificação por push]**.
1. Para o tipo de notificação por push, selecione **[!UICONTROL Enviar push para perfis do Campaign]**.
1. Clique em **[!UICONTROL Próximo]** e digite os detalhes gerais.
1. Na tela Público-alvo , clique em **[!UICONTROL Contagem]** para determinar quantos usuários estimados a notificação por push será enviada.

   >[!TIP]
   >
   >Neste exemplo, a contagem será 3, porque há três dispositivos instalados nos quais o aplicativo está sendo testado.

1. No painel esquerdo, expanda o **[!UICONTROL Perfil]** e arraste a **[!UICONTROL Localização do POI]** filtrar para a área principal.
1. Na janela do filtro POI, digite o nome exato do POI que deseja direcionar.

   >[!TIP]
   >
   >Você pode fazer seleções adicionais para determinar o período de tempo desde a visita anterior do usuário a esse POI.

   ![&quot;Mensagens por push 2 em ACS&quot;](/help/assets/ACS_push2.png)

1. Clique em **[!UICONTROL Confirm]**.
1. Execute a contagem novamente no topo para ver a alteração no tamanho do público-alvo.

   Se você não vir sua atualização de contagem, talvez tenha inserido um nome de POI para o qual nenhum dispositivo acionou uma entrada. Ter o gancho da web Slack torna-se valioso nessa situação, porque você pode ver uma lista de entradas de POI de vários dispositivos de teste.

1. Você pode arrastar filtros de localização de POI adicionais para incluir vários POIs em sua mensagem.
1. Clique em **[!UICONTROL Avançar]** para concluir a criação da notificação por push para entrega.

   ![&quot;Mensagens por push 3 em ACS&quot;](/help/assets/ACS_push3.png)

Usar o Places Service com o Adobe Campaign Standard oferece uma ferramenta poderosa para segmentar e direcionar suas mensagens para usuários com base em entradas e saídas de cerca geográfica. Essa integração ajuda a criar casos de uso mais personalizados e contextuais.
