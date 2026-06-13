# AGENTS.md

## Project

**The Lantern Keeper** — an interactive multimedia bedtime story about a lighthouse, a boy named Finn, and the light that never goes out. Zero-dependency static site (HTML/CSS/JS), deployed on Netlify with AI-generated oil-painting scenes.

## Project Structure

```
goal-test/
├── scenes/              # 18 AI-generated oil-painting scene images (16:9, 1K)
│   ├── 01_the_watcher.png        → Finn watches the lighthouse from afar
│   ├── 02_the_storm_gathers.png  → The storm approaches
│   ├── 03_the_mercy.png          → The ship in distress
│   ├── 04_the_fox_and_gull.png   → Animals as narrative guides
│   ├── 05_the_choice.png         → Finn decides to climb
│   ├── 06_the_climb.png          → Ascending the lighthouse stairs
│   ├── 07_the_mechanism.png      → Learning the lamp mechanism
│   ├── 08_the_light.png          → First lighting of the lamp
│   ├── 09_the_sight.png          → Spotting the ship
│   ├── 10_the_embrace.png        → Emotional reunion
│   ├── 11_the_dawn.png           → Morning after the storm
│   ├── 12_the_inheritance.png    → Passing of the keeper's role
│   ├── 13a_winter.png            → Winter at the lighthouse
│   ├── 13b_spring.png            → Spring renewal
│   ├── 13c_mother_watching.png   → Mother's perspective
│   ├── 14_the_apprentice.png     → Teaching the next keeper
│   ├── 15a_the_cycle_echo.png    → The cycle continues (close)
│   └── 15b_the_cycle_wide.png    → The cycle continues (wide)
├── README.md            # Project documentation
├── story.md             # Full ~3,200 word narrative text
├── storyboard.md        # 15 cinematic scenes with camera direction, tone, shot types
├── index.html           # Single-page interactive website with storyboard grid + modal viewer
├── netlify.toml         # Netlify deploy config (image CDN, caching, minification)
├── favicon.svg           # Lighthouse favicon
└── AGENTS.md            # This file — project reference for AI agents
```

