---
name: AgentHub System
colors:
  surface: '#f8f9ff'
  surface-dim: '#cbdbf5'
  surface-bright: '#f8f9ff'
  surface-container-lowest: '#ffffff'
  surface-container-low: '#eff4ff'
  surface-container: '#e5eeff'
  surface-container-high: '#dce9ff'
  surface-container-highest: '#d3e4fe'
  on-surface: '#0b1c30'
  on-surface-variant: '#434655'
  inverse-surface: '#213145'
  inverse-on-surface: '#eaf1ff'
  outline: '#737686'
  outline-variant: '#c3c6d7'
  surface-tint: '#0053db'
  primary: '#004ac6'
  on-primary: '#ffffff'
  primary-container: '#2563eb'
  on-primary-container: '#eeefff'
  inverse-primary: '#b4c5ff'
  secondary: '#006c49'
  on-secondary: '#ffffff'
  secondary-container: '#6cf8bb'
  on-secondary-container: '#00714d'
  tertiary: '#784b00'
  on-tertiary: '#ffffff'
  tertiary-container: '#996100'
  on-tertiary-container: '#ffeedd'
  error: '#ba1a1a'
  on-error: '#ffffff'
  error-container: '#ffdad6'
  on-error-container: '#93000a'
  primary-fixed: '#dbe1ff'
  primary-fixed-dim: '#b4c5ff'
  on-primary-fixed: '#00174b'
  on-primary-fixed-variant: '#003ea8'
  secondary-fixed: '#6ffbbe'
  secondary-fixed-dim: '#4edea3'
  on-secondary-fixed: '#002113'
  on-secondary-fixed-variant: '#005236'
  tertiary-fixed: '#ffddb8'
  tertiary-fixed-dim: '#ffb95f'
  on-tertiary-fixed: '#2a1700'
  on-tertiary-fixed-variant: '#653e00'
  background: '#f8f9ff'
  on-background: '#0b1c30'
  surface-variant: '#d3e4fe'
  error-critical: '#ef4444'
  surface-light: '#f8fafc'
  surface-dark: '#0f172a'
  border-subtle: '#e2e8f0'
typography:
  display-lg:
    fontFamily: Inter
    fontSize: 30px
    fontWeight: '700'
    lineHeight: 36px
    letterSpacing: -0.02em
  headline-md:
    fontFamily: Inter
    fontSize: 24px
    fontWeight: '600'
    lineHeight: 32px
    letterSpacing: -0.01em
  headline-sm:
    fontFamily: Inter
    fontSize: 20px
    fontWeight: '600'
    lineHeight: 28px
  body-lg:
    fontFamily: Inter
    fontSize: 16px
    fontWeight: '400'
    lineHeight: 24px
  body-md:
    fontFamily: Inter
    fontSize: 14px
    fontWeight: '400'
    lineHeight: 20px
  label-md:
    fontFamily: Inter
    fontSize: 12px
    fontWeight: '600'
    lineHeight: 16px
    letterSpacing: 0.05em
  mono-code:
    fontFamily: jetbrainsMono
    fontSize: 13px
    fontWeight: '400'
    lineHeight: 20px
rounded:
  sm: 0.25rem
  DEFAULT: 0.5rem
  md: 0.75rem
  lg: 1rem
  xl: 1.5rem
  full: 9999px
spacing:
  sidebar-width: 260px
  container-max: 1440px
  gutter: 1.5rem
  card-padding: 1.25rem
  stack-gap: 1rem
---

## Brand & Style

The design system is engineered for **AgentHub**, a high-performance administrative interface for managing AI agents and operational data. The brand personality is **Professional, Analytical, and Dependable**. It prioritizes data density without sacrificing legibility, ensuring that operations teams can monitor complex systems with minimal cognitive load.

The chosen style is **Corporate / Modern** with a focus on functional clarity. It utilizes a sophisticated neutral palette (Slate) to ground the interface, while using vibrant semantic accents to signal system status. The aesthetic is characterized by:
- **Functional Minimalism:** Removing unnecessary decorative elements to focus on data.
- **Subtle Depth:** Using soft shadows and tiered backgrounds rather than heavy borders.
- **Soft Precision:** Balancing technical rigor with approachable rounded corners (`rounded-lg` and `rounded-xl`) to reduce the "industrial" feel of traditional admin panels.
- **Native Dark Mode:** A first-class dark theme designed for long-duration monitoring, reducing eye strain while maintaining semantic color integrity.

## Colors

The color palette is built on a foundation of **Slate (Neutral)** to provide a stable, professional backdrop that excels in both light and dark modes.

- **Primary (Corporate Blue):** Used for primary actions, navigation highlights, and active states. It represents the "system" and core functionality.
- **Secondary (Success Green):** Reserved for positive growth metrics, revenue figures, and "Active" status indicators.
- **Tertiary (Warning Amber):** Dedicated to non-critical alerts, pending states, and operational warnings.
- **Error (Critical Red):** Used sparingly for system failures, deleted actions, and critical log entries.

**Dark Mode Implementation:**
In dark mode, surfaces transition from `Slate-50` to `Slate-900`. Accents maintain their hue but may adjust in luminance to ensure AA accessibility against dark backgrounds. Borders should shift from a light gray to a semi-transparent white/slate blend to maintain structure without creating harsh lines.

## Typography

This design system uses **Inter** for all UI elements to ensure maximum legibility and a neutral, modern tone. The typographic scale is optimized for information-dense dashboards.

- **Headlines:** Use tighter letter-spacing and heavier weights to create a strong hierarchy.
- **Body Text:** Standard weight for readability. Use `body-md` (14px) as the primary size for tables and sidebar items to maintain high data density.
- **Labels:** Used for badges, chips, and small headers. These are often set in uppercase with slight tracking to differentiate them from body text.
- **Technical Content:** For stack traces and system prompts, **JetBrains Mono** is utilized to provide a clear, monospaced environment for debugging.

**Mobile Scaling:**
On mobile devices, `display-lg` should scale down to 24px (`headline-md`) to prevent text wrapping issues in metric cards.

## Layout & Spacing

The layout follows a **Fluid Grid** philosophy with fixed structural components. 

- **Sidebar:** A persistent 260px vertical navigation on desktop, collapsing to a hidden drawer on mobile.
- **Grid System:** A 12-column responsive grid. Metric cards typically span 3 columns (desktop), 6 columns (tablet), and 12 columns (mobile).
- **Rhythm:** An 8px (0.5rem) base unit governs all spacing.
- **Safe Areas:** Main content area uses a 24px (1.5rem) margin to ensure the UI feels airy despite the high volume of data.

**Breakpoints:**
- **Mobile (<768px):** Single column layout, full-width cards, fixed bottom or top navigation bar.
- **Tablet (768px - 1024px):** 2-column grid for metrics, sidebar transforms into an icon-only bar or overlay.
- **Desktop (>1024px):** Full 12-column grid, persistent sidebar, max-width container of 1440px to prevent excessive line lengths.

## Elevation & Depth

Visual hierarchy is achieved through a combination of **Tonal Layers** and **Ambient Shadows**.

- **Level 0 (Background):** `Slate-50` (Light) / `Slate-950` (Dark). The canvas of the application.
- **Level 1 (Cards/Sidebar):** Pure white (Light) / `Slate-900` (Dark). These elements use a very soft shadow (`0 1px 3px rgba(0,0,0,0.1)`) to appear slightly lifted.
- **Level 2 (Dropdowns/Popovers):** Higher elevation with a more pronounced shadow to indicate interactivity.
- **Level 3 (Modals):** These sit on a semi-transparent backdrop (`Slate-900/50`). They use the largest shadow blur to represent maximum focus.

**Borders:**
Instead of heavy shadows, the system uses low-contrast outlines (`border-slate-200` in light mode, `border-slate-800` in dark mode) to define element boundaries cleanly.

## Shapes

The shape language is defined as **Rounded**, providing a soft but professional geometry.

- **Standard Elements:** Buttons, Input Fields, and Checkboxes use `rounded-lg` (0.5rem).
- **Large Elements:** Cards, Modals, and Main Sidebar containers use `rounded-xl` (1rem).
- **Status Indicators:** Badges and Chips use a full "Pill" shape (9999px) to clearly distinguish them from interactive buttons.

This consistency in rounding ensures the interface feels cohesive and modern, softening the sharp edges of data-heavy tables and logs.

## Components

### Buttons & Actions
- **Primary:** Solid Blue-600 background with white text. High contrast.
- **Secondary/Ghost:** Slate-100 background or just a border. Subtle interaction for less critical tasks.
- **Action Menu (⋮):** A 32x32px ghost button that triggers a floating menu.

### Tables
- **Header:** Slate-100 background, `label-md` typography, sticky positioning.
- **Rows:** Subtle hover state (`bg-slate-50`). Borders only on the bottom of cells.

### Badges (Status)
- **Active:** Green background (low opacity) with deep green text.
- **Inactive/Error:** Red background (low opacity) with deep red text.
- **Warning:** Amber background (low opacity) with deep amber text.

### Metric Cards
- Should feature a top-accent bar or a tinted icon container (20% opacity of the semantic color) to categorize the metric (e.g., Green icon for Revenue).

### Modals
- Centered layout, max-width of 600px for details, 800px for logs/traces.
- Header includes a clear "Close" icon and a title in `headline-sm`.

### Sidebars
- Use `nav-link` components with 12px padding and 8px gap between icon and text. Active states use a subtle left-border or light blue background tint.
