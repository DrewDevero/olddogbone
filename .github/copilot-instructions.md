# Copilot instructions

## Project shape

This repository is the public Old Dog Bone website. It is a dependency-free static site: `index.html` is the brand landing page and `pack-pursuit.html` is a standalone arcade game. Both pages keep their CSS and JavaScript inline; shared images, audio, and video live under `assets/`. There is no application bundler or server-side code.

The landing page presents the three content worlds (Old Dog Teacher, Rufus Reviews, and the Boys) as semantic page sections, with YouTube embeds and links to social channels, merch information, and the ASPCA. Pack Pursuit is a separate page whose inline script is an IIFE: its `worlds` data supplies each world's colors, character art, voice, clip, quote, and CTA; `levelWorlds` maps the ten levels onto those worlds. The canvas game loop and its DOM overlays share the same `state`, while HUD and character presentation are updated from that state.

## Build, test, and lint

There are no build, test, or lint scripts or toolchain manifests in this repository. To preview changes, run from the repository root:

```sh
python3 -m http.server 8000
```

Open `http://localhost:8000/` and `http://localhost:8000/pack-pursuit.html`. There is no automated single-test command; manually smoke-test the page changed. For Pack Pursuit, check character selection, starting/replaying, keyboard and touch movement, pause/resume, level progression, audio controls, and the score/share end screen. For the landing page, check the section navigation, embedded videos, responsive layout, and outbound links.

## Repository-specific conventions

- Keep each page self-contained: page-specific styles and scripts are inline in that page, and local media is referenced from the HTML file using paths relative to the site root.
- Preserve existing asset names and capitalization. Asset filenames include spaces and punctuation; encode spaces as `%20` in URL attributes when needed, and verify local media loads in the browser after changing a path.
- Keep Pack Pursuit's world-specific content in the `worlds` data and level-to-world mapping in `levelWorlds`; avoid duplicating those values in presentation handlers. Keep gameplay transitions aligned with `state.mode` and the existing screen, HUD, and character-presentation updates.
- The game canvas has separate logical dimensions for narrow and wide viewports and scales for device pixel ratio. Keep pointer coordinates translated through the canvas bounds, support keyboard and touch controls, and keep animation updates time-based.
- Preserve the semantic and accessible patterns already used: landmarks and labelled sections, descriptive media text, visible keyboard focus, reduced-motion styles, and live announcements for character changes. Keep external links that open a new tab paired with `rel="noopener noreferrer"`.
- Browser audio playback may be blocked until user interaction; retain the existing interaction-driven playback and rejection handling. Best-score persistence uses `localStorage`, which may be unavailable in some browser contexts.
