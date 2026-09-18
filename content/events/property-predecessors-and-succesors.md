---
title: Event predecessors & successors
tags:
  - event-properties/optional
---

---

Events on Gantt charts or any other type of calendar may have predecessors and successors.
The event properties 'gantt-predecessors' & 'gantt-successors' are meant to connect events on a linear basis.

The plugin highlights incoming links from the specified events. Hovering over or selecting the event visually traces its upstream dependencies.
![Aragorn's coronation](../images/predecessors-successors-example.png)

Both properties are lists containing links to other notes.
If given and activated in settings, ...

- Hovering an event with predecessors with your mouse will show arrows from the predecessors to the left edge of event
- Hovering an event with successors with your mouse will show arrows from the event to the left edges of its successors

> [!example] Event example: "Aragorn's coronation"
> ```
> ---
> gantt-predecessors:
>   - "[[Destruction of the One Ring & Fall of Sauron]]"
>   - "[[Battle of the Morannon (Black Gate)]]"
> gantt-successors:
>   - "[[Wedding of Aragorn & Arwen]]"
> ---
> ```

> [!tip]
> Property type is `list`, its usage is optional.
> You can rename it to you liking, see [[plugin-settings#Property Names & Key Mappings|Plugin Settings > Property Names & Key Mappings]]
>
> Troubleshooting:


