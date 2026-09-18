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

\*: Property `gantt-calendar-definition` marks and holds a calendar definition.
See: [[calendars/]]
\*\*: Property `gantt-item` may be set to optional in the settings.

*All of these can be renamed to your liking*.
