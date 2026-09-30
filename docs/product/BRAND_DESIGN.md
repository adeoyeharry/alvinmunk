# Brand & Design — alvinmunk

_The identity. Everything visual and verbal flows from here. Tokens that implement this live in [DESIGN_SYSTEM_TOKENS.md](./DESIGN_SYSTEM_TOKENS.md)._

_Verified against `globals.css` on 2026-06-15. Token values below are derived from the living `:root` block in `apps/web/src/app/globals.css`._

---

## 1. The idea in one breath

**Collect people, not points.**

alvinmunk is where a community recognizes its own. Someone you trust *vouches*
for you — they put their reputation behind yours — and that moment becomes a small piece
of on-chain art. The more people vouch for you, the brighter your **constellation**.

This is not a leaderboard of strangers grinding tasks. It's the warm, human opposite of
Galxe/POAP: **"someone saw you and backed you."**

## 2. The central metaphor — the Constellation 🌌

We lean fully into "Stellar" and the user's instinct for **galaxy / stars**:

-  Your passport is a **constellation**. Every person who vouches for you is a **star**.
-  A vouch link is **"someone lit a star for you — claim your half of the sky.""*
-  The generative crest (already deterministic per wallet) is reframed as a **personal
  constellation** that grows as your network grows.
-  The leaderboard is a **night sky of the most-connected**, not a number column.

Why it works: it unifies the product soul ("collect people") with the visual language
("stars/galaxy") and the chain ("Stellar"). One metaphor, end to end.

## 3. Color direction

Black-heavy cosmic base · **electric violet** primary (on-chain / verified moments) ·
**mint** secondary (earned) · **gold** accent (human) · **cyan** for connection depth · **lime** for the
sticker kit. Stars are cool-white dust over deep space.

| Role | Feel | Token (`globals\.css`) | Hex |
|------|------|---------------------|-----|
| **Deep space** (bg) | near-black, faint violet undertone | `--background: 270 40% 4%` | `#0B0512` |
| **Soft white** (text) | warm off-white, never pure `#FFF` | `--foreground: 260 30% 96%` | `#F4F1FA` |
| **Electric violet** (primary) | the chain, on-chain / verified moments | `--primary: 265 100% 66%` | `#9A52FF |
| **Mint** (secondary) | earned, growth, vouches landed | `--secondary: 160 84% 60%` | `#43EFB6` |
| **Gold** (accent) | human warmth, "a medal" | `--accent: 45 100% 60%` | `#FFCC33` |
| **Cyan** (tertiary) | sky / connection depth | `--tertiary: 190 100% 60%` | `#33DDFF` |
| **Lime** (sticker kit) | stickers, playful marks | `--lime: 90 100% 60%` | `#99FF33` |

Rule: **violet = the chain; mint = earned; gold = human; cyan = connection.** A page is mostly
black + soft-white with violet as the single primary CTA color; mint appears when a vouch is
*arned/claimed*, gold for human accents, cyan for sky/connection depth, and lime only in the
sticker kit. Don't let the accents outshine the primary.

## 4. Logo & marks

- **Wordmark:** "alvinmunk" in the display face; the dot/▲ of the mark is a small star.
- **Mark:** the shipped logo is a lime **p** glyph (`components/brand/logo.tsx`),
  drawn in the brand lime on the cosmic base. The favicon and PWA icon assets are
  derived from this same mark.
- The generative constellation crest (deterministic per wallet, from `GenesisStamp`)
  remains the **personal constellation** avatar inside the app — it is not the
  favicon or OG anchor.
- **Never** a generic blockchain cube/hexagon. The mark is always the lime *p* or a
  constellation.

## 5. Typography (humanist + warm, with a chain-mono)

- **Display / headings — Bricolage Grotesque** (variable, free): characterful, warm,
  modern. Carries the "human" feeling in heroes and card titles.
- **Body / UI — Inter** (variable): neutral, legible, excellent at small sizes.
- **Mono — Geist Mono / JetBrains Mono**: addresses, hashes, code, the dev docs.

Pairing rationale: a characterful humanist display + a neutral humanist body is the 2026
"warm product" pattern; mono signals the on-chain layer. Load via `next/font` (self-hosted,
no layout shift). Type scale lives in the tokens doc.

## 6. Motion — "the sky breathes" (Kaan)

- Easing: **ease-out, 180–280ms** for UI; nothing snaps.
-  The crest **breathes** (slow 4–6s opacity/scale pulse), stars **drift** with subtle
  parallax (respecting `prefers-reduced-motion` — then they're static).
- The signature moment: when a half-card is claimed, the two halves **merge with a light
  bloom** (not confetti) and a star "ignites" in the constellation.
- Library: **Motion** (`motion/react`). Keep it on `whileInView` for the landing and on
  discrete moments in the app — never ambient CPU burn.

## 7. Brand voice (Bri's 5 rules — canonical for ALL copy)

1. **Plain over clever.** "Vouch for someone you trust", not wordplay.
2. **Honest about trust.** Show the sybil caps/limits; trust is built by being transparent.
3. **Active & short.** "Read a score in one call." No passive constructions.
4. **No hype.** Banned: "revolutionary", "web3 magic", "next-gen". Write the concrete benefit.
5. **One voice, two audiences.** Consumer copy and dev copy share the same calm, human tone.

Signature lines:
-  Tagline: **"Collect people, not points."**
-  Hero: **"Someone vouched for you. Claim your half of the sky."**
-  Manifesto (footer): **"Reputation should name humans, not hoord points. Lit on Stellar."**
-  Dev intro: **"alvinmunk turns trust into a number other apps can read."**

## 8. Feelings & anti-patterns

| We feel like… | We are NOT… |
|---------------|-------------|
| being recognized, warmth, a night sky, a keepsake | a quest grind, an airdrop farm, a cold dashboard |
| a face/constellation first | a number/rank first |
| honest and calm | hype, urgency-bait, FOMO |

**Brand promise:** *Here, your reputation has a face — and the people who believe in you
become the stars you carry.*

## 9. Accessibility as brand (non-negotiable)

- Shape + position encode meaning, never color alone (crest vertices, star count).
- **Soft-white on deep-space meets AA; the violet primary CTA uses near-white foreground
  for AAA.**
-  Every generative crest ships `alt` text ("a 6-point constellation for @handle").
-  `prefers-reduced-motion` disables drift/breathing/bloom.

---

## 10. 2026 Immersive Refresh (implemented)

The metaphor is now **literal and interactive** — the constellation is a real 3D scene,
not just a 2D crest. This is the current shipped design language across landing + app.

**Hero = a live 3D constellation (WebGL / react-three-fiber).** Your star burns at the
center; everyone who vouched you orbits as a star, beamed to you. Hover lights a star
(tooltip: who · note · when), the field tilts to the cursor (parallax) and slowly
rotates. Alive even with an empty sky — orbital rings + drifting particles + a
parallaxing starfield — so a brand-new passport still feels cosmic. three.js is
lazy-loaded (`dynamic(ssr:false)`) so it never touches SSR or the marketing bundle.
Shared scene primitives: `components/brand/constellation-parts` (Star, OrbitRing, glow
sprite); the app hero (`constellation-3d`) and the marketing backdrop
(`constellation-backdrop`) share them so product and pitch are one world.

**Depth palette (added to the cosmic base, brand hues kept):** violet = chain, mint =
earned, gold = human, **a cyan `--tertiary` for sky/connection depth**. New surface system:
glassy translucent `--surface` panels with hairline borders + inner highlight, a slow
**aurora** gradient mesh, and a faint technical **grid** (the "engineered" chain-site motif), masked to fade.

**Interactive primitives (`components/fx`, Magic-UI language, zero heavy deps):**
- **BorderBeam** — a light particle traveling a rounded border (`offset-path`); marks
  live primary CTAs on the landing and app surfaces.
- **NumberTicker** — count-up for XP / USDC / stats (eases in on scroll).
- **AuroraText / ShinyText** — kinetic gradient headline + shimmering eyebrows.

**Typography:** display = Bricolage Grotesque, fluid `.display-hero`
(`clamp(2.75rem,7vw,5.5rem)`, tight tracking) for heroes; `.eyebrow` uppercase kicker
above headings (chain-site rhythm); body Inter; mono for addresses/code.

**Still honors §9 accessibility:** `prefers-reduced-motion` calms autonomous motion(rotation/drift/ticker) while keeping cursor parallax; faces/shapes over numbers holds.
