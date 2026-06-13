# brief.md — The Lantern Keeper

## Product

**Name:** The Lantern Keeper
**Category:** Storybook / narrative showcase (bedtime story, storyboard, scene gallery)
**Register:** Brand — the interface IS the experience
**URL / file:** `index.html` (static single-page)

## Audience & Pressure

**User:** A reader, storyteller, or film-minded visitor arriving to experience a completed narrative.
**Pressure at arrival:** Curious, open, expectant. They want to feel the mood before they read the words. This is not a utilitarian surface — it is an atmosphere to enter.

## Core Artifact

The story itself — a boy who watches a lighthouse, loses his father to a dark sea, lights the lamp himself, and passes the light to the next keeper. Every visual decision must serve the emotional arc of that narrative.

**Artifact hierarchy:**
1. The full story (narrative text, read)
2. The scene-by-scene storyboard (visual breakdown, browse)
3. The scene detail panels (image + caption + cinematic notes, inspect)

## What the page holds

- Hero: title + subtitle + internal nav
- Full story text (long-form, 14 paragraphs, ~3200 words)
- 15 scene cards (responsive grid, thumbnail + number + title + tone + setting)
- Scene detail modal (generated image(s) + visual description + key narrative beat + camera direction)
- 6 visual theme cards (hands on glass, brass wheel, hand on shoulder, bell buoy, gold vs cold, the beam)
- Footer

## Color

**Mood:** Warm amber light in a cold dark sea. Gold fighting frost.

| Role | Hex | Usage |
|------|-----|-------|
| Surface | `#0b111e` | Page background — the deep dark |
| Surface-2 | `rgba(255,255,255,0.02–0.05)` | Card / section backgrounds |
| Text-primary | `#f0ede4` | Body, headings — warm cream |
| Text-muted | `rgba(240,237,228,0.4–0.5)` | Labels, meta, captions |
| Accent | `#fbbf24` | Gold light — section titles, hover borders, emphasis |
| Accent-dim | `rgba(251,191,36,0.3–0.5)` | Subtle accents, scene numbers, list markers |
| Border | `rgba(240,237,228,0.06–0.12)` | Card borders, dividers, nav pills |
| Hero-glow | `radial-gradient` at top | Lantern glow illusion — gold `rgba(217,119,6,0.12)` |

Depth via backdrop-blur on the modal overlay (`rgba(6,10,20,0.92)` + blur(8px)).

## Typography

| Role | Font | Weight | Size |
|------|------|--------|------|
| Display / hero | `Avenir Next / system sans-serif` | 600 | `clamp(2.2rem, 6vw, 3.6rem)` |
| Section headings | `Avenir Next / system sans-serif` | 600 | `clamp(1.4rem, 3vw, 2rem)` |
| Card titles | `Avenir Next / system sans-serif` | 600 | `1rem` |
| Story body | `Georgia / Times New Roman, serif` | 400 | `clamp(1rem, 1.4vw, 1.12rem)` |
| Meta / captions | `Avenir Next / system sans-serif` | 400–500 | `0.7–0.85rem` |
| Scene modal labels | `Avenir Next / system sans-serif` | 600 | `0.75rem` uppercase |

Body measure: `max-width: 700px` for story text (target ~65–75ch).

## Layout & Spacing

**Rhythm:** 4px/16px/36px (1/4/9 unit system from design philosophy).

| Token | Value | Where |
|-------|-------|-------|
| Section padding | `64px 0` | Story and themes sections |
| Container max | `960px` | Centered with `24px` sides |
| Card gap | `16px` | Scene grid |
| Card padding | `14px 16px 16px` | Scene card body |
| Modal body | `28px 32px 32px` | Inside modal |
| Section title bottom | `32px` | Below heading |

Hero: `70vh min` center-aligned, three radial gradients suggesting a lantern glow.

Scene grid: `repeat(auto-fill, minmax(260px, 1fr))` — responsive, min 260px cards.

## Scene cards

- Thumbnail: 16:9 aspect-ratio, `object-fit: cover`, opacity 0.85, scales 1.05 on hover
- Card: `border-radius: 12px`, `background: rgba(255,255,255,0.03)`, `border: 1px solid rgba(240,237,228,0.08)`
- Hover: `translateY(-2px)`, border goes gold, background slightly lighter
- Content: scene number (gold-muted uppercase), title, tone + setting pills
- Click: opens full-screen modal

## Scene detail modal

- Overlay: `position: fixed`, `inset: 0`, `z-index: 1000`, backdrop-blur
- Modal: `max-width: 860px`, `border-radius: 16px`, `background: #111827`
- Entry animation: `modalIn` — `translateY(20px) scale(0.97)` → identity, 0.35s ease-out
- Content: image(s), then body with scene number + title + setting + visual description + key narrative beat + camera direction
- Close: `&times;` button, fixed position top-right, ESC key, overlay click

## Visual themes section

6 cards in responsive grid (`repeat(auto-fill, minmax(280px, 1fr))`). Each: gold heading, body text in muted cream, `—` list markers for bullet items. Background `rgba(255,255,255,0.02)` with subtle border.

## Responsive

| Breakpoint | Changes |
|------------|---------|
| ≤600px | Container padding to 16px, section padding to 40px, scene grid to 1 column, modal body to 20px, themes grid to 1 column |

## Motion

- Modal entrance: `0.35s ease-out` with slight vertical lift + scale
- Card hover: `0.3s ease` on all properties
- Thumbnail zoom: `0.4s ease` on transform
- Nav link hover: `0.25s ease`
- No prefers-reduced-motion override yet (todo)

## States implemented

- **Hero:** resting
- **Story:** resting (full text, no truncation)
- **Scene cards:** resting, hover (lift + glow)
- **Scene modal:** closed, open (with animation), close (via button, overlay click, ESC)
- **Themes:** resting
- **Responsive:** 600px breakpoint
- **Not yet:** image loading state, image error state, empty state (no applicable), focus rings on cards

## Key design decisions

1. **Serif for story, sans for UI.** Georgia for the narrative body signals "this is a story to be read." Avenir Next for everything else signals "this is an interface to navigate." The split helps the reader switch modes.

2. **Gold as the only accent.** No secondary accent color. No tech gradients. The gold is the light. Restraint gives it meaning — it only appears on section titles, hover borders, emphasis text, and scene numbers. 10% rule respected.

3. **Deep navy as the negative space.** #0b111e reads as night, not as a generic dark mode. It is explicitly cold. The warm accent fights it. This mirrors the story's central conflict word-for-word: "for the first time since his father died, he was not cold."

4. **Cards for browse, modal for study.** The grid lets you scan all 15 scenes at once. The modal gives you the full storyboard detail without leaving the page. This is the "explore" pattern — scan first, then dive.

5. **One image per card, multi-panel in modal.** Scene 13 and 15 have multiple images. The card shows the first. The modal shows all panels with individual captions. This prevents the grid from being uneven while still delivering the full content.

## Content inventory

```
/scenes/                     — 18 generated images
  /01_the_watcher.png
  /02_the_storm_gathers.png
  /03_the_mercy.png
  /04_the_fox_and_gull.png
  /05_the_choice.png
  /06_the_climb.png
  /07_the_mechanism.png
  /08_the_light.png
  /09_the_sight.png
  /10_the_embrace.png
  /11_the_dawn.png
  /12_the_inheritance.png
  /13a_winter.png
  /13b_spring.png
  /13c_mother_watching.png
  /14_the_apprentice.png
  /15a_the_cycle_echo.png
  /15b_the_cycle_wide.png

/index.html                  — Single-page static site
/story.md                    — Full narrative text
/storyboard.md               — 15 scenes, visual themes, opening/closing callback
```

## Drift to refuse

- No SaaS dashboard patterns (metric cards, charts, tables, sidebars)
- No "modern tech" gradient backgrounds (purple-to-cyan, blue-violet)
- No cards-inside-cards layout
- No generic serif-for-everything or sans-for-everything type system
- No Inter, Plus Jakarta Sans, or Roboto as default UI fonts
- No exclamation points in copy
- No centered hero with nothing below — the cliffhanger principle already shows 40–80px of the next section
