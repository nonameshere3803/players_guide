---
title: <% tp.file.title %>
description: <%* tR += "TODO: One-sentence summary of what this section contains." %>
draft: false
tags:
  - section
  - player-guide
  - <%* 
    const folder = (tp.file.folder(true).split("/").pop() || "").toLowerCase();
    const map = {
      "charting the new world": "geography",
      "people of the new world": "people",
      "a short history of the new world": "history",
      "history": "history",
      "maps": "maps"
    };
    tR += (map[folder] || "section-topic");
  %>
---

<%* tR += "TODO: 1–2 sentences of orientation (optional). Delete this line if you want it ultra-minimal." %>

## Explore

- [Overview]
- [Subsection One]
- [Subsection Two]

## Notes

- Information here is player-facing and reflects common knowledge, rumor, and partial records.
