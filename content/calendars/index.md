---
title: Calendar Configuration
tags:
  - calendar-properties/advanced
last-upated-plugin-version: 1.5.0
---

Calendars are the core of the plugin.
Custom calendars are defined using YAML frontmatter inside dedicated calendar notes. The plugin supports multiple different types of calendars.

The following screenshot shows 6 calendars.
![Screenshot with 6 calendars](images/six-calendars-showcase.png)

> [!tip]
> Note that you can click a calendar badge to open its note in a new tab.

## Basic Properties

| Property       | Short Description                       | Examples                                       | 
|----------------|-----------------------------------------|------------------------------------------------|
| `id`           | _Mandatory_, unique identifier.         | `shire`                                        | 
| `name`         | Full name of the calendar.              | `The Shire Reckoning`                          | 
| `displayName`  | Short name displayed at the chart axis. | `Hobbits`                                      | 
| `type`         | [[#Calendar Type]].                     | `rule-based` \| `positional`                   | 
| `delimiter`    | Character separating date parts.        | `-`, `/`, `.`                                  | 
| `sharedOffset` | Offset in days to your base calendar.   | +- (any integer)                               | 
| `bcSuffix`     | Date Suffix for years prior to epoch.   | `BCE`, `BC`                                    | 
| `adSuffix`     | Suffix for post-epoch years.            | `CE`, `AD`                                     | 
| `moons`        | List of [[calendar-moons\|moons]].      | See  [[calendar-moons#Example\|moons example]] | 
| `today`        | Any date in this calendar's format.     | `1234-Agosto-23`                               |        

<p>

## Calendar Type

A calendar's type is limited to [[#Rule-Based|`rule-based`]] or [[#Positional|`positional`]].
They define which YAML properties are mandatory and which are optional.

### Rule-Based

Calendars of this type are based on several rules.
Allows custom month lengths, intercalary days, and specific leap year rules. An extensive example would be:

```yaml
  daysInStandardYear: number              # number of total days in a non-leap year   
  noYearZero: boolean                     # (optional) boolean, true makes year go directly from 1 BCE to 1 CE
  leapYearRule: # see below, (optional) leap year rule
    ruleType: 'gregorian'                 # string: 'interval' | 'gregorian' 
    intervalYears: number                 # (optional for type 'gregorian') number of years from 1 leap year to another
    extraDays: number                     # (optional for type 'gregorian') number of extra days (default: 1)
    applyToMonthIndex: number             # (optional for type 'gregorian') index of month
  months: # see below, list of months
    days: number                          # number of days in month
    name: string                          # (optional) string, full name of month
    shortname: string                     # (optional) string, short name of month 
    isIntercalary: boolean                # (optional) boolean (default: false)
  format: ['year', 'month', 'day']        # any combination of these 3 values in any order, may omit 'month'
  outputFormat: ['day', 'month', 'year']  # (optional) same values as format in different order (default: same as format)
```

#### Months

Months are generally optional. If given, they are defined like this:

```yaml
  months:
    - {shortname: "Jag", name: "Jaguar", days: 31} # short notation
    - shortname: "Feb"        # long notation goes over multiple lines
      name: "February"
      days: 22
    - days: 45                # omitting names is totally fine 
    - name: Midyear
      days: 1
      isIntercalary: true     # not part of a month (for example see Hobbit calendar)
```

A calendar _without months_ could look like this

```yaml
ruleBasedDetails:
  format:
    - "year"
    - "day"
  months: []
```

### Positional

Uses fixed numeric units instead of traditional months (e.g., Mesoamerican/Mayan count cycles).

.. work in progress

---

> [!info]- Traits & Settings
> - Calendar notes are automatically indexed when placed in your configured calendar folder.
> - For global calendar settings, see [[plugin-settings#Calendar Configuration|Plugin Settings > Calendar Configuration]].
