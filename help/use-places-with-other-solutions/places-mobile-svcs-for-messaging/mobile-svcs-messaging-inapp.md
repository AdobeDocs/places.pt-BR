---
title: Notificações no aplicativo
description: Esta seção mostra como usar o Places Service com mensagens no aplicativo.
exl-id: c655e64b-0737-44d5-b453-2ac02fb9cbcc
source-git-commit: 010de286c25c1eeb989fb76e3c2adaa82ac9fd35
workflow-type: tm+mt
source-wordcount: '661'
ht-degree: 4%

---

# Notificações no aplicativo {#places-push-messaging}

As informações a seguir mostram como configurar mensagens no aplicativo para serem acionadas a partir de eventos do Places Service.

>[!IMPORTANT]
>
>As mensagens devem estar em uma ocorrência do Analytics.

## Mensagem no aplicativo

O Mobile Services permite usar os dados de localização enviados para o Analytics como evento(s) de acionador e/ou condição para uma mensagem no aplicativo. Se as mensagens no aplicativo forem acionadas a partir do SDK e não precisarem aguardar o processamento dos dados pelo Analytics, as mensagens poderão aparecer em tempo real assim que o acionador ocorrer.

### Notificações locais

Esta é uma lista dos tipos disponíveis de mensagens no aplicativo:

* Tela cheia
* Alerta
* Notificações locais

Esses tipos são mensagens no aplicativo porque são acionadas pelo SDK. As notificações locais parecem ser notificações por push, pois são exibidas quando o aplicativo está em segundo plano. Essas notificações também fornecem notificações em tempo real quando os usuários entram ou saem dos POIs enquanto o aplicativo está em segundo plano.

### Pré-requisitos

Antes de começar, você entende como enviar e criar uma mensagem no aplicativo no Mobile Services e como os acionadores funcionam. Para obter mais informações, consulte [ Criar uma mensagem no aplicativo.](https://docs.adobe.com/content/help/en/mobile-services/using/messaging-ug/inapp-messages/t-in-app-message.html)

## Regras do Experience Platform Launch

Você pode criar regras do Experience Platform Launch que enviam os dados que deseja usar como parte das regras do Acionador de mensagem no aplicativo para o Analytics. Você pode usar dados das extensões do Places nas regras do Experience Platform Launch como eventos e/ou condições, dependendo do caso de uso.

* Usar dados de localização como o evento de acionamento.

   Por exemplo, você pode enviar dados para o Analytics quando um usuário insere um POI.

* Usar os dados de localização como uma condição para um evento de acionamento.

   Por exemplo, se você criou uma tag de metadados personalizada no Places Service para o tempo em POIs diferentes, você pode usar esses metadados como parâmetro para a condição da Regra. Embora você possa usar essa condição com um evento de entrada de POI descrito anteriormente, também pode usar a condição como contexto para qualquer evento.

Depois que a regra for configurada com os parâmetros de evento e condição adequados, conclua a configuração da regra configurando a ação para enviar dados para o Analytics.

## Criar uma ação

Para criar uma ação:

1. Selecione o **[!UICONTROL Adobe Analytics]** extensão.
1. No **[!UICONTROL Tipo de ação]** , selecione **[!UICONTROL Rastrear.]**
1. Digite um nome para sua ação.
1. No painel direito, em **[!UICONTROL Dados de contexto]**, selecione o par de chave-valor para definir os dados de contexto que serão enviados para o Analytics.

Por exemplo, você pode selecionar `poiname` como a chave e `{%%Last Entered POI Name}` como o valor.

>[!TIP]
>
>As Regras de processamento do Analytics podem ser definidas para coletar esses dados de contexto. Para obter mais informações, consulte [Regras de processamento](https://docs.adobe.com/content/help/en/analytics/implementation/analytics-basics/ref-processing-rules.html). No exemplo em *Criar uma ação*, a Ação enviará a variável `poiname` como o contexto para descrever o evento de entrada de POI que está sendo enviado para o Analytics.

![criação de uma ação](/help/assets/configure-action.png)

Este é um exemplo da regra completa:

![regra concluída](/help/assets/create-a-rule.png)

## Criar uma mensagem no aplicativo no Mobile Services

Como parte dos parâmetros do Acionador, você pode criar o público-alvo para a mensagem com dados do Places Service de uma das seguintes maneiras:

* Uso de ações específicas de localização, como uma entrada ou uma saída.
* Usar metadados de POI enviados como dados de contexto para limitar o público-alvo.

   Essa opção pode ser usada com uma ação específica do local, como entrada, ou pode ser usada como contexto para outro evento, como um lançamento ou um clique de botão.

   Este é um exemplo de como configurar uma mensagem no aplicativo para receber usuários que inserirem um POI que tenha **[!UICONTROL Adobe]** No nome:

   ![parâmetros de acionamento](/help/assets/trigger-parameters.png)

* Parâmetros nos cabeçalhos do Places Service na *Triggers e características* no Mobile Services não funcionam com dados do Places Service.

   Esses parâmetros são apenas para o banco de dados herdado do Places Service, criado no Mobile Services.
