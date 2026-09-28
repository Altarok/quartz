---
title: Calendar Moons
tags:
  - yaml/optional
last-upated-plugin-version: 1.4.3
---

[< Back to calendar overview](calendars/)

---

![Showcase with 5 moons in a single calendar](images/many-moons-example.png)

The `moons` property inside a [[calendars/|Calendar Configuration]] defines celestial bodies orbiting your world. You can configure multiple moons per calendar, each with its own cycle length, phase alignment offset, and custom rendering color.
Moons get rendered at 4 different phases:

- New Moon
- Crescent Half Moon
- Full Moon
- Waning Half Moon

These appear on top of their respective calendar's axis. The more you zoom out, the more moons disappear in favor of performance and clarity.

## Configuration

The `moons` property contains a list of moons. Each moon has the properties `offset`, `cycle` and `color`.

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 820 280" width="100%" style="background-color: #1e1e1e; font-family: monospace; border-radius: 8px;">
  <!-- Grid / Background track -->
  <line x1="40" y1="180" x2="780" y2="180" stroke="#444" stroke-width="2" />
  <!-- Day zero mark -->
  <line x1="100" y1="120" x2="100" y2="200" stroke="#ff4444" stroke-width="2" stroke-dasharray="4,4" />
  <text x="100" y="220" fill="#ff6666" font-size="13" text-anchor="middle" font-weight="bold">Day 0</text>
  <text x="100" y="238" fill="#888" font-size="11" text-anchor="middle">(Epoch Origin)</text>
  <!-- First Full Moon (Day 0 + Offset) -->
  <line x1="260" y1="140" x2="260" y2="200" stroke="#ffd700" stroke-width="1.5" stroke-dasharray="2,2" />
  <circle cx="260" cy="180" r="12" fill="#ffd700" />
  <text x="260" y="220" fill="#ffd700" font-size="13" text-anchor="middle" font-weight="bold">Day 10</text>
  <text x="260" y="238" fill="#aaa" font-size="11" text-anchor="middle">1st Full Moon</text>
  <!-- Offset Arrow -->
  <g>
    <line x1="100" y1="150" x2="260" y2="150" stroke="#ffaa00" stroke-width="2" />
    <polygon points="260,150 250,145 250,155" fill="#ffaa00" />
    <text x="180" y="142" fill="#ffaa00" font-size="12" text-anchor="middle">offset = 10 days</text>
  </g>
  <!-- Second Full Moon (Day 10 + Cycle) -->
  <line x1="660" y1="140" x2="660" y2="200" stroke="#ffd700" stroke-width="1.5" stroke-dasharray="2,2" />
  <circle cx="660" cy="180" r="12" fill="#ffd700" />
  <text x="660" y="220" fill="#ffd700" font-size="13" text-anchor="middle" font-weight="bold">Day 40</text>
  <text x="660" y="238" fill="#aaa" font-size="11" text-anchor="middle">2nd Full Moon</text>
  <!-- Cycle Arrow -->
  <g>
    <line x1="260" y1="80" x2="660" y2="80" stroke="#4bc0c0" stroke-width="2" />
    <polygon points="260,80 270,75 270,85" fill="#4bc0c0" />
    <polygon points="660,80 650,75 650,85" fill="#4bc0c0" />
    <text x="460" y="72" fill="#4bc0c0" font-size="13" text-anchor="middle" font-weight="bold">cycle = 30 days</text>
    <text x="460" y="95" fill="#888" font-size="11" text-anchor="middle">(Full Moon to Full Moon Distance)</text>
  </g>
  <!-- Timeline ticks -->
  <line x1="180" y1="175" x2="180" y2="185" stroke="#666" stroke-width="1" />
  <line x1="340" y1="175" x2="340" y2="185" stroke="#666" stroke-width="1" />
  <line x1="420" y1="175" x2="420" y2="185" stroke="#666" stroke-width="1" />
  <line x1="500" y1="175" x2="500" y2="185" stroke="#666" stroke-width="1" />
  <line x1="580" y1="175" x2="580" y2="185" stroke="#666" stroke-width="1" />
  <line x1="740" y1="175" x2="740" y2="185" stroke="#666" stroke-width="1" />
</svg>

| Property | Type                | Default        | Short Description                               |
|:---------|:--------------------|:---------------|:------------------------------------------------|
| `cycle`  | `number` (required) | n/a            | Days between two consecutive full moons.        |
| `offset` | `number` (required) | n/a            | Shift in days relative to calendar's **Day 0**. |
| `color`  | `string` (optional) | `currentColor` | Hex color or CSS color name.                    |

The `cycle` determines the period of the synodic month. The `offset` aligns the phase sequence to your timeline: an `offset` of `0` means a full moon occurs precisely on **Day 0**.

## Example Configuration

Below is the moon part of a [[calendars/|Calendar Configuration]] example featuring a primary moon, a smaller, faster secondary moon, and a legendary blood-red moon:

```yaml
moons:
  - cycle: 28.3 # Primary Silver Moon (default notation)
    offset: 10
    color: '#ffd700'
  - cycle: 12.72 # Secondary Moon (without color)
    offset: 2.5
  - {cycle: 3000, offset: 2123, color: crimson} # Crimson moon (in short notation)
```
