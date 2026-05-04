---
title: Uso de metadados com POIs
description: Esta seção fornece informações e estratégias sobre como usar metadados com POIs.
exl-id: e669e560-a999-43ff-aeb4-06e6308b0d5c
TQID: https://experienceleague.adobe.com/wTzahAs7MMSv0q-cEhkNObBpALUJXqDXlOcqjitezwY
product_v2:
  - id: d0a3eab4-7b10-4d96-a71e-6c0f8e7b7c87
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
  - id: e43347a8-f2c5-4aa4-8623-6f13875d7e3a
  - id: e55547f1-a1ff-40c6-8978-026e40ab7fa4
  - id: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
feature_v2:
  - id: e08599ea-8888-4294-ba74-3ba0a7762a46
subfeature_v2:
  - id: d2a6cbf4-df32-480f-909e-b42f66dcb9f0
topic_v2:
  - id: a004cc84-67b9-4a33-a3a7-8ec7273ef4dc
  - id: d3cdead0-685a-4489-9250-4bb709942f66
source-git-commit: f962cef761f006c8e7d45b76ba24746e36bdaba6
workflow-type: tm+mt
source-wordcount: 296
ht-degree: 0%

---

# Estratégias para usar metadados com POIs {#using-metadata-pois}

No Places Service, ao criar um novo POI, os únicos elementos necessários são Nome, Raio, Latitude e Longitude. Para obter mais informações sobre como criar um POI, consulte [Criar um POI](/help/poi-mgmt-ui/create-a-poi-ui.md). Se, no entanto, você estiver inserindo apenas as informações mínimas, perderá uma oportunidade de criar valor adicional.

Os metadados de POI podem ser usados de várias maneiras. Do ponto de vista do gerenciamento de POI, a adição de valores de metadados pode ajudar a pesquisar ou filtrar uma lista de milhares de POIs em potencial. A criação de metadados para atributos principais relacionados a um POI pode gerar valor em workflows downstream. Por exemplo, uma cadeia de hotéis que cria POIs para cada propriedade pode querer incluir metadados como se a propriedade do hotel tivesse uma piscina ou não, ou um restaurante e bar, ou se eles tivessem uma instalação de ginástica. Esses metadados podem ser incluídos como dados de contexto no analytics e também podem ser usados para ofertas ou mensagens direcionadas.

## Metadados do serviço de Places no Launch

No Experience Platform Launch, você pode criar elementos de dados para cada campo de metadados do Places Service que é importante para fins de rastreamento ou mensagem.

![elemento de dados para a academia](/help/assets/gymfacility.png)

Em seguida, você pode criar uma ação com a extensão do Analytics para criar uma nova ocorrência que inclua os metadados que deseja como dados de contexto.

![ação para a academia](/help/assets/Analytics-gym.png)

## Mensagens no aplicativo no Adobe Campaign

Os metadados podem ser usados como um filtro para notificações locais e mensagens no aplicativo definidas no Adobe Campaign Standard. Usar metadados como um filtro oferece a oportunidade de criar uma mensagem mais relevante que é contextual ao local real.

![filtrando notificações locais e mensagens no aplicativo no ACS](/help/assets/ACS_gym_metadata.png)
