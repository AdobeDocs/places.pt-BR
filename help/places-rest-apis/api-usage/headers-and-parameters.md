---
title: Cabeçalhos e parâmetros
seo-title: Cabeçalhos e parâmetros
description: Cabeçalhos e parâmetros disponíveis nas APIs REST do Places.
seo-description: Cabeçalhos e parâmetros disponíveis nas APIs REST do Places.
translation-type: tm+mt
source-git-commit: ef3d77eba407013e1f701ed001ef9ab7b3818e07

---


# Cabeçalhos e parâmetros {#headers-and-parameters}

Estes são os detalhes sobre os cabeçalhos e parâmetros que estão disponíveis na API REST do Places:

## Cabeçalhos suportados

| Cabeçalho | Descrição | Método | Exemplo |
| :--- | :--- | :--- | :--- |
| `Authorization` | Seu token portador | Todos |  |
| `x-api-key` | Sua chave de API | Todos | `19776964b4cde49e08d8f62e5824f777b` |
| `x-gw-ims-org-id` | Sua ID organizacional | Todos | `18FB61145BAC2FFB0A494777@AdobeOrg` |
| `Content-Type` | Formato do conteúdo enviado ou recebido | PUT, POST | `application/json` |
| `Accept-Language` | Idioma usado para mensagens de erro | Opcional | `en-US` |

## Parâmetros da biblioteca

| Parâmetro | Descrição | Tipo | Limite | Solicitação ou resposta | Exemplo |
| :--- | :--- | :--- | :--- | :--- | :--- |
| `id` | ID da biblioteca | atribuído | n/a | Resposta | `"id": "b2488788-2d2a-462b-b1a2-305272777dda"` |
| `name` | Nome da biblioteca | string | 256 caracteres | ambos, obrigatório na solicitação | `"name": "Amazing Places"` |
| `orgID` | Experience Cloud orgID da organização | atribuído | n/a | Resposta | `"orgID": "777F20F55BACA09E0A495D8F@AdobeOrg"` |
| `poiCount` | Número de POIs na biblioteca | integer | 150.000 máx. | Resposta | `"poiCount": 25149` |
| `metadataDescriptors` | Contagem para cada par de valores de chave de metadados POI exclusivo | misto | n/a | Resposta |  |
| `poiCountInCities` | Contar para cada valor exclusivo da cidade POI | misto | n/a | Resposta |  |

## Parâmetros de POI

| Parâmetro | Descrição | Tipo | Limite | Solicitação ou resposta | Exemplo |
| :--- | :--- | :--- | :--- | :--- | :--- |
| `data` | Dados de postagem | Matriz de detalhes do POI | n/a | both |  |
| `id` | ID do POI | atribuído | n/a | resposta | `"id": "1455462b-7f9c-4220-9f42-5bbce777a0d1"` |
| `name` | Nome do POI | string | 512 caracteres | ambos, opcional\* | `"name": "My Favorite Place"` |
| `description` | Descrição do IPC | string | 512 caracteres | ambos, opcional\* | `"description": "This is a very good place."` |
| `location` | Matriz do tipo e coordenadas do POI | array (misto) | n/a | both | `"location": {"type": "Point", "coordinates": [-122.201007, 37.604713]` |
| `type` | Tipo de POI | string | apenas "Ponto" atualmente suportado | ambos, obrigatório na solicitação | `"type": "Point"` |
| `coordinates` | Matriz de longitude e latitude do POI | array (flutuante) | longitude: -180 a 180, latitude -85 a 85 | ambos, obrigatório na solicitação | `"coordinates": [-122.201007, 37.604713]` |
| `radius` | Tamanho da geofence circular em torno do POI | flutuante | 10 - 2000 metros | ambos, obrigatório na solicitação | `"radius": 100` |
| `country` | País para o POI | string | 32 caracteres | ambos, opcional* | `"country": "United States"` |
| `state` | Estado do POI | string | 32 caracteres | ambos, opcional* | `"state": "California"` |
| `city` | Cidade para o POI | string | 32 caracteres | ambos, opcional* | `"city": "San Jose"` |
| `street` | Endereço do POI | string | 256 caracteres | ambos, opcional* | `"street": "122 Woz Way"` |
| `category` | Categoria do IPC | string | 100 caracteres | ambos, opcional* | `"category": "cafe"` |
| `icon` | Ícone para o POI | string | 50 caracteres | ambos, opcional* | `"icon": "star"` |
| `color` | Cor do POI | string | 8 caracteres | ambos, opcional* | `"color": "blue"` |
| `metadata` | Matriz de pares de chave/valor para POI | array(string) | chave: 256 caracteres, valor: 256 caracteres, no máximo 10 pares | ambos, opcional* | `"metadata": {"region": "Equator"}` |
| `lib_id` | ID da biblioteca na qual o POI está | n/a | n/a | ambos, obrigatório | `"lib_id": "ac7a0b25-c6c2-43ba-bbc6-2b1777b80fe9"` |

* Se o valor do parâmetro não for incluído, o valor será definido como `empty` no banco de dados. Se o par de chave/valor existente não estiver incluído, o par de chave/valor será removido para esse POI no banco de dados.

