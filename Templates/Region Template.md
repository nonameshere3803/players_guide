<%*
const displayName = tp.file.path(true)
  .split("/")
  .pop()
  .replace(/\.md$/i, "")

const regionTag = displayName
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

const descriptionText = `An overview of ${displayName}.`

const continentIndexLink = `[[Charting the New World/${continentName}/index.md|${continentName}]]`
const regionsIndexLink = `[[Charting the New World/${continentName}/Regions of ${continentName}/index.md|Regions of ${continentName}]]`
%>
---
title: <%* tR += displayName %>
description: <%* tR += descriptionText %>
draft: true
tags:
  - places
  - region
  - <%* tR += continentTag %>
  - <%* tR += regionTag %>
---

## At a Glance
- **Continent:** <%* tR += continentIndexLink %>
- **Region Index:** <%* tR += regionsIndexLink %>
- **Type:** Region / Landmark / Wilderness / Borderland
- **Known for:** TODO
- **Danger level:** Low / Moderate / High / Unknown




## Overview
TODO (3–5 short paragraphs):
- What this region *is* and what it’s like to arrive here.
- What dominates the senses: climate, terrain, sounds, smells, the “shape” of the place.
- What most outsiders believe is true (even if incomplete).
- What makes the region distinct from its neighbors.
- A final paragraph that hints at why someone would come here… or avoid it.

## What Outsiders Know
- TODO (2–3 sentences): broad climate and terrain. What an informed traveler expects before they arrive.
- TODO (2–3 sentences): a widely known landmark, feature, or historical scar. Something that shows up on maps or in stories.
- TODO (2–3 sentences): a common warning or reputation. Bandits, storms, cursed ground, brutal passes, etc.

## What Locals Understand
- TODO (2–3 sentences): the truth behind the climate (dry heat, sudden night cold, seasonal rains, humidity that clings, etc).
- TODO (2–3 sentences): practical knowledge outsiders lack. What to pack, what to avoid, when to travel, how to read the land.
- TODO (2–3 sentences): a local “everybody knows” detail. Customs, taboos, signals, safe routes, unspoken rules.

## Places Within
- TODO: [[City or Site]]
- TODO: [[Landmark Template]]
- TODO: [[Ruin / Dungeon]]
- TODO: [[Road / Pass / River Crossing]]

## Travel & Dangers
- **Terrain:** TODO (plains, marsh, broken hills, basalt cliffs, etc.)
- **Paths & Routes:** TODO (none, game trails, old roads, marked routes, river travel)
- **How people move:** TODO (on foot, mounts, carts, boats, Stormbringer route, escorts required)
- **What slows travel:** TODO (weather, flooding, steep grades, sand, dense growth, patrols, tolls)
- **Hazards:** TODO (predators, bandits, sickness, unstable ground, cursed sites, sudden storms)
- **Signs to watch for:** TODO (smoke columns, lantern codes, cairns, warnings, silence, unnatural tracks)

## Factions & Powers
- TODO: [[Faction]] (presence / influence, if any)
- TODO: [[Faction]] (presence / influence, if any)

## Myths & Rumors
- TODO
- TODO
- TODO
