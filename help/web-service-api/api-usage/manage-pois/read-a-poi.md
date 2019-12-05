---
title: Ler um POI
description: Leia um POI usando as APIs REST do Places.
translation-type: tm+mt
source-git-commit: 5a0705f02c8ecd540506b628371aec45107df7b2

---


# Ler um POI

Um método GET que retorna os detalhes de um POI.

## Solicitação

```text
GET https://api-places.adobe.io/places/placesapi/v1/pois/<POIID>
```

## Cabeçalhos

```text
-H' Content-Type: application/json'  
-H 'Authorization: Bearer <TOKEN>'  
-H 'x-api-key: <API KEY>'  
-H 'x-gw-ims-org-id: <ORGID>'  
-H 'Accept-Language: en-US'
```

## Resposta de exemplo

```text
{
    "id": "66e3c0fb-12fe-4af2-863e-16e0e578d777",
    "name": "Train Station Road",
    "description": "18827",
    "location": {
        "type": "Point",
        "coordinates": [
            -121.902498,
            37.331087
        ]
    },
    "radius": 66,
    "country": "PH",
    "state": "41",
    "city": "Quezon City",
    "street": "No. 10 Train Station Road",
    "category": "",
    "icon": "",
    "color": "",
    "metadata": {
        "ownership": "LS",
        "brand": "Train station"
    },
    "lib_id": "6efd87bc-c9c4-4ff3-9503-051bfbc81777"
}
```

## comando CURL

Use o seguinte comando CURL para testar a API:

```text
curl -X GET 'https://api-places.adobe.io/places/placesapi/v1/pois/<POIID>' -H 'x-api-key: <API KEY>' -H 'Authorization: Bearer <TOKEN>' -H 'x-gw-ims-org-id: <ORGID>'
```

>[!IMPORTANT]
>
>Substitua `<POIID>`, `<API KEY>`e `<TOKEN>`por `<ORIGIN>` valores reais.

