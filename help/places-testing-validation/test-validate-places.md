---
title: Testar e validar o Places Service
description: Esta seção fornece informações sobre como você pode testar e validar o Places Service.
exl-id: 8dad6619-566b-4aea-b29c-a89192a66441
TQID: https://experienceleague.adobe.com/nO4tOQW9rp3zjkHT6aJ5IcXHcD9heOaRAJiEchiz1Fk
product_v2: id: d0a3eab4-7b10-4d96-a71e-6c0f8e7b7c87id: dc5cf79d-43c4-4731-bffa-1df5d7549cb1id: dfc56824-e8b9-499e-85d4-21aedb507314id: e43347a8-f2c5-4aa4-8623-6f13875d7e3aid: e55547f1-a1ff-40c6-8978-026e40ab7fa4id: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
feature_v2: id: c93393a4-e558-47e1-992e-c91ed4d480ceid: d5ef99fa-df0c-4153-bf94-105ad0724167id: daec7ead-f475-492a-a3b3-02ae08565d6fid: e08599ea-8888-4294-ba74-3ba0a7762a46id: eb9732ab-8232-4b21-bc4c-89de86dbe4d7id: ed0d8d0e-04b9-4326-be72-a0fbca265377id: f7c7de77-382f-4f48-8b36-61a170f06d3did: fd307ce7-56f5-4ee3-af68-a7833ff6e85e
subfeature_v2: id: c3bf7e1e-1db5-4c72-9293-e2f0b1ab73d0id: d2a6cbf4-df32-480f-909e-b42f66dcb9f0
topic_v2: id: a004cc84-67b9-4a33-a3a7-8ec7273ef4dcid: b5ce8718-c3af-4fdb-a1a9-fca32f83a87cid: d3cdead0-685a-4489-9250-4bb709942f66
source-git-commit: f962cef761f006c8e7d45b76ba24746e36bdaba6
workflow-type: tm+mt
source-wordcount: 1748
ht-degree: 2%

---

# Recommendations para testar o Places Service {#test-validate-loc-svc}

Muitos clientes e organizações definirão POIs em todo o mundo, portanto, é importante ter uma maneira de simular e testar como o Places Service interage com seu aplicativo. Essas informações ajudam você a entender como testar e validar as entradas e saídas do Serviço de Places que estão sendo acionadas corretamente com base nos POIs definidos e na localização atual de um usuário.

Como as variáveis ambientais podem ser um fator no sinal de localização e na precisão, recomendamos que você primeiro estabeleça os resultados da linha de base trabalhando localmente com ferramentas de desenvolvedor e entradas de localização simuladas. O objetivo é validar se todos os eventos de localização estão funcionando corretamente. Depois que os eventos de localização forem validados corretamente, as integrações da solução (por exemplo, Analytics, Target e Campaign) poderão ser testadas. Para ajudar em suas atividades de teste, você deve configurar Webhooks do Slack com um postback e carregar arquivos GPX em seu ambiente de desenvolvimento individual.

>[!IMPORTANT]
>
>Este plano pressupõe que os POIs foram criados na [Interface do Usuário de Serviço do Places](https://places.adobe.com) e que as versões mais recentes da extensão do Places foram instaladas e configuradas corretamente. Se estiver fazendo o monitoramento de região ativo, ele também pressupõe que uma solução de monitoramento de região esteja implementada. Para obter mais informações, consulte a [extensão do Places](/help/places-ext-aep-sdks/places-extension/places-extension.md), a [documentação do CoreLocation](https://developer.apple.com/documentation/corelocation/monitoring_the_user_s_proximity_to_geographic_regions) para iOS ou a [documentação de localização do Android](https://developer.android.com/training/location/geofencing).

| Etapa | Descrição | Resultado esperado |
|--- |--- |--- |
| 1 | Confirme se as chaves de manifesto apropriadas foram inseridas para que o Android conceda acesso à localização do rastreamento. | Confirmado |
| 1a | Confirme se as atualizações de local estão configuradas no iOS. Além disso, verifique se você tem as chaves de plist apropriadas configuradas no iOS para solicitar permissão do usuário para rastrear a localização. | Confirmado |
| 2 | Confirme qual modo de monitoramento está definido para o iOS. O modo contínuo permite maior precisão e persistência, mas também consome mais a vida útil da bateria. | Alterações significativas ou contínuas |
| 3 | Se estiver usando mais de uma biblioteca de POIs, confirme se as bibliotecas apropriadas foram selecionadas na extensão Places para o Experience Platform Launch. | Confirmado |
| 4 | Confirme se as versões mais recentes das extensões Mobile Core e Places foram fornecidas com o aplicativo por meio da Gradle ou da CocoaPods. | Confirmado - para obter mais informações sobre atualizações recentes, consulte as [notas de versão.](/help/release-notes.md) |
| 5 | Confirme se os ambientes corretos estão configurados para teste. A ID do ambiente do Launch deve corresponder ao ambiente de desenvolvimento do Launch. | Confirmado |
| 6 | Crie arquivos GPX para cada POI que deseja testar. Os arquivos GPX podem ser usados no ambiente de desenvolvimento local para simular uma entrada de local. Para obter informações sobre como criar e usar arquivos GPX, consulte o seguinte: <br>[Arquivos GPX para o iOS Simulator [fechado]](https://stackoverflow.com/questions/17292783/gpx-files-for-ios-simulator)<br>[https://mapstogpx.com/mobiledev.php](https://mapstogpx.com/mobiledev.php)<br>[TESTE DE LOCALIZAÇÃO EM APLICATIVOS MÓVEIS](https://qacumtester.wordpress.com/2014/02/27/location-testing-in-mobile-apps/) | Os arquivos GPX são criados e carregados no projeto de aplicativo. |
| 7 | Sem fazer mais nada, você poderá iniciar o aplicativo a partir do Android Studio ou do XCode e ver o alerta apropriado para solicitar acesso ao local de rastreamento. Clique na permissão *Sempre permitir*.<br><br>Recomendamos que você use um dispositivo real que esteja conectado ao computador em vez de usar o simulador de dispositivo. | O prompt da solicitação de localização deve ser exibido no aplicativo carregado pelo IDE |
| 8 | Assim que a permissão Localização for aceita. O Places SDK tentará recuperar o local atual do dispositivo e o código de monitoramento da região deve começar a monitorar os 20 POIs mais próximos do local atual | Consulte a amostra de log abaixo da tabela. |
| 9 | Alternar entre locais diferentes no XCode ou no Android Studio deve produzir eventos de entrada para POIs específicos. Os registros abaixo são esperados na entrada de um POI. | Consulte a amostra de log abaixo da tabela. |
| 10 | Depois que o monitor de região encontrar POIs próximos, você deverá testar enviando pings de localização. No Launch, crie uma nova regra que use a extensão Places para acionar com base em uma entrada de delimitação geográfica. Em seguida, crie uma nova ação usando o Mobile Core para enviar um Postback. A criação de um aplicativo Webhook do Slack ajuda a visualizar entradas e saídas de local. Para obter informações sobre como criar um aplicativo Webhook do Slack, consulte [Envio de mensagens usando Webhooks de Entrada.](https://api.slack.com/messaging/webhooks) |  |
| 10a Espanhol (Peru) | No Launch, adicione elementos de dados para a extensão do Places, incluindo o seguinte: <br>Nome do POI atual<br>Lat do POI atual<br>long do POI atual<br>Nome da última entrada<br>Lat da última entrada<br>Lat da última entrada<br>Nome da última saída<br>Lat da última saída<br>Lat da última saída longa<br>Carimbo de data e hora |  |
| 10b | Crie uma nova regra com um Evento = Locais → Inserir POI |  |
| 10c | Criar uma ação = Mobile Core → Postback |  |
| 10d | Use o URL do Webhook para seu aplicativo do Slack, por exemplo, https://hooks.slack.com/services/TKN5FKS68/BNFP7SVD..... |  |
| 10e | O corpo da publicação seria semelhante a: `{text: User is in POI -  {%%Last Entered POI Name%%} in {%%Last Entered POI City%%} additional information: Radius:{%%Last Entered POI Radius%%} Timestamp: {%%timestamp%%}}`. <br>Certifique-se de usar os elementos de dados específicos criados aqui. |  |
| 10f | Certifique-se de publicar todos os novos elementos de dados e alterações de regra no Launch. (Você deve selecionar uma biblioteca de desenvolvimento em funcionamento no canto superior direito da interface do Launch.) |  |
| 11 | Inicie e teste seu aplicativo novamente, alternando entre as localizações do GPX no IDE do desenvolvedor. | Agora você deve ver as notificações do Slack mostrando entradas para cada POI, à medida que seleciona locais diferentes no ambiente de desenvolvimento. |
|  | **PONTO DE RESUMO RÁPIDO**<br> Todos esses testes podem ser conduzidos localmente sem a necessidade de ir para um local de POI específico. O teste de validação ajuda a garantir que seu aplicativo esteja configurado corretamente e tenha recebido as permissões corretas para o local. <br><br>Essa validação também garante que os POIs definidos estão funcionando corretamente com a implementação de monitoramento de sua região.  Após essa etapa, começaremos a testar as mensagens no Campaign para ver se as mensagens apropriadas são exibidas com base nas entradas e saídas do POI. |  |
|  | **Testando Mensagens no Aplicativo do Adobe Campaign Standard com o Serviço Places.** |  |
| 12 | No painel principal do Campaign, configure uma nova mensagem no aplicativo (type = broadcast) |  |
| 12a | Em disparadores, selecione **Tipo de evento do Places - Entrada como disparador**. |  |
| 12b | Selecione **[!UICONTROL Metadados personalizados do Places]** como um filtro adicional - use o tipo de POI = Último POI inserido.<br>Usamos **[!UICONTROL Última inserção]** como o tipo de POI porque, na maioria dos casos, **[!UICONTROL Última inserção]** será o mesmo que **[!UICONTROL POI atual]**. <br><br>**[!UICONTROL O POI atual ]**deve ser usado somente em instâncias onde há geolocalizações de POI sobrepostas. Nesse caso, esses POIs precisam ser CLASSIFICADOS e, em seguida, o**[!UICONTROL  POI atual ]**exibirá o POI mais bem classificado dentre as 2 ou 3 cercas geográficas nas quais um usuário pode estar no momento. |  |
| 12c | Selecione uma chave de metadados personalizada que ajudará você a limitar quais POIs receberão uma mensagem. |  |
| 12d | Para frequência e duração, mantenha em apenas um ou dois dias, para que, se você não gostar dos critérios, possa expirar o acionador em um período mais curto. |  |
| 12e | Para click-through Sempre/Uma ou Até, selecione *SEMPRE* para testar em vários locais. | Uma mensagem no aplicativo é exibida SEMPRE quando você simula uma alteração de local que atende aos critérios de metadados apropriados. |
| 12f | Para a exibição, selecione uma opção diferente de Notificação local. Isso facilita a visualização ao testar com o aplicativo em primeiro plano.) |  |
| 12g | Prepare/confirme e implante a mensagem no aplicativo. |  |
| 13 | No ambiente de desenvolvimento, para garantir que novas regras de campanha sejam baixadas, encerre e inicie o aplicativo novamente. | Não se esqueça de que os aplicativos devem ser completamente iniciados novamente para que o novo arquivo de regras do Campaign seja baixado no dispositivo. |
| 14 | No aplicativo de desenvolvimento, alterne os locais usando os arquivos GPX criados anteriormente. | Você deve ver a mensagem no aplicativo ser exibida com base nos critérios anteriores que foram definidos. |
| 15 | Para o próximo teste, copiaremos essencialmente as mesmas etapas de antes, mas desta vez testaremos a NOTIFICAÇÃO LOCAL. | O resultado esperado é que as notificações locais sejam exibidas sempre que os critérios de correspondência forem atendidos. |
| 16 | Configurar uma nova mensagem no aplicativo (tipo = difusão). |  |
| 16a | Em disparadores, selecione **[!UICONTROL Tipo de evento do Places]** - **[!UICONTROL Entrada como disparador]**. |  |
| 16b | Selecione os metadados Personalizados do Places como um filtro adicional - use o **[!UICONTROL tipo de POI]** = **[!UICONTROL Último POI inserido]**. |  |
| 16c | Selecione uma chave de metadados personalizada que ajudará você a limitar quais POIs receberão uma mensagem. |  |
| 16d | Para frequência e duração, mantenha apenas um ou dois dias, para que, se não gostar dos critérios, possa expirar o acionador em um período mais curto. |  |
| 16e | Para click-through Sempre/Uma ou Até, **[!UICONTROL SEMPRE]**. |  |
| 16f | Para o tipo de exibição, selecione **[!UICONTROL Notificação Local]**. |  |
| 16g | Prepare/confirme e implante a mensagem no aplicativo. |  |
| 17 | No ambiente de desenvolvedor, conecte seu dispositivo e pressione **[!UICONTROL Reproduzir]** na compilação. Depois de estabelecer que o local está funcionando, coloque o aplicativo em segundo plano e continue alternando os locais no Xcode ou no Android Studio. Você ainda deve ver as leituras do console indicando a alteração de local, e também deve ver as notificações locais exibidas, dependendo dos critérios definidos no acionador. (Pode haver um atraso de 1 a 2 segundos.) | O resultado esperado é que as notificações locais sejam exibidas sempre que os critérios correspondentes forem atendidos. |
|  | **PONTO DE RESUMO** <br>Neste estágio, devemos ver entradas de POI em nosso ambiente local. Também devemos ver mensagens do Campaign com base no trabalho do POI. Se houver falhas, verifique se uma notificação do Slack não foi enviada. Se não houver nenhuma mensagem do Slack, verifique o console do aplicativo, pois uma nova entrada de local pode não ter sido registrada. Se os resultados forem bem-sucedidos, podemos ter certeza de que o aplicativo está funcionando corretamente e que o Serviço de Places e o Serviço de mensagens do Campaign também estão funcionando corretamente. |  |
|  | **TESTE NO LOCAL** <br>Não deve haver muitas alterações ao testar no local. Manter o postback do Slack ativo deve ajudar a entender se o dispositivo está obtendo uma entrada e saída para o local. |  |
| 18 | Realize testes com dispositivos começando com Wi-Fi e celular desativados, e depois ative uma vez na região de POI. | Se houver uma falha, observe se você está obtendo uma entrada de geolocalização e uma notificação no Slack. Qual é o carimbo de data e hora na notificação do Slack? |
| 19 | Faça o teste apenas com a rede celular ativada e com o Wi-Fi desligado. |  |
| 20 | Realize o teste com a rede celular e o Wi-Fi ativados. |  |
|  | **PONTO DE RESUMO** <br>O teste no site deve corresponder muito ao teste de desenvolvimento. Lembre-se de que há alguns fatores ambientais que podem ser usados na determinação da localização do usuário, como a duração do tempo gasto em uma geolocalização de POI, a disponibilidade do sinal da célula e a intensidade dos pontos de acesso Wi-Fi próximos. |  |

## Amostras de log

**Etapa 8 :** Logs esperados do iOS e do Android durante uma atualização de local

**iOS**

```
[AdobeExperienceSDK DEBUG <Places>]: Requesting 20 nearby POIs for device location (<lat>, <longitude>)
[AdobeExperienceSDK DEBUG <Places>]: Response from Places Query Service contained <n> nearby POIs   
```

**Android**

```
PlacesExtension - Dispatching nearby places event with n POIs   
```

**Etapa 9:** Logs esperados do iOS e do Android durante um evento

**iOS**

```
[AdobeExperienceSDK TRACE <Places>]: Dispatching Places region entry event for place ID <poiId>
```

**Android**

```
PlacesExtension -  Dispatching Places Region Event for <poi name> with eventType entry
```
