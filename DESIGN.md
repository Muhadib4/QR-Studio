# QR Studio Design System

## Product identity
QR Studio is a local-first QR signal encoder: part print terminal, part technical laboratory, and part compact design workstation. The editor is the product, so the interface prioritizes a live preview, short technical labels, visible reliability diagnostics, and fast controls over promotional navigation.

## Visual language
The signature `COMPOSITE` shell combines dark graphite surfaces, phosphor green highlights, mono readouts, faint grid/depth-map lines, subtle scanlines, and receipt-paper output surfaces. Visual effects are application-shell decoration only. They never enter exported QR output unless an explicit QR design setting changes the QR itself.

Visual modes are token-based: `COMPOSITE`, `CRT`, `RECEIPT`, `NIGHT VISION`, and `1-BIT`. The `VISUAL FX` setting changes shell decoration only. Reduced-motion users receive the same functionality without scanline and transition emphasis.

## Color system
 
| Token | Role | Default |
| --- | --- | --- |
| `--bg` | graphite application background | `#101413` |
| `--surface` | panels and modal surfaces | `#171d1b` |
| `--surface-2` | raised controls | `#202925` |
| `--line` | technical borders and separators | `#33413a` |
| `--ink` | readable primary text | `#eef3e9` |
| `--muted` | secondary technical labels | `#84928b` |
| `--phosphor` | primary action and success | `#b8ff64` |
| `--warn` | reliability warnings | `#efb96a` |
| `--danger` | failed diagnostics | `#ff7066` |

QR output colors are stored separately in design state, with solid, linear gradient, and transparent-background options.

## Typography, spacing, and grid
Primary UI text uses a clean system sans-serif. Technical labels, status readouts, payload previews, and metadata use a monospace stack. Long-form copy remains normal text-sized and readable; bitmap-like treatments are decorative only. Spacing uses compact 4–16px control increments, with 1px borders and a 10px workspace radius. The desktop grid is a 280px payload rail, flexible preview, and 300px customization rail. At 800px and below, the workspace becomes a preview-first mobile tab flow.

## QR workspace
The preview is the visual center and renders a real QR matrix from the `qrcode` encoder. The SVG renderer adds safe module shapes, finder eyes, gradients, transparent checkerboard preview, an optional local logo, quiet-zone padding, and export dimensions. Shell effects are never included in this SVG. The center stage includes non-output coordinate marks and restrained topology rings.

## Components and interactions
The header owns new/open/save/project actions, preset access, undo/redo, randomize, and shell settings. The left rail owns payload type and payload forms. The right rail owns module, color, background, reliability, frame, logo, and export controls. On mobile, tab buttons reveal one panel while keeping the preview immediately above it.

Controls use visible focus rings, minimum touch-friendly padding, short state transitions, and toast feedback instead of browser alerts. Presets modify actual QR settings, randomize selects from curated safe presets, and saved designs use localStorage. Project JSON is versioned and validated by product marker and expected top-level state before loading.

## Reliability and accessibility
The scan diagnostics panel reports measured foreground/background contrast, quiet zone, payload length, logo/ECC relationship, and background state. Warnings are explicit when a quiet zone is below four modules or a logo is active without H correction. The editor supports keyboard focus, semantic labels, color inputs, file pickers, reduced motion, and responsive layouts without horizontal overflow.

## Receipt, depth, datamosh, 1-bit, and night vision rules
Receipt mode changes shell tokens to thermal paper and dark ink. Depth-map contours are low-opacity decorative rings around—not over—the QR. CRT lines and noise are subtle and static. There is no continuous datamosh that could impair editing. 1-bit is reserved for shell contrast and selected QR presets. Night vision uses deep green-black surfaces and phosphor green. All of these are shell choices, not accidental QR output effects.
