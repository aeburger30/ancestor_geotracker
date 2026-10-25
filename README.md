# 🧭 Ancestor GeoTracker

**Historical Migration, Route & Proximity GIS** — A zero-build, single-page geospatial genealogy tracker built with Leaflet.js and Tailwind CSS.

🔗 **Live App (GitHub Pages):** [https://aeburger30.github.io/ancestor_geotracker/](https://aeburger30.github.io/ancestor_geotracker/)

---

## ✨ Features

- **⚡ Proximity GeoRadar & Full-Timeline Convergence Scanner**:
  - Automatically computes Haversine distances between all active ancestors in the selected year and highlights overlaps with pulsing pins and proximity lines.
  - Click **🔎 Scan Full Timeline for Convergences** to scan across every year on the timeline and discover every time two ancestors lived or traveled near one another.
- **🚂 Historical Route Telemetry**:
  - Click any migration segment on the map to inspect distance, historically likely transport mode (*Sailing Packet Ship, Transatlantic Steamship, Erie Canal Packet, Ox Wagon / Handcart, Early Steam Railroad*), estimated travel duration, and historical context.
- **📜 GEDCOM (`.ged`) Import + Built-In Historical Gazetteer**:
  - Import standard `.ged` files exported from FamilySearch, Ancestry, RootsMagic, or Gramps.
  - Extracts individuals, spousal/parental links, and dated life events (`BIRT`, `CHR`, `MARR`, `RESI`, `CENS`, `EMIG`, `IMMI`, `DEAT`, `BURI`), using a built-in historical gazetteer and background OpenStreetMap Nominatim geocoding.
- **✏️ Full Ancestor & Waypoint Management**:
  - Click any ancestor in the sidebar to expand their chronological waypoints and relationships, focus their trail on the map (`🎯`), toggle visibility (`👁️`), or edit/delete individual waypoints and ancestors (`✏️` / `🗑`).
  - Search by name, place, or FamilySearch ID, and filter by lineage color.
- **🌍 Google Earth (`.KML`), JSON Backup & Firebase Cloud Sync**:
  - Auto-saves locally in `localStorage`.
  - Optionally connect a free **Firebase Realtime Database URL** to sync seamlessly across devices on GitHub Pages.
  - Export timestamped `.KML` trails directly to Google Earth Pro / Web.
