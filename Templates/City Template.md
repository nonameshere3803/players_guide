<%*
const displayName = tp.file.path(true)
  .split("/")
  .pop()
  .replace(/\.md$/i, "")

const cityTag = displayName
  .replace(/['’]/g, "")
  .trim()
  .replace(/\s+/g, "_")

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

// ✅ IMPORTANT: add content/ prefix when vault root is repo root
const isRepoRootVault = tp.file.path(true).startsWith("content/")
const rootPrefix = isRepoRootVault ? "content/" : ""

// Index links
const citiesIndexLink =
  `[[${rootPrefix}Charting the New World/${continentName}/Cities of ${continentName}/index.md|Cities of ${continentName}]]`

const continentIndexLink =
  `[[${rootPrefix}Charting the New World/${continentName}/index.md|${continentName}]]`

// Region prompt
const regionNameRaw = await tp.system.prompt(
  "Region this city is located in (exact name). Leave blank if unknown."
)

let regionName = (regionNameRaw ?? "").trim()

let regionTag = "Unknown_Region"
let regionLink = "TODO: [[Region Name]]"

if (regionName.length > 0) {
  regionTag = regionName
    .replace(/['’]/g, "")
    .trim()
    .replace(/\s+/g, "_")

  // ✅ Explicit path so missing region creates in correct folder (under content/)
  const regionFolder = `${rootPrefix}Charting the New World/${continentName}/Regions of ${continentName}`
  regionLink = `[[${regionFolder}/${regionName}|${regionName}]]`
}

const descriptionText = `An overview of ${displayName}, a notable city in ${continentName}.`
%>


---
title: <%* tR += displayName %>
description: <%* tR += descriptionText %>
draft: true
tags:
  - places
  - city
  - <%* tR += continentTag %>
  - <%* tR += regionTag %>
  - <%* tR += cityTag %>
---

## At a Glance
- **Continent:** <%* tR += continentIndexLink %>
- **Region:** <%* tR += regionLink %>
- **City Index:** <%* tR += citiesIndexLink %>
- **Population:** Small / Moderate / Large / Massive
- **City Focus:** Industrial / Militant / Mercantile / Spiritual / Scholarly / Maritime / Arcane / Hybrid
- **What sustains it:** TODO (trade routes, resource control, faith, force of arms, geography, relics)


## Overview
TODO (3–5 short paragraphs):
- What it feels like to approach and enter the city.
- The dominant sights, sounds, and smells.
- What the city is *known for* beyond its borders.
- How travelers are generally treated.
- Why this place matters in the wider world.

## What Outsiders Know
- TODO (2–3 sentences): the city’s reputation and why people recognize its name.
- TODO (2–3 sentences): common expectations about safety, wealth, or danger.
- TODO (2–3 sentences): a widely known historical or cultural detail.

## What Locals Understand
- TODO (2–3 sentences): what daily life here is really like.
- TODO (2–3 sentences): unspoken rules, customs, or survival knowledge.
- TODO (2–3 sentences): truths outsiders usually misunderstand or ignore.

## Districts & Quarters
- TODO: [[District Name]] — short description
- TODO: [[District Name]] — short description
- TODO: [[District Name]] — short description

## Getting Around
- **Layout:** TODO (planned streets, organic sprawl, vertical, layered, canal-based)
- **Movement:** TODO (on foot, mounts, carts, ferries, lifts)
- **Access points:** TODO (gates, docks, passes, sky-ports)
- **Restrictions:** TODO (curfews, closed wards, tolls, permits, patrols)

## Power & Influence
- **Form of governance:** TODO (council, theocracy, martial rule, merchant compact, arcane conclave)
- **Who holds authority:** TODO ([[Faction]], lineage, institution, or figure)
- **Enforcers & control:** TODO (guards, militias, magical oversight, social pressure)
- **Influential factions:** TODO ([[Faction]] — trade, faith, guild, military, criminal)
- **Notable figures:** TODO ([[Person]] — widely known leaders or power brokers)

## Trade & Livelihood
- **Exports:** TODO
- **Imports:** TODO
- **What sustains the city:** TODO (river, road, magic, pilgrimage, conquest)

## Myths & Rumors
- TODO
- TODO
- TODO
