---
title: 'Visão geral da API de serviços da Web '
seo-title: 'Visão geral da API de serviços da Web '
description: O Places é o conjunto de serviços que facilita para os clientes da Adobe a hidratação das soluções da Adobe Experience Cloud e da Adobe Experience Platform com os dados de localização e a experiência certa para a pessoa certa no momento certo e no lugar certo.
seo-description: O Places é o conjunto de serviços que facilita para os clientes da Adobe a hidratação das soluções da Adobe Experience Cloud e da Adobe Experience Platform com os dados de localização e a experiência certa para a pessoa certa no momento certo e no lugar certo.
translation-type: tm+mt
source-git-commit: e204958ac3acbf5fb45d2347987f35557be70e43

---


# Visão geral da API de serviços da Web {#places-web-services-api}

O Places é o conjunto de serviços que facilita para os clientes da Adobe a hidratação das soluções da plataforma Adobe Cloud e da plataforma Adobe Experience com dados de localização e a experiência certa para a pessoa certa no momento certo e no lugar certo.

As APIs de serviços da Web permitem fazer o seguinte:

* Gerenciar geofences
* Meça a localização dos usuários mesmo quando o aplicativo estiver em segundo plano
* Usar dados em tempo real quando for importante

Esta seção fornece informações sobre como usar as REST APIs e o banco de dados POI, que contém os dados POI de sua organização.

## REST APIs

A API REST do Places permite trabalhar de forma programática com os POIs de sua organização. Essas APIs permitem que você crie, atualize e exclua suas bibliotecas e os POIs nessas bibliotecas. Essas APIs usam os padrões JavaScript Object Notation (JSON) para formatar os dados enviados e recebidos. Uma vantagem principal do JSON é que ele facilita a gravação, a leitura e a análise de consultas de API por desenvolvedores e máquinas.

Antes de usar a API de serviços da Web, verifique se os seguintes requisitos foram atendidos:

* Os locais são provisionados em sua organização e você tem acesso apropriado como usuário.

   Para obter mais informações, consulte a seção Requisitos *da* organização abaixo.

* Depois que os Locais forem provisionados em sua organização e você tiver acesso, crie uma integração da Adobe para os Locais.

   Para obter mais informações, consulte *Criar integração* de locais na visão geral [da integração de E/S](/help/web-service-api/adobe-i-o-integration.md)da Adobe.

Informações adicionais:

* Para obter mais informações sobre as APIs disponíveis e como usá-las, consulte [Gerenciar bibliotecas](/help/web-service-api/api-usage/manage-libraries/manage-libraries.md) e [gerenciar POIs](/help/web-service-api/api-usage/manage-pois/manage-pois.md).
* Para obter mais informações sobre os cabeçalhos e parâmetros nessas APIs, consulte [Cabeçalhos e parâmetros](/help/web-service-api/api-usage/headers-and-parameters.md).

## Requisitos organizacionais {#org-requirements}

Para acessar as APIs REST de serviços da Web, verifique com o administrador do sistema se as seguintes tarefas foram concluídas:

* Os locais foram provisionados e aparecem na organização.
* Você foi adicionado à organização.
* Você foi adicionado aos Locais em sua organização.

   Para obter mais informações, consulte *Adicionar um usuário ao Places e ao lançamento* da plataforma de experiência em perguntas [](/help/places-faqs.md)frequentes.

* Você foi adicionado como um desenvolvedor do Places à sua organização.

   Para obter mais informações sobre a função de desenvolvedor, consulte [Gerenciar desenvolvedores](https://helpx.adobe.com/enterprise/using/manage-developers.html).