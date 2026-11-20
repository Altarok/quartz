---
title: Calendar Identifier
tags:
  - frontmatter/mandatory
  - yaml/mandatory
last-upated-plugin-version: 1.7.8
---

[< Back to calendar overview](calendars/)

---

Each calendar needs a *unique* identifier. Events use these identifiers to tell the plugin which calendar they refer to.

The identifier is defined by you in the calendar's `.md` file, you have to repeat the identifier in the file!

1. It must be set as value of the frontmatter property `'gantt-calendar-definition'`.
2. It must be set as value of the YAML property `'id'`.

> [!warning]+ Why the repetition?
> - The frontmatter property is useful for the plugin to quickly filter calendar files.
> - The YAML property is useful for the plugin to quickly parse your calendar.

Click to see some [calendar examples](example-calendars/).

---

> [!info]- Property traits
> The type of the frontmatter property `'gantt-calendar-definition'` is `text`.
> Its usage is mandatory in calendar definition notes.
> Unlike event properties, this property can not be renamed in the plugin's settings.
