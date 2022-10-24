---
title: Perguntas frequentes
description: Este tópico fornece informações adicionais sobre algumas perguntas frequentes.
exl-id: cee9f447-5e50-4ed8-b37b-baecbc0e9b7b
source-git-commit: 010de286c25c1eeb989fb76e3c2adaa82ac9fd35
workflow-type: tm+mt
source-wordcount: '554'
ht-degree: 1%

---

# Perguntas frequentes

Aqui estão algumas informações e perguntas frequentes sobre o Places Service.

## Migração de trackLocation no v4 SDK

Se você estiver migrando do SDK v4 e estiver procurando uma substituição para o `trackLocation` Por favor, consulte o tópico [Usar o Places Service sem monitoramento de região ativa](use-places-without-active-monitoring.md).

## Tamanho e confiabilidade

É importante observar que todas as geofences estão sendo usadas no monitoramento de região a partir de um aplicativo móvel, independentemente do uso do Adobe ou de outro serviço. Os sistemas operacionais recomendam que alguns parâmetros sejam considerados ao criar geofences. Para maior confiabilidade, as geofences devem ter um raio de pelo menos 100 metros. Não há problema em criar geofences menores, mas os eventos de entrada e saída podem não ser gerados ou podem ser gerados depois que o usuário para de se mover por um período.

Além disso, a precisão e a confiabilidade podem ser reduzidas com base em condições de hardware, como o wi-fi que está sendo desligado ou indisponível, e também com base na localização do dispositivo em relação a impedir sinais GPS. Por exemplo, áreas montanhosas, configurações urbanas e áreas interiores podem reduzir a precisão de localização dos sistemas operacionais iOS e Android.

## Como um evento de saída é acionado?

O monitor de região implementado deve solicitar uma lista de POIs próximos. Uma vez recebida, uma região deve ser registrada no sistema operacional para cada POI. O sistema operacional agora é responsável por notificar o SDK quando o dispositivo ultrapassa um limite (entrada ou saída) para uma das regiões monitoradas. O SDK aciona um evento de saída somente quando o sistema operacional notifica o SDK de que o evento ocorreu. A principal razão para esta notificação é a sensibilidade ao tempo dos dados de localização.

Se o sistema operacional não puder fornecer um evento de saída quando o dispositivo deixar uma região, é mais seguro para o SDK omitir o evento de saída. Se o SDK fabricar um evento de saída sem que o evento seja acionado pelo sistema operacional, há um risco de que o evento de saída possa ser processado bem fora do período em que o dispositivo estava perto do POI.

## Número de POIs

Na interface de gerenciamento de POI do Places Service, os clientes podem adicionar até 150 mil pontos de interesse em uma biblioteca específica. Se desejar, os clientes podem definir várias bibliotecas para agrupar segmentos de POIs.

## Algumas observações sobre alteração de localização e monitoramento de região ativa

A monitorização de uma região geográfica começa imediatamente após o registro de aplicações autorizadas. No entanto, não espere receber um evento imediatamente, pois somente os cruzamentos de limite geram um evento. Em particular, se a localização do usuário já estiver dentro da região no momento do registro, o gerenciador de localização não gera um evento automaticamente. Em vez disso, seu aplicativo deve esperar que o usuário ultrapasse o limite da região antes que um evento seja gerado e enviado ao delegado.

Tenha cuidado ao especificar o conjunto de regiões a serem monitoradas. As regiões são um recurso de sistema compartilhado e o número total de regiões disponíveis em todo o sistema é limitado. Por esse motivo, a Localização principal limita a 20 o número de regiões que podem ser monitoradas simultaneamente por um único aplicativo. Para contornar esse limite, considere registrar apenas essas regiões na vizinhança imediata do usuário.

[Veja informações adicionais sobre o site do desenvolvedor do Apple] (https://developer.apple.com/library/archive/documentation/UserExperience/Conceptual/LocationAwarenessPG/RegionMonitoring/RegionMonitoring.html#//apple_ref/doc/uid/TP40009497-CH9-SW11)
