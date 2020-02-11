---
title: Perguntas frequentes
description: Este tópico fornece informações adicionais sobre algumas perguntas frequentes.
translation-type: tm+mt
source-git-commit: 8691dbf061ac020a60d3880fe16951dcc79040cb

---


# Perguntas frequentes

Estas são algumas informações e perguntas frequentes sobre o Serviço Places.

## Tamanho e confiabilidade

É importante observar que todas as geofences estão sendo usadas no monitoramento de região de um aplicativo móvel, independentemente do uso da Adobe ou de algum outro serviço. Os sistemas operacionais recomendam que alguns parâmetros sejam levados em consideração ao criar geofences. Para uma fiabilidade máxima, as geofences devem ter um raio de pelo menos 100 metros. Não há problema em criar geofences menores, mas os eventos de entrada e saída podem não ser gerados ou podem ser gerados depois que o usuário para de se mover por um período.

Além disso, a precisão e a confiabilidade podem ser reduzidas com base em condições de hardware como wi-fi que está sendo desligado ou indisponível, e também com base na localização do dispositivo em relação aos sinais GPS. Por exemplo, as áreas de montagem, as configurações urbanas e as áreas interiores podem reduzir a precisão de localização dos sistemas operacionais iOS e Android.

## Como um evento exit é acionado?

Quando o SDK (Places Monitor) recebe uma nova lista de POIs próximos, ele registra uma região com o sistema operacional para cada POI. O sistema operacional agora é responsável por notificar o SDK quando o dispositivo atravessa um limite (entrada ou saída) para uma das regiões monitoradas. O SDK aciona apenas um evento exit quando o sistema operacional notifica o SDK de que o evento ocorreu. A principal razão para esta notificação é a sensibilidade temporal dos dados de localização.

Se o sistema operacional não puder fornecer um evento exit quando o dispositivo sair de uma região, é mais seguro para o SDK omitir o evento exit. Se o SDK fabricar um evento de saída sem que o evento seja acionado pelo sistema operacional, há um risco de que o evento exit possa ser processado bem fora do período durante o qual o dispositivo estava perto do POI.

## Número de POIs

Na interface de gerenciamento de POI do Places Service, os clientes podem somar até 150 mil pontos de interesse em uma biblioteca específica. Se desejado, os clientes podem definir várias bibliotecas para agrupar segmentos de POIs.

## Algumas observações sobre a alteração de localização e o monitoramento de região ativa

O monitoramento de uma região geográfica começa imediatamente após o registro para aplicativos autorizados. No entanto, não espere receber um evento imediatamente, pois somente os cruzamentos de limite geram um evento. Especificamente, se a localização do usuário já estiver dentro da região no momento do registro, o gerenciador de locais não gera automaticamente um evento. Em vez disso, seu aplicativo deve aguardar que o usuário ultrapasse o limite da região antes que um evento seja gerado e enviado ao delegado.

Tenha cuidado ao especificar o conjunto de regiões a serem monitoradas. As regiões são um recurso de sistema compartilhado e o número total de regiões disponíveis no sistema é limitado. Por esse motivo, a Localização principal limita a 20 o número de regiões que podem ser monitoradas simultaneamente por um único aplicativo. Para contornar esse limite, considere registrar apenas essas regiões na proximidade imediata do usuário.

[Consulte informações adicionais no site] de desenvolvedores da Apple (https://developer.apple.com/library/archive/documentation/UserExperience/Conceptual/LocationAwarenessPG/RegionMonitoring/RegionMonitoring.html#//apple_ref/doc/uid/TP40009497-CH9-SW11)

