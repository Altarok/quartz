---
title: Plugin Settings
order: 5
---

# Plugin Settings

Global plugin settings allow you to configure default folders, set fallback colors, and manage custom calendar rules across your vault.

## General Configuration

- **Default Events Folder:** Specify the root folder where the plugin searches for event notes (e.g., `Events`). If left blank, the entire vault is scanned.
- **Search Sub-folders for Events:** Enable this toggle to recursively search all nested subdirectories inside the designated events folder.
- **Default Calendar Folder:** Define the folder path where custom calendar definitions are stored (e.g., `calendardefinitions`).
- **Search Sub-folders for Calendars:** Toggle whether subdirectories inside the calendar folder are scanned for YAML definitions.

## Calendar & Group Management

Manage active calendars, assign colors, and control lane order:

- **Active Calendars:** Add or remove calendars by their unique `id`. Toggle visibility to hide entire calendar systems without deleting definitions.
- **Default Group Options:** Pre-define groups to set default colors, toggle default visibility, and adjust lane sorting order on your charts.
- **Fallback Colors:** Set global default colors for timeline markers, bars, and icons when no specific event, group, or calendar color is defined.

> [!tip] Override Priority
> Settings act as vault-wide defaults. You can always override global colors, property names, or folder paths locally using specific code block parameters or Base view configurations.

## Property Names & Key Mappings

Customize the YAML frontmatter keys the plugin looks for in your Markdown notes:

- **Item Marker:** Default is `gantt-item`. Marks a note as an event target.
- **Start / End Dates:** Defaults are `gantt-start` and `gantt-end`.
- **Name & Group:** Defaults are `gantt-name` and `gantt-group`.
- **Calendar & Symbol:** Defaults are `gantt-calendar` and `gantt-symbol`.

*Renaming these properties in settings allows you to align the plugin with existing Dataview or frontmatter conventions in your vault.*


---
---

# Plugin Settings

## Data paths

![[Pasted image 20260905163026.png]]

### Source Paths

- **`eventPath`**: Folder to search for Gantt event definitions. Can be set to the vault root or a subfolder.
- **`eventPathSearchRecursive`**: Toggle to search `eventPath` recursively (include subfolders).
- **`calendarPath`**: Folder to search for calendar (calendar definition) Markdown files.
- **`calendarPathSearchRecursive`**: Toggle to search `calendarPath` recursively.

### Default Values

- **`defaultCalendar`**: Fallback calendar used when an event does not specify a calendar. Default: `gregorian`.
- **`fallbackColor`**: Default color used for events when no color is provided. Default: `#1565C0`.
- **`fallbackColorForIcons`**: Default icon color when an event has an icon but no icon color. Default: `#FF8800`.

## Calendars

![[Pasted image 20260905163148.png]]

## Groups

![[Pasted image 20260905163326.png]]

Two lists display the calendars and groups currently known to the plugin. Both lists function identically:

- **Calendar list**: Defines which calendars the plugin recognizes and how they appear.
- **Group list**: Defines which groups the plugin recognizes and how they appear.

## Advanced

![[Pasted image 20260905163410.png]]

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

### Frontmatter Properties

These settings let you adapt the plugin to use different frontmatter keys in your notes.

- **Gantt event marker**: Primary boolean frontmatter key that marks a file as containing Gantt events.
  Default: `gantt-item`.
- **Marker may be optional**: If enabled, the primary marker becomes optional (saves one property per
  file but reduces explicit control).
- **Calendar definition**: Frontmatter key used to identify a calendar definition file. Default:
  `gantt-calendar-definition`.
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

### Notes & Usage Tips

- Use `Calendars` to register calendar definitions (files that define non-Gregorian calendars). Calendar `id` values are
  used in frontmatter to map events to calendars.
- The `Default values` section allows you to set global fallbacks for color and calendar when individual events omit
  them.
- The `Groups` mechanism is useful to build lanes and logical separations for events (for example, locations, factions,
  or categories).
- Advanced UX settings are non-destructive and can be toggled while experimenting with chart behavior.

## Display and Controls

### Events
![[Pasted image 20260905163504.png]]

### Event overlay
![[Pasted image 20260905163646.png]]

### Zooming and Panning
![[Pasted image 20260905163723.png]]

### Gant chart
![[Pasted image 20260905163747.png]]

### Plugin
![[Pasted image 20260905163810.png]]


## Frontmatter Properties

![[Pasted image 20260905163928.png]]
