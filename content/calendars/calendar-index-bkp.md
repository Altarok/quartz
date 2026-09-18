---
title: Calendar
draft: true
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

Calendars are the core of this plugin.

If you use custom time systems or fictional calendars in your vault, you can define them using a separate note.
For ease of understanding we will call it a calendar note. So there are 3 types of notes:

1) a note (the normal Obsidian note)
2) a calendar note (a note that holds calendar definitions)
3) an event note (a note that is an event in one of your calendars)

To mark a note as a calendar note you need to give it a special frontmatter property:

| Property                    | Type / Values | Optional? | Default / Fallback | Description                                                                              |
|:----------------------------|:--------------|:----------|:-------------------|:-----------------------------------------------------------------------------------------|
| `gantt-calendar-definition` | String        | **No**    | *None*             | Unique identifier of the calendar for referencing via `gantt-calendar` in an event note. |

## Calendar YAML Block Properties

- **`id`**: (string, required) Unique identifier for the calendar. Used by events `gantt-calendar` to reference this
  calendar.
- **`name`**: (string, optional) Human-friendly internal name for the calendar.
- **`displayName`**: (string, optional) Display name shown in the UI (if different from `name`).
- **`sharedOffset`**: (epoch offset definition, required) Defines the calendar's epoch offset. Can be either a single
  integer offset (days from reference day zero) or an object `{ year: number, month: number, day: number }` to describe
  the epoch relative to the plugin's reference. The plugin converts this to an internal numeric offset to day zero.
  Irrelevant if you use only one calendar.
- **`startDay`**: (epoch offset definition, optional) Start date for this calendar; converted to a numeric
  offset for range checks. As this is a calender definition and the calender is a linear numeric timeline which goes into both direction (negative and positive) counting from zero you either need to input the number of DAYS OR the date as defined in your calendar as a positive or negative number. *Example:*
  *Imagine you want to do an offset of one year and one day for a calendar which has 345 days.*
  *`startDay: +-x # x is days, not years!`*
  *`startDay: -346 # x is days, as offset into the negative!`*
  *`startDay: +346 # x is days, as offset into the positive!`*

alternativly you can do:

```
startDay:   
  year: +-x   
  month: y   
  day: z   
```

```
startDay:   
  year: 0   
  month: 12   
  day: 1   
```

OR if every line counts

`startDay: {year: 0, month: 12, day: 1}`

**Be aware that only year can be 0 or negative.
Month and day in this notation can never be 0 or negative.**

- **`endDay`**: (epoch offset definition, optional) End date for this calendar; converted to a numeric offset. See `startDay` the same applies here.
  for range checks.
- **`offsetToDayZero`**: (number, calculated) Not usually set by users — the plugin writes/calculates this value when
  reading the calendar from YAML. It represents days offset to the plugin's internal day-zero.
- **`type`**: (string, required) Calendar type. Supported values: `positional`, `rule-based`, `gregorian`. Determines
  which additional keys are required:
    - `positional`: Calendar defined by ordered positional units (e.g., seasons, boles). Use `positionalUnits`.
    - `rule-based` / `gregorian`: Use `ruleBasedDetails` to describe months, leap rules, and formats.
- **`delimiter`**: (string, optional) Separator used in textual date representations (for example `-` in
  `1420-Afterlithe-21`).
- **`positionalUnits`**: (array of objects, positional type only) Each unit is `{ name: string, days: number }`. Use for
  calendars that specify named positions with fixed day lengths rather than month/day rules.
- **`ruleBasedDetails`**: (object, rule-based/gregorian only) Contains details for month names, leap-year handling, and
  formatting:
    - **`months`**: array of month objects `{ name: string, shortname?: string, days: number, isIntercalary?: boolean }`
      describing month order and lengths. `isIntercalary` marks days that do not belong to any month (e.g., Yule days).
    - **`leapYearRule`**: object
      `{ ruleType: 'gregorian'|'interval'|'none', intervalYears?: number, extraDays?: number, applyToMonthIndex?: number }`
      describing how leap days are applied. `interval` with `intervalYears` adds every N years; `gregorian` uses the
      Gregorian exceptions; `none` disables leap days.
    - **`daysInStandardYear`**: integer, number of days in a normal year for this calendar (used for calculations).
    - **`format`**: array of date components `['year','month','day','intercalary']` describing how dates are written and
      parsed for this calendar (order of elements).
    - **`outputFormat`**: optional array like `format` to control how the plugin displays parsed dates (if omitted,
      `format` is used).
- **`bcSuffix` / `adSuffix`**: (string, optional) Suffixes to use for BC/AD labels if the calendar prints era markers.
- **`moons`**: (array of objects, optional) For lunar cycles: each moon is
  `{ offset: number, cycle: number, color?: string }` where `offset` shifts the phase, `cycle` is the length in days,
  and `color` is used for display.

### Notes on Types and Parsing

- Epoch offsets (`sharedOffset`, `startDay`, `endDay`) may be provided as a single integer (days) or as a
  `{ year, month, day }` object; the plugin converts them to absolute day offsets.
- `ruleBasedDetails.months` must sum sensibly to `daysInStandardYear` (except when intercalary days exist).
- Use `isIntercalary` for festival days or year-day elements that do not belong to a month; these are represented as
  separate elements in the calendar format.

