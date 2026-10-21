# STATE — रंग भरो (Rang Bharo) Kids Coloring PWA

## Current version: v1.0.0 (2026-10-21)

## What it is
Single-file PWA (`index.html`) for small kids: pick a picture, pick a colour, touch an area (or drag the colour onto it) and the whole area fills. Works offline after first open, installable on Android ("📲 इंस्टॉल" button / Chrome menu → Add to Home screen).

## Files
| File | Purpose |
|---|---|
| `index.html` | Whole app — UI, fill engine and all 227 pictures (drawn as SVG code, no image files) |
| `manifest.json` | PWA install info (name, colours, icons) |
| `sw.js` | Service worker, network-first, offline cache (`rangbharo-v1.0.0`) |
| `icon-192.png`, `icon-512.png` | App icon (palette + crayon on indigo) |
| `STATE.md` | This file |

## Pictures (227)
| Category | Count | Notes |
|---|---|---|
| जानवर | 50 | 25 animals × 2 scenes (2nd one mirrored, different background) |
| पक्षी-कीड़े | 20 | 10 × 2 scenes |
| समुद्र | 20 | 10 × 2 sea backgrounds |
| कार्टून | 22 | 11 original characters × 2 scenes |
| भक्ति | 18 | ॐ, स्वस्तिक, दीया, कलश, मंदिर, कमल, गणेश जी, बांसुरी-मोरपंख, शिवलिंग, त्रिशूल-डमरू, शंख, घंटी, तीर्थंकर भगवान, अहिंसा, माखन मटकी, 3 रंगोली |
| प्रकृति | 12 | full scenes: घर, पहाड़-नदी, इंद्रधनुष, सेब का पेड़, गमले, झोपड़ी, सूरजमुखी, बारिश, रात कैंपिंग, रेगिस्तान, समुद्र किनारा, मशरूम घर |
| गाड़ियाँ | 12 | incl. ऑटो रिक्शा, ट्रैक्टर |
| फल-सब्ज़ी | 14 | |
| खिलौने | 12 | incl. पतंग, लट्टू, ढोल |
| ABC | 26 | big outline letter + object + word |
| गिनती | 10 | 1–10 with English + Hindi word and that many objects |
| स्वर | 11 | अ–अं with object + word |
| मेरी फोटो | ∞ | photo of any colouring-book page → crop → becomes colourable line art |

## Features
- Tap-to-fill with ripple animation, sparkle + pop sound + tiny vibration
- Drag a colour up from the palette and drop it on the picture
- 23 colours + रबर (white eraser) + ✨ जादुई रंग (random colour each tap)
- Pinch to zoom / drag to pan when zoomed, "⤢ पूरा चित्र" to reset
- Undo (40 steps), clear-all with confirm, ‹ › next/previous picture
- Auto-save per picture in IndexedDB; coloured thumbnail + ✓ badge on home
- Save / share PNG (WhatsApp share sheet on Android, download fallback)
- Sound on/off, last category & colour remembered

## Decisions
- Pictures are code (SVG strings) so the whole app is one ~116 KB file and there are no copyrighted images.
- Fill engine: picture rendered to a 1000×1000 canvas → dark pixels = walls → scanline flood fill on a separate colour layer, colour grown 3px under the lines, then line layer drawn on top with `multiply`.
- Photo mode: crop → adaptive threshold (local mean) → speck removal → 1px line thickening → frame border.
- Font Baloo 2 from Google Fonts (non-blocking, cached by SW); system font fallback.

## Pending / ideas
- APK via apk-factory (point config.json at the GitHub Pages URL)
- Pencil / free-draw brush and stickers
- Parent lock for delete / clear
- More picture packs (Jain festivals, Marathi व्यंजन, numbers 11–20)
