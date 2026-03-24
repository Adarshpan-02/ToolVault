# 🗄️ ToolVault — Personal Website & Tool Manager

> A zero-dependency, fully offline personal tool manager built as a single HTML file.
> Save, organise, rate, and export your favourite websites and developer tools — no server, no login, no internet required.

---

## ✨ Features

### 🗂️ Category Management
- Create unlimited categories (e.g. "AI Tools", "Design", "Coding")
- Rename categories inline — click the pencil icon on hover
- Delete categories with a confirmation modal (tools move to Uncategorized)
- Colour-coded category badges on every card

### 🃏 Tool Cards
- Add tools with: **Name**, **URL**, **Description**, **Rating (1–10)**, **Category**, **Favourite toggle**
- Cards show a live rating progress bar, clickable URL, and category badge
- Every uncategorised tool shows an "Uncategorized" badge — nothing is ever invisible
- Long descriptions collapse to 2 lines with a **Show more / Show less** toggle

### ⭐ Favourites
- Mark any tool as a favourite with the heart button
- Filter to favourites-only via the sidebar or the topbar chip
- Favourite state updates instantly without re-rendering the full grid

### 🔍 Search & Filter
- Live search across tool name, description, and category
- Sort by: Newest · Oldest · Rating ↓ · Rating ↑ · A–Z
- Sort preference is **persisted** across page reloads
- Search clear button appears only when there is text (keyboard accessible)

### ↩️ Undo Delete
- Deleting a tool shows a 5-second toast with an **Undo** button
- Click Undo to instantly restore the tool — no data is lost until the timer expires

### 🔄 Import / Export
| Format | Export | Import |
|--------|--------|--------|
| **JSON** | Full data including categories | ✅ |
| **CSV**  | Spreadsheet-compatible | ✅ |
| **HTML** | Shareable standalone page | — |
| **PDF**  | Print-ready via browser print dialog | — |

- Import deduplicates by name + URL — no double entries
- Drag & drop files onto the import drop zone
- PDF export uses a Blob URL (works offline, no popup blocker issues)
- CSV export includes a UTF-8 BOM for correct Excel rendering

### 💾 Offline & Privacy First
- All data lives in your browser's `localStorage` — nothing leaves your device
- Works with zero internet connection after the first load
- No tracking, no analytics, no external requests at runtime

### ♿ Accessibility
- Full keyboard navigation (Tab, Shift+Tab, Enter, Space, Escape)
- ARIA labels, roles, live regions, and `aria-pressed` / `aria-checked` states
- Focus trap inside all modals with correct focus restore on close
- Skip-to-content link for screen reader users
- Respects `prefers-reduced-motion`
- Duplicate URL warning in the Add Tool form

### ⌨️ Keyboard Shortcuts
| Shortcut | Action |
|----------|--------|
| `Ctrl / ⌘ + K` | Focus the search bar |
| `Ctrl / ⌘ + N` | Open "Add Tool" modal |
| `Escape` | Close the current modal or sidebar |

---

## 🚀 Getting Started

No installation needed.

1. Download `index.html`
2. Open it in any modern browser
3. Start adding tools

That's it. One file. No build step. No dependencies.

---

## 🗺️ App Layout

```
┌─────────────────────────────────────────────────────────┐
│  Sidebar            │  Topbar                           │
│  ─────────────────  │  ─────────────────────────────── │
│  📁 All Tools (12)  │  🔍 Search…  ♥ Favorites  Sort ▾ │
│  ♥ Favorites (3)    │                   Import Export + │
│                     ├───────────────────────────────────│
│  CATEGORIES         │  Stats: Total · Favs · Cats · Avg │
│  📂 AI Tools (4)    ├───────────────────────────────────│
│  📂 Design (3)      │                                   │
│  📂 Coding (5)      │  ┌────────┐ ┌────────┐ ┌───────┐ │
│                     │  │ Card 1 │ │ Card 2 │ │Card 3 │ │
│  + New category…    │  └────────┘ └────────┘ └───────┘ │
└─────────────────────┴───────────────────────────────────┘
```

---

## 🛠️ Tech Stack

| Layer | Choice | Why |
|-------|--------|-----|
| Structure | Vanilla HTML5 | Zero build tooling needed |
| Styling | Pure CSS with CSS Variables | Themeable, responsive, no framework |
| Logic | Vanilla JS (ES2020, strict mode) | No dependencies, works offline |
| Storage | `localStorage` | Persistent, private, browser-native |
| Export | Blob URLs + FileReader API | No server required |

---

## 📁 Data Structure

Tools and categories are stored in `localStorage` as JSON under keys `tv5_t` and `tv5_c`.

```json
{
  "version": "5",
  "categories": [
    { "id": "tv17100001", "name": "AI Tools" }
  ],
  "tools": [
    {
      "id": "tv17100002",
      "name": "ChatGPT",
      "url": "https://chat.openai.com",
      "desc": "AI assistant by OpenAI",
      "rating": 9,
      "fav": true,
      "catId": "tv17100001"
    }
  ]
}
```

---

## 📦 Export Formats

### CSV
Compatible with Excel, Google Sheets, and Numbers. Includes a UTF-8 BOM.
Columns: `Name, URL, Description, Rating, Category, Favorite`

### JSON
Full export including categories and tools. Can be re-imported into any ToolVault instance.

### HTML
A self-contained dark-themed HTML table page — shareable with anyone via email or message.

### PDF
Opens a print-ready page in a new tab using the Blob URL method. Select **"Save as PDF"** in your browser's print dialog. Falls back to an HTML download if popups are blocked.

---

## 🔒 Security

- All user content is HTML-escaped via a `san()` function before any `innerHTML` insertion
- URLs are validated with the native `URL` constructor — `javascript:` URIs are rejected
- All external links use `rel="noopener noreferrer"`
- Import file size is capped at 5 MB
- Input lengths are capped: name 80 chars, description 400 chars, category 40 chars

---

## 🌐 Browser Support

| Browser | Support |
|---------|---------|
| Chrome / Edge 90+ | ✅ Full |
| Firefox 90+ | ✅ Full |
| Safari 15+ | ✅ Full |
| Mobile Chrome / Safari | ✅ Full (responsive) |

---

## 📝 Changelog

### v5.0
- Undo delete with 5-second window
- Duplicate URL warning on Add/Edit form
- Description expand/collapse on cards
- Uncategorized badge always shown
- Sort preference persisted across reloads
- Stack-based focus restore for nested modals
- PDF export rewritten using Blob URL (fixes blank tab bug)
- Character counter on description field
- Edit modal now shows "Update Tool" to distinguish from Add

### v4.0
- Full accessibility pass (ARIA, focus trap, live regions)
- Keyboard shortcuts: Ctrl+K, Ctrl+N, Escape
- Category delete always requires confirmation modal
- URL is now a real clickable `<a>` link on each card
- Favourite toggle updates in-place without full grid re-render

---

## 📄 License

MIT — free to use, modify, and distribute.

---

