---
dateCreated: "<% tp.file.creation_date() %>"
score: "1-10"
tags: [dailyNote]
workEnd: ""
workLocation: "home/office"
workStart: ""
---
Note Created: <%+ tp.file.creation_date() %>
Note Last Modified: <%+ tp.file.last_modified_date() %> %%Will render in Reading mode%%

<< [[<% tp.date.now("YYYY-MM-DD_ddd", -1, tp.file.title, "YYYY-MM-DD") %>]] | [[<% tp.date.now("YYYY-MM-DD_ddd", 1, tp.file.title, "YYYY-MM-DD") %>]] >>

# [[<% tp.file.title %>]]
***
## To Dos

## Reminders

## Daily Review


***
## Footnotes
Resources
Links to this page
```dataview
LIST
FROM [[#]]
WHERE file.path != this.file.path
SORT file.name ASC
```