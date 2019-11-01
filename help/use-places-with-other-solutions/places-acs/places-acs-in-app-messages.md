---
title: Mensagens no aplicativo com o Serviço de localização
seo-title: Mensagens no aplicativo com o Serviço de localização
description: Esta seção fornece informações sobre como usar as mensagens de push no Campaign Standard com mensagens no aplicativo no Campaign Standard.
seo-description: 'Esta seção fornece informações sobre como usar "Mensagens de push no Campaign Standard" com mensagens no aplicativo no Campaign Standard. '
translation-type: tm+mt
source-git-commit: a2e30282789d9834e5c65502e28ddb25f3c55dfa

---


# Mensagens no aplicativo com o Serviço de localização {#in-app-messages-loc-service}

Essas informações ajudam você a entender como usar as informações do Serviço de localização da plataforma Adobe Experience para enviar mensagens no aplicativo ou notificações locais.

## Pré-requisitos

Antes de começar, conclua as seguintes tarefas:

* Tenha um aplicativo móvel configurado com o SDK do Adobe Experience Platform Mobile, incluindo a extensão [do](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-campaign-standard)Adobe Campaign Standard.

* Integre o SDK [do](https://aep-sdks.gitbook.io/docs/getting-started/get-the-sdk) Adobe Experience Platform Mobile ao seu aplicativo.
* Adicione o [Adobe Campaign Standard Extension](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-campaign-standard) à configuração do aplicativo móvel.

* [Crie um POI](/help/poi-mgmt-ui/create-a-poi-ui.md) na interface de gerenciamento POI do Places.

* Instale e configure a extensão [](/help/places-ext-aep-sdks/places-extension/places-extension.md) Places e as extensões [do monitor](/help/places-ext-aep-sdks/places-monitor-extension/places-monitor-extension.md) Places no aplicativo móvel.

## Enviar uma mensagem no aplicativo com base em uma entrada ou saída de fronteira geográfica

1. Na instância do Adobe Campaign Standard, clique em **[!UICONTROL Create In-App message]**.
1. Para o tipo de mensagem, selecione **[!UICONTROL Target all users of a Mobile application]**.
1. Clique **[!UICONTROL Next]** e digite os detalhes gerais.
1. No painel esquerdo, verifique se você pode usar vários acionadores relacionados aos serviços de localização.

   * Você pode optar por exibir a mensagem no aplicativo se o usuário tiver inserido uma fronteira geográfica POI.
   * Você também pode usar metadados definidos na interface do usuário do Location Services para filtrar o público-alvo.
   No exemplo abaixo, você pode disparar uma mensagem no aplicativo que é exibida somente para usuários que entram em um dos resorts de férias que participam de um programa de bebida gratuita e deseja enviar a esses usuários um cupom quando chegam.

   !["Metadados de locais de mensagens no aplicativo"](/help/assets/last-entered-vacation.png)

1. Clique no botão **[!UICONTROL Next]** para concluir a criação da mensagem no aplicativo para entrega.

   !["criar um evento"](/help/assets/prepare-ACS.png)

   Para testar a entrega de mensagens no aplicativo, inicie o aplicativo no estúdio Xcode ou Android e use o simulador de localização para selecionar um POI que se ajuste aos critérios de mensagens.

   !["beba cupom"](/help/assets/drink-coupon-on-app.png)

Usar os serviços de localização com o Adobe Campaign Standard oferece uma ferramenta poderosa para segmentar e direcionar suas mensagens aos usuários com base em entradas e saídas de fronteira geográfica. Essa integração permite criar casos de uso mais personalizados e contextuais.

>[!VIDEO](https://www.youtube.com/watch?v=ikiTTQw9c-o)