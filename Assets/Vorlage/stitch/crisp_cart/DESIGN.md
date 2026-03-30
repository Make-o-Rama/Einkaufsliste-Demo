# Design System Strategy: The Digital Greenhouse

## 1. Overview & Creative North Star
The "Creative North Star" for this design system is **The Digital Greenhouse**. 

This vision moves beyond the sterile, utilitarian nature of typical shopping lists to create an experience that feels organic, airy, and hyper-organized—much like a high-end botanical catalog. We are rejecting the "standard app" aesthetic characterized by heavy borders and rigid grids. Instead, we embrace **Soft Structuralism**: using tonal shifts, generous white space, and intentional asymmetry to guide the eye. By layering semi-transparent "glass" surfaces over a mint-tinted base, we create an environment that feels fresh and breathable, turning the mundane chore of grocery shopping into a moment of calm, editorial clarity.

## 2. Colors: Tonal Depth vs. Structural Lines
This system relies on a sophisticated "Mint & Mist" palette to define hierarchy. 

### The "No-Line" Rule
To maintain a premium, editorial feel, **1px solid borders for sectioning are strictly prohibited.** Boundaries must be defined through background color shifts. For example, a list of items should sit on a `surface-container-low` (#eff5f0) section which itself rests on the global `surface` (#f6faf6). This creates "implied containers" that feel integrated rather than partitioned.

### Surface Hierarchy & Nesting
Treat the UI as a series of stacked, organic layers. 
- **Base Layer:** `surface` (#f6faf6) – The canvas.
- **Sectioning:** `surface-container` (#e8f0ea) – Used for grouping related categories (e.g., "Produce").
- **Interactive Cards:** `surface-container-lowest` (#ffffff) – Used for individual list items to make them "pop" against the minty background.

### The "Glass & Gradient" Rule
Floating elements, such as a "Quick Add" FAB (Floating Action Button) or a navigation bar, must utilize **Glassmorphism**. Apply `surface` with 80% opacity and a `20px` backdrop-blur. This allows the vibrant greens of the content to bleed through, softening the interface. Use a subtle linear gradient for primary CTAs, transitioning from `primary` (#286a56) to `primary_dim` (#195e4b) to add "soul" and a tactile, premium weight.

## 3. Typography: Editorial Clarity
We use a dual-typeface system to balance character with extreme readability.

*   **Display & Headlines (Plus Jakarta Sans):** These are our "editorial anchors." Use `display-sm` for empty state headers and `headline-sm` (#2b3530) for category titles. The wide aperture of Jakarta Sans feels modern and inviting.
*   **Body & Labels (Work Sans):** Chosen for its exceptional legibility at small sizes on mobile screens. Use `body-lg` (#2b3530) for active list items and `label-md` (#57615c) for secondary metadata like "quantity" or "aisle number."
*   **Hierarchy Tip:** Create contrast not through size alone, but through weight and color. A `title-sm` in `on_surface` is far more authoritative than a `body-lg` in `on_surface_variant`.

## 4. Elevation & Depth: The Layering Principle
We convey importance through **Tonal Layering** rather than traditional drop shadows.

*   **Ambient Shadows:** When an element must float (e.g., a modal or a floating badge), use an extra-diffused shadow: `box-shadow: 0 12px 32px rgba(43, 53, 48, 0.06)`. By tinting the shadow with the `on_surface` color rather than pure black, the depth feels like natural ambient light in a bright room.
*   **The "Ghost Border" Fallback:** In high-density screens where accessibility requires more definition, use a "Ghost Border." Apply the `outline_variant` (#aab4af) at **15% opacity**. It should be felt, not seen.
*   **Depth through Blur:** Use the `surface_tint` to slightly colorize the background when a modal is active, creating a sense of "submerged" content.

## 5. Components

### Interactive Elements
*   **Checkboxes:** Avoid the standard square. Use a custom circular "organic" checkbox. 
    *   *Unchecked:* A `surface-container-highest` circle. 
    *   *Checked:* `primary` background with a `on_primary` checkmark.
*   **Buttons:**
    *   *Primary:* `primary` background, `xl` (1.5rem) roundedness. No border.
    *   *Secondary:* `secondary_container` background with `on_secondary_container` text.
*   **Input Fields:** Ghost-style inputs. No bottom line or box. Use a `surface-container-low` background with `md` roundedness. The label should use `label-sm` in `primary` when focused.

### Content Organization
*   **List Items:** Forbid divider lines. Use `spacing-4` (1rem) of vertical white space between items. When an item is "long-pressed" for reordering, lift it using the **Ambient Shadow** and transition the background to `surface-container-lowest`.
*   **Date Badges:** Use `tertiary_container` (#b7effb) for the background with `on_tertiary_container` text. Apply `full` roundedness to create a "pill" shape that stands out as a distinct data point.
*   **Quantity Steppers:** Use a semi-transparent `secondary_container` pill where the minus/plus icons are `on_secondary_container`.

## 6. Do's and Don'ts

### Do
*   **DO** use asymmetric margins (e.g., `spacing-6` on the left, `spacing-4` on the right) for headline elements to create a bespoke, editorial rhythm.
*   **DO** use "Micro-interactions." When a checkbox is tapped, trigger a subtle haptic pulse and a soft scale-up animation (1.05x).
*   **DO** leverage the `error_container` for "Out of Stock" alerts, but keep the `on_error_container` text legible.

### Don't
*   **DON'T** use 100% black (#000000) for text. Use `on_surface` (#2b3530) to maintain the soft, organic palette.
*   **DON'T** use "Standard" Material Design cards with heavy shadows. Use background color shifts to define the "card" area.
*   **DON'T** crowd the screen. If in doubt, add more `spacing-5` or `spacing-8`. The "Greenhouse" needs room to breathe.