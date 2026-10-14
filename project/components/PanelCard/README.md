# PanelCard

The "SingleTitleCard" panel: white surface, soft gray elevation `shadow-card-gray` (0 0 5px 1px primary_gray_4), 1.3vmin side padding, a 3.5vmin header with an uppercase bold title over a primary_gray_4 rule, and a body that fills `calc(100% - 3.5vmin)`.

**Consumer provides:** the title, optional header actions (small buttons or `.pendingBtn` / `.completeBtn` chips) and the body content — a chart, table or legend. The card takes `height: calc(100% - 2vmin)` of its grid cell and a 1vmin margin.

- Add `.shadow_none` when nesting inside another elevated surface.
- Card corners are square in this variant; use `radius-card` only for KPI tiles.
