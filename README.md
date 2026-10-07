# Lottie Studio

Lottie Studio is a lightweight, single-page tool for previewing and making practical edits to Lottie animations. The app is delivered as one HTML file, so it can be opened directly in a modern browser without installing a build tool.

## Concept

The animation is rendered in a composition-sized canvas, while the surrounding work area remains a checkerboard. The main preview and the export dialog use separate Lottie player instances, so opening export settings does not interrupt the canvas preview. Editing controls update the loaded animation data, and exports are generated from that data.

The app uses the open-source `@lottiefiles/dotlottie-web` player for JSON and dotLottie playback. The player and its WebAssembly runtime are loaded from jsDelivr, with an esm.sh fallback for the JavaScript module. The dotLottie archive reader also loads `fflate` from jsDelivr when the browser's built-in decompression support is unavailable.

## Features

- Import Lottie JSON (`.json`) and dotLottie (`.lottie` / `.dotlottie`) animations.
- Preview animations in the main canvas, with play/pause, stop, frame scrubbing, speed, loop, and direction controls.
- Start imported animations stopped, then use **Play** to begin playback. **Refresh Animation** rebuilds the main player from the current animation data and starts it again.
- Change composition width, height, frame rate, and frame count. When width or height changes, top-level layers shift together to keep their group centered in the new composition.
- Change static fill and stroke colors, and show or hide top-level layers.
- Set a canvas background color or transparency. The setting applies to the composition canvas; the surrounding work area stays checkerboard.
- Export edited animations as JSON or dotLottie.
- Export GIF or animated WebP with a dedicated live preview and configurable output options.
- Autosave the loaded animation, edits, and preview settings in the current browser tab's session storage. Refreshing the same page in that tab restores the session.
- Light and dark themes; creator attribution is Menye2x.

## Open the app

Open `lottie-studio-v0.27.html` in a current version of Chrome, Edge, or another modern browser. Internet access is needed to load the player runtime and, in some cases, the dotLottie archive decoder. GIF/WebP encoding uses browser canvas support; WebP export requires a browser that can encode WebP.

`waving_grass_lottie.json` is included as a sample animation.

## Session storage

Autosave uses `sessionStorage`, scoped to the page and browser tab. It survives a page refresh in that tab but is not a permanent project file or a cross-device backup. Use **Export JSON** or **Export Lottie** to save a durable copy.

## Project files

- `lottie-studio-v0.27.html` — complete application (currently displays app version 0.30).
- `waving_grass_lottie.json` — sample Lottie JSON animation.
- `.gitignore` — ignores common editor, operating-system, and temporary files.

## Credits and license notes

The playback runtime is `@lottiefiles/dotlottie-web` by LottieFiles, distributed under the MIT license. See the library's package metadata and upstream project for its license and notices. This project currently has no separate license file; add one before redistributing it under a specific license.
