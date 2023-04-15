
```dataviewjs
const rows = dv
	.pages('"Blog"')
	.sort(r => r.date, "desc")
	.filter(r => !r.draft && r.slug)
	.map((r, i, all) => {
		r.file.link.display = r.title
		return [
			r.file.link,
			r.date.toString().split('T')[0].replaceAll('-', '/'),
			all.length - i,
		]
	})

dv.table(['File', 'Date', 'id'], rows)
```
