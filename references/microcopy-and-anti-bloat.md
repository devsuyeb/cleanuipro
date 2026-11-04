# Microcopy & Anti-Bloat Guide

AI assistants naturally tend to write overly verbose, academic, or apologetic prose. In software interfaces, **every unnecessary word adds cognitive strain and visual clutter**.

---

## 1. Core Principles of Clean UI Copy

1. **Context Over Explanation:** A field labeled `Birth Date` followed by `Age: 32` does not need `Calculated age based on provided birth date`. The user’s brain instantly understands the connection.
2. **Action-Driven Buttons:** Use `[Verb] [Noun]` or a single `[Verb]`. Never use filler phrases like *"Click here to submit"*.
3. **No Decorative Help Text:** If 99% of web users know what the field is, delete the help text under it. Only use help text when input format is strictly constrained (e.g. `Must include at least 1 number and 1 special symbol`).

---

## 2. Before & After Transformation Table

### Form Labels & Values
| Bloated AI Output | Clean Human Standard |
| :--- | :--- |
| `Calculated age from birth date` | `Age` |
| `Your registered official email address` | `Email` |
| `Input your account security password here` | `Password` |
| `User identity verification status: Verified` | Badge: `Verified` |
| `Shipping delivery destination street address` | `Street Address` |
| `Total payable billing amount after taxes` | `Total Amount` |
| `Phone contact calling number` | `Phone` |

### Buttons & Call-to-Actions
| Bloated AI Output | Clean Human Standard |
| :--- | :--- |
| `Click here to complete your checkout order` | `Place Order` |
| `Press this button to confirm account deletion` | `Delete Account` |
| `Download your exported monthly PDF invoice report` | `Download PDF` |
| `Click to add a brand new item to the table` | `+ Add Item` |
| `Submit this message to customer support staff` | `Send Message` |
| `Save all modifications and updates` | `Save Changes` |

### Empty States & Notifications
| Bloated AI Output | Clean Human Standard |
| :--- | :--- |
| `There are currently no available items present in this list right now` | `No items found` |
| `Your settings configuration has been successfully saved to the server` | Toast: `Settings saved` |
| `An unexpected error has occurred while attempting to process your request` | `Unable to save changes. Try again.` |
| `Are you completely sure you really want to delete this specific record?` | `Delete this record?` |
