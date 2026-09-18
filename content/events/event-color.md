---
title: Event Color
tags:
  - event-properties/optional
---

[< Back to event overview](events/)

---

![Showcase](images/showcase.png)

Event markers can be colored, as seen in the showcase. Note that `era` events add transparency to their color.
The color value can be a human-readable CSS color like for example `red`, `forestgreen`, `teal` - or a 6-digit hex value starting with `#` like `#ff00ff`, `#bada55`, `#123456`.

The frontmatter property `gantt-color` sets a custom color for an individual event.

> [!tip]+ Color priority
> There are four sources for an event's color. In descending priority, these are:
> 1. Value of the event's property `gantt-color` (Optional)
> 2. Color of the event's group (Optional)
> 3. Color of the event's calendar (Optional)
> 4. Global fallback color.

## Examples

```yaml
---
gantt-color: yellow
---

---
gantt-color: "#FFFF00"
---
```

---

> [!info]- Property traits
> - This property is of type `text`; its usage is optional.
> - You can rename it to your liking, see [[plugin-settings#Event Frontmatter Properties|Plugin Settings > Event Frontmatter Properties]].
