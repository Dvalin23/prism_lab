# Prism Lab

A scroll-driven 3D studio website, built as a demo that a real-time WebGL site can be made without any engine or library. The studio and the eight works are fictional concept pieces.

## What's in this folder

| File | What it is |
| --- | --- |
| `index.html` | The whole site in one file (HTML, CSS and JavaScript). No build step, no dependencies. |
| `prism-lab-reply.mp4` | 16-second 9:16 screen recording of the site, ready to post. |

## How to run it

Double-click `index.html`, or drag it into a browser. It needs a browser with WebGL2 (current Chrome, Edge, Firefox or Safari). If WebGL2 is missing, the page shows a short message instead.

The fonts (Unbounded and IBM Plex Mono) load from Google Fonts. Offline, the site still works with fallback fonts.

## What you will see

1. **Loader:** an animated iris with a percent counter while the artwork is generated.
2. **Hero:** a glitchy "PRISM" logotype inside a 3D grid room, with a glass prism in front of it.
3. **Gallery:** scrolling flies you through eight floating works. The current work's title shows bottom-left.
4. **Ending:** the whole screen flips to paper white around a glowing portal, with the manifesto and a contact button.

## Controls

- **Scroll or swipe:** fly forward.
- **Hover a work:** ripple effect and an "OPEN" cursor.
- **Click a work:** opens a case card. Press `Esc` or the close button to dismiss it.
- **Right-edge bars:** jump to a work.
- **Top nav:** Works, Studio and Contact jump to those parts of the scroll.

## How it is built

- Raw WebGL2, no libraries. The engine (matrices, shaders, geometry, post-processing) is written inline in `index.html`.
- Scene: an inside-out grid room, a flat-shaded glass prism, bendable gallery panels, a particle field, and a portal made of glowing rings.
- Post-processing pass: chromatic split, glitch slices, glow, film grain, vignette and the white flip.
- The gallery artwork is drawn procedurally on 2D canvases at load, so there are no image files.
- The page height (900vh) maps scroll position to camera travel.

## Customising

Everything is in `index.html`:

- **Works (titles, tags, descriptions):** the `WORKS` array near the top of the script.
- **Artwork for each work:** the `STYLES` array (one drawing function per work) and `titleArt()` for the logotype.
- **Colours and fonts:** the `:root` block at the top of the `<style>` section.
- **Copy:** the HTML below the style block (hero text, manifesto, button).
- **Scroll length and path:** the `#scroller` height in CSS, and the constants `SPACING`, `STAND`, `P_A`, `P_B`, `Z_H0` and `Z_END`.

## Notes and limits

- The works are invented concept pieces. The "Start a project" button only shows a demo message; connect it to a real form before using the site for anything real.
- Opening the page with `?cap=1` turns on a frame-by-frame capture mode (`window.__prism.step(dt, progress)`), which is how the video was recorded.
- It is a heavy page for very old phones and laptops without a GPU. Pixel density is capped to keep it smooth.
