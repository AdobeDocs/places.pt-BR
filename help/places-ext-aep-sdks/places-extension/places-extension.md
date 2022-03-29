---
title: Extensão do Places
description: A extensão Places permite agir com base na localização dos usuários.
exl-id: 09c02753-09b3-4e07-82b2-b6c72c4e0e42
source-git-commit: 795808b38851d5afcedc03f58e9a1d6342830934
workflow-type: tm+mt
source-wordcount: '700'
ht-degree: 5%

---

# Extensão do Places {#places-extension}

A extensão Places permite agir com base na localização dos usuários. Essa extensão é a interface para as APIs do Serviço de query do Places. Ao acompanhar eventos que contêm coordenadas GPS e eventos de região de geofence, essa extensão despacha novos eventos que são processados pelo Mecanismo de regras. A extensão Places também recupera e fornece um POI mais próximo para os dados do aplicativo que são recuperados das APIs. As regiões retornadas pelas APIs são armazenadas em cache e persistência, o que permite um processamento offline limitado.

## Instalar a extensão do Places no Adobe Experience Platform Launch

1. No Experience Platform Launch, clique no botão **[!UICONTROL Extensões]** guia .
1. No **[!UICONTROL Catálogo]** localize a guia **[!UICONTROL Places]** e clique em **[!UICONTROL Instalar]**.
1. Selecione as bibliotecas do Places que deseja usar nesta propriedade. Essas são as bibliotecas que estarão acessíveis no seu aplicativo.
1. Clique em **[!UICONTROL Salvar]**.

   Ao clicar em **[!UICONTROL Salvar]**, o SDK do Experience Platform pesquisa os POIs do Places Services nas bibliotecas selecionadas. Os dados de POI não são incluídos no download da biblioteca quando você cria o aplicativo, mas um subconjunto baseado em local de POIs é baixado para o dispositivo do usuário final no tempo de execução e é baseado nas coordenadas GPS do usuário.

1. Conclua o processo de publicação para atualizar a configuração do SDK.

   Para obter mais informações sobre publicação no Experience Platform Launch, consulte [Publicação](https://docs.adobe.com/content/help/pt-BR/launch/using/reference/publish/overview.html).

### Configurar a extensão do Places {#configure-places-extension}

![](/help/assets/places-extension.png)

## Adicionar a extensão do Places ao aplicativo {#add-places-to-app}

Você pode adicionar a extensão do Places aos aplicativos do Android e iOS. As etapas para adicionar Places ao seu aplicativo iOS ou Android podem ser vistas abaixo. As extensões do Places também estão disponíveis para as seguintes plataformas, abaixo. Para adicionar Places ao seu aplicativo ao desenvolver-se com uma dessas plataformas, consulte os links associados:

**[Plug-in do Cordova Places](https://github.com/adobe/cordova-acpplaces/blob/master/README.md)**

**[Plug-in React Native Places](https://github.com/adobe/react-native-acpplaces/blob/master/README.md)**

**[Plug-in Flutter Places](https://github.com/adobe/flutter-acpplaces_monitor)**

**[Plug-in do Xamarin Places](https://github.com/adobe/xamarin-acpcore)**


### Android

Para adicionar a extensão do Places ao aplicativo usando o Java:

1. Adicione a extensão do Places ao projeto usando o arquivo gradle do aplicativo.

   ```java
   implementation 'com.adobe.marketing.mobile:places:1.+'
   implementation 'com.adobe.marketing.mobile:sdk-core:1.+'
   ```

1. Importe a extensão Places na atividade principal do aplicativo.

   ```java
   import com.adobe.marketing.mobile.Places;
   ```


### iOS

Para adicionar a extensão do Places ao seu aplicativo usando Objetive-C ou Swift:

1. Adicionar os locais e [Mobile Core](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/mobile-core) bibliotecas para o seu projeto. Você precisará adicionar os seguintes pods ao seu `Podfile`:

   ```objective-c
   pod 'ACPPlaces', '~> 1.0'
   pod 'ACPCore', '~> 2.0'    # minimum Core version for Places is 2.0.3
   ```

   Como alternativa, se você não estiver usando o Cocoapods, poderá incluir manualmente as bibliotecas do Mobile Core e do Places de nossa [página de lançamentos](https://github.com/Adobe-Marketing-Cloud/acp-sdks/releases/) no Github.

1. Atualize seu Cocoapods:

   ```objective-c
   pod update
   ```

1. Abra o Xcode e, na classe AppDelegate , importe os cabeçalhos Principal e Places:

   **Objetive-C**

   ```objective-c
   #import "ACPCore.h"
   #import "ACPPlaces.h"
   ```

   **Swift**

   ```swift
   import ACPCore
   import ACPPlaces
   ```

### Registre a extensão do Places com o Mobile Core {#register-places-mobile-core}

Você precisa registrar a extensão do Places com o Mobile Core no Android e no iOS.

#### Android

No aplicativo `OnCreate` registrar as extensões do Places:

```java
public class PlacesTestApp extends Application {

    @Override
    public void onCreate() {
        super.onCreate();
        MobileCore.setApplication(this);

        try {
            Places.registerExtension();
            MobileCore.start(null);
        } catch (Exception e) {
            Log.e("PlacesTestApp", e.getMessage());
        }
    }
}
```

#### iOS

No aplicativo `application:didFinishLaunchingWithOptions:` registre a extensão do Places com suas outras chamadas de registro do SDK:

**Objetive-C**

```objective-c
- (BOOL)application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions {
    // make other sdk registration calls
    [ACPPlaces registerExtension];    
    return YES;
}
```

**Swift**

```swift
func application(_ application: UIApplication, didFinishLaunchingWithOptions launchOptions: [UIApplication.LaunchOptionsKey: Any]?) -> Bool {
    // make other sdk registration calls
    ACPPlaces.registerExtension();
    return true;
}
```

### Modificando o tempo de vida da associação do Places {#places-ttl}

Os dados de localização podem rapidamente tornar-se obsoletos, especialmente se o dispositivo não estiver recebendo atualizações de localização em segundo plano.

Controle o tempo de vida dos dados de associação do Places no dispositivo, definindo a variável `places.membershipttl` configuração. O valor transmitido representa o número de segundos em que o estado do Places permanecerá válido para o dispositivo.

#### Android

Dentro do retorno de chamada de `MobileCore.start()` atualize a configuração com as alterações necessárias antes de chamar `lifecycleStart`:

```java
public class PlacesTestApp extends Application {

    @Override
    public void onCreate() {
        super.onCreate();
        MobileCore.setApplication(this);

        try {
            Places.registerExtension();
            MobileCore.start(new AdobeCallback() {
                @Override
                public void call(Object o) {
                    // switch to your App ID from Launch
                    MobileCore.configureWithAppID("my-app-id");

                    final Map<String, Object> config = new HashMap<>();
                    config.put("places.membershipttl", 30);
                    MobileCore.updateConfiguration(config);

                    MobileCore.lifecycleStart(null);
                }
            });
        } catch (Exception e) {
            Log.e("PlacesTestApp", e.getMessage());
        }
    }
}
```

#### iOS

Na primeira linha do retorno de chamada de `ACPCore`&#39;s `start:` método, chamada `updateConfiguration:`

**Objetive-C**

```objective-c
- (BOOL)application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions {
    // make other sdk registration calls

    const UIApplicationState appState = application.applicationState;
    [ACPCore start:^{
        [ACPCore updateConfiguration:@{@"places.membershipttl":@(30)}];

        if (appState != UIApplicationStateBackground) {
            [ACPCore lifecycleStart:nil];            
        }
    }];

    return YES;
}
```

**Swift**

```swift
func application(_ application: UIApplication, didFinishLaunchingWithOptions launchOptions: [UIApplication.LaunchOptionsKey: Any]?) -> Bool {
    // make other sdk registration calls

    let appState = application.applicationState;            
    ACPCore.start {
        ACPCore.updateConfiguration(["places.membershipttl" : 30])

        if appState != .background {
            ACPCore.lifecycleStart(nil)
        }    
    }

    return true;
}
```

## Chaves de configuração

Para atualizar a configuração do SDK de forma programática no tempo de execução, use as seguintes informações para alterar os valores de configuração da extensão do Places. Para obter mais informações, consulte [Referência da API de configuração](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/mobile-core/configuration/configuration-api-reference).

| Chave | Obrigatório | Descrição |
| :--- | :--- | :--- |
| `places.libraries` | Sim | As bibliotecas de extensão do Places para o aplicativo móvel. Especifica a ID da biblioteca e o nome da biblioteca compatível com o aplicativo móvel. |
| `places.endpoint` | Sim | O ponto de extremidade padrão do Serviço de consulta do Places, usado para obter informações sobre bibliotecas e POIs. |
| `places.membershipttl` | Não | Valor padrão de 3600 (segundos em uma hora). Indica por quanto tempo, em segundos, as informações de associação do Places para o dispositivo permanecerão válidas. |
