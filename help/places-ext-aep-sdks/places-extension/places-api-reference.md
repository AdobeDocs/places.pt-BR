---
title: Referência da API do Places
description: Informações sobre as referências de API no Places.
feature: Mobile SDK
exl-id: ce1a113c-dee0-49df-8d2f-789ccc1c8322
source-git-commit: f521d5e3b0b69977877d88382ce41fcb7d1c54b9
workflow-type: tm+mt
source-wordcount: '583'
ht-degree: 32%

---

# Referência da API do Places {#places-api-reference}

Estas são informações sobre as referências de API na extensão do Places:

## Processamento de um evento de região

Quando um dispositivo ultrapassa um dos limites predefinidos da região do Serviço de locais do aplicativo, a região e o tipo de evento são passados para o SDK para processamento.

### ProcessGeofence (Android)

Processar um evento de região `Geofence` para o `transitionType` fornecido.

Passar o `transitionType` de `GeofencingEvent.getGeofenceTransition()`. Atualmente, há suporte para `Geofence.GEOFENCE_TRANSITION_ENTER` e `Geofence.GEOFENCE_TRANSITION_EXIT`.

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

Este método deve ser chamado no delegado `CLLocationManager`, que informa se o usuário entrou ou saiu de uma região específica.

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

Processar todos os `Geofences` em `GeofencingEvent` ao mesmo tempo.

**Sintaxe**

```java
public static void processGeofenceEvent(final GeofencingEvent geofencingEvent);
```

**Exemplo**

Chame este método em seu `IntentService` que está registrado para receber eventos de geofence do Android

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

Retorna uma lista ordenada de POIs próximos em um retorno de chamada. Uma versão sobrecarregada deste método retornará um código de erro se algo der errado com a chamada de rede resultante.

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

Solicita uma lista de POIs nos quais o dispositivo é conhecido no momento em e os retorna em um retorno de chamada.

### ObterPontosDeInteresseAtuais (Android)

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

### ObterPontosDeInteresseAtuais (iOS)

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

Solicita a localização do dispositivo, como conhecido anteriormente, pela extensão Places.

>[!TIP]
>
>A extensão Places só conhece os locais que foram fornecidos a ela por meio de chamadas a `GetNearbyPointsOfInterest`.


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

Limpa os dados do lado do cliente para a extensão do Places no estado compartilhado, no armazenamento local e na memória.

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

### limpar (iOS)

Limpa os dados do lado do cliente para a extensão do Places no estado compartilhado, no armazenamento local e na memória.

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

## Definir status de autorização da localização

### setAuthorizationStatus (Android)

*Disponível a partir de Places v1.4.0*

Define o status de autorização na extensão Places.

O status fornecido é armazenado no estado compartilhado de Places e serve apenas para referência.
Chamar esse método não afeta o status de autorização da localização real deste dispositivo.

**Sintaxe**

Esta é a sintaxe para este método:

```java
public static void setAuthorizationStatus(final PlacesAuthorizationStatus status);
```

**Exemplo**

Esta é a amostra de código para este método:

```java
Places.setAuthorizationStatus(PlacesAuthorizationStatus.ALWAYS);
```

### setAuthorizationStatus (iOS)

*Disponível a partir do ACPLOCES v1.3.0*

Define o status de autorização na extensão Places.

O status fornecido é armazenado no estado compartilhado de Places e serve apenas para referência.
Chamar esse método não afeta o status de autorização da localização real deste dispositivo.

Quando o status de autorização do dispositivo é alterado, o método `locationManager:didChangeAuthorizationStatus:` de `CLLocationManagerDelegate` é chamado. De dentro deste método, você deve passar o novo valor `CLAuthorizationStatus` para a API ACPloces `setAuthorizationStatus:`.

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
