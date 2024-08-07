---
title: Enviar dados de entrada e saída de POI para o Analytics
description: Esta seção fornece informações sobre como enviar dados de entrada e saída do POI para o Analytics.
exl-id: 69e96261-4902-47dd-a930-a8f3d19c179c
source-git-commit: 4ab15ded930b31e4e06920af31f37fdfe45df8eb
workflow-type: tm+mt
source-wordcount: '437'
ht-degree: 1%

---

# Enviar dados de entrada e saída de POI para o Analytics {#places-data-analytics}


>[!IMPORTANT]
>
>Esta seção pressupõe que você tenha o Places Service implementado em seu aplicativo. Para obter mais informações sobre como implementar o Places Service, consulte [Extensões do Places](/help/places-ext-aep-sdks/places-extension/places-extension.md).

Depois que o Serviço de Places enviar os eventos de entrada e saída, você poderá criar regras no Experience Platform Launch para enviar dados do Serviço de Places à Adobe Analytics. Para criar esse tipo de regra, selecione a propriedade no Launch e conclua as seguintes etapas:

## 1. Criar uma regra

1. Na guia **[!UICONTROL Regras]**, clique em **[!UICONTROL Criar nova regra]**.

   Lembre-se das seguintes informações:

   * Se você não tiver regras existentes para esta propriedade, o botão **[!UICONTROL Criar nova regra]** estará no meio da tela.
   * Se a propriedade tiver regras, o botão **[!UICONTROL Criar nova regra]** estará na parte superior direita da tela.

## 2. Selecionar um evento

1. Digite um nome significativo para a regra.

   Dessa forma, a regra será facilmente reconhecível na lista de Regras. Neste exemplo, o nome da Regra é **[!UICONTROL Enviar Dados para o Analytics]**.

1. Na seção **[!UICONTROL Eventos]**, clique em **[!UICONTROL Adicionar]**.

1. Na lista suspensa **[!UICONTROL Extensão]**, selecione **[!UICONTROL Serviço do Places]**.

1. Na lista suspensa **[!UICONTROL Tipo de Evento]**, selecione **[!UICONTROL Inserir POI]**.

1. Clique em **[!UICONTROL Manter alterações]**.

   ![&quot;selecionar um evento&quot;](/help/assets/pt-selectEvent.png)


## 3. Adicionar condições

>[!IMPORTANT]
>
>Conclua esta etapa para adicionar Condições à regra. Caso contrário, pule para *Definir a Ação* abaixo.

Neste exemplo, uma Condição é criada e faz com que a Regra dispare somente quando o nome do POI atual é igual a **[!UICONTROL Meu POI]**.

1. Na seção **[!UICONTROL Condições]**, clique em **[!UICONTROL Adicionar]**.

1. Na lista suspensa **[!UICONTROL Extensão]**, selecione **[!UICONTROL Serviço do Places]**.

1. Na lista suspensa **[!UICONTROL Tipo de Condição]**, selecione **[!UICONTROL Nome]**.

1. No painel direito, no campo de texto, digite **[!UICONTROL Meu POI]**.

1. Clique em **[!UICONTROL Manter alterações]**.

   ![&quot;definir uma condição&quot;](/help/assets/pt-setCondition.png)


## 4. Definir a ação

1. Na seção **[!UICONTROL Ações]**, clique em **[!UICONTROL Adicionar]**.

1. Na lista suspensa **[!UICONTROL Extensão]**, selecione **[!UICONTROL Adobe Analytics]**.

1. Na lista suspensa **[!UICONTROL Tipo de ação]**, selecione **[!UICONTROL Rastrear]**.

1. No painel direito, adicione a ação ou o estado que deseja enviar para o Analytics.

   Você também pode optar por adicionar dados de contexto adicionais a essa solicitação. Lembre-se de que você pode usar elementos de dados para obter esses dados dinamicamente do SDK.

1. Clique em **[!UICONTROL Manter alterações]**.

   No exemplo a seguir, uma chamada `TrackAction` é enviada para o Analytics com dados de contexto adicionais de `poi.name` iguais ao nome do POI que acionou esse evento de entrada:

   ![&quot;definir uma ação&quot;](/help/assets/pt-setAction.png)

## 5. Salve a regra e recrie a propriedade

Após concluir a configuração, verifique se a regra tem a seguinte aparência:

![&quot;regra criada&quot;](/help/assets/pt-ruleComplete.png)

1. Clique em **[!UICONTROL Salvar]**

1. Recrie sua propriedade do Launch e implante-a no ambiente correto.
