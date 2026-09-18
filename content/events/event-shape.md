---
title: Event Shape
tags:
  - event-properties/optional
---

[< Back to event overview](events/)

---

![Showcase](images/showcase.png)

Events can be displayed using different shapes.
The frontmatter property `gantt-symbol` customizes individual event markers.

Supported values include standard geometric shapes.
For timestamp events, these are:

- `point` (default)
- `triangle`
- `box`
- `diamond`
- `pentagon`
- `hexagon`
- `octagon`
- `star`
- `vertical-line`

For timespan events, these are:

- `bar` (default)
- `era`

> [!example]+ Example
> ```yaml
> ---
> gantt-start: 2026-05-10 # Timestamp event
> gantt-symbol: star
> ---
>
> ---
> gantt-start: 2026-05-12 # No symbol given, defaults to 'point'
> ---
> 
> ---
> gantt-start: 1970-01-01
> gantt-end: 2026-05-16 # An end date makes this event a timespan
> gantt-symbol: era
> ---
> ```

---

> [!info]- Property traits
> - This property is of type `text`; its usage is optional.
> - You can rename it to your liking, see [[plugin-settings#Event Frontmatter Properties|Plugin Settings > Event Frontmatter Properties]].
