---
title: Event Marker
tags:
  - event-properties/optional
---

[< Back to event overview](events/)

---

Individual notes can be explicitly included or excluded from the Gantt chart.
The frontmatter property `gantt-item` acts as a filter flag to mark a note's relevance.

### Why it exists

This property was primarily introduced during testing to allow quick toggling of notes without deleting their date metadata, helping maintain a clean and focused chart.

### Usage Considerations

- **Disabled by default**: To keep your note frontmatter minimal, this feature is disabled by default. Skipping it entirely saves you from managing an extra property in every note.
- **Opt-in workflow**: If you prefer explicit control over which notes appear on the chart, activate this feature in [[plugin-settings#Event Frontmatter Properties|Plugin Settings > Event Frontmatter Properties]].

## Examples

```yaml
---
gantt-item: true # Event will be shown on chart
---

---
gantt-item: false # Event will not be shown on chart
---
```

---

> [!info]- Property traits
> - This property is of type `checkbox` (boolean); its usage is optional.
> - You can rename it to your liking, see [[plugin-settings#Event Frontmatter Properties|Plugin Settings > Event Frontmatter Properties]].
