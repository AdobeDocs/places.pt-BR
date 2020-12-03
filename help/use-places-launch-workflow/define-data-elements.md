---
title: Definir elementos de dados
description: Esta seção fornece informações sobre como criar, usar e publicar elementos de dados no Experience Platform Launch for Places.
translation-type: tm+mt
source-git-commit: c22efc36f2eac6b20fc555d998c3988d8c31169e
workflow-type: tm+mt
source-wordcount: '456'
ht-degree: 1%

---


# Definir um elemento de dados {#define-data-elements}

As informações a seguir ajudam você a entender os elementos de dados e como criá-los e publicá-los.

## Sobre elementos de dados

Os elementos de dados são os elementos básicos para o dicionário de dados do aplicativo e são usados para coletar, organizar e fornecer dados em toda a tecnologia de publicidade e marketing.

Um elemento de dados é uma variável na qual o valor pode ser mapeado para uma ID de Visitante, um Nome da operadora, uma ID de anúncio, uma ID de push e assim por diante. No Experience Platform Launch, é possível fazer referência a esse valor pelo nome da variável. Essa coleção de elementos de dados se torna o dicionário de dados definidos que você pode usar para criar suas regras (eventos, condições e ações), e esse dicionário é compartilhado no Experience Platform Launch, onde pode ser usado com qualquer extensão em sua propriedade.

Com a extensão Locais, é possível fazer referência aos valores dos seguintes públicos alvos:

* POI atual, que se refere ao POI no qual seu cliente está localizado no momento.

   Se o usuário estiver localizado em vários POIs, o que pertence à biblioteca com classificação mais alta será escolhido. Se vários POIs pertencerem à biblioteca de classificação mais alta, o com o menor raio será escolhido.
* Último POI encerrado, que se refere ao POI mais recente que o usuário saiu.
* Último POI inserido, que se refere ao POI mais recente inserido pelo usuário.

Cada POI contém as seguintes referências de dados:

* **[!UICONTROL Category]**: categoria do POI
* **[!UICONTROL City]**: cidade do POI
* **[!UICONTROL Country]**: país do POI
* **[!UICONTROL Latitude]**: latitude do POI
* **[!UICONTROL Longitude]**: longitude do POI
* **[!UICONTROL Metadata]**: metadados personalizados do POI
* **[!UICONTROL Name]**: nome do POI
* **[!UICONTROL Radius]**: raio do POI
* **[!UICONTROL Region ID]**: ID do POI
* **[!UICONTROL Region/State]**: região, província ou estado do POI

### Criar um elemento de dados

1. Na página Propriedade do aplicativo, clique na **[!UICONTROL Data Elements]** guia.

1. Clique em **[!UICONTROL Create New Data Element]**.

1. Na lista das extensões instaladas, localize **[!UICONTROL Places]**.

1. Na lista **[!UICONTROL Data Element Type]** suspensa, selecione uma referência de dados para esse elemento de dados.

1. Selecione um público alvo POI.

1. Se esse elemento de dados for uma referência de metadados personalizada, selecione uma chave de metadados.

1. Digite um nome para o elemento de dados e clique em **[!UICONTROL Save]**.

   ![Criar elemento de dados](/help/assets/create-de-7-v3.png)


## Usar um elemento de dados

Depois que um elemento de dados é criado, se um seletor de elemento de dados estiver presente, você pode usar o elemento de dados de qualquer componente de regra.

![Usar o elemento de dados](/help/assets/use-de-v2.png)

Se um seletor de elementos de dados não estiver presente no componente de regra, você pode usar o elemento de dados vinculando o nome do elemento de dados aos **[!UICONTROL %%]** tokens.
Por exemplo, se o nome do elemento de dados for **[!UICONTROL Last POI City]**, você poderá adicionar **[!UICONTROL LAST POI City]** a uma entrada de texto.


## Publicar elementos de dados

Se os elementos de dados forem usados em qualquer um dos componentes da regra, eles também deverão ser incluídos na biblioteca e publicados.
