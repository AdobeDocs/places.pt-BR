---
title: Uso do Places Service com Mobile Services para mensagens
description: Esta seção mostra como usar o Places Service com Mobile Services para mensagens.
translation-type: tm+mt
source-git-commit: 5a21e734c0ef56c815389a9f08b445bedaae557a

---


# Adobe Mobile Services {#places-mobile-services}

Antes de usar a extensão do Mobile Services para mensagens, reveja os seguintes pré-requisitos:

* Os pontos de interesse foram criados no Places Service. For more information, see [Create a POI](/help/poi-mgmt-ui/create-a-poi-ui.md).

   >[!IMPORTANT]
   >
   >O Serviço de Locais inclui um banco de dados POI novo e aprimorado para sua organização que existe fora da interface do usuário legada do Mobile Services. Os POIs localizados na navegação da página *Gerenciar locais* do Mobile Service funcionarão somente na versão 4 do SDK.

* Esta é a página *Gerenciar locais* de gerenciamento de POI na interface do usuário legada do Mobile Services para versões mais antigas do SDK:

   ![Interface do usuário legada](/help/assets/legacy-location-v4-ui.png)

* Esta é a interface do usuário do serviço Places:

   ![Interface do usuário de gerenciamento de POI do Places Service](/help/assets/places-ui.png)

* O SDK ACP está configurado corretamente com as extensões do Places Service e/ou Places Monitor.

   Isso significa que os dados estão disponíveis como eventos e/ou condições no mecanismo de regras do Experience Platform Launch para seu aplicativo móvel. Para obter mais informações, consulte Extensão [de](/help/places-ext-aep-sdks/places-extension/places-extension.md) locais ou Extensão [do Monitor de](/help/places-ext-aep-sdks/places-monitor-extension/using-places-monitor-extension.md)locais.

* Familiarize-se com a criação e publicação de regras de lançamento da plataforma Experience com o SDK ACP em seu aplicativo móvel.

   For more information, see [Rules engine](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/mobile-core/rules-engine).

* Os elementos de dados do Experience Platform Launch são criados a partir dos dados de extensão do Local que serão usados no mecanismo Regras.

   For more information, see [Data elements](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/mobile-core/rules-engine#data-elements).

## Relatório

Antes de usar os relatórios, conclua os seguintes pré-requisitos:

* Envio com êxito dos dados do Serviço do Local para o Conjunto de relatórios do Adobe Analytics.

   Para obter mais informações, consulte [Usar o serviço de locais com o Adobe Analytics](/help/use-places-with-other-solutions/places-adobe-analytics/use-places-adobe-analytics.md).

* Familiarize-se com os relatórios do Mobile Services.

   For more information, see [Reports](https://docs.adobe.com/content/help/en/mobile-services/using/reports-ug/usage.html).

## Visualização de relatórios

Você pode executar relatórios do Mobile Service usando dados do Places Service enviados para o Adobe Analytics. No exemplo a seguir, os eventos são enviados quando os usuários têm entradas em um dos POIs. Neste relatório, um filtro do evento de entrada POI foi adicionado ao longo do relatório de usuário predefinido:

![Visualização de relatório](/help/assets/report-visualize.png)

Flexibilidade adicional na visualização de dados do Serviço de locais está disponível nas interfaces do Adobe Analytics.

