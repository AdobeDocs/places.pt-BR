---
title: Excluir um POI
description: Exclua um POI usando as APIs REST do local.
translation-type: tm+mt
source-git-commit: 8a84fe2dc5a0efe94ce3121e589524e3c7a80c5e

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

## Resposta de exemplo

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
>Substitua `<POIID>`, `<API KEY>`e `<TOKEN>`por `<ORGID>` valores reais.

