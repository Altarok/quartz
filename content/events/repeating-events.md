---
title: Repeating Events
tags:
  - event-properties/optional
last-upated-plugin-version: 1.5.2
---

[< Back to event overview](events/)

---

Repeating events are the core of modern organization. You can make your events repeat.

## How It Works

To make this work add a suffix to one of your date properties `gantt-start` or `gantt-end`.

- If an event is a [[event-dates#Naming|timestamp]], the start date suffix will be parsed.
- [!] If an event is a [[event-dates#Naming|timespan]] instead, the end date suffix beats the start date suffix in priority _if two suffices are defined_.

The suffix consists of 2 comma-separated parts: _How often to repeat_ & _when to end repetitions_.

## 1. How Often To Repeat

To repeat a fixed date in different years, add `' repeat yearly'` or `' repeat after X years'` to your date.
To repeat on day based pattern, add `' repeat daily'` or `' repeat after X days'` to your date.
`X` must be a positive integer > 0 in both cases.

### Year Based Repetition

Use this for _birthdays_ or similar events.

- [p] Pro: Takes leap years into account.
- [c] Con: Only works when the event's calendar configuration is [[calendar-dateformat|rule-based]] and its rule contains `year`.

**Calendar**:

```yaml
type: "rule-based"
format: ["year", "month", "day"] # must contain "year"
```

### Daily Based Repetition

To repeat any [[event-dates#Naming|timestamp]] event after X days, add `' repeat after X days'` to your _start date_. For this to work, X must be a natural number > 0.
To repeat any [[event-dates#Naming|timespan]] event after X days, add `' repeat after X days'` to your _end date_. In this case X may be zero, but never < 0.

- [p] Pro: Works with any calendar.
- [c] Con: Does not work for birthdays in leap year calendars.

### Examples

```yaml
gantt-start: 2026-09-29 repeat after 14 days # a bi-weekly task
```

```yaml
gantt-start: 2026-09-26 repeat after 7 days # a Saturday
gantt-end: 2026-09-27 # a Sunday (this would be weekends)
```

```yaml
gantt-start: 2026-11-22 repeat yearly # a birthday
```

```yaml
gantt-start: 2026-09-29 repeat after 4 years # Olympic games
```

## 2. When To End Repetitions

By default, events start repeating themselves on the note's start date.
Therefore, adding another start date is not possible (yet).

To end an event, type `, until [any date]` after the first suffix.

### Examples For ending Repetitions

The _Historic Olympic Games_ were held from -776 BCE to 393 CE.

```yaml
gantt-start: "-776 repeat after 4 years, until 394"
```

