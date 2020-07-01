## hiding/showing elements with mix-blend-mode

During the first course of the webdesign minor (CSS To The Rescue) i was asked to explore the limits of CSS, there is something cool i found out you could do with the `mix-blend-mode` property, you can see the result below.

![blend modes](https://user-images.githubusercontent.com/36195440/86238680-37959c00-bb9e-11ea-8e80-3f14e48ee3e2.gif)

Mix blend modes allow you to mix the colors of an element with the colors of its parent, i used this techinique together with an optical illusion trick i learned from watching [ this video](https://www.youtube.com/watch?v=lvvcRdwNhGM) i created two SVG's one of which was an animation of 12 frames with all frames layered over one another and only 1/12 of iets content visible.
The second SVG is a black box with small openings which were 1/12 parts wide where the black bars are the remaining 11/12 parts this shows every section of each of the 12 animation frames individually when you move them over one another.

### Applying mix-blend-mode
As i explained above mix-blend-modes can be used to blend colors of elements layered over one another, the blend mode i used was: 

`multiply`: the element is multiplied by the background and replaces the background color. The resulting color is always as dark as the background.

Other mix-blend-mode values:
| value | explanation                                           |
| ----- | :----------------------------------------------------:|
| `screen` |multiplies the background and the content then complements the result. This will result in content which is brighter than the |
| `overlay` | multiplies or screens the content depending on the background color. This is the inverse of the hard-light blend mode. |
| `color-dodge` | this attribute brightens the background color to reflect the color of the content. |
| `color-burn` | this darkens the background to reflect the content’s natural color. |
| `hard-light` | depending on the color of the content this attribute will screen or multiply it.|
| `soft-light` | depending on the color of the content this will darken or lighten it. |
| `difference` | this subtracts the darker of the two colors from the lightest color. |
| `exclusion` | similar to `difference` but with lower contrast. |
| `hue` | creates a color with the hue of the content combined with the saturation and luminosity of the background. |
| `saturation` | creates a color with the saturation of the content combined with the hue and luminosity of the background. |
| `color` | creates a color with the hue and saturation of the content and the luminosity of the background. |
| `luminosity` | creates a color with the luminosity of the content and the hue and saturation of the background. This is the inverse of the color attribute. |
