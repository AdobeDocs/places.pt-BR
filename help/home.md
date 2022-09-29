---
title: Serviço de Places
description: O Places Service é um contexto importante para entender o envolvimento dos usuários móveis. Ao usar esse contexto, os desenvolvedores de aplicativos móveis podem aprimorar o design do aplicativo e torná-lo uma experiência mais personalizada e envolvente.
exl-id: 7369176f-c072-437a-9ee3-b463c5ff1d12
source-git-commit: c13da9ea3dc0cd574f2f9a496405867f7d36eae0
workflow-type: tm+mt
source-wordcount: '706'
ht-degree: 10%

---

# Serviço de Places {#home}

A localização é um contexto importante para entender e interagir com usuários móveis. Ao usar esse contexto, os desenvolvedores de aplicativos móveis podem aprimorar o design do aplicativo e torná-lo uma experiência mais personalizada e envolvente.

O Places Service, anteriormente conhecido como Adobe Experience Platform Location Service, é um serviço de localização geográfica que permite que aplicativos móveis com detecção de localização compreendam o contexto de localização usando interfaces SDK avançadas e fáceis de usar acompanhadas por um banco de dados flexível de pontos de interesse (POIs).

O Places Service permite o seguinte:

* Crie e gerencie um banco de dados de POIs que podem ser aproveitados com outras soluções da Adobe Experience Cloud.
* Anexe metadados personalizados aos POIs para torná-los mais ricos e significativos ao especificar atributos adicionais.
* Visualize os POIs em um mapa para entender facilmente o contexto espacial e adicionar/editar atributos de metadados.
* Configure o SDK no Adobe Experience Platform Launch para definir suas regras acionadas por localização e condições baseadas em metadados.
* Reduza o código que você precisa gravar para monitorar a localização de um dispositivo e usar a extensão Places para acionar automaticamente as regras específicas da localização.

Isso permitirá que você tome ações de sinais de localização em tempo real, quando e onde isso importa. O contexto adequado fornece uma experiência de engajamento móvel mais enriquecedora.

Estas são algumas das maneiras de usar o Places:

* Enviar uma notificação em tempo real quando alguém inserir um POI, *&quot;Ei...bem-vindos ao estádio.&quot;*
* Analise o tráfego de pedestres de suas próprias lojas em relação às lojas de concorrentes.
* Segmente um público com base no comportamento offline usando perfis de público-alvo com contexto de localização.
* Direcione um usuário com uma experiência na loja, quando relevante.

## Componentes do Places Service

O Places Service inclui os seguintes componentes:

* **Serviço Web**

   Você pode criar e gerenciar POIs usando as APIs REST do Places. Para obter mais informações sobre as REST APIs, consulte [Gerenciar bibliotecas](/help/web-service-api/api-usage/manage-libraries/manage-libraries.md) e [Gerenciar POIs](/help/web-service-api/api-usage/manage-pois/manage-pois.md).

* **Interface de gerenciamento de POI**

   Visualize POIs em um mapa para entender o contexto espacial e adicionar/editar POIs e seus metadados personalizados.

* **Extensão do Places**

   A interface da API móvel multiplataforma para integrar o contexto de localização em seus aplicativos móveis. Para obter mais informações sobre os SDKs, consulte [Extensão do Places](/help/places-ext-aep-sdks/places-extension/places-extension.md).

* **Regras de lançamento**

   As regras geo-inteligentes do Launch que permitem acionar ações com eventos de entrada e saída. As regras também permitem usar atributos geográficos em condições para personalizar a experiência.

* **Extensão do Places Monitor**

   O SDK móvel multiplataforma que pode ser incorporado no aplicativo móvel para monitorar automaticamente as alterações de localização do usuário e acionar as regras do Places. Para obter mais informações, consulte [Extensão do Places Monitor](/help/places-ext-aep-sdks/places-monitor-extension/places-monitor-extension.md).

## Terminologia

Estes são alguns termos comuns usados nesta documentação:

* A **ponto de interesse (POI)** é uma localização geográfica que interessa à sua organização.

   Você pode definir POIs com atributos como nome, raio, endereço, categoria e tags de metadados.

* A **geofence** é um tipo de POI.

   Esse tipo de POI é um limite geográfico virtual definido pelas coordenadas de latitude e longitude.

* A **beacon** é um tipo de POI.

   Esse tipo de POI é um dispositivo físico que representa um local emitindo um sinal de bluetooth de baixa energia. O suporte a beacons será lançado em uma versão futura.

* Uma **biblioteca** é uma coleção de POIs que são agrupados para atribuir regras facilmente a um conjunto, em vez de um POI.

* Um **extensão** é a extensão do Experience Platform Launch necessária para integrar o SDK do Places em aplicativos móveis.

   A extensão usada com outros SDKs móveis para adicionar contexto de localização às suas experiências.

* Uma **organização** é a entidade da Adobe que identifica a empresa na Adobe Experience Cloud.

   Normalmente, uma organização é o nome da sua empresa. No entanto, uma empresa pode ter mais de uma organização. O administrador da organização pode configurar grupos e usuários e configurar a funcionalidade de logon único.

* A **orgID** é a ID que representa a organização na Adobe Experience Platform.

   Para obter mais informações, consulte [Localização da orgID](https://forums.adobe.com/thread/2339895).

* O **Experience Cloud ID** O serviço fornece uma ID persistente e universal que identifica os visitantes em todas as soluções no Experience Cloud.

   Para obter mais informações, consulte [Visão geral](https://docs.adobe.com/content/help/pt-BR/id-service/using/intro/overview.html).
