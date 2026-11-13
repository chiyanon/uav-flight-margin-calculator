# UAV Flight Plan Margin Calculator

A web app for UAV photogrammetrists. It turns the **“Margin”** setting of DJI flight-planning apps (GS RTK, GS Pro, Pilot 2) into the frontlap and sidelap you actually get at the **edge** of your survey area. It then recommends the margin that makes the whole area — boundary included — good enough for orthomosaics and 3D models.

**▶ Use it online:** https://YOUR-USERNAME.github.io/uav-flight-margin-calculator/

It is a single HTML file with no dependencies and no data sent anywhere. You can also download `index.html` and open it offline in any browser, for example in the field.

## Why a margin?

A point inside the survey area is photographed from both sides. A point on the boundary is only photographed from the inside, unless the route continues past it. With no margin, boundary points get roughly **half** the photos of interior points, so orthomosaic and 3D-model edges are weak. The margin extends the route beyond the boundary. This app tells you how much is enough.

## Features

- **Payload presets** with locked, manufacturer-published sensor values:
  - DJI Phantom 4 Pro / RTK / Multispectral
  - Mavic 3E / 3M, Matrice 3D / 4E / 4D
  - Zenmuse P1 / L1 / L2 / L3
  - Wingtra, eBee X, Trinity Pro (Sony LR1), Phase One iXM-100
  - MicaSense RedEdge-P / Altum-PT
  - Custom camera
- **Recommended margin** worked out from your edge frontlap/sidelap targets, including the effect of tall objects (rooftops, canopy).
- **Verification:** simulates every photo and flight line and checks that every point of the area meets the targets, whichever way the app places the first line.
- **Coverage map** coloured by local frontlap, sidelap, images per point, or pass/fail, with a breakdown of the survey area by overlap class.
- **Motion-blur and camera-interval checks**, with shutter-speed guidance.
- **Help system:** a “?” on every setting with its meaning, valid range, typical values and effect; a Help centre covering concepts, a settings reference, DJI app usage, FAQ and glossary; and input range checks.
- Works on desktop and mobile, in light and dark mode.

## How it works (short)

| Quantity | Formula |
|---|---|
| GSD | altitude × pixel pitch ÷ focal length |
| Photo interval B | footprint along × (1 − frontlap) |
| Line spacing S | footprint across × (1 − sidelap) |
| Guaranteed photos per axis at overlap o | m = ⌊1 ÷ (1 − o)⌋ |
| Guaranteed photos at the boundary with margin M | ⌊(min(M, F/2) + F/2) ÷ step⌋ |
| Recommended margin | M = m × step − F/2 (along and across track; the larger one is used) |

The in-app Help centre gives the full explanation.

## Limitations

The model assumes:
- a rectangular area aligned with the flight lines
- nadir (straight-down) photos
- a constant height above the evaluated surface
- no wind drift

Real apps may add turns, place lines differently or clip the margin. Always compare the route the app draws before flying. Sensor values come from published specifications; where a manufacturer does not publish a value, the preset note says so.

## Licence

[MIT](LICENSE)
