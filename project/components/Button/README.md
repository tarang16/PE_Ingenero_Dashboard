# Button

Uppercase, flat, square-cornered (`radius-control`, 0.3vmin) buttons in sabic_text_regular at 1.4vmin. Use `.btn_cyan` / `.btn_active` (primary_blue, hover primary_blue_hover) for the main action, `.btn_reset` (primary_gray_2) for reset/secondary, `.btn_disabled` for blocked actions (`cursor: not-allowed`), `.primary_blue_btn` for compact in-panel actions and `.refreshBtn` for refresh.

**Consumer provides:** a `<button>` with one class and a short uppercase-rendered label (write it in any case; CSS uppercases it). Icon-only buttons take an `<img>` of a brand SVG; recolour it white with `.icon_white` on blue grounds.

- Standard buttons are `min-width: 15vmin`, padding `0.9vmin 0`.
- Icon-only: `.backgroundBlueButtonMonitoring` / `.backgroundGrayButtonMonitoring` are 3.5 × 6vmin; `.backgroundBlueButton` is 3 × 3vmin with a 20% radius.
- No visible focus ring in the source (`button:focus-visible { outline: none }`).
- Known gap: white on primary_blue is 2.99:1, below 4.5:1 for 15px text.
