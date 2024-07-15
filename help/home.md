---
title: Places Service
description: O Places Service é um contexto importante para entender o envolvimento dos usuários móveis. Ao usar esse contexto, os desenvolvedores de aplicativos móveis podem aprimorar o design do aplicativo e torná-lo uma experiência mais personalizada e envolvente.
exl-id: 7369176f-c072-437a-9ee3-b463c5ff1d12
source-git-commit: e78e3c5ee6623d6cdf2a33c0582667a70283fdc6
workflow-type: tm+mt
source-wordcount: '663'
ht-degree: 9%

---

# Places Service {#home}

A localização é um contexto importante para entender e interagir com os usuários móveis. Ao usar esse contexto, os desenvolvedores de aplicativos móveis podem aprimorar o design do aplicativo e torná-lo uma experiência mais personalizada e envolvente.

O Places Service, anteriormente conhecido como Adobe Experience Platform Location Service, é um serviço de localização geográfica que permite que aplicativos móveis com detecção de localização compreendam o contexto de localização usando interfaces SDK avançadas e fáceis de usar acompanhadas por um banco de dados flexível de pontos de interesse (POIs).

O Places Service permite obter o seguinte:

* Crie e gerencie um banco de dados de POIs que podem ser aproveitados com outras soluções da Adobe Experience Cloud.
* Anexe metadados personalizados aos POIs para torná-los mais ricos e significativos especificando atributos adicionais.
* Visualize os POIs em um mapa para entender facilmente o contexto espacial e adicionar/editar atributos de metadados.
* Configure o SDK no Adobe Experience Platform Launch para definir suas regras acionadas por localização e condições baseadas em metadados.
* Reduza o código que você precisa gravar para monitorar a localização de um dispositivo e use a extensão Places para acionar automaticamente as regras específicas da localização.

Isso permitirá que você execute ações de sinais de localização em tempo real, quando e onde for importante. O contexto certo oferece uma experiência de envolvimento móvel mais enriquecedora.

Estas são algumas das maneiras de usar o Places:

* Envie uma notificação em tempo real quando alguém digitar um POI, *&quot;Ei..bem-vindo ao estádio.&quot;*
* Analise o tráfego de pé de suas próprias lojas em relação às lojas de seus concorrentes.
* Segmente um público com base no comportamento offline usando perfis de público com contexto de localização.
* Direcione um usuário com experiência na loja quando relevante.

## Componentes do Places Service

O Places Service inclui os seguintes componentes:

* **Serviço Web**

  Você pode criar e gerenciar POIs usando as APIs REST do Places. Para obter mais informações sobre as APIs REST, consulte [Gerenciar bibliotecas](/help/web-service-api/api-usage/manage-libraries/manage-libraries.md) e [Gerenciar POIs](/help/web-service-api/api-usage/manage-pois/manage-pois.md).

* **Interface de Gerenciamento de POI**

  Visualize POIs em um mapa para entender o contexto espacial e adicionar/editar POIs e seus metadados personalizados.

* **Extensão do Places**

  A interface da API móvel de várias plataformas para integrar o contexto de localização em seus aplicativos móveis. Para obter mais informações sobre os SDKs, consulte [Extensão do Places](/help/places-ext-aep-sdks/places-extension/places-extension.md).

* **Iniciar regras**

  As regras geo-inteligentes do Launch que permitem acionar ações com eventos de entrada e saída. As regras também permitem usar atributos geográficos em condições para personalizar a experiência.

## Terminologia

Estes são alguns termos comuns usados nesta documentação:

* Um **ponto de interesse (POI)** é uma localização geográfica de interesse de sua organização.

  Você pode definir POIs com atributos como nome, raio, endereço, categoria e tags de metadados.

* **geofence** é um tipo de POI.

  Esse tipo de POI é uma fronteira geográfica virtual definida por coordenadas de latitude e longitude.

* Um **sinal** é um tipo de POI.

  Esse tipo de POI é um dispositivo físico que representa um local ao emitir um sinal bluetooth de baixa energia. O suporte a beacons será lançado em uma versão futura.

* Uma **biblioteca** é uma coleção de POIs que são agrupados para atribuir regras facilmente a um conjunto, em vez de um POI.

* Uma **extensão** é a extensão do Experience Platform Launch necessária para integrar o SDK do Places em seus aplicativos móveis.

  A extensão usada com outros SDKs móveis para adicionar contexto de localização às suas experiências.

* Uma **organização** é a entidade da Adobe que identifica a empresa na Adobe Experience Cloud.

  Normalmente, uma organização é o nome da sua empresa. No entanto, uma empresa pode ter mais de uma organização. O administrador da organização pode configurar grupos e usuários e configurar a funcionalidade de logon único.

* A **orgID** é a ID que representa a organização na Adobe Experience Platform.

  Para obter mais informações, consulte [Localizando sua orgID](https://forums.adobe.com/thread/2339895).

* O serviço **Experience Cloud ID** fornece uma ID persistente e universal que identifica os visitantes em todas as soluções no Experience Cloud.

  Para obter mais informações, consulte [Visão geral](https://experienceleague.adobe.com/docs/id-service/using/intro/overview.html?lang=pt-BR).

