---
title: Event Dates
tags:
  - event-properties/mandatory
last-upated-plugin-version: 1.4.4
---

[< Back to event overview](events/)

---

![Showcase](images/showcase.png)

All events have a start and end point in time. Since the plugin does not support time of day (yet), all days point to a single point on an infinite timeline.

## Naming

- **Timestamps**: Events without an end date will be called _timestamp_ in this documentation, since they point to a single point on the timeline.
- **Timespan**: Events with an end date will be called _timespan_, since they point to a range of points on the timeline.

For this to work, the frontmatter property `gantt-start`, defining a start date, is the ==only mandatory property== for any event.
Omitting `gantt-end` will make the event a _timestamp_.

## Dates

Dates must match a [[calendar-dateformat|calendar's date format]] to be parsed by the plugin.
The [[gregorian-calendar|Gregorian Calendar]] will be used for the following examples.

## Special Dates

Right now, there is one special keyword: `today`. This will be interpreted as your local current day. Using it for an event will obviously show it at different timestamps each day.

You can add a fixed amount of days to it. To achieve this you can write: `today` + (`+` or `-`) + (`a positive integer`)

## Repeating Events

There's a [[repeating-events|special page]] for it.

## Examples

```yaml
---
gantt-start: 2026-08-20
gantt-end: today+5 # This makes the event duration increase each day
---

---
gantt-start: 2026-02-30 # Event will not render on the chart since February never has 30 days
---

---
gantt-start: today # This adds a marker to your calendar always showing the current date
gantt-symbol: vertical-line
---
```

---

> [!info]- Property traits
> - Both properties are of type `text`.
> - The `gantt-start` property is mandatory, `gantt-end` is optional.
> - You can rename them to your liking, see [[plugin-settings#Event Frontmatter Properties|Plugin Settings > Event Frontmatter Properties]].
