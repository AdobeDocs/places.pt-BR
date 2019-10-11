---
title: Obter a classificação de uma biblioteca
seo-title: Obter a classificação de uma biblioteca
description: Obtenha a classificação de uma biblioteca usando a API REST do Places.
seo-description: Obtenha a classificação de uma biblioteca usando a API REST do Places.
translation-type: tm+mt
source-git-commit: ef3d77eba407013e1f701ed001ef9ab7b3818e07

---


# Obter a classificação de uma biblioteca

Um método GET que permite classificar bibliotecas.

## Solicitação

`GET https://api-places.adobe.io/places/placesapi/v1/libraries/rank`

## Cabeçalhos

```
-H Content-Type: application/JSON  
-H 'Authorization: Bearer <TOKEN>'  
-H 'x-api-key: <API KEY>'  
-H 'x-gw-ims-org-id: <ORGID>'  
-H 'Accept-Language: en-US'
```

## Resposta de exemplo

```
{"library_rank_order":["ea45781f-26af-44b1-b4f8-43baf5f0fe28","dfcc5270-1d6d-4bc9-9cd9-85ecd5ebc12b"]}
```

## comando CURL

```
curl -X GET 'https://api-places.adobe.io/places/placesapi/v1/libraries/rank ' -H 'x-api-key: <API KEY>' -H 'Authorization: Bearer <TOKEN>' -H 'x-gw-ims-org-id: <ORGID>'
```

>[!IMPORTANT]
>
>Substitua variáveis como `<API KEY>`, `<TOKEN>`e `<ORGID>` por valores reais.

