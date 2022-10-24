---
title: Uso do Places Service com Mobile Services para mensagens
description: Esta seção mostra como usar o Places Service com Mobile Services para mensagens.
exl-id: dfa6b8bb-6bf2-44eb-8bfc-87294807ec3b
source-git-commit: 010de286c25c1eeb989fb76e3c2adaa82ac9fd35
workflow-type: tm+mt
source-wordcount: '346'
ht-degree: 1%

---

# Adobe Mobile Services {#places-mobile-services}

Antes de usar a extensão Mobile Services para mensagens, revise os seguintes pré-requisitos:

* Pontos de interesse foram criados no Places Service. Para obter mais informações, consulte [Criar um POI](/help/poi-mgmt-ui/create-a-poi-ui.md).

   >[!IMPORTANT]
   >
   >O Places Service inclui um banco de dados de POI novo e aprimorado para sua organização que existe fora da interface do usuário do Mobile Services herdada. POIs localizados no Mobile Service *Gerenciar locais* a navegação de página funcionará somente para a versão 4 do SDK.

* Aqui está o *Gerenciar locais* Página de gerenciamento de POI na interface do usuário herdada do Mobile Services para versões mais antigas do SDK:

   ![Interface do usuário herdada](/help/assets/legacy-location-v4-ui.png)

* Esta é a interface do usuário do Places Service:

   ![Interface do usuário de gerenciamento de POI do Places Service](/help/assets/places-ui.png)

* O SDK ACP é configurado corretamente com a extensão do Places.

   Isso significa que os dados estão disponíveis como eventos e/ou condições no mecanismo de regras do Experience Platform Launch para seu aplicativo móvel. Para obter mais informações, consulte [Extensão do Places](/help/places-ext-aep-sdks/places-extension/places-extension.md).

* Familiarize-se com a criação e a publicação de regras do Experience Platform Launch para o SDK ACP em seu aplicativo móvel.

   Para obter mais informações, consulte [Mecanismo de regras](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/mobile-core/rules-engine).

* Os elementos de dados do Experience Platform Launch são criados a partir dos dados da extensão do Places que serão usados no mecanismo Regras.

   Para obter mais informações, consulte [Elementos de dados](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/mobile-core/rules-engine#data-elements).

## Relatórios

Antes de usar os relatórios, conclua os seguintes pré-requisitos:

* Enviar dados do Places Service com êxito para o Conjunto de relatórios do Adobe Analytics.

   Para obter mais informações, consulte [Usar o Places Service com o Adobe Analytics](/help/use-places-with-other-solutions/places-adobe-analytics/use-places-adobe-analytics.md).

* Familiarize-se com os relatórios do Mobile Services.

   Para obter mais informações, consulte [Relatórios](https://docs.adobe.com/content/help/en/mobile-services/using/reports-ug/usage.html).

## Visualização de relatórios

Você pode executar relatórios do Mobile Service usando dados do Places Service enviados para o Adobe Analytics. No exemplo a seguir, os eventos são enviados quando os usuários têm entradas em um dos POIs. Neste relatório, um filtro do evento de entrada de POI foi adicionado sobre o relatório de usuário pronto para uso:

![Visualização de relatório](/help/assets/report-visualize.png)

Flexibilidade adicional na visualização de dados do Places Service está disponível nas interfaces do Adobe Analytics.
