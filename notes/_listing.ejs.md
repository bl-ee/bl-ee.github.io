```{=html}
<%
function noteDate(value) {
  const date = value instanceof Date ? value : new Date(value);
  return String(date.getFullYear()) + "-" +
    String(date.getMonth() + 1).padStart(2, "0") + "-" +
    String(date.getDate()).padStart(2, "0");
}
%>
<ul class="notes-list">
<% for (const item of items) { %>
  <% const date = noteDate(item.date); %>
  <li>
    <div class="note-row">
      <a class="note-title" href="<%- item.path %>"><%- item.title %></a>
      <time class="note-date" datetime="<%= date %>"><%= date %></time>
    </div>
  </li>
<% } %>
</ul>
```
