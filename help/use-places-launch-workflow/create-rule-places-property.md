---
title: Criação de uma regra para sua propriedade Locais
seo-title: Criação de uma regra para sua propriedade Locais
description: 'O SDK de Locais controla o local atual, monitora os POIs configurados em torno do local atual e rastreia os eventos de entrada e saída desses POIs. '
seo-description: 'O SDK de Locais controla o local atual, monitora os POIs configurados em torno do local atual e rastreia os eventos de entrada e saída desses POIs. '
translation-type: tm+mt
source-git-commit: f6c92bbd4fb21999f5c96ea0df8ede6919d1bc79

---


# Criar uma regra para sua propriedade Locais {#creating-rule-places-property}

O SDK do Serviço de Localização controla o local atual, monitora os POIs configurados em torno do local atual e acompanha os eventos de entrada e saída desses POIs.

## Regras

Você pode configurar uma regra, que é composta de um evento, uma condição e uma ação. Cada regra é composta do seguinte:

* Um ou mais eventos
* (Opcional) condições
* Uma ou mais ações

### Eventos

Os locais oferecem os seguintes eventos nos quais você pode executar uma regra:

* **[!UICONTROL Enter POI]**, que é acionada pelo SDK de Locais quando o cliente entra no POI configurado.
* **[!UICONTROL Exit POI]**, que é acionada pelo SDK de Locais quando seu cliente sai do POI configurado.

### Condições

As condições definem os critérios que os dados associados ao evento, ou o estado compartilhado de uma extensão nessa instância, devem atender para que a ação seja tomada. Por exemplo, você pode definir uma condição para acionar uma ação em uma entrada em uma cafeteria somente na cidade de São Francisco.

O SDK do Serviço de Localização mantém os seguintes estados:

* POI atual, que se refere ao POI no qual seu cliente está localizado no momento.
* Último POI encerrado, que se refere ao POI mais recente que seu cliente saiu.
* Último POI inserido, que se refere ao POI mais recente inserido pelo cliente.

Cada POI contém os seguintes elementos de dados:

* ID
* Nome:
* Latitude/longitude
* Raio
* Metadados como cidade, país, estado, categoria

### Ações

As ações definem o que o aplicativo fará em resposta à condição para a regra ser atendida para o evento acionado. Por exemplo, quando seu cliente entra no POI, você pode configurar uma mensagem de boas-vindas para ser exibida em seu dispositivo móvel.

## Criar uma regra: exemplo

>[!CAUTION]
>
>Este exemplo supõe que você tenha criado uma biblioteca POI de todas as cafeterias nos Estados Unidos. Para obter mais informações sobre como criar POIs e bibliotecas, consulte [Criar um POI](/help/poi-mgmt-ui/create-a-poi-ui.md) e consulte *Criar uma biblioteca* em [Gerenciar bibliotecas na interface do usuário](/help/poi-mgmt-ui/manage-libraries-in-the-places-ui.md)do Places.

O procedimento a seguir é um exemplo de como criar uma regra que envie uma publicação de volta para a Esquerda quando você entra em uma cafeteria em São Francisco.

O evento, a condição e a ação são definidos das seguintes maneiras:

* **Evento**: Evento de entrada do Serviço de Localização.
* **Condição**: A cidade do POI **atual** é São Francisco
* **Ação**: Envie um postback para a Sunders o nome da cafeteria que seu cliente inseriu.

### Pré-requisitos

Antes de criar uma regra, você deve criar um elemento de dados no Experience Platform Launch. Os elementos de dados preenchem automaticamente as informações necessárias sobre seu POI na mensagem de postback.

Para criar um elemento de dados no Experience Platform Launch:

1. Click the **[!UICONTROL Data Elements]** tab.
2. Clique em **[!UICONTROL Add Data Element]**.
3. Type a name, for example, **[!UICONTROL Current coffee shop name]**.
4. Na lista **[!UICONTROL Extension]** suspensa, selecione **[!UICONTROL Places – Beta]**.
5. Em **[!UICONTROL Data Element]**, selecione **[!UICONTROL City]**.
6. No painel direito, selecione POI **atual**.
7. Clique em **[!UICONTROL Save]**.

### Criar uma regra no Experience Platform Launch for Location Service

![](//help/assets/create-a-rule.png)

1. Em Experience Platform Launch, clique na **[!UICONTROL Rules]** guia.
2. Clique em **Adicionar regra**.
3. Digite um nome para a regra, por exemplo, **Rastrear entrada para cafeteria no SF**.

### Criar um evento

1. Na seção Eventos, clique em **[!UICONTROL + Add]**. Os eventos determinam quando você deseja que a regra seja acionada.
2. Na lista **[!UICONTROL Extension]** suspensa, selecione **[!UICONTROL Places – Beta]**.
3. Na lista **[!UICONTROL Event Type]** suspensa, selecione **[!UICONTROL Enter POI]**.
4. Em **[!UICONTROL Name]**, digite um nome para o evento, por exemplo, **[!UICONTROL Entering a coffee shop]**.
5. Clique em **[!UICONTROL Keep Changes]**.

### Criar uma condição

1. Na seção Condições, clique em **[!UICONTROL +Add]**. As condições determinam os critérios a cumprir para a ação a empreender.
2. Em **[!UICONTROL Logic Type]**, selecione Regular, o que permite que as ações sejam executadas se a condição for atendida.
3. Na lista suspensa **Extensão** , selecione **[!UICONTROL Places – Beta]**.
4. Em **[!UICONTROL Condition Type]**, selecione **[!UICONTROL City]**.
5. Type a condition name, for example, **[!UICONTROL Coffee shop in SF]**.
6. No painel direito, clique em **[!UICONTROL Current POI]** e, na lista suspensa, selecione **[!UICONTROL San Francisco]** como uma de suas cidades.
7. Clique em **[!UICONTROL Keep Changes]**.

### Criar uma ação

1. Na **[!UICONTROL Actions]** seção, clique em **[!UICONTRO+ Adicionar]**.
2. Na lista suspensa **[!UICONTRO Extensão]** , deixe a opção padrão **[!UICONTRO Mobile Core]** selecionada.
3. Selecione um tipo de ação, por exemplo, **[!UICONTRO Enviar postback]**.

   a. Em **[!UICONTROL URL]**, digite o URL de postback para a falta, por exemplo, `https://hooks.slack.com/services/`.

   b. Para enviar um corpo da publicação, marque a caixa de seleção **[!UICONTRO Adicionar corpo]** da publicação.

   c. No corpo da **[!UICONTRO postagem]**, adicione o corpo da postagem, por exemplo: `{ "text": "A customer has entered" }`

   c. Digite um tipo de conteúdo, por exemplo, **[!UICONTRO application/json]**.

   d. Selecione um valor de tempo limite, por exemplo, **5**.

4. Click **[!UICONTRO Keep Changes]**.

### Publicar a regra

1. Para ativar a regra, é necessário publicá-la. Para obter mais informações sobre como publicar sua regra no Experience Platform Launch, consulte [Publicação](https://docs.adobelaunch.com/launch-reference/publishing).