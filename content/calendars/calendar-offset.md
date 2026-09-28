---
title: Calendar Offset
tags:
  - yaml
last-upated-plugin-version: 1.4.3
---

[< Back to calendar overview](calendars/)

---

This page discusses how calendars work together. 3 YAML properties are used for this kind of calculation:

- ´sharedOffset´ -> aligns where the calendar sits in time, _controls time ==math==_.
- ´startDay´ (optional) -> control when and if the calendar starts, _controls ==visual rendering== bounds_.
- ´endDay´ (optional) -> control when and if the calendar ends, _controls ==visual rendering== bounds_.

> [!tip]
> If you do not plan to use more than one calendar, just keep `sharedOffset` at `0` (zero) and omit the other two.

## Visual Example:

Scroll down for more in-depth explanation.

- Gregorian: Has no `startDay` or `endDay` set, so its timeline extends infinitely in both directions.
- Mayan Long Count: Has both `startDay` ({year: -3114, month: 8, day: 11}) and `endDay` (in the year 2012), drawing the calendar axis strictly within that window.
- French Republican: Has a `startDay` (in the year 1792) when the calendar was created, but no `endDay`, so it continues drawing forward into the future.
- Your dnd campaign might use The Dale Reckoning (DR) calendar, which anchors its global math epoch to Year 0 DR (`sharedOffset`). However, your campaign only takes place during a specific 5-year arc (1370 DR – 1375 DR). Setting `startDay` to 1370 and `endDay` to 1375 crops the rendered axis strictly to those active adventure years.

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 850 610" width="100%" style="background-color: #1e1e2e; font-family: -apple-system, BlinkMacSystemFont, sans-serif; border-radius: 8px; padding: 10px;">
  <defs>
    <marker id="arrow" markerWidth="6" markerHeight="6" refX="5" refY="3" orient="auto">
      <polygon points="0 0, 6 3, 0 6" fill="#89b4fa" />
    </marker>
    <marker id="arrow-french" markerWidth="6" markerHeight="6" refX="5" refY="3" orient="auto">
      <polygon points="0 0, 6 3, 0 6" fill="#a6e3a1" />
    </marker>
    <marker id="arrow-harptos" markerWidth="6" markerHeight="6" refX="5" refY="3" orient="auto">
      <polygon points="0 0, 6 3, 0 6" fill="#f9e2af" />
    </marker>
    <marker id="arrow-start" markerWidth="6" markerHeight="6" refX="1" refY="3" orient="auto">
      <polygon points="6 0, 0 3, 6 6" fill="#89b4fa" />
    </marker>
  </defs>
  <!-- Header -->
  <text x="30" y="40" fill="#cdd6f4" font-size="20px" font-weight="bold">Multi-Calendar Axis Bounds &amp; Alignment</text>
  <text x="30" y="62" fill="#a6adc8" font-size="13px">Demonstrating sharedOffset (Epoch Alignment) vs startDay / endDay (Axis Drawing Limits)</text>
  <!-- GLOBAL TIMELINE BASE -->
  <g transform="translate(30, 90)">
    <!-- Global Timeline Axis -->
    <line x1="50" y1="50" x2="780" y2="50" stroke="#45475a" stroke-width="2" stroke-dasharray="4" />
    <!-- Global Anchor Line -->
    <line x1="320" y1="20" x2="320" y2="460" stroke="#f38ba8" stroke-width="2" />
    <text x="320" y="15" fill="#f38ba8" font-size="12px" font-weight="600" text-anchor="middle">Gregorian / Global Day 0 Anchor</text>
    <!-- 1. GREGORIAN -->
    <g transform="translate(0, 60)">
      <text x="50" y="25" fill="#89b4fa" font-size="14px" font-weight="bold">1. Gregorian Calendar</text>
      <text x="50" y="43" fill="#a6adc8" font-size="11px">sharedOffset: 0 | startDay: none | endDay: none (Unbounded baseline)</text>
      <line x1="80" y1="65" x2="740" y2="65" stroke="#89b4fa" stroke-width="3" marker-start="url(#arrow-start)" marker-end="url(#arrow)" />
      <circle cx="320" cy="65" r="5" fill="#89b4fa" />
      <text x="320" y="85" fill="#cdd6f4" font-size="10px" text-anchor="middle">Year 0 / Epoch</text>
    </g>
    <!-- 2. MAYAN LONG COUNT -->
    <g transform="translate(0, 160)">
      <text x="50" y="25" fill="#fab387" font-size="14px" font-weight="bold">2. Mayan Long Count</text>
      <text x="50" y="43" fill="#a6adc8" font-size="11px">sharedOffset: -3114y | startDay: -3114y | endDay: +2012y (Offset &amp; bounds match)</text>
      <line x1="100" y1="65" x2="580" y2="65" stroke="#fab387" stroke-width="6" stroke-linecap="round" />
      <line x1="100" y1="53" x2="100" y2="77" stroke="#fab387" stroke-width="2" />
      <text x="100" y="90" fill="#fab387" font-size="11px" font-weight="bold" text-anchor="middle">startDay (-3114y)</text>
      <line x1="580" y1="53" x2="580" y2="77" stroke="#fab387" stroke-width="2" />
      <text x="580" y="90" fill="#fab387" font-size="11px" font-weight="bold" text-anchor="middle">endDay (+2012y)</text>
      <circle cx="320" cy="65" r="5" fill="#fab387" />
    </g>
    <!-- 3. FRENCH REPUBLICAN -->
    <g transform="translate(0, 270)">
      <text x="50" y="25" fill="#a6e3a1" font-size="14px" font-weight="bold">3. French Republican Calendar</text>
      <text x="50" y="43" fill="#a6adc8" font-size="11px">sharedOffset: +1792y | startDay: +1792y | endDay: none (Creation year = axis start)</text>
      <line x1="550" y1="65" x2="740" y2="65" stroke="#a6e3a1" stroke-width="3" marker-end="url(#arrow-french)" />
      <line x1="550" y1="53" x2="550" y2="77" stroke="#a6e3a1" stroke-width="2" />
      <text x="550" y="90" fill="#a6e3a1" font-size="11px" font-weight="bold" text-anchor="middle">startDay (+1792y)</text>
      <line x1="320" y1="65" x2="540" y2="65" stroke="#a6e3a1" stroke-width="1.5" stroke-dasharray="3" />
      <text x="435" y="58" fill="#a6e3a1" font-size="10px" text-anchor="middle">+1792y offset shift</text>
    </g>
    <!-- 4. HARPTOS / FORGOTTEN REALMS (CAMPAIGN BOUNDS) -->
    <g transform="translate(0, 380)">
      <text x="50" y="25" fill="#f9e2af" font-size="14px" font-weight="bold">4. Calendar of Harptos (D&amp;D Campaign Arc)</text>
      <text x="50" y="43" fill="#a6adc8" font-size="11px">sharedOffset: -1000y | startDay: 1370 DR | endDay: 1375 DR (Epoch != Campaign Axis Bounds)</text>
      <!-- Bounded campaign arc line (1370 DR to 1375 DR) shifted right -->
      <line x1="480" y1="65" x2="680" y2="65" stroke="#f9e2af" stroke-width="6" stroke-linecap="round" />
      <!-- Epoch Anchor dot (0 DR / Standing Stone) -->
      <circle cx="200" cy="65" r="5" fill="#f9e2af" />
      <text x="200" y="85" fill="#f9e2af" font-size="10px" text-anchor="middle">0 DR (Epoch Anchor)</text>
      <!-- startDay marker (1370 DR) -->
      <line x1="480" y1="53" x2="480" y2="77" stroke="#f9e2af" stroke-width="2" />
      <text x="480" y="90" fill="#f9e2af" font-size="11px" font-weight="bold" text-anchor="middle">startDay (1370 DR)</text>
      <!-- endDay marker (1375 DR) -->
      <line x1="680" y1="53" x2="680" y2="77" stroke="#f9e2af" stroke-width="2" />
      <text x="680" y="90" fill="#f9e2af" font-size="11px" font-weight="bold" text-anchor="middle">endDay (1375 DR)</text>
      <!-- Dotted distance between Epoch 0 DR and Campaign Start 1370 DR -->
      <line x1="205" y1="65" x2="475" y2="65" stroke="#f9e2af" stroke-width="1.5" stroke-dasharray="2" />
    </g>
  </g>
</svg>

## Property `sharedOffset`

Imagine having two calendars, each starting their respective timeline on the first day of their first month of their first year. How would the plug-in know how to place them next to each other?

This property is used to answer this question. it defines which day on an infinite timeline is the absolute day zero of each calendar.

### Real World Example

For this example, let's use Gregorian as anchor. This means the calendar has no offset.
Day One for Gregorian would be January 1st, 1 AD. Day Zero would be the day before.

Giving a second calendar, however defined, the same offset would mean that both Day One instances meet each other on the timeline.

Giving a third calendar the offset -15000 means that its Day One is 15000 days _before_ Gregorian's Day One.

- Giving a second calendar the same `sharedOffset` would mean their respective starting days are the same.
- Shifting a second calendar's `sharedOffset` by +-X would shift its respective starting day by the same amount.

## Properties 'startDay' and 'endDay'

These properties define if and when a calendar starts and ends in time. Both are optional. They define a single day in time, not a year.

- Omitting both creates a calendar which extends infinitely in both directions.
- Adding `startDay` creates a lower bound for the calendar.
- Adding `endDay` creates an upper bound for the calendar.

## Format

All 3 of these properties share the same format:

```Typescript
number | {year: number, month: number, day: number}
```

When using only a `number`, it defines days - not years!
The alternative would be a combination of `year`, `month`, and `day`. These values represent Gregorian dates.

### Real Calculation Example

The Mayan calendar started August 9th, 3114 BC. All of the following 3 examples would accomplish this result.

```YAML
sharedOffset: {year: -3114, month: 8, day: 11}

sharedOffset: -1137507

sharedOffset:
  year: -3114
  month: 8
  day: 11
```
