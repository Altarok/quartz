---
title: Event icons
tags:
  - frontmatter/optional
---

[< Back to event overview](events/index)

---

![Showcase](images/showcase.png)

All events except `vertical-line` can be decorated with an icon as shown above.
Icons can be colored.
The frontmatter properties `'gantt-displayIcon'` & `'gantt-displayIconColor'` are meant to define the icon of your choice.

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
> - Both property's type is `text`, their usage is optional.
> - You can rename them to your liking, see [[plugin-settings#Property Names & Key Mappings|Plugin Settings > Property Names & Key Mappings]]
