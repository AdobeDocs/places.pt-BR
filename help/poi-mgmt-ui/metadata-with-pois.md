---
title: Uso de metadados com POIs
description: Esta seção fornece informações e estratégias sobre como usar metadados com POIs.
exl-id: e669e560-a999-43ff-aeb4-06e6308b0d5c
source-git-commit: 4ab15ded930b31e4e06920af31f37fdfe45df8eb
workflow-type: tm+mt
source-wordcount: '293'
ht-degree: 0%

---

# Estratégias para usar metadados com POIs {#using-metadata-pois}

No Places Service, ao criar um novo POI, os únicos elementos necessários são Nome, Raio, Latitude e Longitude. Para obter mais informações sobre como criar um POI, consulte [Criar um POI](/help/poi-mgmt-ui/create-a-poi-ui.md). Se, no entanto, você estiver inserindo apenas as informações mínimas, perderá uma oportunidade de criar valor adicional.

Os metadados de POI podem ser usados de várias maneiras. Do ponto de vista do gerenciamento de POI, a adição de valores de metadados pode ajudar a pesquisar ou filtrar uma lista de milhares de POIs em potencial. A criação de metadados para atributos principais relacionados a um POI pode gerar valor em workflows downstream. Por exemplo, uma cadeia de hotéis que cria POIs para cada propriedade pode querer incluir metadados como se a propriedade do hotel tivesse uma piscina ou não, ou um restaurante e bar, ou se eles tivessem uma instalação de ginástica. Esses metadados podem ser incluídos como dados de contexto no analytics e também podem ser usados para ofertas ou mensagens direcionadas.

## Metadados do serviço de Places no Launch

No Experience Platform Launch, você pode criar elementos de dados para cada campo de metadados do Serviço do Places que é importante para fins de rastreamento ou mensagem.

![elemento de dados para as instalações do ginásio](/help/assets/gymfacility.png)

Em seguida, você pode criar uma ação com a extensão do Analytics para criar uma nova ocorrência que inclua os metadados que deseja como dados de contexto.

![ação para a instalação de ginástica](/help/assets/Analytics-gym.png)

## Mensagens no aplicativo no Adobe Campaign

Os metadados podem ser usados como um filtro para notificações locais e mensagens no aplicativo definidas no Adobe Campaign Standard. Usar metadados como um filtro oferece a oportunidade de criar uma mensagem mais relevante que é contextual ao local real.

![filtragem de notificações locais e mensagens no aplicativo no ACS](/help/assets/ACS_gym_metadata.png)
