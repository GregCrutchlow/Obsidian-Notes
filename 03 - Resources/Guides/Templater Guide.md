
### Code Snipets

###### How to jump cursor to specified area in template
```
<% tp.file.cursor(1) %>
```

###### How to set date for link

Sets link to yesterdays date, "November 30, 2024"
```
[[<% tp.date.yesterday("MMMM D, YYYY") %>]]
```

Sets link to tomorrows date, "December 2, 2024"
```
[[<% tp.date.tomorrow("MMMM D, YYYY") %>]]
```