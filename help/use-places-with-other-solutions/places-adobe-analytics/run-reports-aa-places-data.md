---
title: Executar relatórios no Adobe Analytics que incluem dados do Local
seo-title: Executar relatórios no Adobe Analytics que incluem dados do Local
description: Esta seção fornece informações sobre como executar relatórios no Analytics que incluem dados de Locais.
seo-description: Esta seção fornece informações sobre como executar relatórios no Analytics que incluem dados de Locais.
translation-type: tm+mt
source-git-commit: 0612e2fb06e45ff25ad580e3336be3eb48bb39b9

---


# Executar relatórios no Adobe Analytics que incluem dados do Local {#run-reports-aa-locserv-data}

>[!IMPORTANT]
>
>Este documento presume que você tenha o Adobe Places implementado em seu aplicativo. Para obter mais informações sobre a implementação do Adobe Places, consulte Extensões [do](/help/places-ext-aep-sdks/places-extension/places-extension.md)Places.

Depois que o Places enviar os eventos de entrada e saída, você pode criar regras no Experience Platform Launch e anexar seus dados do Places a todos os eventos do Adobe Analytics. Para criar esse tipo de regra, selecione sua propriedade em Iniciar e conclua as seguintes etapas:

## 1. Criar uma regra

1. Na **[!UICONTROL Rules]** guia, clique em **[!UICONTROL Create New Rule]**.

   Lembre-se das seguintes informações:
   * Se você não tiver regras existentes para essa propriedade, o botão estará no meio da tela.
   * Se sua propriedade tiver regras, o botão estará no canto superior direito da tela.

## 1.Selecione um evento

1. Dê um nome significativo à sua regra para que ela seja facilmente reconhecível na sua lista de Regras.

   Neste exemplo, a regra é chamada de **Anexar dados de locais aos eventos** de ação de rastreamento do Analytics.

2. Na **[!UICONTROL Events]** seção, clique em **[!UICONTROL Add]**.

3. Na lista **[!UICONTROL Extension]** suspensa, selecione **[!UICONTROL Mobile Core]**.

4. Na lista **[!UICONTROL Event Type]** suspensa, selecione **[!UICONTROL Track Action]**.

Agora você pode determinar os acionadores que deseja incluir para esta Regra. Neste exemplo, o acionador se baseia em todas as `TrackAction` chamadas. Depois de configurar o Evento, clique em **[!UICONTROL Keep Changes]**.

!["criar um evento"](/help/assets/ad-setEvent.png)


## 2. Adicionar condições

>[!IMPORTANT]
>
>Conclua esta etapa se desejar adicionar Condições à sua regra. Caso contrário, pule para a seção *Definir a ação* abaixo.

Neste exemplo, é criada uma Condição que faz com que a Regra seja acionada somente para clientes AT&amp;T.

1. Na **[!UICONTROL Conditions]** seção, clique em **[!UICONTROL Add]**.

2. Na lista **[!UICONTROL Extension]** suspensa, selecione **[!UICONTORL Mobile Core]**.

3. Na lista **[!UICONTROL Condition Type]** suspensa, selecione **[!UICONTROL Carrier Name]**.

4. Na janela à direita, marque a **[!UICONTROL AT&T]** caixa de seleção.

5. Clique em **[!UICONTROL Keep Changes]**.

!["criar uma condição"](/help/assets/ad-setCondition.png)

## 3. Definir a ação

1. Na **[!UICONTROL Actions]** seção, clique em **[!UICONTROL Add]**.

2. Na lista **[!UICONTROL Extension]** suspensa, selecione **[!UICONTROL Mobile Core]**.

3. Na lista **[!UICONTROL Action Type]** suspensa, selecione **[!UICONTROL Attach Data]**.

4. No painel direito, no **[!UICONTROL JSON Payload]** campo, digite os dados que serão adicionados a este Evento.

5. Clique em **[!UICONTROL Keep Changes]**.

No painel direito, é possível adicionar uma carga JSON de forma livre que adicione dados a um evento SDK antes que uma extensão que está acompanhando esse evento possa ouvir o evento. Neste exemplo, alguns dados de contexto são adicionados a esse evento antes da extensão do Analytics processá-lo. Os dados de contexto adicionados agora estarão na ocorrência de saída do Analytics.

No exemplo a seguir, `poi.city` e `poi.name` os valores são adicionados aos dados de contexto do evento do Analytics. Os valores das novas chaves são determinados dinamicamente pelo SDK quando esse evento é processado.

!["criar uma ação"](/help/assets/pt-setAction.png)

## 4. Salve a regra e recrie sua propriedade

Após concluir a configuração, verifique se a Regra se parece com a seguinte imagem:

!["a regra está completa."](/help/assets/pt-ruleComplete.png)

1. Clique em **[!UICONTROL Save]**

2. Recrie a propriedade Launch e implante-a no Ambiente correto.
