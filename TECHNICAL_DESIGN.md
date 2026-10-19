# Technical Design – Nagrik Sathi

## 1. Goal
Give every citizen, including first-time smartphone users, one simple screen to reach public services, safety tools and trusted information.

## 2. Architecture
```
 User (mobile / desktop browser)
        |
 index.html  (UI + logic, single file, no backend)
   |-- UI layer: tiles, cards, bottom navigation, language selector, light/dark theme
   |-- State layer: localStorage (profile, contacts, language, preferences) – device only
   |-- Service layer:
   |     |-- Geolocation API  -> user coordinates
   |     |-- Open-Meteo API   -> 3-day forecast -> disaster-risk evaluation (rain, wind gusts, heat)
   |     |-- Outbound links   -> official portals (NCS, Skill India, PIB Fact Check, Bhashini, IRCTC, etc.)
   |-- Fallback layer: friendly messages when offline, location denied, or API unavailable
```

## 3. Data flow (disaster alert)
1. User opens Alerts -> app requests location permission.
2. Coordinates are sent to Open-Meteo (no key, no personal data).
3. Response (rain, gusts, max temperature, weather code) is evaluated against thresholds.
4. App shows a plain-language risk level and safety advice in the chosen language.

## 4. Design principles
- Mobile first, large touch targets, readable fonts, dark-mode support
- Multilingual, low literacy friendly wording and icons
- Privacy: no login, no tracking, no server-side storage
- Resilience: single static file, loads fast on slow networks, graceful fallbacks
- Open source (MIT) so any state or NGO can fork and localise it

## 5. Security and privacy
- No personal data leaves the device except coordinates sent to the weather API
- No third-party scripts; only fonts and one public API
- Emergency contacts are stored locally and used only when the user taps send

## 6. Scalability roadmap
- Plug in state-level service directories and IMD / NDMA alert feeds
- Offline caching with a service worker
- More Indian languages through Bhashini
- Optional volunteer / panchayat dashboard
