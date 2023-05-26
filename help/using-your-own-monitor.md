---
title: Usar seu próprio monitor
description: Você também pode usar os serviços de monitoramento e integrar com o Places Service usando as APIs de extensão do Places Service.
exl-id: 8ca4d19b-0f23-4291-b335-af47f03179fa
source-git-commit: 4ab15ded930b31e4e06920af31f37fdfe45df8eb
workflow-type: tm+mt
source-wordcount: '264'
ht-degree: 1%

---

# Usar seu próprio monitor {#using-your-monitor}

Você também pode usar os serviços de monitoramento e integrar com o Places Service usando as APIs da extensão Places.

## Registrando Geofences

Se decidir usar seus serviços de monitoramento, registre as geofences dos POIs em torno de sua localização atual seguindo as etapas abaixo:

### iOS

No iOS, conclua as seguintes etapas:

1. Passe as atualizações de localização obtidas dos Serviços principais de localização da iOS para a extensão Places.

1. Use o `getNearbyPointsOfInterest` API da extensão Places para obter a matriz de `ACPPlacesPoi` objetos em torno do local atual.

   ```objective-c
   - (void) locationManager: (CLLocationManager*) manager didUpdateLocations: (NSArray<CLLocation*>*) locations {
       [ACPPlaces getNearbyPointsOfInterest:currentLocation limit:10 callback: ^ (NSArray<ACPPlacesPoi*>* _Nullable nearbyPoi) {
           [self startMonitoringGeoFences:nearbyPoi];
       }];
   }
   ```

1. Extrair as informações do obtido `ACPPlacesPOI` objetos e comece a monitorar esses POIs.

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

1. Transmita as atualizações de localização obtidas dos serviços da Google Play ou dos serviços de localização do Android para a Extensão do Places.

1. Use o `getNearbyPointsOfInterest` API da extensão Places para obter a lista de `PlacesPoi` objetos em torno do local atual.

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

1. Extraia os dados do obtido `PlacesPOI` objetos e comece a monitorar esses POIs.

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


Chamando o `getNearbyPointsOfInterest` A API resulta em uma chamada de rede que obtém a localização ao redor da localização atual.

>[!IMPORTANT]
>
>Você deve chamar a API com moderação ou somente quando houver uma alteração significativa na localização do usuário.

## Publicação de eventos de geofence

### iOS

No iOS, chame `processGeofenceEvent` API do Places na `CLLocationManager` delegado. Essa API notifica se o usuário entrou ou saiu de uma região específica.

```objective-c
- (void) locationManager:(CLLocationManager *)manager didEnterRegion:(CLRegion *)region {
    [ACPPlaces processRegionEvent:region forRegionEventType:ACPRegionEventTypeEntry];
}

- (void) locationManager:(CLLocationManager *)manager didExitRegion:(CLRegion *)region {
    [ACPPlaces processRegionEvent:region forRegionEventType:ACPRegionEventTypeExit];
}
```

### Android

No Android, chame `processGeofence` juntamente com o evento de transição apropriado em seu receptor de transmissão Geofence. Convém preparar a lista de geofences recebidos para evitar entradas/saídas duplicadas.

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
