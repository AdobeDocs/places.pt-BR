---
title: Adobe Target
description: Esta seção fornece informações sobre como usar o Serviço Places com a Adobe Target.
translation-type: tm+mt
source-git-commit: d33e4e2d798c7048bdd275cdf6c0aabf3434f789
workflow-type: tm+mt
source-wordcount: '477'
ht-degree: 2%

---


# Usar o serviço Places com a Adobe Target {#places-target}

Esse documento supõe que você tenha a extensão Locais implementada em seu aplicativo. Se precisar de ajuda para implementar a extensão de Locais, consulte Extensões [de](/help/places-ext-aep-sdks/places-extension/places-extension.md)Locais.

Depois que a extensão Locais estiver enviando eventos para entradas e saídas, você poderá aproveitar as Regras no Launch para anexar seus dados do Serviço de Locais aos eventos do SDK do Adobe Target. Com a propriedade desejada selecionada em Iniciar, você pode criar esse tipo de regra completando as seguintes tarefas:

## 1. Criar uma regra

1. On the **[!UICONTROL Rules]** tab, click **[!UICONTROL Create New Rule]**.

   Lembre-se das seguintes informações:

   * Se você não tiver regras existentes para essa propriedade, o botão estará no meio da tela.
   * Se sua propriedade tiver regras, o botão estará no canto superior direito da tela.

## 2. Selecionar um Evento

1. Dê um nome significativo à sua regra para que ela seja facilmente reconhecível na sua lista de Regras.

   Neste exemplo, a Regra é nomeada **[!UICONTROL Attach Places Service Data to Target Content Requested]**.

1. Under the **[!UICONTROL Events]** section, click **[!UICONTROL Add]**.
1. Na lista **[!UICONTROL Extension]** suspensa, selecione **[!UICONTROL Adobe Target]**.
1. Na lista **[!UICONTROL Event Type]** suspensa, selecione **[!UICONTROL Content Requested]**.
1. Clique em **[!UICONTROL Keep Changes]**.

![adicionar um evento](/help/assets/ad-setEvent_target.png)

## 3. Adicionar condições

>[!IMPORTANT]
>
>Conclua esta etapa se desejar adicionar Condições à sua regra. Caso contrário, pule para *Definir a ação* abaixo.

No exemplo a seguir, é criada uma Condição que faz com que a Regra seja acionada somente para usuários que inicializaram o aplicativo cinco ou mais vezes.

1. Under the **[!UICONTROL Conditions]** section, click **[!UICONTROL Add]**.
1. Na lista **[!UICONTROL Extension]** suspensa, selecione **[!UICONTROL Mobile Core]**.
1. Na lista **[!UICONTROL Condition Type]** suspensa, selecione **[!UICONTROL Launches]**.
1. No painel direito, modifique a lista suspensa e os controles de número para que a condição seja lida **[!UICONTROL User has launched the app greater than or equal to 5 times]**.
1. Clique em **[!UICONTROL Keep Changes]**.

![adicionar uma condição](/help/assets/ad-setCondition_target.png)

## 4. Definir a ação

1. Under the **[!UICONTROL Actions]** section, click **[!UICONTROL Add]**.
1. Na lista **[!UICONTROL Extension]** suspensa, selecione **[!UICONTROL Mobile Core]**.
1. Na lista **[!UICONTROL Action Type]** suspensa, selecione **[!UICONTROL Attach Data]**.
1. No painel direito, no **[!UICONTROL JSON Payload]** campo, digite os dados que serão adicionados a esse Evento.
1. Clique em **[!UICONTROL Keep Changes]**.

No painel direito, é possível adicionar uma carga JSON de forma livre que adicione dados a um evento SDK antes que as extensões que ouvem esse evento o ouçam.

No exemplo a seguir, `poiCity` e `poiName` valores são adicionados ao **[!UICONTROL mboxparameters]** para cada solicitação processada no evento do Público alvo. Os valores das novas chaves são determinados dinamicamente pelo SDK no momento em que o evento é processado.

>[!TIP]
>
>Essa carga JSON usa uma notação especial para o `request` objeto. No evento original, `request` há uma matriz de objetos anônimos. Ao anexar dados a todos os objetos em um storage usando Anexar dados, a `[*]` notação em uma chave que é conhecida por conter um storage faz com que a carga seja aplicada a todos os objetos nesse storage.
>
>A notação de `request[*]` pode ser lida em voz alta como _para cada objeto na `request` matriz_.

![definir a ação](/help/assets/ad-setAction-target.png)

## 5. Salve a regra e recrie sua propriedade

Após concluir a configuração, verifique se a Regra se parece com a seguinte imagem:

![regra concluída](/help/assets/ad-ruleComplete-target.png)

1. Clique em **[!UICONTROL Save]**
1. Recrie a propriedade Launch e implante-a no Ambiente correto.
