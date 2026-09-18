---
title: Property 'gantt-symbol'
tags:
  - event-properties/optional
---

[< Back to event overview](events/index.md)

---

![Showcase](images/showcase.png)

Events have different shapes.
The frontmatter property `'gantt-symbol'` allows you to customize individual event markers.

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
> gantt-start: 2026-05-10 # timestamp event
> gantt-symbol: star
> ---
>
> ---
> gantt-start: 2026-05-12 # no symbol given, will default to 'point'
> ---
> 
> ---
> gantt-start: 1970-01-01
> gantt-end: 2026-05-16 # an end date makes this event a timespan
> gantt-symbol: era
> ---
> ```

> [!tip]- Tips
> Property type is `text`, its usage is optional.
> You can rename this property to your liking, see [[plugin-settings#Property Names & Key Mappings|Plugin Settings > Property Names & Key Mappings]].
