---
title: Notificações no aplicativo
description: Esta seção mostra como usar os Locais com mensagens no aplicativo.
translation-type: tm+mt
source-git-commit: 5a0705f02c8ecd540506b628371aec45107df7b2

---


# Notificações no aplicativo (#place-push-messaging)

As informações a seguir mostram como configurar mensagens no aplicativo para disparar dos eventos Locais.

>[!IMPORTANT]
>
>As mensagens devem estar em uma ocorrência do Analytics.

## Mensagem no aplicativo

O Mobile Services permite que você use dados de localização que estão sendo enviados ao Analytics como evento(s) de disparo e/ou condição para uma mensagem no aplicativo. Se as mensagens no aplicativo forem disparadas do SDK e não precisarem aguardar o processamento dos dados pelo Analytics, elas poderão aparecer em tempo real assim que o acionador ocorrer.

### Notificações locais

Esta é uma lista dos tipos de mensagens disponíveis no aplicativo:

* Tela cheia
* Alerta
* Notificações locais

Esses tipos são mensagens no aplicativo porque são acionados pelo SDK. As notificações locais parecem notificações por push, pois são exibidas quando o aplicativo está em segundo plano. Essas notificações também fornecem notificações em tempo real à medida que os usuários entram ou saem de seus POIs enquanto o aplicativo está em segundo plano. Para obter mais informações, consulte a extensão [do Monitor de](/help/places-ext-aep-sdks/places-monitor-extension/places-monitor-extension.md)locais.

### Pré-requisitos

Antes de começar, você entende como enviar e criar uma mensagem no aplicativo no Mobile Services e como os acionadores funcionam. Para obter mais informações, consulte [Criar uma mensagem no aplicativo.](https://docs.adobe.com/content/help/en/mobile-services/using/messaging-ug/inapp-messages/t-in-app-message.html)

## Regras do Experience Platform Launch

É possível criar regras de inicialização que enviem os dados que você deseja que possam ser usados como parte das regras de Acionador de mensagem no aplicativo para o Analytics. Você pode usar dados das extensões Locais nas regras de lançamento como eventos e/ou condições, dependendo do caso de uso.

* Usar dados de localização como evento de acionamento.

   Por exemplo, você pode enviar dados para o Analytics quando um usuário digitar um POI.

* Uso de dados de localização como uma Condição para um evento de acionamento.

   Por exemplo, se você tiver criado uma tag de metadados personalizada no Serviço de localização para o tempo em POIs diferentes, poderá usar esses metadados como parâmetro para a condição Regra. Embora seja possível usar essa condição com um evento de entrada POI descrito anteriormente, também é possível usar a condição como contexto para qualquer evento.

Depois que a regra for configurada com os parâmetros de evento e condição apropriados, conclua a configuração da regra configurando a ação para enviar dados ao Analytics.

## Criar uma ação

Para criar uma ação:

1. Selecione a extensão do **[!UICONTROL Adobe Analytics]**.
1. Na lista **[!UICONTROL Action type]**suspensa, selecione**[!UICONTROL Track.]**
1. Digite um nome para sua ação.
1. No painel direito, em **[!UICONTROL Context Data]**, selecione o par de valores chave para definir os dados de contexto que serão enviados para o Analytics.

Por exemplo, você pode selecionar `poiname` como a chave e `{%%Last Entered POI Name}` o valor.

>[!TIP]
>
>As Regras de processamento do Analytics podem ser definidas para coletar esses dados de contexto. Para obter mais informações, consulte [Regras de processamento](https://docs.adobe.com/content/help/en/analytics/implementation/analytics-basics/ref-processing-rules.html). No exemplo em *Criar uma ação*, a Ação enviará o `poiname` como o contexto para descrever o evento de entrada POI que está sendo enviado para o Analytics.

![criação de uma ação](/help/assets/configure-action.png)

Este é um exemplo da regra completa:

![regra concluída](/help/assets/create-a-rule.png)

## Criar uma mensagem no aplicativo no Mobile Services

Como parte dos parâmetros do Acionador, você pode criar o público-alvo para a mensagem com dados do Serviço de localização de uma das seguintes maneiras:

* Usando ações específicas de localização, como uma entrada ou uma saída.
* Usar metadados POI enviados como dados de contexto para restringir a meta do seu público-alvo.

   Essa opção pode ser usada com uma ação específica do local, como entrada, ou pode ser usada como contexto para outro evento, como uma inicialização ou um clique de botão.

   Este é um exemplo de como configurar uma mensagem no aplicativo para receber usuários que digitam um POI que tenha **[!UICONTROL Adobe]**o nome:

   ![parâmetros de acionamento](/help/assets/trigger-parameters.png)

* Os parâmetros nos cabeçalhos Locais na página *Acionadores e Características* no Mobile Services não funcionam com dados do Serviço de Localização.

   Esses parâmetros são apenas para o banco de dados herdado do Places criado no Mobile Services.