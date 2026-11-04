# Viewport-Safe Tooltips & Popovers

A common flaw in AI-generated web interfaces is tooltips that:
1. Render underneath adjacent cards due to `overflow: hidden` on parent containers.
2. Render off the left or right edge of mobile screens.
3. Obscure the interactive element they describe.

---

## 1. CSS & Markup Pattern for Safe Tooltips

### Pure CSS Safe Tooltip (Center-Clamped)
```html
<div class="relative inline-flex items-center group">
  <!-- Trigger -->
  <button type="button" class="text-text-muted hover:text-text transition-colors p-1" aria-label="Help info">
    <svg class="w-4 h-4" fill="none" stroke="currentColor" viewBox="0 0 24 24">
      <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M13 16h-1v-4h-1m1-4h.01M21 12a9 9 0 11-18 0 9 9 0 0118 0z" />
    </svg>
  </button>

  <!-- Tooltip Bubble -->
  <div role="tooltip" class="absolute bottom-full left-1/2 -translate-x-1/2 mb-2 hidden group-hover:flex group-focus-within:flex flex-col items-center z-50 pointer-events-none w-max max-w-[220px] sm:max-w-xs">
    <div class="bg-slate-900 dark:bg-slate-800 text-white text-xs font-normal rounded-lg px-2.5 py-1.5 shadow-lg border border-slate-700/50 leading-relaxed text-center">
      Tooltip text goes here. Short, concise and informative.
    </div>
    <!-- Arrow -->
    <div class="w-2 h-2 bg-slate-900 dark:bg-slate-800 rotate-45 -mt-1 border-r border-b border-slate-700/50"></div>
  </div>
</div>
```

---

## 2. Dynamic Viewport Collision Prevention (JS)

When placing tooltips near the viewport edges (especially on mobile), use boundary checking:

```javascript
function positionTooltip(triggerEl, tooltipEl) {
  const triggerRect = triggerEl.getBoundingClientRect();
  const tooltipRect = tooltipEl.getBoundingClientRect();
  const padding = 12; // Screen margin

  // Default: Center above trigger
  let top = triggerRect.top - tooltipRect.height - 8;
  let left = triggerRect.left + (triggerRect.width / 2) - (tooltipRect.width / 2);

  // Flip to bottom if clipping top of screen
  if (top < padding) {
    top = triggerRect.bottom + 8;
  }

  // Shift left if clipping right edge of screen
  if (left + tooltipRect.width > window.innerWidth - padding) {
    left = window.innerWidth - tooltipRect.width - padding;
  }

  // Shift right if clipping left edge of screen
  if (left < padding) {
    left = padding;
  }

  tooltipEl.style.position = 'fixed';
  tooltipEl.style.top = `${top}px`;
  tooltipEl.style.left = `${left}px`;
  tooltipEl.style.zIndex = '9999';
}
```

### Essential Rules:
- **Never place tooltips inside `overflow: hidden` containers** without fixing their position or portaling them to `document.body`.
- **Touch Devices:** Don't rely solely on `:hover`. Support tap-to-toggle or long-press on mobile devices.
