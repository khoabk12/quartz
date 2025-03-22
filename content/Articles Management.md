---
date: 2025-03-02T15:09:50+07:00
---
# Published
```dataview
table file.name as "File Name"
from ""
where publish = true
sort file.name asc
```

# Draft

```dataview
table file.name as "File Name", draft
from ""
where draft != null
sort file.name asc
```


```dataview
table file.name as "File Name" from "" where draft = false
```
