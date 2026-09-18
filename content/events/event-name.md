---
title: Event Name
tags:
  - event-properties/optional
---

[< Back to event overview](events/)

---

![Showcase](images/showcase.png)

Each event displays a name on the Gantt chart.
The frontmatter property `gantt-name` sets a custom name for an individual event. If lacking the property, the note's filename will be shown on the chart.
To hide the name on the chart completely, set the property to an empty string (`gantt-name: ""`).

## Examples

```yaml
--- # No name given, defaults to filename 
---

---
gantt-name: "" # Empty name given, hides the name on the chart
---

---
gantt-name: "Aragorn's coronation"
---
```

---

> [!info]- Property traits
> - This property is of type `text`; its usage is optional.
> - You can rename it to your liking, see [[plugin-settings#Event Frontmatter Properties|Plugin Settings > Event Frontmatter Properties]].
