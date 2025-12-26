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

// Derive secondary tag from last meaningful word in folder name
const stopWords = ["of", "the", "and", "new"]
const words = folderName.split(" ").filter(w =>
  !stopWords.includes(w.toLowerCase())
)
const derivedTag = words.length > 0
  ? words[words.length - 1].replace(/\s+/g, "_")
  : null

// Reusable description text
const descriptionText = `An overview of ${folderName}.`
%>
---
title: <%* tR += folderName %>
description: <%* tR += descriptionText %>
draft: true
tags:
  - <%* tR += category %>
<%* if (derivedTag) { tR += `  - ${derivedTag}\n` } %>
---




TODO: 1–2 sentences of orientation (optional). Delete this line if you want it ultra-minimal.

## Explore

- [Overview]
- [Subsection One]
- [Subsection Two]

## Notes

- Information here is player-facing and reflects common knowledge, rumor, and partial records.
