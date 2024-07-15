---
title: Notificações por push com o Places Service
description: Esta seção fornece informações sobre como usar o Serviço de Places com notificações por push em Campaign Standard.
exl-id: 4b50f552-deb8-49cd-9221-fbbf33aaa5f9
source-git-commit: 010de286c25c1eeb989fb76e3c2adaa82ac9fd35
workflow-type: tm+mt
source-wordcount: '981'
ht-degree: 1%

---

# Notificações por push com o serviço de Places {#push-notifications}

Nesta seção, você aprenderá a usar informações históricas de localização geográfica para direcionar notificações por push enviadas pelo Adobe Campaign Standard.

## Pré-requisitos

Antes de começar, conclua as seguintes tarefas:

* Ter um aplicativo móvel configurado com o SDK do Adobe Experience Platform Mobile, incluindo a [extensão do Adobe Campaign Standard](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-campaign-standard).

* Integre o [Adobe Experience Platform Mobile SDK](https://aep-sdks.gitbook.io/docs/getting-started/get-the-sdk) ao seu aplicativo.
* Adicione a [Extensão do Adobe Campaign Standard](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-campaign-standard) à configuração do aplicativo móvel.

* [Crie um POI](/help/poi-mgmt-ui/create-a-poi-ui.md) na interface de gerenciamento de POIs do Places Service.

* Habilite e instale a [extensão do Places](/help/places-ext-aep-sdks/places-extension/places-extension.md).


## Criar elementos de dados no Experience Platform Launch

Depois de verificar se a extensão Places e uma solução de monitoramento de região ([Documentação do CoreLocation](https://developer.apple.com/documentation/corelocation/monitoring_the_user_s_proximity_to_geographic_regions) para iOS ou [Documentação de localização do Android](https://developer.android.com/training/location/geofencing)) estão funcionando corretamente no aplicativo, é necessário criar elementos de dados no Experience Platform Launch. Os elementos de dados permitem ler as informações fornecidas pelas extensões provenientes do hub de eventos do SDK móvel e agem como um alias para recuperar dados do aplicativo cliente. Para recuperar dados das extensões do Places e enviar as informações do Serviço do Places para o Campaign, é necessário criar alguns elementos de dados.

Para criar um elemento de dados:

1. Na propriedade do Experience Platform Launch mobile, clique na guia **[!UICONTROL Elementos de Dados]** e clique em **[!UICONTROL Adicionar Elemento de Dados]**.
1. Na lista suspensa **[!UICONTROL Extensão]**, selecione **[!UICONTROL Serviço do Places]**.
1. Na lista suspensa **[!UICONTROL Tipo de Elemento de Dados]**, selecione **[!UICONTROL Nome]**.
1. No painel do lado direito, você pode selecionar **[!UICONTROL POI atual]**, que recupera o nome do POI no qual o usuário está localizado no momento.

   **[!UICONTROL Última Entrada]** recupera o nome do POI inserido pela última vez e **[!UICONTROL Última Saída]** fornece o nome do POI deixado pelo último usuário. Neste exemplo, selecionamos **[!UICONTROL Última Entrada]** e digitamos um nome para o elemento de dados, como **[!UICONTROL Último Nome de POI Inserido]** e clicamos em **[!UICONTROL Salvar]**.

   ![&quot;Mensagens por push no Campaign Standard&quot;](/help/assets/ACS_Push1.png)

1. Repita as etapas 1 a 4 acima e crie elementos de dados para *Latitude do Último POI de Entrada*, *Longitude do Último POI de Entrada* e *Raio do Último POI de Entrada*.

Além dos elementos de dados para o Places Service, crie elementos de dados principais móveis para *App ID* e *Experience Cloud ID*.

## Criar uma regra para enviar dados de localização ao Adobe Campaign Standard

As regras no Experience Platform Launch permitem criar fluxos de trabalho complexos de várias soluções com base em acionadores de eventos. Com regras de, você pode criar novas regras ou modificar as existentes e implantar as atualizações dinamicamente nos aplicativos móveis. No exemplo a seguir, a regra será acionada quando um usuário inserir um POI com geosfera. Depois que a regra é acionada, uma atualização é enviada para o Campaign Standard para registrar uma entrada para um POI específico para um usuário específico com base na ID do Experience Cloud.

1. Na propriedade do Experience Platform Launch mobile, na guia **[!UICONTROL Regras]**, clique em **[!UICONTROL Adicionar regra]**.
1. Na seção **[!UICONTROL Eventos]**, clique em **[!UICONTROL +]** e selecione **[!UICONTROL Places Service]** como extensão.
1. Para o **[!UICONTROL Tipo de Evento]**, selecione **[!UICONTROL Inserir POI]**.
1. Nomeie a regra, por exemplo, **POI inserido pelo usuário**.
1. Clique em **[!UICONTROL Manter alterações]**.
1. Deixe a seção **[!UICONTROL Condições]** em branco.

   Esta seção permite filtrar ou colocar restrições sobre quando essa regra deve ser acionada.

1. Na seção **[!UICONTROL Ações]**, clique em **[!UICONTROL +]**.
1. Na lista suspensa **[!UICONTROL Extensão]**, selecione **[!UICONTROL Mobile Core]** e, na lista suspensa **[!UICONTROL Tipo de ação]**, selecione **[!UICONTROL Enviar postback]**.
1. Em **[!UICONTROL URL]**, você precisa construir seu ponto de extremidade de locais de Campaign Standard.

   A URL deve ser semelhante a `https:///rest/head/mobileAppV5//locations/`.
Certifique-se de usar os elementos de dados corretos criados anteriormente para o servidor e a pKey do Campaign.

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
1. Em **[!UICONTROL Tipo de conteúdo]**, digite **[!UICONTROL aplicativo/json]**.
1. Clique em **[!UICONTROL Manter alterações]**.

>[!IMPORTANT]
>
>* Pode ser útil ter um gancho da Web Slack configurado como uma ação adicional para validar se as entradas estão sendo acionadas e se os dados corretos estão sendo coletados.
>* Lembre-se de publicar as alterações recentes no aplicativo para garantir que a regra e todos os elementos de dados sejam implantados como parte da configuração. Depois de publicar, inicie o aplicativo móvel novamente para obter as atualizações de configuração mais recentes.

## Usar dados de localização para direcionar mensagens de campanha

Agora que temos dados de localização preenchidos no Campaign, podemos usar os POIs como uma ferramenta de segmento de público-alvo.

1. Na instância do Adobe Campaign Standard, clique em **[!UICONTROL Criar notificação por push]**.
1. Para o tipo de notificação por push, selecione **[!UICONTROL Enviar push para perfis de campanha]**.
1. Clique em **[!UICONTROL Avançar]** e digite os detalhes gerais.
1. Na tela Público, clique em **[!UICONTROL Contagem]** para determinar quantos usuários estimados a notificação por push será enviada.

   >[!TIP]
   >
   >Neste exemplo, a contagem será 3, pois há três dispositivos instalados nos quais o aplicativo está sendo testado.

1. No painel esquerdo, expanda a guia **[!UICONTROL Perfil]** e arraste o filtro **[!UICONTROL local do POI]** para a área principal.
1. Na janela do filtro POI, digite o nome exato do POI que deseja direcionar.

   >[!TIP]
   >
   >Você pode fazer seleções adicionais para determinar o período desde a visita anterior do usuário a esse POI.

   ![&quot;Mensagens por push 2 no ACS&quot;](/help/assets/ACS_push2.png)

1. Clique em **[!UICONTROL Confirmar]**.
1. Execute a contagem novamente na parte superior para ver o tamanho do público-alvo mudar.

   Se você não vir a atualização da contagem, pode ter inserido um nome de POI para o qual nenhum dispositivo acionou uma entrada. Ter o Slack web hook torna-se valioso nessa situação, porque você pode ver uma lista de entradas de POI de vários dispositivos de teste.

1. Você pode arrastar filtros adicionais de localização de POI para incluir vários POIs em sua mensagem.
1. Clique em **[!UICONTROL Avançar]** para concluir a criação da notificação por push para entrega.

   ![&quot;Mensagens por push 3 no ACS&quot;](/help/assets/ACS_push3.png)

Usar o Places Service com o Adobe Campaign Standard oferece uma ferramenta poderosa para segmentar e direcionar suas mensagens para os usuários com base em entradas e saídas de geolocalização. Essa integração ajuda a criar casos de uso mais personalizados e contextuais.
