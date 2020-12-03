---
title: Usando seu próprio monitor
description: Você também pode usar seus serviços de monitoramento e fazer a integração com o Serviço de Locais usando as APIs de extensão do Serviço de Locais.
translation-type: tm+mt
source-git-commit: 0ca2162f113fba6bfbd54443109068b1a506762b
workflow-type: tm+mt
source-wordcount: '264'
ht-degree: 1%

---


# Usando seu próprio monitor {#using-your-monitor}

Você também pode usar seus serviços de monitoramento e fazer a integração com o Serviço de Locais usando as APIs de extensão de Locais.

## Registrando Geofences

Se você decidir usar seus serviços de monitoramento, registre as geofences dos POIs em torno do seu local atual, concluindo as seguintes etapas:

### iOS

No iOS, conclua as seguintes etapas:

1. Passe as atualizações de localização obtidas dos principais serviços de localização do iOS para a extensão de Locais.

1. Use a API de extensão `getNearbyPointsOfInterest` Locais para obter a matriz de `ACPPlacesPoi` objetos em torno do local atual.

   ```objective-c
   - (void) locationManager: (CLLocationManager*) manager didUpdateLocations: (NSArray<CLLocation*>*) locations {
       [ACPPlaces getNearbyPointsOfInterest:currentLocation limit:10 callback: ^ (NSArray<ACPPlacesPoi*>* _Nullable nearbyPoi) {
           [self startMonitoringGeoFences:nearbyPoi];
       }];
   }
   ```

1. Extraia as informações dos `ACPPlacesPOI` objetos obtidos e do start que monitora esses POIs.

   ```objective-c
   - (void) startMonitoringGeoFences: (NSArray*) newGeoFences {
       // verify if the device supports monitoring geofences
       // check for location permission
   
       for (ACPPlacesPoi * currentRegion in newGeoFences) {
           // make the circular region
           CLLocationCoordinate2D center = CLLocationCoordinate2DMake(currentRegion.latitude, currentRegion.longitude);
           CLCircularRegion* currentCLRegion = [[CLCircularRegion alloc] initWithCenter:center
                                                                                 radius:currentRegion.radius
                                                                             identifier:currentRegion.identifier];
           currentCLRegion.notifyOnExit = YES;
           currentCLRegion.notifyOnEntry = YES;
   
           // start monitoring the new region
           [_locationManager startMonitoringForRegion:currentCLRegion];
       }
   }
   ```

### Android

1. Passe as atualizações de localização obtidas dos serviços do Google Play ou dos serviços de localização do Android para a Extensão de locais.

1. Use a API de extensão de `getNearbyPointsOfInterest` locais para obter a lista de `PlacesPoi` objetos em torno do local atual.

   ```java
   LocationCallback callback = new LocationCallback() {
       @Override
       public void onLocationResult(LocationResult locationResult) {
           super.onLocationResult(locationResult);
   
           Places.getNearbyPointsOfInterest(currentLocation, 10, new AdobeCallback<List<PlacesPOI>>() {
               @Override
               public void call(List<PlacesPOI> pois) {
                   starMonitoringGeofence(pois);
               }
           });
       }
   };
   ```

1. Extraia os dados dos `PlacesPOI` objetos obtidos e do start que monitora esses POIs.

   ```java
   private void startMonitoringFences(final List<PlacesPOI> nearByPOIs) {
       // check for location permission
       for (PlacesPOI poi : nearByPOIs) {
           final Geofence fence = new Geofence.Builder()
               .setRequestId(poi.getIdentifier())
               .setCircularRegion(poi.getLatitude(), poi.getLongitude(), poi.getRadius())
               .setExpirationDuration(Geofence.NEVER_EXPIRE)
               .setTransitionTypes(Geofence.GEOFENCE_TRANSITION_ENTER |
                                   Geofence.GEOFENCE_TRANSITION_EXIT)
               .build();
           geofences.add(fence);
       }
   
       GeofencingRequest.Builder builder = new GeofencingRequest.Builder();
       builder.setInitialTrigger(GeofencingRequest.INITIAL_TRIGGER_ENTER);
       builder.addGeofences(geofences);
       builder.build();
       geofencingClient.addGeofences(builder.build(), geoFencePendingIntent)
   }
   ```


Chamar a `getNearbyPointsOfInterest` API resulta em uma chamada de rede que obtém o local em torno do local atual.

>[!IMPORTANT]
>
>Você deve chamar a API com moderação ou somente quando houver uma alteração significativa de localização do usuário.

## Postando Eventos Geofence

### iOS

No iOS, chame a API `processGeofenceEvent` Locais no `CLLocationManager` delegado. Essa API notifica se o usuário entrou ou saiu de uma região específica.

```objective-c
- (void) locationManager:(CLLocationManager *)manager didEnterRegion:(CLRegion *)region {
    [ACPPlaces processRegionEvent:region forRegionEventType:ACPRegionEventTypeEntry];
}

- (void) locationManager:(CLLocationManager *)manager didExitRegion:(CLRegion *)region {
    [ACPPlaces processRegionEvent:region forRegionEventType:ACPRegionEventTypeExit];
}
```

### Android

No Android, chame o `processGeofence` método junto com o evento de transição apropriado em seu receptor de transmissão Geofence. Talvez você queira preparar a lista de geofences recebidas para impedir entradas/saídas de duplicados.

```java
void onGeofenceReceived(final Intent intent) {
    // do appropriate validation steps for the intent
    ...

    // get GeofencingEvent from intent
    GeofencingEvent geoEvent = GeofencingEvent.fromIntent(intent);

    // get the transition type (entry or exit)
    int transitionType = geoEvent.getGeofenceTransition();

    // validate your geoEvent and get the necessary Geofences from the list
    List<Geofence> myGeofences = geoEvent.getTriggeringGeofences();

    // process region events for your geofences
    for (Geofence geofence : myGeofences) {
        Places.processGeofence(geofence, transitionType);
    }
}
```
