---
name: PulseLog Kinetic Mono
fontOverride: "'Roboto Mono', monospace"
colors:
  dark:
    bg: '#090916'
    surface: '#181824'
    surface-raised: '#242430'
    advisory-bg: '#2A1A1A'
    text-primary: '#F5F5FE'
    text-secondary: '#9B9BA6'
    border: '#30303B'
    accent-primary: '#FF5A36'
    accent-success: '#10B981'
    accent-info: '#5FD6F1'
    accent-error: '#FFB4AB'
  light:
    bg: '#F3F6F9'
    surface: '#FFFFFF'
    surface-raised: '#EEEEEF'
    advisory-bg: '#FFF0EB'
    text-primary: '#17212F'
    text-secondary: '#5A6578'
    border: '#E3E4E6'
    accent-primary: '#FF5A36'
    accent-success: '#10B981'
    accent-info: '#00A0BA'
    accent-error: '#93000A'
typography:
  font-family: "'Roboto Mono', monospace"
  display-lg:
    fontSize: 32px
    fontWeight: 700
    lineHeight: 40px
    letterSpacing: -0.5px
  display-lg-mobile:
    fontSize: 26px
    fontWeight: 700
    lineHeight: 34px
    letterSpacing: -0.25px
  headline-metric:
    fontSize: 20px
    fontWeight: 700
    lineHeight: 28px
  headline-section:
    fontSize: 18px
    fontWeight: 700
    lineHeight: 26px
  body-default:
    fontSize: 14px
    fontWeight: 400
    lineHeight: 22px
  label-button:
    fontSize: 13px
    fontWeight: 600
    lineHeight: 18px
  label-micro:
    fontSize: 10px
    fontWeight: 600
    lineHeight: 14px
    letterSpacing: 1.8px
rounded:
  card: 10px
  input: 10px
  button: 10px
  pill: 9999px
spacing:
  xs: 0.5rem      # 8px
  sm: 0.75rem     # 12px
  md: 1.25rem     # 20px (grid gutter)
  lg: 1.5rem      # 24px (card padding & mobile outer margin)
  xl: 3.5rem      # 56px (section rhythm)
dimensions:
  container-max: 1120px
  button-primary-height: 48px
  input-height: 44px
  icon-button-size: 40px
  progress-bar-height: 8px
---

# PulseLog Kinetic Mono — Design Specification

## 1. Visual Philosophy
Airy, tactical, data-first terminal aesthetic combining flat surface contrast (`1px solid` borders, zero blurry drop shadows) with generous breathing room (`56px` section rhythm, `24px` card padding, `20px` grid gutter, max 2–3 cards per row).
- **Desktop Dark Mode** screenshots live in `design/`.
- **Light Mode** and **Mobile (375px)** layouts are derived directly from the token table above.

## 2. Strict Typography Rule
Every element across the entire interface (`h1`–`h6`, `p`, `button`, `input`, `table`, `span`) uses **`'Roboto Mono', monospace`**.

## 3. Component Rules
- **Primary CTA Button:** Background `#FF5A36`, text `#FFFFFF`, border-radius `10px`, height `48px`, font `13px/600`.
- **Ghost / Secondary Button:** Transparent fill, `1px solid` border (`#E3E4E6` light / `#30303B` dark), text primary ink, border-radius `10px`, height `44px`.
- **Icon Button:** Pill-shaped (`9999px`), `40px × 40px`.
- **Cards:** `24px` internal padding, `10px` border radius, `1px solid` border (`#FFFFFF` with `#E3E4E6` in light; `#181824` with `#30303B` in dark).
- **Advisory & 14-Day Calibration Box:** `10px` border radius, `16px` padding, background `#FFF0EB` (light) / `#2A1A1A` (dark), bordered by `1px solid #FF5A36`.
- **Form Inputs:** Height `44px`, `10px` border radius, `1px solid` border, focus border switches to `#FF5A36`.
- **Progress Bars:** Height `8px`, border radius `9999px`, track `#E3E4E6` (light) / `#242430` (dark), fill `#FF5A36` or `#10B981`.