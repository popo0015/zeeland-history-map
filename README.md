# Battle of the Scheldt – Interactive Map

An interactive, narrative-driven map of the October–November 1944 campaign to clear the Scheldt Estuary and open Antwerp’s port.

---

## 📦 Core Libraries & Assets

- **[Leaflet.js](https://leafletjs.com/)** for map rendering, markers, polylines & popups  
- **Google Fonts** (Crimson Text) for a warm, historical feel  
- **OpenStreetMap** tiles (no API keys required)

---

## 🏗️ HTML Structure

1. **Title Page**  
   - Fullscreen hero with “Begin Historical Journey” & “Start Story Mode” buttons  
2. **Map View**  
   - `<div id="map">` as the Leaflet container  
   - A tiny, absolute-positioned **legend** explaining the three dashed-line colors  
3. **Story Mode Overlay**  
   - Stepped slides, each with a headline, description and image  
4. **Artifact Sidebar**  
   - Slide-in panel showing period artifacts per region

---

## 🔑 Key JavaScript Decisions

### 1. One-Time Initialization  
Guard `loadMap()` with a `window._mapInitialized` flag so repeated openings don’t duplicate layers or markers.

### 2. City Markers & Popups  
- **Data-driven**: array of `{ name, coords, liberationDate, images }`  
- **Tinted icons**: use Leaflet’s default pin + a CSS filter (`hue-rotate`, `saturate`, `brightness`) to shift it to a deep brown/black.

### 3. Troop Movements  
Three coordinate-chain arrays represent:  
- **Main push** (red dashed)  
- **Zuid-Beveland** (gray dashed)  
- **Walcheren crossing** (green dashed)  
Each polyline is semi-transparent and dashed, with rotated SVG arrows at midpoints on longer segments.

### 4. Legend  
A small `<div id="legend">` overlaid on the map, showing swatches that match our line styles.

---

## 🎨 Styling & Theming

- **Color palette**: Zeeland-browns, deep reds, soft grays  
- **Typography**: Crimson Text serif for a period-appropriate look  
- **Responsive tweaks**: Ensures buttons, modals and sidebar work on mobile

---

## 🚀 Minimal Lightbox Trick

Instead of a heavy library, we add:

1. A hidden `<div id="cityModal">` in HTML  
2. CSS to center it, dim the backdrop and style the image  
3. A small JS snippet: on popup open, hook `.view-all` clicks to swap the modal’s `<img>` source and show it  

This gives users a fullscreen preview of any city’s gallery with **zero extra dependencies**.

---

## 📜 Story Mode

An array of `{ title, content, image }` slides is injected dynamically:

- Fade/slide CSS transitions  
- “Next →” button advances until looping back to the map  

---

### TL;DR
> We built a fully interactive, narrative map with **Leaflet** + **light CSS**, focusing on **data-driven** markers & routes, a **tiny legend**, a **minimal lightbox**, and an engaging **story overlay**—all while keeping extra code to an absolute minimum.

