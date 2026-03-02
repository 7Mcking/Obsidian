<%*
/**
 * Sync: properties → body
 * - Reads frontmatter from tp.frontmatter
 * - Rewrites the "header block" in the body
 */

const fm = tp.frontmatter;

// Helper: format date nicely if it's YYYY-MM-DD
let prettyDate = "";
if (fm.date) {
  try {
    prettyDate = tp.date.now("YYYY-MM-DD (dddd)", 0, fm.date);
  } catch (e) {
    prettyDate = fm.date;
  }
}

// Build header block from properties
const headerBlock = [
  `# ${fm.meeting_title || tp.file.title}`,
  "",
  `- **Client/Project:** ${fm.client || ""}`,
  `- **Type:** ${fm.type || ""}`,
  `- **Date:** ${prettyDate || (fm.date || "")}`,
  `- **Time:** ${fm.time || ""}`,
  `- **Location:** ${fm.location || ""}`,
  `- **Previous meeting:** ${fm.previous_meeting || "N/A"}`,
  `- **Attendees:** ${fm.attendees || ""}`,
  "",
  "---",
  ""
].join("\n");

// Get current file content (string)
const content = tp.file.content;

// Find frontmatter block
const firstSep = content.indexOf("---");
if (firstSep === -1) {
  new Notice("No frontmatter found.");
  return;
}
const secondSep = content.indexOf("---", firstSep + 3);
if (secondSep === -1) {
  new Notice("No closing frontmatter delimiter found.");
  return;
}

const frontmatterRaw = content.slice(firstSep + 3, secondSep).trim();
let body = content.slice(secondSep + 3).trimStart();

// Replace the first header block (from # ... until the first ---) if present
const headerRegex = /^#.*?^---$/ms;
if (headerRegex.test(body)) {
  body = body.replace(headerRegex, headerBlock + "---");
} else {
  // If no header/--- block found, just prepend it
  body = headerBlock + "---\n" + body;
}

// Rebuild full content
const newContent = `---\n${frontmatterRaw}\n---\n\n${body.trimStart()}\n`;

// Write note using Obsidian vault API
const file = app.workspace.getActiveFile();
if (!file) {
  new Notice("No active file.");
} else {
  await app.vault.modify(file, newContent);
}
-%>