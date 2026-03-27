# Design System Specification: Power Express
## 1. Overview & Creative North Star: "The Kinetic Monolith"
This design system is built upon the **Kinetic Monolith** philosophy. It represents the intersection of raw industrial power and clean, futuristic precision. Unlike standard energy platforms that rely on cluttered dashboards, this system treats data as art. 
The aesthetic is driven by **intentional asymmetry** and **tonal depth**. We break the "template" look by using **Display** typography that commands the screen and overlapping elements that suggest a three-dimensional interface. The experience should feel like a high-end physical product—weighty, premium, and impossibly smooth.
---
## 2. Color Strategy & Surface Logic
Our palette moves away from flat "web colors" toward a multi-dimensional environment that mimics the glow of high-tech hardware in a dark room.
### The "No-Line" Rule
**Explicit Instruction:** Do not use 1px solid borders for sectioning or containers. Structural boundaries must be defined solely through background color shifts (e.g. a `surface-container-low` card sitting on a `surface` background). This forces a more sophisticated, editorial use of space.
### Surface Hierarchy & Nesting
Treat the UI as a series of physical layers. We use **Surface Tiering** to create a natural sense of place:
- **Base Layer:** `surface` (#081020) – The deep, infinite void.
- **Sectioning:** `surface-container-low` (#0F1A2B) – For grouping related modules.
- **Actionable Cards:** `surface-container` (#142033) – The primary interaction layer.
- **Floating/Active Elements:** `surface-container-highest` (#1A263A) – To indicate immediate focus.
### The "Glass & Gradient" Rule
To achieve a premium futuristic polish, secondary actions and floating navigation should utilize **Glassmorphism**.
- **Formula:** `surface-variant` at 60% opacity + `backdrop-blur: 24px`.
- **Signature Textures:** Use a subtle linear gradient for primary buttons transitioning from `primary` (#0098F1) to a lighter blue `primary-container` (#5BBBF7) at a 135° angle. This creates a clean, luminous effect without overpowering the interface.
---
## 3. Typography: The Editorial Voice
We use **Space Grotesk** as the sole typeface across all text. No other typefaces.

**Google Fonts URL (use on every page):**
`https://fonts.googleapis.com/css2?family=Space+Grotesk:wght@300..700&display=swap`

### Type Scale

| Role | Element | Size (desktop) | Weight |
|------|---------|----------------|--------|
| Hero Title | `h1` (hero) | 72–88px (`clamp`) | 700 Bold |
| Section Heading | `h2` | 32–40px | 700 Bold |
| Sub-heading | `h3` | 20–28px | 600 Semibold |
| Component Title | `h4` | 16–20px | 600 Semibold |
| Body Copy | `p`, `span` | 16–18px | 300 Light |
| Navigation | `nav` links | 14–16px | 300 Light |
| Footer | `footer` text | 14–16px | 300 Light |

### Heading Rules
*   **Color system:** All headings default to `color: white`. Apply a single `<span class="text-primary">...</span>` to the last or most significant word for a white + blue accent hierarchy. This is the standard visual pattern across every page.
*   **No trailing periods:** Headings and titles must not end with a full stop. Question marks and other punctuation used for meaning are permitted.
*   **CSS override (applied on every page):**
    ```css
    h1, h2, h3, h4, h5, h6 { font-family: 'Space Grotesk', sans-serif !important; color: white; }
    h1, h2 { font-weight: 700; }
    h3, h4, h5, h6 { font-weight: 600; }
    body { font-weight: 300; }
    nav, footer { font-weight: 300; }
    ```
*   **Body, Navigation & Footer — Space Grotesk (Light 300):** Base weight 300 for all body copy, nav links, footer text, button labels, captions, data chips, and form fields. Use 500–600 for inline emphasis, 700 for uppercase labels/badges.
*   **Tailwind config:** `fontFamily.headline = ["Space Grotesk", "sans-serif"]` · `fontFamily.body = fontFamily.sans = fontFamily.label = ["Space Grotesk", "sans-serif"]`

### Testimonial Images
*   **Real human photographs only.** Do not use illustrated, cartoon, or AI-generated avatar images in testimonial sections. Use high-quality, professional, realistic headshots with consistent lighting, neutral backgrounds, and forward-facing framing. Source from Unsplash or equivalent royalty-free libraries.
---
## 4. Elevation & Depth: Tonal Layering
Traditional drop shadows are forbidden. We use light to define space, not ink.
*   **The Layering Principle:** Depth is achieved by stacking. A `surface-container-lowest` card placed on a `surface-container-low` background creates a carved out look. Conversely, a higher-tier surface creates a lifted look.
*   **Ambient Shadows:** For floating elements (Modals/Popovers), use a subtle shadow.
    *   **Value:** `0px 24px 48px -12px rgba(0, 152, 241, 0.08)`  
*   **The "Ghost Border" Fallback:** If accessibility requires a stroke, use `outline-variant` at **15% opacity**. It should feel like a faint reflection on the edge of a glass pane, not a drawn line.
---
## 5. Component Guidelines
### Buttons (The "Power Cells")
- **Primary:** Solid fill (`primary` #0098F1). `borderRadius: md` (0.5rem). No border. Label in `on-primary` (white).
- **Secondary:** `surface-container-highest` fill with a `secondary` ghost-border (15% opacity).
- **Tertiary:** Text-only in `secondary`, using `1.5` (0.5rem) spacing for icon-padding.
### Cards & Modules
- **Rule:** Forbid divider lines.
- **Layout:** Use `spacing-8` (2.75rem) between internal card elements to let the content breathe. 
- **Interaction:** On hover, a card should shift from `surface-container` to `surface-container-high`. Do not move the card's position; only change the tonal value.
### Data Chips
- **Status:** Use `secondary-container` (#65D7CF) for "Charging/Active" states. 
- **Shape:** `full` (9999px) pills. Typography must be `label-sm` (0.6875rem) with `font-weight: 700`.
### Technical Input Fields
- **Base:** `surface-container-lowest` fill. 
- **Active State:** A 1px `ghost-border` using `primary` (#0098F1) to mimic active focus.
- **Labels:** Always use `label-md` floating above the field, never placeholder-only.
---
## 6. Do’s and Don’ts
### Do:
- **Do** embrace "Extreme Breathing Room." If you think there is enough whitespace, add 20% more.
- **Do** use `primary-fixed-dim` (#5BBBF7) for secondary data visualizations. It is more legible against dark backgrounds than the pure primary blue.
- **Do** overlap images or text across different surface tiers to break the "grid-block" feel.
### Don't:
- **Don't** use pure #000000. Use `surface` (#081020) to keep the "ink" from feeling dead.
- **Don't** use 100% opaque borders. They create "visual noise" that destroys the premium, seamless feel.
- **Don't** use standard "Material" blue for links. Every interactive element must stem from the Primary Blue or Teal tokens.
- **Don't** use "Drop Shadows" on cards that are resting on the background. Use tonal shifts instead.
---
## 7. Spacing Scale (The "Rhythm")
Use these tokens to maintain a "Stripe-like" mathematical rigor:
- **Macro-Spacing (Sections):** `20` (7rem) or `24` (8.5rem).
- **Micro-Spacing (Components):** `3` (1rem) or `4` (1.4rem).
- **Nesting Gap:** Always use `1.5` (0.5rem) when nesting a container inside another container.
*Director's Note: Every pixel should feel like it was placed by a watchmaker. If a component feels "standard," you haven't pushed the tonal layering far enough.*