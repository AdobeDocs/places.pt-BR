---
title: Referência de evento de locais
description: Uma lista dos eventos que são manipulados pela extensão Places.
feature: Mobile SDK
exl-id: 98210ef4-5ff1-4792-b97b-2845ce02e78a
product_v2:
  - id: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
    internal-label: Experience Platform
feature_v2:
  - id: a8a79b8d-fdca-499c-a5ef-f88a099d8eb9
    internal-label: Mobile SDK
source-git-commit: d8704da9c84a066f72471421290d4b46c65f41e1
workflow-type: tm+mt
source-wordcount: '247'
ht-degree: 17%
---
# Referência de evento de locais {#places-event-reference}

Esta é uma lista dos eventos que são manipulados pela extensão Places.

## ObterPontosDeInteresseAtuais

**Detalhes do evento**

| Tipo | Fonte | Nome | Emparelhado |
| :--- | :--- | :--- | :--- |
| PLACES | REQUEST_CONTENT | `requestgetuserwithinplaces` | Verdadeiro |

**Descrição do evento**

Esse evento é uma solicitação para recuperar os POIs nos quais o dispositivo está localizado no momento.

**Definição da carga de dados**

n/d

## ObterPontosDeInteressePróximos

**Detalhes do evento**

| Tipo | Fonte | Nome | Emparelhado |
| :--- | :--- | :--- | :--- |
| PLACES | REQUEST_CONTENT | `requestgetnearbyplaces` | Verdadeiro |

**Descrição do evento**

Esse evento é uma solicitação para obter os POIs próximos, considerando a localização atual do dispositivo e as bibliotecas configuradas do Places.

**Definição da carga de dados**

| Chave | Tipo de valor | Obrigatório | Valor padrão | Descrição |
| :--- | :--- | :--- | :--- | :--- |
| latitude | duplo | verdadeiro | n/d | Mantém o valor de latitude do centro da pesquisa por POIs próximos. |
| longitude | duplo | verdadeiro | n/d | Contém o valor de longitude do centro da pesquisa por POIs próximos. |
| raio | inteiro | falso | n/d | Raio, em metros, usado pela pesquisa de POIs próximos. |
| contagem | inteiro | falso | 10 | Número máximo de POIs a serem retornados no evento de resposta resultante. |

## EventoRegiãoProcesso

**Detalhes do evento**

| Tipo | Fonte | Nome | Emparelhado |
| :--- | :--- | :--- | :--- |
| PLACES | REQUEST_CONTENT | `requestprocessregionevent` | Falso |

**Descrição do evento**

Esse evento faz com que a extensão Places processe um evento de entrada ou saída de geofence.

**Definição da carga de dados**

| Chave | Tipo de valor | Obrigatório | Descrição |
| :--- | :--- | :--- | :--- |
| regionid | sequência de caracteres | verdadeiro | ID da região que gera o evento. |
| regioneventtype | int | verdadeiro | Tipo de evento de região que está sendo gerado. 1 para entrada e 2 para saída. |

## Eventos despachados pela extensão Places

Estas informações estão atualmente em andamento.
