---
title: Code Block Configuration
tags:
  - codeblock
last-upated-plugin-version: 1.8.0
---

[< Back to overview](../)

> [!tip] This page handles Gantt chart creation with code blocks. If you prefer the more sophisticated Bases, Obsidian's native way of doing things, skip this page.

## MOC

- [[#What is a Code Block?]]
- [[#How to configure a Code Block?]]
- [[#Parameters]]
    - [[#Data Sources]]
    - [[#Initial View Bounds]]
    - [[#Layout]]

---

## What is a Code Block?

If you prefer embedding a chart directly inside a Markdown note without using Obsidian Bases, you can insert a `gantt-this` code block.

````md
```gantt-this
```
````

There a few parameters available. Every parameter inside the code block is **optional**. When omitted, the chart falls back to your global plugin settings.

---

## How to configure a Code Block?

Parameters are written as `key: value` pairs, one per line. Blank lines and lines without a `:` are ignored.

````md
```gantt-this
eventPath: local
eventPathSearchRecursive: true
calendarPath: Calendars
calendarPathSearchRecursive: false
calendarForBounds: gregorian
lowerBoundDate: 2020-01-01
upperBoundDate: 2025-12-31
width: 800px
```
````

> [!tip] You can generate this code block interactively using the **Open code block creator** ribbon icon or command.

---

## Parameters

#### Data Sources

These parameters control where the plugin searches for data to render on your chart.

- **`eventPath`** *(string, default: global Event path setting)*: Folder path containing your event notes.
  Supports two special keywords:
    - `root` — searches from the vault root (`/`).
    - `local` — searches the folder of the currently open note.
- **`eventPathSearchRecursive`** *(boolean, default: global setting)*: Set to `true` to include subfolders of `eventPath`, or `false` to search only the top-level folder.
- **`calendarPath`** *(string, default: global Calendar path setting)*: Folder path containing your calendar definition notes. Also supports `root` and `local`.
- **`calendarPathSearchRecursive`** *(boolean, default: global setting)*: Set to `true` to include subfolders of `calendarPath`, or `false` to search only the top-level folder.

#### Initial View Bounds

These parameters control the visible date range when the chart first loads. You can still zoom and pan freely afterward, and clicking **Reset view** returns to these bounds.

- **`calendarForBounds`** *(string, default: global Default calendar setting)*: ID of the calendar used to parse `lowerBoundDate` and `upperBoundDate`.
- **`lowerBoundDate`** *(string)*: Earliest date shown in the initial viewport (uses the date format of `calendarForBounds`, including relative dates like `today-30` or positional shortcuts).
- **`upperBoundDate`** *(string)*: Latest date shown in the initial viewport. Can be used on its own or combined with `lowerBoundDate`.

#### Layout

- **`width`** *(string)*: Restricts the maximum width of the rendered chart container. Accepts pixel or percentage values matching `^\d+(px|%)$` (for example, `600px` or `80%`).

---

> [!info]- Property traits
> - All parameters in a `gantt-this` code block are **optional**; an empty code block renders using your plugin defaults.
> - Boolean values match case-insensitively (`true` enables the option; any other value evaluates to `false`).
> - Path keywords `root` and `local` are case-insensitive.
