---
title: Referência da API de locais
seo-title: Referência da API de locais
description: Informações sobre as referências da API em Locais.
seo-description: Informações sobre as referências da API em Locais.
translation-type: tm+mt
source-git-commit: ef720c112bc0de386e070094629c5bab69938e76

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
          // Call Adobe Places API to process information
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
        // Call Adobe Places API to process information
        Places.processGeofenceEvent(geofencingEvent);
    }
}
```

## Recuperar pontos de interesse próximos

Retorna uma lista ordenada de POIs próximos em um retorno de chamada.

### GetNearbyPointsOfInterest (Android)

Esta é a sintaxe para este método:

**Sintaxe**

```java
public static void getNearbyPointsOfInterest(final Location location,
    final int limit, final AdobeCallback<List<PlacesPOI>> callback);
```

**Exemplo**

Esta é a amostra de código para este método:

```java
Places.getNearbyPlaces(currentLocation, 10, new AdobeCallback<List<PlacesPOI>>() {
    @Override
    public void call(List<PlacesPOI> pois) {
        // do required processing with the returned nearbyPoi array
        startMonitoringPois(pois);
    }
});
```

### GetNearbyPointsOfInterest (iOS)

**Sintaxe**

```objectivec
+ (void) getNearbyPointsOfInterest: (nonnull CLLocation*) currentLocation
                             limit: (NSUInteger) limit
                          callback: (nullable void (^) (NSArray<ACPPlacesPoi*>* _Nullable nearbyPoi)) callback;
```

**Exemplo**

```objectivec
[ACPPlaces getNearbyPointsOfInterest:location
                               limit:10     
                            callback:^(NSArray<ACPPlacesPoi*>* nearbyPoi) {
    // do required processing with the returned nearbyPoi array
    [self startMonitoringPois:nearbyPOI];
}];
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
