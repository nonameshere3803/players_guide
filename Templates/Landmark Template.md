<%*
/* ===============================
   Landmark Template Automation
   =============================== */

// Get display name from filename (post-rename safe)
const displayName = tp.file.path(true)
  .split("/")
  .pop()
  .replace(/\.md$/i, "")

// Landmark tag: spaces -> underscores, strip apostrophes
const landmarkTag = displayName
  .replace(/['’]/g, "")
  .trim()
  .replace(/\s+/g, "_")

// Prompt: what kind of landmark?
const landmarkType = await tp.system.suggester(
  [
    "Ruin",
    "Dungeon",
    "Natural Feature",
    "Ancient Site",
    "Cursed Place",
    "Sacred Site",
    "Settlement Ruins",
    "Other"
  ],
  [
    "Ruin",
    "Dungeon",
    "Natural Feature",
    "Ancient Site",
    "Cursed Place",
    "Sacred Site",
    "Settlement Ruins",
    "Other"
  ],
  false,
  "What kind of landmark is this?"
)

// Prompt: which region is this in?
const regionName = await tp.system.prompt(
  "Region this landmark is located in (exact name)"
)

// Region tag + backlink (if provided)
let regionTag = "Unknown_Region"
let regionLink = "TODO: [[Region Name]]"

if (regionName && regionName.trim().length > 0) {
  regionTag = regionName
    .replace(/['’]/g, "")
    .trim()
    .replace(/\s+/g, "_")

  regionLink = `[[${regionName}]]`
}

// Continent auto-detect (same logic as Region template)
const folderPath = tp.file.folder(true)
const parts = folderPath.split("/")
const ctnwIdx = parts.indexOf("Charting the New World")
const continentName = (ctnwIdx !== -1 && parts.length > ctnwIdx + 1)
  ? parts[ctnwIdx + 1]
  : "Unknown"

const continentTag = continentName
  .replace(/['’]/g, "")
  .trim()
  .replace(/\s+/g, "_")

const descriptionText = `An overview of ${displayName}, a notable ${landmarkType.toLowerCase()}.`
%>
---
title: <%* tR += displayName %>
description: <%* tR += descriptionText %>
draft: true
tags:
  - places
  - landmark
  - <%* tR += continentTag %>
  - <%* tR += regionTag %>
  - <%* tR += landmarkTag %>
---

## At a Glance
- **Type:** <%* tR += landmarkType %>
- **Region:** <%* tR += regionLink %>
- **Known for:** TODO
- **Perceived danger:** Low / Moderate / High / Unknown

## Overview
TODO (2–4 paragraphs):
- What this place is and how it appears from a distance.
- The environment around it: terrain, sounds, smells, weather.
- Why travelers notice or avoid it.
- Any widely known historical or mythic significance.

## What Outsiders Know
- TODO (2–3 sentences): what most people believe about this place.
- TODO (2–3 sentences): reputation, warnings, or half-true stories.
- TODO (2–3 sentences): why it appears on maps or in tavern tales.

## What Locals Understand
- TODO (2–3 sentences): practical truths outsiders miss.
- TODO (2–3 sentences): how the place *actually* behaves over time.
- TODO (2–3 sentences): what locals do to avoid, exploit, or respect it.

## Approach & Surroundings
- **Terrain:** TODO (swamp, broken stone, forested ridge, dunes, etc.)
- **Visibility:** TODO (visible for miles, hidden, revealed only at certain times)
- **Access:** TODO (open, guarded, seasonal, dangerous to reach)
- **Nearby signs:** TODO (old markers, bones, shrines, ruins, unnatural silence)

## Myths & Rumors
- TODO
- TODO
- TODO
