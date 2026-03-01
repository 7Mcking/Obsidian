---
tags:
  - dashboard
  - eisenhower
  - "#views"
cssclass: eisen-kanban
date: 2026-03-01
image: https://imgs.search.brave.com/2ECenEc4fbrkMmQ85ysUwp4C8dwfQy-LOp3peVbfDbk/rs:fit:860:0:0:0/g:ce/aHR0cHM6Ly93d3cu/c2h1dHRlcnN0b2Nr/LmNvbS9pbWFnZS12/ZWN0b3IvZWlzZW5o/b3dlci1tYXRyaXgt/dXJnZW50LWltcG9y/dGFudC1wcmlvcml0/aXplLTI2MG53LTE3/MDY2MTk1NjIuanBn
---
## 🔴 Q1 — Urgent & Important  
```dataview  
TASK
FROM ""
WHERE !completed
AND contains(tags, "#urgent")
AND contains(tags, "#important")
```  
  
## 🟢 Q2 — Important, Not Urgent  
```dataview  
TASK  
FROM ""  
WHERE !completed  
AND !contains(tags, "#urgent")  
AND contains(tags, "#important")
FLATTEN file.link AS Source 
```  
  
## 🟡 Q3 — Urgent, Not Important  
```dataview  
TASK  
FROM ""  
WHERE !completed  
AND contains(tags, "#urgent")  
AND !contains(tags, "#important")  
```  
  
## ⚪ Q4 — Neither  
```dataview  
TASK  
FROM ""  
WHERE !completed  
AND !contains(tags, "#urgent")  
AND !contains(tags, "#important")  
```
