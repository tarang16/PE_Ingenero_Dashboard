# Table

The plain HTML table (`table.module.scss`) for simple custom tables: sticky 5.5vmin header on primary_blue_bg with uppercase sabic_text_bold 1.2vmin labels and a 1px divider between header cells; 5.5vmin body rows, cell padding 1vmin 0.5vmin, 1.3vmin uppercase text, `primary_gray_4` row rules.

**Consumer provides:** column headers, row data and, optionally, a row-action icon per row (`.rowAction`, fades in on row hover over 0.5s).

- Highlight a row or cell with `.HighlightRow` / `.HighlightCell` (primary_blue_60).
- Outer header corners take `radius-3px`.
- For sorting, filtering or virtualisation use **DataGrid** instead.
