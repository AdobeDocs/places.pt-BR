---
title: Gerenciar POIs existentes
description: Na interface do serviço de Places, você pode editar, excluir ou filtrar os POIs existentes.
exl-id: a4cf28ae-1e3c-4724-bca3-ac1d0cd6da09
source-git-commit: 4ab15ded930b31e4e06920af31f37fdfe45df8eb
workflow-type: tm+mt
source-wordcount: '407'
ht-degree: 5%

---

# Gerenciar POIs existentes {#managing-existing-pois}

Os POIs e as bibliotecas são criados e gerenciados no banco de dados do Places usando a interface do usuário do Places.

## Editar um POI

1. Faça logon no Places usando a Adobe ID.
1. Faça logon no Places Service usando a Adobe ID.
1. No lado superior direito, clique no ícone que parece uma lista com marcadores.
1. Localize o POI que deseja editar.
1. Clique em **[!UICONTROL ...]** e selecione **[!UICONTROL Exibir Detalhes]**.
1. Atualize as informações e clique em **[!UICONTROL Salvar]**.

## Excluir um POI

1. Faça logon no Places usando a Adobe ID.
1. Faça logon no Places Service usando a Adobe ID.
1. No lado superior direito, clique no ícone que parece uma lista com marcadores.
1. Localize o POI que deseja excluir.
1. Clique em **[!UICONTROL ...]** e selecione **[!UICONTROL Excluir]**.

## Filtrar POIs por cidade, estado, país ou metadados

![filtrar um POI](/help/assets/filter_poi.png)

1. Faça logon na interface do usuário do Places Service usando a Adobe ID.
1. No lado superior direito, clique no ícone de filtragem.
1. Você pode filtrar POIs de uma das seguintes maneiras:

   * Por biblioteca:

     a. Selecione uma biblioteca.

   * Por propriedade:

     a. Na lista suspensa Propriedade, selecione **[!UICONTROL País]**, **[!UICONTROL Estado]** ou **[!UICONTROL Cidade]**.

     b. Na próxima linha, informe um valor.

     Por exemplo, você pode selecionar **[!UICONTROL Estado]** e digitar **[!UICONTROL Califórnia]**.

   * Com metadados:

     a. Insira uma chave e um valor.

## Definição de um POI de geofence

As geofences são um tipo de POI e são definidas no banco de dados com base nas seguintes chaves:

| Chaves | Descrição | Obrigatório? |
| :--- | :--- | :--- |
| ID | Identificador exclusivo atribuído a cada POI | Sim |
| Nome | Nome amigável dado ao POI. | Sim |
| Biblioteca | Cada POI deve ser atribuído a uma biblioteca por organização. | Sim |
| Raio | O raio do POI em metros. | Sim |
| Ícone | Auxiliar nas visualizações dos POIs. | Sim (padrão atribuído) |
| Cor | Auxiliar nas visualizações dos POIs. | Sim (padrão atribuído) |
| Categoria | Atribua uma estrutura comum de categorias que são comuns em todos os POIs em todas as bibliotecas. | Não |
| Endereço | Endereço. | Não |
| Cidade | Cidade do POI. | Não |
| Estado/Região | Estado do POI. | Não |
| País | País do POI. | Não |
| Latitude | Coordenada de latitude para o centro do POI. | Sim |
| Longitude | Coordenada de longitude do centro do POI. | Sim |
| Metadados | Pares de chave e valor personalizados que podem ser atribuídos a POIs. Esses metadados simplificam os workflows futuros permitindo agrupar POIs em bibliotecas para cada um usar regras e filtros em workflows downstream, como enviar uma notificação por push quando alguém insere um POI com o Tipo = Concorrente. | Não |
