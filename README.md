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

The layout follows the owner's sketch (**`images/tv_cabinet.jpg`**) and the site photos. The
**north wall is the TV wall** and reads, left to right, exactly as drawn:

| 廚房門 | 中空櫃 |  電視櫃 — 白色飾牆 + **冷氣窗**(窗口式冷氣) + 電視 + 長櫃  | 廁門貨架 | 廁所門 |
| --- | --- | --- | --- | --- |
| 0.70 m | 0.50 m | 1.95 m — **云石窗台 ≈ 2 m** | 0.40 m | 0.70 m |

* **Shell** — teak strip-parquet floor (≈230 instanced planks), white walls, 6 recessed downlights.
* **電視牆 TV wall** — light-oak 廚房門; walnut **中空櫃** (glass display over an open shoe rack);
  raised white feature wall carrying the **55″ TV** and the **窗口式冷氣** in its 冷氣窗; the long low
  **電視櫃** drawn in the sketch — top slab + divided lower level, **three bays**, open, white with
  oak lipping; dark plank wall with the clock, the **廁門貨架** book shelf, and the 廁所門.
* **Window wall (south)** — ≈ 3 m window with a **云石 window board**, security grille and sheer
  curtains. The sofa sits with its back to it, facing the TV wall. Outside: a procedural high-floor
  **city view** whose lit windows glow at night.
* **Living side** — cream leather sofa, ottoman with a **sleeping ginger cat** (breathing animation),
  rug and teddy bear. **No coffee table.**
* **大柜 & 飯台** — the big pastel drawer chest stands on the sofa's **right**; the light-oak dining
  table and chairs, pendant lamp and fruit bowl sit on its **left**, with the sideboard, lamp and
  abstract art on the west wall.
* **Entry / rooms** — main door on the east wall with shoes, umbrella stand and coat hooks; behind
  the TV wall you glimpse a mini galley kitchen (hob + wok, 抽氣扇, washing machine, fridge) and a
  tiled bathroom.

**No ceiling fan** and no split A/C — the cooling is the window-type unit above the TV cabinet.

## Lighting

One cross-fading rig: warm directional "sun" + hemisphere light + PMREM `RoomEnvironment` by day;
downlights, pendant, cabinet LEDs, kitchen/bathroom strips and the TV shader take over at night.
Shadows: PCFSoft.

## Tech

three.js `0.170.0` (jsDelivr import map), `OrbitControls`, `RoomEnvironment` and a seeded PRNG
(`mulberry32`) for reproducible detail. Single file, no dependencies.
