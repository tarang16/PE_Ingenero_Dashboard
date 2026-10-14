# StatusChip

Deviation / alert status chips: a 1px border and text in the solid semantic colour on a tint of the same hue, `radius-control`, 0.8vmin padding, min-height 2.8vmin, fixed 12vmin width, uppercase.

**Consumer provides:** the status word; pick the class by meaning — `.deviation-new` / `.deviation-pending` (primary_yellow on primary_yellow_80), `.deviation-in-progress` (primary_blue, transparent), `.deviation-closed` (primary_blue on primary_blue_80), `.deviation-overdue` (primary_orange on secondary_orange_10).

- Always keep the word: colour alone does not carry status.
- `.blink_dot` (1s blink, infinite) is reserved for "needs attention" indicators.
- Known gap: yellow text on primary_yellow_80 is far below 4.5:1 — kept as in source.
