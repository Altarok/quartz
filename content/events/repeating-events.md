---
title: Repeating Events
tags:
  - event-properties/optional
last-upated-plugin-version: 1.4.5
---

[< Back to event overview](events/)

---

Repeating events are the core of modern organization. You can make your events repeat.

## How It Works

To make this work add a suffix to one of your date properties `gantt-start` or `gantt-end`.
- If an event is a [[event-dates#Naming|timestamp]], the start date suffix will be parsed.
- [!] If an event is a [[event-dates#Naming|timespan]] instead, the end date suffix beats the start date suffix in priority _if two suffices are defined_.

## Yearly Repetition

This is the easiest suffix to create, just add `' repeat yearly'` to your date.
Use it for _birthdays_ and other dates repeating on the same day each year.

- [p] Pro: This takes leap years into account.
- [c] Con: It only works when the event's calendar configuration is [[calendar-dateformat|rule-based]] and its rule contains `year`.  

### Example

Calendar:

```yaml
type: "rule-based"
format: ["year", "month", "day"] # must contain "year"
```

Event:

```yaml
gantt-start: 2026-09-29 repeat yearly
```

## Day-based Repetition

To repeat any [[event-dates#Naming|timestamp]] event after X days, add `' repeat after X days'` to your _start date_. For this to work, X must be a natural number > 0.
To repeat any [[event-dates#Naming|timespan]] event after X days, add `' repeat after X days'` to your _end date_. In this case X may be zero, but never < 0.

- [p] Pro: Works with any calendar.
- [c] Con: Does not work for birthdays in leap year calendars.

### Examples

```yaml
gantt-start: 2026-09-29 repeat after 7 days # once every week (if in Gregorian calendar)
```

```yaml
gantt-start: 2026-09-26 repeat after 7 days # Saturday
gantt-end: 2026-09-28 # Sunday (this would be weekends)
```

