# room3D — 3D Living & Dining Room

An interactive **3D living & dining room** built with **three.js** in a **single HTML file**, modelled
after a real Hong Kong "2-bedroom, 1-living-room" flat (living room ≈ **4.25 m × 2.60 m**).

**▶ View it online: <https://mzf3334-dev.github.io/room3D/>**

> **Procedural only.** Every object is generated from three.js geometry primitives at runtime —
> **no 3D models, no texture maps, no image files**. Materials, the city outside the window, the TV
> screen artwork, even the abstract wall art are pure code.

## Run it locally

No build step, no server needed:

* Open **`index.html`** directly (it works from `file://`), or
* serve the folder: `python -m http.server` → open `http://localhost:8000/`

Internet is needed on first load — three.js r170 is pulled from the jsDelivr CDN via an import map.

## Controls

| Input | Action |
| --- | --- |
| Drag | Orbit |
| Wheel / pinch | Zoom |
| Right-drag | Pan |
| Keys `1`–`5` | Camera presets (Entrance / Sofa / Dining / TV / Top) |
| Key `N` | Day ⇄ Night |

On-screen chips: camera presets, **🌙 Night** (cross-fades the whole light rig), **🎥 Tour** (guided camera) and **⟳ Spin**.

## What's in the room

* **Shell** — teak strip-parquet floor (≈230 instanced planks), white walls, 6 recessed downlights.
* **Window wall** — casement window with security grille, wavy sheer curtains, ceiling fan, split A/C.
  Outside: a procedural high-floor **city view** whose lit windows glow at night.
* **TV wall** — floating oak console, 55" wall TV running a shader animation, soundbar, wall clock.
* **Display wall** — walnut display cabinet with LED strip, tiny figurines and a book niche.
* **Living side** — leather sofa, coffee table, ottoman with a **sleeping ginger cat** (breathing
  animation), rug, teddy bear, sideboard with lamp and abstract art.
* **Dining side** — light-oak table and chairs, pendant lamp, fruit bowl; a **kitchen pass-through**
  shows a mini galley kitchen (hob + wok, range hood, washing machine, fridge) beyond.
* **Entry / bathroom** — main door, shoes, umbrella stand, coat hooks; a tiled mini-bathroom visible
  through the folding door.

## Lighting

One cross-fading rig: warm directional "sun" + hemisphere light + PMREM `RoomEnvironment` by day;
downlights, pendant, cabinet LEDs, kitchen/bathroom strips and the TV shader take over at night.
Shadows: PCFSoft.

## Tech

three.js `0.170.0` (jsDelivr import map), `OrbitControls`, `RoomEnvironment` and a seeded PRNG
(`mulberry32`) for reproducible detail. Single file, no dependencies.
