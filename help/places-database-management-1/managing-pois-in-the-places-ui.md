---
title: Gerenciar POIs na interface do usuário do Places
seo-title: Gerenciar POIs na interface do usuário do Places
description: Use a interface do usuário do Places para gerenciar seus POIs.
seo-description: Use a interface do usuário do Places para gerenciar seus POIs.
translation-type: tm+mt
source-git-commit: 01617e4e1658f92234803baf1e57282777d04b13

---


# Gerenciar POIs na interface do usuário do Places

Os POIs e as bibliotecas são criados e gerenciados no banco de dados Locais usando a interface do usuário Locais.

## Definição de um POI de geofence

Geofences são um tipo de POI e são definidos no banco de dados com base nas seguintes chaves:

| Teclas | Descrição | Obrigatório? |
| :--- | :--- | :--- |
| ID | Identificador exclusivo atribuído a cada POI | Sim |
| Nome | Nome amigável dado ao POI | Sim |
| Biblioteca | Cada POI deve receber uma biblioteca para a organização | Sim |
| Ícone | Auxiliar com visualizações dos POIs | Sim (padrão atribuído) |
| Cor do canal | Auxiliar com visualizações dos POIs | Sim (padrão atribuído) |
| Categoria | Atribua uma estrutura comum de categorias comuns em todos os POIs em todas as bibliotecas | Não |
| Endereço | Endereço | Não |
| Cidade | cidade do POI | Não |
| Estado/Região | estado ou região do POI | Não |
| País | país do POI | Não |
| Latitude | Coordenada Latitude para o centro do POI | Sim |
| Longitude | Coordenadas de longitude para o centro do POI | Sim |
| Metadados | pares de chaves + valores personalizados que podem ser atribuídos aos POIs. Esses metadados simplificam fluxos de trabalho futuros permitindo agrupar POIs em bibliotecas para cada uma usar regras e filtros em fluxos de trabalho de downstream, como enviar uma notificação por push sempre que alguém entrar em um POI com Tipo = Concorrente. | Não |

## Crie um POI {#create-a-poi}

Um ponto de interesse (POI) é um local ou ponto em um mapa que é de seu interesse. Pode incluir locais como cafés, restaurantes e assim por diante.

1. Faça logon no Adobe Places com sua Adobe ID.
2. No lado superior direito, clique no ícone que se parece com uma lista com marcadores e clique em **[!UICONTROL New]**.
3. Digite um nome para seu POI.
4. Selecione ou adicione uma biblioteca.
5. Insira ou selecione um raio.

   a. Selecione um ícone para seu POI.
b.b. Selecione uma cor para o ícone.

6. Expanda a **[!UICONTROL Location]** seção.

   a. Digite um endereço.

   b. Digite a cidade.

   c. Digite o nome do estado.

   d. Digite o nome do país.

   e. Selecione ou insira uma latitude ou longitude.

   f.Clique em **[!UICONTROL Drop Pin on Map]**.

7. Expanda a **[!UICONTROL Metadata]** seção e clique em **[!UICONTROL Add Metadata]**.

   a. Digite o nome da chave.

   b. Digite o valor da chave.

8. Clique em **[!UICONTROL Confirm]** e em **[!UICONTROL  Save]**.

## Editar um POI

1. Faça logon nos locais usando sua Adobe ID.
1. Faça logon no Adobe Places Service usando sua Adobe ID.
1. No lado superior direito, clique no ícone que se parece com uma lista com marcadores.
1. Localize o POI que deseja editar.
1. Clique **[!UICONTROL ...]** e selecione **[!UICONTROL View Details]**.
1. Atualize as informações e clique em **[!UICONTROL Save]**.

## Excluir um POI

1. Faça logon nos locais usando sua Adobe ID.
1. Faça logon no Adobe Places Service usando sua Adobe ID.
1. No lado superior direito, clique no ícone que se parece com uma lista com marcadores.
1. Localize o POI que deseja excluir.
1. Clique **[!UICONTROL ...]** e selecione **[!UICONTROL Delete]**.

## Filtrar POIs por cidade, estado, país ou metadados

1. Faça logon no Adobe Places Service usando sua Adobe ID.
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

