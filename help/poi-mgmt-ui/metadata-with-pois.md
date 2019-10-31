---
title: Uso de metadados com POIs
seo-title: Uso de metadados com POIs
description: Esta seção fornece informações e estratégias sobre como usar metadados com POIs.
seo-description: 'Esta seção fornece informações e estratégias sobre como usar metadados com POIs. '
translation-type: tm+mt
source-git-commit: 6a01c7c2c573baf572fdc27f47f8fc62322cfd02

---


# Estratégias para usar metadados com POIs {#using-metadata-pois}

No Serviço de localização, quando você cria um novo POI, os únicos elementos necessários são Nome, Raio, Latitude e Longitude. Para obter mais informações sobre como criar um POI, consulte [Criar um POI](/help/poi-mgmt-ui/create-a-poi-ui.md). No entanto, se você estiver inserindo apenas as informações mínimas, perderá uma oportunidade de criar valor adicional.

Os metadados de ponto de interesse podem ser usados de várias maneiras. Do ponto de vista do gerenciamento de POI, a adição de valores de metadados pode ajudar a procurar ou filtrar uma lista de milhares de POIs em potencial. A criação de metadados para atributos principais relacionados a um POI pode gerar valor em fluxos de trabalho downstream. Por exemplo, uma cadeia de hotéis que cria POIs para cada propriedade pode querer incluir metadados como se a propriedade do hotel tivesse um pool ou não, ou um restaurante e bar, ou se eles tivessem uma instalação de ginástica. Esses metadados podem ser incluídos como dados de contexto no Analytics e também podem ser usados para ofertas direcionadas ou mensagens.

## Metadados do Serviço de Localização no Launch

No Adobe Experience Platform Launch, você pode criar elementos de dados para cada campo de metadados do Serviço de localização importante para fins de rastreamento ou mensagens.

![elemento de dados para o ginásio](/help/assets/gymfacility.png)

Em seguida, é possível criar uma ação com a extensão do Analytics para criar uma nova ocorrência que inclua os metadados que você deseja como dados de contexto.

![ação a favor da academia](/help/assets/Analytics-gym.png)

## Mensagens no aplicativo no Adobe Campaign

Os metadados podem ser usados como filtro para notificações locais e mensagens no aplicativo definidas no Adobe Campaign Standard. Usar metadados como filtro oferece a oportunidade de criar uma mensagem mais relevante que seja contextual para o local real.

![filtrar notificações locais e mensagens no aplicativo no ACS](/help/assets/ACS_gym_metadata.png)