---
title: Criação de uma regra para sua propriedade Locais
description: 'O SDK de Locais controla o local atual, monitora os POIs configurados em torno do local atual e rastreia os eventos de entrada e saída desses POIs. '
translation-type: tm+mt
source-git-commit: 5a0705f02c8ecd540506b628371aec45107df7b2

---


# Criar regras de entrada e saída {#create-entry-exit-rules}

Com as extensões do Monitor de locais e locais instaladas em seu aplicativo móvel, você pode criar regras no Adobe Experience Platform Launch que são acionadas ou condicionadas pelos dados de localização, incluindo eventos de entrada e saída.

## Regras

Você pode configurar uma regra, que é composta de um evento, uma condição e uma ação. Cada regra é composta do seguinte:

* Um ou mais eventos
* (Opcional) condições
* Uma ou mais ações

### Eventos de local

Os locais oferecem os seguintes eventos nos quais você pode executar uma regra:

* **Insira o POI**, que é acionado pelo SDK de Locais quando o cliente entra no POI configurado.
* **Saia do POI**, que é acionado pelo SDK de Locais quando seu cliente sai do POI configurado.

### Condições de locais

As condições definem os critérios que os dados associados ao evento, ou o estado compartilhado de uma extensão nessa instância, devem atender para que a ação seja tomada. Por exemplo, você pode definir uma condição para acionar uma ação em uma entrada em uma cafeteria somente na cidade de São Francisco.

O SDK de Locais mantém os seguintes estados:

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
>Este exemplo pressupõe que você criou uma biblioteca de POI de todas as cafeterias dos Estados Unidos. For more information about creating POIs and libraries, see [Create a POI](/help/poi-mgmt-ui/create-a-poi-ui.md) and *Create a Library* in [Manage multiple libraries](https://docs.adobe.com/content/help/en/places/using/poi-mgmt-ui/manage-libraries-in-the-places-ui.html).

O procedimento a seguir é um exemplo de como criar uma regra que envie uma publicação de volta para a Esquerda quando você entra em uma cafeteria em São Francisco.

O evento, a condição e a ação são definidos das seguintes maneiras:

* **Evento**: Insere o evento de entrada.
* **Condição**: a cidade do **POI atual** é São Francisco
* **Ação**: Envie um postback para a Sunders o nome da cafeteria que seu cliente inseriu.

### Pré-requisitos

Antes de criar uma regra, você deve criar um elemento de dados no Adobe Experience Platform Launch. Os elementos de dados preenchem automaticamente as informações necessárias sobre seu POI na mensagem de postback.

Para criar um elemento de dados no Experience Platform Launch:

1. Clique na guia Elementos **de** dados.
1. Click **Add Data Element**.
1. Digite um nome, por exemplo, o nome **atual da cafeteria**.
1. Na lista suspensa **Extensão** , selecione **Locais - Beta**.
1. Em **Elemento de dados**, selecione **Cidade**.
1. No painel direito, selecione POI **atual**.
1. Clique em **Salvar**.

### Criar uma regra no Experience Platform Launch for Places

![criação de uma regra](/help/assets/placesrule.png)

1. In Experience Platform Launch, click the **[!UICONTROL Rules]**tab.
1. Clique em **[!UICONTROL Add Rule]**.
1. Digite um nome para a regra, por exemplo, **[!UICONTROL Track entry for coffee shop in SF]**.

### Criar um evento

1. Na seção Eventos, clique em **[!UICONTROL + Add]**. Os eventos determinam quando você deseja que a regra seja acionada.
1. Na lista **[!UICONTROL Extension]**suspensa, selecione**[!UICONTROL Places – Beta]**.
1. Na lista **[!UICONTROL Event Type]**suspensa, selecione**[!UICONTROL Enter POI]**.
1. Em **[!UICONTROL Name]**, digite um nome para o evento, por exemplo,**[!UICONTROL Entering a coffee shop]**.
1. Clique em **[!UICONTROL Keep Changes]**.

### Criar uma condição

1. Na seção Condições, clique em **[!UICONTROL +Add]**. As condições determinam os critérios a cumprir para a ação a empreender.
1. In **[!UICONTROL Logic Type]**, select Regular, which allows actions to execute if the condition is met.
1. Na lista **[!UICONTROL Extension]**suspensa, selecione**[!UICONTROL Places – Beta]**.
1. Em **[!UICONTROL Condition Type]**, selecione**[!UICONTROL City]**.
1. Type a condition name, for example, **[!UICONTROL Coffee shop in SF]**.
1. In the right pane, click **[!UICONTROL Current POI]**, and in the drop-down list, select**[!UICONTROL San Francisco]** as one of your cities.
1. Clique em **[!UICONTROL Keep Changes]**.

### Criar uma ação

1. In the **[!UICONTROL Actions]**section, click**[!UICONTROL + Add]**.
1. Na lista **[!UICONTROL Extension]**suspensa, deixe a opção padrão**[!UICONTROL Mobile Core]** selecionada.
1. Selecione um tipo de ação, por exemplo, **[!UICONTROL Send Postback]**.

   a. Em **[!UICONTROL URL]**, digite o URL de postback para a falta, por exemplo,`https://hooks.slack.com/services/`.

   b. Para enviar um corpo de publicação, marque a caixa de **[!UICONTROL Add Post Body]**seleção.

   c. Em **[!UICONTROL Post Body]**, adicione o corpo da publicação, por exemplo:`{ "text": "A customer has entered" }`

   c. Digite um tipo de conteúdo, por exemplo **[!UICONTROL application/json]**.

   d. Selecione um valor de tempo limite, por exemplo, **[!UICONTROL 5]**.

1. Clique em **[!UICONTROL Keep Changes]**.

### Publicar a regra

1. Para ativar a regra, é necessário publicá-la. Para obter mais informações sobre como publicar sua regra no Experience Platform Launch, consulte [Publicação](https://docs.adobelaunch.com/launch-reference/publishing).

### Pensando além das entradas e saídas

O uso de entradas e saídas geográficas do Serviço de Localização para acionar regras no Experience Platform Launch é incrivelmente poderoso, mas você também pode usar os dados de localização como condição para que outros eventos sejam acionados. Por exemplo, você pode ter um acionador de evento Mobile Core Track Action pronto para disparar com base em um evento de chamada trackAction específico dentro do aplicativo. Com base nesse evento, você pode colocar condições de localização adicionais ao evento antes que uma ação seja executada. Por exemplo, abra uma pesquisa no aplicativo quando um `trackAction` evento de compra ocorrer, mas **somente** se o local atual do usuário incluir metadados específicos do Serviço de localização.

![criar uma condição](/help/assets/places-condition.png)