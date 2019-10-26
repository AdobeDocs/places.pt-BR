---
title: Notificações por push
seo-title: Notificações por push
description: Esta seção fornece informações sobre como usar Locais com notificações por push no Campaign Standard.
seo-description: 'Esta seção fornece informações sobre como usar Locais com notificações por push no Campaign Standard. '
translation-type: tm+mt
source-git-commit: 0612e2fb06e45ff25ad580e3336be3eb48bb39b9

---


# Notificações por push com o Serviço de localização da plataforma de experiência {#push-notifications}

Neste guia, mostraremos como você pode usar informações históricas de localização geográfica para direcionar notificações por push fornecidas pelo Adobe Campaign Standard.

>[!IMPORTANT]
>
>Antes de começar, conclua as seguintes tarefas:
>
>* Tenha um aplicativo móvel configurado com o SDK do Adobe Experience Platform Mobile, incluindo a extensão [do](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-campaign-standard)Adobe Campaign Standard.
   >
   >
* Integre o SDK [do](https://aep-sdks.gitbook.io/docs/getting-started/get-the-sdk) Adobe Experience Platform Mobile ao seu aplicativo.
>* Adicione o [Adobe Campaign Standard Extension](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-campaign-standard) à configuração do aplicativo móvel.
   >
   >
* [Crie um POI](/help/poi-mgmt-ui/create-a-poi-ui.md) na interface de gerenciamento POI do Places.
   >
   >
* Ative e instale a extensão [](/help/places-ext-aep-sdks/places-extension/places-extension.md)Locais.



## Criar elementos de dados no Experience Platform Launch

Depois de verificar se as extensões do Monitor de locais e locais para serviços de localização estão funcionando corretamente no aplicativo, crie elementos de dados no Experience Platform Launch. Os elementos de dados permitem ler as informações fornecidas pelas extensões que vêm pelo hub de eventos do SDK móvel e agem como um alias para recuperar dados do aplicativo cliente. Vamos criar alguns elementos de dados para recuperar dados das extensões Locais, para que possamos enviar as informações do Local para o Campaign.

1. Em sua propriedade móvel do Experience Platform Launch, clique na guia Elementos **de** dados e clique em **Adicionar elemento** de dados.
2. Na lista suspensa **Extensão** , selecione **Locais**.
3. Na lista suspensa Tipo **de elemento de** dados, selecione **Nome**.
4. No painel do lado direito, você pode selecionar POI **atual** que recupera o nome do POI no qual o usuário está localizado no momento.

   **Última entrada** recupera o nome do POI que o usuário digitou pela última vez, e a opção **Última saída** fornece o nome do POI que o usuário deixou pela última vez. Neste exemplo, selecionaremos **Última inserção** e digite um nome para o elemento de dados, como **Último nome** inserido e clique em **Salvar**.

   !["Mensagens de push no Campaign Standard"](/help/assets/ACS_Push1.png)


5. Repita as mesmas etapas acima e crie elementos de dados para Latitude _com POI_ inserido pela última vez, Longitude _de POI inserido pela_&#x200B;última vez e Raio __ de POI inserido pela última vez.

Além dos elementos de dados do Serviço de localização, certifique-se de criar elementos de dados do Mobile Core para a ID _do_ aplicativo e a _Experience Cloud ID_.

## Criar uma regra para enviar dados de localização para o Adobe Campaign Standard

As regras no Experience Platform Launch permitem criar fluxos de trabalho complexos e de várias soluções com base em acionadores de eventos. O que é ótimo nas regras é que você pode criar novas regras ou modificar as existentes e ter as atualizações implantadas dinamicamente em seus aplicativos móveis. Neste exemplo, criaremos uma regra que será acionada quando um usuário digitar um POI delimitado geograficamente. Depois que a regra é acionada, uma atualização é enviada ao Campaign para gravar uma entrada em um POI específico para um usuário específico com base na Experience Cloud ID.

1. Na propriedade Launch mobile, clique na guia **Regras** e clique em **Adicionar regra**.
2. Na seção **Eventos** , clique em **+** e selecione **Locais** como a extensão.
3. Para o Tipo **de** evento, selecione **Inserir POI**.
4. Nomeie a regra, por exemplo, POI inserido pelo **usuário**.
5. Click **Keep Changes**.
6. A seção **Condições** permite que você filtre ou coloque restrições sobre quando esta regra deve ser acionada.  Por enquanto, deixaremos isto em branco.
7. Na seção **Ações** , clique em **+** para criar uma nova ação
8. Na lista suspensa **Extensão** , selecione Núcleo **móvel e,** na lista suspensa Tipo **de** ação, selecione **Enviar postback**.
9. Para o **URL**, é necessário construir o terminal de locais do Campaign Standard.  O URL deve ser semelhante ao abaixo. Certifique-se de usar os elementos de dados corretos que você criou anteriormente para o servidor do Campaign e a pKey. `https:///rest/head/mobileAppV5//locations/`
10. Clique na caixa para adicionar um corpo de publicação e enviar o seguinte:

   ```
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

11. Certifique-se de estar usando seus elementos de dados específicos criados na seção anterior.
12. Em Tipo **de** conteúdo, digite **application/json**.
13. Clique em **Manter alterações** depois de configurar.
14. Pode ser útil ter uma configuração de gancho da Web em falta como uma ação adicional para validar se as entradas estão sendo acionadas e se os dados corretos estão sendo coletados.


>Não se esqueça de publicar as alterações recentes no aplicativo para garantir que a regra e todos os seus elementos de dados sejam implantados como parte da configuração. Após a publicação, você deve iniciar o aplicativo móvel novamente para obter as atualizações de configuração mais recentes.

## Usar dados de localização para direcionar mensagens da campanha

Agora que temos dados de localização preenchidos no Campaign, podemos usar POIs como uma ferramenta de segmento de público-alvo.

1. Na instância do Adobe Campaign Standard, clique em **Criar notificação** por push.
2. Para o tipo de notificação por push, selecione **Enviar perfis** de push para campanha.
3. Clique em **Avançar** e digite os detalhes gerais na próxima tela.
4. Na tela Público-alvo, clique em **Contagem** para ver quantos usuários estimados a notificação por push será enviada.

   *Nesse caso, minha contagem será igual a três, já que tenho três dispositivos que instalei para testar o aplicativo.*

5. Na barra lateral esquerda, expanda a guia **Perfil** e arraste o filtro de localização **do** POI para a área principal
6. Na janela do filtro POI, digite o nome exato do POI que você deseja direcionar.

   *Você pode fazer seleções adicionais para determinar o intervalo de tempo desde a última visita do usuário a esse POI.*

   !["Mensagens de push 2 em ACS"](/help/assets/ACS_push2.png)


7. Clique em **Confirmar**.
8. Execute a contagem novamente na parte superior para ver o tamanho do seu público-alvo mudar.  Se você não vir a atualização da contagem, talvez tenha inserido um nome POI para o qual nenhum dispositivo disparou uma entrada. Este é o local onde o gancho da Web Slow se torna valioso, porque você pode ver uma lista de entradas de POI de vários dispositivos de teste.
9. Você pode arrastar outros filtros de localização de POI para incluir vários POIs na sua mensagem.
10. Clique em **Avançar** para concluir a criação da notificação por push para entrega.

   !["Mensagens de push 3 em ACS"](/help/assets/ACS_push3.html)

Usar o Serviço de localização com o Adobe Campaign Standard oferece uma ferramenta poderosa para segmentar e direcionar suas mensagens para usuários com base em entradas e saídas de fronteira geográfica. Essa simples integração abre a porta para a construção de casos de uso mais personalizados e contextuais.