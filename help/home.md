---
title: Serviço de Places
description: 'O Serviço de Locais é um contexto importante para entender o envolvimento de usuários móveis. Ao usar esse contexto, os desenvolvedores de aplicativos móveis podem aprimorar o design do aplicativo e torná-lo uma experiência mais personalizada e envolvente. '
translation-type: tm+mt
source-git-commit: 05b4d29aa7925f7a43e70c644e3cb88045cbe446
workflow-type: tm+mt
source-wordcount: '708'
ht-degree: 10%

---


# Serviço de Places {#home}

![&quot;Serviço de Places&quot;](/help/assets/places-service-header.png)

A localização é um contexto importante para entender e interagir com usuários móveis. Ao usar esse contexto, os desenvolvedores de aplicativos móveis podem aprimorar o design do aplicativo e torná-lo uma experiência mais personalizada e envolvente.

O Places Service, anteriormente conhecido como Adobe Experience Platform Location Service, é um serviço de localização geográfica que permite que aplicativos móveis com detecção de localização compreendam o contexto de localização usando interfaces SDK avançadas e fáceis de usar acompanhadas por um banco de dados flexível de pontos de interesse (POIs).

O Serviço de Locais permite que você atinja o seguinte:

* Crie e gerencie um banco de dados de POIs que pode ser aproveitado com outras soluções da Adobe Experience Cloud.
* Anexe metadados personalizados aos POIs para torná-los mais ricos e mais significativos ao especificar atributos adicionais.
* Visualize os POIs em um mapa para entender facilmente o contexto espacial e adicionar/editar atributos de metadados.
* Configure o SDK no Adobe Experience Platform Launch para definir suas regras acionadas por localização e condições baseadas em metadados.
* Reduza o código que você precisa gravar para monitorar a localização de um dispositivo e use a extensão Locais para acionar automaticamente as regras específicas de localização.

Isso permitirá que você tome ações dos sinais de localização em tempo real, quando e onde isso importa. O contexto correto fornece uma experiência de envolvimento móvel mais enriquecedora.

Estas são algumas das maneiras de usar os Locais:

* Envie uma notificação em tempo real quando alguém entrar em um POI, *&quot;Ei...bem-vindos ao estádio.&quot;*
* Analise o tráfego de pés de suas próprias lojas em relação às lojas de concorrentes.
* Segmente uma audiência com base no comportamento offline usando perfis de audiência com contexto de localização.
* Público alvo um usuário com uma experiência na loja, quando relevante.

## Componentes do Places Service

O Serviço de Locais inclui os seguintes componentes:

* **Serviço Web**

   Você pode criar e gerenciar POIs usando as APIs REST do Places. Para obter mais informações sobre REST APIs, consulte [Gerenciar bibliotecas](/help/web-service-api/api-usage/manage-libraries/manage-libraries.md) e [gerenciar POIs](/help/web-service-api/api-usage/manage-pois/manage-pois.md).

* **Interface de gerenciamento de POI**

   Visualize POIs em um mapa para entender o contexto espacial e adicionar/editar POIs e seus metadados personalizados.

* **Extensão do Places**

   A interface da API móvel de várias plataformas para integrar o contexto de localização em seus aplicativos móveis. Para obter mais informações sobre os SDKs, consulte a extensão [](/help/places-ext-aep-sdks/places-extension/places-extension.md)Locais.

* **Regras de inicialização**

   As regras de lançamento geo-inteligentes que permitem acionar ações com eventos de entrada e saída. As regras também permitem usar atributos geográficos em condições para personalizar a experiência.

* **Extensão do monitor de locais**

   O SDK móvel multiplataforma que pode ser incorporado no aplicativo móvel para monitorar automaticamente as alterações de localização do usuário e acionar as regras de Locais. Para obter mais informações, consulte a extensão [do Monitor de](/help/places-ext-aep-sdks/places-monitor-extension/places-monitor-extension.md)locais.

## Terminologia

Estes são alguns termos comuns usados nesta documentação:

* Um **ponto de interesse (POI)** é uma localização geográfica que interessa à sua organização.

   É possível definir POIs com atributos como nome, raio, endereço, categoria e tags de metadados.

* Uma **geofence** é um tipo de POI.

   Este tipo de POI é um limite geográfico virtual definido pelas coordenadas de latitude e longitude.

* Um **beacon** é um tipo de POI.

   Este tipo de POI é um dispositivo físico que representa um local emitindo um sinal de bluetooth de baixa energia. O suporte a beacons será lançado em uma versão futura.

* Uma **biblioteca** é uma coleção de POIs que são agrupados para atribuir regras facilmente a um conjunto, em vez de um POI.

* Uma **extensão** é a extensão Experience Platform Launch necessária para integrar o SDK do Places nos aplicativos móveis.

   A extensão usada com outros SDKs móveis para adicionar o contexto de localização às suas experiências.

* Uma **organização** é a entidade da Adobe que identifica a empresa na Adobe Experience Cloud.

   Normalmente, uma organização é o seu nome de empresa. No entanto, uma empresa pode ter mais de uma organização. O administrador da organização pode configurar grupos e usuários e configurar a funcionalidade de logon único.

* A **orgID** é a ID que representa a organização na Adobe Experience Platform.

   Para obter mais informações, consulte [Localizando sua orgID](https://forums.adobe.com/thread/2339895).

* The **Experience Cloud ID** service provides a universal, persistent ID that identifies your visitors across all the solutions in the Experience Cloud.

   Para obter mais informações, consulte [Visão geral](https://docs.adobe.com/content/help/pt-BR/id-service/using/intro/overview.html).
