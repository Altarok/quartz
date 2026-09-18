---
title: Plugin Settings
last-upated-plugin-version: 1.3.0
---

## Map of contents

The plugin's settings are distributed among 4 setting groups, the latter one being split into and 2 sub-pages.

1. [[#Data paths]] - define which files to use for the chart
2. [[#Calendars]] - manage your calendars
3. [[#Groups]] - manage your groups
4. [[#Advanced]]
    - [[#Display and controls]] - manage user experience
        - [[#Events]] - default event values
        - [[#Event overlay]] - graphics when hovering events
        - [[#Zooming and Panning]]
        - [[#Gantt chart]]
        - [[#Plugin]] - plugin-wide settings
    - [[#Frontmatter properties]] - manage frontmatter properties
        - [[#Calendar Frontmatter Properties]]
        - [[#EventFrontmatter Properties]]

# Data paths

This section tells the plugin where to search for event and calendar notes.

- `Event path`: Folder to search for Gantt event definitions. Can be any folder including vault root.
    - Default: root
- `Search recursively`: Toggle to search `Event path` recursively.
    - Default: false
- `Calendar path`: Folder to search for calendar definitions. Can be any folder including vault root.
    - Default: root
- `Search recursively`: Toggle to search `Calendar path` recursively.
    - Default: false

# Calendars

This section manages your calendars.
Click the `'+'` button to create a new calendar.

> [!tip] Calendar IDs must be unique and case-sensitive!

- You can toggle the calendar visibility by clicking the `eye` button.
- You can choose (or reset) the calendar's color, this applies to related events lacking a color.
- You can sort the calendar priorities by dragging the vertical line button.
- You can delete a calendar. This will not remove it from any charts, only delete color, visibility and priority.

# Groups

See [[#Calendars]], it's 100% the same logic.

# Advanced

The following settings are hidden in sub-pages.

## Display and controls

### Events

- **Symbol**: Choose a shape for timestamp events. See [[gantt-symbol]].
    - Default: `'point'`
- **Calendar**: Default event calendar. See [[gantt-calendar]].
    - Default: `'gregorian'`
- **Group**: Default event group. See [[gantt-group]].
    - Default: `'general'`
- **Color**: Default event color. See [[gantt-group]].
    - Default: `#1565C0`
- **Icon color**: Default icon color. See [[gantt-color]].
    - Default: `#FF8800`
- **Vertical line width**: Width of vertical line events. Raise to simplify clicking the event.
    - Default: 3
- ~~Filename as start date~~: Deactivated for now as it tries to parse your entire vault's filenames if not configured properly.

### Event overlay

This section handles what happens when hovering events with your mouse.

- **Highlight event**: If true, will show a box around the hovered event matching the event's shape.
    - Toggle. Default: true
- **Highlight related events**: If true, will highlight predecessors and successors of hovered event with native highlight color.
    - Toggle. Default: true
- **Connect related events**: If true, will draw arrows between hovered event and its predecessors and successors.
    - Toggle. Default: false
- **Show vertical line**: If true, will show a vertical line over the hovered event to compare to others in the same time range.
    - Toggle. Default: false
- **Color**: Color for both highlights: surrounding box and vertical line.
- **Tooltip**: If true, will add the event's absolute day to its tooltip. Useful for testing and comparison.
    - Toggle. Default: false

### Zooming and Panning

This section handles how and when the plugin zooms and pans around the chart.

- **Restrict minimum and maximum zoom**: If true, the maximum zoom shows 4 adjacent days, minimum zoom fits your complete dataset.
    - Toggle. Default: true
- **Zoom key** & **Pan key**: While can pan while dragging the chart horizontally (mouse or finger) or zoom with 2-finger pinching (mobile only), these settings allow you to define 2 additional ways to do so using the mouse wheel. For each, choose a button to hold while scrolling to achieve zoom or pan.
- **Zoom and pan buttons**: Additionally to the options in the aforementioned setting, you can zoom and pan in fixed steps using buttons in the toolbar. To see them, activate this setting.
    - Toggle. Default: true

### Gantt chart

This section additional things related to the chart itself.

- **Moons**: If true, each calendar's moons will appear over the calendar axis.
    - Toggle. Default: true
- **Show group visibility toggles**: If true, adds 1 button per group to the toolbar for quick visibility toggles.
    - Toggle. Default: false
- **Color-code calendar axis**: If true, each calendar's color will apply to its axis. This may strain the eye if using very much calendars.
    - Toggle. Default: false
- **Move toolbar down**: If true, moves the toolbar to below the chart. Use this if you barely use the toolbar.
    - Toggle. Default: false
- **Rerender cooldown (seconds)**: Slow down the rerender listener
    - Number between 0 and 30. Default: 5

### Plugin

This section lets you add additional utilities to Obsidian.

- **Add ribbon icon**: If true, adds a ribbon icon with a fully functioning chart live preview for testing. You *can* copy the thereby created code block or save it directly to the currently open Markdown file. This may be useful to define multiple charts in one note. Reload app after change.
    - Default (desktop): true
    - Default (mobile): false
- **Add plugin commands**: If true, adds commands to Obsidian. Reload app after change. See [[commands]].
    - Default: true

## Frontmatter Properties

This section lets you rename the frontmatter properties used by the plugin. Note that you can't change the property types (yet). ***Doing so enables you to use the same properties for multiple plugins***.

### Calendar Frontmatter Properties

- **Calendar definition**: Frontmatter key used to identify a calendar definition file.
    - Default: `gantt-calendar-definition`. See [[gantt-calendar-definition]]

### Event Frontmatter Properties

- **Event marker**: Primary boolean frontmatter key that marks a file as containing Gantt events.
    - Default: `gantt-item`.
- **Marker may be optional**: If enabled, the primary marker becomes optional. This saves one property per file but reduces explicit control.
    - Default: true (meaning it *is* optional)
- **Event calendar**: Frontmatter key that defines which calendar an event belongs to. Default:
  `gantt-calendar`.
- **Event name**: Frontmatter key for the event name. Default: `gantt-name`.
- **Event start date**: Frontmatter key for the event start date (mandatory). Default:
  `gantt-start`.
- **Event end date**: Frontmatter key for the event end date (optional). Default: `gantt-end`.
- **Event color**: Frontmatter key for event color (hex or name). Default: `gantt-color`.
- **Event group**: Frontmatter key for the event's group (used to sort and color events). Default: `gantt-group`.
- **Event symbol**: Frontmatter key to override the event symbol per-event. Default: `gantt-symbol`.
- **Event icon**: Frontmatter key for an icon name (Lucide icons). Default: `gantt-displayIcon`.
- **Event icon color**: Frontmatter key for the icon color. Default: `gantt-displayIconColor`.
- **Target header**: Frontmatter key for a note-internal header; when set clicking the event will
  navigate to that header instead of top-of-note. Default: `gantt-linkToHeader`.

------------

### Default Values

- **`defaultCalendar`**: Fallback calendar used when an event does not specify a calendar. Default: `gregorian`.
- **`fallbackColor`**: Default color used for events when no color is provided. Default: `#1565C0`.
- **`fallbackColorForIcons`**: Default icon color when an event has an icon but no icon color. Default: `#FF8800`.

## Groups

![[Pasted image 20260905163326.png]]

Two lists display the calendars and groups currently known to the plugin. Both lists function identically:

- **Calendar list**: Defines which calendars the plugin recognizes and how they appear.
- **Group list**: Defines which groups the plugin recognizes and how they appear.

#### Entry Properties

- **ID**: A unique identifier
    - Used by frontmatter `gantt-calendar`/`gantt-calendar-definition` for calendars.
    - Used by frontmatter `gantt-group` for groups.
    - *Note: These are __NOT CASE-SENSITIVE__!*
- **Visibility**: Toggles whether related events are shown on the chart.
- **Color**: Optional color applied to color related events and axis.
- **Priority**: Order of appearance in the list determines sorting in the chart.

#### List Controls

- **Add entry**: Click the `+` icon in the list header.
- **Delete entry**: Click the `X` icon.
- **Reset color**: Click the reset button next to the color picker to revert to the default event color.
- **Reorder**: Drag and drop using the handle icon (`⋮`).

### Advanced UX Settings

- **Event symbol**: Default symbol for timestamp events.
    - Options: `point`, `triangle`, `box`, `diamond`, `pentagon`, `hexagon`, `octagon`, `star` and
      `vertical-line`.
- **Add ribbon icon**: Show a ribbon icon in the Obsidian UI to quickly open a live chart preview.
- **Add plugin commands**: Add plugin commands (currently work-in-progress / disabled in UI).
- **Show overlay box**: Show an overlay box around an event when hovered.
- **Show overlay vertical line**: Show a vertical line on hover to compare dates.
- **Group visibility toggles**: Add toolbar buttons that allow hiding/showing groups individually.
- **Restrict minimum and maximum zoom**: Automatically constrain min/max zoom to reasonable bounds for the current data.
    - Minimum zoom would fit your complete dataset on the screen.
    - Maximum zoom would show adjacent days.
- **Zoom key**: Key to hold while scrolling to zoom in or out.
- **Pan key**: Key to hold while scrolling to pan horizontally.
    - Both options offer Ctrl, Alt, and Shift. (Ctrl, Option, Shift on MacOS)
- **Color-code calendar axis**: Apply calendar color to its axis (may be visually noisy; optional).
- **Vertical line event width**: Numeric width, in pixels, for events drawn as vertical lines (slider 1–10).

### Notes & Usage Tips

- Use `Calendars` to register calendar definitions (files that define non-Gregorian calendars). Calendar `id` values are
  used in frontmatter to map events to calendars.
- The `Default values` section allows you to set global fallbacks for color and calendar when individual events omit
  them.
- The `Groups` mechanism is useful to build lanes and logical separations for events (for example, locations, factions,
  or categories).
- Advanced UX settings are non-destructive and can be toggled while experimenting with chart behavior.

