---
title: World Map
draft: true
tags:
  - map
created: 2025-01-01
---

 
```zoommap
image: zz_attachements/Images/Map_of_New_World.jpg
# markers is optional; defaults to <image>.markers.json
# markers: Assets/Map.jpg.markers.json

# Map view limits
minZoom: 0.3
maxZoom: 8

# Size & interactivity
height: 760px
width: 100%
resizable: true
resizeHandle: native     # left | right | both | native
render: canvas           # or: dom

# Responsive display (fit into width, no wheel/pinch/dblclick pan/zoom)
responsive: false        # true → always fit; disables pan/zoom gestures

# Storage (optional)
# storage: note          # default is json; use "note" to store markers inline
# id: map-1              # optional stable id for inline storage (per code block)

# Alignment / wrapping (optional)
align: center             # left | center | right
wrap: true               # wrap text; useful with left/right alignment
```

<!-- Below is ONLY for the Quartz website. Obsidian treats this as plain HTML. -->

<div id="world-map" style="height: 760px; width: 100%; margin: 0 auto;"></div>

<link
  rel="stylesheet"
  href="https://unpkg.com/leaflet@1.9.4/dist/leaflet.css"
  integrity="sha256-p4NxAoJBhIIN+hmNHrzRCf9tD/miZyoHS5obTRR9BMY="
  crossorigin=""
/>

<script
  src="https://unpkg.com/leaflet@1.9.4/dist/leaflet.js"
  integrity="sha256-20nQCchB9co0qIjJZRGuk2/Z9VM+kNiyxNV1lvTlZBo="
  crossorigin=""
></script>

<script>
const imageUrl = "zz_attachements/Images/Map_of_New_World.jpg"

// Replace these with your actual image dimensions (in pixels)
const imageWidth = 3000
const imageHeight = 2000

const map = L.map("world-map", {
  crs: L.CRS.Simple,
  minZoom: 0,
  maxZoom: 4,
})

const bounds = [[0, 0], [imageHeight, imageWidth]]
L.imageOverlay(imageUrl, bounds).addTo(map)
map.fitBounds(bounds)

// Example marker:
// L.marker([1000, 1500]).addTo(map).bindPopup("Some place")
</script>







