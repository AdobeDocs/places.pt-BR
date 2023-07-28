---
title: Notas de versão
description: Notas de versão do Places Service.
exl-id: 76da9548-4e32-4b23-9a15-7012973915f3
source-git-commit: d5c216aebd99ffef01c37c17c62576835b52438b
workflow-type: tm+mt
source-wordcount: '1490'
ht-degree: 2%

---

# Notas de versão {#release-notes}

## 8 de julho de 2020

* **Extensões do Places e do Places Monitor**

   * As extensões do Places e do Places Monitor foram adicionadas para [Aplicativos nativos React](https://aep-sdks.gitbook.io/docs/resources/upgrading-to-aep/current-sdk-versions#react-native)
   * As extensões do Places e do Places Monitor foram adicionadas para [aplicativos Cordova](https://aep-sdks.gitbook.io/docs/resources/upgrading-to-aep/current-sdk-versions#cordova)
   * Para obter mais informações, consulte: [Utilização da extensão Places](https://experienceleague.adobe.com/docs/places/using/places-ext-aep-sdks/places-extension/places-extension.html)


## 12 de maio de 2020

* **Places Service**

   * Importação de POIs em massa de um arquivo CSV usando o botão &quot;Importar POIs&quot;
   * Selecione vários POIs e edite em massa ou adicione valores de metadados

## 6 de maio de 2020

* **PlacesMonitor 2.2.1**

   * **Android**

      * Melhoria no registro

## 5 de maio de 2020


* **PlacesMonitor 2.1.3**

   * **iOS**

      * Melhoria no registro

## 20 de fevereiro de 2020

* **ACPLOICES 1.3.1 (iOS)**

   * A extensão do Places agora relata informações de versão ao hub de eventos no SDK principal.
   * As informações de associação do POI do dispositivo agora têm um tempo de vida padrão de uma hora a partir do momento em que são coletadas. Para obter mais informações, consulte [Modificação da duração da vida da associação de Places](places-ext-aep-sdks/places-extension/places-extension.md#places-ttl)


* **Places 1.4.1 (Android)**

   * A extensão do Places agora relata informações de versão ao hub de eventos no SDK principal.
   * As informações de associação do POI do dispositivo agora têm um tempo de vida padrão de uma hora a partir do momento em que são coletadas. Para obter mais informações, consulte [Modificação da duração da vida da associação de Places](places-ext-aep-sdks/places-extension/places-extension.md#places-ttl)

## 27 de janeiro de 2020

* **PlacesMonitor 2.2.0**

   * **Android**

      * Chame a nova API do Places para coletar o status de autorização de localização quando o aplicativo for iniciado e quando a autorização for alterada enquanto o aplicativo estiver em execução.
      * Adição da API setRequestLocationPermission e da API setLocationPermission obsoleta.

## 9 de janeiro de 2020

* **Places 1.4.0**

   * **Android**

      * Adição de uma nova API, `setAuthorizationStatus`, para definir o status de autorização do dispositivo para Serviços de Places. O valor é armazenado e usado no estado compartilhado Places.

## 4 de dezembro de 2019

* **PlacesMonitor 2.1.2**

   * **iOS**

      * Chame a API de locais para coletar CLAuthorizationStatus do dispositivo quando ele for alterado.

## 3 de dezembro de 2019

* **ACPLOCES 1.3.0**

   * **iOS**

      * Adição de uma nova API, `setAuthorizationStatus`, para definir o status de autorização do dispositivo para Serviços de Places. O valor é armazenado e usado no estado compartilhado Places.

## 25 de novembro de 2019

* **PlacesMonitor 2.1.1**

   * **iOS**

      * Correção de declarações de importação para projetos Cocoapods usando várias opções de projetos pod.

## 22 de novembro de 2019

* **PlacesMonitor 2.1.1**

   * **Android**

      * O Monitor agora reconhece a inicialização de um dispositivo Android e, se necessário, registra as geofences novamente no SO com base na localização atual do dispositivo.
      * Correção de uma condição de corrida que, às vezes, fazia com que eventos de entrada/saída fossem descartados.

## 9 de outubro de 2019

* **PlacesMonitor 2.1.0**

   * **iOS**

      * Adição de uma nova API, `setRequestAuthorizationLevel`, para definir o tipo de solicitação de autorização de localização para a qual o usuário será solicitado.


   * **Android**

      * Adição de uma nova API, `setLocationPermission`, para definir o tipo de solicitação de permissão de localização para a qual o usuário será solicitado.
      * O Places Monitor agora é compatível com o Android 10.

## 8 de agosto de 2019

As seguintes atualizações foram feitas nesta versão:

### Atualizações da interface

Esta é uma lista das atualizações na interface do usuário do Places:

#### Novos recursos

* Adição de uma nova exibição de lista que mostra POIs sem o mapa.
* Adicionadas opções de filtragem de POI para a cidade, o estado, o país e os metadados.
* A primeira biblioteca em uma organização é criada automaticamente.
* Adição da classificação de POI à Exibição de lista.

#### Atualizações da interface

* A lista e o painel de detalhes foram movidos para o lado direito da interface do usuário.
* Adição de um novo painel de pesquisa na parte superior da interface do usuário do.
* Se houver apenas uma biblioteca, ela será selecionada automaticamente quando você criar um POI.
* Gerenciamento de biblioteca movido para uma janela pop-up.
* Adição de uma contagem de POI ao lado dos filtros.

## 6 de agosto de 2019

As seguintes atualizações foram feitas nesta versão:

### Extensão do Monitor Launch 2.0.0

* Atualização das instruções de instalação do Android e do iOS para o Places Monitor 2.0.

## 31 de julho de 2019

As seguintes atualizações foram feitas nesta versão:

### Places Monitor 2.0.0

* O status de monitoramento agora é mantido entre inicializações.
* A manipulação do retorno de chamada, que resultou de uma solicitação de permissão de local, não requer mais que você estenda PlacesActivity.
* Uma API existente foi alterada, permitindo que os desenvolvedores limpem todos os dados do Places do dispositivo:

  API antiga: `public static void stop();`

  Nova API: `public static void stop (final boolean clearData);`

* Atualização do uso do `getNearbyPointsOfInterest` API para lidar com cenários de erro com mais eficiência.

## 25 de julho de 2019

As seguintes atualizações foram feitas nesta versão:

### ACPLacesMonitor 2.0.0

* Para apagar todos os dados de Places do dispositivo,

  no ACPacesMonitor, uma API existente foi substituída `+ (void) stop;` com`+ (void) stop: (BOOL) clearData;`.

* Atualização do uso dos Locais ACC `getNearbyPointsOfInterest` API para lidar com cenários de erro com mais eficiência.

## 22 de julho de 2019

As seguintes atualizações foram feitas nesta versão:

### Android Places 1.3.0

* Adição de uma nova API que limpa todos os dados relacionados ao Places do estado compartilhado, da memória no aplicativo e da preferência compartilhada.
* Correção de um problema em que o estado compartilhado não era atualizado durante a inicialização do aplicativo.
* Correção de um erro em que `getNearbyPointsOfInterest` o retorno de chamada estava retornando o código de erro `SERVER_RESPONSE_ERROR instead of CONNECTIVITY_ERROR` sem acesso à Internet.
* `getNearbyPointsOfInterest` A API (sem o errorCallback) terá a `successCallback` chamado com lista de poi vazia, em caso de erro ao recuperar os pontos de interesse próximos.

## 19 de julho de 2019

As seguintes atualizações foram feitas nesta versão:

**iOS Places 1.2.0**

Adição de uma nova API que limpa todos os dados relacionados ao Places do estado compartilhado, da memória no aplicativo e `NSUserDefaults`.

## 25 de junho de 2019

As seguintes atualizações foram feitas nesta versão:

**iOS Places Monitor 1.0.2**

* Melhorias na qualidade de vida, incluindo melhor documentação no código e registro.

## 17 de junho de 2019

As seguintes atualizações foram feitas nesta versão:

**iOS Places 1.1.0**

* Adição de uma nova API para retornar um código de erro quando houver uma falha na recuperação de locais próximos.
* Quando o status de privacidade for alterado para opt-out, todos os dados relacionados a Places agora serão apagados do dispositivo.
* Correção de um problema que, após uma primeira inicialização, às vezes fazia com que os eventos do Places fossem perdidos devido a más condições de rede.
* Correção de um problema em que, ao processar eventos de entrada de POI em rápida sucessão, a substituição de token por meio do Mecanismo de regras às vezes referenciava o POI incorreto.

## 30 de maio de 2019

**Android Places Monitor 1.0.1**

* Correção de um problema que impedia um evento de entrada para POIs quando o monitoramento do Places era iniciado.

## 28 de maio de 2019

Correção dos seguintes problemas na interface do usuário do Places:

* Atualização do Alternador de soluções no Places para alinhar-se ao restante do Experience Cloud.
* Correção de um problema em que a classificação era salva nas instâncias em que nenhuma alteração de classificação era feita.
* O raio mínimo permitido na interface do usuário foi aumentado para 10 metros.
* Correção de um problema em que, ao excluir todos os números no campo, o campo de raio era redefinido para 20 metros.

## 17 de maio de 2019

As seguintes atualizações foram feitas nesta versão:

**Android Places 1.2.0**

* Adição de uma nova API para processar um Geofence individual.
* Correção de erros para evitar vários eventos de entrada consecutivos.

**Android Places Monitor 1.0.0**

Versão inicial do Places Monitor para Android.

O Places Monitor gerencia as APIs de localização no nível do sistema operacional e se comunica diretamente com a extensão do Places. Com ambas as extensões instaladas, os clientes podem ter monitoramento de região pronto para uso em seus aplicativos.
Para obter mais informações sobre o Places Monitor, clique aqui.


## 2 de maio de 2019

**Android Places 1.1.0**

* Introdução de uma nova API para getNearByPlaces, que tem um errorCallback e é chamada com um errorCode que indica o motivo do erro.
* A extensão Places agora enfileira os eventos até que uma configuração seja obtida.
* Adição de suporte para configurações com reconhecimento de ambiente.
* Correção de erros : corrigiu as chaves para os eventos de entrada/saída da região
* O armazenamento do último local conhecido agora respeita adequadamente o status de privacidade do usuário


## 9 de abril de 2019

As seguintes atualizações foram feitas nesta versão:

**iOS Places Monitor 1.0.1**

* Adição da cobertura completa do teste de unidade.
* Integração CI (CircleCI)
* Integração de cobertura de código (codecov)

## 25 de março de 2019

iOS Places Monitor 1.0.0

Versão inicial do Places Monitor para iOS.

O Places Monitor gerencia as APIs de localização no nível do sistema operacional e se comunica diretamente com a extensão do Places. Com ambas as extensões instaladas, os clientes podem ter monitoramento de região pronto para uso em seus aplicativos.

## 28 de fevereiro de 2019

### Versão Beta

Esta é a primeira versão do Places Service, um conjunto de ferramentas que permite aos clientes enriquecer as experiências de seus usuários com dados de localização reais. Para a primeira versão, nosso principal caso de uso é permitir que aplicativos móveis recuperem dados de localização personalizados e atuem sobre esses dados por meio do Adobe Experience Platform Launch.

### Recursos principais

Estes são os principais recursos nesta versão:

#### Interface do usuário do Places Service

Lançamos uma interface do usuário de gerenciamento na qual você pode visualizar e gerenciar seus pontos de interesse (POIs). Você também pode organizar seus POIs em bibliotecas. Além dos metadados padrão, como cidade, estado e categoria, também oferecemos suporte à capacidade de adicionar metadados personalizados aos POIs.

* Para ver a interface do usuário do, acesse [https://places.adobe.com](https://places.adobe.com).
* Para começar a usar a interface do usuário, consulte [Introdução](/help/getting-started.md).

#### Extensão do Places

Usando a Extensão Places, você pode adicionar suas bibliotecas do Places Service ao aplicativo móvel e agir de acordo com seus POIs. Usando o construtor de regras no Experience Platform Launch, você pode acionar ações para serem acionadas quando os usuários entrarem e saírem dos POIs.

Na extensão Places:

* Você pode escolher quais bibliotecas POI incluir no aplicativo.
* Eventos de regra que acionam na entrada ou saída do POI.
* Crie elementos de dados que apontem para o POI atual do usuário.

Para obter mais informações sobre a extensão Places, consulte [Extensão do Places](/help/places-ext-aep-sdks/places-extension/places-extension.md).

#### APIs do Places

Você pode usar as APIs do Places para fazer o seguinte:

* Permite que os desenvolvedores preencham e atualizem sua lista de POIs.
* Crie sua própria interface do usuário ou integre a um banco de dados de POI existente.
* Use os endpoints em lote da API do Places para fazer uma importação em massa de POIs.

  Você pode usar o utilitário Python fornecido para concluir a importação em massa.

Para obter mais informações sobre as APIs do Places, consulte [API do serviço Web](/help/web-service-api/places-web-services.md).

### Em breve

#### Integração do Analytics

A extensão do Analytics está sendo atualizada para adicionar automaticamente dados de contexto de localização do banco de dados do Places Service a todas as chamadas de saída do Analytics quando um usuário estiver em um POI (chamadas passivas). Essa atualização também permitirá a criação de regras para acionar chamadas de rastreamento do Analytics diretamente na entrada ou saída do POI (chamadas ativas).
