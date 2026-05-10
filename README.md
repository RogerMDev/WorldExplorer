# WorldExplorer

Aplicació Flutter que integra REST Countries + Open-Meteo per consultar informació d'un país i el temps actual/previsió de la seva capital.

## Fase 1 - Investigació APIs

1. Endpoint REST Countries per nom:
`GET https://restcountries.com/v3.1/name/{nom}?fullText=false`

Camps utilitzats: `name`, `capital`, `flags.png`, `region`, `subregion`, `population`, `capitalInfo.latlng`, `languages`, `currencies`, `timezones`, `borders`, `area`.

2. Coordenades a REST Countries:
`capitalInfo.latlng` (latitud/longitud de la capital).

3. Endpoint Open-Meteo meteorologia actual:
`GET https://api.open-meteo.com/v1/forecast?latitude={lat}&longitude={lon}&current_weather=true`

Per la previsió diària:
`&daily=temperature_2m_max,temperature_2m_min,weathercode&timezone=auto`

4. Estructura JSON Open-Meteo:
- `current_weather`: `temperature`, `windspeed`, `weathercode`, `time`
- `daily`: `time[]`, `temperature_2m_max[]`, `temperature_2m_min[]`, `weathercode[]`

## Funcionalitats implementades

### Base obligatòria (B1-B3)
- B1 cercador amb `TextField`, loading, cerca REST Countries, gestió 404.
- B2 detall de país: bandera, nom oficial/comú, capital, regió/subregió, població formatada.
- B3 segona crida encadenada a Open-Meteo amb temperatura, vent i condició.

### Extensions
- E1 favorits persistents (`shared_preferences`) + pantalla de favorits.
- E2 previsió meteorològica de 7 dies + mapatge de `weathercode` a icones.
- E3 secció "Més informació" (idiomes, monedes, zones horàries, fronteres, àrea, densitat).
- E4 historial de 5 cerques persistents amb chips i botó d'esborrar.
- E5 preferències persistents: mode fosc/clar i unitat ºC/ºF.
- E6 gestió robusta d'errors: offline, 404, timeout, resposta malformada + reintentar.

## Dependències

- `http`: consum d'APIs REST.
- `shared_preferences`: persistència local de preferències/favorits/historial.
- `intl`: format de població.

## Execució

```bash
flutter pub get
flutter run
```

Plataforma objectiu principal: Android.
