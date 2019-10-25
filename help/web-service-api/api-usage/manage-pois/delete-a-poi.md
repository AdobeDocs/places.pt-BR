---
title: Excluir um POI
seo-title: Excluir um POI
description: Exclua um POI usando as APIs REST do local.
seo-description: Exclua um POI usando as APIs REST do local.
translation-type: tm+mt
source-git-commit: 6ae0c8d90cad4c437e1db7f562a0bc9c6b072ce6

---


# Excluir um POI

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

