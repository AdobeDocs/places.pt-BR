---
title: Referência da API de locais
seo-title: Referência da API de locais
description: Informações sobre as referências da API em Locais.
seo-description: Informações sobre as referências da API em Locais.
translation-type: tm+mt
source-git-commit: 5d4974a341f6d0009ad93a9eea2f940ac9d8e871

---


# Referência da API de locais {#places-api-reference}

Estas são informações sobre as referências da API em Locais:

## Processando um evento de região

Quando um dispositivo ultrapassa um dos limites predefinidos da região Locais do aplicativo, a região e o tipo de evento são passados para o SDK para processamento.

### ProcessGeofence (Android)

Processar um evento de `Geofence` região para o evento fornecido `transitionType`.

Passe o `transitionType` de `GeofencingEvent.getGeofenceTransition()`. Atualmente `Geofence.GEOFENCE_TRANSITION_ENTER` e `Geofence.GEOFENCE_TRANSITION_EXIT` são compatíveis.

**Sintaxe**

Esta é a sintaxe para este método:

```java
public static void processGeofence(final Geofence geofence, final int transitionType);
```

**Exemplo**

Chame esse método em seu `IntentService` que está registrado para receber eventos de geofence do Android.

Esta é uma amostra de código para este método:

```java
public class GeofenceTransitionsIntentService extends IntentService {

    public GeofenceTransitionsIntentService() {
        super("GeofenceTransitionsIntentService");
    }

    protected void onHandleIntent(Intent intent) {
        GeofencingEvent geofencingEvent = GeofencingEvent.fromIntent(intent);

        List<Geofence> geofences = geofencingEvent.getTriggeringGeofences();

        if (geofences.size() > 0) {
          // Call the Places API to process information
          Places.processGeofence(geofences.get(0), geofencingEvent.getGeofenceTransition());
        }
    }
}
```

### ProcessRegionEvent (iOS)

Esse método deve ser chamado no `CLLocationManager` delegado, que informa se o usuário entrou ou saiu de uma região específica.

**Sintaxe**

Esta é a sintaxe para este método:

```objectivec
+ (void) processRegionEvent: (nonnull CLRegion*) region forRegionEventType: (ACPRegionEventType) eventType;
```

**Exemplo**

Esta é a amostra de código para este método:


```objectivec
- (void) locationManager:(CLLocationManager *)manager didEnterRegion:(CLRegion *)region {
    [ACPPlaces processRegionEvent:region forRegionEventType:ACPRegionEventTypeEntry];
}

- (void) locationManager:(CLLocationManager *)manager didExitRegion:(CLRegion *)region {
    [ACPPlaces processRegionEvent:region forRegionEventType:ACPRegionEventTypeExit];
}
```

### ProcessGeofencingEvent (Android)

Processar tudo `Geofences` ao `GeofencingEvent` mesmo tempo.

**Sintaxe**

```java
public static void processGeofenceEvent(final GeofencingEvent geofencingEvent);
```

**Exemplo**

Chame esse método em seu `IntentService` que está registrado para receber eventos de geofence do Android

```java
public class GeofenceTransitionsIntentService extends IntentService {

    public GeofenceTransitionsIntentService() {
        super("GeofenceTransitionsIntentService");
    }

    protected void onHandleIntent(Intent intent) {
        GeofencingEvent geofencingEvent = GeofencingEvent.fromIntent(intent);
        // Call the Places API to process information
        Places.processGeofenceEvent(geofencingEvent);
    }
}
```

## Recuperar pontos de interesse próximos

Retorna uma lista ordenada de POIs próximos em um retorno de chamada. Uma versão sobrecarregada desse método retornará um código de erro se algo deu errado com a chamada de rede resultante.

### GetNearbyPointsOfInterest (Android)

Esta é a sintaxe para este método:

**Sintaxe**

```java
public static void getNearbyPointsOfInterest(final Location location, final int limit,
                                             final AdobeCallback<List<PlacesPOI>> callback);

public static void getNearbyPointsOfInterest(final Location location, final int limit,
                                             final AdobeCallback<List<PlacesPOI>> callback,
                                             final AdobeCallback<PlacesRequestError> errorCallback);
```

**Exemplo**

Esta é a amostra de código para este método:

```java
// getNearbyPointsOfInterest without an error callback
Places.getNearbyPointsOfInterest(currentLocation, 10, new AdobeCallback<List<PlacesPOI>>() {
    @Override
    public void call(List<PlacesPOI> pois) {
        // do required processing with the returned nearbyPoi array
        startMonitoringPois(pois);
    }
});

// getNearbyPointsOfInterest with an error callback
Places.getNearbyPointsOfInterest(currentLocation, 10,
    new AdobeCallback<List<PlacesPOI>>() {
        @Override
        public void call(List<PlacesPOI> pois) {
            // do required processing with the returned nearbyPoi array
            startMonitoringPois(pois);
        }
    }, new AdobeCallback<PlacesRequestError>() {
        @Override
        public void call(PlacesRequestError placesRequestError) {
            // look for the placesRequestError and handle the error accordingly
            handleError(placesRequestError);
        }
    }
);
```

### GetNearbyPointsOfInterest (iOS)

**Sintaxe**

```objectivec
+ (void) getNearbyPointsOfInterest: (nonnull CLLocation*) currentLocation
                             limit: (NSUInteger) limit
                          callback: (nullable void (^) (NSArray<ACPPlacesPoi*>* _Nullable nearbyPoi)) callback;

+ (void) getNearbyPointsOfInterest: (nonnull CLLocation*) currentLocation
                             limit: (NSUInteger) limit
                          callback: (nullable void (^) (NSArray<ACPPlacesPoi*>* _Nullable nearbyPoi)) callback
                     errorCallback: (nullable void (^) (ACPPlacesRequestError result)) errorCallback;
```

**Exemplo**

```objectivec
// getNearbyPointsOfInterest without an error callback
[ACPPlaces getNearbyPointsOfInterest:location
                               limit:10     
                            callback:^(NSArray<ACPPlacesPoi*>* nearbyPoi) {
    // do required processing with the returned nearbyPoi array
    [self startMonitoringPois:nearbyPOI];
}];

// getNearbyPointsOfInterest with an error callback
[ACPPlaces getNearbyPointsOfInterest:location limit:10
    callback:^(NSArray<ACPPlacesPoi *> * _Nullable nearbyPoi) {
        // do required processing with the returned nearbyPoi array
        [self startMonitoringPois:nearbyPOI];
    } errorCallback:^(ACPPlacesRequestError result) {
        // look for the error and handle accordingly
        [self handleError:result];
    }
];
```

## Recuperar pontos de interesse do dispositivo atual

Solicita uma lista de POIs nos quais o dispositivo é conhecido por estar e os retorna em um retorno de chamada.

### GetCurrentPointsOfInterest (Android)

Esta é a sintaxe para este método:

**Sintaxe**

```java
public static void getCurrentPointsOfInterest(final AdobeCallback<List<PlacesPOI>> callback);
```

**Exemplo**

Esta é a amostra de código para este método:

```java
Places.getCurrentPointsOfInterest(new AdobeCallback<List<PlacesPOI>>() {
    @Override
    public void call(List<PlacesPOI> pois) {
        // use the obtained POIs that the device is within
        processUserWithinPois(pois);        
    }
});
```

### GetCurrentPointsOfInterest (iOS)

**Sintaxe**

Esta é a sintaxe para este método:

```objectivec
+ (void) getCurrentPointsOfInterest: (nullable void (^) (NSArray<ACPPlacesPoi*>* _Nullable userWithinPoi)) callback;
```

**Exemplo**

Esta é a amostra de código para este método:

```objectivec
[ACPPlaces getCurrentPointsOfInterest:^(NSArray<ACPPlacesPoi*>* userWithinPoi) {
    // do required processing with the returned userWithinPoi array
    [self processUserWithinPois:userWithinPoi];
}];
```


## Obter a localização do dispositivo

Solicita a localização do dispositivo, como anteriormente conhecido, pela extensão Locais.

>[!TIP]
>
>A extensão Places só sabe sobre locais que foram fornecidos para ela por meio de chamadas para `GetNearbyPointsOfInterest`.


### GetLastKnownLocation (Android)

**Sintaxe**

Esta é a sintaxe para este método:

```java
public static void getLastKnownLocation(final AdobeCallback<Location> callback);
```

**Exemplo**

Esta é a amostra de código para este método:

```java
Places.getLastKnownLocation(new AdobeCallback<Location>() {
    @Override
    public void call(Location lastLocation) {
        // do something with the last known location
        processLastKnownLocation(lastLocation);        
    }
});
```

### GetLastKnownLocation (iOS)

**Sintaxe**

Esta é a sintaxe para este método:

```objectivec
+ (void) getLastKnownLocation: (nullable void (^) (CLLocation* _Nullable lastLocation)) callback;
```

**Exemplo**

Esta é a amostra de código para este método:

```objectivec
[ACPPlaces getLastKnownLocation:^(CLLocation* lastLocation) {
    // do something with the last known location
    [self processLastKnownLocation:lastLocation];
}];
```

## Limpar dados do cliente


### Limpar (Android)

Limpa os dados do cliente para Locais em estado compartilhado, armazenamento local e na memória.

**Sintaxe**

Esta é a sintaxe para este método:

```java
public static void clear();
```

**Exemplo**

Esta é a amostra de código para este método:

```java
Places.clear();
```

### clear (iOS)

Limpa os dados do cliente para Locais em estado compartilhado, armazenamento local e na memória.

**Sintaxe**

Esta é a sintaxe para este método:

```objectivec
+ (void) clear;
```

**Exemplo**

Esta é a amostra de código para este método:

```objectivec
[ACPPlaces clear];
```

## Definir status de autorização de localização

### setAuthorizationStatus (Android)

Em breve

### setAuthorizationStatus (iOS)

*[Disponível a partir do ACPPlaces v1.3.0]*

Define o status de autorização na extensão Locais.

O status fornecido é armazenado no estado compartilhado Locais e é apenas para referência.
Chamar esse método não afeta o status real de autorização de localização desse dispositivo.

Quando o status de autorização do dispositivo é alterado, o `locationManager:didChangeAuthorizationStatus:` método de seu `CLLocationManagerDelegate` é chamado. Dentro desse método, você deve passar o novo `CLAuthorizationStatus` valor para a API ACPPlaces `setAuthorizationStatus:` .

**Sintaxe**

Esta é a sintaxe para este método:

```objectivec
+ (void) setAuthorizationStatus: (CLAuthorizationStatus) status;
```

**Exemplo**

Esta é a amostra de código para este método:

```objectivec
- (void) locationManager: (CLLocationManager*) manager didChangeAuthorizationStatus: (CLAuthorizationStatus) status {    
    [ACPPlaces setAuthorizationStatus:status];
}
```
