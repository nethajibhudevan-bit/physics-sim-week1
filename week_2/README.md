# Week 2 — The Sandbox

Cellular automata with falling sand and water.

- **Spec:** [`week2.pdf`](./week2.pdf) — read it first, it is the authority.
- **Template:** [`temp.py`](./temp.py) — runs as-is, but the physics is missing.
  One `NotImplementedError` in `SandSim.update()`: sand fall/slide and water
  spread. Fire, smoke, and wood are the bonus.
- **Setup:** see the [root README](../README.md).


question1
If the swap grid started completely empty (filled with zeros), any sand grain that doesn't move during a tick wud just disappear. Because we copy the original grid first, any grain that stays still keeps its spot safely in the swap grid. If we started blank instead, we'd have to manually re-copy every single un-moved grain back over, otherwise the simulation would accidentally erase them all.

question2
f you scan strictly left-to-right instead of randomizing the columns, the sand pile starts leaning heavily to the right side and looks totally asymmetrical. This happens because the left-side particles always get checked and processed first every single tick. They get the first chance to slide down to the right, filling up those spots before the right-side particles even get a turn to move left. Randomizing the order fixes this so both sides get an equal chance to slide, making the pile fall evenly.

This assignment was all about building a 2D sand and water simulation using Python, NumPy, and Pygame. Updating the grid bottom-up is what keeps particles from dropping multiple rows at once and flickering all over the place. Shuffling the column order every frame stops the sand from awkwardly piling up to one side, so it falls naturally instead. Copying the grid before making any moves keeps resting sand from just disappearing into nowhere. The physics itself is pretty straight to the point sand falls straight down or slides diagonally if it hits something, and water does all of that plus spreads out sideways to fill up flat spots.