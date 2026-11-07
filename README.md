# 🪔 Diwali: Find the Diya

An interactive Diwali greeting built with plain HTML, CSS and JavaScript. No frameworks, no build step, no libraries.

You start in a pitch-black room with only a small torch light that follows your cursor. Somewhere in the dark, five diyas are hiding. Strike a match, carry the flame to each wick, and light them all. When the last diya catches, the room fills with light, the screen slides away, and **"Happy Diwali"** appears in the dark, followed by fireworks.

## How to play

1. Move the mouse (or drag a finger) to search the dark with the torch light.
2. **Double-click** (or **double-tap** on touch screens) to light the matchstick.
3. Bring the flame close to a diya's wick to light it. The counter at the top left tracks progress (for example `2/5`).
4. Light all five diyas. The screen then slides up and the greeting and fireworks begin.

The match burns for about 22 seconds, and each diya you light adds 6 seconds. If it burns out, double-click again to strike a new one. Lit diyas stay lit.

## Features

- Torch-light effect drawn on a `<canvas>` overlay, with a warm flickering glow around the match and lit diyas
- Five diyas placed at random on every load: one in each corner area and one near the centre
- Matchstick that follows the cursor, with a flame that shrinks as it burns down
- Letter-by-letter "Happy Diwali" reveal with bright gradient letters and a glow
- Canvas fireworks (rockets and particle bursts) behind the greeting
- Sound effects generated in the browser with the Web Audio API, with no audio files needed: match strike, flame crackle, diya chimes, whoosh, letter shimmer, rocket whistles and booms
- Sound on/off button at the top right
- Responsive layout for phones, tablets, laptops and large monitors, in portrait and landscape

## Running the project

The whole project is a single file: **`diwali.html`**.

1. Download `diwali.html`.
2. Open it in any modern browser (double-click the file).

No server is needed. An internet connection is only used to load two Google Fonts (**Yatra One** and **Tiro Devanagari Hindi**). Without it, the page falls back to Georgia and still works.

> Browsers only allow sound after a user gesture, so audio starts on your first click or tap.

## Project structure

Everything lives in one file, in three parts:

| Part | What it does |
| --- | --- |
| `<style>` | Layout, typography, diya and match artwork, greeting animation, responsive rules |
| HTML body | Scene 1 (the dark room, diyas, match, hint, counter) and Scene 2 (greeting, fireworks canvas) |
| `<script>` | Torch rendering, game state, sound engine, diya placement, fireworks |

If you prefer separate files, move the `<style>` contents into `style.css` and the `<script>` contents into `script.js`, then link them from `index.html`.

## Customising

All values are near the top of the relevant sections in the script.

| What to change | Where |
| --- | --- |
| How long the match burns | `burnEnd = performance.now() + 22000` in `strike()` |
| Extra burn time per lit diya | `burnEnd += 6000` in `lightDiya()` |
| Torch size | `95 * K()` (idle torch) and `170` (match light) in `frame()` |
| How close the flame must be to light a diya | `55 * k` in the hit test inside `frame()` |
| Number of diyas | The `for (let i = 0; i < 4; i++)` clone loop. The `i === 4` check places the fifth diya at the centre, so update it if you change the count. The counter updates automatically. |
| Greeting text | The string `'Happy Diwali'` in the title builder |
| Letter colours | The two gradient arrays in the title builder |
| Fireworks frequency | `nextLaunch = now + 500 + Math.random() * 1100` in `fxLoop()` |

## Browser support

Works in current versions of Chrome, Edge, Firefox and Safari, on desktop and mobile. It uses Canvas 2D, the Web Audio API, CSS `clamp()`, `background-clip: text` and Pointer Events.

## Notes

- The `prefers-reduced-motion` setting is respected for the slide transition and the rising sparks.
- On touch devices the torch and flame are drawn slightly above your finger so your hand doesn't hide the light.
- "Light it again" at the end simply reloads the page, which hides the diyas in new spots.

## Credits

Built with HTML, CSS and JavaScript, created with the help of [Claude](https://claude.ai) by [Anthropic](https://www.anthropic.com). Fonts: [Yatra One](https://fonts.google.com/specimen/Yatra+One) and [Tiro Devanagari Hindi](https://fonts.google.com/specimen/Tiro+Devanagari+Hindi) from Google Fonts.

Happy Diwali! ✨
