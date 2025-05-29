```julia
bloch_sphere(
    states...;
    textsize,
    color,
    drawing_size,
    offset_x,
    offset_y,
    filename,
    format,
    fontfamily,
    background_color,
    lw,
    eye_point,
    extra_kwargs...
) -> Luxor.Drawing

```

Draw a bloch sphere, with the inputs being a list of `string => state` pairs, where the string is a label for the state and a state can be a complex vector of size 2, a Yao register or `DensityMatrix`. If you want to get a raw drawing, use `draw_bloch_sphere` instead.

### Keyword Arguments

Note: The default values can be specified in submodule `BlochStyles`.

  * `textsize`: the size of the text
  * `color`: the color of the drawing
  * `drawing_size`: the size of the drawing
  * `offset_x`: the offset of the drawing in x direction
  * `offset_y`: the offset of the drawing in y direction
  * `filename`: the filename of the output file, if not specified, a temporary file will be used
  * `format`: the format of the output file, if not specified, the format will be inferred from the filename
  * `fontfamily`: the font family of the text
  * `background_color`: the background color of the drawing
  * `lw`: the line width of the drawing
  * `eye_point`: the eye point of the drawing
  * `extra_kwargs`: extra keyword arguments passed to `draw_bloch_sphere`

      * `dot_size`: the size of the dot
      * `ball_size`: the size of the ball
      * `show_projection_lines`: whether to show the projection lines
      * `show_angle_texts`: whether to show the angle texts
      * `show_line`: whether to show the line
      * `show01`: whether to show the 0 and 1 states
      * `colors`: the colors of the states
      * `axes_lw`: the line width of the axes
      * `axes_textsize`: the size of the axes texts
      * `axes_colors`: the colors of the axes
      * `axes_texts`: the texts of the axes

### Examples

```jldoctest
julia> using YaoPlots, YaoArrayRegister

julia> bloch_sphere("|ψ⟩"=>rand_state(1), "ρ"=>density_matrix(rand_state(2), 1));
```
