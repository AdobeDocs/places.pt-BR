---
title: Enviar dados de locais para o Adobe Analytics
seo-title: Enviar dados de locais para o Adobe Analytics
description: Esta seção fornece informações sobre como enviar dados do Local para o Analytics.
seo-description: 'Esta seção fornece informações sobre como enviar dados do Local para o Analytics. '
translation-type: tm+mt
source-git-commit: 0612e2fb06e45ff25ad580e3336be3eb48bb39b9

---


# Enviar dados de locais para o Adobe Analytics {#places-data-analytics}


(Espaço reservado para o vídeo de Steve.)

>[!IMPORTANT]
>
>Este documento presume que você tenha Locais implementados em seu aplicativo. Para obter mais informações sobre a implementação de Locais, consulte Extensões [de](/help/places-ext-aep-sdks/places-extension/places-extension.md)Locais.

Depois que o Places enviar os eventos de entrada e saída, você pode criar regras no Experience Platform Launch para enviar os dados do Local ao Adobe Analytics. Para criar esse tipo de regra, selecione sua propriedade em Iniciar e conclua as seguintes etapas:

## 1. Criar uma regra

1. Na **[!UICONTROL Rules]** guia, clique em **[!UICONTROL Create New Rule]**.

   Lembre-se das seguintes informações:

   * Se você não tiver regras existentes para essa propriedade, o botão estará no meio da tela.
   * Se sua propriedade tiver regras, o botão estará no canto superior direito da tela.

## 2. Selecionar um evento

1. Dê um nome significativo à sua regra para que ela seja facilmente reconhecível na sua lista de Regras. Neste exemplo, a regra se chama **Enviar dados para o Analytics**.

2. In the **[!UICONTROL Events]** section, click **[!UICONTROL Add]**.

3. Na lista **[!UICONTROL Extension]** suspensa, selecione **[!UICONTROL Places]**.

4. Na lista **[!UICONTROL Event Type]** suspensa, selecione **[!UICONTROL Enter POI]**.

5. Clique em **[!UICONTROL Keep Changes]**.

   !["selecionar um evento"](/help/assets/pt-selectEvent.png)


## 3. Adicionar condições

>[!IMPORTANT]
>
>Conclua esta etapa se desejar adicionar Condições à sua regra. Caso contrário, pule para *Definir a ação* abaixo.


Neste exemplo, é criada uma Condição que faz com que a Regra seja acionada somente quando o nome do POI atual for igual **[!UICONTROL My POI]**.

1. Na **[!UICONTROL Conditions]** seção, clique em **[!UICONTROL Add]**.

2. Na lista **[!UICONTROL Extension]** suspensa, selecione **[!UICONTROL Places]**.

3. Na lista **[!UICONTROL Condition Type]** suspensa, selecione **[!UICONTROL Name]**.

4. Na janela à direita, no campo de texto, digite **[!UICONTROL My POI]**.

5. Clique em **[!UICONTROL Keep Changes]**.

   !["definir uma condição"](/help/assets/ad-setCondition.png)


## 4. Definir a ação

1. Na **[!UICONTROL Actions]** seção, clique em **[!UICONTROL Add]**.

2. Na lista **[!UICONTROL Extension]** suspensa, selecione **[!UICONTROL Adobe Analytics]**.

3. Na lista **[!UICONTROL Action Type]** suspensa, selecione **[!UICONTROL Track]**.

4. No painel direito, adicione a ação ou o estado que deseja enviar ao Analytics. Você também pode optar por adicionar quaisquer dados de contexto adicionais a essa solicitação. Lembre-se de que você pode usar elementos de dados para obter esses dados dinamicamente do SDK.

5. Clique em **[!UICONTROL Keep Changes]**.

No exemplo a seguir, uma `TrackAction` chamada é enviada ao Analytics com dados de contexto adicionais de **poi.name** iguais ao nome do POI que acionou esse evento de entrada:

!["definir uma ação"](/help/assets/pt-setAction.png)

## 5. Salve a regra e recrie sua propriedade

Após concluir a configuração, verifique se a Regra se parece com a seguinte imagem:

!["regra é criada"](/help/assets/pt-ruleComplete.png)


1. Clique em **[!UICONTROL Save]**

2. Recrie a propriedade Launch e implante-a no Ambiente correto.

