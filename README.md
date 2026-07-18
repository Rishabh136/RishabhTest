# Staff Ledger

A simple PIN-based staff and payment register for a small shop (e.g. a kapra ghar / cloth store). Everything runs in the browser — no server, no build step. Data is stored in the browser's localStorage.

## How to use

Open `index.html` in any browser (double-click it, or host it somewhere like GitHub Pages). No internet connection or build step is needed — React is bundled in the `vendor/` folder.

### Roles

- **Admin (business owner)** — create a business with a 4-digit PIN, add employees (name + 10-digit phone + 4-digit PIN), and keep a money ledger per employee: salary/bonus credits and advances/payments given, with a running balance.
- **Employee** — log in with the business, their phone number, and their PIN to see their own ledger (read-only).
- **Platform owner (super admin)** — the small "Platform owner login" link at the bottom of the landing screen. Master key: `kapraghar-owner-2026` (change the `SUPER_ADMIN_KEY` constant in `index.html` before relying on it). Shows every registered business with its creation date, owner PIN, and employees, and can delete a business.

### Design notes

- Login and signup keep fully separate PIN fields, and PIN fields clear automatically after a failed attempt — this fixes the "wrong PIN" bug caused by digits carrying over between forms.
- Businesses with the same name are allowed but shown with their creation date and employee count so you can tell them apart; signup warns before creating an exact duplicate name.

## Important limitation

This is a fully client-side app: all PINs and the master key are visible to anyone who inspects the page or localStorage, and data lives only in the browser it was created in (it does not sync between devices). Fine for personal/testing use — not a real security boundary.
