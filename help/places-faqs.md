---
title: Perguntas frequentes
description: Este tópico fornece informações adicionais sobre algumas perguntas frequentes.
exl-id: cee9f447-5e50-4ed8-b37b-baecbc0e9b7b
TQID: https://experienceleague.adobe.com/LL9eLMDJaq8ZmeiZxv28QZoqXL1A0QKZ-DvTDUx4Gnw
product_v2:
  - id: d0a3eab4-7b10-4d96-a71e-6c0f8e7b7c87
  - id: dc5cf79d-43c4-4731-bffa-1df5d7549cb1
  - id: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
feature_v2:
  - id: e08599ea-8888-4294-ba74-3ba0a7762a46
subfeature_v2:
  - id: d2a6cbf4-df32-480f-909e-b42f66dcb9f0
topic_v2:
  - id: d3cdead0-685a-4489-9250-4bb709942f66
source-git-commit: f962cef761f006c8e7d45b76ba24746e36bdaba6
workflow-type: tm+mt
source-wordcount: 557
ht-degree: 1%

---

# Perguntas frequentes

Estas são algumas informações e perguntas frequentes sobre o Places Service.

## Migração do trackLocation na v4 SDK

Se você estiver migrando do SDK v4 e estiver procurando uma substituição para a API `trackLocation`, consulte o tópico [Usar o Serviço do Places sem o Monitoramento de região ativa](use-places-without-active-monitoring.md).

## Tamanho e confiabilidade

Importante observar para todas as geofences que estão sendo usadas no monitoramento de região de um aplicativo móvel, independentemente do uso do Adobe ou de algum outro serviço. Os sistemas operacionais recomendam alguns parâmetros que devem ser considerados ao criar geofences. Para máxima confiabilidade, as geofences devem ter um raio de pelo menos 100 metros. Não há problema em criar geofences menores, mas os eventos de entrada e saída podem não ser gerados ou podem ser gerados depois que o usuário para de se mover por um período.

Além disso, a precisão e a confiabilidade podem ser reduzidas com base nas condições do hardware, como o Wi-Fi estar desligado ou indisponível, e também com base na localização do dispositivo em relação aos sinais de GPS que estão sendo obstruídos. Por exemplo, áreas montanhosas, ambientes urbanos e áreas internas podem reduzir a precisão da localização dos sistemas operacionais iOS e Android.

## Como um evento de saída é acionado?

O monitor de região implementado deve solicitar uma lista de POIs próximos. Uma vez recebida, uma região deve ser registrada no sistema operacional para cada POI. O sistema operacional agora é responsável por notificar a SDK quando o dispositivo atravessar um limite (entrada ou saída) para uma das regiões monitoradas. O SDK só aciona um evento de saída quando o sistema operacional notifica a SDK de que o evento ocorreu. O principal motivo para esta notificação é a sensibilidade temporal dos dados de localização.

Se o sistema operacional não puder entregar um evento de saída quando o dispositivo sair de uma região, é mais seguro que o SDK apenas omita o evento de saída. Se a SDK fabrica um evento de saída sem que o evento seja acionado pelo sistema operacional, há o risco de que o evento de saída seja processado bem fora do período durante o qual o dispositivo esteve próximo ao POI.

## Número de POIs

Na interface de gerenciamento de POIs do Places Service, os clientes podem adicionar até 150 mil pontos de interesse em uma biblioteca específica. Os clientes podem definir várias bibliotecas para agrupar segmentos de POIs, se desejado.

## Algumas observações sobre alteração de local e monitoramento de região ativa

O monitoramento de uma região geográfica começa imediatamente após o registro para aplicativos autorizados. No entanto, não espere receber um evento imediatamente, pois somente cruzamentos de limites geram um evento. Especificamente, se a localização do usuário já estiver dentro da região no momento do registro, o gerenciador de localização não gera um evento automaticamente. Em vez disso, seu aplicativo deve esperar que o usuário cruze o limite da região antes que um evento seja gerado e enviado ao delegado.

Seja criterioso ao especificar o conjunto de regiões a serem monitoradas. As regiões são um recurso de sistema compartilhado e o número total de regiões disponíveis em todo o sistema é limitado. Por esse motivo, a Localização principal limita a 20 o número de regiões que podem ser monitoradas simultaneamente por um único aplicativo. Para contornar esse limite, considere registrar apenas as regiões nas proximidades imediatas do usuário.

[Consulte informações adicionais no site do desenvolvedor do Apple] (https://developer.apple.com/library/archive/documentation/UserExperience/Conceptual/LocationAwarenessPG/RegionMonitoring/RegionMonitoring.html#//apple_ref/doc/uid/TP40009497-CH9-SW11)
