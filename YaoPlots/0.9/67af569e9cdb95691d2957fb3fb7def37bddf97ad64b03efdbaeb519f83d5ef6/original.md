```
vizcircuit(circuit; w_depth=0.85, w_line=0.75, format=:svg, filename=nothing,
    show_ending_bar=false, starting_texts=nothing, starting_offset=-0.3,
    ending_texts=nothing, ending_offset=0.3)
```

Visualize a `Yao` quantum circuit.

### Keyword Arguments

  * `w_depth` is the circuit column width.
  * `w_line` is the circuit row width.
  * `format` can be `:svg`, `:png` or `:pdf`.
  * `filename` can be `"*.svg"`, `"*.png"`, `"*.pdf"` or nothing (not saving to a file).
  * `starting_texts` and `ending_texts` are texts shown before and after the circuit.
  * `starting_offset` and `end_offset` are offsets (real values) for starting and ending texts.
  * `show_ending_bar` is a boolean switch to show ending bar.

### Styles

To change the gates styles like colors and lines, please modify the constants in submodule `CircuitStyles`. They are defined as:

  * CircuitStyles.unit = Ref(60)                      # number of points in a unit
  * CircuitStyles.r = Ref(0.2)                        # size of nodes
  * CircuitStyles.lw = Ref(1.0)                       # line width
  * CircuitStyles.textsize = Ref(16.0)                # text size
  * CircuitStyles.paramtextsize = Ref(10.0)           # text size (longer texts)
  * CircuitStyles.fontfamily = Ref("JuliaMono")       # font family
  * CircuitStyles.linecolor = Ref("#000000")          # line color
  * CircuitStyles.gate_bgcolor = Ref("transparent")   # gate background color
  * CircuitStyles.textcolor = Ref("#000000")          # text color
