---
title: Perguntas frequentes
description: Este tópico fornece informações adicionais sobre algumas perguntas frequentes.
exl-id: cee9f447-5e50-4ed8-b37b-baecbc0e9b7b
source-git-commit: 010de286c25c1eeb989fb76e3c2adaa82ac9fd35
workflow-type: tm+mt
source-wordcount: '541'
ht-degree: 1%

---

# Perguntas frequentes

Estas são algumas informações e perguntas frequentes sobre o Places Service.

## Migração do trackLocation no SDK v4

Se você estiver migrando do SDK v4 e estiver procurando uma substituição para a API `trackLocation`, consulte o tópico [Usar o Serviço do Places sem o Monitoramento de região ativa](use-places-without-active-monitoring.md).

## Tamanho e confiabilidade

Importante observar para todas as geofences que estão sendo usadas no monitoramento de região de um aplicativo móvel, independentemente de usar o Adobe ou algum outro serviço. Os sistemas operacionais recomendam alguns parâmetros que devem ser considerados ao criar geofences. Para máxima confiabilidade, as geofences devem ter um raio de pelo menos 100 metros. Não há problema em criar geofences menores, mas os eventos de entrada e saída podem não ser gerados ou podem ser gerados depois que o usuário para de se mover por um período.

Além disso, a precisão e a confiabilidade podem ser reduzidas com base nas condições do hardware, como o Wi-Fi estar desligado ou indisponível, e também com base na localização do dispositivo em relação aos sinais de GPS que estão sendo obstruídos. Por exemplo, áreas montanhosas, ambientes urbanos e áreas internas podem reduzir a precisão da localização dos sistemas operacionais iOS e Android.

## Como um evento de saída é acionado?

O monitor de região implementado deve solicitar uma lista de POIs próximos. Uma vez recebida, uma região deve ser registrada no sistema operacional para cada POI. O sistema operacional agora é responsável por notificar o SDK quando o dispositivo ultrapassa um limite (entrada ou saída) para uma das regiões monitoradas. O SDK só aciona um evento de saída quando o sistema operacional notifica o SDK de que o evento ocorreu. O principal motivo para esta notificação é a sensibilidade temporal dos dados de localização.

Se o sistema operacional não puder entregar um evento de saída quando o dispositivo sair de uma região, é mais seguro para o SDK simplesmente omitir o evento de saída. Se o SDK fabrica um evento de saída sem que o evento seja acionado pelo sistema operacional, há o risco de que o evento de saída seja processado bem fora do período durante o qual o dispositivo esteve próximo do POI.

## Número de POIs

Na interface de gerenciamento de POIs do Places Service, os clientes podem adicionar até 150 mil pontos de interesse em uma biblioteca específica. Os clientes podem definir várias bibliotecas para agrupar segmentos de POIs, se desejado.

## Algumas observações sobre alteração de local e monitoramento de região ativa

O monitoramento de uma região geográfica começa imediatamente após o registro para aplicativos autorizados. No entanto, não espere receber um evento imediatamente, pois somente cruzamentos de limites geram um evento. Especificamente, se a localização do usuário já estiver dentro da região no momento do registro, o gerenciador de localização não gera um evento automaticamente. Em vez disso, seu aplicativo deve esperar que o usuário cruze o limite da região antes que um evento seja gerado e enviado ao delegado.

Seja criterioso ao especificar o conjunto de regiões a serem monitoradas. As regiões são um recurso de sistema compartilhado e o número total de regiões disponíveis em todo o sistema é limitado. Por esse motivo, a Localização principal limita a 20 o número de regiões que podem ser monitoradas simultaneamente por um único aplicativo. Para contornar esse limite, considere registrar apenas as regiões nas proximidades imediatas do usuário.

[Consulte informações adicionais no site do desenvolvedor do Apple] (https://developer.apple.com/library/archive/documentation/UserExperience/Conceptual/LocationAwarenessPG/RegionMonitoring/RegionMonitoring.html#//apple_ref/doc/uid/TP40009497-CH9-SW11)
