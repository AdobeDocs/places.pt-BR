---
title: Mensagens no aplicativo com o Places Service
description: Esta seção fornece informações sobre como usar mensagens de push no Campaign Standard com mensagens no aplicativo no Campaign Standard.
exl-id: c80727b8-20c9-4ca0-9f2c-20ec646bb7fa
source-git-commit: 010de286c25c1eeb989fb76e3c2adaa82ac9fd35
workflow-type: tm+mt
source-wordcount: '394'
ht-degree: 4%

---

# Mensagens no aplicativo com o Places Service {#in-app-messages-loc-service}

Essas informações ajudam você a entender como usar as informações do Places Service para enviar mensagens no aplicativo ou notificações locais.

## Pré-requisitos

Antes de começar, conclua as seguintes tarefas:

* Ter um aplicativo móvel configurado com o SDK do Adobe Experience Platform Mobile, incluindo o [Extensão do Adobe Campaign Standard](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-campaign-standard).

* Integre o [Adobe Experience Platform Mobile SDK](https://aep-sdks.gitbook.io/docs/getting-started/get-the-sdk) no seu aplicativo.
* Adicione o [Extensão do Adobe Campaign Standard](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-campaign-standard) à configuração do aplicativo móvel.

* [Criar um POI](/help/poi-mgmt-ui/create-a-poi-ui.md) na interface de gerenciamento de POI do Places Service.

* Instalar e configurar o [Extensão do Places](/help/places-ext-aep-sdks/places-extension/places-extension.md) e de uma solução de monitorização da região ([Documentação do CoreLocation](https://developer.apple.com/documentation/corelocation/monitoring_the_user_s_proximity_to_geographic_regions) para iOS ou [Documentação de localização do Android](https://developer.android.com/training/location/geofencing)) no aplicativo móvel.

## Envio de uma mensagem no aplicativo com base em uma entrada ou saída de fronteira geográfica

1. Na instância do Adobe Campaign Standard, clique em **[!UICONTROL Criar mensagem no aplicativo]**.
1. Para o tipo de mensagem, selecione **[!UICONTROL Direcionar todos os usuários de um aplicativo móvel]**.
1. Clique em **[!UICONTROL Próximo]** e digite os detalhes gerais.
1. No painel esquerdo, verifique se você pode usar vários acionadores relacionados ao Places Services.

   * Você pode optar pela exibição da mensagem no aplicativo se o usuário tiver inserido uma geolocalização de POI.
   * Você também pode usar metadados definidos na interface do usuário do Places Services para filtrar o público-alvo.

   No exemplo abaixo, você pode acionar uma mensagem no aplicativo exibida somente para usuários que entram em um dos resorts de férias que estão participando de um programa de bebidas gratuitas, e deseja enviar um cupom para esses usuários quando chegarem.

   ![&quot;Metadados do local das mensagens no aplicativo&quot;](/help/assets/last-entered-vacation.png)

1. Clique no botão **[!UICONTROL Próximo]** para concluir a criação da mensagem no aplicativo para entrega.

   ![&quot;criar um evento&quot;](/help/assets/prepare-ACS.png)

   Para testar o delivery de mensagens no aplicativo, inicie o aplicativo no Xcode ou no Android studio e use o simulador de localização para selecionar um POI que se ajuste aos critérios de mensagens.

   ![&quot;cupom de bebida&quot;](/help/assets/drink-coupon-on-app.png)

Usar o Places Services com o Adobe Campaign Standard oferece uma ferramenta poderosa para segmentar e direcionar suas mensagens para usuários com base em entradas e saídas de cerca geográfica. Essa integração permite criar casos de uso mais personalizados e contextuais.

<!--I changed this embed to a link to pass validation. We should not link to youtube videos, so please upload this to MCP-->

[Serviço de localização do Adobe Experience Platform com mensagens de campanha](https://www.youtube.com/watch?v=ikiTTQw9c-o)
