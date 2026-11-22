# AGENTS.md

## Project
Dueply is a single-file static site (`index.html`): HTML, CSS and vanilla JS, no dependencies, no build.

## Rules
- Keep it one file with no framework. Render with `textContent` / DOM nodes, never `innerHTML` with user input.
- Do not edit or reorder existing entries in the `B` question array: daily puzzles are seeded from it. Append only.
- Every question needs `[topic, text, answer, unit, difficulty]`. Verify the answer by hand (g = 9.8) before adding.
- Allowed units: `m`, `s`, `m/s`, `m/s2`. Extend `OKU` in `grade()` if adding more.
- Marking lives in `grade()`: 100 correct (unit optional or sloppy), 40 wrong unit or within 3%, else 0. Keep it lenient on formatting but strict on numbers.
- Colour tokens live in `:root`. Keep the dark-ink and brass palette.
- Test manually: a full daily, a timeout, an arcade run, and clearing localStorage keys prefixed `dueply.m.`.
- The `#gd` overlay is the student guide. Keep it accurate: dropped means u = 0 (not v = 0); v = 0 only at rest or at the top of a throw.
- The endless mode is called **Trainer** in the UI (internal names still say `arcade`).
- Algebra answers are marked by `compile()`/`gradeAlg()`, which evaluates the answer at random points and compares it with the reference. Keep new `alg` questions consistent: `a` must equal `s`.
- Each topic needs a How to tab (`#g-<topic>`) and generators (`GENS`) so the Trainer never runs out.
