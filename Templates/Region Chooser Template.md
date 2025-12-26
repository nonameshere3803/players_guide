<%*
const kind = await tp.system.suggester(
  ["Region", "Landmark"],
  ["region", "landmark"],
  false,
  "Create what?"
)

let name = tp.file.title
if (name.toLowerCase() === "untitled") {
  const input = await tp.system.prompt(kind === "region" ? "Region name" : "Landmark name")
  if (input) {
    name = input
    await tp.file.rename(name)
  }
}

if (kind === "region") {
  tR += await tp.file.include("[[Region Template]]", { name })
} else {
  tR += await tp.file.include("[[Landmark Template]]", { name })
}
%>
