---
title: Extensão do monitor de locais
seo-title: Extensão do monitor de locais
description: A extensão do Monitor de locais lida com as interações com o sistema operacional para registrar e monitorar os POIs mais próximos do usuário.
seo-description: 'A extensão do Monitor de locais lida com as interações com o sistema operacional para registrar e monitorar os POIs mais próximos do usuário. '
translation-type: tm+mt
source-git-commit: ef720c112bc0de386e070094629c5bab69938e76

---


# Extensão do monitor de locais {#places-monitor-extension}

A extensão do Monitor de locais lida com as interações com o sistema operacional para registrar e monitorar os POIs mais próximos do usuário. Essa extensão recupera os POIs que precisam ser registrados da extensão Locais e transmite as notificações de entrada e saída para a extensão Locais. Essas notificações estarão disponíveis nas regras de lançamento da plataforma Experience como eventos.

A extensão Monitor é opcional, pois alguns clientes podem já estar monitorando regiões com o sistema operacional. Se esse for o caso, adicione as APIs de extensão de Locais para receber os POIs mais próximos do banco de dados de Locais e também para enviar os eventos de entrada e saída, de modo que as ações apropriadas possam ser tomadas.