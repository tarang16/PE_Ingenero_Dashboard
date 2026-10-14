PE Dashboard is SABIC's Plant Efficiency monitoring product: a dense, data-first dashboard that fills a fixed 16:9 screen. Build every new page so it scales as one picture, speaks in uppercase structural labels and colours everything from the SABIC palette below — never a new hex value.

## Units: build in vmin

- Size everything — font sizes, padding, margins, gaps, widths, heights, radii, icon sizes — in **`vmin`**. The app sets `body { aspect-ratio: 16/9 }` and has **no media queries**; the whole UI scales together.
- The tokens in this system are recorded in px at the 1920 × 1080 reference canvas (**1vmin = 10.8px**). Every token's usage note gives its vmin value: write `1.4vmin`, not `15.12px`.
- Use px only for things that must not scale: `hairline` (1px) borders and the small fixed radii (`radius-2px`, `radius-3px`, `radius-4px`).
- Page regions are percentages of the canvas height (`layout-*` tokens), because they must sum to 100%.
- This is not a responsive web app: do not add breakpoints or assume it reflows on narrow viewports.

## Content fundamentals

- **Structural UI labels are UPPERCASE**: table headers, table cells in plain tables, tabs, buttons, status chips, panel-card titles, tooltips (`TRENDS`, `OVERDUE SINCE (DAYS)`, `VIEW DETAILS`). Free text and content stay in sentence case.
- Breadcrumbs are capitalised (`Home › Affiliates › Plant list`).
- Vocabulary comes from plant operations: *plants, systems, affiliates, alerts, deviations, production opportunity, process / energy / environment efficiency, CO₂ reduction, case details, tags, pipelines, health check*. Use these words, not generic ones.
- Units sit beside values in parentheses or after the number: `PRODUCTION OPPORTUNITY (MT/DAY)`, `PROCESS EFFICIENCY (%)`.
- Dates read `30-Oct-2024`; range presets are `1W 1M 2M 3M 6M 1Y`.
- Statuses are single words: *New, Pending, In progress, Closed, Overdue, Active, Implemented, Rejected, Auto-closed*.
- No emoji. Icons are the brand SVGs in the asset groups.

## Colour

- Text is `primary_gray` (#4d4d4d) on `primary_white`, `primary_bg` or `primary_gray_bg`. `primary_black` is for maximum contrast and the dark tooltip only.
- `primary_blue` (#009fdf) is the one action and brand colour: primary buttons, active nav, active tab text, active page, links, breadcrumbs, checked controls, focus borders, and the *healthy* status. Hover is `primary_blue_hover`.
- `primary_blue_bg` (#eaf9ff) is the primary tint: table and grid headers, sidebar nav items, header icon chips, inactive triangle tabs.
- Page ground is `primary_gray_bg`; cards are `primary_white`. Borders use `primary_gray_3`; dividers, row rules and hover washes use `primary_gray_4`.
- `primary_dark_blue` (#041e41) is the deep navy for brand moments; `header_gradient_start` (#0047bb) only opens the header hairline.
- Chart series and highlights use the alpha tints (`primary_blue_20…80`, `primary_yellow_20…80`, `primary_orange_60`, `primary_green_60`, `primary_gray_12`). `primary_blue_60` is also the table row/cell highlight.

### Status colours

| Meaning | Colour | Pattern |
|---|---|---|
| Healthy / OK / primary | `primary_blue` | `status-healthy`, active states |
| Success / complete | `primary_green` (+ `secondary_green` border, `secondary_green_Light` bg) | `completeBtn`, success toast |
| Warning / pending / new | `primary_yellow` on `primary_yellow_80` | `deviation-new`, `deviation-pending` |
| Alert / error / overdue | `primary_orange` on `secondary_orange_10` | `deviation-overdue`, `pendingBtn`, error toast |
| In progress / closed | `primary_blue` on transparent / `primary_blue_80` | `deviation-in-progress`, `deviation-closed` |
| Disabled / neutral | `primary_gray_2` | `btn_disabled`, `btn_inactive` |

Status chips are always **1px border + tint fill + solid text in the same hue**, and always carry the word.

### Contrast — known gaps kept from the source

These source pairs miss WCAG 4.5:1 for small text; they are kept exact. Prefer them for large or bold text and marks, and do not spread them further:

- White on `primary_blue` and `primary_blue` on white: 2.99:1 (buttons, links).
- `primary_orange` on white: 3.81:1. `primary_gray_2` on white / white on it: 3.0:1.
- `primary_yellow` text on `primary_yellow_80` chips: well under 3:1 — the word, not the colour, must carry the meaning.
- `primary_green` on white is 4.89:1 and passes.

## Typography

- Brand faces are the SABIC webfonts, one family name per weight: `sabic_text_light` (300), `sabic_text_regular` (400), `sabic_text_bold` (700), and `sabic_headline_light`, `sabic_headline_regular`, `sabic_headline_bold`. Fallback is `serif` — a deliberate quirk of the codebase; keep it.
- Global default: `font-family: 'sabic_text_regular', serif; font-weight: 500;` in `primary_gray`.
- The scale runs `text-9` → `text-30` (0.9–3.0vmin), each in `-light`, `-regular`, `-bold`, all at line-height 1.2. Pick weight by family, not by `font-weight`.
- Defaults: body, buttons and tabs `text-14-regular`; table headers `text-12-bold` uppercase; table cells `text-13-regular`; page header `text-15`; card titles `text-18-bold`; KPI values `text-20`–`text-24-bold`; hero / empty states `text-30` or `sabic_headline_bold`.
- Line-height helpers exist (`1`, `1.2`, `1.3`) and letter-spacing `0.05vmin` / `0.09vmin` for tight caps.

## Spacing

Snap to the vmin scale `space-0_3 … space-6` (0.3, 0.4, 0.5 … 1, 1.2, 1.5, 2, 2.5, 3, 4, 5, 6vmin):

- 0.3–0.8vmin between tightly related things (icon + label, chip padding).
- 1–2vmin inside components (card body, modal body, cell padding). Standard flex gap 1.5vmin.
- 2–5vmin between cards, sections and page edges.

## Elevation, borders and radii

- Default elevation is `boxShadow_card` (0 0 6px rgba(0,0,0,.15)) for cards, tables, tab panels, tooltips and menus. KPI tiles use `boxShadow_kpi`; status/legend panels the softer `shadow-card-gray`; popovers `shadow-card-strong` or `shadow-menu`; the sidebar alone uses `sidebar_boxshadow`. Inline content and table rows are flat.
- Radii: `radius-control` (0.3vmin) for controls and inputs, `radius-card` (0.8vmin) for elevated KPI cards, `radius-round` for avatars and dots, `radius-0` for Bootstrap tabs, pagination and search buttons. Panels and modals are near-square (`radius-2px`).
- Borders are 1px `primary_gray_3`; focus keeps the same border — no glow. The only blue borders are the active date field (2px), the toggle and the draggable modal.

## Layout

The page is one fixed vertical stack (see **AppShell**): header 10.5% → blue header hairline 0.4% → content 85% (19vmin sidebar + main) → yellow footer hairline 0.4% → footer. Main is a 5vmin title/filter bar over the card grid. The **blue hairline on top and yellow hairline at the bottom** are the brand signature: keep them on every new page.

## Motion

Minimal and purposeful. Hover colour changes are instant or `0.3s ease-in-out`; row actions fade in over 0.5s; submenus cross-fade in 0.2s; tab chips widen over 0.5s. Infinite loops only for things that need attention: the 1s blinking alert dot and the 2s toast progress line.

## Overlays (z-index bands)

Base content 0–20 (`z-sticky-header`, `z-status-banner`); sidebar submenu / draggable content around 1000; Bootstrap modals 1040–1080, +10 per nested modal; pickers, select menus and loading overlays that must sit above an open modal 9999+.

## Iconography

- Icons are flat single-colour SVGs, recoloured at runtime with CSS filter chains rather than shipping colour variants:
  - white: `filter: brightness(0) invert(1)` (`.icon_white`)
  - brand blue: `.blueFilter` — `brightness(0) saturate(100%) invert(49%) sepia(74%) saturate(2003%) hue-rotate(163deg) brightness(90%) contrast(103%)`
  - brand orange: `.orangeFilter`
  - disabled: `filter: grayscale(1)`
- Sizes: 1.4–2vmin inline and in tables, 2–2.6vmin in the header and toolbars, 3.5–4.5vmin for feature, KPI and notification icons.
- A small `icomoon` icon font (`.icon-trend`, glyph U+E900) is loaded as the `icon` family; its map is `assets/IconFont/selection.json`.
- Asset groups: **Logos**, **Header**, **Navigation** (sidebar), **Common** (actions, chart types, checks, warnings, trend keys), **KPIs** (landing and system top KPI icons, home tooltips), **Status** (alert states), **Affiliates** (affiliate marks by code), **Tables**, **FileTypes**, **IconsV2** (the newer icon set), **Loaders**, **Maps**, **Screens** (product screenshots for reference).
- Prefer the **IconsV2** version of an icon when both sets have one.

## Imagery

No photography. Visual content is data — charts (amCharts), tables, maps of the regions (Americas, EU, MEA, world) and the KPI illustrations. The **Screens** group shows real product pages to match against.

## Libraries

React with Bootstrap 5 (`react-bootstrap`), re-themed with these tokens; ag-Grid (`ag-theme-alpine`) for sortable/filterable grids; react-select, react-datepicker and react-tooltip, all re-skinned as in the components. Component classes are in `components/bundle.css`; the source of truth is `src/config/scss/` and `src/index.scss` in the product repo.


---

## Consuming this system (generated — do not edit)

Every path named below is under `project/` in this design system: read `project/api/tokens.md`, not `api/tokens.md`.

23 components are documented without a runnable `components/bundle.js`: read each component’s card, and its README where it has one (`components/<Comp>/README.md`), and build to those guidelines. Tokens: the values are on `api/tokens.md`; a Slides deck or Design canvas also takes `tokens.json` by file path.

Fonts: one file per family is enough (below: the upright face nearest regular weight; bold and italic synthesize). Fetch it as the fetch column says (Artifact tool `read`, that id or path as `path`), upload it as an asset (`publish`, `file_path`, `asset:true`) and declare it with an `@font-face { font-family: "<family>"; src: url(<uploaded>) }` rule.

- **Slides deck:** for each family you use in the deck (`faces` holds at most the number of typefaces Slides’ `deck-files.md` gives), install its file with the system and name the path it lands on as that family’s `src` in `project/deck.json` `faces`, under the key in the Slides column. A deck takes a font as a file only under the rule in Slides’ `fonts.md` (no space or leading underscore in its path, for two): any other font, or one kept by id, is uploaded as `fonts.md` says.

| family | file | fetch | CSS | Slides `faces` key |
| --- | --- | --- | --- | --- |
| sabic_text_light | `fonts/sabictypefacetext_lt-webfont.woff2` (weight 300) | `read` the file with `project/` in front | `var(--font-text-light)` | `sabic-text-light` |
| sabic_text_regular | `fonts/sabictypefacetext_rg-webfont.woff2` (weight 400) | `read` the file with `project/` in front | `var(--font-text)` | `sabic-text-regular` |
| sabic_text_bold | `fonts/sabictypefacetext_bd-webfont.woff2` (weight 700) | `read` the file with `project/` in front | `var(--font-text-bold)` | `sabic-text-bold` |
| sabic_headline_light | `fonts/sabictypefaceheadline_lt-webfont.woff2` (weight 400) | `read` the file with `project/` in front | `var(--font-headline-light)` | `sabic-headline-light` |
| sabic_headline_regular | `fonts/sabictypefaceheadline_rg-webfont.woff2` (weight 400) | `read` the file with `project/` in front | `var(--font-headline)` | `sabic-headline-regular` |
| sabic_headline_bold | `fonts/sabictypefaceheadline_bd-webfont.woff2` (weight 400) | `read` the file with `project/` in front | `var(--font-headline-bold)` | `sabic-headline-bold` |
| icomoon | `fonts/icomoon.woff` (weight 400) | `read` the file with `project/` in front | `var(--font-icon)` | `icomoon` |
| sabictypefaceheadline bd | `fonts/sabictypefaceheadline_bd-webfont.woff` (weight 400) | `read` the file with `project/` in front |  | `sabictypefaceheadline-bd` |
| sabictypefaceheadline lt | `fonts/sabictypefaceheadline_lt-webfont.woff` (weight 400) | `read f9b42b13e16830e67162f86b79e0d6e3` |  | `sabictypefaceheadline-lt` |
| sabictypefaceheadline rg | `fonts/sabictypefaceheadline_rg-webfont.woff` (weight 400) | `read 4ce573a26a51f18f2337e1b04353b9f8` |  | `sabictypefaceheadline-rg` |
| sabictypefacetext bd | `fonts/sabictypefacetext_bd-webfont.woff` (weight 400) | `read ac16b1e7bad5446c417498bc274c671d` |  | `sabictypefacetext-bd` |
| sabictypefacetext lt | `fonts/sabictypefacetext_lt-webfont.woff` (weight 400) | `read 576e186c391bf1306285907a6244c771` |  | `sabictypefacetext-lt` |
| sabictypefacetext rg | `fonts/sabictypefacetext_rg-webfont.woff` (weight 400) | `read f9840ad47a5ea9cf51c34208f7c93b30` |  | `sabictypefacetext-rg` |

**Read, per thing:** a component’s props, parts and examples: `api/components/<Comp>.md`; token values: `api/tokens.md`; stored assets and their paths: `api/assets/<Group>.md`. After this README, fetch the cards and fonts you need in ONE message as parallel calls — none depends on another.

**Two rules.** Before you use a thing — a component, a token group, an icon, an asset — read its card from the index below; a value you did not read from a card is a guess. `tokens.json`, `manifest.json` and `design-system.json` are sources for tools: hand them over. `components/<Comp>/README.md` and `assets/<Group>/README.md` are the long-form second read a card links to; `SKILL.md` and `artifact-type/` beside them are authoring guidance, not needed to consume the system.

## Index (generated — do not edit)

**Tokens**

- `api/tokens.md` — Every token: palette, type, spacing, radius, shadow, z-index, layout. (25.2k)

**Icons and assets**

- `api/assets/Logos.md` — 2 files, by asset id. (1.3k)
- `api/assets/KPIs.md` — 20 files, by asset id. (2.8k)
- `api/assets/IconsV2.md` — 37 files, by asset id. (4.2k)
- `api/assets/Navigation.md` — 20 files, by asset id. (2.6k)
- `api/assets/Header.md` — 11 files, by asset id. (1.8k)
- `api/assets/Common.md` — 42 files, by asset id. (4.7k)
- `api/assets/Status.md` — 14 files, by asset id. (2.0k)
- `api/assets/Tables.md` — 11 files, by asset id. (1.8k)
- `api/assets/FileTypes.md` — 10 files, by asset id. (1.6k)
- `api/assets/Affiliates.md` — 11 files, by asset id. (1.6k)
- `api/assets/Loaders.md` — 12 files, by asset id. (2.0k)
- `api/assets/Maps.md` — 4 files, by asset id. (1.2k)
- `api/assets/Screens.md` — 51 files, by asset id. (5.5k)

**Components** (`api/components/<Comp>.md`, 23)

- **Layout**: `AppShell` — The fixed 16:9 page frame (RootLayout.module.scss): header 10.5% → blue header hairline 0.4% → content 85% (19vmin sidebar + main) → yellow footer hairline 0.4…
- **Navigation**: `Breadcrumb` — Breadcrumb trail: items in primary_blue, capitalised, no underline; a 2.1vmin separator icon (breadcrumb_separator.svg) with 0.6vmin side margins; the last ite… · `Header` — The brand bar (10.5% of the canvas): product lockup on the left, utility icons on primary_blue_bg chips and the SABIC logo on the right, closed by the header h… · `Pagination` — Bootstrap pagination, squared off: .page-link radius-0, min-width 5vmin; active page primary_blue with white text; disabled pages cursor: not-allowed · `Sidebar` — The fixed 19vmin left navigation: white with sidebar_boxshadow, 1.5vmin top padding · `Tabs` — Standard Bootstrap tabs: flat, 6vmin tall, white, no bottom border; labels uppercase 1.4vmin primary_gray; hover and active get primary_gray_4 background and p… · `TriangleTabs` — The distinctive trapezoid "pill" tabs (.commonTriangleTabs): clip-path: polygon(2.5vmin 0, calc(100% - 2.5vmin) 0, 100% 100%, 0 100%), top corners radius-pill…
- **Actions**: `Button` — Uppercase, flat, square-cornered (radius-control, 0.3vmin) buttons in sabic_text_regular at 1.4vmin
- **Forms**: `Checkbox` — Checkboxes and radios: 2 × 2vmin, primary_gray_3 border, radius-control (radios radius-round); checked fills primary_blue with a white tick · `DatePicker` — react-datepicker inputs styled like TextInput (1px primary_gray_3, radius-control); the field being edited gets a 2px primary_blue border · `Select` — react-select, re-skinned (react-select-modifyDetails / react-selectTimezone prefixes): control with 1px primary_gray_3 border and radius-control, no focus glow… · `TextInput` — Text inputs and textareas: 1px primary_gray_3 border, radius-control; focus keeps the same border — no blue glow, no outline · `Toggle` — .switch-friend: 2px primary_blue track border, radius-switch (10px); the handle is outlined primary_blue when off and turns primary_yellow when on
- **Data**: `DataGrid` — ag-Grid (ag-theme-alpine) re-skinned to the brand: wrapper with boxShadow_card and radius-control; header on primary_blue_bg in sabic_text_bold 1.18vmin weight… · `Scrollbar` — Custom thin scrollbar on every scroll container (.pe_scroll): width 0.6vmin, horizontal height 3px, track #f1f1f1, thumb primary_gray_2 → primary_gray on hover · `Table` — The plain HTML table (table.module.scss) for simple custom tables: sticky 5.5vmin header on primary_blue_bg with uppercase sabic_text_bold 1.2vmin labels and a…
- **Cards**: `KpiCard` — Top-of-page KPI tile: a coloured brand KPI icon, an uppercase label and a large bold value with its unit · `PanelCard` — The "SingleTitleCard" panel: white surface, soft gray elevation shadow-card-gray (0 0 5px 1px primary_gray_4), 1.3vmin side padding, a 3.5vmin header with an u…
- **Feedback**: `Loader` — The product's animated SVG loaders, inlined so they animate (the copies in the Loaders asset group are static frames: the asset store strips SVG animation) · `Toast` — .custom-toast: white, 1px border in the semantic colour and a 2px animated progress underline (width 100% → 0% over 2s, looping). .custom-toast-success uses pr…
- **Overlays**: `Modal` — Bootstrap modal, re-skinned: vertically centred, radius-2px dialog with no border; 10px header with a primary_gray_3 rule and a gray close icon (2vmin in a 2.8… · `Tooltip` — react-tooltip, dark by default (primary_black with white text), radius-tooltip (0.2rem), padding 1.4vmin 2vmin 1.1vmin, uppercase 1.4vmin text. .lightTooltipBa…
- **Status**: `StatusChip` — Deviation / alert status chips: a 1px border and text in the solid semantic colour on a tint of the same hue, radius-control, 0.8vmin padding, min-height 2.8vm…
