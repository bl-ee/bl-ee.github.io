```{=html}
<%
let currentYear = null;

function noteDate(value) {
  const date = value instanceof Date ? value : new Date(value);
  return {
    year: date.getFullYear(),
    short: String(date.getMonth() + 1).padStart(2, "0") + "/" +
      String(date.getDate()).padStart(2, "0")
  };
}
%>
<% for (const item of items) { %>
  <% const date = noteDate(item.date); %>
  <% if (date.year !== currentYear) { %>
    <% if (currentYear !== null) { %>
</ul>
    <% } %>
<h2 class="notes-year"><%= date.year %></h2>
<ul class="notes-list">
    <% currentYear = date.year; %>
  <% } %>
  <li>
    <span class="note-date"><%= date.short %></span>
    <span aria-hidden="true">-</span>
    <a href="<%- item.path %>"><%- item.title %></a>
  </li>
<% } %>
<% if (currentYear !== null) { %>
</ul>
<% } %>
```
