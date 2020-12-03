---
title: Referência de eventos de locais
description: 'Uma lista dos eventos manipulados pela extensão Locais. '
translation-type: tm+mt
source-git-commit: 5a0705f02c8ecd540506b628371aec45107df7b2
workflow-type: tm+mt
source-wordcount: '248'
ht-degree: 24%

---


# Referência de eventos de locais {#places-event-reference}

Esta é uma lista dos eventos manipulados pela extensão Places.

## GetCurrentPointsOfInterest

**Detalhes do evento**

| Tipo | Fonte | Nome | Pareado |
| :--- | :--- | :--- | :--- |
| LOCAIS | REQUEST_CONTENT | `requestgetuserwithinplaces` | Verdadeiro |

**Descrição do evento**

Este evento é uma solicitação para recuperar os POIs nos quais o dispositivo está localizado no momento.

**Definição do conteúdo de dados**

n/d

## GetNearbyPointsOfInterest

**Detalhes do evento**

| Tipo | Fonte | Nome | Pareado |
| :--- | :--- | :--- | :--- |
| LOCAIS | REQUEST_CONTENT | `requestgetnearbyplaces` | Verdadeiro |

**Descrição do evento**

Este evento é uma solicitação para obter os POIs próximos, levando em consideração a localização atual do dispositivo e as bibliotecas configuradas de Locais.

**Definição do conteúdo de dados**

| Chave | Tipo de valor | Obrigatório | Valor padrão | Descrição |
| :--- | :--- | :--- | :--- | :--- |
| latitude | duplo | true | n/d | Mantém o valor de latitude para o centro da pesquisa por POIs próximos. |
| longitude | duplo | true | n/d | Mantém o valor da longitude do centro da pesquisa por POIs próximos. |
| raio | integer | false | n/d | Raio, em metros, usado pela busca por POIs próximos. |
| count | integer | false | 10 | Número máximo de POIs para retornar ao evento de resposta resultante. |

## ProcessRegionEvent

**Detalhes do evento**

| Tipo | Fonte | Nome | Pareado |
| :--- | :--- | :--- | :--- |
| LOCAIS | REQUEST_CONTENT | `requestprocessregionevent` | Falso |

**Descrição do evento**

Esse evento faz com que a extensão Locais processe uma entrada de geofence ou um evento exit.

**Definição do conteúdo de dados**

| Chave | Tipo de valor | Obrigatório | Descrição |
| :--- | :--- | :--- | :--- |
| regionid | string | true | ID da região que gera o evento. |
| regioneventtype | int | true | Tipo de evento de região que está sendo gerado. 1 para entrada e 2 para saída. |

## Eventos despachados pela extensão Locais

Essas informações estão em andamento.

