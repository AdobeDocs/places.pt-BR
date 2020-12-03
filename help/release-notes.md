---
title: Notas de versão
description: Notas de versão do Places Service.
translation-type: tm+mt
source-git-commit: 3f986697179eb9c0af1d9b54daf67793a99b8491
workflow-type: tm+mt
source-wordcount: '1503'
ht-degree: 3%

---


# Notas de versão {#release-notes}

## 8 de julho de 2020

* **Extensões do monitor de locais e locais**

   * As extensões de monitores de locais e locais foram adicionadas para aplicativos [React Native](https://aep-sdks.gitbook.io/docs/resources/upgrading-to-aep/current-sdk-versions#react-native)
   * As extensões do Monitor de locais e locais foram adicionadas aos aplicativos [Cordova](https://aep-sdks.gitbook.io/docs/resources/upgrading-to-aep/current-sdk-versions#cordova)
   * Para obter mais informações, consulte: [Uso da extensão de locais](https://docs.adobe.com/content/help/pt-BR/places/using/places-ext-aep-sdks/places-extension/places-extension.translate.html)


## 12 de maio de 2020

* **Serviço de Places**

   * Importação em massa de POIs de um arquivo CSV usando o botão &quot;Importar POIs&quot;
   * Selecionar vários POIs e editar em massa ou adicionar valores de metadados

## 6 de maio de 2020

* **PlacesMonitor 2.1.1**

   * **Android**

      * Registro aprimorado

## 5 de maio de 2020


* **PlacesMonitor 2.1.3**

   * **iOS**

      * Registro aprimorado

## 20 de fevereiro de 2020

* **ACPPlaces 1.3.1 (iOS)**

   * A extensão Places agora relata as informações da versão para o hub do evento no SDK principal.
   * As informações de associação de POI do dispositivo agora têm um tempo de vida padrão de uma hora a partir do momento em que são coletadas. Para obter mais informações, consulte [Modificação do tempo de vida da associação aos locais](places-ext-aep-sdks/places-extension/places-extension.md#places-ttl)


* **Locais 1.4.1 (Android)**

   * A extensão Places agora relata as informações da versão para o hub do evento no SDK principal.
   * As informações de associação de POI do dispositivo agora têm um tempo de vida padrão de uma hora a partir do momento em que são coletadas. Para obter mais informações, consulte [Modificação do tempo de vida da associação aos locais](places-ext-aep-sdks/places-extension/places-extension.md#places-ttl)

## 27 de janeiro de 2020

* **PlacesMonitor 2.2.0**

   * **Android**

      * Chame a nova API de locais para coletar o status de autorização de localização quando o aplicativo for iniciado e a autorização for alterada enquanto o aplicativo estiver em execução.
      * Adicionada a API setRequestLocationPermission e a API setLocationPermission obsoleta.

## 9 de janeiro de 2020

* **Locais 1.4.0**

   * **Android**

      * Adição de uma nova API `setAuthorizationStatus`, para definir o status de autorização do dispositivo para os Serviços locais. O valor é armazenado e usado no estado compartilhado Locais.

## 4 de dezembro de 2019

* **PlacesMonitor 2.1.2**

   * **iOS**

      * Chame a API Places para coletar CLAuthorizationStatus do dispositivo quando ele é alterado.

## 3 de dezembro de 2019

* **ACPPlaces 1.3.0**

   * **iOS**

      * Adição de uma nova API `setAuthorizationStatus`, para definir o status de autorização do dispositivo para os Serviços locais. O valor é armazenado e usado no estado compartilhado Locais.

## 25 de novembro de 2019

* **PlacesMonitor 2.1.1**

   * **iOS**

      * Correção de declarações de importação para projetos do Cocoapods usando a opção de vários projetos do pod.

## 22 de novembro de 2019

* **PlacesMonitor 2.1.1**

   * **Android**

      * O monitor agora reconhece a inicialização de um dispositivo Android e, se necessário, registra as geofences novamente com o SO com base no local atual do dispositivo.
      * Corrigida uma condição de corrida que às vezes fazia com que eventos de entrada/saída fossem descartados.

## 9 de outubro de 2019

* **PlacesMonitor 2.1.0**

   * **iOS**

      * Adicionada uma nova API `setRequestAuthorizationLevel`, para definir o tipo de solicitação de autorização de localização para a qual o usuário será solicitado.
   * **Android**

      * Adicionada uma nova API `setLocationPermission`, para definir o tipo de solicitação de permissão de localização para a qual o usuário será solicitado.
      * O Monitor de locais agora é compatível com Android 10.



## 8 de agosto de 2019

As seguintes atualizações foram feitas nesta versão:

### Atualizações da interface

Esta é uma lista das atualizações da interface do usuário do Places:

#### Novos recursos

* Adicionada uma nova visualização de lista que mostra os POIs sem o mapa.
* Adicionadas opções de filtragem de POI para a cidade, o estado, o país e os metadados.
* A primeira biblioteca em uma organização é criada automaticamente.
* Classificação de POI adicionada à Visualização da Lista.

#### Atualizações da interface

* Painel lista e detalhes movido para o lado direito da interface do usuário.
* Adicionado um novo painel de pesquisa na parte superior da interface do usuário.
* Se apenas uma biblioteca estiver presente, essa biblioteca será selecionada automaticamente quando você criar um POI.
* Gerenciamento de biblioteca movido para uma janela pop-up.
* Foi adicionada uma contagem de POI ao lado dos filtros.

## 6 de agosto de 2019

As seguintes atualizações foram feitas nesta versão:

### Monitor Launch Extension 2.0.0

* Atualizadas as instruções de instalação do Android e do iOS para o Places Monitor 2.0.

## 31 de julho de 2019

As seguintes atualizações foram feitas nesta versão:

### Places Monitor 2.0.0

* O status do monitoramento agora é persistente entre inicializações.
* A manipulação do retorno de chamada, que resultou de uma solicitação de permissão de local, não exige mais que você estenda PlacesActivity.
* Alteração de uma API existente, permitindo que os desenvolvedores limpassem todos os dados do Local do dispositivo:

   API antiga: `public static void stop();`

   New API: `public static void stop (final boolean clearData);`

* Atualização do uso da `getNearbyPointsOfInterest` API para lidar com cenários de erro com mais eficiência.

## 25 de julho de 2019

As seguintes atualizações foram feitas nesta versão:

### ACPPlacesMonitor 2.0.0

* Para apagar todos os dados de Locais do dispositivo,

   no ACPPlacesMonitor, uma API existente foi substituída `+ (void) stop;` por`+ (void) stop: (BOOL) clearData;`.

* Atualização do uso da API ACPPlaces `getNearbyPointsOfInterest` para lidar com cenários de erro com mais eficiência.

## 22 de julho de 2019

As seguintes atualizações foram feitas nesta versão:

### Android Places 1.3.0

* Adicionada uma nova API que limpa todos os dados relacionados ao Local do estado compartilhado, memória no aplicativo e Preferência compartilhada.
* Correção de um problema em que o estado compartilhado não era atualizado durante o start do aplicativo.
* Correção de um bug no qual `getNearbyPointsOfInterest` o retorno de chamada retornava o código de erro `SERVER_RESPONSE_ERROR instead of CONNECTIVITY_ERROR` em nenhuma Internet.
* `getNearbyPointsOfInterest` A API (sem errorCallback) terá o `successCallback` chamado com lista poi vazia, em caso de erro ao recuperar os pontos de interesse próximos.

## 19 de julho de 2019

As seguintes atualizações foram feitas nesta versão:

**iOS Places 1.2.0**

Adicionada uma nova API que limpa todos os dados relacionados ao Local do estado compartilhado, memória no aplicativo e `NSUserDefaults`.

## 25 de junho de 2019

As seguintes atualizações foram feitas nesta versão:

**iOS Places Monitor 1.0.2**

* Melhorias na qualidade de vida, incluindo melhor documentação e registro em log no código.

## 17 de junho de 2019

As seguintes atualizações foram feitas nesta versão:

**iOS Places 1.1.0**

* Adicionada uma nova API para retornar um código de erro quando há uma falha ao recuperar locais próximos.
* Quando o status de privacidade for alterado para opt-out, todos os dados relacionados ao Local serão apagados do dispositivo.
* Correção de um problema que, após uma primeira inicialização, às vezes fazia com que eventos do Places fossem perdidos devido a condições de rede ruins.
* Correção de um problema em que, ao processar eventos de entrada POI em sucessão rápida, a substituição de token via Mecanismo de regras às vezes referenciava o POI incorreto.

## 30 de maio de 2019

**Android Places Monitor 1.0.1**

* Correção de um problema que impedia um evento de entrada para POIs quando o monitoramento de Locais era iniciado.

## 28 de maio de 2019

Correção dos seguintes problemas na interface do usuário do Places:

* Atualização do Alternador de soluções em locais para alinhar com o restante do Experience Cloud.
* Correção de um problema em que a classificação era salva em instâncias em que nenhuma alteração de classificação era feita.
* O raio mínimo permitido na interface do usuário foi aumentado para 10 metros.
* Correção de um problema em que, se todos os números do campo forem excluídos, o campo de raio redefinirá para 20 metros.

## 17 de maio de 2019

As seguintes atualizações foram feitas nesta versão:

**Android Places 1.2.0**

* Adicionada uma nova API para processar uma Geofence individual.
* Correção de erros para evitar vários eventos de entrada consecutivos.

**Android Places Monitor 1.0.0**

Lançamento inicial do Places Monitor para Android.

O Monitor de locais gerencia as APIs de localização no nível do SO e se comunica diretamente com a extensão Locais. Com ambas as extensões instaladas, os clientes podem ter monitoramento de região predefinido em seus aplicativos.
Para obter mais informações sobre o Monitor de locais, clique aqui.


## 2 de maio de 2019

**Android Places 1.1.0**

* Introduziu uma nova API para getNearByPlaces, que tem um errorCallback e é chamada com um errorCode que indica o motivo do erro.
* A extensão Locais agora enfileira os eventos até que uma configuração seja obtida.
* Adicionado suporte para configurações com reconhecimento de ambientes.
* Correção de erros: corrigidas as teclas dos eventos de entrada/saída da região
* Armazenamento do último local conhecido agora respeita corretamente o status de privacidade do usuário


## 9 de abril de 2019

As seguintes atualizações foram feitas nesta versão:

**iOS Places Monitor 1.0.1**

* Cobertura completa de teste de unidade adicionada.
* Integração CI (CircleCI)
* Integração de cobertura de código (codecov)

## 25 de março de 2019

iOS Places Monitor 1.0.0

Lançamento inicial do Places Monitor para iOS.

O Monitor de locais gerencia as APIs de localização no nível do SO e se comunica diretamente com a extensão Locais. Com ambas as extensões instaladas, os clientes podem ter monitoramento de região predefinido em seus aplicativos. Para obter mais informações sobre o Monitor de locais, consulte a extensão [do Monitor de](/help/places-ext-aep-sdks/places-monitor-extension/places-monitor-extension.md)locais.

## 28 de fevereiro de 2019

### Versão beta

Esta é a primeira versão do Places Service, um conjunto de ferramentas que permite aos clientes enriquecer as experiências dos usuários com dados de localização reais. Na primeira versão, nosso caso de uso principal é permitir que aplicativos móveis recuperem dados de localização personalizados e atuem sobre esses dados por meio do Adobe Experience Platform Launch.

### Recursos principais

Estes são os principais recursos desta versão:

#### Interface do usuário do serviço do Places

Lançamos uma interface de usuário de gerenciamento na qual você pode visualização e gerenciar seus pontos de interesse (POIs). Você também pode organizar seus POIs em bibliotecas. Além dos metadados padrão, como cidade, estado e categoria, também oferecemos suporte à capacidade de adicionar metadados personalizados aos POIs.

* Para ver a interface do usuário, vá para [https://places.adobe.com](https://places.adobe.com).
* Para começar a usar a interface do usuário, consulte [Introdução](/help/getting-started.md).

#### Extensão de locais

Usando a Extensão de locais, você pode adicionar as bibliotecas do Serviço de locais ao seu aplicativo móvel e agir de acordo com seus POIs. Usando o construtor de regras no Experience Platform Launch, é possível acionar ações para serem acionadas quando os usuários entram e saem dos POIs.

Na extensão Locais:

* Você pode escolher quais bibliotecas POI devem ser incluídas no aplicativo.
* Eventos de regras que acionam na entrada ou saída do POI.
* Crie elementos de dados que apontem para o POI atual do usuário.

For more information about the Places extension, see [Places extension](/help/places-ext-aep-sdks/places-extension/places-extension.md).

#### Coloca APIs

Você pode usar as APIs do Places para fazer o seguinte:

* Permita que os desenvolvedores preencham e atualizem sua lista de POIs.
* Crie sua própria interface do usuário ou integre-a a um banco de dados de POI existente.
* Use os pontos de extremidade de lote da API Locais para fazer uma importação em massa de POIs.

   Você pode usar o utilitário Python fornecido para concluir a importação em massa.

Para obter mais informações sobre as APIs do Places, consulte API [do serviço](/help/web-service-api/places-web-services.md)da Web.

### Em breve

#### Integração do Analytics

A extensão do Analytics está sendo atualizada para adicionar automaticamente dados de contexto de localização do banco de dados do Places Service a todas as chamadas de saída do Analytics quando um usuário está em um POI (Chamadas Passivas). Essa atualização também permitirá que a criação de regras acione chamadas de rastreamento do Analytics diretamente na entrada ou saída do POI (chamadas ativas).
