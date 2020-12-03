---
title: Uso de metadados com POIs
description: Esta seção fornece informações e estratégias sobre como usar metadados com POIs.
translation-type: tm+mt
source-git-commit: 0ca2162f113fba6bfbd54443109068b1a506762b
workflow-type: tm+mt
source-wordcount: '293'
ht-degree: 0%

---


# Estratégias para usar metadados com POIs {#using-metadata-pois}

No Places Service, ao criar um novo POI, os únicos elementos necessários são Nome, Raio, Latitude e Longitude. Para obter mais informações sobre como criar um POI, consulte [Criar um POI](/help/poi-mgmt-ui/create-a-poi-ui.md). No entanto, se você estiver inserindo apenas as informações mínimas, perderá uma oportunidade de criar valor adicional.

Os metadados POI podem ser usados de várias maneiras. Do ponto de vista do gerenciamento de POI, a adição de valores de metadados pode ajudar a pesquisar ou filtrar uma lista de milhares de POIs em potencial. A criação de metadados para os principais atributos relacionados a um POI pode gerar valor em workflows downstream. Por exemplo, uma cadeia de hotéis que cria POIs para cada propriedade pode querer incluir metadados como se a propriedade do hotel tivesse um pool ou não, ou um restaurante e bar, ou se eles tivessem uma instalação de ginástica. Esses metadados podem ser incluídos como dados de contexto no Analytics e também podem ser usados para ofertas ou mensagens direcionadas.

## Coloca os metadados do serviço no Launch

No Experience Platform Launch, você pode criar elementos de dados para cada campo de metadados do Serviço de Locais que seja importante para fins de rastreamento ou mensagens.

![elemento de dados para o ginásio](/help/assets/gymfacility.png)

Em seguida, é possível criar uma ação com a extensão do Analytics para criar uma nova ocorrência que inclua os metadados que você deseja como dados de contexto.

![ação a favor da academia](/help/assets/Analytics-gym.png)

## Mensagens no aplicativo no Adobe Campaign

Os metadados podem ser usados como filtro para notificações locais e mensagens no aplicativo definidas no Adobe Campaign Standard. O uso de metadados como filtro oferece a oportunidade de criar uma mensagem mais relevante que seja contextual para o local real.

![filtrar notificações locais e mensagens no aplicativo no ACS](/help/assets/ACS_gym_metadata.png)