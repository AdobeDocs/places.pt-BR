---
title: Visão geral
seo-title: APIs de consulta
description: Compreensão e uso das APIs de consulta.
seo-description: Compreensão e uso das APIs de consulta.
translation-type: tm+mt
source-git-commit: ef3d77eba407013e1f701ed001ef9ab7b3818e07

---



# APIs de consulta

Um método GET que permite consultar os POIs mais próximos do chamador.

## Solicitação

```text
GET https://query.places.adobe.com/placesedgequery
```

Com a seguinte entrada, o serviço retorna uma lista dos POIs mais próximos do chamador:

* A posição do chamador \(latitude, longitude\).
* As IDs das bibliotecas POI a serem incluídas na pesquisa.
* O número máximo de POIs a retornar.  O valor padrão é 100.

   A distância entre o chamador e o POI é definida como a distância do chamador até a borda da geofence do POI. Na resposta, os POIs que contêm o chamador serão marcados como tendo o chamador.

Os argumentos são fornecidos como os seguintes parâmetros de consulta:

* (**Obrigatório**) `latitude`

   A latitude do chamador, que deve estar entre -85 e 85.
* (**Obrigatório**) `longitude`

   A longitude do chamador, que deve estar entre -180 e 180.

* (**Opcional**) `limit`

   O número máximo de POIs a retornar.

* (**Obrigatório**) `library`

   A ID da biblioteca a ser consultada. Para consultar várias bibliotecas, certifique-se de incluir várias cópias do parâmetro de biblioteca na consulta.

Este é um exemplo do formato JSON retornado com êxito:

```markup
{
    "places": {
        "userWithin": [
            {
                "p": [
                    "poi id",
                    "poi name",
                    "poi center's latitude",
                    "poi center's longitude",
                    poiRadius,
                    rank
                ],
                "x": {
                    "country": "US",
                    "city": "Fremont",
                    "street": "Vineyard Heights",
                    "Color": "Blue",
                    "state": "CA",
                    <other POI metadata>
                }
            }
        ],
        "pois": [
            {
                "p": [
                    "poi id",
                    "poi name",
                    "poi center's latitude",
                    "poi center's longitude",
                    poiRadius,
                    rank
                ],
                "x": {
                    "country": "US",
                    "city": "Milpitas",
                    "street": null,
                    "state": "CA"
                }
            },
            {
                "p": [
                    "poi id",
                    "poi name",
                    "poi center's latitude",
                    "poi center's longitude",
                    poiRadius,
                    rank
                ],
                "x": {
                    "country": "US",
                    "city": "Fremont",
                    "street": null,
                    "state": "CA"
                }
            }
        ]
    }
}
```

Os POIs em `places.pois` são classificados por distância do chamador até a borda dos POIs. Os POIs em `places.userWithin` contêm o chamador, e esses POIs são ordenados por classificação e, em seguida, por aumento do raio.

## Exemplo de chamada

Este é um exemplo da chamada:

```text
GET https://query.places.adobe.com/placesedgequery?latitude=<userLatitude>&longitude=<userLongitude>&library=<libID1>&library=<libID2>&limit=20
```
