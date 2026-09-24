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
| Keys `1`–`8` | Camera presets (Entrance / Sofa / Dining / TV / Passage / Top / Ceiling / Kitchen) |
| Key `N` | Day ⇄ Night |

The page opens on the **Entrance** view — as if you have just stepped in through the 大門 — and
**天花 Ceiling** (key `7`) drops the camera low and looks up at the ceiling, while **廚房 Kitchen**
(key `8`) steps through the 廚房門 into the galley kitchen.

On-screen chips: camera presets, **🚪 廚房趟門** and **❄️ 冷氣拉門** (slide the kitchen door shut /
draw the A/C cover — the cover stays shut in winter), **🌙 Night** (cross-fades the whole light rig),
**🎥 Tour** (guided camera) and **⟳ Spin**.

## What's in the room

The layout follows the owner's sketch and the site photos. The **north wall is the TV wall** and
reads, left to right, exactly as drawn:

| 廚房門 | 中空櫃 |  電視櫃 — 白色飾牆 + **冷氣窗**(窗口式冷氣) + 電視 + 長櫃  | 廁門貨架 | 廁所門 |
| --- | --- | --- | --- | --- |
| 0.70 m | 0.50 m | 1.95 m — **云石窗台 ≈ 2 m** | 0.40 m | 0.70 m |

* **Shell** — teak strip-parquet floor (≈230 instanced planks), white walls, 6 recessed downlights.
* **電視牆 TV wall** — light-oak **廚房門**, now a **趟門** on a room-side track that slides shut in
  front of the 中空櫃; walnut **中空櫃** (glass display over an open shoe rack); raised white feature
  wall carrying the **55″ TV** and the **窗口式冷氣** in its 冷氣窗 — with a two-panel **拉門** that
  slides across the A/C (shut in winter) and a row of **吊櫃** hanging above it; the long low
  **電視櫃** drawn in the sketch — top slab + divided lower level, **three bays**, open, white with
  oak lipping; dark plank wall with the clock, the **廁門貨架** book shelf, and the 廁所門.
* **Window wall (south)** — ≈ 3 m window with a **云石 window board**, security grille and sheer
  curtains. The sofa sits with its back to it, facing the TV wall. Outside: a procedural high-floor
  **city view** whose lit windows glow at night.
* **Living side** — cream leather sofa, ottoman with a **sleeping ginger cat** (breathing animation),
  rug and teddy bear. **No coffee table.**
* **大門 & 飯台** — the main door is on the **west wall**, between the kitchen door and the dining
  table: step in and the **飯台** (backing onto the west wall, with no cabinet beside it) is on your
  right, the 廚房門 on your left. Pendant lamp above the table; the sideboard, lamp and abstract art
  moved to the east wall.
* **到頂大柜** — the floor-to-ceiling cabinet standing to the sofa's right: **趟門 sliding doors
  below, normal hinged doors above**, hung right up to the ceiling.
* **過道 Passage (east)** — the east wall opens at its north end into a short passage: the 廁所門
  opens off the TV wall just around the corner, the **主人房門** sits on the passage's south side,
  and the passage **ends at the 客房門**, which opens into the guest room beyond — a platform bed
  whose storage drawers face the door, a wall fan, its own window. The passage is kept bare, with
  **no plant decorations**.
* **Entry corner & rooms** — shoes, umbrella stand and coat hooks beside the west door; behind the
  TV wall is a fitted galley kitchen — **double-zone induction hob + 抽氣機 hood**, sink with mixer
  tap, **washing machine under the worktop**, fridge with its magnets and tea towels, rice cooker,
  frosted **吊櫃** wall cabinets and the **廚房平台** worktop run (step in with the **廚房 Kitchen**
  preset) — and a tiled bathroom.

**No ceiling fan** and no split A/C — the cooling is the window-type unit above the TV cabinet.

## Lighting

One cross-fading rig: warm directional "sun" + hemisphere light + PMREM `RoomEnvironment` by day;
downlights, pendant, cabinet LEDs, kitchen/bathroom strips and the TV shader take over at night.
Shadows: PCFSoft.

## Tech

three.js `0.170.0` (jsDelivr import map), `OrbitControls`, `RoomEnvironment` and a seeded PRNG
(`mulberry32`) for reproducible detail. Single file, no dependencies.
