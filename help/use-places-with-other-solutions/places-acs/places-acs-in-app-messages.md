---
title: Mensagens no aplicativo com o Serviço de locais
description: Esta seção fornece informações sobre como usar as mensagens de push no Campaign Standard com mensagens no aplicativo no Campaign Standard.
translation-type: tm+mt
source-git-commit: 462df20bb351795dc72009cc18d390cb45e262a8
workflow-type: tm+mt
source-wordcount: '356'
ht-degree: 3%

---


# Mensagens no aplicativo com o Serviço de locais {#in-app-messages-loc-service}

Essas informações ajudam você a entender como usar as informações do Serviço de Locais para enviar mensagens no aplicativo ou notificações locais.

## Pré-requisitos

Antes de começar, conclua as seguintes tarefas:

* Tenha um aplicativo móvel configurado com o SDK do Adobe Experience Platform Mobile, incluindo a extensão [do](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-campaign-standard)Adobe Campaign Standard.

* Integre o SDK [do](https://aep-sdks.gitbook.io/docs/getting-started/get-the-sdk) Adobe Experience Platform Mobile ao seu aplicativo.
* Adicione o [Adobe Campaign Standard Extension](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-campaign-standard) à configuração do aplicativo móvel.

* [Crie um POI](/help/poi-mgmt-ui/create-a-poi-ui.md) na interface de gerenciamento de POI do Places Service.

* Instale e configure a extensão [](/help/places-ext-aep-sdks/places-extension/places-extension.md) Places e as extensões [do monitor](/help/places-ext-aep-sdks/places-monitor-extension/places-monitor-extension.md) Places no aplicativo móvel.

## Enviar uma mensagem no aplicativo com base em uma entrada ou saída de fronteira geográfica

1. Em sua instância do Adobe Campaign Standard, clique em **[!UICONTROL Create In-App message]**.
1. Para o tipo de mensagem, selecione **[!UICONTROL Target all users of a Mobile application]**.
1. Clique **[!UICONTROL Next]** e digite os detalhes gerais.
1. No painel esquerdo, verifique se você pode usar vários acionadores relacionados aos Serviços do local.

   * Você pode optar por exibir a mensagem no aplicativo se o usuário tiver inserido uma fronteira geográfica POI.
   * Você também pode usar metadados definidos na interface do usuário do Places Services para filtrar a audiência.

   No exemplo abaixo, você pode disparar uma mensagem no aplicativo que é exibida somente para usuários que entram em um dos resorts de férias que participam de um programa de bebida grátis, e você deseja enviar a esses usuários um cupom quando chegam.

   ![&quot;Metadados de locais de mensagens no aplicativo&quot;](/help/assets/last-entered-vacation.png)

1. Click the **[!UICONTROL Next]** to finish creating the In-app message for delivery.

   ![&quot;criar um evento&quot;](/help/assets/prepare-ACS.png)

   Para testar o delivery de mensagens no aplicativo, inicie o aplicativo no estúdio Xcode ou Android e use o simulador de localização para selecionar um POI que se ajuste aos critérios de mensagens.

   ![&quot;beba cupom&quot;](/help/assets/drink-coupon-on-app.png)

O uso do Places Services com a Adobe Campaign Standard oferece uma ferramenta poderosa para segmentar e público alvo suas mensagens para os usuários com base em entradas e saídas de fronteira geográfica. Essa integração permite criar casos de uso mais personalizados e contextuais.

<!--I changed this embed to a link to pass validation. We should not link to youtube videos, so please upload this to MCP-->

[Serviço de localização da Adobe Experience Platform com mensagens de Campanha](https://www.youtube.com/watch?v=ikiTTQw9c-o)
