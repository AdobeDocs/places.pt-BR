---
title: Notificações por push
description: Esta seção mostra como usar o Serviço de Locais com notificações por push.
translation-type: tm+mt
source-git-commit: 0ca2162f113fba6bfbd54443109068b1a506762b

---


# Notificações por push

O Mobile Services permite enviar notificações por push para segmentos do Adobe Analytics. No Places Service, você pode segmentar o público-alvo da sua mensagem de push usando suas interações históricas com seus POIs. Por exemplo, você pode enviar uma mensagem para usuários que estiveram em uma de suas lojas nos últimos 30 dias.

Antes de começar, verifique se você concluiu as seguintes tarefas:

* Os dados do Serviço de Locais foram processados pelo Adobe Analytics.

   Isso significa que seu aplicativo móvel enviou com êxito os dados do Serviço do Local para um Conjunto de relatórios e que os dados estão disponíveis para segmentação.

* O canal de notificação por push no Mobile Services está configurado.

   Para obter mais informações, consulte [Criar uma mensagem por push](https://docs.adobe.com/content/help/en/mobile-services/using/manage-app-settings-ug/configuring-app/prerequisites-push-messaging.html).

* Saiba como enviar uma notificação por push para um segmento do Analytics no Mobile Services.

   Para obter mais informações, consulte [Criar uma mensagem por push](https://docs.adobe.com/content/help/en/mobile-services/using/messaging-ug/push-messages/t-create-push-message.html).

## Enviar uma notificação

Na **[!UICONTROL Audience]**guia *Criar fluxo de trabalho de notificação*por push, é possível criar o público-alvo para essa mensagem de uma das seguintes maneiras:

* Na lista **[!UICONTROL Analytics Segments]**suspensa, selecione um segmento criado anteriormente pelo Adobe Analytics.

* Na **[!UICONTROL Custom Segment]**seção, crie um público-alvo usando os parâmetros de segmento personalizados disponíveis.

![configurar uma mensagem de push](/help/assets/push-set-up.png)
