---
title: Adicionar contexto de localização às solicitações do Analytics
description: Esta seção fornece informações sobre como adicionar contexto de localização às solicitações do Analytics.
exl-id: bee7b6e3-a75b-4a07-b6e2-f93ce33aa042
source-git-commit: 4ab15ded930b31e4e06920af31f37fdfe45df8eb
workflow-type: tm+mt
source-wordcount: '503'
ht-degree: 1%

---

# Adicionar contexto de localização às solicitações do Analytics {#run-reports-aa-locserv-data}

>[!IMPORTANT]
>
>Este documento supõe que você tenha o Places Service implementado em seu aplicativo. Para obter mais informações sobre como implementar o Places Service, consulte [Extensões do Places](/help/places-ext-aep-sdks/places-extension/places-extension.md).

Depois que o Serviço de Places enviar os eventos de entrada e saída, você poderá criar regras no Experience Platform Launch e anexar os dados do Serviço de Places a todos os eventos do Adobe Analytics. Para criar esse tipo de regra, selecione a propriedade no Launch e conclua as seguintes etapas:

## 1. Criar uma regra

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


## 3. Adicionar condições

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

## 4. Definir a ação

1. Na seção **[!UICONTROL Ações]**, clique em **[!UICONTROL Adicionar]**.

1. Na lista suspensa **[!UICONTROL Extensão]**, selecione **[!UICONTROL Mobile Core]**.

1. Na lista suspensa **[!UICONTROL Tipo de ação]**, selecione **[!UICONTROL Anexar dados]**.

1. No painel direito, no campo **[!UICONTROL Carga JSON]**, digite os dados que serão adicionados a este Evento.

1. Clique em **[!UICONTROL Manter alterações]**.

No painel direito, você pode adicionar uma carga JSON de forma livre que adiciona dados a um evento do SDK antes que uma extensão que esteja escutando esse evento possa ouvir o evento. Neste exemplo, alguns dados de contexto são adicionados a esse evento antes que a extensão do Analytics o processe. Os dados de contexto adicionados agora estarão na ocorrência de saída do Analytics.

No exemplo a seguir, os valores `poi.city` e `poi.name` são adicionados aos dados de contexto do evento do Analytics. Os valores das novas chaves são determinados dinamicamente pelo SDK quando esse evento é processado.

![&quot;criar uma ação&quot;](/help/assets/ad-setAction_use-analytics-data.png)

## 5. Salve a regra e recrie a propriedade

Após concluir a configuração, verifique se a regra tem a seguinte aparência:

![&quot;a regra está concluída.&quot;](/help/assets/ad-ruleComplete_use-analytics-data.png)

1. Clique em **[!UICONTROL Salvar]**

1. Recrie sua propriedade do Launch e implante-a no ambiente correto.
