---
title: Enviar dados de locais para o Adobe Analytics
seo-title: Enviar dados de locais para o Adobe Analytics
description: Esta seção fornece informações sobre como enviar dados do Local para o Analytics.
seo-description: Esta seção fornece informações sobre como enviar dados do Local para o Analytics.
translation-type: tm+mt
source-git-commit: 95dd010db8a860ebf489d04c7a70ec9cda8b3fb1

---


# Enviar dados de locais para o Adobe Analytics {#places-data-analytics}


>[!IMPORTANT]
>
>Esta seção presume que você tenha Locais implementados em seu aplicativo. Para obter mais informações sobre como implementar Locais, consulte Extensões [](/help/places-ext-aep-sdks/places-extension/places-extension.md)Locais.

Depois que o Places enviar os eventos de entrada e saída, você pode criar regras no Experience Platform Launch para enviar os dados do Local ao Adobe Analytics. Para criar esse tipo de regra, selecione sua propriedade em Iniciar e conclua as seguintes etapas:

## 1. Criar uma regra

1. Na **[!UICONTROL Rules]** guia, clique em **[!UICONTROL Create New Rule]**.

   Lembre-se das seguintes informações:

   * Se você não tiver regras existentes para essa propriedade, o **[!UICONTROL Create New Rule]** botão estará no meio da tela.
   * Se sua propriedade tiver regras, o **[!UICONTROL Create New Rule]** botão estará no canto superior direito da tela.

## 2. Selecionar um evento

1. Digite um nome significativo para sua regra.

   Dessa forma, a regra será facilmente reconhecível em sua lista de Regras. Neste exemplo, a Regra é nomeada **[!UICONTROL Send Data to Analytics]**.

1. In the **[!UICONTROL Events]** section, click **[!UICONTROL Add]**.

1. Na lista **[!UICONTROL Extension]** suspensa, selecione **[!UICONTROL Places]**.

1. Na lista **[!UICONTROL Event Type]** suspensa, selecione **[!UICONTROL Enter POI]**.

1. Clique em **[!UICONTROL Keep Changes]**.

   !["selecionar um evento"](/help/assets/pt-selectEvent.png)


## 3. Adicionar condições

>[!IMPORTANT]
>
>Conclua esta etapa para adicionar Condições à regra. Caso contrário, pule para *Definir a ação* abaixo.

Neste exemplo, é criada uma Condição que faz com que a Regra seja acionada somente quando o nome do POI atual for igual **[!UICONTROL My POI]**.

1. Na **[!UICONTROL Conditions]** seção, clique em **[!UICONTROL Add]**.

1. Na lista **[!UICONTROL Extension]** suspensa, selecione **[!UICONTROL Places]**.

1. Na lista **[!UICONTROL Condition Type]** suspensa, selecione **[!UICONTROL Name]**.

1. No painel direito, no campo de texto, digite **[!UICONTROL My POI]**.

1. Clique em **[!UICONTROL Keep Changes]**.

   !["definir uma condição"](/help/assets/pt-setCondition.png)


## 4. Definir a ação

1. Na **[!UICONTROL Actions]** seção, clique em **[!UICONTROL Add]**.

1. Na lista **[!UICONTROL Extension]** suspensa, selecione **[!UICONTROL Adobe Analytics]**.

1. Na lista **[!UICONTROL Action Type]** suspensa, selecione **[!UICONTROL Track]**.

1. No painel direito, adicione a ação ou o estado que deseja enviar ao Analytics.

   Você também pode optar por adicionar quaisquer dados de contexto adicionais a essa solicitação. Lembre-se de que você pode usar elementos de dados para obter esses dados dinamicamente do SDK.

1. Clique em **[!UICONTROL Keep Changes]**.

   No exemplo a seguir, uma `TrackAction` chamada é enviada ao Analytics com dados de contexto adicionais `poi.name` iguais ao nome do POI que acionou esse evento de entrada:

   !["definir uma ação"](/help/assets/pt-setAction.png)

## 5. Salve a regra e recrie sua propriedade

Após concluir a configuração, verifique se a Regra se parece com a seguinte imagem:

!["regra é criada"](/help/assets/pt-ruleComplete.png)

1. Clique em **[!UICONTROL Save]**

1. Recrie a propriedade Launch e implante-a no ambiente correto.
