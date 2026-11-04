# Scale-Aware UI Controls

When designing selection interfaces, always design for **growth**. 

A dropdown `<select>` that contains 10 items in a prototype will fail catastrophically when populated with 500 users, 2,000 products, or 50 sports teams in production.

---

## 1. The Component Selection Threshold

| Dataset Size | Recommended Control | Why |
| :--- | :--- | :--- |
| **2 – 5 Options** | Radio Buttons / Segmented Pills | All choices visible at a single glance; 1-click selection. |
| **6 – 15 Options** | Native `<select>` Dropdown | Compact, accessible, easily scrollable on mobile. |
| **15+ Options or Dynamic Data** | Searchable Combobox / Typeahead Input | Scrolling through 50+ items is painful; user typing filters results in ms. |
| **100+ Options / Server-Side** | Debounced Remote Search / Modal Picker | Prevents loading huge DOM trees; queries API on demand. |

---

## 2. Accessible Searchable Input / Combobox Pattern

### Lightweight Vanilla HTML/JS Implementation
```html
<div class="relative w-full max-w-sm" data-combobox>
  <label for="player-search" class="block text-xs font-semibold text-text-muted uppercase mb-1.5">
    Select Player
  </label>
  <div class="relative">
    <input 
      type="search" 
      id="player-search" 
      class="w-full px-3 py-2 pl-9 bg-surface border border-border rounded-lg text-sm text-text placeholder:text-text-muted focus:outline-none focus:ring-2 focus:ring-primary/20 focus:border-primary"
      placeholder="Type to search player..."
      autocomplete="off"
    >
    <!-- Search Icon -->
    <svg class="absolute left-3 top-2.5 w-4 h-4 text-text-muted pointer-events-none" fill="none" stroke="currentColor" viewBox="0 0 24 24">
      <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M21 21l-6-6m2-5a7 7 0 11-14 0 7 7 0 0114 0z"/>
    </svg>
  </div>

  <!-- Filtered Dropdown Results List -->
  <ul 
    class="absolute left-0 right-0 top-full mt-1.5 max-h-56 overflow-y-auto bg-surface border border-border rounded-lg shadow-lg z-50 divide-y divide-border hidden"
    role="listbox"
  >
    <!-- Filtered items injected here dynamically -->
  </ul>
</div>
```

### Debouncing Dynamic Searches
```javascript
function debounce(func, wait = 250) {
  let timeout;
  return function executedFunction(...args) {
    const later = () => {
      clearTimeout(timeout);
      func(...args);
    };
    clearTimeout(timeout);
    timeout = setTimeout(later, wait);
  };
}

const handleSearch = debounce(async (query) => {
  if (query.trim().length < 2) return;
  const res = await fetch(`/api/search?q=${encodeURIComponent(query)}`);
  const data = await res.json();
  renderResults(data);
}, 250);
```
