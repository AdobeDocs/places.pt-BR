---
title: Referência de evento de locais
description: Uma lista dos eventos que são manipulados pela extensão Places.
exl-id: 98210ef4-5ff1-4792-b97b-2845ce02e78a
source-git-commit: 4ab15ded930b31e4e06920af31f37fdfe45df8eb
workflow-type: tm+mt
source-wordcount: '248'
ht-degree: 28%

---

# Referência de evento de locais {#places-event-reference}

Esta é uma lista dos eventos que são manipulados pela extensão Places.

## ObterPontosDeInteresseAtuais

**Detalhes do evento**

| Tipo | Fonte | Nome | Pareado |
| :--- | :--- | :--- | :--- |
| PLACES | REQUEST_CONTENT | `requestgetuserwithinplaces` | Verdadeiro |

**Descrição do evento**

Esse evento é uma solicitação para recuperar os POIs nos quais o dispositivo está localizado no momento.

**Definição do conteúdo de dados**

n/a

## ObterPontosDeInteressePróximos

**Detalhes do evento**

| Tipo | Fonte | Nome | Pareado |
| :--- | :--- | :--- | :--- |
| PLACES | REQUEST_CONTENT | `requestgetnearbyplaces` | Verdadeiro |

**Descrição do evento**

Esse evento é uma solicitação para obter os POIs próximos, considerando a localização atual do dispositivo e as bibliotecas configuradas do Places.

**Definição do conteúdo de dados**

| Chave | Tipo de valor | Obrigatório | Valor padrão | Descrição |
| :--- | :--- | :--- | :--- | :--- |
| latitude | duplo | true | n/a | Mantém o valor de latitude do centro da pesquisa por POIs próximos. |
| longitude | duplo | true | n/a | Contém o valor de longitude do centro da pesquisa por POIs próximos. |
| raio | inteiro | false | n/a | Raio, em metros, usado pela pesquisa de POIs próximos. |
| count | inteiro | false | 10 | Número máximo de POIs a serem retornados no evento de resposta resultante. |

## EventoRegiãoProcesso

**Detalhes do evento**

| Tipo | Fonte | Nome | Pareado |
| :--- | :--- | :--- | :--- |
| PLACES | REQUEST_CONTENT | `requestprocessregionevent` | Falso |

**Descrição do evento**

Esse evento faz com que a extensão Places processe um evento de entrada ou saída de geofence.

**Definição do conteúdo de dados**

| Chave | Tipo de valor | Obrigatório | Descrição |
| :--- | :--- | :--- | :--- |
| regionid | string | true | ID da região que gera o evento. |
| regioneventtype | int | true | Tipo de evento de região que está sendo gerado. 1 para entrada e 2 para saída. |

## Eventos despachados pela extensão Places

Estas informações estão atualmente em andamento.
