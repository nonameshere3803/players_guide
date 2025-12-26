<%*
const choice = await tp.system.suggester(
  [
    "City",
    "Village / Settlement / Camp",
    "District / Quarter",
    "Specific Location (Tavern, Temple, Shop, etc.)",
    "Infrastructure / Route (Gate, Bridge, Road, Port)"
  ],
  [
    "city",
    "settlement",
    "district",
    "location",
    "infrastructure"
  ],
  false,
  "What kind of place is this?"
)

// Prompt for name once (shared by all city-related notes)
let name = tp.file.path(true).split("/").pop().replace(/\.md$/i, "")
if (name.toLowerCase() === "untitled") {
  const input = await tp.system.prompt("Name of this place")
  if (input) {
    name = input
    await tp.file.rename(name)
  }
}

// Include the appropriate template
if (choice === "city") {
  tR += await tp.file.include("[[City Template]]")
} else if (choice === "settlement") {
  tR += await tp.file.include("[[Settlement Template]]")
} else if (choice === "district") {
  tR += await tp.file.include("[[District Template]]")
} else if (choice === "location") {
  tR += await tp.file.include("[[Location Template]]")
} else if (choice === "infrastructure") {
  tR += await tp.file.include("[[Infrastructure Template]]")
}
%>
