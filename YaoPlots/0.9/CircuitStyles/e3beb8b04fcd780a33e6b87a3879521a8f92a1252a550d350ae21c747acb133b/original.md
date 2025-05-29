```
CircuitStyles
```

A module to define the styles of the circuit visualization. To change the styles, please modify the variables in this module, e.g.

```julia
julia> using YaoPlots

julia> YaoPlots.CircuitStyles.unit[] = 40
40
```

### Style variables

#### Sizes

  * `unit` is the number of pixels in a unit.
  * `r` is the size of nodes.
  * `lw` is the line width.

#### Texts

  * `textsize` is the text size.
  * `paramtextsize` is the text size for longer texts.
  * `fontfamily` is the font family.

#### Colors

  * `linecolor` is the line color.
  * `gate_bgcolor` is the gate background color.
  * `textcolor` is the text color.
