# L-System Turtle

Grow plants, dragons and snowflakes from a rewriting rule — Lindenmayer systems drawn by a turtle, with stochastic rules, growth animation and SVG export. Runs entirely in your browser.

**Live:** <https://l-system.slippylabs.com/>

## What it does

- Axiom plus rules, rewritten n times, then read as turtle instructions: `F` draws, `+` and `-` turn, `[` and `]` remember and return.
- Thirteen presets: Koch curve and snowflake, dragon curve, both Sierpinski constructions, Hilbert, Gosper, Lévy C, Peano, and four plants.
- Stochastic rules with weights (`F -> F[+F]F : 0.4`) and a seed, so the same seed always grows the same plant.
- Adjustable angle, iterations, line width, three colouring modes, growth animation, and SVG or PNG export.

## How it works

Two stages kept apart: rewriting knows nothing about geometry, and the turtle knows nothing about grammars. The string grows geometrically — the classic plant triples each iteration — so expansion is capped at two million symbols and says when it stopped rather than letting the tab die.

## Verification

Both stages are exactly checkable, so both are checked exactly against an independent Python implementation, and then against the closed forms these curves are known by:

- Koch: 4ⁿ segments, ends 3ⁿ apart
- Hilbert: 4ⁿ − 1 segments, in a box exactly (2ⁿ − 1) square
- Dragon: 2ⁿ segments, ending √2ⁿ from the start, **and never crossing itself** — tested by checking all segment pairs up to n = 9
- Koch snowflake and the Sierpinski triangle close exactly on their starting point

Stochastic rules are checked for reproducibility (same seed, same string) and for choosing alternatives in proportion to their weights over 3,000 seeds.

## Run it locally

A static site. No build step, no package manager, no dependencies:

```
git clone git@github.com:slippylabs/l-system.slippylabs.com.git
cd l-system.slippylabs.com
python3 -m http.server 8000
```

Then open <http://localhost:8000>.

---

Part of [Slippy Labs](https://slippylabs.com). Every tool is indexed at
[projects.slippylabs.com](https://projects.slippylabs.com).
