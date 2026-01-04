# Title

File Created: <% tp.file.creation_date() %>
Last Modified: <% tp.file.last_modified_date() %>
<%* tp.hooks.on_all_templates_executed(async () => {
  const file = tp.file.find_tfile(tp.file.path(true));
  await tp.app.fileManager.processFrontMatter(file, (frontmatter) => {
    frontmatter["publish"] = "true";
  });
}); 
-%>


Status:

Tags:

  
# References
