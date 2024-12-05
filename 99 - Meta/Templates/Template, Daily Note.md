---
date: <%tp.date.now("dddd MMMM D, YYYY")%> <%tp.date.now("h:mm:sa")%>
tags: Daily
cssclasses: daily - <%tp.date.now("dddd",0,tp.file.title, "MMMM D, YYYY").toLowerCase()%>
---
[[<%tp.date.now("MMMM D, YYYY", -1)%>]] | [[<%tp.date.now("MMMM D, YYYY", +1)%>]]
***

<% tp.file.cursor(1) %>

