---
title: Notificações no aplicativo
description: Esta seção mostra como usar o Serviço de Places com mensagens no aplicativo.
exl-id: c655e64b-0737-44d5-b453-2ac02fb9cbcc
source-git-commit: d5c216aebd99ffef01c37c17c62576835b52438b
workflow-type: tm+mt
source-wordcount: '644'
ht-degree: 2%

---

# Notificações no aplicativo {#places-push-messaging}

As informações a seguir mostram como configurar mensagens no aplicativo para acionar eventos do Places Service.

>[!IMPORTANT]
>
>As mensagens devem estar em uma ocorrência do Analytics.

## Mensagem no aplicativo

O Mobile Services permite usar dados de localização enviados para o Analytics como evento(s) de acionador e/ou condição para uma mensagem no aplicativo. Se as mensagens no aplicativo forem acionadas pelo SDK e não precisarem aguardar o processamento dos dados pelo Analytics, as mensagens poderão aparecer em tempo real assim que o acionador ocorrer.

### Notificações locais

Esta é uma lista dos tipos de mensagens no aplicativo disponíveis:

* Tela cheia
* Alerta
* Notificações locais

Esses tipos são mensagens no aplicativo porque são acionadas pelo SDK. As notificações locais parecem notificações por push porque aparecem quando o aplicativo está em segundo plano. Essas notificações também fornecem notificações em tempo real, pois os usuários entram ou saem dos POIs enquanto o aplicativo está em segundo plano.

### Pré-requisitos

Antes de começar, você entende como enviar e criar uma mensagem no aplicativo no Mobile Services e como os acionadores funcionam. Para obter mais informações, consulte [Criar uma mensagem no aplicativo.](https://experienceleague.adobe.com/docs/discontinued/using/mobile-services.htmlhtml?lang=pt-BR)

## Regras no Experience Platform Launch

Você pode criar regras de Experience Platform Launch que enviam os dados que deseja poder usar como parte das regras de acionador de mensagens no aplicativo para o Analytics. Você pode usar dados das extensões do Places em suas regras de Experience Platform Launch como eventos e/ou condições, dependendo do caso de uso.

* Utilização de dados de localização como evento de acionamento.

  Por exemplo, você pode enviar dados para o Analytics quando um usuário insere um POI.

* Uso de dados de localização como uma Condição para um evento de acionamento.

  Por exemplo, se você criou uma tag de metadados personalizada no Serviço de Places para o clima em diferentes POIs, poderá usar esses metadados como um parâmetro para a condição Regra. Embora você possa usar essa condição com um evento de entrada de POI descrito anteriormente, também é possível usá-la como contexto para qualquer evento.

Depois que a regra for configurada com os parâmetros de evento e condição apropriados, conclua a configuração da regra configurando a ação para enviar dados ao Analytics.

## Criar uma ação

Para criar uma ação:

1. Selecione a extensão **[!UICONTROL Adobe Analytics]**.
1. Na lista suspensa **[!UICONTROL Tipo de ação]**, selecione **[!UICONTROL Rastrear.]**
1. Digite um nome para a ação.
1. No painel direito, em **[!UICONTROL Dados de contexto]**, selecione o par de valores chave para definir os dados de contexto que serão enviados para o Analytics.

Por exemplo, você pode selecionar `poiname` como chave e `{%%Last Entered POI Name}` como valor.

>[!TIP]
>
>As Regras de processamento do Analytics podem ser configuradas para coletar esses dados de contexto. Para obter mais informações, consulte [Regras de processamento](https://experienceleague.adobe.com/docs/analytics/admin/admin-tools/manage-report-suites/edit-report-suite/report-suite-general/c-processing-rules/processing-rules.html?lang=pt-BR). No exemplo em *Criar uma ação*, a Ação enviará `poiname` como contexto para descrever o evento de entrada do POI que está sendo enviado para o Analytics.

![criando uma ação](/help/assets/configure-action.png)

Este é um exemplo da regra completa:

![regra concluída](/help/assets/create-a-rule.png)

## Criação de uma mensagem no aplicativo no Mobile Services

Como parte dos parâmetros do Acionador, você pode criar o público-alvo para a mensagem com dados do serviço do Places de uma das seguintes maneiras:

* Usar ações específicas de localização, como uma entrada ou saída.
* Uso de metadados de POI enviados como dados de contexto para restringir o público-alvo.

  Essa opção pode ser usada com uma ação específica do local, como uma entrada, ou como contexto para outro evento, como uma inicialização ou um clique de botão.

  Este é um exemplo de como configurar uma mensagem no aplicativo para receber usuários que entram em um POI que tem **[!UICONTROL Adobe]** no nome:

  ![parâmetros do acionador](/help/assets/trigger-parameters.png)

* Os parâmetros nos cabeçalhos do Serviço do Places na página *Triggers e Características* do Mobile Services não funcionam com dados do Serviço do Places.

  Esses parâmetros são somente para o banco de dados herdado do Places Service que foi criado no Mobile Services.
