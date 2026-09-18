---
title: Property 'gantt-group'
tags:
  - event-properties/optional
---

[< Back to event overview](events/index)

---

![Showcase](images/showcase.png)

All events can be placed into groups which are visible at the left of the Gantt chart.
The frontmatter property `'gantt-group'` is meant to do that.
The events in the showcase are sorted into the groups `'symbols'`, `'icons'`, and `'general'` (see left side of screenshot).

> [!tip] Tips
> - An event without a group will be given the fallback group `'general'`.
> - Events of type `era` or `vertical-line` not given a group will span the entire height of the chart. As seen on the right side of the showcase.

# Managing groups

Groups can be managed in the Plugin settings. This is optional, but doing so allows you to:

- Sort groups by priority.
- Define a default color for events of that group.
- Toggle visibility for events of that group.

---

> [!info]- Property traits
> Property type is `text`, its usage is optional.
> You can rename it to your liking, see [[plugin-settings#Property Names & Key Mappings|Plugin Settings > Property Names & Key Mappings]]
