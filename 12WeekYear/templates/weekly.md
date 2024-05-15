---
twystart: 2024-02-19
goals: 2
sow: <% tp.date.weekday("YYYY-MM-DD", 0, tp.file.title, "YYYY-[W]WW") %>
eow: <% tp.date.weekday("YYYY-MM-DD", 6, tp.file.title, "YYYY-[W]WW") %>
cssclass: "weekly-note"
---

```dataviewjs
const {TwelveWeekYear} = customJS;
// Array containing goals IDs: [1,2,...]
const goalsArray = Array.from({length: dv.current().goals}, (_, i) => i + 1);
// request tasks for each goal for this week
const resultsWeek = await Promise.all(goalsArray.map(v => {return dv.query(TwelveWeekYear.getWeekTasksQuery(dv.current(), v))}));
// request tasks for each goal for the 12 week year until today (or end of this week)
const resultsYear = await Promise.all(goalsArray.map(v => {return dv.query(TwelveWeekYear.getYearTasksQuery(dv.current(), v))}));
// create container element
let elem = this.container.createEl('div', {cls: ["twy-widget"]});
// render widget
await TwelveWeekYear.render(elem, resultsWeek, resultsYear, dv.current().twystart.toFormat('yyyy-MM-dd'), dv.current().eow.toFormat('yyyy-MM-dd'), dv.current().goals);
```
# MONDAY
![[<% tp.date.weekday("YYYY-MM-DD", 0, tp.file.title, "YYYY-WW") %>]]

# TUESDAY
![[<% tp.date.weekday("YYYY-MM-DD", 1, tp.file.title, "YYYY-WW") %>]]

# WEDNESDAY
![[<% tp.date.weekday("YYYY-MM-DD", 2, tp.file.title, "YYYY-WW") %>]]

# THURSDAY
![[<% tp.date.weekday("YYYY-MM-DD", 3, tp.file.title, "YYYY-WW") %>]]

# FRIDAY
![[<% tp.date.weekday("YYYY-MM-DD", 4, tp.file.title, "YYYY-WW") %>]]

# SATURDAY
![[<% tp.date.weekday("YYYY-MM-DD", 5, tp.file.title, "YYYY-WW") %>]]

# SUNDAY
![[<% tp.date.weekday("YYYY-MM-DD", 6, tp.file.title, "YYYY-WW") %>]]
