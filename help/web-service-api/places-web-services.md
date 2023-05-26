---
title: Visão geral da API de serviços da Web
description: O Places Service é o conjunto de serviços que facilita aos clientes do Adobe hidratar as soluções da Adobe Experience Cloud e da Adobe Experience Platform com dados de localização e a experiência certa para a pessoa certa, na hora certa e no lugar certo.
exl-id: 9e7358d1-3ba0-4304-aeb2-fed7162afb57
source-git-commit: 4ab15ded930b31e4e06920af31f37fdfe45df8eb
workflow-type: tm+mt
source-wordcount: '335'
ht-degree: 1%

---

# Visão geral da API de serviços da Web {#places-web-services-api}

O Places Service é o conjunto de serviços que facilita aos clientes do Adobe hidratar as soluções da Adobe Cloud Platform e da Adobe Experience Platform com dados de localização e a experiência certa para a pessoa certa, na hora certa e no lugar certo.

As APIs de serviços da Web permitem fazer o seguinte:

* Gerenciar geofences
* Meça a localização dos usuários mesmo quando o aplicativo estiver em segundo plano
* Use dados em tempo real quando for importante

Esta seção fornece informações sobre como usar as REST APIs e o banco de dados de POI, que contém os dados de POI da sua organização.

## REST APIs

A API REST do Places Service permite trabalhar programaticamente com os POIs da sua organização. Essas APIs permitem criar, atualizar e excluir as bibliotecas e os POIs nessas bibliotecas. Essas APIs usam os padrões JavaScript Object Notation (JSON) para formatar os dados enviados e recebidos. Uma vantagem principal do JSON é que ele facilita a gravação, leitura e análise de consultas de API por desenvolvedores e máquinas.

Antes de usar a API de serviços da Web, verifique se os seguintes requisitos foram atendidos:

* O Places Service é provisionado em sua organização e você tem acesso apropriado como usuário.

   Para obter mais informações, consulte *Pré-requisitos para acesso do usuário* in [Visão geral e pré-requisitos da integração](/help/web-service-api/adobe-i-o-integration.md).

* Depois que o Serviço do Places for provisionado em sua organização e você tiver acesso, crie uma integração de Adobe para o Serviço do Places.

   Para obter mais informações, consulte *Criação de uma integração do Places Service* in [Visão geral e pré-requisitos da integração](/help/web-service-api/adobe-i-o-integration.md).

Informações adicionais:

* Para obter mais informações sobre as APIs disponíveis e como usá-las, consulte [Gerenciar bibliotecas](/help/web-service-api/api-usage/manage-libraries/manage-libraries.md) e [Gerenciar POIs](/help/web-service-api/api-usage/manage-pois/manage-pois.md).
* Para obter mais informações sobre os cabeçalhos e parâmetros nessas APIs, consulte [Cabeçalhos e parâmetros](/help/web-service-api/api-usage/headers-and-parameters.md).
