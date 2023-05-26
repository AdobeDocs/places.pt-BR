---
title: Extensão do Places
description: A extensão Places permite que você aja com base na localização dos usuários.
exl-id: 09c02753-09b3-4e07-82b2-b6c72c4e0e42
source-git-commit: 795808b38851d5afcedc03f58e9a1d6342830934
workflow-type: tm+mt
source-wordcount: '700'
ht-degree: 5%

---

# Extensão do Places {#places-extension}

A extensão Places permite que você aja com base na localização dos usuários. Essa extensão é a interface para as APIs de serviço de consulta do Places. Ao acompanhar eventos que contêm coordenadas GPS e eventos da região da geofence, essa extensão despacha novos eventos que são processados pelo Mecanismo de regras. A extensão Places também recupera e fornece uma lista do POI mais próximo para os dados do aplicativo que são recuperados das APIs. As regiões retornadas pelas APIs são armazenadas em cache e persistentes, o que permite um processamento offline limitado.

## Instalar a extensão Places no Adobe Experience Platform Launch

1. No Experience Platform Launch, clique no botão **[!UICONTROL Extensões]** guia.
1. No **[!UICONTROL Catálogo]** localize o **[!UICONTROL Places]** e clique em **[!UICONTROL Instalar]**.
1. Selecione as bibliotecas do Places que você deseja usar nesta propriedade. Essas são as bibliotecas que estarão acessíveis no seu aplicativo.
1. Clique em **[!UICONTROL Salvar]**.

   Ao clicar em **[!UICONTROL Salvar]**, o SDK do Experience Platform pesquisa os POIs nos Serviços do Places nas bibliotecas selecionadas. Os dados de POI não são incluídos no download da biblioteca quando você cria o aplicativo, mas um subconjunto de POIs baseado em localização é baixado para o dispositivo do usuário final no tempo de execução e se baseia nas coordenadas GPS do usuário.

1. Conclua o processo de publicação para atualizar a configuração do SDK.

   Para obter mais informações sobre a publicação no Experience Platform Launch, consulte [Publicação](https://docs.adobe.com/content/help/pt-BR/launch/using/reference/publish/overview.html).

### Configurar a extensão Places {#configure-places-extension}

![](/help/assets/places-extension.png)

## Adicionar a extensão Places ao seu aplicativo {#add-places-to-app}

Você pode adicionar a extensão Places aos aplicativos Android e iOS. As etapas para adicionar o Places ao seu aplicativo iOS ou Android podem ser vistas abaixo. As extensões do Places também estão disponíveis para as seguintes plataformas abaixo. Para adicionar Places ao seu aplicativo durante o desenvolvimento com uma dessas plataformas, consulte os links que acompanham:

**[Plug-in do Cordova Places](https://github.com/adobe/cordova-acpplaces/blob/master/README.md)**

**[Plug-in de locais nativos do React](https://github.com/adobe/react-native-acpplaces/blob/master/README.md)**

**[Flutter Places Plug-In](https://github.com/adobe/flutter-acpplaces_monitor)**

**[Plug- in de locais do XamarinName](https://github.com/adobe/xamarin-acpcore)**


### Android

Para adicionar a extensão Places ao aplicativo usando Java:

1. Adicione a extensão Places ao seu projeto usando o arquivo gradle do aplicativo.

   ```java
   implementation 'com.adobe.marketing.mobile:places:1.+'
   implementation 'com.adobe.marketing.mobile:sdk-core:1.+'
   ```

1. Importe a extensão Places na atividade principal do aplicativo.

   ```java
   import com.adobe.marketing.mobile.Places;
   ```


### iOS

Para adicionar a extensão Places ao seu aplicativo usando Objetive-C ou Swift:

1. Adicionar o Places e o [Núcleo móvel](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/mobile-core) bibliotecas ao seu projeto. Será necessário adicionar os seguintes pods aos seus `Podfile`:

   ```objective-c
   pod 'ACPPlaces', '~> 1.0'
   pod 'ACPCore', '~> 2.0'    # minimum Core version for Places is 2.0.3
   ```

   Como alternativa, se você não estiver usando o Cocoapods, poderá incluir manualmente as bibliotecas Mobile Core e Places de nossa [página de lançamentos](https://github.com/Adobe-Marketing-Cloud/acp-sdks/releases/) no Github.

1. Atualize seu Cocoapods:

   ```objective-c
   pod update
   ```

1. Abra o Xcode e, na classe AppDelegate, importe os cabeçalhos Core e Places:

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

### Registrar a extensão Places com o Mobile Core {#register-places-mobile-core}

É necessário registrar a extensão do Places com o Mobile Core no Android e no iOS.

#### Android

No do seu aplicativo `OnCreate` registrará as extensões do Places:

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

No do seu aplicativo `application:didFinishLaunchingWithOptions:` , registre a extensão Places com suas outras chamadas de registro do SDK:

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

### Modificação da duração da vida da associação de Places {#places-ttl}

Os dados de localização podem se tornar obsoletos rapidamente, especialmente se o dispositivo não estiver recebendo atualizações de localização em segundo plano.

Controle o tempo de vida dos dados de associação de Places no dispositivo definindo o `places.membershipttl` definição de configuração. O valor transmitido representa o número de segundos em que o estado de Places permanecerá válido para o dispositivo.

#### Android

Dentro do retorno de chamada de `MobileCore.start()` atualizar a configuração com as alterações necessárias antes de chamar `lifecycleStart`:

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

Na primeira linha do retorno de chamada de `ACPCore`do `start:` método, chamada `updateConfiguration:`

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

Para atualizar a configuração do SDK de forma programática no tempo de execução, use as informações a seguir para alterar os valores de configuração da extensão do Places. Para obter mais informações, consulte [Referência da API de configuração](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/mobile-core/configuration/configuration-api-reference).

| Chave | Obrigatório | Descrição |
| :--- | :--- | :--- |
| `places.libraries` | Sim | As bibliotecas de extensão do Places para o aplicativo móvel. Especifica a ID da biblioteca e o nome da biblioteca que o aplicativo móvel aceita. |
| `places.endpoint` | Sim | O ponto de extremidade padrão do Serviço de consulta de locais, que é usado para obter informações sobre bibliotecas e POIs. |
| `places.membershipttl` | Não | Valor padrão de 3600 (segundos em uma hora). Indica por quanto tempo, em segundos, as informações de associação de Locais do dispositivo permanecerão válidas. |
