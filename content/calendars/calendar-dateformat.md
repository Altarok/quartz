---
title: Calendar Date Format
tags:
  - yaml/optional
last-upated-plugin-version: 1.4.4
---

[< Back to calendar overview](calendars/)

---

## Positional Calendars (`type: 'positional'`)

Positional calendars count time using fixed, hierarchical units of days rather than variable months or leap years (similar to the Mayan Long Count).

### Configuration Properties

| Property          | Type    | Description                                                                                      |
|:------------------|:--------|:-------------------------------------------------------------------------------------------------|
| `positionalUnits` | `Array` | Ordered list of units from **largest to smallest**, defined by how many days each unit contains. |

### Example (Mayan Long Count)

```yaml
id: mayan-calendar
name: Mayan Long Count
type: positional
delimiter: "."
positionalUnits:
  - name: B'ak'tun
    days: 144000
  - name: K'atun
    days: 7200
  - name: Tun
    days: 360
  - name: Winal
    days: 20
  - name: K'in
    days: 1
```

---

## Rule-Based Calendars

Rule-based calendars define structured years made up of months, custom date formatting, and optional leap years (e.g., Shire/Hobbit, Elven, or custom fantasy calendars).

```yaml
type: "rule-based"
```

### Configuration Properties

| Property                              | Type      | Description                                                                 |
|:--------------------------------------|:----------|:----------------------------------------------------------------------------|
| `ruleBasedDetails.daysInStandardYear` | `number`  | Total number of days in a non-leap year.                                    |
| `ruleBasedDetails.months`             | `Array`   | List of month definitions (`name`, `shortname`, `days`, `isIntercalary`).   |
| `ruleBasedDetails.format`             | `Array`   | Order of date components when parsing strings (`['year', 'month', 'day']`). |
| `ruleBasedDetails.noYearZero`         | `boolean` | Optional. `true` if year count transitions directly from 1 BC to 1 AD.      |

### Example

```yaml
id: fantasy-standard
name: Imperial Calendar
type: rule-based
delimiter: "-"
sharedOffset: 0
ruleBasedDetails:
  daysInStandardYear: 360
  format: ["year", "month", "day"]
  months:
    - name: Firstseed
      days: 30
    - name: Midyear
      days: 30
```

---

## Intercalary Days (`isIntercalary`)

Intercalary days are standalone days or festival periods that sit **between** months and do not belong to any standard month structure (e.g., the Hobbit calendar's *Midyear Days* or *Yule* days).

### How to Define Intercalary Days

Set `isIntercalary: true` on an entry inside the `months` array:

```yaml
ruleBasedDetails:
  daysInStandardYear: 365
  months:
    - name: Foreyule
      days: 30
    - name: Yuletide # Intercalary period
      days: 2
      isIntercalary: true
    - name: Afteryule
      days: 30
```

---

## Leap Year Rules (`leapYearRule`)

Defines how extra days are added to a rule-based calendar on specific recurring year intervals.

### Rule Types (`ruleType`)

* **`gregorian`**: Uses standard Gregorian leap rules ($\text{every 4 years}, \text{except 100}, \text{unless 400}$).
* **`interval`**: Adds extra day (s) every $N$ years.
* **`none`**: Disables leap years entirely.

### Configuration Options

| Property            | Type     | Description                                                  |
|:--------------------|:---------|:-------------------------------------------------------------|
| `intervalYears`     | `number` | How often the leap year repeats (e.g., `4`).                 |
| `extraDays`         | `number` | How many days are added during the leap year (default: `1`). |
| `applyToMonthIndex` | `number` | 0-based index of the month receiving the extra day(s).       |

### Example

```yaml
leapYearRule:
  ruleType: interval
  intervalYears: 4
  extraDays: 1
  applyToMonthIndex: 1 # Adds the extra day to the 2nd month (index 1)
```
