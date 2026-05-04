---
title: Adicionar contexto de localização às solicitações do Analytics
description: Esta seção fornece informações sobre como adicionar contexto de localização às solicitações do Analytics.
exl-id: bee7b6e3-a75b-4a07-b6e2-f93ce33aa042
TQID: https://experienceleague.adobe.com/NR-CowJgzUBMVWcbV-EvdyBDsiwLi72yxM-Vjx5oNwk
product_v2:
  - id: d0a3eab4-7b10-4d96-a71e-6c0f8e7b7c87
  - id: e55547f1-a1ff-40c6-8978-026e40ab7fa4
  - id: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
feature_v2:
  - id: b069d60e-95f3-44d6-95a8-ddc862a4bc38
  - id: e08599ea-8888-4294-ba74-3ba0a7762a46
subfeature_v2:
  - id: d2a6cbf4-df32-480f-909e-b42f66dcb9f0
topic_v2:
  - id: d3cdead0-685a-4489-9250-4bb709942f66
source-git-commit: f962cef761f006c8e7d45b76ba24746e36bdaba6
workflow-type: tm+mt
source-wordcount: 512
ht-degree: 2%

---

# Adicionar contexto de localização às solicitações do Analytics {#run-reports-aa-locserv-data}

>[!IMPORTANT]
>
>Este documento supõe que você tenha o Places Service implementado em seu aplicativo. Para obter mais informações sobre como implementar o Places Service, consulte [Extensões do Places](/help/places-ext-aep-sdks/places-extension/places-extension.md).

Depois que o Places Service envia os eventos de entrada e saída, você pode criar regras no Experience Platform Launch e anexar os dados do Places Service a todos os eventos do Adobe Analytics. Para criar esse tipo de regra, selecione a propriedade no Launch e conclua as seguintes etapas:

## &#x200B;1. Criar uma regra

1. Na guia **[!UICONTROL Regras]**, clique em **[!UICONTROL Criar nova regra]**.

   Lembre-se das seguintes informações:
   * Se você não tiver regras existentes para esta propriedade, o botão **[!UICONTROL Criar nova regra]** estará no meio da tela.
   * Se a propriedade tiver regras, o botão **[!UICONTROL Criar nova regra]** estará na parte superior direita da tela.

## 2.Selecione um evento

1. Dê um nome significativo à regra para que ela seja facilmente reconhecível na lista de Regras.

   Neste exemplo, a Regra é denominada **[!UICONTROL Anexar dados do serviço de Places aos Eventos de ação de rastreamento do Analytics]**.

1. Na seção **[!UICONTROL Eventos]**, clique em **[!UICONTROL Adicionar]**.

1. Na lista suspensa **[!UICONTROL Extensão]**, selecione **[!UICONTROL Mobile Core]**.

1. Na lista suspensa **[!UICONTROL Tipo de Evento]**, selecione **[!UICONTROL Rastrear Ação]**.

Agora você pode determinar os acionadores que deseja incluir para esta regra. Neste exemplo, o acionador se baseia em todas as chamadas `TrackAction`. Após configurar o Evento, clique em **[!UICONTROL Manter alterações]**.

![&quot;criar um evento&quot;](/help/assets/ad-setEvent_use-analytics-data.png)


## &#x200B;3. Adicionar condições

>[!IMPORTANT]
>
>Conclua este procedimento para adicionar Condições à regra. Caso contrário, pule para a seção *Definir a Ação* abaixo.

Neste exemplo, uma Condição é criada e faz com que a Regra seja acionada somente para clientes AT&amp;T.

1. Na seção **[!UICONTROL Condições]**, clique em **[!UICONTROL Adicionar]**.

1. Na lista suspensa **[!UICONTROL Extensão]**, selecione **[!UICONTROL Mobile Core]**.

1. Na lista suspensa **[!UICONTROL Tipo de Condição]**, selecione **[!UICONTROL Nome da Transportadora]**.

1. Na janela à direita, marque a caixa de seleção **[!UICONTROL AT&amp;T]**.

1. Clique em **[!UICONTROL Manter alterações]**.

![&quot;criar uma condição&quot;](/help/assets/ad-setCondition_use-analytics-data.png)

## &#x200B;4. Definir a ação

1. Na seção **[!UICONTROL Ações]**, clique em **[!UICONTROL Adicionar]**.

1. Na lista suspensa **[!UICONTROL Extensão]**, selecione **[!UICONTROL Mobile Core]**.

1. Na lista suspensa **[!UICONTROL Tipo de ação]**, selecione **[!UICONTROL Anexar dados]**.

1. No painel direito, no campo **[!UICONTROL Carga JSON]**, digite os dados que serão adicionados a este Evento.

1. Clique em **[!UICONTROL Manter alterações]**.

No painel direito, você pode adicionar uma carga JSON de forma livre que adiciona dados a um evento do SDK antes que uma extensão que esteja escutando esse evento possa ouvir o evento. Neste exemplo, alguns dados de contexto são adicionados a esse evento antes que a extensão do Analytics o processe. Os dados de contexto adicionados agora estarão na ocorrência de saída do Analytics.

No exemplo a seguir, os valores `poi.city` e `poi.name` são adicionados aos dados de contexto do evento do Analytics. Os valores das novas chaves são determinados dinamicamente pela SDK quando esse evento é processado.

![&quot;criar uma ação&quot;](/help/assets/ad-setAction_use-analytics-data.png)

## &#x200B;5. Salve a regra e recrie a propriedade

Após concluir a configuração, verifique se a regra tem a seguinte aparência:

![&quot;a regra está concluída.&quot;](/help/assets/ad-ruleComplete_use-analytics-data.png)

1. Clique em **[!UICONTROL Salvar]**

1. Recrie sua propriedade do Launch e implante-a no ambiente correto.
