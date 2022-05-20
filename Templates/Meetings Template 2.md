---
dateCreated: "<% tp.file.creation_date() %>"
tags: [meeting]
---
Note Created: <%+ tp.file.creation_date() %>
Note Last Modified: <%+ tp.file.last_modified_date() %> %%Will render in Reading mode%%
Related Note: [[<% tp.date.now("YYYY-MM-DD_ddd") %>]]

# [[<% "Meeting - " + tp.date.now("YYYY-MM-DD HHmm") %>]]
<% tp.file.rename("Meeting - " + tp.date.now("YYYY-MM-DD HHmm")) %>
Topic: 
***

## Attendees

## Meeting Notes

## Companies

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