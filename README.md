# room3D — 客飯廳 3D Living Room

An interactive **3D living & dining room** built with **three.js (via importmap)** in a **single HTML file**.
Modelled after a real Hong Kong "2房1廳" flat (living room ≈ **4.25 m × 2.60 m**, from the floor plan in `images/`).

> **Procedural only.** Every object is generated from three.js geometry primitives at runtime —
> **no 3D models, no texture maps, no images**. Materials, planks, the city outside the window,
> the TV screen artwork, even the abstract wall art are pure code.

## Run it

No build step, no server needed:

* Double-click **`index.html`** (works from `file://`), or
* serve the folder: `python -m http.server` → open `http://localhost:8000/`

Requires an internet connection on first load (three.js r170 is pulled from the jsDelivr CDN through an import map).

## Controls

| Input | Action |
| --- | --- |
| Drag | Orbit |
| Wheel / pinch | Zoom |
| Right-drag | Pan |
| Keys `1`–`5` | Camera presets (Entrance / Sofa / Dining / TV / Top) |
| Key `N` | Day ⇄ Night |

On-screen chips: camera presets, **🌙 夜燈 Night** (cross-fades the whole light rig), **🎥 環繞 Tour** (guided camera), **⟳ 自轉 Spin**.

While the page is open, a small console hook is available for tinkering:
`__room.snapTo('sofa')`, `__room.look(px,py,pz, tx,ty,tz)`, `__room.setNight(true)`, `__room.apply(1)`, `__room.png()`.

## What's in the room

* **Shell** — teak strip-parquet floor (≈230 instanced planks with per-plank tint), white walls,
  skirting, window-side ceiling soffit, 6 recessed downlights.
* **Window wall** — aluminium casement window with mullion/transom + security grille, oak window board,
  wavy sheer curtains (vertex-animated), brass rod, ceiling fan, split A/C.
  Outside: a high-floor **city view** — procedurally generated towers with ~2 000 instanced window
  quads that light up at night, gradient sky shader, distance fog.
* **TV wall** — the **中空櫃** "hollow" floating oak console (open middle shelf with router/books/plant),
  55" wall TV whose screen runs a procedural shader animation (art mode at night), soundbar, white
  4-drawer chest, wall clock above the main door.
* **Display wall** — walnut glass display cabinet with LED strip and six tiny pastel figurines
  (a nod to the figurine cabinet in the reference photos), plus a book niche.
* **Living side** — cream leather sofa (back to the window) with throw pillows and a folded knit,
  round oak coffee table, ottoman with a **sleeping ginger cat** (breathing animation), two-tone rug,
  teddy bear, sideboard with brass table lamp, dried-flower vase and procedural abstract art.
* **Dining side** — light-oak table (as in the photo), two chairs, pendant lamp, fruit bowl and mugs,
  beside the **kitchen pass-through** with a frosted sliding door left open — a mini galley kitchen
  (counter, hob + wok, range hood, washing machine, fridge) is visible beyond.
* **Entry / bathroom** — walnut main door with peephole and door mat, shoe pairs, umbrella stand,
  hook rail with tote and cap; white folding bathroom door ajar, showing a tiled mini-bathroom
  (vanity, round mirror, toilet).

## Lighting

One cross-fading rig: warm directional "sun" through the window + hemisphere light + PMREM
`RoomEnvironment` for reflections during the day; at night the downlights, pendant, cabinet LEDs,
console under-glow, kitchen/bathroom strips and the TV shader take over. Shadows: PCFSoft.

## Notes

* Reference material (floor plan, photos, `room_floor_details.txt`) lives in `images/` and is
  **git-ignored on purpose** — this repo only carries the deliverable.
* Tech: three.js `0.170.0` (jsDelivr import map), `OrbitControls`, `RoomEnvironment`, seeded PRNG
  (`mulberry32`) for reproducible detail. Single file, no dependencies.
