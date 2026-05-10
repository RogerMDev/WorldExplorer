# WorldExplorer

Flutter application that integrates REST Countries and Open-Meteo to search for information about a country and check the current weather / forecast for its capital.

## Phase 1 - API Research

1. REST Countries endpoint by name:  
   `GET https://restcountries.com/v3.1/name/{name}?fullText=false`

   Fields used: `name`, `capital`, `flags.png`, `region`, `subregion`, `population`, `capitalInfo.latlng`, `languages`, `currencies`, `timezones`, `borders`, `area`.

2. Coordinates in REST Countries:  
   `capitalInfo.latlng` contains the latitude and longitude of the capital.

3. Open-Meteo endpoint for current weather:  
   `GET https://api.open-meteo.com/v1/forecast?latitude={lat}&longitude={lon}&current_weather=true`

   For the daily forecast:  
   `&daily=temperature_2m_max,temperature_2m_min,weathercode&timezone=auto`

4. Open-Meteo JSON structure:

   - `current_weather`: `temperature`, `windspeed`, `weathercode`, `time`
   - `daily`: `time[]`, `temperature_2m_max[]`, `temperature_2m_min[]`, `weathercode[]`

## Implemented Features

### Core Features

- Search bar using `TextField`, loading state, REST Countries search and 404 handling.
- Country detail screen showing flag, official/common name, capital, region/subregion and formatted population.
- Chained second API call to Open-Meteo showing temperature, wind speed and weather condition.

### Additional Features

- Persistent favorites using `shared_preferences` and a favorites screen.
- 7-day weather forecast with `weathercode` mapped to icons.
- “More information” section including languages, currencies, time zones, borders, area and density.
- Persistent search history with the last 5 searches, chips and a clear button.
- Persistent preferences: dark/light mode and ºC/ºF temperature unit.
- Robust error handling: offline mode, 404, timeout, malformed response and retry option.

## Dependencies

- `http`: REST API consumption.
- `shared_preferences`: local persistence for preferences, favorites and search history.
- `intl`: population formatting.

## Execution

```bash
flutter pub get
flutter run
```

Mainly made for: Android.
