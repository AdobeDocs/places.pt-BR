---
title: Uso da extensão do Monitor de locais
description: Informações sobre como instalar, configurar e usar a extensão do Places Monitor.
translation-type: tm+mt
source-git-commit: ac1d410a676557064d5390f8392f402541754478

---


# Uso da extensão do Monitor de locais {#using-places-monitor-extension}

Para usar a extensão do Monitor de locais, conclua as seguintes tarefas:

## Instale a extensão do Monitor de locais no Experience Platform Launch

1. In Experience Platform Launch, click the **[!UICONTROL Extensions]**tab.
1. Na **[!UICONTROL Catalog]**guia, localize a**[!UICONTROL Places Monitor]** extensão e clique em **Instalar**.
1. Clique em **[!UICONTROL Save]**.
1. Siga o processo de publicação para atualizar a configuração do SDK.

### Configurar a extensão do Monitor de locais {#configure-places-monitor-extension}

Não há tarefas de configuração para a extensão do Places Monitor.

![configurar o monitor](/help/assets/configure_places_monitor.png)de locais ‌

## Adicionar a extensão do Monitor de locais ao seu aplicativo {#add-monitor-extension-to-app}

É necessário adicionar a extensão do Places Monitor ao aplicativo Android ou iOS.

### Android

No Android, execute as seguintes etapas:

#### Java

1. Adicione a extensão do Places Monitor e a extensão Places ao seu projeto usando o arquivo gradle do aplicativo.

1. Inclua também os serviços mais recentes do Google Location no arquivo gradle.

   ```java
   implementation 'com.adobe.marketing.mobile:places:1.+'
   implementation 'com.adobe.marketing.mobile:places-monitor:1.+'
   implementation 'com.adobe.marketing.mobile:sdk-core:1.+'
   implementation 'com.google.android.gms:play-services-location:16.0.0'
   ```

1. Importe a extensão do Monitor de locais na atividade principal do seu aplicativo.

   ```java
   import com.adobe.marketing.mobile.PlacesMonitor;
   ```

### iOS

No iOS, conclua as seguintes etapas:

1. Adicione a biblioteca ao seu projeto por meio dos Cocoapods `Podfile` adicionando `pod 'ACPPlacesMonitor'`.
1. Importe as bibliotecas do Monitor de locais e locais:

#### Objetive-C

```objectivec
#import "ACPCore.h"
#import "ACPPlaces.h"
#import "ACPPlacesMonitor.h"
```

#### Swift

```swift
import ACPCore
import ACPPlaces
import ACPPlacesMonitor
```


## Registrar e iniciar o Monitor de locais {#register-start-places-monitor}

Você precisa registrar e iniciar o Places Monitor no Android ou iOS.

## Android

No Android, execute as seguintes etapas:

### Java

No `OnCreate` método do aplicativo, registre as extensões do Monitor de locais:

```java
public class MobileApp extends Application {
    @Override
    public void onCreate() {
        super.onCreate();
        MobileCore.setApplication(this);
        MobileCore.ConfigureWithAppId("yourAppId");
        try {
            PlacesMonitor.registerExtension(); //Register PlacesMonitor with Mobile Core
            Places.registerExtension(); //Register Places with Mobile Core
            MobileCore.start(null);
            PlacesMonitor.start();//Start monitoring the geo-fences
        } catch (Exception e) {
            //Log the exception
        }
    }
}
```

>[!IMPORTANT]
>
>O monitoramento de locais depende da extensão de locais. Ao instalar manualmente a extensão do Places Monitor, adicione também a biblioteca `places.aar` ao projeto.

## iOS

Em seus aplicativos`application:didFinishLaunchingWithOptions`iOS, registre-se `PlacesMonitor` e instale o Mobile Core:

### Objetive-C

```objectivec
- (BOOL)application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary*)launchOptions {
    [ACPCore configureWithAppId:@"yourAppId"];
    [ACPPlaces registerExtension];
    [ACPPlacesMonitor registerExtension];
    [ACPCore start:^{            
        // do other initialization required for the SDK
        [ACPPlacesMonitor start];
    }];

    return YES;
}
```

#### Swift

```swift
func application(_ application: UIApplication, didFinishLaunchingWithOptions launchOptions: [UIApplication.LaunchOptionsKey: Any]?) -> Bool {
    ACPCore.configure(withAppId: "yourAppId")
    ACPPlaces.registerExtension()       
    ACPPlacesMonitor.registerExtension()
    ACPCore.start({
        // do other initialization required for the SDK
        ACPPlacesMonitor.start()
    })

    // Override point for customization after application launch.        
    return true
}
```

>[!IMPORTANT]
>
>O monitoramento de locais depende da extensão de locais. When manually installing the Places Monitor extension, ensure that you also add the `libACPPlaces_iOS.a` library to your project.


## Adicionar permissões ao manifesto

### Android

**Java**

Para todas as versões do Android, para declarar que seu aplicativo precisa de permissão de localização, adicione um `<uses-permission>` elemento no manifesto do aplicativo, como filho do elemento de nível superior `<manifest>` . Para aplicativos Android que direcionam a API nível 29 e superior, para permitir que o aplicativo acesse o local em segundo plano, inclua a permissão ACCESS_BACKGROUND_LOCATION.

```java
<manifest xmlns:android="http://schemas.android.com/apk/res/android" package="com.adobe.placesapp">
  <uses-permission android:name="android.permission.ACCESS_FINE_LOCATION" />
    // Only for Android apps targeting API level 29 and above
  <uses-permission android:name="android.permission.ACCESS_BACKGROUND_LOCATION" />
  <application>        
    ...    
  </application>
</manifest>
```


## Ativar atualizações de localização em segundo plano {#enable-location-updates-background}

O iOS suporta a entrega de eventos de localização para aplicativos que estão suspensos ou que não estão mais em execução. Para receber atualizações de localização em segundo plano para a extensão do Places Monitor, configure o recurso de atualizações de localização para o aplicativo em `Xcode.background-location-updates`.

![usando o Monitor de locais](/help/assets/using-the-places-monitor_1.png)

## Configurar as teclas plist

As seguintes teclas devem ser incluídas no `Info.plist` arquivo do aplicativo:

* `NSLocationWhenInUseUsageDescription` - o texto deve descrever o motivo pelo qual o aplicativo está solicitando acesso às informações de localização do usuário durante a execução em primeiro plano.
* `NSLocationAlwaysAndWhenInUseUsageDescription` - o texto deve descrever por que o aplicativo está solicitando acesso às informações de localização do usuário a qualquer momento.

>[!TIP]
>
>Se o aplicativo suportar iOS 10 e anteriores, a `NSLocationAlwaysUsageDescription` chave também será necessária.

![](/help/assets/using-the-places-monitor_2.png)
