# Echo Show Smart Dashboard

A clean, single-file, touch-friendly smart display dashboard designed for Echo Show browsers, bedside tablets, and always-on desk monitors. Built with vanilla HTML/JavaScript, Tailwind CSS, and Tone.js—requiring no build steps, servers, or API keys.

---

## Features

### 🕒 Clock & Dynamic Environment
- **Zero-Jitter Digital Clock & Stacked Date:** Crisp, viewport-scaled typography with `tabular-nums` so numbers never shift horizontally as minutes tick.
- **Weather-Adaptive Wallpapers:** Automatically cross-fades between high-resolution background photography matched to current local weather conditions (`Clear`, `Cloudy`, `Rain`, `Snow`) and day/night cycles.
- **Burn-In Protection:** Subtle periodic pixel-shifting to protect OLED and always-on LCD panels.
- **Offline Caching:** Caches weather and calendar data in `localStorage` for instant startup and uninterrupted display during brief network drops.

### 🌤️ Live Weather & Alerts (Open-Meteo)
- **Unified Weather Pill:** Displays current conditions icon, temperature, and description.
- **Environmental Metrics:** Compact pills for **Feels Like**, **Precipitation Chance**, **UV Index**, **US Air Quality Index (AQI)**, and **Next Sunrise/Sunset**.
- **Automatic Severe Weather & Frost Alerts:** Surfaces a warning pill only when actionable conditions are detected (Freeze Warning, Frost Advisory, High Wind Gusts, Thunderstorms, Freezing Rain, or Unhealthy AQI).

### 🕯️ Jewish Calendar & Shabbat Times (Hebcal)
- **36-Hour Rolling Window:** Automatically filters and displays upcoming Shabbat, Yom Tov, Parashat, Rosh Chodesh, and Omer events occurring within the next 36 hours (hiding automatically when none are imminent).
- **Live Candle-Lighting Countdown:** Highlights the Candle Lighting card in warm amber within 3 hours of Shabbat/Yom Tov and ticks down live (`in 1h 42m` → `in 12m 30s`).

### ⏱️ iOS-Style Kitchen Timer
- **Vertical Capsule Slider:** Tapping **⏱️ Timer** opens a frosted-glass vertical slider (`1m` to `60m`) that smoothly shifts the centered clock and weather to the left to prevent overlap.
- **Top-Center Countdown Pill:** Displays a live circular progress ring, `MM:SS` countdown, quick cancel button, and plays a pleasant harmonic chime via Tone.js upon completion.

### 🎧 Built-In Ambient Soundscapes (Tone.js)
Synthesizes five procedural sleep and focus soundscapes directly in the browser with zero external audio files:
1. **💨 White** — Soft low-pass filtered white noise.
2. **🌀 Fan** — Warm oscillating box-fan rumble.
3. **🌊 Brown** — Deep, soothing brown noise.
4. **🌧️ Rain** — Multi-layered rainfall mist, shower body, and randomized reverberant water droplets.
5. **🔔 Bowl** — Harmonic crystal singing-bowl sound bath rotating across nine soothing frequencies.

### 🌙 Display & Bedside Modes
- **Three-Stage Brightness Cycle (`☀️ Day` → `🌙 Night` → `🔴 Bedside`):** Automatically dims in the evening and shifts to a deep red/amber night-vision-preserving bedside mode during late-night hours (or cycle manually anytime).
- **⬛ Blackout Screen:** One-tap full-screen black sleep mode; tap anywhere to wake.

---

## Quick Setup & Customization

1. Download or copy `dashboard.html` to your device (or host it locally / via GitHub Pages).
2. Open `dashboard.html` in any text editor and customize the `USER_SETTINGS` block right at the top of the `<head>` section:

```javascript
const USER_SETTINGS = {
    // 1. WEATHER & CALENDAR LOCATION
    LOCATION_NAME: 'Teaneck, NJ',
    LATITUDE: 40.8976,
    LONGITUDE: -74.0154,

    // 2. TIMEZONE
    TIMEZONE: 'America/New_York',

    // 3. TEMPERATURE & CLOCK FORMAT
    TEMP_UNIT: 'fahrenheit',          // 'fahrenheit' or 'celsius'
    USE_24_HOUR: false,               // false = 12-hour (AM/PM), true = 24-hour

    // 4. HEBCAL SHABBAT & HOLIDAY CALENDAR SETTINGS
    HEBCAL_ENABLED: true,             // true to show Hebcal events, false to hide
    CANDLE_LIGHTING_MINS: 18,         // Minutes before sunset (e.g., 18, 20, 30, 40)
    HAVDALAH_MINS: 5,                 // Minutes after sunset for Havdalah
    ISRAEL_SCHEDULE: false,           // true for Israel schedule, false for Diaspora
    MAX_CALENDAR_ITEMS: 5,            // Max number of cards to display

    // 5. AUTO NIGHT DIMMING & BEDSIDE RED/AMBER CLOCK MODE (0–23)
    NIGHT_MODE_ENABLED: true,
    NIGHT_START_HOUR: 22,             // 10:00 PM (Dimmed Night Mode)
    BEDSIDE_START_HOUR: 23,           // 11:00 PM (Red/Amber Bedside Mode)
    NIGHT_END_HOUR: 6                 // 6:00 AM
};
```

3. Open `dashboard.html` in your browser (such as Amazon Silk on Echo Show, Safari, or Chrome) and switch to full-screen mode.

---

## Data Sources & Dependencies
- **Weather & Air Quality:** [Open-Meteo API](https://open-meteo.com/) (free, no API key required)
- **Jewish Calendar & Zmanim:** [Hebcal REST API](https://www.hebcal.com/home/developer-apis) (free, no API key required)
- **Styling:** [Tailwind CSS CDN](https://tailwindcss.com/)
- **Web Audio Synthesis:** [Tone.js](https://tonejs.github.io/)

[Gemini]((https://share.gemini.google/02nE5Y7aUHAE)_
