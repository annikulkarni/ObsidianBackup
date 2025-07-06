---
created: <% tp.date.now("YYYY-MM-DD") %>
tags: <% tp.system.suggester(["Agriculture", "Economics", "Geography", "International Relations", "Policy Making", "Science and Tech", "Social Justice", "Society", "Women"], ["#Agriculture", "#Economics", "#Geography", "#International Relations", "#Policy Making", "#Science and Tech", "#Social Justice", "#Society", "#Women"], { placeholder: "Select a category tag" }) %>
---
# <% tp.file.title %>

<%*
const moment = require('moment');
const fs = tp.file.vault.adapter;

// List of valid categories (without #)
const validCategories = ["Agriculture", "Economics", "Geography", "International Relations", "Policy Making", "Science and Tech", "Social Justice", "Society", "Women"];

// Verify the note is in the Notes folder
const currentPath = tp.file.path(true);
if (!currentPath.startsWith("Clippings/")) {
  tR += "Error: Note must be created in the Notes folder.";
  return;
}

// Get creation date (from YAML or file metadata)
let creationDate = tp.frontmatter.created || tp.file.creation_date("YYYY-MM-DD");
const date = moment(creationDate);

// Get ISO week number and year
const year = date.format("YYYY");
const week = date.format("[W]WW"); // e.g., W27 for July 6–July 12, 2025

// Get category from tags
let category = null;
const tags = tp.file.tags; // e.g., ["#Agriculture", "#CA"]
for (const tag of tags) {
  const cleanTag = tag.replace("#", "");
  if (validCategories.includes(cleanTag)) {
    category = cleanTag;
    break;
  }
}

// Fallback to Uncategorized if no valid category tag
if (!category) {
  category = "Uncategorized";
}

// Define target folder
const targetFolder = `${category}/${year}/${week}`;

// Create folder if it doesn’t exist
await fs.exists(targetFolder) || await fs.mkdir(targetFolder);

// Move the note to the target folder
const newPath = `${targetFolder}/${tp.file.title}.md`;
await fs.rename(currentPath, newPath);

// Update the note’s path in Obsidian
tR += `Note moved to ${newPath}`;
%>