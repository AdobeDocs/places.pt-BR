---
title: 'Visão geral dos serviços da Web locais '
seo-title: 'Visão geral dos serviços da Web locais '
description: O Places é o conjunto de serviços que facilita para os clientes da Adobe a hidratação das soluções da Adobe Experience Cloud e da Adobe Experience Platform com os dados de localização e a experiência certa para a pessoa certa no momento certo e no lugar certo.
seo-description: O Places é o conjunto de serviços que facilita para os clientes da Adobe a hidratação das soluções da Adobe Experience Cloud e da Adobe Experience Platform com os dados de localização e a experiência certa para a pessoa certa no momento certo e no lugar certo.
translation-type: tm+mt
source-git-commit: f6c92bbd4fb21999f5c96ea0df8ede6919d1bc79

---


# Visão geral dos serviços da Web locais {#places-web-services-api}

O Places é o conjunto de serviços que facilita para os clientes da Adobe a hidratação das soluções da plataforma Adobe Cloud e da plataforma Adobe Experience com dados de localização e a experiência certa para a pessoa certa no momento certo e no lugar certo.

Os locais permitem que você faça o seguinte:

* Gerenciar geofences
* Meça a localização dos usuários mesmo quando o aplicativo estiver em segundo plano
* Usar dados em tempo real quando for importante

Esta seção fornece informações sobre como usar as REST APIs e o banco de dados Places, que contém os dados POI da sua organização.

## API REST do Places

A API REST do Places permite trabalhar de forma programática com os POIs de sua organização. Essas APIs permitem que você crie, atualize e exclua suas bibliotecas e os POIs nessas bibliotecas. Essas APIs usam os padrões JavaScript Object Notation (JSON) para formatar os dados enviados e recebidos. Uma vantagem principal do JSON é que ele facilita a gravação, a leitura e a análise de consultas de API por desenvolvedores e máquinas.

Antes de usar a API Locais, verifique se os seguintes requisitos foram atendidos:

* Os locais são provisionados em sua organização e você tem acesso apropriado como usuário.

   For more information, see the *Organization requirements* section below.

* Depois que os Locais forem provisionados em sua organização e você tiver acesso, crie uma integração da Adobe para os Locais.

   Para obter mais informações, consulte *Criar integração* de locais na visão geral [da integração de E/S](/help/places-web-service-api/adobe-i-o-integration.md)da Adobe.

Informações adicionais:

* Para obter mais informações sobre as APIs disponíveis e como usá-las, consulte [Gerenciar bibliotecas](/help/places-web-service-api/api-usage/manage-libraries/manage-libraries.md) e [gerenciar POIs](/help/places-web-service-api/api-usage/manage-pois/manage-pois.md).
* Para obter mais informações sobre os cabeçalhos e parâmetros nessas APIs, consulte [Cabeçalhos e parâmetros](/help/places-web-service-api/api-usage/headers-and-parameters.md).

## Requisitos organizacionais {#org-requirements}

Para acessar as APIs REST do Places, verifique com o administrador do sistema se as seguintes tarefas foram concluídas:

* Os locais foram provisionados e aparecem na organização.
* Você foi adicionado à organização.
* Você foi adicionado aos Locais em sua organização.

   Para obter mais informações, consulte *Adicionar um usuário ao Places e ao Experience Platform Launch* nas perguntas frequentes sobre [locais](/help/places-faqs.md).

* Você foi adicionado como um desenvolvedor do Places à sua organização.

   Para obter mais informações sobre a função de desenvolvedor, consulte [Gerenciar desenvolvedores](https://helpx.adobe.com/enterprise/using/manage-developers.html).