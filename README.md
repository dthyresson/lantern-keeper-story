# The Lantern Keeper

A bedtime story about a boy who watches a lighthouse, loses his father to a dark sea, lights the lamp himself, and passes the light to the next keeper. Developed iteratively across four phases.

## Process

### Phase 1 — Story

A 5-paragraph bedtime story skeleton was written from scratch, then refined through **10 iterative passes**. Each pass followed the same cycle: read the current draft, identify weaknesses in character arc and setting, and rewrite. Key developments across the iterations:

| Iteration | Focus |
|-----------|-------|
| 1 | Sensory depth (cold glass, salt air, sound of the sea), Finn's internal doubt |
| 2 | Finn's backstory — father lost on the *Sea Rose* when the lighthouse was dark. The inn scene gained smell and texture (woodsmoke, wet wool, fish stew). Physical doubt (Finn stops, turns, chooses) |
| 3 | Gareth as a character (grinding voice, yellowed teeth, pale blue eyes). The *Mercy* gained cargo and children. Finn's choice was physicalized — foot on the step, then back down |
| 4 | Finn's bedroom felt lived-in. Father's specific last words. Storm build-up with atmospheric pressure. The match pause — Finn whispers his own words |
| 5 | Mother's perspective (avoids the lighthouse, knife stops mid-stroke). Ellie Thorn named. The lighthouse sounds (*tick* of the mechanism). Circular ending — palm on glass |
| 6 | Gareth opens up (tower was his child). The *Mercy* arrives at dawn. Hand motif throughout |
| 7 | Ship's-eye view (Ellie on the *Mercy*). Finn's first season as keeper. The cycle completes with Tom at the base of the tower |
| 8–10 | Prose polish, sea as character, temperature contrast, an ending that lands through image |

The final story is ~3,200 words in `story.md`.

### Phase 2 — Storyboard

The story was broken into **15 cinematic scenes** based on narrative beats and location changes. Each scene was documented in `storyboard.md` with:

- Setting and visual description
- Key narrative beat
- Emotional tone
- Camera direction (shot types, movement, transitions)

**15 scenes:**

| # | Scene | Key Beat |
|---|-------|----------|
| 1 | The Watcher | Finn at the window, watching Gareth climb |
| 2 | The Storm Gathers | Gareth collapses, mother looks at lighthouse |
| 3 | The Mercy | Ellie on the ship, no light |
| 4 | The Fox & Gull | Village in panic, Finn's doubt |
| 5 | The Choice | Finn runs, stops, hears father's voice |
| 6 | The Climb | Spiral stairs, sensory transformation |
| 7 | The Mechanism | Finn works the wheel |
| 8 | The Light | The match, the bloom, the beam |
| 9 | The Sight | Ellie sees the light |
| 10 | The Embrace | Mother holds Finn in the lantern room |
| 11 | The Dawn | Ship arrives, mother on the quay |
| 12 | The Inheritance | Gareth passes the role |
| 13 | The Years | Montage across seasons, mother watching |
| 14 | The Apprentice | Tom arrives at the tower |
| 15 | The Cycle | Tom at the glass, light sweeps out |

**Visual themes** were tracked as running motifs:
- **Hands on Glass** — opening: Finn at bedroom window. Closing: Tom at lantern room glass. Same gesture, reversed context (outside → inside).
- **Hands on the Brass Wheel** — knowledge → mastery → legacy across scenes 7, 8, 12, 15.
- **Hand on Shoulder** — Gareth to Finn to Tom. The unbroken chain.
- **The Bell Buoy** — calm → frantic → calm, tracking the emotional arc.
- **Gold vs. Cold** — warm lamp against dark sea. Climax: "for the first time since his father died, he was not cold."
- **The Beam of Light** — watched from outside (1), created by Finn (8), followed by the ship (9), watched by mother healed (13), endless (15).

A visual themes appendix documents the opening/closing callback: identical composition (boy at window, hands on glass, dusk) but reversed — the watcher becomes the keeper.

### Phase 3 — Image Generation

Each scene was rendered using **fal-ai/nano-banana-2** (Google's fast image generation model) at 1K resolution, 16:9 aspect ratio, in an oil painting style with consistent visual language.

- 18 images generated across 15 scenes (scenes 13 and 15 have multiple panels)
- Saved to `scenes/` with scene-number-prefixed filenames
- Prompts were adapted from storyboard descriptions, refined to remove generic "4K" qualifiers and emphasize narrative-specific visual details

### Phase 4 — Web Page

A single-page HTML site (`index.html`) was designed and built to present all three layers of the project:

**Structure:**
- **Hero** — title, subtitle, nav links
- **The Story** — full narrative in readable serif type (Georgia), warm amber on deep navy
- **Storyboard** — 15 scene cards in a responsive grid with thumbnails. Clicking opens a modal
- **Scene Detail Modal** — shows the generated image(s), visual description, key narrative beat, and camera direction
- **Visual Themes** — 6 theme cards
- **Navigation** — prev/next buttons and arrow key support for stepping through scenes with crossfade and looping

**Design decisions:**
- **Register:** Brand — the interface IS the experience. | **Category:** Storybook / narrative showcase.
- **Color:** Deep navy `#0b111e` (the cold dark), warm gold `#fbbf24` (the light), cream text `#f0ede4`. The color temperature contrast mirrors the story's central conflict.
- **Type:** Georgia for story (reading), Avenir Next for UI (navigating). The split helps the reader switch modes.
- **Layout:** 1/4/9 rhythm (4px/16px/36px spacing scale), 960px container, responsive grid for cards.
- **Motion:** Card hover lift, modal entrance with scale + vertical offset, crossfade on scene navigation.
- **Gold restrained to 10%** — section titles, hover borders, emphasis text, and scene numbers only.

**States implemented:** hero, story text, scene cards (rest + hover), modal (open via card / nav buttons / keyboard — close via button / ESC / overlay click), responsive (600px breakpoint with 1-column grid and smaller controls).

## Files

```
./
├── index.html            # Single-page site with story, storyboard, themes
├── story.md              # Full narrative text (~3,200 words)
├── storyboard.md         # 15 scenes with camera direction + visual themes
├── README.md             # This file
├── scenes/               # 18 generated images (1K, 16:9, oil painting)
│   ├── 01_the_watcher.png
│   ├── 02_the_storm_gathers.png
│   ├── ... (15 scenes, 18 images)
│   └── 15b_the_cycle_wide.png
└── .commandcode/design/
    └── brief.md          # Design brief
```

## Running

Open `index.html` in any browser. No build step, no server, no dependencies.
