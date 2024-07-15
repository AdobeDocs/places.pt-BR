---
title: Excluir um POI
description: Exclua um POI usando as APIs REST do Places.
exl-id: 0325eb3b-f9b2-4b21-bed8-e318e8072a69
source-git-commit: 4ab15ded930b31e4e06920af31f37fdfe45df8eb
workflow-type: tm+mt
source-wordcount: '44'
ht-degree: 4%

---

# Excluir um POI {#delete-a-poi}

Um método DELETE que permite excluir um POI.

## Solicitação

```text
DELETE https://api-places.adobe.io/places/placesapi/v1/pois/<POIID>
```

## Cabeçalhos

```text
-H' Content-Type: application/json'  
-H 'Authorization: Bearer <TOKEN>'  
-H 'x-api-key: <API KEY>'  
-H 'x-gw-ims-org-id: <ORGID>'  
-H 'Accept-Language: en-US'
```

## Exemplo de resposta

```text
If successful a Status of "204 No Content" is returned.
```

## comando CURL

Use o seguinte comando CURL para testar a API:

```text
curl -X DELETE 'https://api-places.adobe.io/places/placesapi/v1/pois/<POIID>' -H 'x-api-key: <API KEY>' -H 'Authorization: Bearer <TOKEN>' -H 'x-gw-ims-org-id: <ORGID>'
```

>[!IMPORTANT]
>
>Substitua `<POIID>`, `<API KEY>`, `<TOKEN>` e `<ORGID>` por valores reais.
