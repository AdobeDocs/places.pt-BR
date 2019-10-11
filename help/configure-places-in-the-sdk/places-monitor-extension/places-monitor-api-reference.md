---
title: Referência da API do monitor de locais
seo-title: Referência da API do monitor de locais
description: 'Uma lista das APIs do Monitor de locais. '
seo-description: 'Uma lista das APIs do Monitor de locais.  '
translation-type: tm+mt
source-git-commit: 01617e4e1658f92234803baf1e57282777d04b13

---


# Referência da API do monitor de locais {#places-api-reference}

## Extensão do monitor de locais de registro

Registra a extensão do Monitor de locais com o Hub de eventos principal.

### RegisterExtension (Android)

Esta é a sintaxe e o código de exemplo desta API:

#### Sintaxe

Esta é a sintaxe em Java:

```java
public static void registerExtension();
```

#### Exemplo

Chame esse método no `onCreate` método em que você inicializa o restante do SDK da plataforma de experiência.

```java
public class MobileApp extends Application {
  @Override
  public void onCreate(){
     super.onCreate();
     MobileCore.setApplication(this);
     try {
        PlacesMonitor.registerExtension();
     } catch (Exception e) {
       //Log the exception
       }
    }
 }
```

### RegisterExtension (iOS)

Esta é a sintaxe e o código de exemplo desta API:

#### Sintaxe

Esta é a sintaxe no Objetivo C:

```objective-c
+ (void) registerExtension;
```

#### Exemplo

This method should be called in the `didFinishLaunchingWithOptions` delegate method of the `AppDelegate`.

```objective-c
- (BOOL)application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions {

    [ACPCore configureWithAppId:@"launch-appID"];    
    [ACPPlaces registerExtension];    
    [ACPPlacesMonitor registerExtension];

    [ACPCore start:^{
        // do other initialization of the SDK
    }];

    return YES;
}
```

## Versão da extensão

Retorna a versão atual da extensão do Monitor de locais

### ExtensionVersion (Android)

Esta é a sintaxe e o código de exemplo desta API:

#### Sintaxe

```java
public static String extensionVersion();
```

#### Exemplo

```java
String placesMonitorVersion = PlacesMonitor.extensionVersion();
```

### ExtensionVersion (iOS)

Esta é a sintaxe e o código de exemplo desta API:

#### Sintaxe

```objective-c
+ (nonnull NSString*) extensionVersion;
```

#### Exemplo

```objective-c
NSString *placesMonitorVersion = [ACPPlacesMonitor extensionVersion];
```

## Iniciar monitoramento do dispositivo

Comece a rastrear a localização do dispositivo e a monitorá-lo nas proximidades de Locais.

### Iniciar (Android)

Se a autorização para usar o local do dispositivo não tiver sido concedida pelo usuário, a primeira chamada para a `start` API solicitará a permissão do usuário.

Esta é a sintaxe e o código de exemplo desta API:

#### Sintaxe

```java
public static void start();
```

#### Exemplo

```java
PlacesMonitor.start();
```

### Iniciar (iOS)

>[!IMPORTANT]
>
>Para começar a monitorização, o serviço de localização deve ter a autorização necessária:
>
>* Se a autorização para o serviço de localização não tiver sido fornecida ao aplicativo, a primeira chamada para a `start` API solicitará a autorização para usar o serviço de localização como configurado para o aplicativo.
>* Dependendo dos recursos do seu dispositivo, se a autorização tiver sido fornecida, o Monitor de locais rastreará a localização do usuário com base na configuração atual `ACPPlacesMonitorMode`. Por padrão, o monitor usa `ACPPlacesMonitorModeSignificantChanges`.


>[!CAUTION]
>
>Se sua chamada para iniciar o monitoramento for feita antes que o SDK termine a inicialização, ela poderá ser ignorada.

Você pode garantir que o SDK terminou a inicialização chamando `start` do retorno de chamada fornecido para `ACPCore::start:`.

Esta é a sintaxe e o código de exemplo desta API:

#### Sintaxe

```objectivec
+ (void) start;
```

#### Exemplo

Iniciando o Monitor de locais quando o SDK estiver inicializando:

```objective-c
[ACPCore start:^{
    [ACPPlacesMonitor start];
}];
```

Iniciando o Monitor de locais posteriormente na execução do aplicativo:

```objective-c
[ACPPlacesMonitor start];
```

## Parar monitoramento do dispositivo

Para de rastrear a localização do dispositivo.

### Parar (Android)

Esta é a sintaxe e o código de exemplo desta API:

#### Sintaxe

```java
public static void stop();
```

#### Exemplo

```java
PlacesMonitor.stop();
```

### Parar (iOS)

Esta é a sintaxe e o código de exemplo desta API:

#### Sintaxe

```objectivec
+ (void) stop;
```

#### Exemplo

```objective-c
[ACPPlacesMonitor stop];
```

## Atualizar local

Use essa API para obter uma atualização imediata da localização do dispositivo. Quando você chama essa API, o dispositivo tenta determinar o local com o nível de precisão especificado. Esse processo também atualiza os POIs próximos que são monitorados pela extensão.

### UpdateLocation (Android)

Esta é a sintaxe e o código de exemplo desta API:

#### Sintaxe

```java
public static void updateLocation();
```

#### Exemplo

```java
PlacesMonitor.updateLocation();
```

### UpdateLocationNow (iOS)

#### Sintaxe

```objective-c
+ (void) updateLocationNow;
```

#### Exemplo

```objective-c
[ACPPlacesMonitor updateLocationNow];
```

## Permissão de localização do aplicativo

Você pode usar essa API para definir o tipo de permissão de localização que o usuário é solicitado e autorizado a usar para serviços de localização.

### SetLocationPermission (Android)

Essa API define o tipo de solicitação de permissão de localização para a qual o usuário é solicitado a selecionar.

>[!TIP]
>
>Essa API é eficaz somente para dispositivos que estão no Android 10 e superior.
>
>Para definir o prompt de autorização apropriado a ser exibido ao usuário, chame essa API antes do `PlacesMonitor.start()`. Chamar esse método, ao monitorar ativamente, atualiza o nível de permissão de local para o valor de permissão solicitado. Se o nível de autorização solicitado já for fornecido ou negado pelo usuário do aplicativo, ou se você tentar fazer o downgrade da permissão de `ALWAYS_ALLOW` para `WHILE_USING_APP`, esse método não terá efeito.

A permissão de local pode ser definida como um dos seguintes valores:

* `PlacesMonitorLocationPermission.WHILE_USING_APP`

   Esse valor solicita que o usuário acesse o local do dispositivo somente ao usar o aplicativo. Um aplicativo é considerado em uso quando o usuário está visualizando o aplicativo na tela do dispositivo, por exemplo, uma atividade está sendo executada em primeiro plano.

   >[!TIP]
   >
   >Verifique se a permissão de usuário ACCESS_FINE_LOCATION está definida no arquivo manifest do aplicativo.

* `PlacesMonitorLocationPermission.ALWAYS_ALLOW`

   Esse valor solicita que o usuário acesse o local do dispositivo mesmo quando o aplicativo está em segundo plano.

   >[!TIP]
   >
   >Verifique se as permissões de usuário ACCESS_BACKGROUND_LOCATION e ACCESS_FINE_LOCATION estão definidas no arquivo manifest do aplicativo.

   `PlacesMonitorLocationPermission.ALWAYS_ALLOW` é o valor de permissão de localização padrão.

>[!IMPORTANT]
>
>Se o usuário do aplicativo receber a `WHILE_USING_APP` permissão, as geofences não serão registradas no sistema operacional. Como resultado, a extensão do Monitor de locais não acionará eventos de entrada/saída em regiões que estão ocorrendo em segundo plano.

Esta é a sintaxe e o código de exemplo desta API:

#### Sintaxe

```java
public static void setLocationPermission(final PlacesMonitorLocationPermission placesMonitorLocationPermission)
```

#### Exemplo

Para solicitar a `WHILE_USING_APP` permissão:

```java
// set the location permission
PlacesMonitor.setLocationPermission(PlacesMonitorLocationPermission.WHILE_USING_APP);
// start monitoring
PlacesMonitor.start()
```

Para atualizar para a `ALWAYS_ALLOW` permissão:

```java
// upgrade the permission level
PlacesMonitor.setLocationPermission(PlacesMonitorLocationPermission.ALWAYS_ALLOW);
```

### SetRequestAuthorizationLevel (iOS)

Essa API define o tipo de solicitação de autorização de localização para a qual o usuário será solicitado.

Para definir o prompt de autorização apropriado a ser exibido ao usuário, chame `SetRequestAuthorizationLevel` antes de chamar `[ACPPlacesMonitor start]`. Para definir o prompt de autorização apropriado a ser exibido ao usuário, chame essa API antes do `[ACPPlacesMonitor start]`. Chamar esse método enquanto monitorar ativamente atualizará o nível de autorização de local para o valor de autorização solicitado. Se o nível de autorização solicitado já for fornecido ou negado pelo usuário do aplicativo ou se houver uma redução da permissão de `ACPPlacesRequestAuthorizationLevelAlways` para `ACPPlacesRequestAuthorizationLevelWhenInUse` autorização, esse método não terá efeito.

O nível de autorização pode ser definido como um dos seguintes valores:

* `ACPPlacesRequestAuthorizationLevelWhenInUse`

   Solicita a permissão do usuário para usar serviços de localização enquanto o aplicativo estiver em uso. O prompt do usuário contém o texto da `NSLocationWhenInUseUsageDescription` chave no arquivo Info.plist do aplicativo, e a presença dessa chave é necessária ao chamar esse método. Para obter mais informações, consulte a documentação da [Apple na solicitaçãoWhenInUseAuthorization](https://developer.apple.com/documentation/corelocation/cllocationmanager/1620562-requestwheninuseauthorization).

* `ACPPlacesRequestMonitorAuthorizationLevelAlways`

   Use essa enumeração para solicitar serviços de localização mesmo quando o aplicativo estiver em segundo plano. Você deve ter as teclas `NSLocationAlwaysUsageDescription` e `NSLocationWhenInUseUsageDescription` no Info.plist do seu aplicativo. Essas teclas definem o texto que será exibido durante o prompt do usuário. Para obter mais informações, consulte a documentação da [Apple sobre requestalwayslicense](https://developer.apple.com/documentation/corelocation/cllocationmanager/1620551-requestalwaysauthorization).

`ACPPlacesRequestAuthorizationLevelAlways` é o valor padrão de autorização de solicitação.

>[!IMPORTANT]
>
>O aplicativo que autorizou o uso da `ACPPlacesRequestAuthorizationLevelWhenInUse` permissão não poderá acionar eventos de entrada/saída em regiões que estão acontecendo em segundo plano.

Esta é a sintaxe e o código de exemplo desta API:

#### Sintaxe

```objective-c
+ (void) setRequestAuthorizationLevel: (ACPPlacesRequestAuthorizationLevel) requestAuthorizationLevel
```

#### Exemplo

Para solicitar a `ACPPlacesRequestAuthorizationLevelWhenInUse` permissão:

```objective-c
// set the request authorization level
[ACPPlacesMonitor setRequestAuthorizationLevel: ACPPlacesRequestAuthorizationLevelWhenInUse];
// start monitoring
[ACPPlacesMonitor start];
```

Para atualizar para a `ACPPlacesRequestAuthorizationLevelAlways` autorização:

```objective-c
// set the request authorization level
[ACPPlacesMonitor setRequestAuthorizationLevel: ACPPlacesRequestAuthorizationLevelAlways]
```

## Modo de monitoramento (somente iOS)

O monitoramento pode ser definido para um dos seguintes valores:

* `ACPPlacesMonitorModeContinuous`

   A extensão de monitoramento recebe e processa locais com mais frequência. Essa estratégia de monitoramento consome muita energia, mas fornece maior precisão. Para obter mais informações, consulte a documentação da [Apple sobre monitoramento](https://developer.apple.com/documentation/corelocation/cllocationmanager/1423750-startupdatinglocation)contínuo.

* `ACPPlacesMonitorModeSignificantChanges`

   A extensão de monitoramento só recebe e processa atualizações de localização após o dispositivo ter movido uma distância significativa do local processado anteriormente. Essa estratégia de monitoramento consome menos energia do que a estratégia de monitoramento contínuo. Para obter mais informações, consulte a documentação da [Apple sobre monitoramento significativo](https://developer.apple.com/documentation/corelocation/cllocationmanager/1423531-startmonitoringsignificantlocati)

### SetPlacesMonitorMode (iOS)

Esta é a sintaxe e o código de exemplo desta API:

#### Sintaxe

```objective-c
+ (void) setPlacesMonitorMode: (ACPPlacesMonitorMode) monitorMode;
```

#### Exemplo

```objective-c
[ACPPlacesMonitor setPlacesMonitorMode:ACPPlacesMonitorModeSignificantChanges];
```
