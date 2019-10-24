---
title: Notas de versão para os locais da plataforma Adobe Experience
seo-title: Notas de versão do Adobe Experience Platform Places.
description: Notas de versão do Adobe Experience Platform Places.
seo-description: Notas de versão do Adobe Experience Platform Places.
translation-type: tm+mt
source-git-commit: 9fc484fd44c74ad77255668e4fbd7bc1642932e2

---


# Notas de versão {#release-notes}

Estas são as notas de versão do Adobe Experience Platform Places (Places):

## 9 de outubro de 2019

* **PlacesMonitor 2.1.0**

   * **iOS**

      * Adicionada uma nova API `setRequestAuthorizationLevel`, para definir o tipo de solicitação de autorização de localização para a qual o usuário será solicitado.
   * **Android**

      * Adicionada uma nova API `setLocationPermission`, para definir o tipo de solicitação de permissão de localização para a qual o usuário será solicitado.
      * O Monitor de locais agora é compatível com Android 10.



## 8 de ago de 2019

As seguintes atualizações foram feitas nesta versão:

### Atualizações da interface do usuário do Places

Esta é uma lista de atualizações da interface do usuário do Places:

#### Novos recursos

* Adicionada uma nova exibição de lista que mostra POIs sem o mapa.
* Adicionadas opções de filtragem de POI para a cidade, o estado, o país e os metadados.
* A primeira biblioteca em uma organização é criada automaticamente.
* Adição da classificação POI à Exibição de lista.

#### Atualizações da interface

* Painel de detalhes e lista movido para o lado direito da interface do usuário.
* Adicionado um novo painel de pesquisa na parte superior da interface do usuário.
* Se apenas uma biblioteca estiver presente, essa biblioteca será selecionada automaticamente quando você criar um POI.
* Gerenciamento de biblioteca movido para uma janela pop-up.
* Foi adicionada uma contagem de POI ao lado dos filtros.

## 6 de ago de 2019

As seguintes atualizações foram feitas nesta versão:

### Places Monitor Launch Extension 2.0.0

* Atualizadas as instruções de instalação do Android e do iOS para o Places Monitor 2.0.

## 31 de julho de 2019

As seguintes atualizações foram feitas nesta versão:

### Places Monitor 2.0.0

* O status do monitoramento agora é persistente entre inicializações.
* A manipulação do retorno de chamada, que resultou de uma solicitação de permissão de local, não exige mais que você estenda PlacesActivity.
* Alteração de uma API existente, permitindo que os desenvolvedores limpassem todos os dados do Local do dispositivo:

   API antiga: `public static void stop();`

   Nova API: `public static void stop (final boolean clearData);`

* Atualização do uso da API Locais `getNearbyPointsOfInterest` para lidar com cenários de erro com mais eficiência.

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
* Correção de um problema em que o estado compartilhado não era atualizado durante o início do aplicativo.
* Correção de um bug no qual `getNearbyPointsOfInterest` o retorno de chamada retornava o código de erro `SERVER_RESPONSE_ERROR instead of CONNECTIVITY_ERROR` em nenhuma Internet.
* `getNearbyPointsOfInterest` A API (sem errorCallback) terá a lista `successCallback` chamada com poi vazio, em caso de erro ao recuperar os pontos de interesse próximos.

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
* Correção de um problema que, após uma primeira inicialização, às vezes fazia com que os eventos do Places fossem perdidos devido a condições de rede ruins.
* Correção de um problema em que, ao processar eventos de entrada POI em sucessão rápida, a substituição de token via Mecanismo de regras às vezes referenciava o POI incorreto.

## 30 de maio de 2019 (locais)

**Android Places Monitor 1.0.1**

* Correção de um problema que impedia um evento de entrada para POIs quando o monitoramento de Locais era iniciado.

## 28 de maio de 2019

Correção dos seguintes problemas na interface do usuário do Places:

* Atualização do Alternador de soluções em locais para alinhar com o restante da Experience Cloud.
* Correção de um problema em que a classificação era salva em instâncias em que nenhuma alteração de classificação era feita.
* O raio mínimo permitido na interface do usuário foi aumentado para 10 metros.
* Correção de um problema em que, se todos os números do campo forem excluídos, o campo de raio redefinirá 20 metros.

## 17 de maio de 2019 (locais)

As seguintes atualizações foram feitas nesta versão:

**Android Places 1.1.0**

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
* Adicionado suporte para configurações compatíveis com o ambiente.
* Correção de erros: corrigidas as teclas dos eventos de entrada/saída da região
* O armazenamento do último local conhecido agora respeita corretamente o status de privacidade do usuário


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

Esta é a primeira versão do Places, um conjunto de ferramentas que permite aos clientes enriquecer as experiências dos usuários com dados de localização reais. Na primeira versão, nosso caso de uso principal é permitir que aplicativos móveis recuperem dados de localização personalizados e atuem sobre esses dados por meio do Adobe Experience Platform Launch.

### Recursos principais

Estes são os principais recursos desta versão:

#### Interface do usuário do Places

Lançamos uma interface de usuário de gerenciamento na qual você pode visualizar e gerenciar seus pontos de interesse (POIs). Você também pode organizar seus POIs em bibliotecas. Além dos metadados padrão, como cidade, estado e categoria, também oferecemos suporte à capacidade de adicionar metadados personalizados aos POIs.

* Para ver a interface do usuário do Places, vá para [https://places.adobe.com](https://places.adobe.com).
* Para começar a usar a interface do usuário do Places, consulte [Introdução](/help/getting-started.md).

#### Extensão de locais

Usando a Extensão de locais, você pode adicionar as bibliotecas de locais ao seu aplicativo móvel e agir conforme os POIs deles. Usando o construtor de regras no Experience Platform Launch, é possível acionar ações para serem acionadas quando os usuários entram e saem dos POIs.

Na extensão Locais:

* Você pode escolher quais bibliotecas POI serão incluídas no aplicativo.
* Eventos de regras que acionam na entrada ou saída do POI.
* Crie elementos de dados que apontem para o POI atual do usuário.

Para obter mais informações sobre a extensão Locais, consulte a extensão [](/help/places-ext-aep-sdks/places-extension/places-extension.md)Locais.

#### Coloca APIs

Você pode usar as APIs do Places para fazer o seguinte:

* Permita que os desenvolvedores preencham e atualizem sua lista de POIs.
* Crie sua própria interface do usuário ou integre-a a um banco de dados de POI existente.
* Use os pontos finais de lote da API Locais para fazer uma importação em massa de POIs.

   Um utilitário python é fornecido com as APIs.

Para obter mais informações sobre as APIs do Places, consulte Serviços [da Web do](/help/places-web-service-api/places-web-services.md)Places.

### Em breve

#### Integração do Analytics

A extensão do Analytics está sendo atualizada para adicionar automaticamente dados de contexto de localização do seu banco de dados do Places a todas as chamadas de saída do Analytics quando um usuário está em um POI (Chamadas Passivas). Essa atualização também permitirá que a criação de regras acione chamadas de rastreamento do Analytics diretamente na entrada ou saída do POI (chamadas ativas).

