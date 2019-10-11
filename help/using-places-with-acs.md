---
title: Uso de locais com o Adobe Campaign Standard
seo-title: Uso de locais com o Adobe Campaign Standard
description: Ter um entendimento profundo das preferências e hábitos de seus clientes é fundamental para qualquer campanha de marketing bem-sucedida. Saber se um usuário visitou uma localização física também pode adicionar um contexto muito valioso para formar uma relação com o consumidor.
seo-description: Ter um entendimento profundo das preferências e hábitos de seus clientes é fundamental para qualquer campanha de marketing bem-sucedida. Saber se um usuário visitou uma localização física também pode adicionar um contexto muito valioso para formar uma relação com o consumidor.
translation-type: tm+mt
source-git-commit: d7c5fe5d7a20a647240114d25307373b493ae2f5

---


# Uso de locais com o Adobe Campaign Standard {#places-with-acs}

*Obrigado por nos visitar na semana passada, gostaríamos de te dar uma surpresa para usar na sua próxima visita!*

Ter um entendimento profundo das preferências e hábitos de seus clientes é fundamental para qualquer campanha de marketing bem-sucedida. Os itens que um usuário pesquisou e o histórico de compras anterior têm um grande papel na definição de metas de público-alvo. Saber se um usuário visitou uma localização física também pode adicionar um contexto muito valioso para formar uma relação com o consumidor.

De acordo com um relatório recente do eMarketer, 85% dos varejistas de alto desempenho acreditam que a localização é muito importante para seus esforços de marketing. Além disso, mais de 58% dos varejistas na América do Norte estão planejando investir em tecnologias de proximidade/localização para melhorar suas experiências com os clientes.

![](/help/assets/using-loc-services-acs_0.png)

Pense em como a localização é crítica na sua experiência de uso de smartphone. Com que frequência pede ao seu smartphone para encontrar restaurantes, postos de gasolina, mercearias ou outros serviços próximos?

Faz sentido, então, que, como marca, você esteja pensando em maneiras de aproveitar a localização em suas campanhas de marketing. Neste guia, mostraremos como você pode aproveitar o poder do Adobe Experience Platform Experience Platform Location Service para adicionar contexto de localização às mensagens por meio do Adobe Campaign Standard, permitindo que você obtenha notificações por push personalizadas ou mensagens no aplicativo com base na entrada do ponto de interesse histórico (POI).

Antes de começarmos, este guia presume que você tenha um aplicativo móvel configurado com o SDK do Adobe Experience Platform Mobile com a extensão do Adobe Campaign Standard. Além do SDK do Adobe Experience Platform Mobile e do Campaign Standard, você deve ter acesso ao Serviço de localização da plataforma Experience.

## Pré-requisitos

1. Integre o SDK [do](https://aep-sdks.gitbook.io/docs/getting-started/get-the-sdk) Adobe Experience Platform Mobile ao seu aplicativo.
1. Adicione o [Adobe Campaign Standard Extension](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-campaign-standard) à configuração do aplicativo móvel.
1. [Crie um ou mais POIs](/help/places-database-management-1/managing-pois-in-the-places-ui.md).

>[!TIP]
>
>Se você estiver procurando maneiras de fazer upload ou gerenciar POIs em massa, examine este [script para fazer upload de POIs de um arquivo CSV](https://github.com/adobe/places-scripts) . Além disso, as APIs [do](/help/places-rest-apis/api-usage/api-usage.md) Places podem ser usadas para criar ou gerenciar pontos de interesse.

Se você não tiver acesso aos Locais, poderá [solicitar acesso aqui](https://forms.office.com/Pages/ResponsePage.aspx?id=Wht7-jR7h0OUrtLBeN7O4fkr821yYptFo-ghlnlXCyhUM0dQVkJCSzVDMFNGWEFXWUUwNEJWSjhSRS4u).

### Ativar e instalar as extensões do Places no aplicativo

Depois de criar pontos de interesse na interface Locais, você precisará adicionar a funcionalidade Locais ao seu aplicativo.

1. Siga as instruções para ativar as extensões do Monitor de locais e locais em seu aplicativo.
1. Na extensão Locais, certifique-se de ter selecionado a biblioteca apropriada de POIs criados anteriormente.

   Bibliotecas adicionais podem ser adicionadas à configuração de extensão a qualquer momento.

1. Certifique-se de ter adicionado essas configurações a uma Biblioteca e publicado as alterações de configuração no Launch.
1. Na guia Ambiente **[de inicialização do]** UICONTROL, clique no ícone de instruções de instalação para exibir instruções sobre como baixar os arquivos apropriados do CocoaPod e Gradle para o projeto do aplicativo.
1. No aplicativo, siga as instruções para adicionar o modo de plano de fundo Local ao aplicativo e inicie o Monitor de localização de locais.
1. Teste seu aplicativo por meio de um simulador de dispositivo para ver a solicitação do aplicativo em pontos de interesse próximos com base na falsificação da localização do dispositivo.

### Criar elementos de dados no Experience Platform Launch

Depois de verificar se as extensões do Monitor de locais e locais estão funcionando corretamente no aplicativo, crie elementos de dados no Experience Platform Launch para ler as informações fornecidas pelas extensões e que estão passando pelo hub de eventos do SDK móvel. Os elementos de dados atuam essencialmente como um alias para recuperar dados do aplicativo cliente. Vamos criar alguns elementos de dados para recuperar dados das extensões do Local.

1. Na propriedade móvel do Experience Platform Launch, na **[!UICONTROL Data Elements]** guia e clique em **[!UICONTROL Add Data Element]**.
1. No menu de extensão, selecione **[!UICONTROL Places]**.
1. Na lista **[!UICONTROL Data Element]** suspensa, selecione **[!UICONTROL Name}**.
1. Na janela à direita, você pode selecionar qual recuperará **[!UICONTROL Current POI]** o nome do POI no qual o usuário está no momento.

   * **[!UICONTROL Last Entered]** recupera o nome do POI que o usuário inseriu por último em um
   * **[!UICONTROL Last Exited]** fornecerá o nome do POI que o usuário deixou por último.

1. Selecione **[!UICONTROL Last Entered]**.
1. Digite um nome para o elemento de dados, como **[!UICONTROL Last Entered POI Name]**, e clique em **[!UICONTROL Save]**.


   ![](/help/assets/using-loc-services-acs_1.png)

1. Repita as mesmas etapas acima e crie elementos de dados para *Última POI inserida Latitude*, *Última longitude* do POI inserido, Raio ** do POI inserido pela última vez.

Além dos elementos de dados do Places, verifique se você também criou elementos de dados do Mobile Core para a ID *do* aplicativo e a *Experience Cloud ID*.

### Criar uma regra para enviar dados de localização para o Adobe Campaign Standard

As regras no Experience Platform Launch permitem criar fluxos de trabalho complexos de várias soluções com base em acionadores de eventos. Você pode criar novas regras ou fazer alterações em regras existentes e ter as atualizações implantadas dinamicamente em seus aplicativos móveis. Neste exemplo, criaremos uma regra que é acionada quando um usuário entra em um POI geograficamente delimitado. Depois que a regra é acionada, uma atualização é enviada para o Campaign Standard para gravar uma entrada em um POI específico para o usuário. Esse POI é baseado na Experience Cloud ID.

1. Na propriedade móvel do Experience Platform Launch, clique na **[!UICONTROL Rules]** guia e clique em **[!UICONTROL Add Rule]**.
1. Na **[!UICONTROL Events]** seção, clique **[!UICONTROL +]** e selecione **[!UICONTROL Places]**.
1. Em **[!UICONTROL Event Type]**, selecione **[!UICONTROL Enter POI]**.
1. Digite um nome para a regra, por exemplo, **[!UICONTROL User entered POI]**.
1. Clique em **[!UICONTROL Keep Changes]**.
1. Deixe a **[!UICONTROL Conditions]** seção em branco.

   Esta seção permite que você filtre ou coloque restrições sobre quando esta regra deve ser acionada.

1. In the **[!UICONTROL Actions]** section, click **[!UICONTROL +]**.
1. Em **[!UICONTROL Extension]**, selecione **[!UICONTROL Mobile Core]** e, em **[!UICONTROL Action Type]**, selecione **[!UICONTROL Send Postback]**.

1. Para o URL, é necessário construir o terminal de locais do Campaign Standard.

   O URL deve ser semelhante ao abaixo. Certifique-se de usar os elementos de dados corretos que você criou anteriormente para o servidor do Campaign e a pKey.

   `https://{%%camp-server%%}/rest/head/mobileAppV5/{%%pkey%%}/locations/`

1. Clique na caixa para adicionar um corpo de publicação e enviar o seguinte:

   ```text
   {
   "locationData": {
   "distances": "{%%Last Entered POI Radius%%}",
   "poiLabel": "{%%Last Entered POI Name%%}",
   "latitude": "{%%Last Entered POI Lat%%}",
   "longitude": "{%%Last Entered POI Long%%}",
   "appId": "{%%AppID%%}",
   "marketingCloudId": “{%%ecid%%}”
   }
   }
   ```

1. Use os elementos de dados específicos criados na seção anterior.
1. Em **[!UICONTROL Content Type]**, digite **[!UICONTROL application/json]**.
1. Clique **[!UICONTROL Keep Changes]** depois de configurar.

   Pode ser útil configurar um gancho da Web Slow como uma ação adicional para validar que minha ação está sendo acionada e que os dados certos estão sendo coletados.

   >[!IMPORTANT]
   >
   >Lembre-se de publicar as alterações recentes no aplicativo para garantir que a regra e todos os seus elementos de dados sejam implantados como parte da configuração. Após a publicação, você deve reiniciar o aplicativo móvel para obter as atualizações de configuração mais recentes.

### Usar dados de localização para direcionar mensagens do Campaign Standard

Agora que temos dados de localização preenchidos no Campaign, podemos usar pontos de interesse como uma ferramenta de segmento de público-alvo.

1. Na instância do Adobe Campaign Standard, clique em **[UICONTROL Criar notificação]** por push.
1. Para o tipo de notificação por push, selecione **[UICONTROL Enviar push para assinantes]** do aplicativo.

   Esse tipo de push direcionará todos os usuários do aplicativo. Se os usuários móveis estiverem conectados a um perfil de campanha, você também poderá selecionar **[UICONTROL Enviar push para perfis]** de campanha i.

1. Clique **[!UICONTROL Next]** e digite os detalhes gerais na próxima tela.
1. Na tela Público-alvo, clique para ver quantos usuários estimados a notificação por push será enviada. **[!UICONTROL Count]**

   Nesse caso, a contagem é três, pois há três dispositivos instalados no aplicativo de teste.

1. Na barra lateral esquerda, expanda a **[!UICONTROL Profile]** guia e arraste o **[!UICONTROL POI location]** filtro para a área principal.
1. Na janela do filtro POI, digite o nome exato do POI que você deseja direcionar.

   Você pode fazer seleções adicionais para determinar o intervalo de tempo desde a última visita do usuário a esse POI.

   ![](/help/assets/using-loc-services-acs_2.png)

1. Clique em [!**Confirmar]UICONTROL**.
1. Execute a contagem novamente na parte superior para ver o tamanho do seu público-alvo mudar.

   Se você não estiver vendo sua atualização de contagem, talvez tenha inserido um nome POI para o qual nenhum dispositivo disparou uma entrada. Este é o local onde o gancho da Web Slow se torna valioso, como você pode ver uma lista de entradas de POI de vários dispositivos de teste.
1. Você pode arrastar outros filtros de localização de POI para incluir vários POIs na sua mensagem.
1. Clique **[!UICONTROL Next]** para concluir a criação da notificação por push para entrega.

   ![](/help/assets/using-loc-services-acs_3.png)

Além das notificações por push, também é possível usar dados de localização para segmentar quais usuários você gostaria de receber uma mensagem no aplicativo.

1. Na instância do Adobe Campaign Standard, clique em **[!UICONTROL Create In-App message]**.
1. Para o tipo de mensagem, selecione **[!UICONTROL Target all users of a Mobile application]**.
1. Clique **[!UICONTROL Next]** e digite os detalhes gerais na próxima tela.
1. No painel esquerdo, verifique se agora é possível usar vários acionadores relacionados a Locais.
1. Se o usuário tiver inserido uma fronteira geográfica POI, você poderá optar por exibir a mensagem no aplicativo.

   Você também pode usar os metadados definidos na interface do usuário do Places para filtrar seu público-alvo. Neste exemplo, eu quero disparar uma mensagem no aplicativo mostrada somente para usuários que saíram pela última vez de um POI que também tinha uma instalação de Gym. Talvez eu queira enviar uma pesquisa para ver se eles usaram/gostaram da academia.

1. Clique **[!UICONTROL Next]** para concluir a criação da mensagem no aplicativo para entrega.

   ![](/help/assets/using-loc-services-acs_4.png)

O uso do Places com o Adobe Campaign Standard oferece uma ferramenta muito poderosa para segmentar e direcionar suas mensagens aos usuários com base na localização do histórico. Essa simples integração abre a porta para a construção de casos de uso mais personalizados e contextuais.

Estamos constantemente melhorando os Locais e as soluções integradas para trazer o contexto de localização para os fluxos de trabalho móveis. Um produto que se beneficiará do Places é a solução da jornada acionada que permitirá aos clientes criar fluxos de trabalho em tempo real com base em acionadores de eventos, como localização.

## Links recomendados

Para obter mais informações, consulte:

* [Adobe Experience Location Service](https://www.adobe.com/experience-platform/location-service.html)
* [Adobe Campaign Standard](https://www.adobe.com/marketing/campaign.html)
* [Cadastre-se para acessar o Adobe Places Beta](https://forms.office.com/Pages/ResponsePage.aspx?id=Wht7-jR7h0OUrtLBeN7O4fkr821yYptFo-ghlnlXCyhUM0dQVkJCSzVDMFNGWEFXWUUwNEJWSjhSRS4u)
* [Adobe Experience Platform Mobile SDK](https://sdkdocs.com/)
* [Integração do Adobe Campaign com o Experience Platform SDK](https://helpx.adobe.com/campaign/kb/configuring-app-sdk.html)
