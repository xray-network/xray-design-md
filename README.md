# XRAY Design System

XRAY/Network is a **multi-blockchain mini app hub** by xray.network — a single shell that hosts a catalog of crypto mini apps, backed by a **crypto API provider** (a unified set of on-chain data APIs across multiple chains) and a **mini app builder** for composing new apps on top of those APIs. The design language is **content-first finance**: a quiet canvas where balances, addresses, and data tables are the subject, the UI recedes into hairline-bordered panels, and a single electric blue carries every action. XRAY lets the *data* — token tickers, deltas, geometric account avatars — be the color, the same way in either theme.

**Key Characteristics:**
- Pure-black immersive dark theme (`#000` -> `#0e0e18` -> `#1f2937`) — UI recedes, data leads
- XRAY Blue (`#1940ed`) as the singular brand accent — functional, never decorative
- Green (`#15e4a3`) as the "do-it" color — send, receive, online, success
- Satoshi Variable for all UI; DM Mono for addresses, hashes, and token labels
- Capsule geometry everywhere — `100px` pills for buttons/chips/rows, `50%` for avatars
- **Flat on dark**: 1px hairline borders do the elevation work, not shadows (light mode adds a soft card shadow)
- The four-segment geometric "pie" account avatar is the signature brand mark
- No emoji, no gradients, no photography, no illustration — information design only
- **Two themes** — dark and light — switchable via `<html data-theme="…">`

---

## 1. Color Palette & Roles

### Primary Brand
- **XRAY Blue** (`#1940ed`): Primary accent — CTAs, active nav, selected chips, the wordmark dot
- **Pure Black** (`#000000`): Root canvas, deepest layer
- **Panel** (`#0e0e18`, gray-950): Cards, panels, sidebar interior
- **Chip** (`#1f2937`, gray-800): Selected chips, gray buttons, icon tiles

### Text
- **White** (`#ffffff`): `--fg-1`, primary text and headings
- **Silver** (`#d1d5db`, gray-300): `--fg-2`, secondary text
- **Slate** (`#6e758d`, gray-500): `--fg-3`, meta and muted labels
- **Deep Slate** (`#55556d`, gray-600): `--fg-4`, footer / `id:` low-contrast meta

### Semantic
- **Green** (`#15e4a3`): `--success` — send, receive, online dot, success shield
- **Red** (`#fa2c37`): `--danger` — `preview` testnet tag, destructive, dangerous deltas
- **Orange** (`#f85e08`): chain identity (NIGHT token), avatar segments
- **Yellow** (`#f0b000`): `--warning` — caution, BTC accent, stake-pool saturation

### Surface & Border
- **Hairline** (`#1e2232`, gray-900): `--border` — the 1px panel border, near-invisible on black
- **Strong Border** (`#1f2937`, gray-800): `--border-strong` — input pills, focus
- **Soft Divider** (`rgba(255,255,255,0.06)`): `--border-soft` — dividers inside chips

### Shadows (rare — see §6)
- **Menu** (`rgba(0,0,0,0.5) 0px 4px 12px`): dropdowns, popovers
- **Modal** (`rgba(0,0,0,0.6) 0px 16px 40px`): dialogs, overlays

---

## 2. Typography Rules

### Font Families
- **Sans (UI / display)**: `Satoshi Variable`, fallback `Satoshi, -apple-system, BlinkMacSystemFont, system-ui, sans-serif`
- **Mono**: `DM Mono`, fallback `Fira Mono, ui-monospace, "SF Mono", Menlo, monospace`

### Hierarchy

| Role | Font | Size | Weight | Line Height | Notes |
|------|------|------|--------|-------------|-------|
| Page Heading | Satoshi | 30px | 700 | 1.0 | `-0.01em` tracking |
| Section Heading | Satoshi | 24px | 700 | 1.1 | |
| Card Title | Satoshi | 18px | 700 | 1.2 | |
| Body | Satoshi | 16px | 500 | 1.4 | Standard body & button label |
| Body Bold | Satoshi | 16px | 700 | 1.4 | Emphasis |
| Label | Satoshi | 14px | 500 | 1.3 | Secondary labels |
| Meta | Satoshi | 14px | 500 | 1.3 | `#6e758d` muted metadata |
| Meta Tiny | Satoshi | 12px | 500 | 1.3 | Footer, legal |
| Token Label | DM Mono | 20.57px | 500 | 1.1 | Uppercase, `0.058em` tracking |
| Address | DM Mono | 14px | 500 | 1.3 | Truncated `addr1q…azf5ek` |
| Balance Numeric | Satoshi | 40–48px | 900 | 1.0 | Integer big; fraction drops to ~0.55em |

### Principles
- **Weight contrast over size variation**: most text is 500 (medium) or 700 (bold); 900 (black) is reserved exclusively for balance numerics. 400 is for dense table values.
- **Mono is for machine data**: addresses, tx hashes, color tokens, and `id:` fields use DM Mono with wide uppercase tracking — a systematic "on-chain" voice distinct from content.
- **The price-tag numeral**: balances render the integer in Satoshi Black, then the decimal fraction drops to ~55% size and a muted gray (`1,252,251`**`.254221`** `ADA`). The ticker follows, uppercase, small.
- **Compact and functional**: this is a dApp, not a magazine. Line-heights stay tight; headings sit at `line-height: 1`.

---

## 3. Component Stylings

### Buttons (all capsules — `100px` radius, `40px` tall)
- **Primary**: `#1940ed` bg, white text — CTAs, active nav
- **Gray**: `#1f2937` bg, white text — secondary actions
- **Outline**: transparent bg, `1px solid #1e2232` border, white text
- **Success**: `#075c42` bg, `#15e4a3` text — Receive / confirm
- Padding `0 18px`; hover lifts the action color one step (`blue-500 -> blue-400`); press goes one step darker (`-> blue-600`)

### Cards & Panels
- Background `#0e0e18`; radius `16–20px`; `1px solid #1e2232` hairline border
- **No drop shadow by default** — the border defines the card
- Hover (interactive cards): border brightens to `#1f2937`

### Inputs
- Pill fields: transparent bg, `1px solid #1e2232`, `100px` radius, `40px` tall (matches buttons)
- Focus: border steps up to `#374151` (gray-700)
- Leading icon in `#6e758d`; trailing unit/meta in DM Mono

### Account Chip & Asset Row
- `40px` (chip) / `60px` (asset row) tall pills; selected state fills `#1f2937`, idle is transparent
- Avatar at left, mono ticker/address, balance right-aligned, delta badge or status dot trailing

### Navigation
- Top nav: a row of capsule pills (`Default` / `Select` / `Small Gray`) — never icon-only
- Left rail (~265px): wordmark + `preview` tag, search, primary CTA, account list, mini-app launcher grid, footer links
- Mini-app icons: `60×60` (`44.76` on the rail) `#1f2937` tile, `16.66px` radius, **6px `#1940ed` strip across the top edge**, white glyph centered

---

## 4. Layout Principles

### Spacing System
- Base unit: **4px**
- Scale: 4, 8, 12, 16, 20, 24, 32, 40, 48, 64 (`--space-1` … `--space-16`)

### Grid & Container
- Sidebar (fixed ~265px) + main content canvas filling the remainder
- The whole app is wrapped in a `20px`-radius panel inset from a pure-black frame — "panel inside the void"
- Asset rows `56–60px` tall, `8px` apart; main content gutter `16px` from the sidebar

### Whitespace Philosophy
- **Dark compression**: content is packed densely — the black background provides visual rest between elements without large gaps. Every pixel serves the data, not breathing room.

### Border Radius Scale
- **8px** (`--radius-sm`): small swatches
- **12.43px** (`--radius-md`): rail icon tiles (exact)
- **16.66px** (`--radius-lg`): mini-app tiles (exact)
- **20px** (`--radius-xl`): cards, panels, sidebar
- **100px** (`--radius-pill`): buttons, chips, address pills, asset rows
- **50%**: avatars, status dots

---

## 5. Depth & Elevation

| Level | Treatment | Use |
|-------|-----------|-----|
| Base (0) | `#000000` background | Root canvas |
| Surface (1) | `#0e0e18` + `1px #1e2232` border | Cards, panels, sidebar |
| Chip (1) | `#1f2937` fill, no border | Selected chips, gray buttons |
| Menu (2) | `rgba(0,0,0,0.5) 0px 4px 12px` | Dropdowns, popovers |
| Dialog (3) | `rgba(0,0,0,0.6) 0px 16px 40px` | Modals, overlays |

**Shadow Philosophy**: XRAY is **flat on dark**. Unlike most dark systems it leans on *borders*, not shadows, for everyday elevation — the `1px` gray-900 hairline is enough to lift a card against pure black. Shadows appear only on truly floating surfaces (menus, modals). There is no backdrop-blur and no alpha-overlay dimming; dim states use a flat darker fill.

**Theming**: dark is the brand-primary default; **light is opt-in** via `<html data-theme="light">`. Every component re-themes through the semantic tokens. Light intentionally diverges in two ways — it **permits a soft card shadow** (`--shadow-card`, since hairlines vanish on white) and shifts blue/green/red/yellow to **darker scale steps** for contrast. Full token map and rationale live in `DESIGN.md` §5a.

---

## 6. Do's and Don'ts

### Do
- Use pure-black backgrounds (`#000` -> `#0e0e18` -> `#1f2937`) — depth through shade
- Apply XRAY Blue (`#1940ed`) only for actions, active states, and the brand dot — one blue element per region
- Use Green (`#15e4a3`) for the functional "do-it" role: send, receive, online, success
- Pill everything — `100px` for buttons/chips/rows, `50%` for avatars
- Let borders carry elevation; reserve shadows for menus and modals
- Use DM Mono for all machine data (addresses, hashes, tokens, `id:`)
- Render balances with the price-tag numeral (big integer, dropped fraction)

### Don't
- Don't use Blue decoratively or as a background wash — it's functional only
- Don't add colored left-border accent cards, multi-stop gradients, or glows
- Don't introduce photography, illustration, textures, or patterns — none exist in the kit
- Don't use emoji, Unicode glyphs-as-icons, or filled (solid) heroicons
- Don't use thin/subtle shadows on cards — borders do that job; shadows are for overlays
- Don't relax line-heights — XRAY type is compact; headings sit at `line-height: 1`

---

## 7. Iconography

See `ICONOGRAPHY.md` for the full catalogue.

- **System icons**: Heroicons **outline** @ 24×24, ~1.5px stroke, `#fff` on dark. Copied locally to `assets/heroicons/`.
- **Product icons** (Wallet, Stake, Assets…): branded `60×60` tiles — `#1f2937` bg, `16.66px` radius, **6px `#1940ed` top strip**, white glyph. Glyphs in `assets/app-icons/`.
- **Account avatars**: `40×40` round, four hard-edged geometric segments in brand colors `{ blue, orange, yellow, pink, green }` — the signature XRAY mark in miniature.
- **No emoji.** The only decorative Unicode is the middle dot in `Privacy Policy · Terms of Service`.

---

## 8. Agent Prompt Guide

### Quick Color Reference
- Background: Pure Black (`#000000`)
- Surface: Panel (`#0e0e18`)
- Chip: (`#1f2937`)
- Text: White (`#ffffff`) / Slate meta (`#6e758d`)
- Accent: XRAY Blue (`#1940ed`)
- Action: Green (`#15e4a3`)
- Border: Hairline (`#1e2232`)
- Error: Red (`#fa2c37`)

### Example Component Prompts
- "Create a card: `#0e0e18` bg, `20px` radius, `1px solid #1e2232` border, no shadow. Title 18px Satoshi 700 white; meta 14px 500 `#6e758d`."
- "Design a primary button: `#1940ed` bg, white text, `100px` radius, `40px` tall, `0 18px` padding, 16px Satoshi 500. Hover -> `#3f5ff0`, press -> `#0f2fbf`."
- "Build a balance numeral: integer in Satoshi Black 48px white; fraction at 0.55em `#9ca3af`; ticker 18px 700 `#6e758d` uppercase, trailing."
- "Create an account chip: `40px` pill, transparent idle / `#1f2937` selected. 40px 4-segment avatar, mono address, balance, trailing status dot `#15e4a3`."
- "Make a mini-app tile: `60×60`, `#1f2937` bg, `16.66px` radius, `6px #1940ed` strip on the top edge, centered white glyph."

### Iteration Guide
1. Start with `#000` — everything lives on pure black
2. Borders before shadows — a `1px #1e2232` hairline defines every card
3. Pill everything — `100px` buttons/chips, `50%` avatars
4. Blue for action, green for "do-it" — one accent element per region
5. DM Mono for machine data; the price-tag numeral for balances
6. Let the data be the color — the UI stays achromatic

---

## Index

- `README.md` — _you are here_
- `SKILL.md` — agent skill manifest (cross-compatible with Claude Code)
- `ICONOGRAPHY.md` — icon system notes
- `colors_and_type.css` — tokens (palette, semantic vars, type roles, radii, spacing, shadow, motion)
- `fonts/` — `Satoshi-Variable.ttf`
- `assets/` — `xray-logo.svg`, `xray-logo-white.svg`, `xray-mark.png`, `heroicons/` (outline 24×24), `app-icons/` (Wallet, Stake, Builder, Wiki, Faucet, Pad, Swap)
- `preview/` — Design-System tab cards (color scales, type specimens, components)
- `components/` — exported React components (consumable via `window.XRAYDesignSystem_b0c12a`). Each has a `.jsx` (source), `.d.ts` (types), and an `@dsCard` `.html` preview: `AccountAvatar`, `AssetRow`, `BalanceCard`, `Button`, `PaymentForm`, `Tag`.

---

## Caveats

- **Codebase not provided.** Components are cosmetic recreations. Spacing/colors match; production data flows are mocked.
- **DM Mono** is loaded from a CDN. Attach a TTF if you need a self-contained build.
- **Heroicons** are used at v1 (outline). For the most accurate stroke metrics, prefer `https://unpkg.com/heroicons@1.0.6/...`.
