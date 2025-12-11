# Vicky Line Pub Crawl  
A mobile-first, TfL-styled progressive web application that maps every Victoria line station and links it with a curated pub stop. The app provides walking routes, estimated walking durations, and an interactive UI designed to resemble the Victoria line aesthetic. It is installable on both iOS and Android via PWA standards.

![Vercel Deployment](https://img.shields.io/badge/Deploy-Vercel-black)
![Mapbox](https://img.shields.io/badge/Maps-Mapbox-blue)
![Leaflet](https://img.shields.io/badge/Library-Leaflet-green)
![PWA Supported](https://img.shields.io/badge/PWA-Supported-orange)
![HTML5](https://img.shields.io/badge/HTML-5-red)
![JavaScript](https://img.shields.io/badge/JavaScript-ES6-yellow)

---

## Overview  
The Vicky Line Pub Crawl app displays all Victoria line stations from Brixton to Walthamstow Central, paired with nearby pubs for a full-day crawl experience. Tapping on a pub or station reveals a walking route generated through Mapbox Directions, including an estimated duration. The interface features a bottom sheet navigation panel, TfL-inspired colour scheme, interactive markers, and PWA installation support.

This project is built by The Blackhall Group.

---

## Features  
- All Victoria line stations mapped with accurate pedestrian entrances  
- Curated list of pubs, one matched to each station  
- Live walking routes using Mapbox Directions API  
- Estimated walking time displayed for each leg  
- TfL Victoria line–inspired base map and UI theme  
- Interactive bottom sheet with swipe and tap interactions  
- Responsive design for mobile-first use  
- Full PWA installation support (iOS and Android)  
- Auto-deploy via Vercel with continuous integration  
- Custom app icon and branding  

---

## Technologies Used  

### Frontend  
- HTML5  
- CSS3  
- Vanilla JavaScript (ES6)  
- Leaflet.js for map container, markers, and polylines  
- Mapbox GL JS for custom vector tiles and map styling  
- mapbox-gl-leaflet bridge to integrate Mapbox GL into Leaflet  
- Custom Mapbox Studio style using TfL Victoria line colours  

### Mapping and Routing  
- Mapbox Directions API (walking profile)  
- GeoJSON walking route geometry  
- Route caching to reduce duplicate API calls  
- Accurate pedestrian paths using `steps`, `alternatives`, and `exclude=motorway` flags  

### PWA  
- `manifest.webmanifest`  
- Service worker registration for offline and standalone mode  
- Homescreen icons (192px and 512px)  
- Standalone display mode on iOS and Android  

### Deployment  
- GitHub for version control  
- Vercel for hosting, build automation, HTTPS, and CDN distribution  

---

## Technical Architecture  

### Overview  
The application is a purely client-side web app with no backend. All interaction, routing, and UI state is handled directly in the browser. The design prioritises mobile usability, TfL branding accuracy, and efficient map rendering.

### Mapping Layer  
- Leaflet is used as the primary map container for marker and polyline management.  
- Mapbox GL JS is integrated into Leaflet to provide vector tiles and custom styling.  
- A Mapbox Studio style replicates the visual identity of the Victoria line.  
- A Carto label-only layer is added for high-contrast street text.

### Routing Engine  
- Routes are fetched using Mapbox’s Directions API.  
- Each walking route includes:  
  - geometry for display  
  - duration in seconds  
  - alternative route options for higher accuracy  
- Routes are cached by index to avoid redundant API calls.  
- Bounding box fitting is applied to adjust the map view after route selection.

### UI Layer  
- A top header with TfL-styled branding and app identity  
- A gesture-enabled bottom sheet that:  
  - collapses to reveal more map area  
  - expands to show route cards  
  - highlights the active pub stop  
- Cards for each station–pub pair show times and walking duration  
- Interactive markers with popups for stations and pubs  

### PWA Implementation  
- Manifest file declares name, theme, icons, and standalone mode  
- Service worker enables offline caching and installation badges  
- Safari and Chrome both support add-to-homescreen behaviour  
- App opens without browser UI once installed  

### Deployment  
- Vercel handles all static hosting and push-to-deploy  
- GitHub repository triggers automatic redeploys on commit  
- Served over HTTPS to support geolocation and PWA features  

---

## Running Locally  

Clone the repository:
git clone https://github.com/kodiakthebear/vicky-line-crawl
cd vicky-line-crawl

To run locally, either open `index.html` directly or start a local web server:
python3 -m http.server

Open the app in a browser at:
http://localhost:8000

---

## Installation as a Mobile Web App (PWA)  

### iOS (Safari)  
1. Open the site in Safari.  
2. Tap the Share icon.  
3. Select Add to Home Screen.  
4. Tap Add.  
5. The app will appear on the homescreen and open in standalone mode.

Note: iOS only allows PWA installation from Safari.

### Android (Chrome or Chromium browsers)  
1. Open the site in Chrome.  
2. Wait for the Install App prompt, or open the menu.  
3. Tap Install App or Add to Home Screen.  
4. Confirm installation.  
5. The app will appear as a standalone Android app.

---

## Deployment Instructions  
This project is deployed using Vercel.

To deploy manually:

1. Fork or clone the repository  
2. Import the repository into Vercel  
3. Ensure the root directory contains `index.html` and `manifest.webmanifest`  
4. Deploy automatically  
5. Vercel will assign a URL and manage HTTPS for you

No server runtime or build configuration is required.

---

## Credits  
Built by The Blackhall Group.

Design, mapping, routing, and frontend architecture by Joanna "Asia" Sobczak and Mukund "Bo" Tiwari.

---

## License (MIT)
MIT License

Copyright (c) 2025 The Blackhall Group

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the “Software”), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in
all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED “AS IS”, WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING
FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER
DEALINGS IN THE SOFTWARE.
