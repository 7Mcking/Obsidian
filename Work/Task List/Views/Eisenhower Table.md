---
tags:
  - dashboard
  - eisenhower
  - views
cssclass: eisen-table
---
# 📋 Eisenhower Matrix 


```dataviewjs
// Collect tasks (incomplete)
const all = dv.pages("").file.tasks.where(t => !t.completed);

// Helpers
const hasTag = (t, tag) => (t.tags ?? []).includes(tag);

function quadrant(t){
  const u = hasTag(t, "#urgent");
  const i = hasTag(t, "#important");
  if (u && i) return "Urgent + Important";
  if (!u && i) return "Important, not urgent";
  if (u && !i) return "Urgent, not important";
  return "Neither";
}

// Sort order
const order = {
  "Urgent + Important": 1,
  "Important, not urgent": 2,
  "Urgent, not important": 3,
  "Neither": 4
};

const tasks = all.array()
  .map(t => ({ t, q: quadrant(t) }))
  .sort((a,b) => {
    const qa = order[a.q] ?? 99;
    const qb = order[b.q] ?? 99;
    if (qa !== qb) return qa - qb;

    const da = a.t.due?.ts ?? Number.POSITIVE_INFINITY;
    const db = b.t.due?.ts ?? Number.POSITIVE_INFINITY;
    if (da !== db) return da - db;

    return (a.t.link.path ?? "").localeCompare(b.t.link.path ?? "");
  });

// Build table
const table = dv.el("table", "", { cls: "eisen-table-view" });
const thead = table.createEl("thead");
const hr = thead.createEl("tr");

const headers = [
  { key: "q",    label: "Quadrant" },
  { key: "task", label: "Task (interactive)" },
  { key: "asgn", label: "Assigned To" },
  { key: "src",  label: "Source" },
  { key: "due",  label: "Due" },
];

for (const h of headers) {
  hr.createEl("th", { text: h.label, cls: `col-${h.key}` });
}

const tbody = table.createEl("tbody");

function sourceLinkCell(td, path){
  const a = td.createEl("a", { text: path.split("/").pop() });
  a.setAttr("href", `obsidian://open?path=${encodeURIComponent(path)}`);
}

// Render rows
for (const {t, q} of tasks) {
  const tr = tbody.createEl("tr");

  // Quadrant
  tr.createEl("td", { text: q, cls: "col-q" });

  // Task (interactive checkbox via Dataview)
  const tdTask = tr.createEl("td", { cls: "col-task" });
  const old = dv.container;
  dv.container = tdTask;
  dv.taskList([t], false);   // interactive checkbox
  dv.container = old;

  // Assigned To (section heading like "## Somak")
  const assigned = t.section?.subpath ?? "";
  tr.createEl("td", { text: assigned, cls: "col-asgn" });

  // Source
  const tdSrc = tr.createEl("td", { cls: "col-src" });
  sourceLinkCell(tdSrc, t.link.path);

  // Due
  const due = t.due ? t.due.toFormat("yyyy-LL-dd") : "";
  tr.createEl("td", { text: due, cls: "col-due" });
}
```


