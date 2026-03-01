<%*
/**
 * Sync: body → properties
 * - Reads the header block in the body
 * - Updates frontmatter fields to match
 *
 * Assumes lines like:
 * - **Client/Project:** X
 * - **Type:** Y
 * - **Date:** 2026-03-01 (Sunday)
 * - **Time:** 15:28
 * - **Location:** Z
 * - **Previous meeting:** N/A or [[...]]
 * - **Attendees:** A, B
 */

// Get full note content (string)
let content = tp.file.content;

// --- 1. Split out frontmatter safely ---
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

let frontmatterRaw = content.slice(firstSep + 3, secondSep).trim();
let body = content.slice(secondSep + 3).trimStart();

// --- 2. Extract header block: from first "#" to first --- in body ---
const headerMatch = body.match(/^(#.*?^---)$/ms);
if (!headerMatch) {
  new Notice("No header block found in body.");
  return;
}
const headerBlock = headerMatch[1];

// --- 3. Parse fields from header block ---
const getField = (label) => {
  const re = new RegExp(`^- \\*\\*${label}:\\*\\* ?(.*)$`, "m");
  const m = headerBlock.match(re);
  return m ? m[1].trim() : "";
};

const meetingTitleMatch = headerBlock.match(/^# (.*)$/m);
const meeting_title = meetingTitleMatch ? meetingTitleMatch[1].trim() : "";

const client           = getField("Client/Project");
const type             = getField("Type");
let dateLine           = getField("Date");
const time             = getField("Time");
const location         = getField("Location");
const previous_meeting = getField("Previous meeting");
const attendees        = getField("Attendees");

// Try to strip pretty part from date like "2026-03-01 (Sunday)" → "2026-03-01"
const dateMatch = dateLine.match(/^(\d{4}-\d{2}-\d{2})/);
const date = dateMatch ? dateMatch[1] : dateLine;

// --- 4. Parse current frontmatter lines (very simple YAML handling) ---
let lines = frontmatterRaw.split("\n");

// Helper: set or add a scalar key in YAML-like frontmatter
const setKey = (key, value) => {
  const idx = lines.findIndex(l => l.trim().startsWith(key + ":"));
  const yamlValue = (value === undefined || value === null) ? "" : String(value);
  if (idx === -1) {
    lines.push(`${key}: ${yamlValue}`);
  } else {
    lines[idx] = `${key}: ${yamlValue}`;
  }
};

// Update fields we care about
if (meeting_title) setKey("meeting_title", `"${meeting_title}"`);
if (client)        setKey("client", `"${client}"`);
if (type)          setKey("type", `"${type}"`);
if (date)          setKey("date", `${date}`);
if (time)          setKey("time", `${time}`);
setKey("location", `${location || ""}`);
if (previous_meeting) setKey("previous_meeting", `${previous_meeting}`);
if (attendees)    setKey("attendees", `${attendees}`);

// Rebuild frontmatter text
const newFm = lines.join("\n").trim();

// --- 5. Rebuild full content ---
const newContent = `---\n${newFm}\n---\n\n${body}\n`;

// Write note using Obsidian vault API
const file = app.workspace.getActiveFile();
if (!file) {
  new Notice("No active file.");
} else {
  await app.vault.modify(file, newContent);
}
-%>