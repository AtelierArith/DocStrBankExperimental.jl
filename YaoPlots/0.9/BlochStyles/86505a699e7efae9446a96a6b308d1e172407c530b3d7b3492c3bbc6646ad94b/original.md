```
BlochStyles
```

The module to define the default styles for bloch sphere drawing. To change the default styles, you can modify the values in this module, e.g.

```julia
using YaoPlots
YaoPlots.BlochStyles.lw[] = 2.0
```

### Style variables

#### Generic

  * `lw`: the line width of the drawing
  * `textsize`: the size of the text
  * `fontfamily`: the font family of the text
  * `background_color`: the background color of the drawing
  * `color`: the color of the drawing

#### Sphere

  * `ball_size`: the size of the ball
  * `dot_size`: the size of the dot
  * `eye_point`: the eye point of the drawing

#### Axis

  * `axes_lw`: the line width of the axes
  * `axes_colors`: the colors of the axes
  * `axes_texts`: the texts of the axes, default to `["x", "y", "z"]`

#### State display

  * `show_projection_lines`: whether to show the projection lines
  * `show_angle_texts`: whether to show the angle texts
  * `show_line`: whether to show the line
  * `show01`: whether to show the 0 and 1 states
