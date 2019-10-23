---
title: Excluir uma biblioteca
seo-title: Excluir uma biblioteca
description: Exclua uma biblioteca usando as APIs REST do Places.
seo-description: Exclua uma biblioteca usando as APIs REST do Places.
translation-type: tm+mt
source-git-commit: 26b0cab7bdada26a7598b20623095b72f7c8d334

---


# Excluir uma biblioteca

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

## Resposta de exemplo

```text
If successful a Status of "204 No Content" is returned.
```

## comando CURL

Use o seguinte comando CURL para testar esta API:

```text
curl -X DELETE 'https://api-places.adobe.io/places/placesapi/v1/libraries/<LIBRARYID>' -H 'x-api-key: <API KEY>' -H 'Authorization: Bearer <TOKEN>' -H 'x-gw-ims-org-id: <ORGID>'
```

>[!IMPORTANT]
>
>Substitua variáveis como `<lIBRARYID>`, `<API KEY>`, `<TOKEN>`e `<ORGID>`por valores reais.

