---
title: Adobe Target
description: Esta seção fornece informações sobre como usar o Places Service com o Adobe Target.
exl-id: 6ee91fca-ea48-4de2-8dcf-87981813c678
source-git-commit: 4ab15ded930b31e4e06920af31f37fdfe45df8eb
workflow-type: tm+mt
source-wordcount: '542'
ht-degree: 1%

---

# Usar o Places Service com o Adobe Target {#places-target}

Este documento supõe que a extensão Places esteja implementada no aplicativo. Se precisar de ajuda para implementar a extensão do Places, consulte [Extensões do Places](/help/places-ext-aep-sdks/places-extension/places-extension.md).

Depois que a extensão Places envia eventos para entradas e saídas, você pode aproveitar as Regras no Launch para anexar os dados do Serviço Places aos eventos do SDK da Adobe Target. Com a propriedade desejada selecionada no Launch, você pode criar esse tipo de regra concluindo as seguintes tarefas:

## 1. Criar uma regra

1. Na guia **[!UICONTROL Regras]**, clique em **[!UICONTROL Criar nova regra]**.

   Lembre-se das seguintes informações:

   * Se você não tiver regras existentes para essa propriedade, o botão estará no meio da tela.
   * Se a propriedade tiver regras, o botão estará na parte superior direita da tela.

## 2. Selecionar um Evento

1. Dê um nome significativo à regra para que ela seja facilmente reconhecível na lista de Regras.

   Neste exemplo, a regra é chamada **[!UICONTROL Anexar dados do serviço de locais ao conteúdo de destino solicitado]**.

1. Na seção **[!UICONTROL Eventos]**, clique em **[!UICONTROL Adicionar]**.
1. Na lista suspensa **[!UICONTROL Extensão]**, selecione **[!UICONTROL Adobe Target]**.
1. Na lista suspensa **[!UICONTROL Tipo de Evento]**, selecione **[!UICONTROL Conteúdo Solicitado]**.
1. Clique em **[!UICONTROL Manter alterações]**.

![adicionar um evento](/help/assets/ad-setEvent_target.png)

## 3. Adicionar condições

>[!IMPORTANT]
>
>Conclua esta etapa se desejar adicionar Condições à regra. Caso contrário, pule para a *Definir a Ação* abaixo.

No exemplo a seguir, uma Condição é criada e faz com que a Regra seja acionada somente para usuários que inicializaram o aplicativo cinco ou mais vezes.

1. Na seção **[!UICONTROL Condições]**, clique em **[!UICONTROL Adicionar]**.
1. Na lista suspensa **[!UICONTROL Extensão]**, selecione **[!UICONTROL Mobile Core]**.
1. Na lista suspensa **[!UICONTROL Tipo de Condição]**, selecione **[!UICONTROL Inicializações]**.
1. No painel direito, modifique a lista suspensa e os controles de número para que a condição exiba **[!UICONTROL O usuário iniciou o aplicativo mais ou igual a 5 vezes]**.
1. Clique em **[!UICONTROL Manter alterações]**.

![adicionar uma condição](/help/assets/ad-setCondition_target.png)

## 4. Definir a ação

1. Na seção **[!UICONTROL Ações]**, clique em **[!UICONTROL Adicionar]**.
1. Na lista suspensa **[!UICONTROL Extensão]**, selecione **[!UICONTROL Mobile Core]**.
1. Na lista suspensa **[!UICONTROL Tipo de ação]**, selecione **[!UICONTROL Anexar dados]**.
1. No painel direito, no campo **[!UICONTROL Carga JSON]**, digite os dados que serão adicionados a este Evento.
1. Clique em **[!UICONTROL Manter alterações]**.

No painel direito, você pode adicionar uma carga JSON de forma livre que adiciona dados a um evento do SDK antes que as extensões que estão escutando esse evento o ouçam.

No exemplo a seguir, os valores `poiCity` e `poiName` são adicionados aos **[!UICONTROL mboxparameters]** para cada solicitação que é processada no evento Target. Os valores das novas chaves são determinados dinamicamente pelo SDK no momento em que esse evento é processado.

>[!TIP]
>
>Esta carga JSON usa uma notação especial para o objeto `request`. No evento original, `request` é uma matriz de objetos anônimos. Ao anexar dados a todos os objetos em uma matriz usando Anexar Dados, a notação `[*]` em uma chave que é conhecida por conter uma matriz faz com que a carga seja aplicada a todos os objetos nessa matriz.
>
>A notação de `request[*]` pode ser lida em voz alta como _para cada objeto na matriz `request`_.

![definir a ação](/help/assets/ad-setAction-target.png)

## 5. Salve a regra e recrie a propriedade

Após concluir a configuração, verifique se a regra tem a seguinte aparência:

![regra concluída](/help/assets/ad-ruleComplete-target.png)

1. Clique em **[!UICONTROL Salvar]**
1. Recrie sua propriedade do Launch e implante-a no ambiente correto.
