# CleanUIPro

**CleanUIPro** is an Antigravity skill and UI/UX design intelligence standard. It eliminates generic "AI tells" such as bloated explanatory labels, childish colored accent card borders, circus color palettes, and broken mobile data lists.

---

## What CleanUIPro Solves

1. **Microcopy Anti-Bloat:**
   - Stops AI from writing *"Calculated age from birth date: 24"*. Replaces with clean, human microcopy: `Age: 24`.
   - Eliminates redundant button explanations (e.g., replaces *"Click here to save your changes to database"* with `Save`).
2. **Scale-Aware UI Controls:**
   - Replaces dumb 100-item `<select>` tags with searchable comboboxes, typeaheads, and debounced autocomplete inputs.
3. **Strict Typography Weight Discipline (Stop the Bold Epidemic):**
   - Eliminates gratuitous bold fonts (`font-bold`, `font-extrabold`) slapped onto every label, table cell, badge, and small caption.
   - Enforces default normal weight (`font-normal`, 400), subtle medium (`font-medium`, 500) for interactive buttons/headers, and reserves semibold (`font-semibold`, 600) strictly for primary titles and KPI figures.
4. **No Childish Colored Stripe Borders:**
   - Bans dated `border-l-4 border-blue-500` / `border-t-4` styling.
   - Enforces mature elevation, 1px subtle borders, and clean typography.
5. **Strict Zero Emojis as Icons (SVG Only):**
   - Strictly bans emojis (🚀, 🔥, ⚙️, etc.) as UI icons across all components.
   - Enforces clean inline SVGs or `.svg` files with `currentColor` stroke/fill for crisp, theme-aware rendering across all operating systems.
6. **Color Discipline (No Circus Palettes):**
   - 60-30-10 rule: 1 single primary brand accent, neutral surfaces/text, and functional-only semantic colors (red/green reserved strictly for alerts & badges).
7. **Viewport-Safe Tooltips:**
   - Prevents tooltips from clipping off-screen or being trapped under parent `overflow: hidden` elements.
8. **Full Light/Dark Mode Coherence:**
   - Enforces semantic design tokens and dark mode pairs for all components.
9. **Mobile-Responsive Data Lists (Progressive Disclosure):**
   - Enforces 2-3 priority columns on mobile screens, tucking secondary details into clean sub-lines or modals/drawers instead of breaking horizontal viewport bounds.

---

## Directory Structure

```text
cleanuipro/
├── SKILL.md
├── README.md
├── .gitignore
└── references/
    ├── microcopy-and-anti-bloat.md
    ├── typography-weight-discipline.md
    ├── scale-aware-controls.md
    ├── tooltips-and-popovers.md
    └── responsive-lists-and-tables.md
```

---

## Installation

```bash
# Clone into your Antigravity skills directory
git clone git@github.com:devsuyeb/cleanuipro.git ~/.gemini/config/skills/cleanuipro
```

---

## Documentation

- [Microcopy & Anti-Bloat Guide](references/microcopy-and-anti-bloat.md)
- [Typography Weight Discipline](references/typography-weight-discipline.md)
- [Scale-Aware Controls Guide](references/scale-aware-controls.md)
- [Viewport-Safe Tooltips & Popovers](references/tooltips-and-popovers.md)
- [Responsive Lists & Tables (Progressive Disclosure)](references/responsive-lists-and-tables.md)

---

## License

MIT License.
