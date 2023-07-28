---
title: Utilização do Places Service com Mobile Services para mensagens
description: Esta seção mostra como usar o Places Service com o Mobile Services para mensagens.
exl-id: dfa6b8bb-6bf2-44eb-8bfc-87294807ec3b
source-git-commit: d5c216aebd99ffef01c37c17c62576835b52438b
workflow-type: tm+mt
source-wordcount: '343'
ht-degree: 1%

---

# Adobe Mobile Services {#places-mobile-services}

Antes de usar a extensão Mobile Services para mensagens, verifique os seguintes pré-requisitos:

* Pontos de interesse foram criados no Places Service. Para obter mais informações, consulte [Criar um POI](/help/poi-mgmt-ui/create-a-poi-ui.md).

  >[!IMPORTANT]
  >
  >O Places Service inclui um banco de dados de POI novo e aprimorado para sua organização, que existe fora da interface herdada do Mobile Services. POIs localizados no Mobile Service *Gerenciar locais* A navegação de página só funcionará com a versão 4 do SDK.

* Aqui está o *Gerenciar locais* Página de gerenciamento de POI na interface herdada do Mobile Services para versões mais antigas do SDK:

  ![Interface herdada](/help/assets/legacy-location-v4-ui.png)

* Esta é a interface do usuário do Places Service:

  ![Interface do usuário de gerenciamento de POI do Places Service](/help/assets/places-ui.png)

* O SDK do ACP está configurado corretamente com a extensão do Places.

  Isso significa que os dados estão disponíveis como eventos e/ou condições no mecanismo de regras do Experience Platform Launch para seu aplicativo móvel. Para obter mais informações, consulte [Extensão do Places](/help/places-ext-aep-sdks/places-extension/places-extension.md).

* Familiarize-se com a criação e a publicação de regras de Experience Platform Launch para o SDK do ACP em seu aplicativo móvel.

  Para obter mais informações, consulte [Mecanismo de regras](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/mobile-core/rules-engine).

* Os elementos de dados Experience Platform Launch são criados a partir dos dados da extensão Places que serão usados no mecanismo Regras.

  Para obter mais informações, consulte [Elementos de dados](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/mobile-core/rules-engine#data-elements).

## Relatórios

Antes de usar os relatórios, conclua os seguintes pré-requisitos:

* Os dados do Serviço de locais foram enviados com sucesso para o Conjunto de relatórios do Adobe Analytics.

  Para obter mais informações, consulte [Usar o Places Service com o Adobe Analytics](/help/use-places-with-other-solutions/places-adobe-analytics/use-places-adobe-analytics.md).

* Familiarize-se com os relatórios do Mobile Services.

  Para obter mais informações, consulte [Relatórios](https://experienceleague.adobe.com/docs/discontinued/using/mobile-services.html).

## Visualização de relatórios

Você pode executar relatórios do Mobile Service usando dados do Places Service enviados para a Adobe Analytics. No exemplo a seguir, os eventos são enviados quando os usuários têm entradas em um dos POIs. Neste relatório, um filtro do evento de entrada de POI foi adicionado ao relatório de usuário pronto para uso:

![Visualização de relatório](/help/assets/report-visualize.png)

Flexibilidade adicional na visualização de dados do Places Service está disponível nas interfaces do Adobe Analytics.
