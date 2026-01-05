---
publish: "false"
---
# Title

File Created: <% tp.file.creation_date() %>  
Last Modified: <% tp.file.last_modified_date() %>

<% tp.file.move("/Unpublished Notes/" + tp.file.title) %>