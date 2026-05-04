---
title: Notificações por push
description: Esta seção mostra como usar o Places Service com notificações por push.
exl-id: c094fe9c-6148-45ba-850a-f4c520d3362c
TQID: https://experienceleague.adobe.com/aaTMSoOkVUfbPDpPiRm7P3-8d8JSO9N0Ga12Hlmf-go
product_v2:
  - id: d0a3eab4-7b10-4d96-a71e-6c0f8e7b7c87
  - id: e55547f1-a1ff-40c6-8978-026e40ab7fa4
  - id: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
feature_v2:
  - id: e08599ea-8888-4294-ba74-3ba0a7762a46
subfeature_v2:
  - id: d2a6cbf4-df32-480f-909e-b42f66dcb9f0
topic_v2:
  - id: d3cdead0-685a-4489-9250-4bb709942f66
source-git-commit: f962cef761f006c8e7d45b76ba24746e36bdaba6
workflow-type: tm+mt
source-wordcount: 229
ht-degree: 14%

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
