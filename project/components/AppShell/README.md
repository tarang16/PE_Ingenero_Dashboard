# AppShell

The fixed 16:9 page frame (`RootLayout.module.scss`): header 10.5% → blue header hairline 0.4% → content 85% (19vmin sidebar + main) → yellow footer hairline 0.4% → footer strip. Main splits into a 5vmin `topContainer` (page title, filters) and a `bottomContainer` holding the cards.

**Consumer provides:** header contents, sidebar items, the page title and the card grid.

- `body { aspect-ratio: 16/9 }`; there are no media queries — everything scales in vmin.
- Fill `bottomContainer` with KPI tiles on top and panel cards below on the primary_gray_bg ground.
