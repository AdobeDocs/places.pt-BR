---
title: Usar locais com Mobile Services para mensagens
description: Esta seção mostra como usar os Locais com Mobile Services para mensagens.
translation-type: tm+mt
source-git-commit: 5a0705f02c8ecd540506b628371aec45107df7b2

---


# Adobe Mobile Services {#places-mobile-services}

Antes de usar a extensão do Mobile Services para mensagens, reveja os seguintes pré-requisitos:

* Os pontos de interesse foram criados no Serviço de Localização. Consulte Documentação, se necessário. (link para criar um POI)Observação: O Serviço de Localização inclui um banco de dados de ponto de interesse novo e aprimorado para sua organização que existe fora da interface herdada do AMS. Todos os POIs encontrados na navegação &quot;Gerenciar locais&quot; do AMS funcionarão somente na versão 4 do SDK.
   * Esta é a interface de gerenciamento herdada do POI Places no AMS para versões mais antigas do SDK:

      ![Interface do usuário legada](/help/assets/legacy-location-v4-ui.png)

   * Esta é a interface de gerenciamento POI do Serviço de Localização:

      ![Interface do usuário de gerenciamento de POI do Serviço de Localização](/help/assets/places-ui.png)

* O SDK ACP está configurado corretamente com extensões do Monitor de locais e/ou locais. Isso significa que os dados estão disponíveis como eventos e/ou condições no mecanismo de regras de inicialização para seu aplicativo móvel. Consulte a documentação, se necessário. (https://aep-sdks.gitbook.io/docs/beta/adobe-places)

* Familiarize-se com como criar e publicar regras de inicialização no SDK ACP em seu aplicativo móvel. Consulte a documentação, se necessário. (https://aep-sdks.gitbook.io/docs/using-mobile-extensions/mobile-core/rules-engine)

* Os Elementos de dados de inicialização são criados a partir dos dados de extensão do SDK do Places que serão usados nas Regras. Consulte a documentação (https://aep-sdks.gitbook.io/docs/using-mobile-extensions/mobile-core/rules-engine#data-elements)

## Relatório

Antes de usar os relatórios, conclua os seguintes pré-requisitos:

* Envio de dados do Serviço de localização com êxito para o Conjunto de relatórios do Adobe Analytics. Visite a documentação do Adobe Analytics, se necessário (link para os documentos do Steve).
* Familiarize-se com os relatórios do AMS. Visite a documentação, se necessário (https://docs.adobe.com/content/help/en/mobile-services/using/reports-ug/usage.html)

## Visualização de relatórios

Você pode executar relatórios do AMS usando dados do Serviço de localização enviados para o Adobe Analytics. Por exemplo, eu enviei eventos quando os usuários têm entradas em um dos meus POIs. Neste relatório, adicionei um filtro do evento de entrada POI sobre meu relatório de usuário predefinido:

![Visualização de relatório](/help/assets/report-visualize.png)

Flexibilidade adicional na visualização de dados do Serviço de localização está disponível nas interfaces do Adobe Analytics.

