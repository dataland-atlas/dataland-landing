# dataland-landing

The public landing and sign-in gate for **Atlas**, Dataland's internal platform — live at [dataland.team](https://dataland.team).

A procedural "synapse tree" grows behind the page: a deterministic branching skeleton (seed `A71A5`, the same tree on every load) fleshed out with up to 220,000 GPU particles, its branch tips linked into a firing neural graph. Nature and machine intelligence in one organism — the studio's own subject matter. The pointer parts the particles and makes nearby synapses fire; the numbers in the footer are the scene's real telemetry.

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

- The scene honors `prefers-reduced-motion` (renders a single still frame) and falls back to a static gradient without WebGL2.
- Particle count drops to 70,000 on narrow screens; device pixel ratio is capped at 2.
- All page code, geometry, and shaders are original to this repository. Three.js is MIT-licensed; Geist is licensed under the SIL Open Font License 1.1 — texts in [`licenses/`](licenses/).
