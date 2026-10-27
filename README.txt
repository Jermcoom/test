SYSTEM PANEL v2
Desktop order: Time | Timezone | Date / Location | Weather | Memento Mori.
On narrow screens tiles reflow to two or one column, keeping reading order.
Upload system-panel.html to your GitHub Pages site and embed the published URL.
Standalone HTML files are included. No live Console changes or deployment made.

Clock: 12-hour AM/PM; Settings chooses Standard time or Civilian time description.
Timezone: current long name (seasonally adjusted) and IANA identifier from device.
Date: Oct 27 / 2026 with weekday below. Location: bold city and country below.

Location is requested from the device on opening the combined/location/weather
widget. Browser consent, secure HTTPS hosting and iframe permission are required.
If denied or blocked by the embedding host, location/weather show an explicit
unavailable state. Open the hosted file directly to check browser permissions;
permission in a top-level window does not guarantee access inside an embed.
No IP-based fallback or made-up city. Refresh from Settings if you move.
Coordinates stay in memory, not browser storage; they are sent to Open-Meteo for
weather and BigDataCloud reverse-geocode-client for city/country lookup.
No API keys required. Browser/network/provider restrictions may affect requests.

Weather: Open-Meteo current model temperature, today's daily high/low at device
coordinates, and condition text. Refreshes every 15 minutes while open. Not a
live station observation. Weather uses location timezone; clock uses device zone.
Weather data: https://open-meteo.com/ (CC BY 4.0).
City/country lookup: https://www.bigdatacloud.com/ .

Memento Mori: optional birth date and chosen horizon, not a lifespan prediction.
Settings persist locally when permitted, not across devices. Old birth/horizon/
unit settings migrate from v1; old manual timezone/location are intentionally
ignored. Do not publish a birth date in public source code unless intended.

v3 SETTINGS FIX
The combined file contains all six tiles and does NOT load the standalone files.
Host ONLY system-panel.html for the dashboard. The standalone files are optional
alternatives, not dependencies. CSS, icons and JavaScript are all inline.

Settings now use the same SVG gear as the original Clock/Memento widgets, with
an accessible 44px click target. An inline expandable settings panel replaces
the modal. Save validates fields, applies changes, verifies storage by reading
it back, and shows a visible success or error. It stays open so you can read it.
Close or Escape dismisses settings. Malformed saved data is sanitized.

If the embed forbids browser storage, changes apply only for that session; this
is reported explicitly. No static HTML file can force persistent localStorage
when the host/browser blocks it. A direct hosted-page tab may have different
storage than an embedded context. Moving to a different origin also gives a
separate settings store. Some HTML chat previews restrict scripts completely;
use the hosted URL to test real embedding behavior.
Save is now a direct button action, NOT a form-submit button. Tested in a real
iframe with sandbox="allow-scripts" (no allow-forms and no allow-same-origin).
It applies settings even there; storage is reported as session-only. Ordinary
HTTPS-origin storage was tested to persist after reload. Validation, Escape,
and malformed saved-data recovery were also tested. The user's exact live
Notion embed policy and external API networking have not been verified.

V4: City now uses the same 500 weight as other values. Memento fill is white;
its neutral dark-gray track keeps the fill visible in light and dark themes.

V5: Toolbar: Time, Timezone, Date, Location, Weather, Memento, Refresh, Settings.
Widget icons toggle tiles off/on. Slashed icons indicate off; titles and accessible
pressed states identify each. Visibility persists when storage is available.
Hidden weather suspends automatic weather requests (location may still be used
by another visible widget). Refresh updates time, device location and visible
weather in place; it never reloads the page or discards session-only settings.
Memento subtext is now numeric years left relative to the configured horizon,
clamped at zero, shown to one decimal. Without birth date it requests setup.
