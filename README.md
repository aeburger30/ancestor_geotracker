# 🧭 Ancestor GeoTracker

**Historical Migration, Route & Proximity GIS** — A zero-build, single-page geospatial genealogy tracker built with Leaflet.js and Tailwind CSS.

🔗 **Live App (GitHub Pages):** [https://aeburger30.github.io/ancestor_geotracker/](https://aeburger30.github.io/ancestor_geotracker/)

---

## ✨ Features

- **⚡ Proximity GeoRadar & Full-Timeline Convergence Scanner**:
  - Automatically computes Haversine distances between all active ancestors in the selected year and highlights overlaps with pulsing pins and proximity lines.
  - Click **🔎 Scan Full Timeline for Convergences** to scan across every year on the timeline and discover every time two ancestors lived or traveled near one another.
- **📄 Direct FamilySearch Family Group Record PDF Importer (`📄 Import FS PDF`)**:
  - Powered by Mozilla PDF.js (`pdf.min.js`) to extract and parse FamilySearch Family Group Record PDFs directly in the browser.
  - Parses Husband, Wife, Other Spouses, and Children blocks (extracting Names, FamilySearch IDs like `(KVG8-YVV)`, Birth/Marriage/Death dates & places, and Census/Obituary notes from the Sources pages), links all parent-child and spousal relationships, and geocodes places automatically (supporting **Merge** vs. **Replace**).
- **🌲 Built-In Burger Family Group (`KVG8-YVV`) Preset**:
  - One-click **🌲 Load Burger Family (KVG8-YVV)** button in the header (and inside the Paste JSON modal) that loads or merges the complete Frederick Burger (1800–1871) & Mabel (1806–1854) family group dataset—including George Burger (`KVLF-ZFX`), Ann Jane Marvin, Phoebe Jane Marvin, William Burger, Jane Burger, Sophia Burger, and Truman W. Bennett—with their New York to Waukesha, Marquette, Green Lake, and Winnebago County, Wisconsin migration waypoints and 1878 obituary notes.
- **🌊 Curved Geodesic Ocean Arcs & 🥾 Overland Terrain Trail Routing (OSRM)**:
  - Automatically detects transatlantic and ocean crossings (>800 miles crossing longitude `-30°`) and renders smooth 30-point quadratic/geodesic Bezier arcs across the ocean instead of flat lines.
  - For overland segments, click **🥾 Snap to Overland Terrain (OSRM)** in the **Journey Inspector Card** or any ancestor's **Waypoint Drawer** to fetch real foot/valley/mountain pass trail geometry via OSRM and cache `routeGeometry` directly on the waypoint.
- **📋 Paste / Merge JSON Modal & Gemini-in-Chrome FamilySearch Extractor**:
  - Click **📋 Paste JSON** (or **⬆ Import JSON**) to either **Merge into current tree** (deduplicating people by `fsId` or `name + birthYear`, and deduplicating waypoints by `type + year`) or **Replace entire dataset**.
  - Includes a built-in one-click **📋 Copy Gemini-in-Chrome FamilySearch Extractor Prompt** button so you can extract any ancestor's FamilySearch Person Details page directly into GeoTracker JSON.
- **🔗 Direct FamilySearch Links**:
  - Every ancestor card in the sidebar and every map marker popup displays a clickable `🔗 FS-ID` link (`https://www.familysearch.org/tree/person/details/${fsId}`) that opens their FamilySearch Person Details profile in a new tab.
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
  - Export timestamped `.KML` trails (including curved ocean arcs and OSRM overland terrain trails) directly to Google Earth Pro / Web.
