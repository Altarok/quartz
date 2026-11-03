---
title: Calendar Weekdays
tags:
  - yaml/optional
last-upated-plugin-version: 1.7.1
---

[< Back to calendar overview](calendars/)

---

## Weekdays

The `weekdays` property inside a [[calendars/|Calendar Configuration]] defines the repeating cycle of named days that form a week in your world. Custom calendars can feature weeks of any length—from a simple 3-day cycle to complex fantasy weeks spanning dozens of days.

Weekdays are displayed sequentially on the calendar axes, date pickers, and view headers.

## Configuration

The `weekdays` property is a structured object containing an offset and an array of individual weekday definitions.

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 820 220" width="100%" style="background-color: #1e1e1e; font-family: monospace; border-radius: 8px;">
  <!-- Track line -->
  <line x1="40" y1="140" x2="780" y2="140" stroke="#444" stroke-width="2" />

  <!-- Week 1 Box -->
  <rect x="60" y="70" width="330" height="110" fill="none" stroke="#4bc0c0" stroke-width="1.5" stroke-dasharray="4,4" rx="6" />
  <text x="225" y="60" fill="#4bc0c0" font-size="12" text-anchor="middle" font-weight="bold">Cycle Repeats (dayCount: 3)</text>

  <!-- Week 2 Box -->
  <rect x="430" y="70" width="330" height="110" fill="none" stroke="#4bc0c0" stroke-width="1.5" stroke-dasharray="4,4" rx="6" />
  <text x="595" y="60" fill="#4bc0c0" font-size="12" text-anchor="middle" font-weight="bold">Next Cycle</text>

  <!-- Day Ticks Cycle 1 -->
  <circle cx="100" cy="140" r="6" fill="#ffd700" />
  <text x="100" y="115" fill="#ffd700" font-size="12" text-anchor="middle" font-weight="bold">Moonday</text>
  <text x="100" y="168" fill="#888" font-size="11" text-anchor="middle">Index 0</text>

  <circle cx="225" cy="140" r="6" fill="#ffffff" />
  <text x="225" y="115" fill="#ffffff" font-size="12" text-anchor="middle" font-weight="bold">Godsday</text>
  <text x="225" y="168" fill="#888" font-size="11" text-anchor="middle">Index 1</text>

  <circle cx="350" cy="140" r="6" fill="#ff6666" />
  <text x="350" y="115" fill="#ff6666" font-size="12" text-anchor="middle" font-weight="bold">Waterday</text>
  <text x="350" y="168" fill="#888" font-size="11" text-anchor="middle">Index 2</text>

  <!-- Day Ticks Cycle 2 -->
  <circle cx="470" cy="140" r="6" fill="#ffd700" />
  <text x="470" y="115" fill="#ffd700" font-size="12" text-anchor="middle" font-weight="bold">Moonday</text>

  <circle cx="595" cy="140" r="6" fill="#ffffff" />
  <text x="595" y="115" fill="#ffffff" font-size="12" text-anchor="middle" font-weight="bold">Godsday</text>

  <circle cx="720" cy="140" r="6" fill="#ff6666" />
  <text x="720" y="115" fill="#ff6666" font-size="12" text-anchor="middle" font-weight="bold">Waterday</text>
</svg>

| Property | Type        | Default | Description                                             |
|:---------|:------------|:--------|:--------------------------------------------------------|
| `offset` | `number`    | `0`     | Shift in days relative to calendar's **Day 0**.         |
| `days`   | `Weekday[]` | n/a     | Ordered array of weekday objects defining the sequence. |

### Weekday Object (`Weekday`)

| Property | Type                | Default | Description                                  |
|:---------|:--------------------|:--------|:---------------------------------------------|
| `name`   | `string`            | n/a     | Full name of the weekday.                    |
| `short`  | `string` (optional) | n/a     | Abbreviation used in compact calendar views. |

The sequence of `days` repeats continuously throughout the calendar starting from **Day 0** (adjusted by `offset`).

## Example

Below is the `weekdays` configuration in a [[calendars/|Calendar Configuration]] demonstrating the root object structure alongside short-name abbreviations:

```yaml
weekdays:
  offset: 0 # 0 -> no offset. 1st day of calendar = 1st day of array
  # x -> offset start of week by x days. (1+x)th day of calendar = 1st day of array       
  days:
    - name: Moonday
      short: Moo
    - name: Godsday
    - {name: Waterday, short: Wat}
    - name: Marketday
    - name: Restday
      short: Rst
```
