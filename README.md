# PasswordGenerator

An advanced, privacy-friendly, in-browser password generator (single HTML file). Generates passwords locally with strength feedback, multi-password output, and optional local history/export.

## Quick start

1. Open `PasswordGenerator.html` in any modern browser (no server or install required).
2. Choose **Length**, **Quantity**, and **Character types**.
3. (Optional) Expand **Advanced** to refine generation rules.
4. Click **Generate** (or press **Ctrl/⌘ + Enter**).
5. Use the output actions to **Reveal**, **Copy**, **Regenerate**, **Save**, or **Export**.

## Features

### Modern UI & layout
- **Modern 2-column responsive layout**:
  - Left: settings and generation controls
  - Right: output, strength/entropy, multi-password list, and saved history
  - Automatically stacks for smaller screens
- **Theme switcher** with persistent preference:
  - **System**, **Light**, **Dark**, **High-contrast**
  - Reacts to OS theme changes when in **System** mode
- **Keyboard shortcut hint** visible in the header for quick discovery
- **Toast notifications** for feedback (copy success/failure, warnings, actions)
  - Dismiss via close button or **Esc**

### Password length & quantity
- **Length slider + numeric input** with live label
  - Range: **4–64**
- **Quantity control** to generate multiple passwords per run
  - Range: **1–10**
  - Additional generated passwords are shown in a list with per-item actions

### Character set controls
- Built-in character types:
  - **Uppercase (A–Z)**
  - **Lowercase (a–z)**
  - **Numbers (0–9)**
  - **Symbols** (enabled by user; off by default for compatibility)
- **Custom characters** input:
  - Adds your own characters to the generation set
  - Automatically de-duplicates repeated characters

### Advanced options (accordion)
- **Exclude similar characters** (helps readability / reduces confusion):
  - Filters: `i, l, 1, L, o, 0, O`
  - Applies across all enabled groups (including custom characters)
- **Exclude ambiguous symbols**:
  - Filters common “hard-to-type / easy-to-mistake” punctuation (e.g., braces/brackets and similar)
  - Applies to the **symbol** group
- **Require each selected type**:
  - Ensures the generated password contains at least one character from every enabled set
  - If **Custom characters** are provided and this option is enabled, at least one custom character is included
- Convenience toggles:
  - **Auto-copy on generate** (copies the primary output password)
  - **Auto-save to history** (saves the primary output password automatically)

### Output tools
- Read-only password output field with icon actions:
  - **Show/Hide** (reveal toggle)
  - **Copy**
  - **Regenerate**
- **Strength meter** (0–100) with label:
  - Weak / Medium / Strong / Very strong
- **Entropy estimate (bits)** and **charset size indicator**:
  - Displays an estimated entropy value based on length and effective character set size
  - Shows the total unique characters available in the final charset

### Inline validation & safe disabling
- **Inline validation messaging** explains invalid configurations and prevents actions:
  - Disables Generate/Regenerate/Copy when invalid
  - Example: requiring each type when length is too short for the number of selected groups

### Multi-password output list
- When Quantity > 1:
  - Additional generated passwords appear in a list
  - Each item includes:
    - **Copy**
    - **Save** (stores that specific password into history)

### History & export
- **Save to history** button for the main output password (manual save)
- Saved history includes:
  - Local timestamps for each entry
  - Per-entry actions:
    - **Use** (loads into the main output field)
    - **Copy**
    - **Delete**
- **History capacity limit**:
  - Keeps up to **40** saved entries (oldest entries are dropped automatically)
- **Clear history** with a non-blocking confirm step:
  - Requires a second click within a short window (“Confirm clear”) to avoid accidental loss
- **Export to `.txt`**:
  - Exports:
    - Current output password (if present)
    - Additional generated passwords (if present)
    - Saved history (timestamped)
  - File name: `passwords-export.txt`

### Persistence (local storage)
- **Settings automatically persist** in the browser via `localStorage`:
  - Length, quantity, selected character types, advanced toggles, and custom characters
- **Theme mode persists** in the browser
- **History persists** in the browser until deleted/cleared

## Keyboard shortcuts
- **Ctrl/⌘ + Enter** — Generate
- **Ctrl/⌘ + C** — Copy (only when the password field is focused)
- **Esc** — Dismiss toast notification

## Security & privacy notes
- Passwords are generated **locally in your browser**.
- Randomness:
  - Uses `crypto.getRandomValues` when available (preferred for security)
  - If unavailable, falls back to `Math.random` and shows a warning toast (reduced security)
- Clipboard:
  - Copy uses the Clipboard API when available, with a fallback method for older contexts
  - Some browsers or environments may block clipboard access; the UI will notify you
- Local storage:
  - If you enable saving (or use auto-save), passwords are stored in **browser localStorage**.
  - Avoid saving passwords on shared/public machines; clear history when finished.

## Defaults & limits
- Default length: **16**
- Default quantity: **1**
- Default enabled types: **Uppercase**, **Lowercase**, **Numbers**
- Symbols: **off by default**
- Length bounds: **4–64**
- Quantity bounds: **1–10**
- Saved history cap: **40 entries**
