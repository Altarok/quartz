---
title: Roadmap
---

See [[changelog|Changelog]] for implemented features.

---

> Disclaimer: The mentioned frontmatter properties represent their default keys; you may have renamed them in your vault.

> The following list is not exhaustive. It contains only features confirmed for implementation. See [[#Unsorted ideas|below]] for a shorthand list of unsorted ideas.

## Features to come, by priority

- [x] Recurring events. - _CePeU and others_
- Keep calendar axis visible while scrolling over the chart.
- Keep toolbar visible while scrolling over the chart.
- Apply the calendar's optional `outputFormat` property to tooltip dates. - _CePeU_
- Place events into multiple groups. - _CePeU and others_
    - Change the frontmatter property `gantt-group` from `text` to `list`.
- Zoom:
    - Hide the smallest date format elements consecutively while zooming out.
    - Focus shown dates on more natural periods.
    - Set a safe default zoom and restore it when re-opening files.
- Calendars:
    - Add a manually configurable leap year rule. - _CePeU_
    - Add `YyWwDd` format. - _CePeU_
    - Remove duplicate calendar ID definition in calendar notes.
    - Rename `rule-based`.
- Highlight weekends.
- Manage rerender cooldown depending on the content of the changed file. - _CePeU_
- Add a setting for the time difference between calendar axis ticks. - _Charatzu_
- Make data exportable for use in other plugins. - _CePeU_

---

## Unsorted ideas

- In-plugin CSS themes.
- Calendars:
    - Add format without days.
    - Add seasons.
    - Add quarters.
    - Add format without years.
- Select groups and calendars on a per-chart basis (doable with base filters) in code-block charts. - _CePeU_
- Moon-only calendar. - _CePeU_
- Settings:
    - Join tooltip-related settings.
    - Use CLI to rename properties vault-wide when renaming Gantt properties.
- Add event symbol suffixes for chainable symbols. - _CePeU_
- Prevent duplicate events on the chart. - _CePeU_
- Add time of day to events, not only dates. - _CePeU_
- Add right-click context menu. Unsure what to add to it.
- Allow events to open a canvas or base when clicked. - _CePeU_
- Allow events to open other Gantt charts when clicked. - _CePeU_
- Allow differing day lengths across calendars.

