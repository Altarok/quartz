---
title: Event Icons
tags:
  - event-properties/optional
---

[< Back to event overview](events/)

---

![Showcase](images/showcase.png)

All events except `vertical-line` can be decorated with a colored SVG icon as shown above.
The frontmatter properties `gantt-displayIcon` and `gantt-displayIconColor` define and color the icon of your choice.

**Tips**:

- [lucide.dev](https://lucide.dev/) is a good source for icon names.
- Icon names are case-sensitive.
- Set a default icon color in [[plugin-settings#Events|Plugin Settings > Events]].

> [!example]+ Example icon definitions
> ```yaml
> ---
> gantt-displayIcon: heart
> gantt-displayIconColor: pink # CSS knows a lot of human-readable colors
> ---
> 
> ---
> gantt-displayIcon: plus
> gantt-displayIconColor: "#0f172a" # You can use hex-colors
> ---
> 
> ---
> gantt-displayIcon: settings # No icon color is fine
> ---
> ```

---

> [!info]- Property traits
> - Both properties are of type `text`; their usage is optional.
> - You can rename them to your liking, see [[plugin-settings#Event Frontmatter Properties|Plugin Settings > Event Frontmatter Properties]].
