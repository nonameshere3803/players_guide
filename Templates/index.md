<%*
const folderPath = tp.file.folder(true)
const parts = folderPath.split("/")
const folderName = parts[parts.length - 1]

// Prompt for category tag
const category = await tp.system.suggester(
  ["people", "places", "things"],
  ["people", "places", "things"],
  false,
  "Select category tag"
)

// Decide whether this folderName is a structural label like "Regions of X"
const lower = folderName.toLowerCase()
const structuralPrefixes = [
  "regions of ",
  "cities of ",
  "inhabitants of ",
  "history of ",
  "story of ",
  "people of ",
  "places of ",
  "history of ",
  "story of ",
]

const isStructural = structuralPrefixes.some(p => lower.startsWith(p))

// If structural, tag is the part after " of " (e.g., "Regions of Westerion" -> "Westerion")
// Otherwise, tag is the full folder name (e.g., "Order of the Veil" -> "Order of the Veil")
let tagSource = folderName
if (isStructural && lower.includes(" of ")) {
  tagSource = folderName.split(/ of /i).slice(-1)[0]
}

// Normalize tag:
// - remove apostrophes (straight and curly)
// - collapse whitespace to underscores
const derivedTag = tagSource
  .replace(/['’]/g, "")
  .trim()
  .replace(/\s+/g, "_")

// Reusable description
const descriptionText = `An overview of ${folderName}.`
%>
---
title: <%* tR += folderName %>
description: <%* tR += descriptionText %>
draft: true
tags:
  - <%* tR += category %>
  - <%* tR += derivedTag %>
---






TODO: 1–2 sentences of orientation (optional). Delete this line if you want it ultra-minimal.

## Explore

- [Overview]
- [Subsection One]
- [Subsection Two]

## Notes

- Information here is player-facing and reflects common knowledge, rumor, and partial records.
