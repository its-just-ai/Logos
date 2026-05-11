# Logos — Learning App

## Files

- `index.html` — The entire app (all content, logic, and styles)
- `manifest.json` — PWA configuration for “Add to Home Screen”
- `sw.js` — Service worker (offline support)
- `icon-180.png`, `icon-192.png`, `icon-512.png` — App icons (create these separately)

## Deploying as a PWA (iPhone)

1. Host these files on any HTTPS server (GitHub Pages, Netlify, Vercel, etc.)
1. Visit the URL in Safari on iPhone
1. Tap the Share button → “Add to Home Screen”
1. The app installs with its own icon and runs fullscreen

## Icons

You need to create icon image files:

- `icon-180.png` — 180×180px (used by iOS for the home screen icon)
- `icon-192.png` — 192×192px
- `icon-512.png` — 512×512px

Use any image editor. A simple dark background (#0f1117) with a gold letter “L” in Playfair Display font works well.

## How to Add a New Subject in the Future

Open `index.html` and find the `UNITS` array near the top of the `<script>` block.

Each unit has this structure:

```javascript
{
  id: 'u1',                        // Unique ID (don't reuse)
  title: 'Unit Title',
  desc: 'Short description',
  lessons: [
    {
      id: 'l1',                    // Unique ID
      title: 'Lesson Title',
      content: () => `             // Returns HTML string
        <div class="content-block">
          <p>Your content here...</p>
        </div>
      `
    }
  ],
  quiz: [
    {
      q: 'Question text',
      scenario: 'Optional scenario shown above the question',  // Can omit
      options: ['Option A', 'Option B', 'Option C', 'Option D'],
      correct: 0,                  // Index of correct answer (0-based)
      feedback: 'Explanation shown after answer is selected'
    }
  ]
}
```

To add a **new subject**, the cleanest approach is to:

1. Tell me (Claude) the subject
1. I will research it, structure the pedagogy appropriately for that domain, and write the content units
1. You paste the new UNITS array entries into the file

## Available CSS Classes for Lesson Content

- `.content-block` — Wrap each section
- `.callout` / `.callout.blue` — Highlighted quote or key point
- `.definition-box` — Term + definition card
- `.bias-card` — Named concept card (works for anything, not just biases)
- `.elements-grid` — 2-column grid of small cards
- `.element-item` with `.el-name` — Grid item
- `.standards-list` — Wrapping pill row
- `.standard-pill` — Individual pill
- `.two-col` — 2-column layout
- `.sys-card.s1` / `.sys-card.s2` — Red/blue comparison cards
- `.source-note` — Small italic citation text

## Content Policy

All lesson content must be based on:

- Published research papers
- Peer-reviewed textbooks
- Established scholarly frameworks

Paraphrasing and synthesis of sources is appropriate. Original claims not traceable to sources are not added.
