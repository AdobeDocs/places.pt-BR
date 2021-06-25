---
title: Extensão do Places Monitor
description: A extensão Places Monitor lida com as interações com o sistema operacional para registrar e monitorar os POIs mais próximos do usuário.
exl-id: 254b33a0-79c4-4d51-8835-16e60f5c055e
source-git-commit: 8dcd777acf5d578b748afae9aa609c2349ea94a9
workflow-type: tm+mt
source-wordcount: '310'
ht-degree: 0%

---

# Extensão do Places Monitor {#places-monitor-extension}

A extensão Places Monitor lida com as interações com o sistema operacional para registrar e monitorar os POIs mais próximos do usuário. Essa extensão recupera os POIs que precisam ser registrados da extensão do Places e transmite as notificações de entrada e saída para a extensão do Places. Essas notificações estarão disponíveis nas regras do Experience Platform Launch como eventos.

A extensão Monitor é opcional, pois alguns clientes podem já estar monitorando regiões com o sistema operacional. Se esse for o caso, adicione as APIs de extensão do Places para receber os POIs mais próximos do banco de dados do Places Service e também para transmitir os eventos de entrada e saída para que as ações apropriadas possam ser tomadas.

## Substituição do Places Monitor

Em 31 de agosto de 2021, a extensão Places Monitor para os SDKs do Adobe Experience Platform Mobile será substituída. A extensão Places Monitor não receberá mais atualizações ou suporte após 31 de agosto.

Os clientes que atualmente usam a extensão do Places Monitor podem continuar usando essa extensão com a compreensão de que nenhuma atualização ou suporte adicional estará disponível por meio do Adobe.

A desaprovação da extensão do Places Monitor não tem impacto ou impacto negativo na extensão do Places Service, que continuará sendo compatível com aprimoramentos e atualizações.

Os clientes que desejam fazer a transição da extensão do Places Monitor para sua própria solução de monitoramento devem consultar a documentação para: [Use o Places Service com sua própria solução de monitoramento](https://experienceleague.adobe.com/docs/places/using/using-your-own-monitor.html?lang=en). Este documento explica como interagir com o Places Service implementando [Serviços principais de localização](https://developer.apple.com/documentation/corelocation) no iOS ou [Serviços de localização](https://developers.google.com/android/reference/com/google/android/gms/location/package-summary) no Google Play.
