# DataGrid

ag-Grid (`ag-theme-alpine`) re-skinned to the brand: wrapper with `boxShadow_card` and `radius-control`; header on primary_blue_bg in sabic_text_bold 1.18vmin weight 600; cells 1.3vmin primary_gray, vertically centred, 0.5vmin side padding; 0.1vmin primary_gray_4 row borders. Menus and filters: white, primary_gray_3 borders, `radius-control` inputs.

**Consumer provides:** ag-Grid column definitions and row data; status columns render a cell with `.status-healthy` / `.status-alert` / `.status-warning` and a `.square` swatch.

- Status mapping: healthy → primary_blue, alert → primary_orange, warning → primary_yellow swatch (text bold).
- The preview recreates the skin with plain markup; in product it is the ag-Grid theme override in `index.scss`.
