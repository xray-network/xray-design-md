---
name: xray-design
description: Use this skill to generate well-branded interfaces and assets for XRAY/Network (multi-blockchain mini app hub — crypto API provider + mini app builder + mini app catalog), either for production or throwaway prototypes/mocks/etc. Contains essential design guidelines, colors, type, fonts, assets, and UI kit components for prototyping.
user-invocable: true
---

Read the `README.md` file within this skill, and explore the other available files.

If creating visual artifacts (slides, mocks, throwaway prototypes, etc), copy
assets out of `assets/` and load `colors_and_type.css` directly. Use the
exported React components in `components/` (the dark capsule-button + flat-on-dark
pattern) as building blocks.

If working on production code, the rules in `README.md` (palette, type roles,
radii, motion) can be lifted verbatim — they were extracted from the canonical
XRAY UI KIT figma.

**Key rules to internalize before designing:**
- Pure-black canvas (`#000`); panels at `gray-950` (`#0e0e18`); chips at
  `gray-800` (`#1f2937`). Borders are `gray-900` hairlines.
- `blue-500` (`#1940ed`) is the brand action color. Use sparingly.
- All buttons are capsules (`border-radius: 100px`). 40 px tall.
- Satoshi Variable everywhere; DM Mono for tokens, addresses, hashes. No other
  fonts.
- **No emoji.** No gradients. No background imagery. No drop shadows on default
  cards — borders do the elevation work.
- Account avatars are the brand mark: 40 round, 4 geometric segments in brand
  colors (use `AccountAvatar.jsx`).
- **Two themes**: dark is the default; light is opt-in via `<html data-theme="light">`.
  All component colors flow through semantic tokens, so both themes work
  automatically — never hardcode hex in a component. Light adds a soft
  `--shadow-card` and uses darker accent/status steps. See `DESIGN.md` §5a.
- Mini-app icons live in a 60 × 60 `gray-800` tile, `r 16.66`, with a 6 px
  `blue-500` strip at the top edge.

If the user invokes this skill without any other guidance, ask them what they
want to build or design, ask some clarifying questions (which surface — App or
Explorer? data shown? interactive or static?), and act as an expert designer
who outputs HTML artifacts _or_ production code, depending on the need.

**Files at a glance:**
- `README.md` — full design system documentation
- `ICONOGRAPHY.md` — icon catalogue & rules
- `colors_and_type.css` — drop-in CSS variables (palette, semantic, type,
  radii, spacing, shadows, motion)
- `fonts/Satoshi-Variable.ttf` — bundled. DM Mono loaded from Google Fonts CDN.
- `assets/heroicons/*.svg` — 35 outline icons (24 sq, ~1.5 stroke)
- `assets/app-icons/*.svg` — mini-app glyphs (wallet, stake, swap, builder,
  faucet, wiki, pad)
- `assets/xray-logo.svg`, `assets/xray-mark.png` — wordmark + small mark
- `preview/*.html` — design-system cards (foundations + components)
- `components/` — exported React components, reachable on
  `window.XRAYDesignSystem_b0c12a` once `_ds_bundle.js` is loaded:
  `AccountAvatar`, `AssetRow`, `BalanceCard`, `Button`, `Tag`. Each ships a
  `.jsx` source, a `.d.ts`, and an `@dsCard` `.html` preview.
