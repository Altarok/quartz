---
title: Event property 'gantt-linkToHeader'
tags:
  - frontmatter/optional
---

[< Back to event overview](events/index)

---

Clicking on any event in the Gantt chart normally opens the related note in a new tab.
The frontmatter property `'gantt-linkToHeader'` is meant to overwrite this behavior.

If given and set to the name of any header in the note, ...

- Clicking the event will open the note and focus the header.
- Obsidian's native hover preview will also show the header.

> [!example]+ Example
> At this to a note named "Daily tasks".
> When the event is clicked, the note "Daily tasks" will be opened and focused at the header "Take out the trash".
>
> ```yaml
> ---
> gantt-linkToHeader: [[Take out the trash]]
> ---
> ```

---

> [!info]- Property traits
> Property type is `text`, its usage is optional.
> You can rename it to your liking, see [[plugin-settings#Property Names & Key Mappings|Plugin Settings > Property Names & Key Mappings]]
