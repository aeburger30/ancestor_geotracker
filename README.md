# 🧭 Ancestor GeoTracker

**Historical Migration, Route & Proximity GIS** — A zero-build, single-page geospatial genealogy tracker built with Leaflet.js and Tailwind CSS.

🔗 **Live App (GitHub Pages):** [https://aeburger30.github.io/ancestor_geotracker/](https://aeburger30.github.io/ancestor_geotracker/)

---

## ✨ Features

- **📍 Strict Documented Location Tracking (Zero Guessing / Interpolation)**:
  - **📌 Lock to Last Documented Place (`"hold"`, default)**: Never interpolates mid-transit coordinates between waypoints. An ancestor remains locked at their last documented waypoint coordinates until the timeline reaches the exact year of their next documented record, badged as either `✅ Exact Documented Record (YYYY)` or `📌 Last Documented: Place (YYYY Event)`.
  - **🎯 Show Only on Exact Documented Years (`"exact"`)**: Plots an ancestor on the map and in the Proximity GeoRadar *only* when the timeline year matches an actual documented waypoint year (`event.year === currentYear`).
  - **⏮ Prev Record Year / Next Record Year ⏭**: Bottom timeline buttons that jump the slider directly between unique documented waypoint years in `appData.events`.
- **🗺️ 100% Keyless Tile Basemaps**:
  - Includes **🗺️ OpenStreetMap (Standard)** (default), **📜 USGS Topo & Relief** (USGS National Map), **⛰️ Topographic Contours** (OpenTopoMap), and **🛰️ Satellite Imagery** (Esri World Imagery)—all running cleanly on GitHub Pages without API key errors.
- **⚡ Proximity GeoRadar, Full-Timeline Convergence Scanner & Kinship Path Finder**:
  - Automatically computes Haversine distances between all active ancestors in the selected year (strictly at documented waypoint coordinates—never interpolated) and highlights overlaps with pulsing pins and proximity lines.
  - Click **🔎 Scan Full Timeline for Convergences** to scan across documented records and discover every time two ancestors lived or were recorded near one another.
  - Includes a built-in **Kinship Path Finder (`findRelationshipPath`)** that traverses `appData.relationships` up to 6 degrees and tags every proximity alert and convergence scan result with a relationship badge (*Spouses*, *Parent / Child*, *Siblings*, *In-Laws / Extended*, or *Unlinked Branch — Potential Relative!*).
- **🛤️ Toggleable Historical Migration Corridors Layer**:
  - Enable **🛤️ Historical Trails Overlay** in GeoTracker Layers to plot period transportation corridors on the map—including the **Catskill Turnpike & Susquehanna Route**, the **Erie Canal** (Albany to Buffalo, 1825+), the **Great Lakes Steamer Route** (Buffalo through Lakes Erie, Huron, and Michigan to Milwaukee & Green Bay/Fox River), and the **Mormon / Oregon Trail**—complete with interactive historical context popups.
- **📄 Direct FamilySearch Family Group Record PDF Importer (`📄 Import FS PDF`)**:
  - Powered by Mozilla PDF.js (`pdf.min.js`) to extract and parse FamilySearch Family Group Record PDFs directly in the browser.
  - Parses Husband, Wife, Other Spouses, and Children blocks (extracting Names, FamilySearch IDs like `(KVG8-YVV)`, Birth/Marriage/Death dates & places, and Census/Obituary notes from the Sources pages), links all parent-child and spousal relationships, and geocodes places automatically (supporting **Merge** vs. **Replace**).
- **🌲 Built-In Verbatim Burger Family Group (`KVG8-YVV` & `GSRP-RWT`) Preset**:
  - One-click **🌲 Load Burger Family (KVG8-YVV)** button in the header (and inside the Paste JSON modal) restricted strictly to the verbatim towns, counties, states, and dates printed in `20261025FamilyKVG8-YVV.pdf`:
    - **Frederick Burger (`KVG8-YVV`, 1800–1871)**: 1800 Birth in `Kortright, Delaware, New York`; 1819 Marriage in `Delaware, New York`; Nov 1854 Marriage to Phoebe Jane Marvin (`KJWC-B8Q`) in `Dartford, Green Lake, Wisconsin`; 1860 & 1870 Census and 1871 Death in `Waukesha, Waukesha, Wisconsin`.
    - **Mabel (`GSRP-RWT`, 1806–1854)**: 1806 Birth in `Massachusetts`; 1819 Marriage in `Delaware, New York`.
    - **George Burger (`KVLF-ZFX`, 1820–1878)** & **Ann Jane Marvin (`KJWC-148`)**: 8 Jul 1820 Birth in `New York City, New York, New York`; 8 Nov 1852 Marriage in `Montello, Marquette, Wisconsin`; Oct 1853 Settlement in `Shields, Marquette, Wisconsin` (per *Montello Express* obituary); 18 Jan 1878 Death in `Mecan / Shields, Marquette, Wisconsin`.
    - **William Burger (`GSPD-MP2`, 1827–1883)**, **George Burger (`MCLH-1Q2`, b. 1831)**, and **Jane Burger (`GSPD-4TX`, b. 1832)**: Birth & 1850 Census in `New York, United States` (state-level only as printed in PDF).
    - **Sophia Burger (`GSP8-5DZ`, 1836–1872)** & **Truman W. Bennett (`GXQ4-W6J`)**: 1836 Birth in `New York, United States`; 1859 Marriage, 1860/1870 Census, and 25 Feb 1872 Death in `Menasha, Winnebago, Wisconsin`.
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
