---
title: Notificações por push
description: Esta seção mostra como usar o Places Service com notificações por push.
exl-id: c094fe9c-6148-45ba-850a-f4c520d3362c
source-git-commit: d5c216aebd99ffef01c37c17c62576835b52438b
workflow-type: tm+mt
source-wordcount: '216'
ht-degree: 10%

---

# Notificações por push

O Mobile Services permite enviar notificações por push para segmentos do Adobe Analytics. No Places Service, você pode segmentar o público da mensagem de push usando as interações históricas com os POIs. Por exemplo, você pode enviar uma mensagem aos usuários que estiveram em uma de suas lojas nos últimos 30 dias.

Antes de começar, verifique se você concluiu as seguintes tarefas:

* Os dados do Serviço de Places foram processados pela Adobe Analytics.

  Isso significa que seu aplicativo móvel enviou com êxito dados do Places Service em um conjunto de relatórios e que os dados estão disponíveis para segmentação.

* O canal de notificação por push no Mobile Services está configurado.

  Para obter mais informações, consulte [Criar uma mensagem por push](https://experienceleague.adobe.com/docs/discontinued/using/mobile-services.htmlhtml?lang=pt-BR).

* Entenda como enviar uma notificação por push para um segmento do Analytics no Mobile Services.

  Para obter mais informações, consulte [Criar uma mensagem por push](https://experienceleague.adobe.com/docs/discontinued/using/mobile-services.htmlhtml?lang=pt-BR).

## Enviar uma notificação

Na guia **[!UICONTROL Público-alvo]** do fluxo de trabalho *Criar notificação por push*, você pode criar o público-alvo para esta mensagem de uma das seguintes maneiras:

* Na lista suspensa **[!UICONTROL Segmentos do Analytics]**, selecione um segmento do Adobe Analytics criado anteriormente.

* Na seção **[!UICONTROL Segmento personalizado]**, crie um público-alvo usando os parâmetros de segmento personalizado disponíveis.

![configurando uma mensagem de push](/help/assets/push-set-up.png)
