---
title: Crie um POI
description: Crie um POI usando as APIs REST do Places.
translation-type: tm+mt
source-git-commit: 8a84fe2dc5a0efe94ce3121e589524e3c7a80c5e

---


# Crie um POI {#create-a-poi}

Um método POST que permite criar um POI.

## Solicitação

```text
POST https://api-places.adobe.io/places/placesapi/v1/pois
```

## Cabeçalhos

```text
-H' Content-Type: application/json'  
-H 'Authorization: Bearer <TOKEN>'  
-H 'x-api-key: <API KEY>'  
-H 'x-gw-ims-org-id: <ORGID>'  
-H 'Accept-Language: en-US'
```

## Corpo

```text
{
  "name": "string",
  "description": "string",
  "location": {
    "type": Point",
    "coordinates": [<LONGITUDE>, <LATITUDE>]
  },
  "radius": radius,
  "country": "string",
  "state": "string",
  "city": "string",
  "street": "string",
  "category": "string",
  "icon": "string",
  "color": "string",
  "metadata": {
          "brand": "string",
          "owndership": "string",
          "Color": "string"
  },
  "lib_id": "{libraryID}"
}
```

## Resposta de exemplo

```text
{
    "id": "66e3c0fb-12fe-4af2-863e-16e0e777d777",
    "name": "New POI",
    "description": "18827",
    "location": {
        "type": "Point",
        "coordinates": [
            -123.000507,
            37.698029
        ]
    },
    "radius": 66,
    "country": "US",
    "state": "CA",
    "city": "Small City",
    "street": "1 Island Road",
    "category": "",
    "icon": "",
    "color": "",
    "metadata": {
        "ownership": "LS",
        "brand": "Island station"
    },
    "lib_id": "6efd87bc-c9c4-4ff3-9503-051bfbc81777"
}
```

## comando CURL

Use o seguinte comando CURL para testar esta API:

```text
curl -X POST 'https://api-places.adobe.io/places/placesapi/v1/pois' -H 'x-api-key: <API KEY>' -H 'Authorization: Bearer <TOKEN>' -H 'x-gw-ims-org-id: <ORGID>' -d '<SINGLEPOIDATA>' -H "Content-Type: application/json"
```

>[!IMPORTANT]
>
>Lembre-se de substituir `<API KEY>`, `<TOKEN>`, &#39;,&#39; e `<SINGLEPOIDATA>` por valores reais.
