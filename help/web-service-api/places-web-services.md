---
title: 'Visão geral da API de serviços da Web '
description: O Places Service é o conjunto de serviços que facilita para os clientes do Adobe a hidratação das soluções Adobe Experience Cloud e Adobe Experience Platform com dados de localização e a experiência certa para a pessoa certa no momento certo e no lugar certo.
translation-type: tm+mt
source-git-commit: 0ca2162f113fba6bfbd54443109068b1a506762b
workflow-type: tm+mt
source-wordcount: '335'
ht-degree: 1%

---


# Visão geral da API de serviços da Web {#places-web-services-api}

O Places Service é o conjunto de serviços que facilita para os clientes do Adobe a hidratação das soluções Adobe Cloud Platform e Adobe Experience Platform com dados de localização e a experiência certa para a pessoa certa no momento certo e no lugar certo.

As APIs de serviços da Web permitem fazer o seguinte:

* Gerenciar geofences
* Meça a localização dos usuários mesmo quando o aplicativo estiver em segundo plano
* Usar dados em tempo real quando for importante

Esta seção fornece informações sobre como usar as REST APIs e o banco de dados POI, que contém os dados POI de sua organização.

## REST APIs

A API REST do serviço Places permite que você trabalhe de forma programática com os POIs de sua organização. Essas APIs permitem que você crie, atualize e exclua suas bibliotecas e os POIs nessas bibliotecas. Essas APIs usam os padrões JavaScript Object Notation (JSON) para formatar os dados enviados e recebidos. Uma vantagem principal do JSON é que ele facilita a gravação, a leitura e a análise de query de API por desenvolvedores e máquinas.

Antes de usar a API de serviços da Web, verifique se os seguintes requisitos foram atendidos:

* O Serviço de Locais é provisionado em sua organização e você tem acesso apropriado como usuário.

   Para obter mais informações, consulte *Pré-requisitos para acesso* do usuário na visão geral e pré-requisitos [da integração](/help/web-service-api/adobe-i-o-integration.md).

* Depois que o Serviço de Locais for provisionado em sua organização e você tiver acesso, crie uma integração de Adobe para o Serviço de Locais.

   Para obter mais informações, consulte *Criação de uma integração* do Serviço de Locais na visão geral e nos pré-requisitos [da](/help/web-service-api/adobe-i-o-integration.md)Integração.

Informações adicionais:

* Para obter mais informações sobre as APIs disponíveis e como usá-las, consulte [Gerenciar bibliotecas](/help/web-service-api/api-usage/manage-libraries/manage-libraries.md) e [gerenciar POIs](/help/web-service-api/api-usage/manage-pois/manage-pois.md).
* Para obter mais informações sobre os cabeçalhos e parâmetros nessas APIs, consulte [Cabeçalhos e parâmetros](/help/web-service-api/api-usage/headers-and-parameters.md).