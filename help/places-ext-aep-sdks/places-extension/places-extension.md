---
title: Extensão do Places
description: A extensão Locais permite que você atue com base na localização dos usuários.
translation-type: tm+mt
source-git-commit: 5a0705f02c8ecd540506b628371aec45107df7b2

---


# Extensão do Places {#places-extension}

A extensão Locais permite que você atue com base na localização dos usuários. Essa extensão é a interface das APIs do Serviço de Consulta de Locais. Ao acompanhar eventos que contêm coordenadas GPS e eventos de região geofence, essa extensão despacha novos eventos processados pelo Mecanismo de regras. A extensão Locais também recupera e fornece uma lista do POI mais próximo para os dados do aplicativo que são recuperados das APIs. As regiões retornadas pelas APIs são armazenadas em cache e persistência, o que permite um processamento offline limitado.

## Instale a extensão Locais no Adobe Experience Platform Launch

1. In Experience Platform Launch, click the **[!UICONTROL Extensions]** tab.
1. Na **[!UICONTROL Catalog]** guia, localize a **[!UICONTROL Places]** extensão e clique em **[!UICONTROL Install]**.
1. Selecione as bibliotecas Locais que deseja usar nesta propriedade. Essas são as bibliotecas que estarão acessíveis no seu aplicativo.
1. Clique em **[!UICONTROL Save]**.

   Quando você clica **[!UICONTROL Save]**, o SDK da plataforma da experiência pesquisa POIs nos serviços do local nas bibliotecas selecionadas. Os dados de POI não são incluídos no download da biblioteca quando você cria o aplicativo, mas um subconjunto baseado em localização de POIs é baixado para o dispositivo do usuário final em tempo de execução e é baseado nas coordenadas GPS do usuário.

1. Conclua o processo de publicação para atualizar a configuração do SDK.

   Para obter mais informações sobre a publicação no Experience Platform Launch, consulte [Publicação](https://docs.adobelaunch.com/launch-reference/publishing).

### Configure the Places extension {#configure-places-extension}

![](//help/assets/places-extension.png)

## Adicionar a extensão de Locais ao aplicativo {#add-places-to-app}

Você pode adicionar a extensão Locais aos aplicativos Android e iOS.

### Android

Para adicionar a extensão Locais ao seu aplicativo usando Java:

1. Adicione a extensão Locais ao seu projeto usando o arquivo gradle do aplicativo.

   ```java
   implementation 'com.adobe.marketing.mobile:places:1.+'
   implementation 'com.adobe.marketing.mobile:sdk-core:1.+'
   ```

1. Importe a extensão de Locais na atividade principal do seu aplicativo.

   ```java
   import com.adobe.marketing.mobile.Places;
   ```


### iOS

Para adicionar a extensão de Locais ao aplicativo usando Objetive-C ou Swift:

1. Adicione as bibliotecas Places e [Mobile Core](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/mobile-core) ao seu projeto. Você precisará adicionar os seguintes pods ao `Podfile`:

   ```objective-c
   pod 'ACPPlaces', '~> 1.0'
   pod 'ACPCore', '~> 2.0'    # minimum Core version for Places is 2.0.3
   ```

   Como alternativa, se você não estiver usando o Cocoapods, poderá incluir manualmente as bibliotecas do Mobile Core e do Places da nossa página [de](https://github.com/Adobe-Marketing-Cloud/acp-sdks/releases/) lançamentos no Github.

1. Atualize seus Cocoapods:

   ```objective-c
   pod update
   ```

1. Abra o Xcode e, na classe AppDelegate, importe os cabeçalhos Principais e Locais:

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

### Registre locais com o Mobile Core {#register-places-mobile-core}

Você precisa registrar Locais com o Mobile Core no Android e iOS.

#### Android

No `OnCreate` método do aplicativo, registre as extensões dos serviços de localização:

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

No `application:didFinishLaunchingWithOptions:` método do aplicativo, registre a extensão de Locais com suas outras chamadas de registro do SDK:

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

## Chaves de configuração

Para atualizar a configuração do SDK programaticamente no tempo de execução, use as seguintes informações para alterar os valores de configuração do Places. Para obter mais informações, consulte Referência [da API de](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/mobile-core/configuration/configuration-api-reference)configuração.

| Chave | Obrigatório | Descrição |
| :--- | :--- | :--- |
| `places.libraries` | Sim | As bibliotecas de locais do aplicativo móvel. Ela especifica a ID da biblioteca e o nome da biblioteca que o aplicativo móvel suporta. |
| `places.endpoint` | Sim | O terminal padrão do Serviço de consulta de localização da plataforma Experience, que é usado para obter informações sobre bibliotecas e POIs. |

