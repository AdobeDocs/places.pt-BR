---
title: Definir uma classificação em suas bibliotecas
seo-title: Definir uma classificação em suas bibliotecas
description: Defina uma classificação em suas bibliotecas usando a API REST do Places.
seo-description: Defina uma classificação em suas bibliotecas usando a API REST do Places.
translation-type: tm+mt
source-git-commit: 6ae0c8d90cad4c437e1db7f562a0bc9c6b072ce6

---


# Definir uma classificação em suas bibliotecas

Um método PUT que permite definir uma ordem de classificação em todas as bibliotecas.

## Solicitação

`PUT https://api-places-dev.adobe.io/places/placesapi/v1/libraries/rank`

## Cabeçalhos

```-H Content-Type: application/json'
-H 'Authorization: Bearer <TOKEN>`  
-H 'x-api-key: <API KEY>'  
-H 'x-gw-ims-org-id: <ORGID>'  
-H 'Accept-Language: en-US'
```

## Dados de PUT

```
"library_rank_order": ["dfcc5270-1d6d-4bc9-9cd9-85ecd5ebc12b","ea45781f-26af-44b1-b4f8-43baf5f0fe28"]  
}
```

## Resposta de exemplo

```
{"library_rank_order" ["dfcc5270-1d6d-4bc9-9cd9-85ecd5ebc12b","ea45781f-26af-44b1-b4f8-43baf5f0fe28"]}
```

## comando CURL

```
curl -X PUT `'https://api-places.adobe.io/places/placesapi/v1/libraries/rank'` -H 'x-api-key: <API KEY>' -H 'Authorization: Bearer <TOKEN>' -H 'x-gw-ims-org-id: <ORGID>' -d '{"library_rank_order": ["dfcc5270-1d6d-4bc9-9cd9-85ecd5ebc12b","ea45781f-26af-44b1-b4f8-43baf5f0fe28"]}' -H "Content-Type: application/json"
```

>[!IMPORTANT]
>
>Substitua variáveis como `<API KEY>`, `<TOKEN>`e `<ORGID>` por valores reais.

