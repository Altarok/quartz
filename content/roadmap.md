---
title: Roadmap
---

See [[changelog|Changelog]] for implemented features.

---

> Disclaimer: The mentioned frontmatter properties represent their default keys; you may have renamed them in your vault.

> The following list is not exhaustive. It contains only features confirmed for implementation. See [[#Unsorted ideas|below]] for a shorthand list of unsorted ideas.

## Features to come, by priority

- [+] Recurring events. - _CePeU and others_
- [5] Keep calendar axis visible while scrolling over the chart.
- [4] Keep toolbar visible while scrolling over the chart.
- [4] Apply the calendar's optional `outputFormat` property to tooltip dates. - _CePeU_
- [3] Place events into multiple groups. - _CePeU and others_
    - Change the frontmatter property `gantt-group` from `text` to `list`.
- Zoom:
    - [4] Hide the smallest date elements consecutively while zooming out.
    - [3] Focus shown dates on more natural periods.
    - [2] Store default zoom and restore it when re-opening files.
- Calendars:
    - [4] Add a manually configurable leap year rule. - _CePeU_
    - [2] Add `YyWwDd` format. - _CePeU_
    - Remove duplicate calendar ID definition in calendar notes.
    - [1] Rename `rule-based` to `year-based`.
- [1] Highlight weekends. Gregorian only.
- [1] Manage rerender cooldown depending on the content of the changed file. - _CePeU_
- [3] Add a setting for the time difference between calendar axis ticks. - _Charatzu_


---

## Unsorted ideas

- [?] Make data exportable for use in other plugins. Task unclear, data iab just your notes.- _CePeU_
- [1] In-plugin CSS themes.
- Calendars:
    - [+] Add format without days.
    - [0] Add seasons.
    - [0] Add quarters.
    - [0] Add format without years.
- [1] Select groups and calendars on a per-chart basis in _code-block_ charts. - _CePeU_
  - Bases can already do that.
- [?] Moon-only calendar. - _CePeU_
- Settings:
    - [1] Join tooltip-related settings.
    - [0] Use CLI to rename properties vault-wide when renaming Gantt properties.
- [0] Add chainable symbols. - _CePeU_
- [0] Prevent duplicate events on the chart. - _CePeU_
- [0] Add time of day to events, not only dates. - _CePeU_
- [?] Add right-click context menu. Unsure what to add to it.
- [0] Allow events to open a canvas or base when clicked. - _CePeU_
- [0] Allow events to open other Gantt charts when clicked. - _CePeU_
- Allow differing day lengths across calendars.

