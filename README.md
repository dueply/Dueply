# THE SCALE

A higher-or-lower trivia game for the browser. Each round puts two very different real-world numbers side by side, such as Minecraft copies sold vs. the population of Brazil. One number is shown. The other is hidden, and you guess whether it is **HIGHER ▲** or **LOWER ▼**. Each right answer adds to your streak. One wrong answer ends the run.

## Features

- **76 exhibits** in nine categories: Music, Gaming, Earth, Space, Internet, Sports, Screen, Books, Life.
- The deck is shuffled at the start of each run, and no item appears twice in a run.
- Matchups are picked to stay close in magnitude, and they get closer as your streak grows.
- The hidden number rolls up for about 1.2 seconds before it lands, with a ticking sound and a marker that moves along an order-of-magnitude rail.
- Correct guesses flash green, play a chime, and slide the revealed card into place. Wrong guesses shake the screen, flash red, and play a thud.
- The Game Over screen shows your final streak, your all-time best (saved in `localStorage`), a rank title, an emoji **Share Score** button and **Play Again**.
- All sound is made with the Web Audio API, and there is a mute toggle (also on the `M` key).
- Keyboard controls: `↑`/`H` for higher, `↓`/`L` for lower, `Enter` to play again.
- The layout is responsive: cards sit side by side on desktop and stack on mobile.

## Tech

- One `index.html` file containing all the HTML, CSS and JavaScript.
- The only external dependency is Google Fonts (Space Grotesk and Inter).
- It is hosted on Netlify as a static site, with no build step (see `netlify.toml`).

## Run locally

Open `index.html` in a browser, or serve the folder:

```bash
npx serve .
# or
netlify dev --port 8889
```

## Editing content

All exhibits live in the `DATA` array near the top of the `<script>` block. Each entry looks like this:

```js
{ c: "Music", t: "The Weeknd", d: "monthly Spotify listeners", v: 110000000, n: "Approx. · 2025" }
```

`c` is the category, which must be a key in `CATS`. `t` is the title, `d` is the description shown under the number, `v` is the value, `p` is an optional prefix such as `"$"`, and `n` is the footnote.
