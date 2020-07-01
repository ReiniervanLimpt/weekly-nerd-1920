## hiding elements with mix-blend-mode

During the first course of the webdesign minor (CSS To The Rescue) i was asked to explore the limits of CSS, there is something cool i found out you could do with the `mix-blend-mode` property, you can see the result below.

![blend modes](https://user-images.githubusercontent.com/36195440/86238680-37959c00-bb9e-11ea-8e80-3f14e48ee3e2.gif)

Mix blend modes allow you to mix the colors of an element with the colors of its parent, i used this techinique together with an optical illusion trick i learned from watching [ this video](https://www.youtube.com/watch?v=lvvcRdwNhGM) i created two SVG's one of which was an animation of 12 frames with all frames layered over one another and only 1/12 of iets content visible.
The second SVG is a black box with small openings which were 1/12 parts wide where the black bars are the remaining 11/12 parts this shows every section of each of the 12 animation frames individually when you move them over one another.

### Applying mix-blend-mode

