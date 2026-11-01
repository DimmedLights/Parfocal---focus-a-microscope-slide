# Parfocal

Play it at **https://parfocal.vercel.app**

A daily microscope game. Find the specimen at low power, swing in the next objective, add oil for the last one, and lock focus as close to the right plane as you can. Scoring is measured against each objective's real depth of field.

Designed by Destiny, coded with Claude (Anthropic) as a collaborator.

## Modes

- **Brightfield**: Gram- and Ziehl–Neelsen-stained smears of twelve organisms, from *S. aureus* clusters to *Candida* pseudohyphae and gonococci inside neutrophils. Six of them show a real micrograph at 100x. Watch for dust on the coverslip, 170 µm above the smear.
- **Fluorescence**: drawn cultured cells labelled with DAPI, Alexa 488 (tubulin) and phalloidin-568 (actin), or a real three-channel field of HT29 cells (DNA, phospho-histone H3, cell body). Pick the right filter cube for each target and close the shutter to limit photobleaching.
- **Confocal**: thick epithelial organoids with nuclear, membrane-GFP and lysosome layers at different depths. Out-of-focus planes go dark; the pinhole trades brightness against section thickness.

Each mode has a shared daily slide plus random practice slides, timed or timeless play, and its own guided tutorial. Tutorials alternate between full-page lessons (big type beside a lit illustration of the microscope or a live diagram) and hands-on steps at the bench; the page morphs between the two.

- **Brightfield tutorial**: coarse and fine focus, the dust trap, parfocal objectives and immersion oil.
- **Fluorescence tutorial**: how epi-illumination and filter cubes work, why you focus on DAPI first, photobleaching and the shutter, indirect immunofluorescence (Alexa 488 on α-tubulin) and phalloidin for F-actin, one cube per label, then merging channels.
- **Confocal tutorial**: laser scanning and optical sectioning in a thick organoid, what the pinhole does and what an Airy unit is, finding layers by depth, a hands-on 1 AU vs 2 AU comparison, membrane-GFP and LysoTracker, and z-stacks.

## Microscopy guide

A guide, reachable from the title menu, the pause menu, the results screen, each tutorial lesson and the "What is a … microscope?" link under the microscope tabs:

- **Microscope pages** for brightfield, epifluorescence and confocal: a lit illustration with every part clickable and explained, the light path, how the instrument is used in a real lab, and its strengths and limits.
- **Concept pages**, each with something to play with: numerical aperture, immersion oil, depth of field, parfocal objectives, Gram and acid-fast stains, DAPI, immunofluorescence, phalloidin, GFP, LysoTracker, fluorescence and the Stokes shift, the filter cube, photobleaching, the pinhole and Airy units, z-stacks and organoids.

The site opens on a start screen: browsers only allow sound after a click or key press, so that first press switches the music and sound effects on.

## Controls

- Title menu: ↑ ↓ to choose, Enter to open, Q / E to switch microscope, T for timed or timeless, M for sound, B for music.
- In a round: hold ↑ ↓ for fine focus (it speeds up the longer you hold), Shift + ↑ ↓ for coarse, Enter to lock, O for oil, Esc to pause. The knob's outer ring is coarse and its centre is fine; turning fast travels further.
- The timer sits on the eyepiece: a draining arc on the rim and a plate with the seconds. The last five seconds tick out loud.
- On a phone the knob becomes two drag strips (Coarse and Fine).

## Optics

| Mode | Objectives |
|---|---|
| Brightfield | 10x/0.25 · 40x/0.65 · 100x/1.25 oil |
| Fluorescence | 10x/0.30 · 40x/0.75 · 100x/1.40 oil |
| Confocal | 10x/0.40 · 40x/0.95 · 63x/1.40 oil |

- Depth of field (widefield): λn / NA²
- Optical section (confocal, 1 AU): 0.88 λ / (n − √(n² − NA²))
- Defocus blur: blur-disc diameter 2·Δz·tan θ, with sin θ = NA / n
- The knobs have no steps. Coarse moves 0.8 µm per degree turned slowly and gears up to 6× when you spin fast; fine moves 0.07 µm per degree, up to 4×. A viscous drive (time constant 60–85 ms) delivers each turn to the stage frame by frame, so the image slides continuously through focus.
- Immersion oil sits on the coverslip as a bead about 0.8 mm tall. The front lens wets once the gap is under that, and the column breaks if you lift past 1.6 mm. The loupe zooms out in 3× steps so the lens and bead stay in view.


## Scoring

Focus is graded by what you can see, not by raw distance from a target. Each plane of the target is scored by the extra blur it shows on screen (on the confocal, by how much it dims): under 0.7 px of added blur is invisible and costs nothing, and credit halves by 2.2 px. Planes are weighted by how much specimen sits in them, and the total is compared with the sharpest plane that field allows, so a thick patch of smear isn't held to a standard no plane could meet. The verdict draws that sharpness curve with where you locked. Time bonus and technique penalties (coarse above 10x, no oil, wrong cube, bleaching) apply on top.

## Running it

It is a single static page with no build step. Open `index.html` in a browser, or deploy the folder to any static host. The live site deploys from `main` on Vercel.

## Photographs

`images/` holds the real micrographs, and `images/manifest.json` lists each one's author, licence, source page and the edits made (cropping, scale bars painted out). The modified CC BY-SA images are shared under the same licence. Everything else is drawn in code.

## Music

The soundtrack, "Coverslip Lounge", is an original generative jazz loop synthesised live in the browser (electric piano, bass, brushes, vibraphone and a pad). It turns down and muffles while you focus, opens up in menus, and ducks under the victory tune.

## Inspiration

The one-slide-a-day format comes from [dialed.gg](https://dialed.gg). The menus take their energy from *Persona 3 Reload* (Atlus), borrowing ideas only: tilted type, a highlight that slides between choices, and diagonal screen cuts. No Atlus art, type or sound is used.

## Live footage

Every fluorescence and confocal slide, and most brightfield ones, are real recordings of living samples: chromatin, mitochondria, ER, growing microtubules (EB1 comets), swimming bacteria, virus particles entering cells, Lyme spirochetes and neutrophils eating bacteria inside living mice, zebrafish and fruit fly embryos, organoids, Paramecium, Vorticella, rotifers, Euglena, diatoms, a dividing C. elegans embryo and cytoplasmic streaming. Clips live in `videos/` (credits in `videos/CREDITS.md`).

- 13 live slides (4 fluorescence, 4 confocal, 5 brightfield) built from 32 clips. Each clip is a 20–40 s seamless loop with a crossfaded seam, so it doesn't visibly restart while you focus.
- Each slide plays one clip per objective. Defocus blur, confocal dimming, photobleaching and the filter cube are applied live: a cube shows only the colour channel it passes, so a label goes dark under the wrong cube.
- Only the clip in view decodes; playback stops when the tab is hidden or you quit.
- Fixed slides remain only as Gram smears in brightfield, in the tutorials, and as a fallback if a clip fails to load.

## Lab technique and progress

- **Condenser aperture** (brightfield, `[` `]`): closing it raises contrast in unstained living cells but adds diffraction blur. About 65–85% open is the target for wet mounts; stained smears can stay open.
- **Lamp and laser power** (fluorescence and confocal, `L`): High is brighter but bleaches 2.4× faster; Low saves the dye but gives a dim, noisy image. Confocal now bleaches too, with its own signal meter.
- **Wrong cube cue**: a live label that a cube can't pass leaves the field black, so the eyepiece says "No signal" and the right cube pulses.
- **What you're seeing**: every verdict on a live slide adds one fact about that clip.
- **Z-stack** (confocal, after 63x): capture the sharpest plane, then the planes 1.2 µm either side using the Z readout. Scored separately on the results.
- **Results recap**: the three clips you focused play as small eyepieces, with folded footage credits.
- **Streaks and calendar**: a streak counter and the last two weeks of dailies on the title screen, four weeks on daily results.
- **Phones**: the eyepiece and its controls share one screen. The next objective's clip starts decoding during each verdict.

## Rendering and performance

- **GPU live view.** Live footage is not drawn into a canvas. The `<video>` sits in the eyepiece and its blur, colour channel (a multiply tint), brightness and opacity are CSS filters the browser composites on the GPU. Each frame the game only changes a few style values, and only when focus or settings change. Confocal sections and their fainter neighbouring planes are merged into one blur and one brightness.
- **Drawn slides** (Gram smears, tutorials) use the same path: each pre-drawn layer is its own element with its own CSS blur, stacked with normal or additive blending. The dust plane, far from focus, is pre-blurred and only redrawn when its blur changes by about 12%.
- The canvas renderer (`renderField`) remains for the share card, z-stack thumbnails, tests and browsers without CSS filters.
- **No frosted glass** on the screens or top bar (it re-blurred the moving footage every frame); overlays keep it. Entrance animations no longer leave a `filter` behind, the confetti canvas exists only while confetti flies, empty overlay canvases are hidden, and the timer arc has no drop-shadow filter.
- Per-frame DOM writes are deduplicated; the microscope side drawing redraws at most about 20 times a second while the knob turns on phones; the title's light cone only redraws when it moves.
- Measured in headless Chromium on a phone profile with the CPU throttled 4×: idle game 10 → 60 fps, turning the knob 11 → 47–56 fps, title 16 → 60 fps.
