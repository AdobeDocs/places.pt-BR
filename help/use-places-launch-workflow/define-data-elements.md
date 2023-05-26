---
title: Definir elementos de dados
description: Esta seção fornece informações sobre como criar, usar e publicar elementos de dados no Experience Platform Launch for Places.
exl-id: 57e88a37-0b0b-4064-ab72-382a36a0d01d
source-git-commit: 4ab15ded930b31e4e06920af31f37fdfe45df8eb
workflow-type: tm+mt
source-wordcount: '485'
ht-degree: 1%

---

# Definir um elemento de dados {#define-data-elements}

As informações a seguir ajudam a entender os elementos de dados e como criá-los e publicá-los.

## Sobre elementos de dados

Os elementos de dados são os blocos fundamentais do dicionário de dados do aplicativo e são usados para coletar, organizar e fornecer dados em toda a tecnologia de marketing e anúncios.

Um elemento de dados é uma variável na qual o valor pode ser mapeado para uma ID de visitante, um Nome da operadora, uma ID de publicidade, uma ID de push e assim por diante. No Experience Platform Launch, é possível fazer referência a esse valor pelo nome da variável. Essa coleção de elementos de dados se torna o dicionário de dados definidos que você pode usar para criar suas regras (eventos, condições e ações) e esse dicionário é compartilhado no Experience Platform Launch, onde pode ser usado com qualquer extensão em sua propriedade.

Com a extensão Places, você pode fazer referência a valores dos seguintes destinos:

* POI atual, que se refere ao POI no qual seu cliente está localizado no momento.

   Se o usuário estiver localizado em vários POIs, o que pertencer à biblioteca com classificação mais alta será escolhido. Se vários POIs pertencerem à biblioteca de classificação mais alta, aquele com o menor raio será escolhido.
* Último POI de saída, que se refere ao POI mais recente do usuário.
* Último POI inserido, que se refere ao POI mais recente que o usuário inseriu.

Cada POI contém as seguintes referências de dados:

* **[!UICONTROL Categoria]**: categoria do POI
* **[!UICONTROL Cidade]**: cidade do POI
* **[!UICONTROL País]**: país do POI
* **[!UICONTROL Latitude]**: latitude do POI
* **[!UICONTROL Longitude]**: longitude do POI
* **[!UICONTROL Metadados]**: metadados personalizados do POI
* **[!UICONTROL Nome]**: nome do POI
* **[!UICONTROL Raio]**: raio do POI
* **[!UICONTROL ID da região]**: ID do POI
* **[!UICONTROL Região/Estado]**: região, província ou estado do POI

### Criar um elemento de dados

1. Na página Propriedade do seu aplicativo, clique na guia **[!UICONTROL Elementos de dados]** guia.

1. Clique em **[!UICONTROL Criar novo elemento de dados]**.

1. Na lista de extensões instaladas, localize **[!UICONTROL Places]**.

1. No **[!UICONTROL Tipo de elemento de dados]** selecione uma referência de dados para esse elemento de dados.

1. Selecione um destino de POI.

1. Se esse elemento de dados for uma referência de metadados personalizada, selecione uma chave de metadados.

1. Digite um nome para o elemento de dados e clique em **[!UICONTROL Salvar]**.

   ![Criar elemento de dados](/help/assets/create-de-7-v3.png)


## Usar um elemento de dados

Depois que um elemento de dados for criado, se um seletor de elemento de dados estiver presente, você poderá usar o elemento de dados de qualquer componente de regra.

![Usar o elemento de dados](/help/assets/use-de-v2.png)

Se um seletor de elemento de dados não estiver presente no componente de regra, você poderá usar o elemento de dados vinculando o nome do elemento de dados com o **[!UICONTROL %%]** tokens.
Por exemplo, se o nome do elemento de dados for **[!UICONTROL Cidade do Último POI]**, você pode adicionar **[!UICONTROL Cidade do ÚLTIMO POI]** para uma entrada de texto.


## Publicar elementos de dados

Se os elementos de dados forem usados em qualquer um dos componentes da regra, esses elementos de dados também deverão ser incluídos na biblioteca e publicados.
