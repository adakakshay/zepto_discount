# Zepto Discount Sorter

A browser bookmarklet that adds a floating control panel to Indian grocery sites (Zepto, BigBasket, JioMart, Blinkit, etc.) for sorting products by discount percentage or price.

## Features

- **Pincode Support** — Enter your delivery pincode once; it's saved to localStorage and auto-applied before every search
- **One-Click Category Search** — 19 preset categories (Atta, Rice, Oil, Ghee, Dal, Masala, Dairy, Electronics, etc.)
- **Sort by Discount %** — Products sorted highest discount first, with purple discount badges overlaid on each item
- **Sort by Price** — Toggle to sort lowest price first
- **Auto Scroll & Load** — Automatically scrolls the page to trigger lazy-loading, capturing all available products
- **Sort Current Page** — "Sort Page" button works on any page you've already navigated to
- **Links Open in New Tab** — All product links open in a new tab so you don't lose your sorted view
- **Minimize/Close** — Collapsible floating dock that stays out of the way

## How It Works

```
┌──────────────────┐
│  ✕  −            │
│  Pincode         │
│  [560001    ]    │
│  [Set Pincode]   │
│                  │
│  ⚡ Sort Page     │
│                  │
│  Atta            │
│  Rice            │
│  Oil             │
│  Ghee            │
│  Dal             │
│  ...             │
└──────────────────┘
```

1. **Set Pincode** — Enter your 6-digit pincode and click "Set Pincode". The bookmarklet attempts to find the site's location/delivery input and apply it automatically.
2. **Click a Category** — The bookmarklet searches for that category, scrolls to load all results, then sorts them by discount.
3. **Toggle Sort** — Click the "% Off ⬇" / "Price ⬆" pill at the top to switch sort modes.

## Installation

### As a Bookmarklet

1. Create a new bookmark in your browser
2. Name it something like "Zepto Sorter"
3. Paste the contents of `sort-deals-bookmarklet.txt` as the bookmark URL
4. Navigate to any grocery site and click the bookmark

### From Console

1. Open the browser developer console (F12 → Console)
2. Paste the contents of `sort-deals.js` and press Enter

## Files

| File | Description |
|------|-------------|
| `sort-deals.js` | Readable, formatted source code |
| `sort-deals-bookmarklet.txt` | Minified single-line version for bookmark URL |

## Supported Sites

Works on any Indian grocery/e-commerce site that:
- Displays prices with the ₹ symbol
- Has a text search input
- Uses standard DOM elements for product listings

Tested on: **Zepto**, **BigBasket**, **JioMart**, **Blinkit**

## Pincode Auto-Detection

The pincode feature uses a multi-strategy approach:
1. Looks for buttons/elements with text like "Deliver", "Location", "Pincode" and clicks to open the location modal
2. Finds input fields with matching placeholder/name/aria-label/id attributes
3. Falls back to searching inputs inside modal/overlay/popup containers
4. Types the pincode, then clicks confirm/apply buttons or submits via Enter

The pincode is persisted in `localStorage` (key: `z_pin`) so it survives page reloads.

## License

MIT
