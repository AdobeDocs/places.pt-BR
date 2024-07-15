---
title: Excluir uma biblioteca
description: Excluir uma biblioteca usando as APIs REST do Places.
exl-id: ad45ea38-9e12-43d7-b05f-17d3e40abaf5
source-git-commit: 4ab15ded930b31e4e06920af31f37fdfe45df8eb
workflow-type: tm+mt
source-wordcount: '47'
ht-degree: 4%

---

# Excluir uma biblioteca {#delete-a-library}

Um método DELETE que permite excluir uma biblioteca.

## Solicitação

```text
DELETE https://api-places.adobe.io/places/placesapi/v1/libraries/<lIBRARYID>
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

Use o seguinte comando CURL para testar essa API:

```text
curl -X DELETE 'https://api-places.adobe.io/places/placesapi/v1/libraries/<LIBRARYID>' -H 'x-api-key: <API KEY>' -H 'Authorization: Bearer <TOKEN>' -H 'x-gw-ims-org-id: <ORGID>'
```

>[!IMPORTANT]
>
>Substitua variáveis como `<lIBRARYID>`, `<API KEY>`, `<TOKEN>` e `<ORGID>` por valores reais.
