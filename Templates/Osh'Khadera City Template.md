<%*
let displayName = tp.file.title

if (displayName.toLowerCase() === "untitled") {
  const input = await tp.system.prompt("City / Settlement name")
  if (input) {
    displayName = input
    await tp.file.rename(displayName)
  }
}

// tag-safe version: spaces → underscores (leave punctuation as-is unless you want stricter)
const tagName = displayName
  .trim()
  .replace(/\s+/g, "_")
%>
---
title: <%* tR += displayName %>
description: One-sentence summary of this city (what it’s known for).
draft: true
tags:
  - places
  - city
  - Osh'Khadera
  - <%* tR += tagName %>
---

## At a Glance
- **Type:** City / Town / Port / Fort / Village / Ruin
- **Population:** TODO
- **Authority:** TODO
- **Primary Trade:** TODO
- **Languages:** TODO

## What Travelers Know
- TODO (common knowledge)
- TODO (common knowledge)
- TODO (rumor)

## Districts & Notable Places
- **TODO District:** [[Location]] , [[Location]]
- **TODO District:** [[Location]] , [[Location]]
- **Outside the Walls:** [[Location]]

## People You Might Meet
- **[[NPC Name]]** — TODO (role + why they matter)
- **[[NPC Name]]** — TODO

## Factions & Politics
- **[[Faction]]** — TODO (influence / goals)
- **Local Laws:** weapons, magic, contraband, curfew, etc.

## Services
- **Lodging:** TODO
- **Food & Drink:** TODO
- **Gear & Repairs:** TODO
- **Healing / Temples:** TODO

## Rumors & Hooks
- TODO (lead)
- TODO (problem)
- TODO (mystery)

## Notes
TODO
