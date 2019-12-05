---
title: Perguntas frequentes
seo-title: Perguntas frequentes
description: Este tópico fornece informações adicionais sobre algumas perguntas frequentes.
seo-description: Este tópico fornece informações adicionais sobre algumas perguntas frequentes.
translation-type: tm+mt
source-git-commit: f4b8bccc154df346e67ef17295d7c6b42c68b26d

---


# Perguntas frequentes

Estas são algumas informações e perguntas frequentes sobre o Serviço de Localização.

## Tamanho e confiabilidade

É importante observar que todas as geofences estão sendo usadas no monitoramento de região de um aplicativo móvel, independentemente do uso da Adobe ou de algum outro serviço. Os sistemas operacionais recomendam que alguns parâmetros sejam levados em consideração ao criar geofences. Para uma fiabilidade máxima, as geofences devem ter um raio de pelo menos 100 metros. Não há problema em criar geofences menores, mas os eventos de entrada e saída podem não ser gerados ou podem ser gerados depois que o usuário para de se mover por um período.

Além disso, a precisão e a confiabilidade podem ser reduzidas com base em condições de hardware como wi-fi que está sendo desligado ou indisponível, e também com base na localização do dispositivo em relação aos sinais GPS. Por exemplo, as áreas de montagem, as configurações urbanas e as áreas interiores podem reduzir a precisão de localização dos sistemas operacionais iOS e Android.

## Como um evento exit é acionado?

Quando o SDK (Places Monitor) recebe uma nova lista de POIs próximos, ele registra uma região com o sistema operacional para cada POI. O sistema operacional agora é responsável por notificar o SDK quando o dispositivo atravessa um limite (entrada ou saída) para uma das regiões monitoradas. O SDK aciona apenas um evento exit quando o sistema operacional notifica o SDK de que o evento ocorreu. A principal razão para esta notificação é a sensibilidade temporal dos dados de localização.

Se o sistema operacional não puder fornecer um evento exit quando o dispositivo sair de uma região, é mais seguro para o SDK omitir o evento exit. Se o SDK fabricar um evento de saída sem que o evento seja acionado pelo sistema operacional, há um risco de que o evento exit possa ser processado bem fora do período durante o qual o dispositivo estava perto do POI.
