---
title: Criar uma biblioteca
description: Crie uma biblioteca usando a API REST do Places.
translation-type: tm+mt
source-git-commit: 8a84fe2dc5a0efe94ce3121e589524e3c7a80c5e
workflow-type: tm+mt
source-wordcount: '48'
ht-degree: 18%

---


# Criar uma biblioteca {#create-a-library}

Um método POST que permite criar uma biblioteca.

## Solicitação

```text
POST https://api-places.adobe.io/places/placesapi/v1/libraries
```

## Cabeçalhos

```text
-H' Content-Type: application/json'  -H 'Authorization: Bearer <TOKEN>'  -H 'x-api-key: <API KEY>'  -H 'x-gw-ims-org-id: <ORGID>'  -H 'Accept-Language: en-US'
```

## Corpo

```text
{"name": "<LIBRARY_NAME>"}
```

## Exemplo de resposta

```text
{       "id": "449f08f3-eff5-4658-9329-2d9687af777e",       "name": "Facinating places",      "customerID": "777F20F55BACA09E0A495D8F@AdobeOrg",       "poiCount": 0  }
```

## comando CURL

Use o seguinte comando CURL para testar esta API:

```text
curl -X POST 'https://api-places.adobe.io/places/placesapi/v1/libraries' -H 'x-api-key: <API KEY>' -H 'Authorization: Bearer <TOKEN>' -H 'x-gw-ims-org-id: <ORGID>' -d '{"name":"New Library Name"}' -H "Content-Type: application/json"
```

>[!IMPORTANT]
>
>Substitua variáveis como `<API KEY>`, `<TOKEN>`e `<ORGID>` por valores reais.

