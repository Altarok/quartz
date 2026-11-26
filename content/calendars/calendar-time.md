---
title: Time of Day Configuration
tags:
  - time-of-day
  - yaml/optional
last-upated-plugin-version: 1.8.0
---

[< Back to calendar overview](calendars/)

---

## What is Time of Day?

Time of day lets you position events within a single day rather than snapping every start or end point to a whole-day boundary.

Internally, time of day is expressed as a fractional day offset added to `startDays` and `endDays` so sub-day start and end positions render accurately on the timeline.

---

## How to configure Time of Day?

Time of day values are attached to events or calendar settings depending on how your timeline rules and frontmatter properties are structured.

1. [[#Supported Formats|Supported Formats]]
2. [[#Fractional Day Behavior|Fractional Day Behavior]]
3. [[#Examples|Examples]]

> [!tip] To read about common configuration sections, see [here](calendars/).

---

### Supported Formats

Time of day values parse clock-style strings into fractional day offsets (`0.0` to `1.0` across a 24-hour day).

```yaml
start-time: "08:30"
end-time: "17:15"
```

> [!tip]+ Whole-Day Alignment
> All internal timeline, offset, and duration calculations in the plugin combine whole days (`startDays`, `endDays`) with fractional day offsets (`startTimeOfDay.value`, `endTimeOfDay.value`). Keep start and end times consistent so sub-day intervals stay accurate.

---

### Fractional Day Behavior

When time of day is omitted, the fractional offset defaults to `0`, keeping the event aligned with the start of the day.

```yaml
defaultTimeOfDay: "00:00"
```

1. **Clock parsing:** Converts time strings into a numeric day fraction (`value`) used in `startDayWithTimeOfDay` and `endDayWithTimeOfDay`.
2. **Missing values:** Default cleanly to the start of the day (`0`) when not specified on an event.
3. **Timeline rendering:** Shifts visual placement along the axis without altering whole-day counters (`startDays` and `endDays`).

> [!warning]+ Duration and Ordering
> Make sure end times do not precede start times on single-day events unless your span intentionally crosses into a following day.

Click to see some [calendar examples](example-calendars/).

---

### Examples

A typical workday entry pairs date fields with start and end times so you can distinguish morning and afternoon blocks on the same day.

```yaml
gantt-start: 10
start-time: "09:00"
gantt-end: 10
end-time: "12:30"
```

1. **Morning block:** Starts at `09:00` (`0.375` of a day) and ends at `12:30` (`0.5208...` of a day) on day `10`.
2. **Full-day fallback:** Omitting start and end times treats the bounds as `0.0` offset on their respective days.

---

> [!info]- Property traits
> 1. Time of day fields are **optional**; omitting them defaults to a `0` day offset.
> 2. Whole-day fields (`startDays`, `endDays`) remain separate from parsed time-of-day fractions.
> 3. Base calendar and event properties still apply as usual.

