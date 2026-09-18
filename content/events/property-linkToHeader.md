---
title: Event property 'gantt-linkToHeader'
tags:
  - event-properties/optional
---

---

Clicking on any event in the Gantt chart normally opens the related note in a new tab.
The property `'gantt-linkToHeader'` is meant to overwrite this behavior.

If given and set to the name of any header in the note, ...

- Clicking the event will open the note and focus the header.
- Obsidian's native hover preview will also show the header.

> [!example]
> ```
> ---
> gantt-linkToHeader: [[WhatICanDoToday#EveningMeal]]
> ---
> ```

> [!tip]
> Property type is `text`, its usage is optional.
> You can rename it to you liking, see [[plugin-settings#Property Names & Key Mappings|Plugin Settings > Property Names & Key Mappings]]
