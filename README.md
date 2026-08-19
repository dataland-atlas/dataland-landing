# dataland-landing

The public landing and sign-in gate for **Atlas**, Dataland's internal platform — live at [dataland.team](https://dataland.team).

One enormous limb arches behind the page: a deterministic skeleton (seed `A71A5`, the same growth on every load) that enters off-frame at the lower left, sweeps across the viewport and plunges off the bottom right, with offshoots leaning from its upper side. Its surface is not geometry but up to 340,000 GPU particles laid on the tube's skin, with up to 45,000 instanced grass blades rooted on its back and ~225 point-cloud flowers and mushrooms sprouting between them — bioluminescent, on true black, in the language of immersive point-cloud installations: lime canopy fading through electric cyan into blue-violet hollows, rare magenta blooms, ember-hearted blue flowers, rim-lit mushroom domes, warm gold fireflies. Nature and machine intelligence in one organism — the studio's own subject matter. The pointer is a lantern: whatever it passes over burns brighter, and the grass parts under it like a brushed pelt. The numbers in the footer are the scene's real telemetry.

**The entrance.** One expanding wavefront conducts the whole load. A temporary wire cage rides the front and explains the limb's topology; the particle skin condenses into place a beat behind it, with a bright band where it lands, and the grass grows out of the surface as the front passes; then the cage burns off and is disposed. The page copy reveals word by word over the same 3.4 seconds.

## Run locally

No install, no build step — one static page:

```bash
python3 -m http.server 4173 --bind 127.0.0.1
```

Then open [http://127.0.0.1:4173](http://127.0.0.1:4173).

## Structure

```text
index.html                        # the complete page — markup, styles, scene
assets/
  three.module.min.js             # vendored Three.js r180 (+ three.core.min.js)
  geist-sans-variable.woff2       # vendored Geist variable fonts
  geist-mono-variable.woff2
licenses/                         # third-party license texts
```

The sign-in form currently forwards to `APP_URL` (top of the script in `index.html`); point it at the deployed Atlas app when IAM wiring lands.

## Notes

- The scene honors `prefers-reduced-motion` (skips the sweep and renders the settled limb as a still frame) and falls back to a static gradient without WebGL2.
- Particle count drops to 110,000 on narrow screens; device pixel ratio is capped at 2.
- `window.__atlas` exposes the scene for inspection: `seek(t)` parks the entrance at any point of its travel and holds it there, `play()` resumes, `warp()` jumps to the finished state. A true replay of the cage means reloading — it is disposed once the sweep completes, which is the point.

### Credits

The skeleton, the particle shell, the palette and the page are original to this repository. Two interaction techniques are adapted from **[MengTo/Skills](https://github.com/MengTo/Skills)** (MIT, © 2026 Meng To) — `build-wireframe-scan-reveal` for the paired cage-and-surface entrance and its landed timings, `staggered-word-reveal` for the word-by-word copy, and `threejs-landscape` for the instanced-ribbon grass technique (all wind and bend in the vertex shader).

Note that **[MengTo/sylva](https://github.com/MengTo/sylva)** — the site these skills were extracted from — carries **no license** of its own (no `LICENSE` file; its `licenses/` folder holds only third-party texts). Publishing source publicly is not a grant, so nothing here is copied from it. The skills repo is the part deliberately licensed for reuse, and it is the only part used.

Three.js is MIT-licensed; Geist is licensed under the SIL Open Font License 1.1. All texts in [`licenses/`](licenses/).
