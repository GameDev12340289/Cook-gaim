# Cooking Game Template (First Person)

A dependency-free HTML/JS cooking game with a simple, blocky first-person kitchen. Open `index.html` in a browser to play.

## How to play
1. **Look around** by moving the mouse to the left or right screen edge, or with A/D or the arrow keys.
   Jump straight to a station with keys **1-6** or the buttons under the header.
2. Click pantry ingredients on the shelf (1). Some go straight to the tray; others need prep.
3. **Chop**: pick up the knife next to the cutting board (2), then click the item on the board. Click the knife rest to put it back.
4. **Cook** items in the pan (3) or with the blowtorch (4, faster). Click them to take them out while the needle is in the green zone.
5. Walk to the serving window (5) and click the customer whose order matches your tray before their patience bar runs out.
6. Click the bin (6) or press **C** to clear the tray.

There is no timer: play as long as you like. New ingredients unlock every 100 points (`pointsPerUnlock`), and the Start button restarts your score.

## Customize
Everything is in `index.html` (one file): the `<style>` block, the content block (`INGREDIENTS`, `RECIPES`, `CONFIG`) and the game script. The kitchen is drawn on a canvas with flat colors and emoji; station positions are the `AT` angles at the top of the game script.

## Ideas to extend
Add new stations (oven, blender), difficulty levels, sound, sprites, upgrades, or a level select.
