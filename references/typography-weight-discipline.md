# Typography Weight Discipline (Stop the Bold Epidemic)

AI coding assistants have an instinctive habit of applying `font-bold` (700) or `font-extrabold` (800) to virtually every label, table cell, badge, and paragraph. When everything is bold, **nothing stands out**, and the interface looks amateurish, aggressive, and visually cluttered.

---

## 1. The Weight Hierarchy Rules

### Default is Always Normal (400)
- **85%+ of all text on screen must be normal weight (`font-normal`, 400).**
- Body paragraphs, form input labels, placeholder text, table cells, secondary metadata, help text, and tooltips must default to `font-normal`.
- Form labels: Use `text-xs text-slate-600 dark:text-slate-400 font-normal` or `font-medium` at most. Never `font-bold`.

### Subtle Structural Emphasis (500)
- Use `font-medium` (500) when slight differentiation is needed without visual weight heaviness:
  - Table header labels (`th`).
  - Interactive buttons (`button`, `.btn`).
  - Tab navigation labels.
  - Active dropdown selection items.
  - Primary list row title (e.g. user name in a contact list).

### Strict Reserved Usage for Semibold (600)
- Use `font-semibold` (600) strictly for high-level landmark hierarchy:
  - Primary page headings (`h1`, `h2`).
  - Key numerical KPI figures (e.g. `৳24,500` or `99.8%`).
  - Primary modal title.

### Bold / Heavy (700+) is Restricted
- **BANNED on standard UI components:**
  - No bold table data cells.
  - No bold input labels.
  - No bold small badges or tags.
  - No bold tooltips.
- Hero marketing headlines on landing pages are the only acceptable place for 700+ weights.

---

## 2. Before & After Code Comparisons

### Form Labels & Inputs
```html
<!-- BANNED AI HABIT: Bold labels screaming for attention -->
<div>
  <label class="block text-sm font-bold text-gray-900 mb-1">Customer Full Name</label>
  <input class="w-full font-bold p-2 ..." />
</div>

<!-- CLEAN STANDARD: Normal weight, restrained and elegant -->
<div>
  <label class="block text-xs font-medium text-slate-700 dark:text-slate-300 mb-1">Customer Name</label>
  <input class="w-full font-normal text-sm p-2 text-slate-900 dark:text-slate-100 ..." />
</div>
```

### Table Rows & Cells
```html
<!-- BANNED AI HABIT: Bold text in every single cell -->
<tr>
  <td class="p-3 font-bold text-gray-900">John Doe</td>
  <td class="p-3 font-bold text-gray-700">john@example.com</td>
  <td class="p-3 font-bold text-blue-600">Admin</td>
</tr>

<!-- CLEAN STANDARD: Name in medium/normal, secondary metadata in muted normal -->
<tr>
  <td class="p-3 font-medium text-slate-900 dark:text-slate-100">John Doe</td>
  <td class="p-3 font-normal text-slate-500 dark:text-slate-400">john@example.com</td>
  <td class="p-3 font-normal text-xs text-primary">Admin</td>
</tr>
```

### KPI / Metric Cards
```html
<!-- BANNED AI HABIT: Everything bolded -->
<div class="p-4 bg-white rounded-lg">
  <p class="font-bold text-gray-500 text-xs">TOTAL REVENUE</p>
  <h3 class="font-black text-2xl text-gray-900">$12,450</h3>
</div>

<!-- CLEAN STANDARD: Subtle muted label, semibold value -->
<div class="p-5 bg-surface border border-border rounded-xl">
  <p class="text-xs font-medium text-text-muted uppercase tracking-wider">Total Revenue</p>
  <h3 class="text-2xl font-semibold text-text mt-1">$12,450</h3>
</div>
```

---

## 3. How to Create Visual Hierarchy Without Heavy Weights

1. **Size Contrast:** Step down secondary text from `text-sm` (14px) to `text-xs` (12px).
2. **Color Contrast:** Use high-contrast for primary elements (`text-slate-900 dark:text-white`) and low-contrast for secondary metadata (`text-slate-500 dark:text-slate-400`).
3. **Tracking (Letter Spacing):** For small uppercase tags or category headers, add `tracking-wider` or `tracking-wide` rather than cranking the font weight to bold.
