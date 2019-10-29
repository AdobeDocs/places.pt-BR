---
title: Mensagens no aplicativo
seo-title: Mensagens no aplicativo
description: Esta seção mostra como usar os Locais com mensagens no aplicativo.
seo-description: Esta seção mostra como usar os Locais com mensagens no aplicativo.
translation-type: tm+mt
source-git-commit: 7985943cef606525401983c4c80862c277f41bf0

---


# Notificações no aplicativo (#place-push-messaging)

Como configurar mensagens no aplicativo para disparar de eventos do Places; as mensagens devem estar em uma ocorrência do Analytics.

## Mensagem no aplicativo

O AMS permite que você use dados de localização que estão sendo enviados para o Analytics como evento(s) de disparo e/ou condição para uma mensagem no aplicativo. As mensagens no aplicativo podem ser exibidas ao usuário em tempo real assim que o acionador é acionado do SDK e não é necessário aguardar o processamento dos dados pelo Analytics.

Notificações locais: As mensagens no aplicativo têm três tipos diferentes:

* Tela cheia
* Alerta
* Notificações locais.

Esses tipos se qualificam como mensagens no aplicativo porque são acionadas pelo SDK, mas é importante observar que as notificações locais parecem notificações por push à medida que aparecem enquanto o aplicativo não está em primeiro plano. As notificações locais são uma excelente opção para fornecer notificações em tempo real aos usuários quando eles entram ou saem do POI enquanto o aplicativo está em segundo plano. Consulte a documentação de extensão do Monitor de locais para entender o monitoramento de locais (https://placesdocs.com/places-services-by-adobe-documentation/configure-places-in-the-sdk/places-monitor-extension).

### Pré-requisitos

* Saiba como enviar e criar uma mensagem no aplicativo no AMS e como os Acionadores funcionam.

   Para obter mais informações, consulte [Criar uma mensagem no aplicativo](https://docs.adobe.com/content/help/en/mobile-services/using/messaging-ug/inapp-messages/t-in-app-message.html).


## Criar uma regra no Experience Platform Launch

Crie regras de lançamento que enviem os dados corretos para o Analytics que você deseja que possam ser usados como parte das regras de disparador de mensagens no aplicativo. Você pode usar dados das extensões Locais nas regras de lançamento como eventos e/ou condições, dependendo do caso de uso.

* Usar dados de localização como evento de acionamento. Por exemplo, se você deseja enviar dados para o Analytics quando um usuário entra em um POI.

* Uso de dados de localização como uma Condição para um evento de acionamento. Por exemplo, se você tiver criado uma tag de metadados personalizada no Serviço de localização para o tempo em POIs diferentes, poderá usar esses metadados como parâmetro para a condição Regra, como mostrado abaixo. Embora seja possível usar essa condição para o evento de entrada POI descrito anteriormente, também é possível usá-la como contexto para qualquer evento.

Depois que a regra for configurada com os parâmetros de evento e condição apropriados, conclua a configuração da regra configurando a ação para enviar dados ao Analytics. Para fazer isso:

* Selecione o Adobe Analytics como extensão
* Escolha "Rastrear" como o tipo de ação
* Determine um nome para sua ação
* Defina Dados de contexto para serem enviados com o evento. Use a interface Dados de contexto para mapear Elementos de dados de inicialização para os nomes de chave que deseja enviar ao Analytics.

Observe que as Regras de processamento do Analytics podem ser definidas para coletar esses dados de contexto. Consulte Regras de processamento do Analytics, se necessário (https://docs.adobe.com/content/help/en/analytics/implementation/analytics-basics/ref-processing-rules.html)Por exemplo, esta ação está enviando o ponteiro como contexto para descrever o evento POIentry que está sendo enviado ao Analytics.

![criação de uma ação](/help/assets/configure-action.png)

Este é um exemplo de como a regra finalizada poderia ser.

![regra concluída](/help/assets/create-a-rule.png)

## Criação de uma mensagem no aplicativo no AMS:

Você criará o público-alvo da mensagem com dados do Serviço de localização como parte dos parâmetros do Acionador.

* Uso de ações específicas de localização, como entrada ou saída
* Usar metadados POI enviados como dados de contexto para restringir o destino do seu público-alvo. Isso pode ser usado com uma ação específica do local, como entrada, ou pode ser usado como contexto para outro evento, como Iniciar ou clicar no botão.

   Este é um exemplo de como você pode configurar uma mensagem no aplicativo para receber usuários que digitam um POI que tenha "Adobe" no nome:

   ![parâmetros de acionamento](/help/assets/trigger-parameters.png)

* Os parâmetros encontrados nos cabeçalhos "Locais" nos AMS Triggers e Traits não funcionam com dados do Serviço de Localização. Esses parâmetros são para o banco de dados herdado Places criado no AMS.