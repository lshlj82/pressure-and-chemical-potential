# Pressure and Chemical Potential, Interactively

An interactive, single-page web demo of mechanical and diffusive equilibrium: how pressure, P = T(∂S/∂V), and the chemical potential, μ = −T(∂S/∂N), arise from entropy just as temperature does; the thermodynamic identity; how non-quasistatic processes create entropy; and a summary of classical thermodynamics.

Created by **Claude Opus 5.5**, based on the lecture notes by **Sang Hoon Lee** (Statistical Physics 1, Chapter 3, Interactions and Implications, Sections 3.4 to 3.6). It follows the demo for Sections 3.1 to 3.3 (what temperature really is).

## What's inside

**Mechanical equilibrium and pressure.** Two ideal gases share energy and volume through a movable partition. A rotatable 3D surface of S<sub>total</sub>(U<sub>A</sub>, V<sub>A</sub>) shows the system climbing to its peak when the partition is released, with the temperatures and pressures of both sides converging and a drawing of the partition and gas densities. The derivation of P = T(∂S/∂V)<sub>U,N</sub> and from it the ideal gas law.

**The thermodynamic identity.** dU = T dS − P dV, Q = T dS for quasistatic processes, isentropic processes, and C<sub>V</sub> = T(∂S/∂T)<sub>V</sub> and C<sub>P</sub> = T(∂S/∂T)<sub>P</sub> (Problem 3.33). A live experiment compresses a one-dimensional gas to half its length, or expands it to twice its length, with a piston at any speed: slowly, the process is isentropic (ΔS ≈ 0); fast compression puts in more work than −P dV and creates entropy; a piston pulled out faster than the molecules gives free expansion, ΔS = Nk<sub>B</sub> ln 2.

**Diffusive equilibrium and chemical potential.** μ = −T(∂S/∂N)<sub>U,V</sub> = (∂U/∂N)<sub>S,V</sub>, the generalized identity dU = T dS − P dV + μ dN, and the smallest example (an Einstein solid going from N = 3, q = 3 to N = 4, q = 2 at fixed Ω = 10, so μ = −ε). A calculator gives the chemical potential of an ideal gas at any temperature and pressure (−0.33 eV for helium at room temperature and 10<sup>5</sup> Pa; per mole as chemists quote it). A simulation of two chambers joined by an opening shows particles flowing from high μ to low until μ<sub>A</sub> = μ<sub>B</sub>. Problem 3.37 rederives the exponential atmosphere from μ(z) = μ<sub>0</sub> + mgz, with a chart of the two parts of μ against height. The page notes the chemical potential's central role in chemical reactions and phase transformations (Chapter 5) and in quantum statistics (Chapter 7).

**Summary of classical thermodynamics.** The table of thermal, mechanical, and diffusive interactions with their governing variables and formulas.

## Running it

There is nothing to build or install. The whole demo is one self-contained file, `index.html`, with all CSS and JavaScript inline.

Open it locally by double-clicking `index.html`, or serve the folder:

```bash
python3 -m http.server 8000
# then visit http://localhost:8000
```

### Publishing with GitHub Pages

1. Push this repository to GitHub.
2. Go to **Settings → Pages**.
3. Under **Build and deployment**, choose **Deploy from a branch**, select your main branch and the `/ (root)` folder, then save.
4. After a minute or so, the demo will be live at `https://<your-username>.github.io/<repository-name>/`.

## Technical notes

- Plain HTML, CSS, and vanilla JavaScript drawn on `<canvas>`. No frameworks, no build step.
- The partition's path follows the gradient of S<sub>total</sub> = (3/2)N<sub>A</sub> ln U<sub>A</sub> + N<sub>A</sub> ln V<sub>A</sub> + (the same for B): energy flows toward the side with the larger 1/T, and the partition moves toward the side with the smaller P/T. It ends at U<sub>A</sub>/U<sub>total</sub> = V<sub>A</sub>/V<sub>total</sub> = N<sub>A</sub>/N<sub>total</sub>.
- The piston experiment uses 300 noninteracting molecules moving along one direction, bouncing elastically off a wall moving at constant speed. Its entropy change is computed from Ω ∝ L<sup>N</sup>U<sup>N/2</sup> at the final length and energy, as if the gas then settled into equilibrium. Checked: a slow piston gives ΔS ≈ 0 and the quasistatic energy U ∝ 1/L², and a very fast expansion gives exactly Nk<sub>B</sub> ln 2.
- The 3D surface is drawn with a lightweight hand-written projection (no 3D library).
- Long equations wrap on narrow screens.
- Equations are typeset with [MathJax 3](https://www.mathjax.org/) (SVG output, loaded from cdnjs), so they need no extra web fonts.
- The only other external resources are the Newsreader and Instrument Sans fonts from Google Fonts, with system font fallbacks if they fail to load.
- Opening the page requires an internet connection for MathJax; offline, the equations appear as raw TeX.
- Supports light and dark mode: it follows `prefers-color-scheme`, and a sun/moon button in the top-right corner switches by hand, and the choice is remembered across pages; and is responsive down to phone widths.
- Constants used: k<sub>B</sub> = 1.381 × 10<sup>−23</sup> J/K, h = 6.626 × 10<sup>−34</sup> J s, N<sub>A</sub> = 6.022 × 10<sup>23</sup>.

## Caveats

- The chemical-potential calculator uses the monatomic ideal-gas formula; for nitrogen it treats the molecules as point particles, ignoring rotation.
- The atmosphere chart assumes a uniform 280 K.

## Credits

- Demo: Claude Opus 5.5
- Physics content and examples: lecture notes by Sang Hoon Lee
- The lecture follows Daniel V. Schroeder, *An Introduction to Thermal Physics* (Sections 3.4 to 3.6 and Problems 3.33 and 3.37).

## License

No license has been chosen yet. Add a `LICENSE` file (for example, MIT or CC BY 4.0) before sharing or reusing this project publicly, and confirm that any use of the lecture material is permitted by its author.
