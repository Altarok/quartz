---
title: Event Calendar
tags:
  - event-properties/optional
---

[< Back to event overview](events/)

---

Each event belongs to one calendar.
The frontmatter property `gantt-calendar` assigns the event to a specific calendar ID defined in your plugin settings.

When configured with a valid calendar ID:

- The event renders using the rules, epoch offsets, and leap years of that calendar.
- The chart colors and displays the event according to the designated calendar configuration.

If omitted, the event defaults to your primary calendar.

```yaml
---
gantt-start: 1420-05-12
gantt-calendar: shire-calendar
---
```

... is not the same as ...

```yaml
---
gantt-start: 1420-05-12
gantt-calendar: gregorian
---
```

---

> [!info]- Property traits
> - This property is of type `text`; its usage is optional.
> - You can rename it to your liking, see [[plugin-settings#Event Frontmatter Properties|Plugin Settings > Event Frontmatter Properties]].

> [!note]- Legacy Property Name
> In earlier versions of the plugin, this property was named `gantt-type`. No frontmatter updates are required when upgrading, as property key mappings are preserved in your plugin settings.
