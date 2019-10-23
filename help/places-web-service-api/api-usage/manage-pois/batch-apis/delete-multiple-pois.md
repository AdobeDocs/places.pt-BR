---
title: Excluir vários POIs
seo-title: Excluir vários POIs
description: Use as APIs em lote para excluir vários POIs.
seo-description: Use as APIs em lote para excluir vários POIs.
translation-type: tm+mt
source-git-commit: 26b0cab7bdada26a7598b20623095b72f7c8d334

---



# Excluir vários POIs {#delete-multiple-pois}

Um método POST que permite excluir vários POIs.

## Solicitação

```text
POST https://api-places.adobe.io/places/placesapi/v1/pois/batchDelete
```

## Cabeçalhos

```text
-H' Content-Type: application/json'  -H 'Authorization: Bearer <TOKEN>'  -H 'x-api-key: <API KEY>'  -H 'x-gw-ims-org-id: <ORGID>'  -H 'Accept-Language: en-US'
```

## Corpo

```text
{  "ids": [    "<POIID>",    "<POIID>",    .    .    .    "<POIID>",    "<POIID>"  ]}
```

## Resposta de exemplo

```text
If successful a Status of "204 No Content" is returned.
```

## comando CURL

Use o seguinte comando CURL para testar esta API:

```text
curl -X POST 'https://api-places.adobe.io/places/placesapi/v1/pois/batchDelete' -H 'x-api-key: <API KEY>' -H 'Authorization: Bearer <TOKEN>' -H 'x-gw-ims-org-id: <ORGID>' --data-binary "@<PATHTOBATCHDELETEJSONFILE>" -H "Content-Type: application/json"
```

>[!IMPORTANT]
>
>Substitua `<API KEY>`, `<TOKEN>`e `<ORGID>`e `<PATHTOBATCHDELETEJSONFILE>` por valores reais.

## Exemplo de arquivo JSON

Este é o exemplo de arquivo JSON para a `batchDelete` API:

```text
{​"ids":["31a49d5c-c6ad-46ae-b88d-a6912a8a6b2f","6a78a729-7973-4373-9199-36da18cc5b8c","74eaa3da-2464-4298-9b6d-5376fa7ea00f"]​}
```
