---
title: Mensagens por push
seo-title: Mensagens por push
description: Esta seção mostra como usar Locais com mensagens de push.
seo-description: Esta seção mostra como usar Locais com mensagens de push.
translation-type: tm+mt
source-git-commit: accfa6ba009ad3419481d9bd3b498143228099fc

---


# Notificações por push (#place-push-messaging)

Notificação por push: O AMS permite enviar notificações por push para segmentos do Adobe Analytics. O Serviço de localização permite que você segmente o público-alvo da mensagem de push por meio de suas interações históricas com seus POIs. Por exemplo, você pode enviar uma mensagem para usuários que estiveram em uma de suas lojas nos últimos 30 dias.

Antes de começar, verifique se você concluiu as seguintes tarefas:

* Os dados do Serviço de localização foram processados pelo Adobe Analytics.

   Isso significa que seu aplicativo móvel enviou com êxito os dados do Serviço de localização para um Conjunto de relatórios e os dados estão disponíveis para segmentação.

* O canal de notificação por push no Mobile Services está configurado.

   Para obter mais informações, consulte [Criar uma mensagem por push](https://docs.adobe.com/content/help/en/mobile-services/using/manage-app-settings-ug/configuring-app/prerequisites-push-messaging.html).

* Familiarize-se com como enviar uma notificação por push para um segmento do Analytics no Mobile Services.

   * Para obter mais informações, consulte [Criar uma mensagem por push](https://docs.adobe.com/content/help/en/mobile-services/using/messaging-ug/push-messages/t-create-push-message.html).

## Envio de uma notificação

Na **[!UICONTROL Audience]** guia *Criar fluxo de trabalho de notificação* por push, é possível criar o público-alvo para essa mensagem de uma das seguintes maneiras:

* Selecione um segmento do Adobe Analytics criado anteriormente.

* Crie um público-alvo usando os parâmetros de segmento personalizados disponíveis.

![configurar uma mensagem de push](/help/assets/push-set-up.png)

