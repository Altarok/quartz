---
title: Event Header Link
tags:
  - event-properties/optional
---

[< Back to event overview](events/)

---

Clicking on any event in the Gantt chart normally opens the related note in a new tab.
The frontmatter property `gantt-linkToHeader` overrides this default behavior.

If set to the name of a heading in the note:

- Clicking the event will open the note and focus the heading.
- Obsidian's native hover preview will also show the heading.

> [!example]+ Example
> Add this to a note named "Daily tasks".
> Clicking the event opens "Daily tasks" directly at the "Take out the trash" heading.
>
> ```yaml
> ---
> gantt-linkToHeader: "[[Take out the trash]]"
> ---
> ```

---

> [!info]- Property traits
> - This property is of type `text`; its usage is optional.
> - You can rename it to your liking, see [[plugin-settings#Event Frontmatter Properties|Plugin Settings > Event Frontmatter Properties]].

