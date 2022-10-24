---
title: Criação de uma regra para sua propriedade do Places Service
description: O SDK do Places acompanha o local atual, monitora os POIs configurados ao redor do local atual e rastreia os eventos de entrada e saída desses POIs.
exl-id: dd5aa7ac-55f9-44dc-8632-e483ef3b91a0
source-git-commit: 010de286c25c1eeb989fb76e3c2adaa82ac9fd35
workflow-type: tm+mt
source-wordcount: '927'
ht-degree: 15%

---

# Criar regras de entrada e saída {#create-entry-exit-rules}

Com a extensão do Places e uma solução de monitoramento de região instaladas no aplicativo móvel, é possível criar regras no Adobe Experience Platform Launch que são acionadas ou condicionadas aos dados de localização, incluindo eventos de entrada de local e de saída.

## Regras

Você pode configurar uma regra, que é composta de um evento, uma condição e uma ação. Cada regra é composta do seguinte:

* Um ou mais eventos
* (Opcional) condições
* Uma ou mais ações

### Eventos do Places Service

O Places Service oferece os seguintes eventos nos quais você pode executar uma regra:

* **Inserir POI**, que é acionado pelo SDK do Places quando o cliente entra no POI configurado.
* **Saída do POI**, que é acionado pelo SDK do Places quando o cliente sai do POI configurado.

### Condições do Places Service

As condições definem os critérios que os dados associados ao evento, ou o estado compartilhado de uma extensão nessa instância, devem atender para que a ação seja tomada. Por exemplo, você pode definir uma condição para acionar uma ação em uma entrada em uma cafeteria somente na cidade de São Francisco.

O SDK do Places mantém os seguintes estados:

* POI atual, que se refere ao POI no qual seu cliente está localizado no momento.
* Último POI de saída, que se refere ao POI mais recente do qual seu cliente saiu.
* Último POI inserido, que se refere ao POI mais recente inserido pelo cliente.

Cada POI contém os seguintes elementos de dados:

* ID
* Nome
* Latitude/longitude
* Raio
* Metadados como cidade, país, estado, categoria

### Ações

As ações definem o que o aplicativo fará em resposta à condição para a regra ser atendida para o evento acionado. Por exemplo, quando seu cliente entra no POI, você pode configurar uma mensagem de boas-vindas para ser exibida em seu dispositivo móvel.

## Criar uma regra: um exemplo

>[!CAUTION]
>
>Este exemplo pressupõe que você criou uma biblioteca de POI de todas as cafeterias dos Estados Unidos. Para obter mais informações sobre como criar POIs e bibliotecas, consulte [Criar um POI](/help/poi-mgmt-ui/create-a-poi-ui.md) e *Criar uma biblioteca* em [Gerenciar várias bibliotecas](https://docs.adobe.com/content/help/en/places/using/poi-mgmt-ui/manage-libraries-in-the-places-ui.html).

O procedimento a seguir é um exemplo de como criar uma regra que envia uma publicação de volta ao Slack quando você entra em uma cafeteria em São Francisco.

O evento, a condição e a ação são definidos das seguintes maneiras:

* **Evento**: Evento de entrada do Places.
* **Condição**: a cidade do **POI atual** é São Francisco
* **Ação**: Envie um postback para o Slack do nome da cafeteria em que seu cliente entrou.

### Pré-requisitos

Antes de criar uma regra, você deve criar um elemento de dados no Adobe Experience Platform Launch. Os elementos de dados preenchem automaticamente as informações necessárias sobre o POI na mensagem de postback.

Para criar um elemento de dados no Experience Platform Launch:

1. Clique no botão **Elementos de dados** guia .
1. Clique em **Adicionar elemento de dados**.
1. Digite um nome, por exemplo, **Nome atual da cafeteria**.
1. No **Extensão** , selecione **Places - Beta**.
1. Em **Elemento de dados**, selecione **Cidade**.
1. No painel direito, selecione **POI atual**.
1. Clique em **Salvar**.

### Criar uma regra no Experience Platform Launch para o Places Service

![criação de uma regra](/help/assets/placesrule.png)

1. Em Experience Platform Launch, clique na guia **[!UICONTROL Regras]**.
1. Clique em **[!UICONTROL Adicionar regra]**.
1. Digite um nome para a regra, por exemplo, **[!UICONTROL Rastrear entrada para cafeteria em SF]**.

### Criar um evento

1. Na seção Eventos , clique em **[!UICONTROL + Adicionar]**. Os eventos determinam quando você deseja que a regra seja acionada.
1. No **[!UICONTROL Extensão]** , selecione **[!UICONTROL Places - Beta]**.
1. Na lista suspensa **[!UICONTROL Tipo de evento]**, selecione **[!UICONTROL Inserir POI]**.
1. Em **[!UICONTROL Nome]**, digite um nome para o evento, por exemplo, **[!UICONTROL Entrar em uma cafeteria]**.
1. Clique em **[!UICONTROL Manter alterações]**.

### Criar uma condição

1. Na seção Condições , clique em **[!UICONTROL +Adicionar]**. As condições determinam quais os critérios a cumprir para a ação a empreender.
1. Em **[!UICONTROL Tipo de lógica]**, selecione Regular, o que permite que as ações sejam executadas se a condição for atendida.
1. No **[!UICONTROL Extensão]** , selecione **[!UICONTROL Places - Beta]**.
1. Em **[!UICONTROL Tipo de condição]**, selecione **[!UICONTROL Cidade]**.
1. Digite um nome de condição, por exemplo, **[!UICONTROL Loja de café no SF]**.
1. No painel direito, clique em **[!UICONTROL POI atual]** e, na lista suspensa, selecione **[!UICONTROL São Francisco]** como uma das cidades.
1. Clique em **[!UICONTROL Manter alterações]**.

### Criar uma ação

1. No **[!UICONTROL Ações]** seção , clique em **[!UICONTROL + Adicionar]**.
1. No **[!UICONTROL Extensão]** , deixe o padrão **[!UICONTROL Mobile Core]** opção selecionada.
1. Selecione um tipo de ação, por exemplo, **[!UICONTROL Enviar postback]**.

   a. Em **[!UICONTROL URL]**, digite o URL de postback para o Slack, por exemplo, `https://hooks.slack.com/services/`.

   b. Para enviar um corpo de publicação, selecione a variável **[!UICONTROL Adicionar corpo da publicação]** caixa de seleção.

   c. **[!UICONTROL Corpo da postagem]**, adicione o corpo da publicação, por exemplo: `{ "text": "A customer has entered" }`

   c. Digite um tipo de conteúdo, por exemplo **[!UICONTROL application/json]**.

   d. Selecione um valor de tempo limite, por exemplo, **[!UICONTROL 5]**.

1. Clique em **[!UICONTROL Manter alterações]**.

### Publicar a regra

1. Para ativar a regra, você deve publicá-la. Para obter mais informações sobre como publicar sua regra no Experience Platform Launch, consulte [Publicação](https://docs.adobe.com/content/help/pt-BR/launch/using/reference/publish/overview.html).

### Pensando além das entradas e saídas

Usar entradas e saídas de geolocalização do Places Service para acionar regras no Experience Platform Launch é incrivelmente poderoso, mas você também pode usar os dados de localização como uma condição para que outros eventos sejam acionados. Por exemplo, você pode ter um acionador de evento de Ação de rastreamento principal móvel pronto para ser disparado com base em um evento de chamada trackAction específico dentro do aplicativo. Com base nesse evento, você pode colocar condições de localização adicionais ao evento antes que uma ação seja executada. Por exemplo, abra uma pesquisa no aplicativo quando uma compra `trackAction` ocorre, mas **only** se o local atual do usuário incluir metadados específicos do Places Service.

![criar uma condição](/help/assets/places-condition.png)
