# Dueply: the daily maths duel

A single-file, no-build, no-backend web game of applied-maths problems (kinematics).

- **Daily**: 5 problems, the same for everyone, seeded from the UTC date. 2 minutes per question, up to 100 pts each. Shows how you compare with the average player.
- **Trainer** (endless): endless problems, 90 s each. One wrong answer ends the run. Personal best is saved.

## Marking
- Right number with correct units, missing units, or sloppy units (`ms`, `m/s`, `ms^-1`): **100 pts**.
- Right number with a clearly wrong unit, or within 3%: **40 pts** (counts as a miss in Trainer).
- Otherwise 0. Fractions such as `7/6` are accepted. Tolerance is 0.5% of the answer.

## Run / deploy
Open `index.html`, or host it on GitHub Pages or Netlify (no build step).

## Adding questions
Append to the `B` array at the **end** of `index.html`:
`["Topic name", "question text", answer, "m" | "s" | "m/s" | "m/s2", difficulty 1-3]`.
Editing or reordering existing entries changes past and future daily puzzles.

## Notes
The "average player" figure is a modelled estimate from question difficulty, not live data.
Make sure you have the right to publish any questions you copy from textbooks or exam papers.

## Titles
Players earn XP (10–15 per correct answer, 3 per near miss, plus a daily-completion bonus) and unlock titles from Pythagoras up to Isaac Newton. Each title needs **XP, an Trainer streak and a number of daily days played**, so top titles take months. Edit the `TITLES` array in `index.html` to tune them. Add new titles at the end only.

## How to
A built-in **📘 How to** guide teaches linear motion with constant acceleration (s, u, v, a, t, the four equations, word clues and common traps). Edit the `#gd` block in `index.html` to change it.

Every question has a **Struggling?** button that opens the How to guide (the timer keeps running).

## Topics
The Trainer lets you pick **All topics** or one topic: **Motion**, **Binomials**, **Rearranging** or **Factorising**. The Daily mixes them (2 motion, 1 binomial, 1 rearranging, 1 factorising). Each topic has its own tab in the **📘 How to** guide, and the *Struggling?* button opens the guide at the current question's topic.

### Adding questions
- **Motion:** append `["Subtopic", "text", answer, "m" | "s" | "m/s" | "m/s2", difficulty]` to the `B` array.
- **Other topics:** append an object to the `NB` array, e.g.
  `{tp:"factor",y:"Trinomials",t:"Factorise 2x² − 5x − 12.",k:"alg",a:"(2x+3)(x-4)",s:"(2x + 3)(x − 4)",f:"factor",d:2}`.
  `k` is `num`, `list` or `alg`. For `alg`, `a` is the reference expression (checked by evaluating it at random values, so any equivalent answer is accepted), `s` is how it is shown, `f` is `factor` (needs brackets), `expand` (no brackets) or `any`.
- Add new questions to the **end** of each array. Reordering changes daily puzzles.
- Bump `DAILY_V` if you change how the daily is built, so old saved progress is discarded.
