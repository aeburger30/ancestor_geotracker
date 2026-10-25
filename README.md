# 🧭 Ancestor GeoTracker

**Historical Migration, Route & Proximity GIS** — A zero-build, single-page geospatial genealogy tracker built with Leaflet.js and Tailwind CSS.

🔗 **Live App (GitHub Pages):** [https://aeburger30.github.io/ancestor_geotracker/](https://aeburger30.github.io/ancestor_geotracker/)

---

## ✨ Features

- **⚡ Proximity GeoRadar, Full-Timeline Convergence Scanner & Kinship Path Finder**:
  - Automatically computes Haversine distances between all active ancestors in the selected year and highlights overlaps with pulsing pins and proximity lines.
  - Click **🔎 Scan Full Timeline for Convergences** to scan across every year on the timeline and discover every time two ancestors lived or traveled near one another.
  - Includes a built-in **Kinship Path Finder (`findRelationshipPath`)** that traverses `appData.relationships` up to 6 degrees and tags every proximity alert and convergence scan result with a relationship badge (*Spouses*, *Parent / Child*, *Siblings*, *In-Laws / Extended*, or *Unlinked Branch — Potential Relative!*).
- **🛤️ Toggleable Historical Migration Corridors Layer**:
  - Enable **🛤️ Historical Trails Overlay** in GeoTracker Layers to plot period transportation corridors on the map—including the **Catskill Turnpike / Susquehanna Route** (Kortright, Delaware Co. to Chenango Co., NY), the **Erie Canal** (Albany to Buffalo, 1825+), the **Great Lakes Steamer Route** (Buffalo through Lakes Erie, Huron, and Michigan to Milwaukee & Green Bay), and the **Mormon / Oregon Trail**—complete with interactive historical context popups.
- **📄 Direct FamilySearch Family Group Record PDF Importer (`📄 Import FS PDF`)**:
  - Powered by Mozilla PDF.js (`pdf.min.js`) to extract and parse FamilySearch Family Group Record PDFs directly in the browser.
  - Parses Husband, Wife, Other Spouses, and Children blocks (extracting Names, FamilySearch IDs like `(KVG8-YVV)`, Birth/Marriage/Death dates & places, and Census/Obituary notes from the Sources pages), links all parent-child and spousal relationships, and geocodes places automatically (supporting **Merge** vs. **Replace**).
- **🌲 Built-In Burger Family Group (`KVG8-YVV` & `GSRP-RWT`) & 🔬 1800 NY Candidates Presets**:
  - One-click **🌲 Load Burger Family (KVG8-YVV)** button in the header (and inside the Paste JSON modal) that loads or merges the complete Frederick Burger (`KVG8-YVV`, 1800–1871) & Mabel (`GSRP-RWT`, 1806–1854) family group dataset—including George Burger (`MCLH-1Q2` & `KVLF-ZFX`), Ann Jane Marvin (`L69L-7N2`), Phoebe Jane Marvin (`K2V7-G1Z`), William Burger (`KCG1-SZ2`), Jane Burger (`GSPD-4TX`), Sophia Burger (`GSP8-5DZ`), and Truman W. Bennett (`LQRZ-5S5`)—with their step-by-step migration from Kortright, Delaware County, NY to the 1830–1850 Chenango County, NY Census Cluster, and onward to Waukesha, Marquette, Green Lake, and Winnebago Counties, Wisconsin, plus 1878 obituary notes.
  - One-click **🔬 Merge 1800 NY Candidates** button in the header and inside `#pasteJsonModal` that merges 1800 NY Census and Dutch Reformed Church Burger parental/collateral candidates—William Burger (`p_WM_BURGER_1800`, 1768–1835), Ezekiel Burger (`p_EZEK_BURGER_1800`, 1765–1830), Hieronymus Burger (`p_HIER_BURGER_1724`, 1724–1802), Helena Sluiter (`p_HELENA_SLUITER`, 1728–1798), John Burger (`p_JOHN_BURGER_ULSTER`, 1760–1828), and Peter Burger (`p_PETER_BURGER_DUTCH`, 1745–1815)—scrubs the timeline to `1800`, and flies to the Hudson Valley / Delaware County corridor (`[42.20, -74.50]`, zoom `8`) to surface `✨ Unlinked Branch — Potential Relative!` alerts.
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
