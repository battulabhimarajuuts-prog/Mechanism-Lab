# Mechanism Lab

A responsive mechanical engineering reference website with six mechanism guides, an animated slider–crank, searchable categories, and eight formula calculators with explicit SI units and modeling assumptions.

## Run locally

Open `dist/index.html` in your browser, or run:

```sh
python3 -m http.server 8000 --directory dist
```

Visit http://localhost:8000. No installation or build is required. Google Fonts are optional; system fonts provide fallbacks.

## Upload to GitHub

1. Create an empty GitHub repository named `mechanism-lab`.
2. Extract the source ZIP. Upload its contents, preserving `dist/` and `.github/workflows/pages.yml`. For hidden folders, Git CLI is the most reliable option.
3. In repository **Settings → Pages → Build and deployment**, choose **GitHub Actions**.
4. Push to `main`, or run the **Deploy GitHub Pages** workflow from Actions.
5. The workflow reports the published GitHub Pages URL.

```sh
git init -b main
git add .
git commit -m "Add Mechanism Lab website"
git remote add origin https://github.com/YOUR_USERNAME/mechanism-lab.git
git push -u origin main
```

Replace YOUR_USERNAME with your GitHub username. Authenticate using GitHub's supported sign-in flow. No credentials belong in this project.

## Project layout

- `dist/index.html`: page structure
- `dist/style.css`: responsive styles
- `dist/app.js`: mechanism data, diagrams, animation, filters and calculators
- `.github/workflows/pages.yml`: automatic GitHub Pages deployment
- `LICENSE`: MIT license

Add mechanisms in the `mechanisms` array and formulas in the `formulas` array in `dist/app.js`. Each calculator defines input units, a calculation function and its assumptions.

## Engineering scope

Calculators use idealized mechanics models. All lengths, forces and material properties must follow the units shown. Values are nominal; verify boundary conditions, stress concentrations, tolerances, load cases and applicable standards before design use. Mechanism schematics illustrate topology and are not dimensioned manufacturing drawings. The live slider–crank uses exact in-line rod closure with l > r.

## Validation

JavaScript syntax verified with `node --check dist/app.js`. Reference cases: stress 1000 N / 100 mm² = 10 MPa; cantilever tip deflection (100 N, 500 mm, E=200000 MPa, I=100000 mm⁴) = 0.208333 mm; 20:60 gear pair at 1200 rpm gives 400 rpm; aluminum-like expansion at 23 µm/(m·K), 1000 mm and 50 K gives 1.15 mm.
