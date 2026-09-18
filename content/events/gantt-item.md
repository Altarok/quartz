---
title: Property 'gantt-item'
tags:
  - event-properties/optional
---

[< Back to event overview](events/index.md)

---

Individual notes can be explicitly toggled to be included or excluded from the Gantt chart.
The frontmatter property `'gantt-item'` acts as a filter flag to mark a note's relevance.

### Why it exists

This property was primarily introduced during testing to allow quick toggling of notes without deleting their date metadata, helping maintain a clean and focused chart.

### Usage considerations

- **Disabled by default**: To keep your note frontmatter minimal, this property is disabled by default. Skipping it entirely saves you from managing an extra property in every note.
- **Opt-in workflow**: If you prefer explicit control over which notes appear on the chart, activate this feature in [[plugin-settings#Frontmatter Properties|Plugin Settings > Frontmatter Properties]].

> [!example]+ Example
> ```yaml
> ---
> gantt-item: true # event will be shown on chart
> ---
> 
> ---
> gantt-item: false # event will not be shown on chart
> ---
> ```

---

> [!info]- Property traits
> Property type is `checkbox`, its usage is optional.
> You can rename this property to your liking, see [[plugin-settings#Property Names & Key Mappings|Plugin Settings > Property Names & Key Mappings]].
