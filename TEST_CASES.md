# Test Cases – Nagrik Sathi

| ID | Scenario | Steps | Expected result |
|----|----------|-------|-----------------|
| T1 | App loads | Open index.html | Home screen with service tiles appears, no errors |
| T2 | Language change | Pick another language in header | All labels change; choice remembered after reload |
| T3 | Theme | Switch device to dark mode | App switches to dark colours with readable text |
| T4 | Location allowed | Open Alerts, allow location | 3-day forecast and risk level shown |
| T5 | Location denied | Open Alerts, deny location | Friendly message, no crash |
| T6 | Offline | Turn off internet, open Alerts | Fallback message shown; rest of app still works |
| T7 | Heavy rain sample | Use weatherSample in sample-data.json (85 mm day) | High rain-risk warning displayed |
| T8 | Emergency contacts | Save sample contacts, tap send request | Message opens for saved contacts |
| T9 | Official links | Tap each portal tile | Correct official site opens in new tab |
| T10 | Privacy | Clear browser data | Saved profile and contacts are removed |
