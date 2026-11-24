---
name: cleanuipro
description: >-
  Clean, mature UI/UX design intelligence and implementation standards.
  Eliminates AI copy bloat, redundant explanations, childish colored accent borders,
  gratuitous bold typography, and circus color palettes. Enforces concise microcopy,
  scalable UI controls (searchable comboboxes vs dumb dropdowns), disciplined font
  weights, viewport-safe tooltips, full light/dark mode harmony, and mobile-responsive
  data lists with progressive disclosure.
metadata:
  version: "1.0.0"
---

# CleanUIPro: Mature, Bloat-Free UI/UX Design System

CleanUIPro enforces production-grade, human-centered UI/UX design. It specifically eradicates generic "AI tells" (over-explaining obvious features, tacky colored card borders, multi-color chaos, and broken mobile tables).

---

## 1. Microcopy & Labeling: The "Say Less" Rule

> [!IMPORTANT]
> **Never explain how data was derived, and never explain standard UI actions.**
> Users know what a button does. Keep labels strictly 1 to 2 words.

### The Bloat vs. Clean Rulebook

| Bloated AI Output (Banned) | CleanUIPro Standard (Required) | Why |
| :--- | :--- | :--- |
| `Calculated age from birth date: 24` | `Age: 24` | Users already know age comes from birth date. |
| `Click here to save your changes to database` | `Save Changes` (or `Save`) | Obvious action; redundant words waste cognitive energy. |
| `User unique system identification number` | `User ID` (or `#ID`) | Standard industry shorthand is universally understood. |
| `Enter your valid personal email address below` | Placeholder: `name@domain.com`, Label: `Email` | Explaining "valid personal" is patronizing clutter. |
| `Current live subscription plan status: Active` | Badge: `Active` next to `Plan` | Status color and single word tell the entire story. |
| `Total price after discount and taxes calculation` | `Total: $49.00` | Break calculations into line items in a receipt, not label prose. |

---

## 2. Scale-Aware UI Controls (Future-Proofing)

When rendering selection controls, **never assume data stays small**.

```
Item Count < 7      ──► Segmented Control or Radio Buttons
Item Count 7 - 15   ──► Standard Native <select> Dropdown
Item Count 15+      ──► Searchable Combobox / Typeahead Input (Debounced)
```

- **Example (Sports Score/Team/User Management):**
  - **Banned:** `<select>` with 200 player names where users must scroll endlessly on a phone.
  - **Required:** Search input with dropdown suggestions / typeahead combobox (`<input type="search" placeholder="Search player..." list="players">` or custom autocomplete).

---

## 3. Visual Restraint & Anti-AI Tells

### Ban the "Childish Colored Stripe Border"
AI models habitually slap `border-l-4 border-blue-500` or `border-t-4 border-indigo-600` on cards. This looks dated, templated, and juvenile.

- **Banned:**
  ```html
  <!-- Tacky AI style: thick colored left border -->
  <div class="bg-white border-l-4 border-blue-600 p-4 shadow">...</div>
  ```
- **Clean Alternative:**
  Use refined elevation, subtle single-pixel neutral borders, soft surface tints, or minimalist badges:
  ```html
  <!-- Mature clean card -->
  <div class="bg-surface rounded-xl border border-outline-variant/60 p-5 shadow-sm hover:border-outline transition-colors">
      <div class="flex items-center justify-between mb-3">
          <span class="text-xs font-semibold text-text-muted uppercase tracking-wider">Metric</span>
          <span class="inline-flex items-center px-2 py-0.5 rounded-full text-xs font-medium bg-primary/10 text-primary">Live</span>
      </div>
      ...
  </div>
  ```

### Strict Color Discipline (No "Circus" Palettes)
A single page must never have purple buttons, green headings, orange cards, and blue accents all fighting for attention.
1. **60-30-10 Rule:**
   - **60% Dominant Base:** Clean background & surface neutrals (slate/zinc/gray).
   - **30% Structure & Text:** High-contrast neutral typography and subtle border lines.
   - **10% Single Accent:** **ONE** primary brand color for actionable elements (active states, primary CTA, active tab).
2. **Semantic Colors are Functional, Never Decorative:**
   - Red (`danger`), Green (`success`), and Amber (`warning`) are strictly reserved for alerts, validation, and status badges. **Never** use green or red as decorative background accents.

---

## 4. Typography Weight Discipline (Stop the Bold Epidemic)

> [!IMPORTANT]
> **Stop making everything bold.** AI assistants habitually slap `font-bold` (700+) across every label, table cell, badge, paragraph, list item, and small caption. This creates visual fatigue and destroys visual hierarchy.

### The Weight Hierarchy Standard:

| Weight Class | CSS / Tailwind | Permitted Usage | Prohibited Usage (AI Tells) |
| :--- | :--- | :--- | :--- |
| **Normal** (400) | `font-normal` (or default) | **Default for 85%+ of UI text**: Body text, descriptions, table cells, form labels, tooltips, secondary metadata, captions. | Never upgrade body copy or standard labels to bold just to "make them stand out". |
| **Medium** (500) | `font-medium` | **Subtle structural emphasis**: Interactive buttons, tab labels, table header titles (`th`), active dropdown items. | Avoid stacking multiple medium elements inside a single row. |
| **Semibold** (600) | `font-semibold` | **Strict hierarchy milestones**: Primary page titles (H1/H2), key numerical KPI metrics (e.g. `$24,500`), primary modal headers. | Never use on small body text, table data cells, or form inputs. |
| **Bold / Heavy** (700+) | `font-bold` / `font-extrabold` | **Strictly restricted**: Hero landing display headlines only. | **BANNED on standard UI components**: No bold table cells, no bold form labels, no bold tooltips. |

### Contrast Rule:
Create visual hierarchy through **font size scale** (`text-sm`, `text-xs`) and **color contrast** (`text-slate-900` vs `text-slate-500` / `dark:text-slate-100` vs `dark:text-slate-400`), **never** by making everything bold.

---

## 5. Viewport-Safe Micro-Help & Tooltips

Never clutter the interface with descriptive paragraphs under every input or button.
- If an explanation is truly necessary for an esoteric metric (e.g. *"Net Churn Rate calculation"*), use a subtle info icon `(i)` with a tooltip.
- **Tooltip Viewport Guard:** Tooltips must **never** clip off-screen or hide beneath lower z-index cards.

### Rules for Safe Tooltips:
1. Position dynamically or use standard safe offsets (default to top/center, auto-flip to bottom if near the screen edge).
2. Set container to `z-50` and use `max-w-xs`, `whitespace-normal`, and `pointer-events-none`.
3. Never place a tooltip inside a parent with `overflow: hidden` unless the tooltip is portaled or uses `position: fixed`.

---

## 6. Light & Dark Mode Coherence

Every new page or component must dynamically inherit the active theme.

1. **Zero Hardcoded Colors:** Never use hardcoded hex values (`#fff`, `#111`, `#f3f4f6`) in components.
2. **Semantic Tokens or Theme Classes:**
   - Tailwind: Always pair background and text with dark variants (`bg-white dark:bg-slate-900 text-slate-900 dark:text-slate-100 border-slate-200 dark:border-slate-800`).
   - Plain CSS: Always use CSS custom properties (`var(--color-bg)`, `var(--color-surface)`, `var(--color-text)`, `var(--color-border)`).
3. **Contrast Verification:** Ensure muted text (`text-slate-500` on light) switches to readable slate (`dark:text-slate-400` on dark) with minimum 4.5:1 contrast ratio.

---

## 7. Responsive Lists & Tables (Progressive Disclosure)

Data tables that squeeze 7+ columns on a phone cause ugly horizontal overflows and truncated gibberish.

### The Mobile Progressive Disclosure Pattern:
- **Desktop (md+):** Full tabular view (ID, Name, Role, Email, Date, Status, Actions).
- **Mobile (<md):** Collapse to priority card or essential 2-3 columns:
  1. Primary Identifier (Name + Badge).
  2. Secondary context wrapped cleanly (Date or Status).
  3. Action link/button (`View Details`) that opens a slide-over drawer, modal, or dedicated view.
- **Line Breaks & Truncation:** Use `truncate` with `title="..."` attribute or wrap gracefully with `break-words`. Never let unconstrained text push elements off-screen.

```html
<!-- Responsive Table Row Example -->
<tr class="border-b border-border hover:bg-surface-hover transition-colors">
  <td class="p-4">
    <div class="font-medium text-text">Sarah Connor</div>
    <!-- Secondary info visible only on mobile under the name -->
    <div class="text-xs text-text-muted md:hidden">sarah@skynet.com • Added Oct 24</div>
  </td>
  <td class="p-4 hidden md:table-cell text-text-muted">sarah@skynet.com</td>
  <td class="p-4 hidden md:table-cell text-text-muted">Oct 24, 2026</td>
  <td class="p-4">
    <span class="inline-flex px-2 py-0.5 rounded text-xs font-medium bg-emerald-100 dark:bg-emerald-950/50 text-emerald-700 dark:text-emerald-400">
      Active
    </span>
  </td>
  <td class="p-4 text-right">
    <a href="/user/12" class="text-xs font-semibold text-primary hover:underline">View</a>
  </td>
</tr>
```

---

## 8. Quality Checklist Before Shipping Any UI

- [ ] **Are labels concise?** (No *"Calculated age from..."* or *"Click here to..."*).
- [ ] **Are large lists searchable?** (No 50+ item raw `<select>` tags).
- [ ] **Are childish colored left/top borders avoided?** (Clean, subtle 1px border & elevation used instead).
- [ ] **Is bold typography strictly restrained?** (Default 400 normal weight; semibold 600 reserved strictly for primary titles and KPI metrics; no bold labels or table cells).
- [ ] **Is the color palette restrained?** (1 primary accent, neutrals for everything else, semantic red/green only for status).
- [ ] **Does it look intentional in both Light AND Dark mode?**
- [ ] **Do tooltips stay fully inside the screen?**
- [ ] **Does the mobile view hide secondary columns gracefully without breaking the viewport?**
