<%*
let displayName = tp.file.title

if (displayName.toLowerCase() === "untitled") {
  const input = await tp.system.prompt("Region name")
  if (input) {
    displayName = input
    await tp.file.rename(displayName)
  }
}

// tag-safe version: spaces → underscores
const tagName = displayName
  .trim()
  .replace(/\s+/g, "_")
%>
---
title: <%* tR += displayName %>
description: One-sentence summary of this region.
draft: true
tags:
  - places
  - region
  - Tōnacāpan
  - <%* tR += tagName %>
---

## At a Glance
- **Type:** Region / Landmark / Wilderness / Borderland
- **Known for:** TODO
- **Danger level:** Low / Moderate / High / Unknown
- **Best time to travel:** TODO

## Overview
TODO: 3–6 sentences. What is this place, broadly?

## What Travelers Know
- TODO (common knowledge)
- TODO (common knowledge)
- TODO (rumor or disputed)

## Places Within
- TODO: [[City or Site]]
- TODO: [[Landmark]]
- TODO: [[Dungeon / Ruin]]

## Factions & Powers
- TODO: [[Faction]] (influence/role)
- TODO: [[Faction]] (influence/role)

## Routes & Travel
- **From:** TODO
- **To:** TODO
- **Notes:** terrain, tolls, hazards, seasons

## Current Tensions
- TODO: political pressure, raids, monsters, resource conflict

## Notes & Hooks
- TODO: 1–3 player-facing leads or mysteries