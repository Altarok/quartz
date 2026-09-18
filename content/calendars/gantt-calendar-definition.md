---
title: Calendar property 'gantt-calendar-definition'
tags:
  - frontmatter/calendar/mandatory
---

[< Back to calendar overview](calendars/index.md)

---

Serves as the root YAML key to define a complete calendar system within a note.
The property `'gantt-calendar-definition'` marks a note as a calendar definition profile for the plugin to parse.

When present in frontmatter:

- Registers a calendar profile with a unique `id` for events to reference via [[gantt-calendar]].

You can see multiple examples [[example-calendars/index|here]].

> [!warning]+ The frontmatter property value must match the value of the YAML property `'id'`.
> Why the repetition?
> - The frontmatter property is useful for the plugin to quickly filter calendar files.
> - The YAML property is useful for the plugin to quickly parse your calendar.

---

> [!abstract]- Property traits
> Property type is `text`, its usage is mandatory in calendar definition notes.
> Unlike event properties, this root key is fixed and cannot be renamed in settings.
