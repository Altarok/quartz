---
title: Property 'gantt-group'
tags:
  - event-properties/optional
---

[< Back to event overview](events/index)

---

![Showcase](images/showcase.png)

Events can be organized into vertical groups displayed on the left side of the Gantt chart.
The frontmatter property `'gantt-group'` assigns an event to a designated row.

In the example above, events are categorized into the `'symbols'`, `'icons'`, and `'general'` groups.

> [!tip] Tips
> - Events of type `era` or `vertical-line` not given a group will span the entire height of the chart. As seen on the right side of the showcase.
> - Other events lacking a group will be placed into the group `'general'`.

### Managing groups

Groups can be managed in the [[plugin-settings#Groups|Plugin Settings > Groups]]. This is optional, but doing so allows you to:

- Reorder groups by priority.
- Set a default color for all events in a specific group.
- Toggle visibility for an entire group.

---

> [!info]- Property traits
> Property type is `text`, its usage is optional.
> You can rename it to your liking, see [[plugin-settings#Property Names & Key Mappings|Plugin Settings > Property Names & Key Mappings]]
