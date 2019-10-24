---
title: Locais da plataforma Adobe Experience
seo-title: Locais da plataforma Adobe Experience
description: 'Os locais são um contexto importante para entender o envolvimento dos usuários móveis. Ao usar esse contexto, os desenvolvedores de aplicativos móveis podem melhorar o design do aplicativo e torná-lo uma experiência mais personalizada e envolvente. '
seo-description: 'Os locais são um contexto importante para entender o envolvimento dos usuários móveis. Ao usar esse contexto, os desenvolvedores de aplicativos móveis podem melhorar o design do aplicativo e torná-lo uma experiência mais personalizada e envolvente. '
translation-type: tm+mt
source-git-commit: 9fc484fd44c74ad77255668e4fbd7bc1642932e2

---


# Visão geral {#home}

O Adobe Experience Platform Places (Places) é um contexto importante para entender o envolvimento de usuários móveis. Ao usar esse contexto, os desenvolvedores de aplicativos móveis podem melhorar o design do aplicativo e torná-lo uma experiência mais personalizada e envolvente. O Places é um serviço de localização geográfica que permite aos desenvolvedores de aplicativos móveis compreender o contexto de localização usando interfaces SDK avançadas e fáceis de usar acompanhadas por um banco de dados flexível de pontos de interesse (POIs).

Os locais permitem que você atinja o seguinte:

* Crie e gerencie um banco de dados com POIs que podem ser aproveitados com outras soluções da Adobe Experience Cloud.
* Anexe metadados personalizados aos POIs para torná-los mais ricos e mais significativos ao especificar atributos adicionais.
* Visualize os POIs em um mapa para entender facilmente o contexto espacial e adicionar/editar atributos de metadados.
* Configure o SDK no Adobe Experience Platform Launch para definir suas regras acionadas por localização e condições baseadas em metadados.
* Reduza o código que você precisa gravar no local de um dispositivo de monitor e use o monitor de localização da Adobe para acionar automaticamente as regras específicas de localização.

Isso permitirá que você tome ações dos sinais de localização em tempo real, quando e onde isso importa. O contexto correto fornece uma experiência de envolvimento móvel mais enriquecedora.

Estas são algumas das maneiras de usar os Locais:

* Envie uma notificação em tempo real quando alguém entrar em um POI, *"Ei...bem-vindo ao estádio."*
* Analise o tráfego de pés de suas próprias lojas em relação às lojas concorrentes.
* Segmentar um público-alvo com base no comportamento offline usando perfis de público-alvo com contexto de localização.
* Direcione um usuário com uma experiência na loja quando relevante.

## Adicionar um espaço reservado para o vídeo "Places intro" do Brandon

## Casos de uso de locais

Melhore esta seção com

## Componentes do Places

Os locais são compostos pelos seguintes componentes:

* **Serviço Web de locais**

   Você pode criar e gerenciar POIs usando as APIs REST do Places. Para obter mais informações sobre REST APIs, consulte [Gerenciar bibliotecas](/help/places-web-service-api/api-usage/manage-libraries/manage-libraries.md) e [gerenciar POIs](/help/places-web-service-api/api-usage/manage-pois/manage-pois.md).

* **Interface do usuário do Places**

   Visualize POIs em um mapa para entender o contexto espacial e adicionar/editar POIs e seus metadados personalizados.

* **Places SDK**

   A interface da API móvel de várias plataformas para integrar o contexto de localização em seus aplicativos móveis. Para obter mais informações sobre os SDKs, consulte a extensão [](/help/places-ext-aep-sdks/places-extension/places-extension.md)Locais.

* **Regras de locais**

   As regras de lançamento geo-inteligentes que permitem acionar ações com eventos de entrada e saída. As regras também permitem usar atributos geográficos em condições para personalizar a experiência.

* **Monitor de locais**

   O SDK móvel multiplataforma que pode ser incorporado no aplicativo móvel para monitorar automaticamente as alterações de localização do usuário e acionar as regras de Locais. Para obter mais informações, consulte a extensão [do Monitor de](/help/places-ext-aep-sdks/places-monitor-extension/places-monitor-extension.md)locais.

## Terminologia

Estes são alguns termos comuns usados nesta documentação:

* Um **ponto de interesse (POI)** é uma localização geográfica que interessa à sua organização.

   É possível definir POIs com atributos como nome, raio, endereço, categoria e tags de metadados.

* Uma **geofence** é um tipo de POI.

   Este tipo de POI é um limite geográfico virtual definido pelas coordenadas de latitude e longitude.

* Um **beacon** é um tipo de POI.

   Este tipo de POI é um dispositivo físico que representa um local emitindo um sinal de bluetooth de baixa energia. O suporte a beacons será lançado em uma versão futura.

* Uma **biblioteca** é uma coleção de POIs, que são agrupados para anexar facilmente regras a um conjunto em vez de um POI.

* Uma **extensão** do SDK é a extensão do Experience Platform Launch necessária para integrar o SDK do Places nos aplicativos móveis.

   A extensão usada com outros SDKs móveis para adicionar o contexto de localização às suas experiências.

* Uma **organização** é a entidade da Adobe que identifica sua empresa na Adobe Experience Cloud.

   Normalmente, uma organização é o nome da sua empresa. No entanto, uma empresa pode ter mais de uma organização. O administrador da organização pode configurar grupos e usuários e configurar a funcionalidade de logon único.

* A **orgID** é a ID que representa sua organização na Adobe Experience Platform.

   Para obter mais informações, consulte [Localizando sua orgID](https://forums.adobe.com/thread/2339895).

* The **Experience Cloud ID** service provides a universal, persistent ID that identifies your visitors across all the solutions in the Experience Cloud.

   For more information, see [Overview](https://docs.adobe.com/content/help/en/id-service/using/intro/overview.html).