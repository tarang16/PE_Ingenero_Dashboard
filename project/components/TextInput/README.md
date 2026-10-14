# TextInput

Text inputs and textareas: 1px primary_gray_3 border, `radius-control`; focus keeps the same border — no blue glow, no outline.

**Consumer provides:** value / placeholder and, for formula fields, the validation state class.

- Validation is shown by border colour plus a background icon, not helper text: `.validFormulaBox` (green + check), `.invalidFormulaBox` / `.warningFormulaBox` (orange + warning icon), `.verifyingFormulaBox` (yellow + loader).
