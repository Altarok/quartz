---
title: Calendar Today
tags:
  - yaml/optional
last-upated-plugin-version: 1.6.9
---

[< Back to calendar overview](calendars/)

---

Calendars _may_ have a top-level parameter `'today'`.

## The today Parameter

The `today` parameter defines the reference date for a calendar. It allows you to use dynamic dates in bases options (such as lower and upper bounds) and event notes (e.g., setting an ongoing task's end date to today).

### Rules and Behavior

- **Format Dependency**: The date must strictly match order defined in the calendar's `format` parameter.
- **No Automatic Highlighting**: `today` only establishes a logical reference point. It does not render a visual marker on the chart. To highlight today visually, you must define an event note (such as a `vertical-line` or a `star`).
- **Gregorian Fallback**: If the calendar ID is set to gregorian and today is omitted, the plugin automatically falls back to the real-world current date. For custom calendars, no fallback exists.
- **Relative Expressions**: You can apply relative math offsets directly when referencing it in event dates or chart (upper and lower) bounds:
    - `today -30` (30 days in the past)
    - `today +7` (7 days in the future)

### Example

```yaml
id: harptos
name: "Calendar of Harptos"
today: "1234-Hammer-15"
format: ['year', 'month', 'day']
months:
  - name: "Hammer"
    days: 30
  - name: "Alturiak"
    days: 30
# ...
```
