---
audience: end-user
user-guide-title: Guia do Places Service
user-guide-description: O Places Service é um serviço de localização geográfica que permite que aplicativos móveis com detecção de localização compreendam o contexto de localização.
translation-type: tm+mt
source-git-commit: 12283d11829ee70a808bc11d2bc1241cb1770ac3
workflow-type: tm+mt
source-wordcount: '316'
ht-degree: 19%

---


# Serviço de Places {#using}

+ [Visão geral do Places Service](home.md)
+ [Notas de versão](release-notes.md)
+ [Introdução](getting-started.md)
+ [Obter acesso ao Places Service](places-gain-access.md)
+ Interface do usuário do Places {#poi-mgmt-ui}
   + [Visão geral da interface do usuário do Places Service](poi-mgmt-ui/poi-mgmt-ui-overview.md)
   + [Criar um POI](poi-mgmt-ui/create-a-poi-ui.md)
   + [Gerenciar POIs criados anteriormente](poi-mgmt-ui/managing-pois-in-the-places-ui.md)
   + [Estratégias para usar metadados com POIs](poi-mgmt-ui/metadata-with-pois.md)
   + [Upload em massa de POIs](poi-mgmt-ui/bulk-upload-pois.md)
   + [Gerenciar várias bibliotecas](poi-mgmt-ui/manage-libraries-in-the-places-ui.md)
+ API de serviço da Web {#web-service-api}
   + [Visão geral da API de serviço da Web](web-service-api/places-web-services.md)
   + [Pré-requisitos de integração](web-service-api/adobe-i-o-integration.md)
   + Uso da API {#api-usage}
      + [Visão geral do uso da API](web-service-api/api-usage/api-usage-overview.md)
      + [Cabeçalhos e parâmetros](web-service-api/api-usage/headers-and-parameters.md)
      + Gerenciar bibliotecas {#manage-libraries}
         + [Visão geral do gerenciamento de bibliotecas](web-service-api/api-usage/manage-libraries/manage-libraries.md)
         + [Criar uma biblioteca](web-service-api/api-usage/manage-libraries/create-a-library.md)
         + [Ler uma biblioteca](web-service-api/api-usage/manage-libraries/read-a-library.md)
         + [Atualizar uma biblioteca](web-service-api/api-usage/manage-libraries/update-a-library.md)
         + [Excluir uma biblioteca](web-service-api/api-usage/manage-libraries/delete-a-library.md)
         + [Leia todas as bibliotecas na sua organização](web-service-api/api-usage/manage-libraries/read-all-libraries-in-your-organization.md)
         + [Definir uma classificação nas bibliotecas](web-service-api/api-usage/manage-libraries/set-a-ran-on-your-libraries.md)
         + [Obter a classificação de uma biblioteca](web-service-api/api-usage/manage-libraries/get-a-librarys-rank.md)
      + Gerenciar pontos de interesse {#manage-pois}
         + [Visão geral do gerenciamento de POIs](web-service-api/api-usage/manage-pois/manage-pois.md)
         + [Criar um POI](web-service-api/api-usage/manage-pois/create-a-poi.md)
         + [Ler um POI](web-service-api/api-usage/manage-pois/read-a-poi.md)
         + [Atualizar um POI](web-service-api/api-usage/manage-pois/update-a-poi.md)
         + [Excluir um POI](web-service-api/api-usage/manage-pois/delete-a-poi.md)
         + [Ler todos os POIs em uma biblioteca](web-service-api/api-usage/manage-pois/read-all-pois-in-a-library.md)
         + [Leia todos os POIs em sua organização](web-service-api/api-usage/manage-pois/read-all-pois-in-your-organization.md)
         + APIs em lote {#batch-apis}
            + [Visão geral das APIs em lote](web-service-api/api-usage/manage-pois/batch-apis/batch-apis.md)
            + [Criar vários POIs](web-service-api/api-usage/manage-pois/batch-apis/create-multiple-pois.md)
            + [Atualizar vários POIs](web-service-api/api-usage/manage-pois/batch-apis/update-multiple-pois.md)
            + [Excluir vários POIs](web-service-api/api-usage/manage-pois/batch-apis/delete-multiple-pois.md)
      + [APIs de query](web-service-api/api-usage/query-apis.md)
+ Extensões para SDKs móveis {#places-ext-aep-sdks}
   + Extensão do Places {#places-extension}
      + [Extensão do Places](places-ext-aep-sdks/places-extension/places-extension.md)
      + [Referência da API do Places](places-ext-aep-sdks/places-extension/places-api-reference.md)
      + [Referência de evento do Places](places-ext-aep-sdks/places-extension/places-event-ref.md)
      + [Objetos do Custom Places](places-ext-aep-sdks/places-extension/cust-places-objects.md)
   + Extensão do Places Monitor {#places-monitor-extension}
      + [Extensão do Places Monitor](places-ext-aep-sdks/places-monitor-extension/places-monitor-extension.md)
      + [Uso da extensão do Places Monitor](places-ext-aep-sdks/places-monitor-extension/using-places-monitor-extension.md)
      + [Referência da API do Places Monitor](places-ext-aep-sdks/places-monitor-extension/places-monitor-api-reference.md)
+ [Usar o Places Service com sua própria solução de monitoramento](using-your-own-monitor.md)
+ [Usar o Places Service sem monitoramento de região ativa](use-places-without-active-monitoring.md)
+ Usar o Places Service como parte do fluxo de trabalho do Experience Platform Launch {#use-places-launch-workflow}
   + [Usar o Places Service como parte do fluxo de trabalho do Experience Platform Launch](use-places-launch-workflow/places-launch-workflow.md)
   + [Definir elementos de dados](use-places-launch-workflow/define-data-elements.md)
   + [Criar regras de entrada e saída](use-places-launch-workflow/create-rule-places-property.md)
+ Usar o Places Service com outras soluções do Adobe {#use-places-with-other-solutions}
   + Adobe Analytics {#places-adobe-analytics}
      + [Usar o Places Service com o Adobe Analytics](use-places-with-other-solutions/places-adobe-analytics/use-places-analytics-overview.md)
      + [Enviar entrada de POI e dados de saída para o Analytics](use-places-with-other-solutions/places-adobe-analytics/use-places-adobe-analytics.md)
      + [Adicionar contexto de localização às solicitações do Analytics](use-places-with-other-solutions/places-adobe-analytics/run-reports-aa-places-data.md)
      + [Relatório dos dados de localização no Analytics Workspace](use-places-with-other-solutions/places-adobe-analytics/places-in-workspace.md)
   + Adobe Mobile Services {#places-mobile-svcs-messaging}
      + [Adobe Mobile Services](use-places-with-other-solutions/places-mobile-svcs-for-messaging/use-places-mobie-svcs-messaging.md)
      + [Notificações por push](use-places-with-other-solutions/places-mobile-svcs-for-messaging/mobile-svcs-messaging-push.md)
      + [Notificações no aplicativo](use-places-with-other-solutions/places-mobile-svcs-for-messaging/mobile-svcs-messaging-inapp.md)
   + Adobe Campaign Standard {#places-acs}
      + [Usar o Places Service com o Adobe Campaign Standard](use-places-with-other-solutions/places-acs/places-acs-overview.md)
      + [Notificações por push](use-places-with-other-solutions/places-acs/places-acs-push-notifications.md)
      + [Mensagens no aplicativo](use-places-with-other-solutions/places-acs/places-acs-in-app-messages.md)
   + Adobe Target {#places-target}
      + [Usar o Places Service com o Adobe Target](use-places-with-other-solutions/places-target/places-target.md)
+ Teste e validação {#places-testing-validation}
   + [Testar e validar o Places Service](places-testing-validation/test-validate-places.md)
+ [Perguntas frequentes](places-faqs.md)
