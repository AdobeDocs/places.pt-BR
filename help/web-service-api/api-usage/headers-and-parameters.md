---
title: Cabeçalhos e parâmetros
description: Cabeçalhos e parâmetros disponíveis nas APIs REST do Places Service.
exl-id: 3c7e76de-f0ff-4966-a3ec-7f64d819c140
source-git-commit: 4ab15ded930b31e4e06920af31f37fdfe45df8eb
workflow-type: tm+mt
source-wordcount: '377'
ht-degree: 19%

---

# Cabeçalhos e parâmetros {#headers-and-parameters}

Estes são os detalhes sobre os cabeçalhos e parâmetros que estão disponíveis na API REST do Places Service:

## Cabeçalhos compatíveis

| Header | Descrição | Método | Exemplo |
| :--- | :--- | :--- | :--- |
| `Authorization` | Seu token de portador | Todas |  |
| `x-api-key` | Sua chave de API | Todas | `19776964b4cde49e08d8f62e5824f777b` |
| `x-gw-ims-org-id` | Sua ID da organização | Todas | `18FB61145BAC2FFB0A494777@AdobeOrg` |
| `Content-Type` | Formato do conteúdo enviado ou recebido | PUT, POST | `application/json` |
| `Accept-Language` | Idioma usado para mensagens de erro | Opcional | `en-US` |

## Parâmetros da biblioteca

| Parâmetro | Descrição | Tipo | Limite | Solicitação ou resposta | Exemplo |
| :--- | :--- | :--- | :--- | :--- | :--- |
| `id` | ID da biblioteca | atribuído | n/d | Resposta | `"id": "b2488788-2d2a-462b-b1a2-305272777dda"` |
| `name` | Nome da biblioteca | sequência de caracteres | 256 caracteres | ambos, necessários na solicitação | `"name": "Amazing Places"` |
| `orgID` | OrgID da Experience Cloud da organização | atribuído | n/d | Resposta | `"orgID": "777F20F55BACA09E0A495D8F@AdobeOrg"` |
| `poiCount` | Número de POIs na biblioteca | inteiro | 150.000 máx. | Resposta | `"poiCount": 25149` |
| `metadataDescriptors` | Conte para cada par exclusivo de valores dos metadados de POI | misto | n/d | Resposta |  |
| `poiCountInCities` | Conte para cada valor único de cidade do POI | misto | n/d | Resposta |  |

## Parâmetros de POI

| Parâmetro | Descrição | Tipo | Limite | Solicitação ou resposta | Exemplo |
| :--- | :--- | :--- | :--- | :--- | :--- |
| `data` | Dados de Poi | Matriz de detalhes de POI | n/d | ambos |  |
| `id` | ID do POI | atribuído | n/d | resposta | `"id": "1455462b-7f9c-4220-9f42-5bbce777a0d1"` |
| `name` | Nome do POI | sequência de caracteres | 512 caracteres | ambos, opcional\* | `"name": "My Favorite Place"` |
| `description` | Descrição do POI | sequência de caracteres | 512 caracteres | ambos, opcional\* | `"description": "This is a very good place."` |
| `location` | Matriz de tipo e coordenadas de POI | matriz (mista) | n/d | ambos | `"location": {"type": "Point", "coordinates": [-122.201007, 37.604713]` |
| `type` | Tipo de POI | sequência de caracteres | somente &quot;Ponto&quot; compatível no momento | ambos, necessários na solicitação | `"type": "Point"` |
| `coordinates` | Matriz de longitude e latitude do POI | matriz (flutuante) | longitude: -180 a 180, latitude -85 a 85 | ambos, necessários na solicitação | `"coordinates": [-122.201007, 37.604713]` |
| `radius` | Tamanho da cerca geográfica circular em torno do POI | flutuante | 10 - 2000 metros | ambos, necessários na solicitação | `"radius": 100` |
| `country` | País do POI | sequência de caracteres | 32 caracteres | ambos, opcionais* | `"country": "United States"` |
| `state` | Estado do POI | sequência de caracteres | 32 caracteres | ambos, opcionais* | `"state": "California"` |
| `city` | Cidade do POI | sequência de caracteres | 32 caracteres | ambos, opcionais* | `"city": "San Jose"` |
| `street` | Endereço do POI | sequência de caracteres | 256 caracteres | ambos, opcionais* | `"street": "122 Woz Way"` |
| `category` | Categoria do POI | sequência de caracteres | 100 caracteres | ambos, opcionais* | `"category": "cafe"` |
| `icon` | Ícone do POI | sequência de caracteres | 50 caracteres | ambos, opcionais* | `"icon": "star"` |
| `color` | Cor para o POI | sequência de caracteres | 8 caracteres | ambos, opcionais* | `"color": "blue"` |
| `metadata` | Matriz de pares de chave/valor para o POI | array(string) | chave: 256 caracteres, valor: 256 caracteres, máximo de 10 pares | ambos, opcionais* | `"metadata": {"region": "Equator"}` |
| `lib_id` | ID da biblioteca em que o POI está | n/d | n/d | ambos, obrigatório | `"lib_id": "ac7a0b25-c6c2-43ba-bbc6-2b1777b80fe9"` |

* Se o valor do parâmetro não for incluído, o valor será definido como `empty` no banco de dados. Se o par chave/valor existente não estiver incluído, o par chave/valor será removido para esse POI no banco de dados.
