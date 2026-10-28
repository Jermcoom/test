SYSTEM PANEL v6
Host system-panel.html and embed its HTTPS URL. It is self-contained; the six
standalone files are optional alternatives, not dependencies. No deployment made.

No top toolbar. Each tile has a gear and widget-specific inline settings.
Time: description. Timezone/Date: device-source info and refresh. Location: IP
source/privacy info and refresh. Weather: unit, save and refresh. Memento: birth
date/horizon. Direct Save buttons work without iframe form-submission permission.

Location automatically uses https://ipapi.co/json/ (public-IP geolocation).
No browser geolocation API, location permission, IP input or API key required.
The provider observes the visitor's public IP. The resulting coordinates go to
Open-Meteo for weather. IP location is approximate, not GPS; VPN, proxy, ISP or
application routing can change the city. Timezone/date still follow the device.
IP-service rate limits, CORS, ad blockers and network/host policies can prevent
lookup. Unavailable results are displayed explicitly. No GPS fallback is used.
One IP lookup runs at a time. Refresh Location repeats lookup. Refresh Weather
uses existing IP coordinates or retries lookup if none are available.
IP coordinates and location are not saved in storage.

Weather: Open-Meteo current model temperature, today's high/low and conditions;
refresh every 15 minutes while open. https://open-meteo.com/ (CC BY 4.0).
Memento: numeric years left relative to a chosen horizon, not a prediction.
Prior birth date, horizon, unit, time description retain the same storage key.
Old visibility preferences are ignored: combined panel shows all six widgets.
Standalone files show their selected widget only.
Browser storage limitations still apply; blocked saves report session-only.

V7 TIMEZONE FIX
Time, Timezone and Date now use the IANA timezone returned by ipapi.co, NOT the
embedded browser's reported timezone. The browser clock supplies the current
instant; Intl formats it in the IP-derived timezone and handles daylight saving.
Refresh within Time, Timezone or Date settings re-runs the IP lookup. Standalone
clock/timezone/date files also request IP timezone on load. If no valid timezone
is available, these show an explicit unavailable state rather than silently UTC.
The timestamp still depends on an accurate browser/system clock; no remote time
synchronization is introduced. VPN/proxy/IP-provider accuracy still applies.
No layout/mobile-fitting changes were made in this version.
