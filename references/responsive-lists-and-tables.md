# Responsive Lists & Tables (Progressive Disclosure)

Data tables are notorious for breaking mobile layouts. When an AI generates a table with 6-8 columns, on mobile screens (<640px) it either forces an awkward horizontal scrollbar or squashes columns into illegible vertical slivers.

CleanUIPro enforces **Progressive Disclosure** for tabular and listed data.

---

## 1. Golden Rules for Mobile Data Display

1. **Max 2 to 3 Columns on Mobile:** On a phone, users only need to see **who/what** it is, its **status**, and an **action** to see more.
2. **Hide Secondary Context Gracefully:** Move secondary columns (Email, Date Created, Role, Category) into:
   - A muted sub-line directly under the primary title.
   - Or behind a click/tap target (Drawer / Modal / Detail Page).
3. **Never Allow Text to Push Containers Off-Screen:** Always apply `truncate` with `title="..."` or `break-words` on user-submitted text.

---

## 2. Desktop Table to Mobile Card Stack Pattern

Using Tailwind CSS, you can seamlessly render a clean table on desktop that transforms into stacked cards or compact priority rows on mobile:

```html
<div class="overflow-hidden rounded-xl border border-border bg-surface shadow-sm">
  <table class="w-full text-left text-sm">
    <thead class="border-b border-border bg-surface-muted text-xs uppercase tracking-wider text-text-muted">
      <tr>
        <th class="p-4 font-semibold">User</th>
        <th class="p-4 font-semibold hidden md:table-cell">Role</th>
        <th class="p-4 font-semibold hidden lg:table-cell">Joined</th>
        <th class="p-4 font-semibold">Status</th>
        <th class="p-4 text-right font-semibold">Action</th>
      </tr>
    </thead>
    <tbody class="divide-y divide-border">
      <tr class="hover:bg-surface-muted/50 transition-colors">
        <!-- Primary Cell: Shows extra details on mobile -->
        <td class="p-4">
          <div class="font-medium text-text">Alex Rivera</div>
          <div class="text-xs text-text-muted mt-0.5 md:hidden">
            Developer • Joined Oct 2026
          </div>
        </td>
        
        <!-- Hidden on Mobile -->
        <td class="p-4 hidden md:table-cell text-text-muted">Developer</td>
        <td class="p-4 hidden lg:table-cell text-text-muted">Oct 14, 2026</td>
        
        <!-- Status Badge -->
        <td class="p-4">
          <span class="inline-flex items-center px-2 py-0.5 rounded text-xs font-medium bg-emerald-100 text-emerald-800 dark:bg-emerald-950/60 dark:text-emerald-400">
            Active
          </span>
        </td>
        
        <!-- Compact Action Button -->
        <td class="p-4 text-right">
          <a href="/users/42" class="inline-flex items-center gap-1 text-xs font-semibold text-primary hover:text-primary-dark">
            <span>Details</span>
            <svg class="w-3.5 h-3.5" fill="none" stroke="currentColor" viewBox="0 0 24 24">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 5l7 7-7 7" />
            </svg>
          </a>
        </td>
      </tr>
    </tbody>
  </table>
</div>
```

---

## 3. Dedicated Card List Alternative for High-Density Data

When rows contain multiple complex metrics, switch the entire layout to a card grid on mobile:

```html
<!-- Table on desktop, Cards on mobile -->
<div class="hidden md:block">
  <!-- Standard desktop <table> -->
</div>

<div class="grid grid-cols-1 gap-3 md:hidden">
  <!-- Mobile Card Item -->
  <div class="p-4 bg-surface border border-border rounded-xl shadow-sm space-y-2.5">
    <div class="flex items-center justify-between">
      <h4 class="font-medium text-text">Alex Rivera</h4>
      <span class="px-2 py-0.5 rounded text-xs font-medium bg-emerald-100 text-emerald-800 dark:bg-emerald-950/60 dark:text-emerald-400">
        Active
      </span>
    </div>
    
    <div class="flex items-center justify-between text-xs text-text-muted">
      <span>Role: Developer</span>
      <span>Joined: Oct 14</span>
    </div>
    
    <div class="pt-2 border-t border-border flex justify-end">
      <a href="/users/42" class="text-xs font-semibold text-primary">View Profile &rarr;</a>
    </div>
  </div>
</div>
```
