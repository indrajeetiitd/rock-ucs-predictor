# Rock UCS Predictor (dashboard)

Static web app: choose lithology, rock type, model (Extra Trees, CatBoost, Random Forest) and the three inputs (PLS, Vp, SH) to get the predicted UCS,
the single-split (80/20, seed 42) R2 figure and metrics.
The published RF-LR (Liu et al., 2023) is shown only as a reference. All models run in the browser (JavaScript), so no server is required.

## Publish on GitHub Pages (3 steps)
1. Create a new GitHub repository and upload everything in this folder (index.html, .nojekyll, assets/) to the repository root.
2. Repository **Settings -> Pages -> Build and deployment -> Source: Deploy from a branch**, branch **main**, folder **/ (root)** -> Save.
3. After a minute the site is live at `https://<your-username>.github.io/<repository-name>/` - share that link.

## Run locally
Browsers block loading the model files from `file://`, so serve the folder:

    python -m http.server 8000      # then open http://localhost:8000

## Files
- `index.html`  - the interface and the JavaScript model evaluators
- `assets/meta.json` - metrics, scatter points, ranges, scaler values
- `assets/models/*.json` - exported Extra Trees / Random Forest / CatBoost per lithology (loaded on demand)

Reference: Liu, Z. et al. (2023) Prediction of uniaxial compressive strength of rock based on lithology using stacking models. Rock Mechanics Bulletin 2, 100081.
