---
name: PulseLog Kinetic Mono
colors:
  surface: '#12121e'
  surface-dim: '#12121e'
  surface-bright: '#383845'
  surface-container-lowest: '#0d0d19'
  surface-container-low: '#1a1a27'
  surface-container: '#1f1e2b'
  surface-container-high: '#292935'
  surface-container-highest: '#343441'
  on-surface: '#e3e0f2'
  on-surface-variant: '#e3beb6'
  inverse-surface: '#e3e0f2'
  inverse-on-surface: '#2f2f3c'
  outline: '#aa8982'
  outline-variant: '#5b403a'
  surface-tint: '#ffb4a3'
  primary: '#ffb4a3'
  on-primary: '#630f00'
  primary-container: '#ff5a36'
  on-primary-container: '#5a0c00'
  inverse-primary: '#b52603'
  secondary: '#4edea3'
  on-secondary: '#003824'
  secondary-container: '#00a572'
  on-secondary-container: '#00311f'
  tertiary: '#5fd6f1'
  on-tertiary: '#003640'
  tertiary-container: '#00a0ba'
  on-tertiary-container: '#003039'
  error: '#ffb4ab'
  on-error: '#690005'
  error-container: '#93000a'
  on-error-container: '#ffdad6'
  primary-fixed: '#ffdad2'
  primary-fixed-dim: '#ffb4a3'
  on-primary-fixed: '#3d0600'
  on-primary-fixed-variant: '#8c1900'
  secondary-fixed: '#6ffbbe'
  secondary-fixed-dim: '#4edea3'
  on-secondary-fixed: '#002113'
  on-secondary-fixed-variant: '#005236'
  tertiary-fixed: '#aaedff'
  tertiary-fixed-dim: '#5fd6f1'
  on-tertiary-fixed: '#001f26'
  on-tertiary-fixed-variant: '#004e5c'
  background: '#12121e'
  on-background: '#e3e0f2'
  surface-variant: '#343441'
typography:
  display-lg:
    fontFamily: Space Mono
    fontSize: 32px
    fontWeight: '700'
    lineHeight: 40px
    letterSpacing: -0.5px
  display-lg-mobile:
    fontFamily: Space Mono
    fontSize: 26px
    fontWeight: '700'
    lineHeight: 34px
    letterSpacing: -0.25px
  headline-metric:
    fontFamily: Space Mono
    fontSize: 20px
    fontWeight: '700'
    lineHeight: 28px
  headline-section:
    fontFamily: Space Mono
    fontSize: 18px
    fontWeight: '700'
    lineHeight: 26px
  body-default:
    fontFamily: Space Mono
    fontSize: 14px
    fontWeight: '400'
    lineHeight: 22px
  label-button:
    fontFamily: Space Mono
    fontSize: 13px
    fontWeight: '600'
    lineHeight: 18px
  label-micro:
    fontFamily: Space Mono
    fontSize: 10px
    fontWeight: '600'
    lineHeight: 14px
    letterSpacing: 1.8px
rounded:
  sm: 0.25rem
  DEFAULT: 0.5rem
  md: 0.75rem
  lg: 1rem
  xl: 1.5rem
  full: 9999px
spacing:
  gutter: 1.25rem
  margin: 1.5rem
  space-xs: 0.5rem
  space-sm: 0.75rem
  space-md: 1.25rem
  space-lg: 1.5rem
  space-xl: 3.5rem
---

## Brand & Style

This design system drives a gamified fitness, workout logging, and adaptive TDEE (Total Daily Energy Expenditure) calculation platform. The brand identity fuses clinical precision with the adrenaline of high-output athletic progression. It strips away illustrative fluff and gamified clutter in favor of an airy, tactical, data-first terminal aesthetic.

The target audience comprises analytical lifters, macro trackers, and data-driven athletes who value instant numerical readability, uncompromised speed during mid-workout logging, and algorithmic feedback over cartoonish streaks. The interface evokes a sense of calculated mastery, physical momentum, and rigorous clarity. 

Visually, the style merges technical brutalism with modern flat minimalism: strict monospaced typography, deliberate surface contrast instead of blurry drop shadows, high spatial breathing room, and sharp architectural borders paired with functional pill-shaped micro-elements.

## Colors

Visual hierarchy is established strictly through surface color contrast and targeted chromatic accents rather than elevation shadows.

### Light Theme
- **Page Background:** `#F3F6F9` (cool, expansive off-white canvas)
- **Card Surface:** `#FFFFFF` with a crisp structural border `1px solid #E3E4E6`
- **Advisory / Calibration Box:** `#FFF0EB` (low-saturation warm tint) with `#FF5A36` framing
- **Primary Ink:** `#17212F` (deep technical slate for maximum contrast)
- **Secondary Body:** `#5A6578` (muted slate for metadata and tertiary metrics)
- **Primary Brand Accent:** `#FF5A36` (high-velocity Coral Orange with guaranteed `#FFFFFF` contrast)
- **Success / Target Hit:** `#10B981` (Emerald Mint for caloric equilibrium, PRs, and targets met)

### Dark Theme (Default)
- **Page Background:** `#090916` (deep void navy-black)
- **Card Surface:** `#181824` with a defined border `1px solid #30303B`
- **Raised Pill Surface:** `#242430` (floating controls and interactive chips)
- **Advisory / Calibration Box:** `#2A1A1A` (warm charcoal-amber dark mode tint)
- **Primary Ink:** `#F5F5FE` (stark luminous off-white)
- **Secondary Body:** `#9B9BA6` (cool mid-tone slate for supporting labels)
- **Primary Brand Accent:** `#FF5A36` (retains identical hue for immediate brand recognition across themes)
- **Success / Target Hit:** `#10B981` (vivid neon-mint for clear status delta)

## Typography

The typography operates under an uncompromising rule: strict monospaced typesetting across every single interface layer. Space Mono serves as the unified mechanical foundation for headings, tabular readouts, body blocks, interactive buttons, navigation items, and micro telemetry.

- **Monospaced Metric Alignment:** Every numeric readout, timestamp, and macro breakdown maintains exact character cell widths, preventing layout shift during rapid entry or live timer increments.
- **Micro-Badges:** Rendered at `10px/600`, transformed to full uppercase with `1.8px` letter spacing to preserve legibility on low-profile pills and status tags.
- **Line Heights:** Generously proportioned relative to standard mono typefaces to maintain breathability and avoid vertical density fatigue.

## Layout & Spacing

The layout philosophy centers on open structure, generous breathing margins, and strict constraint caps. Content must never crowd the screen or stretch indefinitely.

- **Grid Architecture:** Responsive fluid grid with maximum density capped at **2 to 3 cards per row** on wide screens. Dashboard layouts lock to 1 column on mobile, 2 columns on tablet, and a strict 2 or 3 columns on desktop.
- **Section Rhythm:** Major vertical layout sections are divorced by a generous `56px` (`3.5rem`, `space-xl`) structural interval, establishing distinct thematic zones (e.g., TDEE Trends vs. Macro Distribution vs. Daily Logs).
- **Component Padding:** Standard cards employ `24px` (`1.5rem`, `space-lg`) internal padding across all edges. Compact data sub-cells use `12px` (`0.75rem`, `space-sm`).
- **Element Gaps:** Component grid systems enforce uniform `20px` (`1.25rem`, `gutter`) spacing horizontally and vertically.
- **Mobile Adaptations:** Outer margins scale down from `48px` on desktop to `24px` (`1.5rem`) on mobile devices.

## Elevation & Depth

This design system avoids blurry, multi-layer drop shadows. Depth and hierarchy are achieved purely through **planar contrast and crisp stroke delineations**:

- **Card Level:** Elevated strictly via surface background fills (`#FFFFFF` in light, `#181824` in dark) bordered by a precise, sharp `1px` outline (`#E3E4E6` in light, `#30303B` in dark).
- **Tertiary & Floating Elements:** Navigation overlays, floating segmented controls, and interactive pill filters sit on elevated surface tokens (e.g., `#242430` in dark mode) without drop shadows.
- **Advisory & High-Priority Boxes:** Highlighted via low-chroma tinted backdrops (`#FFF0EB` in light, `#2A1A1A` in dark) flanked by a distinct primary accent boundary.
- **Active State Interaction:** Buttons and interactive cards express state changes through immediate border illumination or background shifts, never downward shadow movement.

## Shapes

The geometric architecture balances a rigid structural grid with aerodynamic pill elements:

- **10px Radius (`rounded-xs` / `10px`):** Applied strictly to rectangular utility surfaces: content cards, text inputs, metric counters, calibration advisory boxes, and primary CTA buttons. This creates a grounded, mechanical profile.
- **Full Pill Radius (`9999px` / `rounded-full`):** Applied exclusively to transient and navigational micro-elements: floating navigation bars, filter tags, progress bar tracks, completion meters, and circular icon triggers.

## Components

### Primary CTA & Buttons
- **Primary CTA:** Background `#FF5A36`, text `#FFFFFF`, border-radius `10px`, height `48px`, font `Space Mono 13px/600`. Subtle brightness shift on hover; no drop shadow.
- **Ghost / Secondary Button:** Transparent fill, `1px solid` border (`#E3E4E6` light / `#30303B` dark), text color matches Primary Ink, border-radius `10px`.
- **Icon Button:** Pill-shaped (`rounded-full`), `40px` diameter, centered monospaced glyph or functional icon.

### Cards & Data Panels
- **Structure:** `24px` internal padding, `10px` border radius, `1px` border outline.
- **Content Flow:** Section titles styled with `18px/700`, leading directly into large metric values (`20px/700`) with metadata keys styled using secondary ink (`14px/400`).

### Advisory & Calibration Boxes
- **Structure:** `10px` border radius, `16px` padding, tinted background fill (`#FFF0EB` light, `#2A1A1A` dark), bordered by a `1px` stroke matching `#FF5A36`.
- **Content:** Instructional TDEE weight-smoothing warnings and caloric goal recommendations.

### Chips, Pills & Micro-Badges
- **Status Badges:** `9999px` border radius, padding `4px 10px`, typography `10px/600 uppercase` with `1.8px` letter spacing.
- **Target Hit Badge:** Background `#10B981` (or transparent with `#10B981` stroke), text `#FFFFFF` or glowing mint.

### Form Inputs & Number Fields
- **Container:** Height `44px`, `10px` border-radius, background matches card or surface token, `1px solid` border. Focus ring switches border directly to `#FF5A36` without outer glow.
- **Typography:** Numeric entry is locked to monospaced type for clean visual tabulation.

### Progress & Macro Distribution Bars
- **Track:** Height `8px`, border radius `9999px`, background `#E3E4E6` (light) or `#242430` (dark).
- **Fill:** Solid `#FF5A36` (caloric threshold) or `#10B981` (target achieved). Never use gradients.