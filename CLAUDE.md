# CLAUDE.md

## Project
A dependency-free, single-file first-person cooking game. Everything lives in `index.html`; there is no build step, package manager or test suite. Open the file in a browser to run it.

## Layout of `index.html`
- `<style>`: page, header, nav buttons, overlay, toasts.
- First `<script>`: game content you tune: `CONFIG`, `GOOD_ZONE`, `COOKERS`, `INGREDIENTS`, `RECIPES`.
- Second `<script>`: the engine. Game actions (`useIngredient`, `chopClick`, `takeFromCooker`, `serve`, `toggleKnife`), canvas drawing (`drawWindow`, `drawShelf`, `drawBoard`, `drawPan`, `drawTorch`, `drawTray`, `drawHands`), the loop (`update`/`draw`) and input handlers.

## How the first-person view works
- The kitchen is a fixed-position panorama drawn on a 2D canvas. The camera only turns (`yaw`, in degrees, clamped by `YAW_MIN`/`YAW_MAX`); `FOV` degrees are visible.
- Stations sit at angles in the `AT` object. `sx(angle)` converts an angle to a screen x. `u` is 1% of canvas height, `ppd` is pixels per degree; size things with these so they scale.
- Clickable things call `reg(x, y, w, h, action, label)` while drawing. `reg` records the hit area for `pointerdown` and returns whether the mouse is over it, for the highlight and tooltip.
- Keys 1-6 jump to stations (`SPOTS`); A/D, arrow keys and the screen edges turn the camera.

## Rules and conventions
- Keep graphics simple: flat colours, rectangles and emoji. No images or external assets.
- Keep it one file with no dependencies.
- There is no timer. The game is endless; ingredients unlock every `CONFIG.pointsPerUnlock` points (saved in `localStorage` as `cookingRounds`).
- Chopping needs the knife picked up (`state.knife`); the cooking zones come from `GOOD_ZONE`.
- Adding an ingredient: add it to `INGREDIENTS`, then use it in `RECIPES`. The pantry shelf is 4 columns by 2 rows, so more than 8 ingredients needs a layout change in `drawShelf`.

## Testing
No automated tests. Open `index.html`, press Start, and play through: grab ingredients, pick up the knife and chop, cook in the pan and torch, serve a matching tray at the window, and check the browser console for errors.
