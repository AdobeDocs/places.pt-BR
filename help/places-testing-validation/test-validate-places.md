---
title: Testar e validar o serviço de locais
description: Esta seção fornece informações sobre como você pode testar e validar o Serviço de Locais.
translation-type: tm+mt
source-git-commit: 5a21e734c0ef56c815389a9f08b445bedaae557a

---


# Recomendações para testar o Serviço de Locais {#test-validate-loc-svc}

Muitos clientes e organizações definirão POIs em todo o mundo, portanto, é importante ter uma maneira de simular e testar como o Serviço de Locais interage com seu aplicativo. Essas informações ajudam você a entender como testar e validar as entradas e saídas do Serviço de Locais que estão sendo acionadas corretamente com base nos POIs definidos e no local atual do usuário.

Como as variáveis ambientais podem ser um fator no sinal de localização e na precisão, recomendamos que você estabeleça primeiro os resultados da linha de base trabalhando localmente com as ferramentas do desenvolvedor e simulando as entradas de localização. O objetivo é validar se todos os eventos de localização estão funcionando corretamente. Depois que os eventos de localização são validados corretamente, as integrações de solução (por exemplo, Analytics, Target e Campaign) podem ser testadas. Para ajudar em suas atividades de teste, você deve configurar Webhooks com um postback e carregar arquivos GPX em seu ambiente de desenvolvimento individual.

>[!IMPORTANT]
>
>Esse plano supõe que os POIs tenham sido criados na interface do usuário [do](https://places.adobe.com) Places Service e que as versões mais recentes da extensão Places e da extensão do Places Monitor estejam instalados e configurados corretamente. Para obter mais informações, consulte Extensão [de](/help/places-ext-aep-sdks/places-extension/places-extension.md) locais e extensão [do Monitor de](/help/places-ext-aep-sdks/places-monitor-extension/places-monitor-extension.md)locais.

| Etapa | Descrição | Resultado esperado |
|--- |--- |--- |
| 1 | Confirme se as chaves manifest corretas foram inseridas para que o Android conceda acesso ao local de rastreamento. Para obter mais informações, consulte [Adicionar permissões ao manifesto](https://docs.adobe.com/content/help/en/places/using/places-ext-aep-sdks/places-monitor-extension/using-places-monitor-extension.html#add-permissions-to-the-manifest). | Confirmado |
| 1a | Confirme se as atualizações de localização estão configuradas no iOS. Verifique também se você tem as teclas plist apropriadas configuradas no iOS para solicitar permissão do usuário para rastrear a localização. Para obter mais informações, consulte [Ativar atualizações de localização em segundo plano.](https://docs.adobe.com/content/help/en/places/using/places-ext-aep-sdks/places-monitor-extension/using-places-monitor-extension.html#enable-location-updates-background) | Confirmado |
| 2 | Confirme qual modo de monitoramento está definido para iOS. O modo contínuo permite maior precisão e persistência, mas também consome mais energia da bateria. Para obter mais informações, consulte Modo [de monitoramento (somente iOS).](https://docs.adobe.com/content/help/en/places/using/places-ext-aep-sdks/places-monitor-extension/places-monitor-api-reference.html#monitoring-mode-ios-only) | Alterações significativas ou contínuas |
| 3 | Se estiver usando mais de uma biblioteca de POIs, confirme se as bibliotecas apropriadas foram selecionadas na extensão Locais para o Experience Platform Launch. | Confirmado |
| 4 | Confirme se as versões mais recentes das extensões do Mobile Core e Places/Places Monitor foram fornecidas com o aplicativo via Gradle ou CocoaPods. | Confirmado - para obter mais informações sobre atualizações recentes, consulte as notas de [versão.](/help/release-notes.md) |
| 5 | Confirme se os ambientes corretos estão configurados para teste. A ID do ambiente do Launch deve corresponder ao ambiente de desenvolvimento do Launch. | Confirmado |
| 6 | Crie arquivos GPX para cada POI que você deseja testar. Os arquivos GPX podem ser usados no ambiente de desenvolvimento local para simular uma entrada de local. Para obter informações sobre como criar e usar arquivos GPX, consulte o seguinte: Arquivos <br>[GPX para o Simulador iOS [fechado]](https://stackoverflow.com/questions/17292783/gpx-files-for-ios-simulator)<br>[https://mapstogpx.com/mobiledev.](https://mapstogpx.com/mobiledev.php)<br>[phpLOCATION TESTING EM APLICATIVOS MÓVEIS](https://qacumtester.wordpress.com/2014/02/27/location-testing-in-mobile-apps/) | Arquivos GPX são criados e carregados no projeto do aplicativo. |
| 7 | Sem fazer mais nada, você deve ser capaz de iniciar o aplicativo do Android Studio ou XCode e ver o alerta apropriado para solicitar acesso ao local de rastreamento. Clique na permissão *Sempre permitir* .<br><br>Recomendamos que você use um dispositivo real conectado ao seu computador em vez de usar o simulador de dispositivo. | A solicitação de localização deve ser exibida no aplicativo carregado por meio do IDE |
| 8 | Depois que a permissão Local for aceita. O SDK de locais recuperará o local atual do dispositivo e a extensão do Monitor de locais começará a monitorar os 20 POIs mais próximos do local atual | Consulte a amostra de log abaixo da tabela. |
| 9 | A alternância entre diferentes locais no estúdio XCode ou Android deve produzir eventos de entrada para POIs específicos. Os registros abaixo são esperados na entrada de um POI. | Consulte a amostra de log abaixo da tabela. |
| 10 | Depois de ver o Monitor de locais localizado perto de POIs, você deve testar enviando os ping de localização. Em Iniciar, crie uma nova regra que use a extensão Locais para acionar com base em uma entrada de fronteira geográfica. Em seguida, crie uma nova ação usando o Mobile Core para enviar um Postback. A criação de um aplicativo Webhook em falta ajuda você a ver as entradas e saídas de localização. Para obter informações sobre como criar um aplicativo Slow Webhook, consulte [Enviar mensagens usando Webhooks de entrada.](https://api.slack.com/messaging/webhooks) |  |
| 10a | Em Iniciar, certifique-se de ter adicionado elementos de dados para a extensão Locais, incluindo o seguinte: Nome do POI <br>atual<br>Nome do POI atual<br>LatAtual POI<br>longLast<br>Last Entered<br>nameLast Entered lat<br>Last Entered longLast Exited<br>nameLast Exited<br>latLast Exited<br>longTimestamp |  |
| 10b | Criar uma nova regra com um Evento = Locais → Inserir POI |  |
| 10c | Criar uma ação = Mobile Core → Postback |  |
| 10d | Use o URL do Webhook para seu aplicativo Slow, por exemplo, https://hooks.slack.com/services/TKN5FKS68/BNFP7SVD.... |  |
| 10e | O corpo da postagem seria semelhante a: `{text: User is in POI -  {%%Last Entered POI Name%%} in {%%Last Entered POI City%%} additional information: Radius:{%%Last Entered POI Radius%%} Timestamp: {%%timestamp%%}}`. <br>Certifique-se de usar os elementos de dados específicos criados aqui. |  |
| 10f | Certifique-se de publicar todos os novos elementos de dados e alterações de regras no Launch. (Você deve selecionar uma biblioteca dev em funcionamento no canto superior direito da interface do Launch.) |  |
| 11 | Inicie e teste seu aplicativo novamente girando entre os locais GPX no IDE do desenvolvedor. | Agora você deve ver Notificações por falta mostrando entradas para cada POI à medida que seleciona locais diferentes no ambiente de desenvolvimento. |
|  | **RESUMO RÁPIDO**<br> POINTA Todos estes testes podem ser realizados localmente sem a necessidade de ir para um local específico do POI. O teste de validação ajuda a garantir que seu aplicativo esteja configurado corretamente e tenha recebido as permissões corretas para o local. <br><br>Essa validação também oferece confiança de que os POIs definidos estão funcionando corretamente com a extensão do Monitor de locais.  Após esta etapa, começaremos a testar as mensagens no Campaign para ver se as mensagens corretas aparecem com base nas entradas e saídas do POI. |  |
|  | **Testando mensagens no aplicativo do Adobe Campaign Standard com o Serviço de locais.** |  |
| 12 | No painel principal Campanha, configure uma nova mensagem no aplicativo (tipo = transmissão) |  |
| 12a | Em acionadores, selecione o tipo de evento **Locais - Entrada como acionador**. |  |
| 12b | Selecione **[UICONTROL Possui metadados]**personalizados como filtro adicional - use o tipo POI = Último POI inserido.<br>Usamos**[!UICONTROL Last Entered]** o tipo POI porque na maioria dos casos, **[!UICONTROL Last Entered]**será o mesmo que**[!UICONTROL Current POI]**. <br><br>**[!UICONTROL Current POI]** deve ser usado somente em casos em que há sobreposição de fronteiras geográficas POI. Nesse caso, esses POIs precisam ser CLASSIFICADOS e, em seguida, o **[!UICONTROL Current POI]**exibirá o POI classificado no topo das 2 ou 3 fronteiras geográficas em que um usuário pode estar atualmente. |  |
| 12c | Selecione uma chave de metadados personalizada que o ajudará a restringir quais POIs receberão uma mensagem. |  |
| 12d | Para frequência e duração, guarde apenas um ou dois dias, para que, se você não gostar dos critérios, possa expirar o acionador em um período de tempo mais curto. |  |
| 12e | Para clicar em Sempre/Uma vez ou Até, selecione *SEMPRE* para poder testar em vários locais. | Uma mensagem no aplicativo é exibida SEMPRE quando você simula uma alteração de local que atenda aos critérios de metadados apropriados. |
| 12f | Para a tela, selecione uma opção diferente de Notificação local. Isso facilita a visualização ao testar o aplicativo em primeiro plano.) |  |
| 12g | Prepare/confirme e implante a mensagem no aplicativo. |  |
| 13 | Em seu ambiente de desenvolvimento, para garantir que novas regras de campanha sejam baixadas, encerre e inicie o aplicativo novamente. | Não se esqueça de que os aplicativos devem ser completamente iniciados novamente para que o novo arquivo de regras da Campanha seja baixado no dispositivo. |
| 14 | No aplicativo de desenvolvimento, alterne os locais usando os arquivos GPX criados anteriormente. | A mensagem no aplicativo deve ser exibida com base nos critérios anteriores que foram definidos. |
| 15 | Para o próximo teste, nós basicamente copiaremos os mesmos passos de antes, mas desta vez testaremos a NOTIFICAÇÃO LOCAL. | O resultado esperado é que as notificações locais são exibidas sempre que os critérios de correspondência forem atendidos. |
| 16 | Configure uma nova mensagem no aplicativo (tipo = transmissão). |  |
| 16a | Em acionadores, selecione **[!UICONTROL Places event type]**-**[!UICONTROL Entry as the trigger]**. |  |
| 16b | Selecione os metadados Personalizados de locais como um filtro adicional - use **[!UICONTROL POI type]**=**[!UICONTROL Last Entered POI]**. |  |
| 16c | Selecione uma chave de metadados personalizada que o ajudará a restringir quais POIs receberão uma mensagem. |  |
| 16d | Para frequência e duração, mantenha apenas um ou dois dias, de modo que, se você não gostar dos critérios, poderá expirar o acionador em um período de tempo mais curto. |  |
| 16e | Para click-through Sempre/Uma ou Até, **[!UICONTROL ALWAYS]**. |  |
| 16f | Para o tipo de exibição, selecione **[!UICONTROL Local Notification]**. |  |
| 16g | Prepare/confirme e implante a mensagem no aplicativo. |  |
| 17 | No ambiente do desenvolvedor, conecte seu dispositivo e pressione **[!UICONTROL Play]**na compilação. Depois de estabelecer que o local está funcionando, coloque o aplicativo em segundo plano e continue alternando os locais no Xcode ou no Android Studio. Você ainda deve ver as leituras do console indicando a alteração de local e também deve ver as notificações locais exibidas dependendo dos critérios definidos no seu acionador. (Pode haver um atraso de 1 a 2 segundos.) | O resultado esperado é que as notificações locais são exibidas sempre que os critérios de correspondência forem atendidos. |
|  | **RESUMO** Nesta <br>fase, deveríamos ver entradas POI no nosso ambiente local. Também devemos ver mensagens do Campaign baseadas no trabalho do POI. Se houver falhas, verifique se uma notificação por falta não foi enviada. Se não houver uma mensagem de falta, verifique o console do aplicativo, pois uma nova entrada de local pode não ter sido registrada. Se os resultados forem bem-sucedidos, podemos ter certeza de que o aplicativo está funcionando corretamente e de que o serviço de mensagens do Places Service e do Campaign também está funcionando corretamente. |  |
|  | **TESTE** NO SITE Pouco <br>deve mudar ao testar a localização. Manter o postback de folga ativo deve ajudar a entender se o dispositivo está recebendo uma entrada e uma saída para o local. |  |
| 18 | Realize testes com dispositivos que começam com wifi e celular desativados e depois habilitem uma vez na região POI. | Se houver uma falha, observe se você está recebendo uma entrada de cerca geográfica e uma notificação em falta. Qual é o carimbo de data e hora na notificação Slow? |
| 19 | Realize o teste apenas com o celular ativado e com o Wi-Fi desligado. |  |
| 20 | Realize testes com celular e Wi-Fi ligados. |  |
|  | **RESUMO PONTO** Os testes <br>no local devem corresponder aos testes de desenvolvimento. Lembre-se de que existem alguns fatores ambientais que podem entrar em cena ao determinar a localização dos usuários, como a duração do tempo gasto em uma cerca geográfica POI, a disponibilidade do sinal celular e a força dos pontos de acesso wifi próximos. |  |

## Amostras de registro

**** Etapa 8: Registros do iOS e Android esperados durante uma atualização de localização

**iOS**

```
[AdobeExperienceSDK DEBUG <com.adobe.placesMonitor>]: Authorization status changed: Always
[AdobeExperienceSDK DEBUG <Places>]: Requesting 20 nearby POIs for device location (<lat>, <longitude>)
[AdobeExperienceSDK DEBUG <Places>]: Response from Places Query Service contained <n> nearby POIs
[AdobeExperienceSDK DEBUG <com.adobe.placesMonitor>]: Received a new list of POIs from Places: (
<ACPPlacePoi: 0x600002b75a40> Name: <poi name>; ID:<poi id>; Center: (<lat>, <long>); Radius: <radius>
..
..)   
```

**Android**

```
PlacesMonitor - All location settings are satisfied to monitor location
PlacesMonitor - PlacesMonitorInternal : New location obtained: <latitude> <longitude> Attempting to get the near by pois
PlacesExtension - Dispatching nearby places event with n POIs
PlacesMonitor - Attempting to Monitor POI with id <poi id> name <poi name> latitude <lat> longitude <longitude>
PlacesMonitor - Attempting to Monitor POI with id <poi id> name <poi name> latitude <lat> longitude <longitude>
PlacesMonitor - Attempting to Monitor POI with id <poi id> name <poi name> latitude <lat> longitude <longitude>
...
...
PlacesMonitor - Successfully added n fences for monitoring
```

**** Etapa 9 : Registros esperados do iOS e Android durante um evento

**iOS**

```
[AdobeExperienceSDK TRACE <Places>]: Dispatching Places region entry event for place ID <poiId>
```

**Android**

```
PlacesExtension -  Dispatching Places Region Event for <poi name> with eventType entry
```
