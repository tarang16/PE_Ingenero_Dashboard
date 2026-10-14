# KpiCard

Top-of-page KPI tile: a coloured brand KPI icon, an uppercase label and a large bold value with its unit. Shell is `boxShadow_kpi` on primary_white with `radius-card` (0.8vmin); the generic `.box` variant (Cards.module.scss) uses `shadow-card-strong`, padding 0.5vmin / 1.2vmin top.

**Consumer provides:** an icon from the **KPIs** asset group (landing-page or system-page set), a label, a value and an optional unit (e.g. `MT/DAY`, `%`).

- Value in `kpi-value` (sabic_text_bold 2.4vmin), label in 1.2vmin uppercase.
- Lay tiles out in a row with `space-1_5`–`space-2` gaps.
