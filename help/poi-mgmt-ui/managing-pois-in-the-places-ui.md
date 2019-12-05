---
title: Gerenciar POIs existentes
description: Na interface do usuário do Serviço de Localização, é possível editar, excluir ou filtrar POIs existentes.
translation-type: tm+mt
source-git-commit: 5a0705f02c8ecd540506b628371aec45107df7b2

---


# Gerenciar POIs existentes {#managing-existing-pois}

Os POIs e as bibliotecas são criados e gerenciados no banco de dados Locais usando a interface do usuário Locais.

## Editar um POI

1. Faça logon nos locais usando sua Adobe ID.
1. Faça logon no Serviço de locais usando sua Adobe ID.
1. No lado superior direito, clique no ícone que se parece com uma lista com marcadores.
1. Localize o POI que deseja editar.
1. Clique **[!UICONTROL ...]** e selecione **[!UICONTROL View Details]**.
1. Atualize as informações e clique em **[!UICONTROL Save]**.

## Excluir um POI

1. Faça logon nos locais usando sua Adobe ID.
1. Faça logon no Serviço de locais usando sua Adobe ID.
1. No lado superior direito, clique no ícone que se parece com uma lista com marcadores.
1. Localize o POI que deseja excluir.
1. Clique **[!UICONTROL ...]** e selecione **[!UICONTROL Delete]**.

## Filtrar POIs por cidade, estado, país ou metadados

![filtrar um POI](/help/assets/filter_poi.png)

1. Faça logon na interface do usuário do Serviço de localização usando sua Adobe ID.
1. No lado superior direito, clique no ícone de filtragem.
1. É possível filtrar POIs de uma das seguintes maneiras:

   * Por biblioteca:

      a. Selecione uma biblioteca.

   * Por propriedade:

      a. Na lista suspensa Propriedade, selecione **[!UICONTROL Country]**, **[!UICONTROL State]** ou **[!UICONTROL City]**.

      b. Na linha seguinte, insira um valor.

      Por exemplo, você pode selecionar **[!UICONTROL State]** e digitar **[!UICONTROL California]**.

   * Com metadados:

      a. Insira uma chave e um valor.

## Definição de um POI de geofence

Geofences são um tipo de POI e são definidos no banco de dados com base nas seguintes chaves:

| Teclas | Descrição | Obrigatório? |
| :--- | :--- | :--- |
| ID | Identificador exclusivo atribuído a cada POI | Sim |
| Nome | Nome amigável dado ao POI. | Sim |
| Biblioteca | Cada POI deve receber uma biblioteca para a organização. | Sim |
| Ícone | Assistir a visualizações dos POIs. | Sim (padrão atribuído) |
| Cor do canal | Assistir a visualizações dos POIs. | Sim (padrão atribuído) |
| Categoria | Atribua uma estrutura comum de categorias comuns em todos os POIs em todas as bibliotecas. | Não |
| Endereço | Endereço. | Não |
| Cidade | Cidade do POI. | Não |
| Estado/Região | Estado ou região do POI. | Não |
| País | País do POI. | Não |
| Latitude | Coordenada Latitude para o centro do POI. | Sim |
| Longitude | Coordenada de longitude para o centro do POI. | Sim |
| Metadados | Pares personalizados de chave e valor que podem ser atribuídos aos POIs. Esses metadados simplificam fluxos de trabalho futuros permitindo agrupar POIs em bibliotecas para cada uma usar regras e filtros em fluxos de trabalho de downstream, como enviar uma notificação por push quando alguém entra em um POI com o Tipo = Concorrente. | Não |
