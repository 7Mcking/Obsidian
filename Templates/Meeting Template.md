<%*
/**
 * Meeting template with:
 * - Prompted meeting title
 * - Prompted client & type
 * - Automatic filename
 * - Previous meeting link
 */

// 1. Ask for high-level info
const meetingTitle = await tp.system.prompt("Meeting title", "Weekly Mech Sync");
const client       = await tp.system.prompt("Client / Project", "Mech Sync");
const kind         = await tp.system.prompt("Meeting type (e.g. Weekly)", "Weekly");

// 2. Build and apply filename: 2026-03-01 - Mech Sync - Weekly
const date = tp.date.now("YYYY-MM-DD");
const newName = `${date} - ${client} - ${kind}`;
if (tp.file.title !== newName) {
  await tp.file.rename(newName);
}

// 3. Find previous meeting (same client + type) in this folder
const folder = tp.file.folder(true);
const allFiles = app.vault.getFiles().filter(f => f.path.startsWith(folder));
const currentDate = date;
let previousFile = null;

for (const f of allFiles) {
  const match = f.basename.match(/^(\d{4}-\d{2}-\d{2}) - (.+) - (.+)$/);
  if (!match) continue;
  const [_, fDate, fClient, fType] = match;
  if (fClient === client && fType === kind && fDate < currentDate) {
    if (!previousFile || fDate > previousFile.date) {
      previousFile = { file: f, date: fDate };
    }
  }
}

const prev = previousFile ? previousFile.file : null;
-%>
---
meeting_title: "<% meetingTitle %>"
client: "<% client %>"
type: "<% kind %>"
date: <% date %>
time: <% tp.date.now("HH:mm") %>
attendees: 
location: 
previous_meeting: <% prev ? "[[" + prev.basename + "]]" : "" %>
tags: [meeting, "<% client %>"]
---
# <% meetingTitle %>

- **Client/Project:** <% client %>
- **Type:** <% kind %>
- **Date:** <% tp.date.now("YYYY-MM-DD (dddd)") %>
- **Time:** <% tp.date.now("HH:mm") %>
- **Location:** 
- **Previous meeting:** <% prev ? "[[" + prev.basename + "]]" : "N/A" %>
- **Attendees:**
  - 

---

## Agenda

- [ ] 

---

## Notes

- 

---

## Decisions

- [ ] 

---

## Action Items

- [ ] **Owner:**  • **Task:**  • **Due:** 