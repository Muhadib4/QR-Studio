# QR Studio

QR Studio is a local-first QR code design workstation for creating, styling, validating, and exporting real QR signals. It combines a practical editor with a restrained CRT / receipt-terminal visual language.

## Features

- URL, text, email, phone, SMS, Wi-Fi, vCard, geo, event, and media-link payloads.
- Live QR rendering with square, rounded, dots, extra-rounded, diamond, pixel, and finder-eye variations.
- Solid and gradient foregrounds, transparent or solid backgrounds, safe quiet-zone control, ECC L/M/Q/H, and local center logo support.
- Scan diagnostics for contrast, quiet zone, payload size, logo occlusion, and background status.
- Curated presets, safe randomize, undo/redo, local saved designs, versioned JSON project import/export.
- PNG, SVG, and WebP exports at 256, 512, 1024, 2048, and 4096px.
- Responsive preview-first mobile workflow and reduced-motion support.

## Installation

```bash
npm install
npm run dev
```

Open the local URL shown by Vite. The production build is:

```bash
npm run build
npm run preview
```

## Technology

- React 18+
- Vite
- `qrcode` for local QR matrix encoding
- `lucide-react` for consistent interface icons
- CSS custom properties and responsive CSS; no external runtime service is required

## Project structure

```text
index.html
src/
  main.jsx       # state model, payload builders, QR renderer, editor UI
  styles.css     # design tokens, shell effects, responsive layout
DESIGN.md        # implemented visual and interaction system
```

## Payload support

Payloads are generated locally. URL normalization adds `https://` to obvious bare domains. Wi-Fi and vCard payloads follow their standard text formats. Event payloads use a compact VEVENT representation. Media mode is intentionally named **Media Link**: it encodes a public URL, not the media bytes.

A browser-selected image, video, or PDF is not uploaded and is not represented with a temporary `blob:` URL. Large media cannot realistically fit inside a QR code. A real storage provider can be added later behind the media-link boundary without changing QR encoding.

## Export and privacy

QR generation, styling, logo handling, project saves, and exports happen in the browser. Saved projects use this browser's localStorage. No analytics, accounts, tracking, or automatic file uploads are included. PNG transparency is preserved; SVG is the preferred scalable format. JPEG is intentionally not offered because transparent output should not be flattened accidentally.

## Browser compatibility

Use a current Chrome, Edge, Firefox, or Safari release. Clipboard copy requires browser clipboard permissions and a secure or localhost context. File selection and canvas image export require normal browser file APIs. If a browser blocks clipboard access, the app reports that limitation instead of pretending the copy succeeded.

## Limitations

The current renderer validates design risks heuristically rather than claiming a successful camera decode. A production deployment can add a decoder library behind the same renderer abstraction for device-independent decode testing. Finder patterns are kept structurally recognizable and decorative effects remain outside the QR output.

## License

No license has been selected for this repository. Add one before public distribution.
