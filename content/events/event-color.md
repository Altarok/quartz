---
title: Event Color
tags:
  - event-properties/optional
---

[< Back to event overview](events/)

---

![Showcase](images/showcase.png)

Event markers can be colored, as seen in the showcase.
The frontmatter property `gantt-color` sets a custom color for an individual event.
Note that `era` events add transparency to their color.

> [!tip]+ Color priority
> An event can get colored in four different ways. In descending priority, these are:
> 1. Value of the event's property `gantt-color` (Optional)
> 2. Color of the event's group (Optional)
> 3. Color of the event's calendar (Optional)
> 4. Global fallback color.

## Example

```yaml
---
gantt-color: yellow
---
```

---

> [!info]- Property traits
> - This property is of type `text`; its usage is optional.
> - You can rename it to your liking, see [[plugin-settings#Event Frontmatter Properties|Plugin Settings > Event Frontmatter Properties]].
