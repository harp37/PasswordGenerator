# PasswordGenerator
A feature-filled in-browser password generator!

**Features**
* Modern 2-column responsive layout (settings on the left, output/history on the right; stacks cleanly on mobile)
* Theme switcher: System / Light / Dark / High-contrast
* Length slider + numeric input with live length label
* Icon action buttons on the password field: show/hide, copy, regenerate
* Strength meter upgrade plus entropy estimate (bits) and charset size indicator
* Advanced options accordion with smoother behavior and better grouping
* Inline validation messaging (disables generation when settings are invalid, explains why)
* Safer preset button (quickly applies safer defaults)
* History tools: clear-all with a non-blocking confirm step, plus Export to .txt
* Keyboard shortcuts: Ctrl/⌘ + Enter to generate; Ctrl/⌘ + C to copy when the password field is focused
* Improved randomness using crypto.getRandomValues when available (with a graceful fallback warning)
