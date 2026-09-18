---
title: Event Properties
tags:
  - event-properties
---

![Showcase](images/showcase.png)

This screenshot shows all possible types of events including some randomly chosen icons.
In the chart, each element above the calendar axis represents an event defined in a Markdown note.

## Features & Structure

- **Events:** Each point or bar in the timeline corresponds to an event. Events are split into timestamps and timespans.
    - **Bars:** Represent time spans.
    - **Points / Symbols:** Represent specific points in time or milestones.
- **Decentralized in Frontmatter:** Events are defined directly within the YAML properties of your Markdown files.
- **Structuring:** Events can be organized, filtered, and sorted by groups and custom calendars.
- **Flexible Visibility:** Groups, calendars, time spans, and individual points can be shown or hidden independently.
- **Custom Styling:** Points in time can be customized with icons from Obsidian's cache and custom colors.
- **Interactivity:**
    - Mouseover displays relevant metadata in a tooltip (Desktop).
    - Clicking an event directly opens the source note—optionally jumping to a specific heading.
    - Full navigation via drag & zoom (mouse wheel on Desktop, touch gestures on mobile devices).

## Populating Your Gantt Chart / Timeline

See below for more in-depth examples.
To display one or more notes as events in your timeline, add the corresponding properties to the YAML frontmatter of your Markdown file:

```yaml
gantt-item: true           # Optional by default: Marks the note as an event 
gantt-start: 2026-01-01    # Start date / point in time
gantt-end: 2026-01-05      # Optional: end date (fallback: gantt-start) - marks event as timespan if given
gantt-name: "My Project"   # Optional: name (fallback: filename)
gantt-group: "Development" # Optional: group (fallback: `general`)
```

# Note property Overview

The following table lists all available properties you can use in your notes:

| Property                                                 | Type    | Mandatory | Description                                                               | Fallback                                |
|:---------------------------------------------------------|:--------|:----------|:--------------------------------------------------------------------------|:----------------------------------------|
| [[calendar-definition]]                                  | String  | Yes\*     | Marks the note as holding a calendar definition                           | _None_                                  |
| [[event-marker\|gantt-item]]                             | Boolean | Yes\*\*   | Marks the note as an event target for the plugin.                         | true                                    |
| [[event-type\|gantt-calendar]]                           | String  | No        | Determines the assigned calendar type.                                    | Calendar for this event                 |
| [[event-name\|gantt-name]]                               | String  | No        | Name of the event in the timeline and tooltip.                            | Filename, without extension             |
| [[event-start\|gantt-start]]                             | String  | Yes       | Start date or start value of the event.                                   | _None_                                  |
| [[event-end\|gantt-end]]                                 | String  | No        | End date of the event. If identical to start value, a point is displayed. | Value of `gantt-start`                  |
| [[event-symbol\|gantt-symbol]]                           | String  | No        | Sets the visual representation format of the event.                       | `bar` (timespan) or `point` (timestamp) |
| [[event-color\|gantt-color]]                             | String  | No        | Overrides the background color of the event individually.                 | Group color → Calendar color → Default  |
| [[event-group\|gantt-group]]                             | String  | No        | Group used for row layout and structuring.                                | `'general'`                             |
| [[event-icon\|gantt-displayIcon]]                        | String  | No        | Displays an icon on the event.                                            | *None*                                  |
| [[event-icon\|gantt-displayIconColor]]                   | String  | No        | Sets the color of the icon.                                               | Default icon color                      |
| [[event-heading\|gantt-linkToHeader]]                    | String  | No        | Links directly to a specific heading when clicked.                        | *None* (Jumps to top of file)           |
| [[event-predecessors-and-succesors\|gantt-predecessors]] | list    | No        | Predecessor events will be highlighted on the chart                       | *None*                                  |
| [[event-predecessors-and-succesors\|gantt-succesors]]    | list    | No        | Successor events will be highlighted on the chart                         | *None*                                  |

\*: Property `gantt-type-definition` marks and holds a calendar definition.
See: [[Calendars]]
\*\*: Property `gantt-item` may be set to optional in the settings.

*All of these can be renamed to your liking*.

# Understanding Event Properties

## Timespan Events (bar)

![Timespans](images/showcase-highlighted-timespans.png)
Any event with start- and end-date property is defined as a timespan.
There are two types of timespan events:

- `'bar'`: Bars are shown as horizontal rectangles. See markers (4) and (5) in the screenshot: (4) is named 'Bar' and set into group 'symbols', while (5) is placed into group 'icons.'

- `'era'`: Eras are shown as semi-transparent rectangle behind all other events. They can be placed in a group or span the entire height of the chart (if no group is defined). See markers (1), (2) and (3) in the screenshot. (1) is placed in group 'symbols', (2) inside 'icons', while (3) has no group.

```yaml
gantt-start: 2026-08-27
gantt-end: 2026-08-30
gantt-symbol: bar | era | (omit or leave empty to default to 'bar')
```

## Timestamp Events (point)

![Timespans](images/showcase-highlighted-timestamps.png)
Timestamp events are defined by adding a start-date to any event. Omit the end-date or leave it empty.

There are 8 different symbols usable for a normal timestamp event. All of these function the same way, the only thing that changes is the SVG graphic. See central box of the screenshot.

- `point` | `triangle` | `box` | `diamond` | `pentagon` | `hexagon` | `octagon` | `star`

But they were all betrayed - for a ninth symbol was made to betray them all. See right box of the screenshot. This symbol was added to create separators and/or markers for special days like "today". Similar to `era` above, it spans the entire height when not placed into a specific group.

- `vertical-line`

```yaml
gantt-start: 2026-08-27
gantt-symbol: point | triangle | box | diamond | pentagon
  | hexagon | octagon | star | (omit for default symbol - configurable in settings)
```

## Special dates

Right now, there is one special keyword: `today`. This will be interpreted as your local current day. Adding this to an event will obviously show it at different timestamps each day.

You can add a fixed amount of days to it. To achieve this you can use the following properties:

```yaml
gantt-start: 2026-08-20
gantt-end: today+5
```

