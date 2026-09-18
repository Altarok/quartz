---
title: Calendar Definition
tags:
  - calendar-properties/advanced
---

[< Back to event overview](events/)

---

Calendars are the core of the plugin.
Custom calendars are defined using YAML frontmatter inside dedicated calendar notes. The plugin supports multiple different types of calendars.

Have a look at [[gregorian-calendar|this example]] before reading any further.

## Basic Properties

| Property       | Type                 | Description                                                                 | 
|----------------|----------------------|-----------------------------------------------------------------------------|
| `id`           | `text`               | **Mandatory.** Unique identifier for the calendar (e.g., `shire-calendar`). |
| `name`         | `text`               | Full name of the calendar.                                                  |
| `displayName`  | `text`               | Short name displayed at the chart axis.                                     |
| `type`         | `text`               | Calendar algorithm type: `gregorian`, `rule-based`, or `positional`.        |
| `delimiter`    | `text`               | Character separating date parts (e.g. `-`, `/`, or `.`).                    |
| `sharedOffset` | `number` \| `object` | Offset in days to Day Zero of your default/base calendar.                   |
| `bcSuffix`     | `text`               | Suffix for years prior to epoch (e.g., `BCE`).                              |
| `adSuffix`     | `text`               | Suffix for post-epoch years (e.g., `CE`).                                   |

## Calendar Types

### Gregorian

Standard modern calendar system. Does not require custom month or leap year definitions.

### Rule-Based

Allows custom month lengths, intercalary days, and specific leap year rules (e.g., Shire, Elven, or custom fantasy calendars).

### Positional

Uses fixed numeric units instead of traditional months (e.g., Mesoamerican/Mayan count cycles).

## Rule-Based Calendar Properties

When `type` is set to `rule-based`, define the structure under `ruleBasedDetails`:

- `daysInStandardYear`: Total days in a non-leap year.
- `noYearZero`: Set to `true` if the calendar moves directly from year 1 BCE to 1 CE.
- `format`: List defining input parsing order (`year`, `month`, `day`, `intercalary`).
- `months`: Array of month definitions containing `name`, `shortname`, `days`, and optional `isIntercalary` flags.

## Examples

Custom Rule-Based Calendar

```yaml
---
id: shire-calendar
name: Shire Calendar
type: rule-based
delimiter: "-"
sharedOffset: 0
ruleBasedDetails:
  daysInStandardYear: 365
  format:
    - year
    - month
    - day
  months:
    - name: Afterlithe
      days: 30
    - name: Midyear Day
      days: 1
      isIntercalary: true
---
```

---

> [!info]- Traits & Settings
> - Calendar notes are automatically indexed when placed in your configured calendar folder.
> - For global calendar settings, see [[plugin-settings#Calendar Configuration|Plugin Settings > Calendar Configuration]].
